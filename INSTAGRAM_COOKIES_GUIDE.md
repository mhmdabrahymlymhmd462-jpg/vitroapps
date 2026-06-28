# دليل تحديث ملف Cookies لـ Instagram

## المشكلة
يظهر الخطأ التالي عند محاولة تحميل فيديو من Instagram:
```
ERROR: [Instagram] Instagram sent an empty media response
```

## الحل: تحديث ملف cookies.txt

### الطريقة 1: استخدام إضافة المتصفح (الأسهل)

1. **تثبيت الإضافة:**
   - لمتصفح Chrome/Edge: [Get cookies.txt LOCALLY](https://chrome.google.com/webstore/detail/get-cookiestxt-locally/cclelndahbckbenkjhflpdbgdldlbecc)
   - لمتصفح Firefox: [cookies.txt](https://addons.mozilla.org/en-US/firefox/addon/cookies-txt/)

2. **تسجيل الدخول إلى Instagram:**
   - افتح [instagram.com](https://www.instagram.com) في المتصفح
   - سجل دخولك بحسابك

3. **تصدير الـ Cookies:**
   - اضغط على أيقونة الإضافة في شريط الأدوات
   - اختر "Export" أو "تصدير"
   - احفظ الملف باسم `cookies.txt`

4. **نسخ الملف:**
   - انسخ ملف `cookies.txt` إلى مجلد المشروع:
   ```
   H:\All Floders\HTML,CSS,JS,BOOTSTRAP\Coching\Vitro1\cookies.txt
   ```

### الطريقة 2: استخدام yt-dlp مباشرة

يمكنك استخدام yt-dlp لاستخراج الـ cookies من المتصفح تلقائياً:

```bash
yt-dlp --cookies-from-browser chrome https://www.instagram.com/p/DYstN1viF_B/
```

أو لـ Edge:
```bash
yt-dlp --cookies-from-browser edge https://www.instagram.com/p/DYstN1viF_B/
```

### الطريقة 3: تحديث الكود ليستخدم Cookies من المتصفح

في ملف `server.js`، ابحث عن السطر:
```javascript
'--cookies', 'cookies.txt',
```

واستبدله بـ:
```javascript
'--cookies-from-browser', 'chrome',  // أو 'edge' أو 'firefox'
```

## التحقق من نجاح التحديث

بعد تحديث الـ cookies، جرب تحميل فيديو من Instagram مرة أخرى. إذا نجح التحميل، فقد تم حل المشكلة!

## ملاحظات مهمة

- ملف الـ cookies يحتاج للتحديث كل فترة (عادة كل 30-60 يوم)
- تأكد من أن حسابك على Instagram نشط وليس محظوراً
- بعض الفيديوهات الخاصة قد لا تعمل حتى مع الـ cookies
- لا تشارك ملف cookies.txt مع أحد لأنه يحتوي على معلومات تسجيل الدخول الخاصة بك

## استكشاف الأخطاء

### إذا استمرت المشكلة:

1. **تحديث yt-dlp:**
   ```bash
   yt-dlp -U
   ```

2. **التحقق من الحساب:**
   - تأكد من أنك مسجل دخول على Instagram في المتصفح
   - جرب فتح الرابط في المتصفح للتأكد من أنه يعمل

3. **محاولة رابط مختلف:**
   - جرب فيديو Instagram آخر
   - تأكد من أن الفيديو عام وليس خاص

## روابط مفيدة

- [دليل yt-dlp للـ Cookies](https://github.com/yt-dlp/yt-dlp/wiki/FAQ#how-do-i-pass-cookies-to-yt-dlp)
- [صفحة مشاكل Instagram في yt-dlp](https://github.com/yt-dlp/yt-dlp/issues?q=instagram)
