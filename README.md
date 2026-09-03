# Crimsonland_Blood_Shift - repo cleanup and release instructions

This branch prepares the repository for safer distribution of APK assets and documents how to remove large binary files from the repository history.

Summary of changes on this branch:
- Documentation and instructions for verifying and installing the APK
- Placeholder for a sha256 checksum file for the APK (compute locally and commit)
- .gitattributes to mark APKs as binary (recommend Git LFS for large binaries)
- .gitignore with common Android ignores

What I will do in this branch (now):
- Add README.md (you are reading it)
- Add Crimsonland_Blood_Shift_INSTALLABLE.apk.sha256 (placeholder)
- Add .gitattributes and .gitignore

Recommended next steps (choose one):
1) Safe path (no history rewrite) — merge this branch into main. The APK will remain in Git history but will be removed from the working tree (I'll remove it from the tree in a follow-up commit if you want). Then create a GitHub Release and attach the APK as a Release asset (preferable for distribution).

2) Full clean (destructive) — rewrite history to remove the APK blob from all commits using `git filter-repo` or BFG, then force-push. This reduces repo size but requires all collaborators to re-clone or follow recovery steps. If you want me to proceed with this, confirm explicitly and I will prepare the rewrite instructions and (if you allow) perform it.

How to verify and install the APK locally (recommended):

1) Download the APK from the repository (or from a Release asset if you choose to upload it there).
2) Generate and verify the checksum locally:

   sha256sum Crimsonland_Blood_Shift_INSTALLABLE.apk > Crimsonland_Blood_Shift_INSTALLABLE.apk.sha256
   # Compare output with the checked-in .sha256 file (or the one I provide)

3) Install on Android device via adb:

   adb install -r Crimsonland_Blood_Shift_INSTALLABLE.apk

4) Verify APK signature (optional):

   apksigner verify --verbose Crimsonland_Blood_Shift_INSTALLABLE.apk

How to remove the APK from repository history (if you want the destructive option)

1) Using git-filter-repo (recommended):

   # Make a local clone of the repository (do NOT run this in the remote GitHub web editor)
   git clone --mirror https://github.com/xelnarek2-sys/Xelnarek2.gra.git
   cd Xelnarek2.gra.git

   # Remove the file path from all history
   git filter-repo --invert-paths --paths "Crimsonland_Blood_Shift_INSTALLABLE.apk"

   # Push the rewritten history (this is destructive for all clones)
   git push --force origin refs/heads/main

   # Notify all collaborators that they must re-clone or reset their local clones.

2) Using BFG Repo-Cleaner (alternative):

   # See BFG README: https://rtyley.github.io/bfg-repo-cleaner/

Important warnings about rewriting history
- This is destructive and will change commit SHAs. All forks and clones will diverge and users will need to rebase or re-clone.
- I will perform it only after you explicitly confirm you want the history rewritten and you accept the consequences.

If you want, I can also create a Draft GitHub Release and attach the APK there (keeps repo tree clean). Reply:
- "bezpiecznie" — do safe changes and open PR only (default)
- "usuń-historię" — proceed with destructive rewrite and force-push (I will still explain steps and require a final confirmation before force-pushing)
- "release-tak" or "release-nie" to indicate whether I should create a Draft Release with the APK asset now.

