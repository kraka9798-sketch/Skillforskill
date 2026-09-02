# Skill for Skill — Android APK Project

Ye project Android phone se APK banane ke liye prepare kiya gaya hai.

## Sabse easy method: GitHub + GitHub Actions (phone se)

Agar aapke paas sirf Android phone hai, to Android Studio install karna zaroori nahi hai. GitHub ke cloud runner par APK build kar sakte hain.

### 1. GitHub account
1. Phone ke browser mein GitHub open karein: https://github.com/
2. Sign in karein ya free account banayein.
3. **New repository** banayein, example naam: `SkillForSkill`.

### 2. Project upload karein
1. Is project ke saare files/folders repository mein upload karein.
2. Repository ke root mein `settings.gradle`, `build.gradle` aur `app/` folder directly hone chahiye.
3. GitHub website par **Add file → Upload files** se upload kiya ja sakta hai.

### 3. GitHub Actions workflow add karein
Repository mein ye file banayein:

`.github/workflows/build-apk.yml`

Is file ka purpose Android project ko cloud runner par build karna hai. Agar workflow file is ZIP mein already di gayi ho, to manually dobara banane ki zaroorat nahi.

### 4. Build start karein
1. GitHub repository mein **Actions** tab kholein.
2. `Build Android APK` workflow select karein.
3. **Run workflow** dabayein, agar manual trigger enabled hai.
4. Build complete hone tak wait karein.

### 5. APK phone mein download karein
1. Successful workflow run open karein.
2. Neeche **Artifacts** section mein `skill-for-skill-debug-apk` jaisa artifact milega.
3. Artifact download karein.
4. ZIP extract karke `app-debug.apk` phone mein open karein.
5. Android permission maange to browser/file manager ke liye **Install unknown apps** allow karein.
6. APK install karein.

## Alternative: Android phone par local build

Agar aap Termux jaise Android development environment use karna chahte hain, to Java/Gradle/Android SDK setup karna padega. Ye method comparatively difficult hai aur phone storage/RAM zyada use karta hai. Cloud build recommended hai.

## APK kahan milega?

Local Android Studio build ke baad:

`app/build/outputs/apk/debug/app-debug.apk`

GitHub Actions build ke baad APK workflow ke **Artifacts** section mein milega.

## Important: online login/chat

Is basic Android wrapper mein local WebView frontend bundled hai. Real multi-user login/chat ke liye online backend deploy karke frontend mein HTTPS API URL configure karna hoga. Backend URL ko code mein hard-code karne se pehle production HTTPS endpoint use karein.

## Release APK

Testing ke liye `debug APK` theek hai. Public distribution/Play Store ke liye signed `release APK/AAB`, secure secrets, HTTPS, database backups, rate limiting, password reset/email verification aur moderation controls add karna chahiye.

## Phone-only recommended flow

**Phone → GitHub repository → GitHub Actions → APK artifact → Download → Install**

Aapko build karne ke liye PC ki zaroorat nahi padegi, agar repository aur cloud workflow correctly configured hain.
