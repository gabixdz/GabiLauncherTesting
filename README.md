# gabi home — android launcher

a real android home launcher. your HTML runs in a fullscreen WebView and can
launch actual apps on the device.

## setup

1. download and install **android studio** (free)
   https://developer.android.com/studio

2. open android studio → File → Open → select the `GabiLauncher` folder

3. let it sync (downloads gradle, might take a few minutes first time)

4. plug in your android phone via USB
   - enable developer mode: settings → about phone → tap build number 7 times
   - enable USB debugging: settings → developer options → USB debugging

5. hit the green ▶ Run button in android studio

6. on your phone, press the home button
   - android will ask "select a home app" → pick **gabi home**
   - tap "always" to make it the default

## how it works

```
home.html          ← your UI (edit this freely)
     ↕ JavaScript bridge
LauncherActivity.kt ← thin native wrapper
     ↕
Android OS         ← real app list, real launching
```

## editing the UI

just edit `app/src/main/assets/home.html` and re-run.
no kotlin knowledge needed.

## Android bridge calls available in JS

```javascript
Android.launchApp("com.spotify.music")   // open any app by package name
Android.openSettings()                   // open android settings
Android.vibrate(30)                      // haptic feedback (ms)
Android.getInstalledAppsJson()           // returns JSON string of all apps
```
