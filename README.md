# Ledger — Android App

Ye ek Android project hai jo aapki website
`https://ledger-eight-rouge.vercel.app/` ko app ke andar (WebView) load karta
hai — bilkul native app ki tarah, sath hi login sessionStorage/localStorage bhi
kaam karega.

## GitHub par APK banayein (Android Studio ki zaroorat nahi)

Is project mein ek **GitHub Actions workflow** shamil hai
(`.github/workflows/build-apk.yml`) jo har push par khud APK bana deta hai.

1. GitHub par ek naya repository banayein (public ya private, dono chalenge).
2. Is `LedgerApp` folder ka poora content us repo mein push kar dein:
   ```bash
   cd LedgerApp
   git init
   git add .
   git commit -m "Ledger android app"
   git branch -M main
   git remote add origin https://github.com/<aapka-username>/<repo-name>.git
   git push -u origin main
   ```
   (Ya GitHub website par "Add file → Upload files" se sabhi files/folders
   drag-drop kar dein — `.github` folder ko bhi zaroor upload karein.)
3. Repo ke **Actions** tab par jayein — "Build APK" workflow khud chal jayega
   (1-2 minute lagte hain).
4. Workflow run complete hone par us run ko kholein, neeche **Artifacts**
   section mein `ledger-app-debug` milega — download kar lein.
5. Download ki gayi zip ke andar `app-debug.apk` hai — ye file seedha phone
   par install ho sakti hai (Settings → allow install from unknown sources).

Agar workflow chalane ke liye khud se trigger karna ho: Actions tab →
"Build APK" → **Run workflow** button.

## Local Android Studio se build karna ho (optional)

1. Android Studio install karein: https://developer.android.com/studio
2. **File → Open** se `LedgerApp` folder kholein.
3. "Gradle wrapper not found" prompt par **OK / Use bundled Gradle** karein.
4. Sync hone dein, phir **Run ▶** ya **Build → Build APK(s)**.

## App ka logo

Simple blue "L" icon generate kiya gaya hai. Logo change karna ho to
`app/src/main/res/mipmap-*` folders mein PNG files replace kar dein
(har density folder mein `ic_launcher.png` aur `ic_launcher_round.png`).

## Site URL change karni ho

`app/src/main/java/com/ledger/app/MainActivity.kt` mein `siteUrl` variable
edit karein.

## Features

- Full screen WebView
- JavaScript + localStorage / sessionStorage support (login kaam karega)
- Cookies enabled
- Progress bar while loading
- Back button previous page pe jata hai
- Hardware acceleration

## Note

- App sirf internet connection ke sath chalegi (offline nahi), kyunke ye
  aapki live website load karta hai.
