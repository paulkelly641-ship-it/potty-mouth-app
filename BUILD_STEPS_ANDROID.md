# Build and ship to Google Play

## One-time setup
1. Google Play Console account (one-time $25 fee): https://play.google.com/console
2. Install Node 18+, JDK 17, and Android Studio.
3. In `capacitor.config.json`, change `appId` to your own (e.g. `com.janedoe.pottymouth`). It can never change after you publish.

## Build the Android app
```
npm install
npx cap add android
npx capacitor-assets generate --android
npx cap sync android
npx cap open android
```
In Android Studio: **Build > Generate Signed App Bundle / APK > Android App Bundle**.
Create a new keystore, and BACK IT UP somewhere safe (lose it = can't update the app).
Choose the `release` build. You get an `.aab` file.

## Publish
1. Play Console > Create app > Potty Mouth Songwriter, free app.
2. Paste text from `store/PLAY_STORE_LISTING.md`.
3. Upload `store/icon-512.png` and `store/feature-graphic-1024x500.png`.
4. Add at least 2 phone screenshots (run the app on a phone/emulator and screenshot it).
5. Host `store/privacy-policy.html` somewhere public (GitHub Pages is free) and paste the URL. Put your email in it first.
6. Fill in the content rating and Data safety forms using the answers in `STORE_LISTING.md`.
7. Upload the `.aab` and submit.

Note: new personal developer accounts have usually had to run a closed test with a set number of testers for about 14 days before going to production. Check the Play Console for the current requirement.
