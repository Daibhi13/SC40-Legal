# Strength Coach Analysis — App Review Notes

Paste the contents below into **App Store Connect > App Review Information > Notes**.

---

## 1. Screen recording
A screen recording captured on a physical device is attached. It demonstrates:
- Launching the app for the first time
- Completing the onboarding flow (user name, unit preference, notification permission)
- Creating a new strength-training session
- Adding exercises, sets, reps, and weight
- Viewing the session summary
- Tapping the Pro feature to open the paywall
- The subscription flow (price, trial, terms/privacy links, purchase, restore)
- Restoring purchases

## 2. Tested devices and operating systems
- iPhone [DEVICE MODEL], iOS [VERSION] (primary test device)
- iPhone [DEVICE MODEL], iOS [VERSION] (secondary test device)

*Please replace the bracketed placeholders above with the actual device models and iOS versions used for testing.*

## 3. App purpose and target audience
**Strength Coach Analysis** is a strength-and-conditioning tracking tool for athletes, coaches, and personal trainers who want to log, analyse, and improve resistance-training performance.

The app solves the problem of fragmented workout logging by letting users record exercises, sets, reps, weight, and rest times in one place. It then provides analysis cards, training history, and trend views to help users monitor progress and make informed programming decisions.

## 4. How to access the main features
No account registration or login is required. To use the app:
1. Launch the app and complete the short onboarding flow.
2. Tap **New Session** to create a workout.
3. Add exercises from the built-in library, then record sets, reps, and weight.
4. Save the session.
5. View recent sessions from the **Home** tab.
6. View training history from the **History** tab.
7. View trends and analytics from the **Trends** tab (Pro feature).

To experience the paywall/subscription flow:
- Tap **More** > **Strength Coach Pro Active** row, or
- Tap any Pro-gated feature such as **Trends**.

## 5. External services and frameworks
- **StoreKit** — used to display the auto-renewable subscription product, process purchases, restore purchases, and verify entitlements.
- **SwiftData** — local persistence for workouts, exercises, sessions, and user profile.
- **HealthKit** — optional integration to read/write workout data if the user grants permission.
- **UserNotifications** — used only if the user opts in, to schedule workout reminders and trial reminders.
- No third-party authentication, payment processors, AI/ML services, or advertising SDKs are used.

## 6. Regional differences
The app functions identically in all regions. There are no region-locked features, localised content differences, or region-specific pricing beyond Apple’s localised App Store pricing.

## 7. Regulated content or protected material
The app does not operate in a regulated industry and does not include any protected third-party material. All content, exercise data, and analysis logic are built in-house.

## Additional information
- **Login credentials:** Not required; the app has no account system.
- **Demo account:** Not applicable.
- **Subscription:** The auto-renewable subscription title, price, length, and Terms of Use / Privacy Policy links are clearly shown on the paywall screen.
- **Purpose strings:** All required Info.plist usage strings (HealthKit, notifications, etc.) are present and describe why the permission is requested.
- **EULA and privacy policy:** The paywall links to the EULA and privacy policy documents included with the app submission.
