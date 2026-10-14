# Mealwise: deploy and publish guide

Mealwise is a free, offline-capable calorie and macro tracker. It is one web app, so the same files
go to Netlify, Google Play and the Apple stores.

## 1. Put it online with Netlify (free, about 2 minutes)
1. Unzip `mealwise.zip` so you have a folder named `mealwise`.
2. Go to https://app.netlify.com/drop (free account needed).
3. Drag the whole `mealwise` folder onto the page.
4. Netlify gives you an https link. Open it on your phone and Mac to test.

Rename the app: search for `Mealwise` in `index.html`, `manifest.webmanifest` and this file.
After any change, bump `CACHE = 'mealwise-v1'` in `sw.js` (to v2, v3...) and re-upload, so installed copies update.

## 2. Install without any store (free)
- Android Chrome: menu, Install app.
- Mac Safari: File, Add to Dock. Chrome/Edge: install icon in the address bar.
- iPhone Safari: Share, Add to Home Screen.

## 3. Google Play Store
Needs a Google Play developer account (one-time fee, currently about 25 USD). Steps:
1. Finish step 1 so you have a public https link.
2. Go to https://www.pwabuilder.com, paste your Netlify link, and choose the Android package.
3. Download the package, keep the signing key it gives you somewhere safe, and upload the .aab file in Play Console.
4. Fill in the store listing, privacy policy (say all data stays on the device; online food search sends only your search text to Open Food Facts; optional AI sends meals/photos to Google using the user's own key), and the Health apps declaration.
Check Google's current rules for new personal accounts: they have required a period of closed testing with a minimum number of testers before production release.

## 4. Mac App Store / Apple stores
Needs the Apple Developer Program (currently 99 USD per year) and a Mac with Xcode. PWABuilder can generate an Apple
project from your link, but check what it currently supports for macOS. Apple can reject apps that are only a
repackaged website (Guideline 4.2), so expect to add something native-feeling, and a privacy policy and support URL are required.
The free Add to Dock route in step 2 gives Mac users an app icon today without the store.

## 5. Optional AI photo logging
In the app: Settings, paste a Google Gemini API key (from Google AI Studio). The key stays on the device.
If Google renames the model, change the model name in Settings.

## Data
Everything is stored in the browser on each device. Use Settings, Export backup, to move data between devices.
