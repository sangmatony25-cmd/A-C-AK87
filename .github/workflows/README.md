# A-C-AK87

Android APK Builder with GitHub Actions

## বৈশিষ্ট্য

✅ **স্বয়ংক্রিয় বিল্ড** - Push এবং PR এর সময় Debug APK স্বয়ংক্রিয়ভাবে বিল্ড হয়
✅ **মাস্যুয়াল বিল্ড** - Actions ট্যাব থেকে Debug বা Release যেকোনো অপশন বেছে নিন
✅ **Artifact সংরক্ষণ** - বিল্ট APK স্বয়ংক্রিয়ভাবে ডাউনলোড করার জন্য উপলব্ধ
✅ **রিলিজ তৈরি** - Release বিল্ডের জন্য স্বয়ংক্রিয় GitHub রিলিজ তৈরি হয়

## কীভাবে ব্যবহার করবেন?

### স্বয়ংক্রিয় বিল্ড
- `main` বা `develop` ব্রঞ্চে push করুন
- Pull Request তৈরি করুন
- Debug APK স্বয়ংক্রিয়ভাবে বিল্ড হবে

### মাস্যুয়াল বিল্ড
1. রিপোজিটরিতে যান
2. **Actions** ট্যাবে ক্লিক করুন
3. **Build APK** ওয়ার্কফ্লো বেছে নিন
4. **Run workflow** ক্লিক করুন
5. **Build Type** তে `debug` বা `release` বেছে নিন
6. **Run workflow** ক্লিক করুন

### Artifact ডাউনলোড করুন
1. Workflow সম্পন্ন হওয়ার পর **Artifacts** সেকশনে যান
2. `debug-apk` বা `release-apk` ডাউনলোড করুন
