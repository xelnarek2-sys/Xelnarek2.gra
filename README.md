# Crimsonland_Blood_Shift - APK distribution and install instructions

This repository contains the Crimsonland Blood Shift APK. To play, download the APK from the repository and install it on your Android device.

Important files in this repository:
- Crimsonland_Blood_Shift_INSTALLABLE.apk — the APK binary (stored in the repo tree). If this file is large, consider downloading it from Releases instead.
- Crimsonland_Blood_Shift_INSTALLABLE.apk.sha256 — SHA-256 checksum file (placeholder). Verify the checksum before installing.

How to verify and install the APK
1) Download the APK from the repository (or from Releases if available).

2) Verify the checksum locally (replace the filename if needed):

   sha256sum Crimsonland_Blood_Shift_INSTALLABLE.apk > Crimsonland_Blood_Shift_INSTALLABLE.apk.sha256
   # Compare the generated checksum with the one in the checked-in .sha256 file (if present)

3) Install on your Android device via ADB:

   adb install -r Crimsonland_Blood_Shift_INSTALLABLE.apk

4) (Optional) Verify APK signature using apksigner (Android SDK build-tools):

   apksigner verify --verbose Crimsonland_Blood_Shift_INSTALLABLE.apk

Notes and recommendations
- For long-term distribution it's recommended to attach the APK to a GitHub Release instead of keeping large binaries in the repo tree. If you want, I can help create a Release and upload the APK there.
- If you'd like me to automatically remove the APK from history to shrink the repo size, confirm explicitly — that operation rewrites history and requires force-push.

