Hundred Masks - app kit for iPhone, iPad, Android phones, tablets and foldables

SET UP (once)
1. Make a free GitHub account, then a new PUBLIC repository (free GitHub Pages, which delivers the
   over-the-air updates, only works on public repositories).
2. In the repository: Settings > Pages > Build and deployment > Source: "GitHub Actions".
3. Android signing key: Settings > Secrets and variables > Actions > New repository secret, twice:
     ANDROID_KEYSTORE      = the whole text of ANDROID_KEYSTORE.base64.txt
     ANDROID_KEY_PASSWORD  = the text of ANDROID_KEY_PASSWORD.txt
   (both files are in C:\Users\A2\HundredMasks-signing - never upload those files themselves, keep a backup:
   every Android update must be signed with this same key or phones refuse to install it over the old app).
4. Click "uploading an existing file" and drag in EVERYTHING in this folder, including the .github and story-voice folders
   (if it gets left out: "Add file > Create new file", type the path, e.g. .github/workflows/build-android.yml,
   and paste that file's contents; do this for all three files in .github/workflows).
5. Open the Actions tab. Three runs start by themselves: "Build iPhone and iPad app", "Build Android app" and
   "Publish game update". The app builds take ~10 minutes each.

ANDROID (phones, tablets, foldables)
6. Open the finished "Build Android app" run and download HundredMasks-android. It holds:
     HundredMasks.apk  install this on the phone or tablet
     HundredMasks.aab  only for publishing on Google Play (Play Console > Create app > upload it)
7. Copy HundredMasks.apk to the device (or download it there), open it and allow "Install unknown apps" for the
   app you opened it with when Android asks. Android 6.0 and newer; the game fills tablets and unfolded
   foldables and re-fits when you fold, unfold or use split screen. The Back button closes windows, opens the
   pause menu in battle and returns to the Cove; on the Cove it puts the game in the background.
   (Without the signing secrets the run makes HundredMasks-debug.apk instead: fine to try the game, but a later
   signed build cannot install over it without uninstalling first, which deletes the save.)

IPHONE AND IPAD (and the iPhone Duo)
8. Open the finished "Build iPhone and iPad app" run and download HundredMasks-ipa (a zip holding HundredMasks.ipa).
9. On your PC install Sideloadly (sideloadly.io) and iTunes (from apple.com, not the Microsoft Store), plug in the
   iPhone or iPad, drag the .ipa into Sideloadly, enter your Apple ID and press Start.
10. On the device: Settings > General > VPN & Device Management > trust your Apple ID.
    (iOS 16+: also Settings > Privacy & Security > Developer Mode > On, then restart.)
With a free Apple ID the app must be re-signed every 7 days: just run Sideloadly again (your save is kept).

REMINDERS (both apps)
The app asks once, the first time a Wildface sets sail on an expedition, whether it may send notifications. If you
allow it, it reminds you when an expedition is home, when stamina is full, and when the Daily Treasure arrives.

UPDATES OVER THE AIR (both apps)
When the game changes you get new www.zip.001, .002, ... and version.json. Upload just those files to the repository
(replace the old ones). The update goes live in a few minutes; the apps download it the next time they open and
install it the time after that. No reinstalling needed for game updates.
