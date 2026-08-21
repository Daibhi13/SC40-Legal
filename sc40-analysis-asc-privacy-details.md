# SC40 Analysis — App Store Connect Privacy Details

> Drafted August 21, 2026. Based on actual app code behavior, `PrivacyInfo.xcprivacy`,
> and Apple's App Privacy questionnaire taxonomy.
>
> **App**: SC40 Analysis (display name: "40 Yards")
> **Bundle ID**: `Accelerate.SC40-Analysis`
> **Category**: Health & Fitness
> **Age Rating**: 4+

---

## Data Types Declared in Privacy Manifest (PrivacyInfo.xcprivacy)

The app's `PrivacyInfo.xcprivacy` declares three collected data types, all with
`Linked = false` and `Tracking = false`, purpose = `AppFunctionality`:

1. `NSPrivacyCollectedDataTypeFitnessWorkout`
2. `NSPrivacyCollectedDataTypeUserContent`
3. `NSPrivacyCollectedDataTypePreciseLocation`

### API Access Declared

- `NSPrivacyAccessedAPICategoryUserDefaults` — reason `CA92.1` (access info from same app)
- `NSPrivacyAccessedAPICategoryFileTimestamp` — reason `C617.1` (display timestamps to user)

### Tracking

- `NSPrivacyTracking = false`
- `NSPrivacyTrackingDomains = []` (empty)

---

## App Store Connect — App Privacy Questionnaire Answers

### Data Type 1: Health & Fitness → Fitness & Workout

| Field | Answer |
|-------|--------|
| **Collected?** | Yes |
| **Linked to user?** | No |
| **Used for tracking?** | No |
| **Purposes** | App Functionality |

**What it is**: User-entered sprint times, distances, workout types (40-yard dash, time trial, ladders, etc.), surfaces (track, turf, field, etc.), timing methods, RPE (rate of perceived exertion), drill entries, stride entries, rep counts, rest intervals, and analysis results (speed scores, acceleration scores, sprint profiles, coach feedback).

**Where stored**: Locally on-device via SwiftData (`SC40Analysis.store` in Application Support). Not transmitted to any server.

**Where collected**: `ManualWorkoutView.swift` (user input), `ManualWorkoutSession.swift` (SwiftData model), `AnalysisEngine.swift` (computed scores).

---

### Data Type 2: User Content → Other User Content

| Field | Answer |
|-------|--------|
| **Collected?** | Yes |
| **Linked to user?** | No |
| **Used for tracking?** | No |
| **Purposes** | App Functionality |

**What it is**: Free-text workout notes attached to training sessions. User profile fields: name, age, sex, weight, height, sport, position. These are all manually entered by the user.

**Where stored**: Workout notes in SwiftData. Profile data in UserDefaults (`UserProfile_v2` key). Not transmitted to any server.

**Where collected**: `ManualWorkoutView.swift` (notes input), `UserProfile.swift` (profile model), `UserProfileManager.swift` (UserDefaults persistence).

---

### Data Type 3: Location → Precise Location

| Field | Answer |
|-------|--------|
| **Collected?** | Yes |
| **Linked to user?** | No |
| **Used for tracking?** | No |
| **Purposes** | App Functionality |

**What it is**: GPS coordinates (latitude, longitude) obtained via CoreLocation when the user optionally grants location permission. Used to fetch weather conditions from Open-Meteo API. Coordinates are also stored on the workout session for map display in session detail.

**Where stored**: `latitude: Double?` and `longitude: Double?` fields on `ManualWorkoutSession` in SwiftData. Weather conditions (`WeatherConditions`) and fetch timestamp also stored on session.

**Where transmitted**: Coordinates are sent to `https://api.open-meteo.com/v1/forecast` to retrieve current weather (temperature, humidity, wind speed, weather code). Location name text is sent to Apple's `CLGeocoder` for geocoding. Neither service tracks users across apps.

**Permission**: `NSLocationWhenInUseUsageDescription` — "SC40 Analysis uses your location to record the GPS coordinates of logged workouts so they can be displayed on a map." Location is optional — user can enter a location name manually instead.

**Where collected**: `SC40WeatherSection.swift` (UI), `SCWeatherService.swift` (weather fetch), `SC40LocationDelegate.swift` (CoreLocation delegate), `ManualWorkoutSession.swift` (storage).

---

### Data Types NOT Collected

| Data Type | Collected? | Notes |
|-----------|-----------|-------|
| Contact Info | No | No address book access |
| Financial Info | No | IAP handled by Apple StoreKit; app only stores `isPro` boolean |
| Sensitive Info | No | |
| Contacts | No | |
| Emails or Text Messages | No | |
| Photos or Videos | No | No camera/photo library access |
| Audio Data | No | No microphone access |
| Browsing History | No | |
| Search History | No | |
| Identifiers | No | No user IDs, device IDs, or advertising IDs |
| Diagnostics | No | No crash analytics, no performance monitoring |
| Surroundings | No | |

---

## App Store Connect — App Privacy Section (Summary)

### Data Used to Track You
None. The app does not track users across apps or websites.

### Data Linked to You
None. The app has no user accounts, login, or identity linkage. All data is stored locally on-device and is not linked to an identity.

### Data Not Linked to You
- **Health & Fitness → Fitness & Workout** — for App Functionality
- **User Content → Other User Content** — for App Functionality
- **Location → Precise Location** — for App Functionality

---

## Discrepancies Found (MUST FIX BEFORE SUBMISSION)

### 1. Privacy policy says location is NOT stored — but it IS stored
**File**: `privacy-policy.html` / `sc-analysis-privacy-policy.html`, Location Access section
**Current text**: "Your location is not stored, shared, or used for any other purpose."
**Actual behavior**: `ManualWorkoutSession` stores `latitude: Double?` and `longitude: Double?` for map display in session detail.
**Fix**: Change to "Your GPS coordinates are stored on your device with the workout session for map display. They are not shared with or sent to any server other than the one-time weather API request."

### 2. Wrong privacy policy file (`sc40-analysis-privacy-policy.html`)
**File**: `sc40-analysis-privacy-policy.html`
**Issue**: This file is titled "Strength Coach Analysis" and mentions HealthKit access, strength workouts, and `support@accel-8.com`. It appears to be a copy of the Strength Coach privacy policy, not SC40 Analysis.
**Correct file**: `privacy-policy.html` (or `sc-analysis-privacy-policy.html`) — titled "SC Analysis", correctly states no HealthKit/sensor access.
**Fix**: Delete `sc40-analysis-privacy-policy.html` or replace with correct content. Ensure the URL submitted to App Store Connect points to the correct file.

### 3. Wrong support page title (`sc40-analysis-support.html`)
**File**: `sc40-analysis-support.html`
**Issue**: Title says "Strength Coach Analysis" instead of "SC Analysis" or "SC40 Analysis".
**Fix**: Update title and content to match SC40 Analysis app.

### 4. Contact email mismatch
**Privacy policy**: `support@accel-8.com`
**TESTING_PLAN.md**: `support@sc40.app`
**Fix**: Verify which email inbox exists and update all docs to use the same address.

### 5. App name inconsistency across docs
- Xcode project display name: "40 Yards"
- Privacy policy: "SC Analysis"
- App store listing (`app-store-listing.md`): "Sprint Coach"
- TESTING_PLAN: "SC40 Analysis"
**Fix**: Decide on a single app name and update all docs consistently.

### 6. App store listing describes a different app
**File**: `app-store-listing.md`
**Issue**: ~~Describes "Sprint Coach" for 60m/100m/200m/400m sprints with £1.99/month pricing. SC40 Analysis is a 40-yard dash app. The listing mentions "14-day free trial" but the privacy policy says "1-week free trial."~~
**Status**: RESOLVED — `app-store-listing.md` has been rewritten for Sprint Coach 40 (the watch app). SC40 Analysis needs its own listing if submitted separately.

### 7. IAP capability not enabled for SC40 Analysis target
**File**: `Performance Testing.xcodeproj/project.pbxproj`
**Issue**: SC40 Analysis has `StoreManager.swift`, `PaywallView.swift`, and `SC40_Analysis_PRO.storekit` ($49.99/year), but `com.apple.InAppPurchase` capability is only enabled on the Combine Analysis target, not SC40 Analysis. IAP transactions will fail in production.
**Fix**: Either enable IAP capability on SC40 Analysis target, or remove the paywall/StoreKit code for v1 if IAP is deferred (TESTING_PLAN says "Free app, no IAP for v1").

### 8. Subscription pricing inconsistency
- `SC40_Analysis_PRO.storekit`: $49.99/year
- Privacy policy: "1-week free trial"
- App store listing: "£1.99/month with 14-day free trial" ~~(now fixed — listing updated to 1-week trial)~~
**Fix**: Align pricing across all docs and StoreKit configuration.

---

## App Store Connect Setup Checklist (from TESTING_PLAN Phase 0)

### URLs to add to App Store Connect → App Information
- **Privacy Policy URL**: `https://daibhi13.github.io/SC40-Legal/privacy-policy.html` (verify this is the correct hosted URL for `privacy-policy.html` — NOT `sc40-analysis-privacy-policy.html`)
- **Terms of Service URL**: `https://daibhi13.github.io/SC40-Legal/terms-of-service.html` (verify `sc40-terms-of-service.html` is the right file)
- **Support URL**: `https://daibhi13.github.io/SC40-Legal/` (verify `sc40-analysis-support.html` is served, or use `index.html`)

### App Store Connect → App Privacy
1. Answer "Yes" to "Does this app collect data?"
2. Declare the three data types above (Fitness & Workout, Other User Content, Precise Location)
3. Set all three as "Not Linked to User" and "Not Used for Tracking"
4. Set purpose = "App Functionality" for all three
5. Answer "No" to "Does this app use data to track users?"

### App Store Connect → App Information
- **Category**: Health & Fitness (primary), Sports (secondary if available)
- **Sub-category**: `public.app-category.sports` (already set in build settings)
- **Age Rating**: 4+ (no objectionable content, no unrestricted web access, no gambling)
- **Copyright**: © 2026 David O'Connell (or Accelerate — verify legal entity name)
- **Bundle ID**: `Accelerate.SC40-Analysis`

### App Store Connect → Screenshots
Required device sizes (3-10 screenshots each):
- **6.7"** (iPhone 17 Pro Max / 15 Pro Max) — required
- **6.5"** (iPhone 11 Pro Max / 13 Pro Max) — required (or 6.1" if using newer sizes)
- **5.5"** (iPhone 8 Plus) — required if supporting older display sizes

Suggested screenshots:
1. Onboarding welcome screen
2. Home dashboard with PB display
3. Manual workout entry form
4. Workout history timeline
5. Analysis charts (with data)
6. 40 Yard Smart education content
7. Share Performance report image
8. Settings / profile screen

### App Store Connect → App Review Information
- **Demo instructions**: App has no login. Reviewer completes onboarding (enter name, PB, demographics, accept safety warning), logs a workout (enter sprint distance + time), checks History and Analysis tabs.
- **Review notes**: This is a manual entry app — no GPS tracking, no sensors, no HealthKit. All data is user-entered. Location is optional for weather only.
