# Desert & Drinks POS releases

Update feed and APK downloads for the Desert & Drinks POS app (it isn't on any store).

- `appcast.xml` is read by the app on launch and whenever it comes back to the
  foreground. When it lists a version newer than the installed one, the app
  shows an update popup that downloads the new APK.
- Each version's APK is attached to the matching GitHub release (`v1.2.3`).

## Publishing a version

From the app project:

1. Bump `version:` in `pubspec.yaml`. Raise both the name and the build number
   (e.g. `1.0.0+1` -> `1.0.1+2`). The app compares the name; Android needs a
   higher build number to install over the old APK.
2. Run `tool/release.sh "release notes"` (add `--critical` to force the update:
   the popup then has no Later / Ignore buttons).

The script builds the release APK, creates the GitHub release and adds the
version to `appcast.xml`.
