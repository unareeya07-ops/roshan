# SOH Style Scanner — Android APK via GitHub

This project packages the SOH barcode/style lookup app as an Android app using Capacitor. It includes inventory data extracted from the supplied `1510.xlsx`.

## What the app does
- Search by barcode, style code or style name.
- Shows colour, size and SOH for a matching product/style.
- Uses the phone camera for barcode scanning where the browser/WebView supports `BarcodeDetector`.
- Administrator section imports an updated Excel/CSV inventory.
- Sold form deducts a manually entered quantity for a style + colour + size.
- Export current inventory as CSV.

## Build the APK using GitHub (no Android Studio required)

1. Sign in at https://github.com and create a **new empty repository**, e.g. `soh-style-scanner`. Do not add a README or license during creation.
2. Unzip this project on your computer.
3. Open the new repository page and choose **Add file → Upload files**. Drag all files and folders from the unzipped project into the page, including the `.github` folder. Commit to the `main` branch.
   - Alternatively, use GitHub Desktop to add the unzipped folder as a repository and push it.
4. In the GitHub repository, open **Actions**. If prompted, enable Actions.
5. Choose **Build Android APK** in the workflow list, click **Run workflow**, then click the green **Run workflow** button.
6. Wait until the run finishes successfully. Open that workflow run, scroll to **Artifacts**, and download `SOH-Style-Scanner-debug-apk`.
7. Unzip the artifact; it contains `app-debug.apk`. Transfer the APK to your Android phone and open it to install. You may need to allow your browser/file manager to **Install unknown apps** for this one-time install.

The workflow also runs automatically on pushes to `main`.

## Important notes
- This is a **debug APK** for testing, not a Play Store release. Do not share it as a trusted production app.
- Camera scanning depends on Android WebView support. If scan is unsupported, use manual barcode entry. A future enhancement can add a native barcode scanner plugin for more reliable scanning.
- Excel upload supports `.xlsx`/`.xls` via SheetJS loaded from a CDN, so internet is needed for Excel import. CSV import is built in.
- Inventory and sold changes are in memory only; export CSV before closing the app. They are not synced across devices or saved permanently. A production version should add local persistent storage and ideally authenticated backend sync.
- The included inventory is derived from `1510.xlsx`: column E = barcode, D = item description, H = style code, I = colour, J = size, M = closing stock. Please verify those column mappings against your current stock report before relying on it.


### App icon and header spacing update
The project includes `assets/icon.png` for the Android launcher and `www/icon.png` for the in-app header. The GitHub Actions workflow applies the icon to Android launcher resources and the app header includes safe-area top spacing with a shorter banner.
