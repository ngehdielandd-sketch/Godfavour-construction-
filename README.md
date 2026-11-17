# GODFAVOUR Construction Management — v2

A mobile-first construction operations app designed for Android phones and desktop browsers. The app stores records locally on the device and supports offline use after the first successful load.

## Included modules
- Dashboard, projects and client records
- Itemized BOQ and estimates with automatic totals and print-to-PDF
- Work-section BOQ checklists for foundations, columns, beams, slabs and roofing (quantities and rates must be entered and verified by the user)
- Material rate and stock register
- Labour payment register
- Expense register and project reports / CSV export
- Supplier directory
- Purchase orders with pending / delivered status
- Daily site diary (weather, workforce, activities, delays and instructions)
- JSON backup and restore
- FCFA defaults and editable company profile
- Offline service-worker cache and Android-friendly responsive interface

## Important data and engineering limitations
- Records are stored in browser local storage on the current device. There is no cloud sync, server database, multi-user access control, or automatic cross-device backup.
- Export JSON backups regularly and store a copy somewhere separate from the phone.
- The starter material rates are editable examples, not live market quotations.
- BOQ checklists are estimating aids, not structural designs. They do not determine safe member sizes, reinforcement, soil bearing capacity, or code compliance. A qualified engineer must verify structural designs and quantities before construction.
- This app is an operational estimating/record-keeping tool, not payroll, tax, accounting, or regulatory software.

## Run in a browser
Serve this folder over HTTPS or localhost (service workers require a secure context):

```bash
python -m http.server 8000
```

Open `http://localhost:8000`.

## Install immediately on Android without an APK
1. Host this folder on an HTTPS web host.
2. Open the HTTPS address in Chrome on Android.
3. Open Chrome's menu and choose **Install app** or **Add to Home screen**.
4. Open GODFAVOUR from the home screen. The app shell is cached for offline use after the first successful load.

## Build a native Android APK with Capacitor
This project includes Capacitor configuration, but the APK has not been compiled or signed in this delivery environment. A native APK build requires Android Studio / Android SDK, Gradle, and a signing key for release distribution.

On a computer with Node.js and Android Studio installed:

```bash
npm install
npm run android:add       # first time only; creates the android/ project
npm run android:open
```

In Android Studio, allow Gradle sync, connect an Android device or start an emulator, then use **Build → Build Bundle(s) / APK(s) → Build APK(s)** for a test APK. For a distributable release, use **Build → Generate Signed Bundle / APK** and securely keep the keystore and passwords. Do not share the keystore publicly.

Package ID: `com.godfavourconstruction.app`

## Optional cloud APK build (GitHub Actions)
The `.github/workflows/android-apk.yml` workflow builds a debug APK in GitHub Actions when manually started or when code is pushed to `main`. Upload this project to a GitHub repository, open **Actions → Build Android APK → Run workflow**, wait for the job to finish, then download the `godfavour-construction-debug-apk` artifact. GitHub account access and an internet connection are required. This produces a debug/test APK; a signed release APK still needs a private signing keystore and release configuration.
