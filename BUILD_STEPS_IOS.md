# Build and ship to the Apple App Store

## One-time setup
1. A Mac with Xcode (free from the Mac App Store).
2. Apple Developer Program membership, $99/year: https://developer.apple.com/programs/
3. In `capacitor.config.json`, set `appId` to your own bundle ID (e.g. `com.janedoe.pottymouth`). Use the same one on Android. It can't change after publishing.

## Build the iOS app
```
npm install
npx cap add ios
npx capacitor-assets generate --ios
npx cap sync ios
npx cap open ios
```
In Xcode:
1. Click the **App** target > **Signing & Capabilities**, tick "Automatically manage signing", pick your Team.
2. In **Info** (Info.plist) add `ITSAppUsesNonExemptEncryption` = `NO` (the app uses no custom encryption; this skips the export-compliance prompt).
3. Set the version to 1.0 and build to 1.
4. Pick "Any iOS Device (arm64)", then **Product > Archive**.
5. In the Organizer: **Distribute App > App Store Connect > Upload**.

## App Store Connect (https://appstoreconnect.apple.com)
1. My Apps > + > New App. Use your bundle ID, name "Potty Mouth Songwriter".
2. Paste text from `store/APP_STORE_LISTING.md`.
3. Upload `store/appstore-icon-1024.png` only if asked (Xcode already includes it).
4. Add screenshots (see the listing file for sizes). Run the app in the Xcode simulator and press Cmd+S to save them.
5. Host `store/privacy-policy.html` publicly (GitHub Pages is free), put your email in it, and paste the URL.
6. Fill in App Privacy and Age Rating using the answers in the listing file.
7. Select the uploaded build, then **Submit for Review**.

## Review tips
- Apple can reject apps that are "just a website in a wrapper" (Guideline 4.2). This one has real built-in functionality, works offline, and has no external links. In the review notes, say that it is an offline song generator with its own content.
- Keep the age rating honest. Under-rating profanity is a common rejection reason.
