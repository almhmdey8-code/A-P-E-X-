# A-P-E-X- تطبيق

## نظرة عامة
تطبيق Android متقدم مع نظام البناء التلقائي المدمج.

## المميزات 🎯
- ✅ بناء تلقائي عبر GitHub Actions
- ✅ دعم Codemagic للبناء والتوزيع
- ✅ اختبارات تلقائية
- ✅ APK Debug و Release
- ✅ تقارير مفصلة

## البدء السريع 🚀

### المتطلبات
- Java 11+
- Android SDK 33+
- Gradle 7.0+

### البناء المحلي
```bash
# استنساخ المشروع
git clone https://github.com/almhmdey8-code/A-P-E-X-.git
cd A-P-E-X-

# بناء Debug APK
./gradlew assembleDebug

# بناء Release APK
./gradlew assembleRelease
```

**للمزيد من التفاصيل، راجع [دليل إعداد البناء الكامل](./BUILD_SETUP.md)**

## سير العمل التلقائي 🔄

### GitHub Actions
يتم التشغيل تلقائياً عند:
- Push إلى `main` أو `develop`
- فت�� Pull Request
- التشغيل اليدوي من تبويب Actions

### Codemagic
- بناء تلقائي على كل commit
- بناء الإصدارات من Tags
- توزيع مباشر

## الملفات المهمة 📁
- `.github/workflows/build-apk.yml` - سير عمل GitHub Actions
- `codemagic.yaml` - إعدادات Codemagic
- `BUILD_SETUP.md` - **دليل تفصيلي للبناء**
- `INSTALLATION.md` - دليل التثبيت
- `gradle.properties` - إعدادات Gradle

## الإخراج 📦
- `app/build/outputs/apk/debug/` - APK التطوير
- `app/build/outputs/apk/release/` - APK الإطلاق
- `app/build/reports/` - التقارير

## المساهمة 👥
1. Fork المشروع
2. إنشاء فرع (`git checkout -b feature/name`)
3. Commit التغييرات
4. Push إلى الفرع
5. فتح Pull Request

## الترخيص 📄
هذا المشروع مرخص تحت MIT License

## الدعم 💬
للمساعدة، افتح Issue أو تواصل عبر البريد الإلكتروني.

---
**تم إنشاؤه بواسطة GitHub Copilot - 2026-09-09**
