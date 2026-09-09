# دليل التثبيت والإعداد 📱

## متطلبات النظام

### ✅ المتطلبات الإلزامية:
- **Java Development Kit (JDK)**: الإصدار 11 فأعلى
- **Android SDK**: API 33 فأعلى
- **Gradle**: يتم تنزيله تلقائياً عبر `gradlew`

### اختياري:
- **Android Studio**: للتطوير المحلي
- **Codemagic Account**: للبناء السحابي

---

## التثبيت المحلي 🛠️

### على Linux/Mac:
```bash
# 1. استنساخ المستودع
git clone https://github.com/almhmdey8-code/A-P-E-X-.git
cd A-P-E-X-

# 2. منح الصلاحيات
chmod +x gradlew

# 3. بناء المشروع
./gradlew build

# 4. بناء APK
./gradlew assembleDebug    # للتطوير
./gradlew assembleRelease  # للإطلاق
```

### على Windows:
```cmd
# 1. استنساخ المستودع
git clone https://github.com/almhmdey8-code/A-P-E-X-.git
cd A-P-E-X-

# 2. بناء المشروع (بدون chmod)
gradlew.bat build

# 3. بناء APK
gradlew.bat assembleDebug    # للتطوير
gradlew.bat assembleRelease  # للإطلاق
```

---

## إعداد GitHub Actions ✅

### تفعيل البناء التلقائي:

1. اذهب إلى **Settings** → **Actions** → **General**
2. فعّل **Actions** ← تأكد من أنها مفعلة
3. انسخ الملف `.github/workflows/build-apk.yml` إلى مستودعك

### المشغّلات التلقائية:
```yaml
# عند Push إلى main أو develop
git push origin main

# عند فتح Pull Request
git push origin feature-branch

# التشغيل اليدوي من Actions tab
# GitHub → Actions → Build APK → Run workflow
```

---

## إعداد Codemagic 🔧

### الخطوة 1: إنشاء حساب
1. توجه إلى [codemagic.io](https://codemagic.io)
2. اختر "Sign up with GitHub"
3. فرّخ الوصول إلى مستودعاتك

### الخطوة 2: ربط المشروع
1. اختر **A-P-E-X-** من قائمة المستودعات
2. Codemagic سيكتشف `codemagic.yaml` تلقائياً
3. اضغط **Start build**

### الخطوة 3: الإشعارات (اختياري)
في `codemagic.yaml`:
```yaml
publishing:
  email:
    recipients:
      - your-email@example.com
  slack:
    channel: '#builds'
```

---

## أوامر Gradle الشائعة 📋

```bash
# بناء وتشغيل الاختبارات
./gradlew test

# تحليل الكود (Lint)
./gradlew lint

# تنظيف الملفات المؤقتة
./gradlew clean

# بناء شامل
./gradlew build

# عرض جميع المهام المتاحة
./gradlew tasks

# بناء مع معلومات تفصيلية
./gradlew assembleDebug --stacktrace

# تشغيل اختبارات محددة
./gradlew test --tests com.example.MyTest
```

---

## التوقيع الرقمي (للإطلاق الحقيقي) 🔐

### إنشاء مفتاح التوقيع:
```bash
keytool -genkey -v -keystore my-release-key.keystore \
  -keyalg RSA -keysize 2048 -validity 10000 \
  -alias my-key-alias
```

### إضافة إلى الإعدادات:
في `gradle.properties`:
```properties
RELEASE_STORE_FILE=my-release-key.keystore
RELEASE_STORE_PASSWORD=your_password
RELEASE_KEY_ALIAS=my-key-alias
RELEASE_KEY_PASSWORD=your_password
```

### البناء الموقّع:
```bash
./gradlew assembleRelease
# النتيجة: app/build/outputs/apk/release/app-release.apk
```

---

## استكشاف المشاكل 🐛

### المشكلة: `gradlew: permission denied`
```bash
chmod +x gradlew
```

### المشكلة: `Java version not supported`
```bash
# تحقق من إصدار Java
java -version

# أو عيّن JAVA_HOME
export JAVA_HOME=/path/to/java11
```

### المشكلة: `Android SDK not found`
```bash
export ANDROID_HOME=$HOME/Android/Sdk
export PATH=$PATH:$ANDROID_HOME/tools:$ANDROID_HOME/platform-tools
```

### المشكلة: فشل البناء على GitHub Actions
1. اذهب إلى **Actions** → الـ workflow الفاشل
2. اضغط على **re-run**
3. تحقق من السجلات للمزيد من التفاصيل

### المشكلة: Gradle Cache غير صحيح
```bash
./gradlew clean build --no-build-cache
```

---

## ملفات مهمة 📁

| الملف | الوصف |
|------|-------|
| `.github/workflows/build-apk.yml` | سير عمل GitHub Actions |
| `codemagic.yaml` | إعدادات Codemagic |
| `gradle.properties` | إعدادات Gradle |
| `.gitignore` | ملفات مستثناة من Git |
| `README.md` | المستند الرئيسي |
| `INSTALLATION.md` | هذا الملف |

---

## المراجع والموارد 📚

- [GitHub Actions Docs](https://docs.github.com/en/actions)
- [Codemagic Documentation](https://docs.codemagic.io/android-builds/)
- [Android Build Documentation](https://developer.android.com/build)
- [Gradle User Manual](https://docs.gradle.org)
- [Android SDK Setup](https://developer.android.com/studio/install)

---

## الدعم الفني 💬

إذا واجهت أي مشكلة:
1. تحقق من السجلات: `app/build/reports/`
2. ابحث في Issues الموجودة
3. افتح Issue جديدة مع تفاصيل المشكلة

---

**آخر تحديث: 2026-09-09**
