# APK বিল্ড গাইড (বাংলা)

এই গাইডটি আপনাকে অটো এবং ম্যানুয়াল APK বিল্ড করার উপায় দেখাবে।

## 📋 প্রয়োজনীয়তা

- Android Studio (সর্বশেষ সংস্করণ)
- JDK 11 বা তার উপরে
- Gradle

## 🔨 স্থানীয় বিল্ডিং (Local Building)

### 1. অটো APK বিল্ড করুন

```bash
./gradlew buildAutoApk
```

এই কমান্ড স্বয়ংক্রিয় বিল্ডের জন্য অপ্টিমাইজড APK তৈরি করবে।

আউটপুট অবস্থান:
```
app/build/outputs/apk/auto/release/app-auto-release.apk
```

### 2. ম্যানুয়াল APK বিল্ড করুন

```bash
./gradlew buildManualApk
```

এই কমান্ড ম্যানুয়াল বিল্ডের জন্য অপ্টিমাইজড APK তৈরি করবে।

আউটপুট অবস্থান:
```
app/build/outputs/apk/manual/release/app-manual-release.apk
```

### 3. উভয় APK বিল্ড করুন

```bash
./gradlew buildAllApks
```

এই কমান্ড উভয় (অটো এবং ম্যানুয়াল) APK একসাথে তৈরি করবে।

## 🤖 স্বয়ংক্রিয় বিল্ডিং (GitHub Actions)

### সেটআপ

1. **Push করুন** কোনো কমিট `main` বা `develop` ব্রাঞ্চে
2. GitHub Actions স্বয়ংক্রিয়ভাবে উভয় APK তৈরি করবে

### ম্যানুয়াল ট্রিগার

1. GitHub রিপোজিটরিতে যান
2. **Actions** ট্যাবে ক্লিক করুন
3. **Build APK (Auto & Manual)** ওয়ার্কফ্লো নির্বাচন করুন
4. **Run workflow** এ ক্লিক করুন
5. বিল্ড টাইপ নির্বাচন করুন:
   - **all** - উভয় APK বিল্ড করে (ডিফল্ট)
   - **auto** - শুধুমাত্র অটো APK
   - **manual** - শুধুমাত্র ম্যানুয়াল APK

## 📦 আউটপুট

বিল্ডের পরে, APK ফাইলগুলি এখানে পাওয়া যাবে:

- **অটো APK**: `app/build/outputs/apk/auto/release/`
- **ম্যানুয়াল APK**: `app/build/outputs/apk/manual/release/`

## 🔐 স্বাক্ষরকরণ (Signing)

### ডিবাগ বিল্ড

ডিবাগ বিল্ড স্বয়ংক্রিয়ভাবে Android এর ডিবাগ কী দিয়ে স্বাক্ষরিত হয়।

### রিলিজ বিল্ড

রিলিজ বিল্ডের জন্য, আপনার সাইনিং কী কনফিগার করুন:

1. `app/build.gradle` এ `signingConfigs.release` সেকশন খুঁজুন
2. আপনার `release.keystore` ফাইল এবং পাসওয়ার্ড যোগ করুন
3. পরিবেশ ভেরিয়েবল সেট করুন:
   ```bash
   export KEYSTORE_PASSWORD='your_password'
   export KEY_ALIAS='your_key_alias'
   export KEY_PASSWORD='your_key_password'
   ```

## 🐛 সমস্যা সমাধান

### সমস্যা: Gradle সিঙ্ক ব্যর্থ হয়েছে

**সমাধান:**
```bash
./gradlew clean
./gradlew sync
```

### সমস্যা: Gradle কমান্ড পাওয়া যায় না

**সমাধান:**
```bash
chmod +x gradlew
./gradlew buildAutoApk
```

### সমস্যা: জাভা সংস্করণ ত্রুটি

**সমাধান:** JDK 11 বা তার উপরে ইনস্টল করুন এবং JAVA_HOME সেট করুন।

## 📝 নোট

- **Product Flavors**: এই প্রজেক্ট `auto` এবং `manual` দুটি ফ্লেভার ব্যবহার করে
- **Build Types**: `debug` এবং `release` উভয় টাইপ উপলব্ধ
- **Proguard**: রিলিজ বিল্ডে কোড মিনিফাই সক্ষম আছে
