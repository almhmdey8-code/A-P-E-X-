# دليل إعداد بناء APK 🚀

## الخطوات الأولية

### 1️⃣ المتطلبات الأساسية
- **Java Development Kit (JDK)**: الإصدار 11 أو أحدث
- **Android SDK**: API 33 أو أحدث
- **Gradle**: الإصدار 7.0 أو أحدث (يُستخدم تلقائياً عبر `gradlew`)

### 2️⃣ إعداد محلي

```bash
# استنساخ المشروع
git clone https://github.com/almhmdey8-code/A-P-E-X-.git
cd A-P-E-X-

# منح الصلاحيات لـ gradlew
chmod +x gradlew

# بناء APK Debug
./gradlew assembleDebug

# بناء APK Release
./gradlew assembleRelease
```

## خيارات البناء

### GitHub Actions ✅
يتم التشغيل تلقائياً عند:
- **Push** إلى الفروع الرئيسية (`main`, `develop`)
- **Pull Requests** على الفروع الرئيسية
- **تشغيل يدوي** من تبويب Actions

#### الملفات المُنتجة:
- 📦 `app/build/outputs/apk/debug/` - APK التطوير
- 📦 `app/build/outputs/apk/release/` - APK الإطلاق
- 📊 `app/build/reports/tests/` - تقارير الاختبارات

---

### Codemagic 🔧
لتفعيل Codemagic:

1. توجه إلى [codemagic.io](https://codemagic.io)
2. قم بتوصيل حسابك على GitHub
3. اختر المشروع `A-P-E-X-`
4. ستُستخدم إعدادات `codemagic.yaml` تلقائياً

#### المميزات:
- 🔄 بناء تلقائي على كل push
- 🏷️ بناء الإصدارات من Tags
- 📧 إشعارات البريد الإلكتروني
- 💬 تكامل Slack
- 📱 توزيع مباشر على الأجهزة

---

## البناء اليدوي

### بناء Debug APK
```bash
./gradlew assembleDebug
```
**النتيجة:** `app/build/outputs/apk/debug/app-debug.apk`

### بناء Release APK
```bash
./gradlew assembleRelease
```
**النتيجة:** `app/build/outputs/apk/release/app-release.apk`

### تشغيل الاختبارات
```bash
./gradlew test
```

### تحليل الكود
```bash
./gradlew lint
```

---

## التوقيع الرقمي (للإطلاق)

لتوقيع Release APK:

1. **إنشاء keystore** (مرة واحدة فقط):
```bash
keytool -genkey -v -keystore my-release-key.keystore -keyalg RSA -keysize 2048 -validity 10000 -alias my-key-alias
```

2. **إضافة إلى `gradle.properties`**:
```properties
RELEASE_STORE_FILE=my-release-key.keystore
RELEASE_STORE_PASSWORD=your_password
RELEASE_KEY_ALIAS=my-key-alias
RELEASE_KEY_PASSWORD=your_password
```

3. **البناء والتوقيع**:
```bash
./gradlew assembleRelease
```

---

## استكشاف الأخطاء

### خطأ: `gradlew not found`
```bash
chmod +x gradlew
```

### خطأ: `Java version not supported`
تأكد من استخدام Java 11 أو أحدث:
```bash
java -version
```

### خطأ: `Android SDK not found`
تأكد من تعيين `ANDROID_HOME`:
```bash
export ANDROID_HOME=$HOME/Android/Sdk
export PATH=$PATH:$ANDROID_HOME/tools:$ANDROID_HOME/platform-tools
```

---

## المراجع

- 📚 [توثيق GitHub Actions](https://docs.github.com/en/actions)
- 📚 [توثيق Codemagic](https://docs.codemagic.io)
- 📚 [دليل بناء Android Gradle](https://developer.android.com/build)

---

## الدعم والمساعدة

في حالة وجود مشاكل:
1. تحقق من سجلات GitHub Actions في تبويب "Actions"
2. راجع سجلات Codemagic في لوحة التحكم
3. استفسر في Issues بتفاصيل الخطأ
