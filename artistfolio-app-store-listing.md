# ArtistFolio — App Store Listing

## App Name
ArtistFolio

## Subtitle (30 chars max)
Artist Portfolio & Enquiries

## Category
Business (as set in the project — LSApplicationCategoryType)

## Keywords (100 chars max, comma-separated)
artist,portfolio,art gallery,artwork,exhibition,QR code,enquiries,commissions,art sales,painter

## Age Rating
4+ — No objectionable content

## Copyright
© 2026 David O'Connell

---

## Promotional Text (170 chars max)
Your gallery in your pocket. Show your work, print QR codes for exhibitions, track offers and enquiries, and grow your own audience — all private on your device.

---

## App Description (4000 chars max)

ArtistFolio is a portfolio and enquiry tool built for independent artists. Carry a polished catalogue of your work, capture interest at exhibitions with QR codes, manage offers and commissions, and grow your own subscriber list — privately, on your own devices.

Made for artists who sell directly: no public marketplace, no commission fees, no accounts for your buyers to create.

FEATURES

• Portfolio
Your bio, photo and featured work on a beautiful home page. A browsable gallery with series, size and availability filters, and rich artwork pages with image carousels, dimensions, medium, year and the story behind each piece.

• Exhibition QR codes
Generate print-ready QR labels for wall tags, business cards and table cards. Codes can open a pre-filled email or text message to you, a WhatsApp chat, your contact card, or any link — no website required.

• Offers & enquiries
Buyers make offers and send enquiries in seconds. Your private inbox tracks each conversation: new, replied, in progress, sold, closed. Call, text or WhatsApp enquirers directly when they leave a number.

• Commissions
A dedicated commissions page explains your process — discuss scope, written quote per job, deposit, collection or on-site installation including walls and murals.

• Audience building
Sign-up forms capture emails and mobile numbers with proper consent records (UK GDPR/PECR friendly). Announcements reach your subscriber list from your own Mail app, or copy the text for a WhatsApp broadcast.

• Private dashboard
Gated behind Face ID or your device passcode — hidden completely from anyone browsing your portfolio. Manage artworks, see engagement stats, export your subscriber list to CSV, and share your contact card.

• Syncs across your devices
Your data lives on your device and syncs between your iPhone, iPad and Mac via your private iCloud account. Nothing is sent to us — no servers, no tracking, no third-party analytics.

WHY ARTISTFOLIO?

• Built for offer-led selling — show "Make an offer" instead of public prices, with private guide prices to help you judge
• QR codes that work today — email, text, WhatsApp and contact-card codes need no backend
• Buyer-friendly — no app or account needed for visitors to enquire (web pages coming soon)
• Your data stays yours — on-device and private iCloud only

Terms of Service: https://daibhi13.github.io/SC40-Legal/shared-terms-of-service.html
Privacy Policy: https://daibhi13.github.io/SC40-Legal/artistfolio-privacy-policy.html

---

## What's New (Release Notes)

Version 1.0 — Initial release.

---

## Support URL
https://daibhi13.github.io/SC40-Legal/artistfolio-support.html

## Privacy Policy URL
https://daibhi13.github.io/SC40-Legal/artistfolio-privacy-policy.html

## Terms of Service URL
https://daibhi13.github.io/SC40-Legal/shared-terms-of-service.html

---

## App Review Information

### Review Notes
ArtistFolio is a portfolio and enquiry tool for independent artists. IMPORTANT — hidden functionality disclosure:

The artist dashboard is intentionally hidden from visitors sharing the device. To reveal it: long-press (or triple-tap) the artist's name on the Home tab, or press ⌘⇧D on Mac, then authenticate with the device passcode or Face ID/Touch ID. The Dashboard tab then appears. This is a deliberate privacy feature, not a defect.

On devices that chose "I'm visiting" at onboarding, the same hidden triggers open an artist sign-in sheet instead of device auth (a visitor can't pass device auth anyway). The sheet offers "I own this device — sign in", which runs device-owner authentication so the device owner can switch to artist mode. No in-app purchase exists in this build.

A fresh install starts empty by design. To set up: unlock the dashboard as above → Artist profile → "Create artist profile". For review convenience, a build with sample data is available on request.

The app uses:
- LocalAuthentication for the dashboard gate (device owner auth — passcode or biometrics)
- iCloud/CloudKit for private sync between the artist's own devices (requires iCloud sign-in)
- Photos picker for artwork images
- Local notifications for optional exhibition announcement reminders
- Share sheets for QR PNGs, contact cards (.vcf) and subscriber CSV export
- mailto: for announcements and enquiry contact — no data leaves the device otherwise

There is no login system, no servers operated by us, and no third-party SDKs or analytics.

### Demo Instructions
1. Launch the app — Home shows the artist profile, featured work and a sign-up card.
2. Long-press the artist's name at the top of Home and authenticate to reveal the Dashboard tab.
3. Dashboard: view stat tiles, browse Artworks, Enquiries, Subscribers, QR codes, Announcements, Artist profile.
4. In Gallery, long-press an artwork card for edit/status/archive controls (visible only while unlocked).
5. Dashboard → QR codes → create a code (email, text, WhatsApp, contact card or link) and share the PNG.
6. Lock the dashboard via "Lock dashboard" at the bottom — the tab disappears.

### Contact Information
Email: support@accel-8.com

---

## App Store Connect Privacy Details

### Data Types Collected
**None.** All data stays on the user's device and their private iCloud account — the developer receives nothing.

If Apple asks about contact data entered in enquiry/sign-up forms: it is provided by the user, stored on the artist's device only, never transmitted to the developer, not linked to identity, not used for tracking.

### Tracking
No — no third-party trackers, no advertising identifiers.

### Privacy manifest
`PrivacyInfo.xcprivacy` ships in the bundle: tracking = No, collected types =
none, accessed API = UserDefaults (reason CA92.1 — the `userRole` preference).

### Third-Party SDKs
None — the app uses only Apple frameworks (SwiftUI, SwiftData, CloudKit, LocalAuthentication, PhotosUI, UserNotifications).

---

## Content Rights (App Store Connect)

### Copyright
© 2026 David O'Connell

### Third-Party Content
No — all content is original. Sample artwork seed data is fictional and debug-only; release installs ship empty.

### Age Rating Content Descriptors
All set to "None".

**Resulting Age Rating**: 4+

### Export Compliance
- Standard Apple encryption only (CloudKit sync, HTTPS for links).
- ITSAppUsesNonExemptEncryption: answer "standard/exempt" — no custom encryption.

---

## Screenshots

### Required Size
Upload one set for **6.9"** (iPhone 16 Pro Max, 1320 × 2868). Apple auto-scales to other iPhone sizes. iPad set needed too — the app supports iPad.

### Suggested Screenshot Plan (10 max)
1. Home — artist bio, photo, featured work carousel
2. Gallery — artwork grid with filters
3. Artwork detail — images, story, "Make an offer"
4. Commissions page
5. Dashboard overview — stat tiles
6. Enquiries inbox
7. QR studio — code preview + share
8. Subscriber list
9. Announcement composer
10. iPad/Mac split-view dashboard

---

## Pricing
Free — **no In-App Purchases** in this build.

(Planned, not yet shipped: an "Artist Pro" auto-renewable subscription —
`artistfolio.artist.monthly` / `artistfolio.artist.yearly` — to convert
visitor installs into artists. The local `ArtistFolio.storekit` config is
still in the repo for when ASC products are created. Do not re-add the
purchase flow until those products exist in App Store Connect.)
