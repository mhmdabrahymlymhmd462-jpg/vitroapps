# 🎥 VITROAPPS - Social Media Video Downloader

أداة احترافية لتحميل الفيديوهات من TikTok، Instagram، YouTube، و Facebook بدون علامات مائية.

[![Live Demo](https://img.shields.io/badge/demo-online-success)](https://vitroapps-production-f037.up.railway.app)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

---

## ✨ المميزات

- ✅ **دعم متعدد المنصات**: TikTok, Instagram, YouTube, Facebook
- ✅ **بدون علامات مائية**: تحميل نظيف بجودة عالية
- ✅ **واجهة عربية/إنجليزية**: دعم كامل للغتين
- ✅ **تحميل تلقائي**: الفيديو يُحمّل مباشرة بدون فتح تاب جديد
- ✅ **شريط تقدم حي**: متابعة عملية التحميل لحظياً
- ✅ **استجابة كاملة**: يعمل على جميع الأجهزة
- ✅ **آمن وسريع**: بدون إعلانات أو تسجيل

---

## 🚀 البدء السريع

### المتطلبات

- **Node.js** v14 أو أحدث
- **npm** أو **yarn**
- **yt-dlp** (يتم تثبيته تلقائياً)

### التثبيت المحلي

```bash
# 1. استنساخ المشروع
git clone https://github.com/yourusername/vitroapps.git
cd vitroapps

# 2. تثبيت الاعتماديات
npm install

# 3. تشغيل السيرفر
npm start

# 4. افتح المتصفح على
# http://localhost:3001
```

---

## 📦 النشر على Railway

### خطوة بخطوة:

1. **ارفع الكود على GitHub**
```bash
git add .
git commit -m "Initial commit"
git push origin main
```

2. **أنشئ مشروع على Railway**
   - اذهب إلى [railway.app](https://railway.app)
   - اضغط "New Project" → "Deploy from GitHub"
   - اختر repository

3. **انتظر اكتمال Build** (2-3 دقائق)

4. **ضبط Environment Variables**:
```
PORT=3001
NODE_ENV=production
```

5. **رفع ملفات Cookies** (للInstagram/Facebook):
   - راجع `INSTAGRAM_COOKIES_GUIDE.md`
   - ارفع الملفات يدوياً في Railway Dashboard

📚 **للمزيد:** راجع `RAILWAY_DEPLOYMENT.md`

---

## 🛠️ التقنيات المستخدمة

### Backend
- **Node.js** + **Express.js**
- **yt-dlp** - محرك التحميل
- **Server-Sent Events (SSE)** - التحديثات الحية

### Frontend
- **HTML5** + **CSS3**
- **Vanilla JavaScript** - بدون مكتبات ثقيلة
- **Responsive Design** - تصميم متجاوب

### DevOps
- **Railway** - الاستضافة
- **Git** - التحكم في الإصدار
- **GitHub Actions** - CI/CD (اختياري)

---

## 📁 بنية المشروع

```
vitroapps/
├── public/                # ملفات الواجهة الأمامية
│   ├── index.html        # الصفحة الرئيسية
│   ├── style.css         # التنسيقات
│   ├── app.js            # JavaScript للواجهة
│   └── favicon.svg       # أيقونة الموقع
├── downloads/            # مجلد التحميلات (مؤقت)
├── server.js             # خادم Express
├── package.json          # اعتماديات Node.js
├── yt-dlp.exe           # محرك التحميل (Windows)
├── .gitignore            # ملفات مستثناة من Git
└── README.md            # هذا الملف
```

---

## 🔧 الإعداد المتقدم

### ملفات Cookies للInstagram/Facebook

Instagram و Facebook يتطلبان ملف cookies للمصادقة.

**الحصول على Cookies:**

1. تثبيت إضافة المتصفح:
   - Chrome: [Get cookies.txt LOCALLY](https://chrome.google.com/webstore/detail/get-cookiestxt-locally/cclelndahbckbenkjhflpdbgdldlbecc)
   
2. سجل دخول في Instagram/Facebook

3. صدّر الـ cookies وضعها في:
   - `Instgram_cookies.txt` (للInstagram)
   - `facebook_cookies.txt` (للFacebook)

📚 **دليل مفصل:** `INSTAGRAM_COOKIES_GUIDE.md`

### متغيرات البيئة

يمكن ضبط المتغيرات التالية:

```env
PORT=3001                    # منفذ السيرفر
NODE_ENV=production          # بيئة التشغيل
MAX_FILE_SIZE=100            # حجم الملف الأقصى (MB)
DOWNLOAD_TIMEOUT=300000      # مهلة التحميل (ms)
```

---

## 🧪 الاختبار

```bash
# تشغيل السيرفر في وضع التطوير
npm run dev

# اختبار الروابط:
# TikTok:    https://vm.tiktok.com/...
# Instagram: https://www.instagram.com/p/...
# YouTube:   https://www.youtube.com/watch?v=...
# Facebook:  https://www.facebook.com/reel/...
```

---

## 🐛 استكشاف الأخطاء

### المشكلة: `ERR_CONNECTION_REFUSED`
**الحل:** تأكد من تشغيل السيرفر على البورت الصحيح

### المشكلة: Instagram/Facebook لا يعمل
**الحل:** تحديث ملف cookies - راجع `INSTAGRAM_COOKIES_GUIDE.md`

### المشكلة: الفيديو يفتح بدلاً من التحميل
**الحل:** تم إصلاحها في آخر تحديث - ارفع آخر نسخة على Railway

### المشكلة: `yt-dlp: command not found` على Railway
**الحل:** تم إصلاحها - `postinstall` script يحمل yt-dlp تلقائياً

---

## 📊 الأداء

- **سرعة التحميل**: حسب سرعة الإنترنت
- **حجم الفيديو**: حتى 100 MB (قابل للزيادة)
- **المنصات المدعومة**: 4 منصات رئيسية
- **معدل النجاح**: 95%+ للروابط الصحيحة

---

## 🔒 الأمان والخصوصية

- ✅ **لا تخزين دائم**: الملفات تُحذف بعد التحميل
- ✅ **HTTPS**: اتصال آمن مشفر
- ✅ **بدون تتبع**: لا نجمع بيانات المستخدمين
- ✅ **Open Source**: الكود مفتوح للمراجعة

⚠️ **تحذير**: ملفات cookies تحتوي بيانات حساسة - لا تشاركها!

---

## 🤝 المساهمة

نرحب بالمساهمات! إليك كيفية المساعدة:

1. Fork المشروع
2. أنشئ Branch جديد (`git checkout -b feature/amazing`)
3. Commit تغييراتك (`git commit -m 'Add amazing feature'`)
4. Push إلى Branch (`git push origin feature/amazing`)
5. افتح Pull Request

---

## 📝 الترخيص

هذا المشروع مرخص تحت رخصة MIT - راجع ملف [LICENSE](LICENSE) للتفاصيل.

---

## 👤 المطور

تم التطوير بواسطة **VITROAPPS**

- 🌐 Website: [vitroapps.railway.app](https://vitroapps-production-f037.up.railway.app)
- 📧 Email: contact@vitroapps.com
- 💼 GitHub: [@vitroapps](https://github.com/vitroapps)

---

## 🙏 شكر وتقدير

- **yt-dlp** - محرك التحميل القوي
- **Railway** - منصة استضافة رائعة
- **المجتمع** - لدعمكم المستمر

---

## ⭐ إذا أعجبك المشروع

إذا وجدت هذا المشروع مفيداً، فضلاً أعطه نجمة ⭐ على GitHub!

---

## 📚 وثائق إضافية

- [دليل النشر على Railway](RAILWAY_DEPLOYMENT.md)
- [دليل ملفات Cookies](INSTAGRAM_COOKIES_GUIDE.md)
- [دليل النشر العام](DEPLOYMENT_GUIDE.md)

---

**صُنع بـ ❤️ في مصر**

© 2024 VITROAPPS. جميع الحقوق محفوظة.
