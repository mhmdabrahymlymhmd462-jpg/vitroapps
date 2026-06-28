# دليل النشر على Railway / Render / Vercel

## ✅ التحديثات المطبقة

تم تحديث الكود ليعمل بشكل صحيح على الاستضافة السحابية:

### 1. **إجبار تحميل الملفات بدلاً من تشغيلها**
تم تحديث `server.js` لإضافة headers تجبر المتصفح على تحميل الفيديو:
```javascript
Content-Disposition: attachment; filename="video.mp4"
```

### 2. **دعم الروابط الديناميكية**
تم تحديث `public/app.js` ليستخدم `window.location.origin` بدلاً من `localhost`:
```javascript
const fullUrl = `${window.location.origin}${downloadUrl}`;
```

### 3. **تحميل تلقائي محسّن**
تم تحسين آلية التحميل التلقائي لتعمل على جميع المتصفحات.

---

## 🚀 خطوات النشر على Railway

### 1. **تحضير المشروع**

تأكد من وجود الملفات التالية:

```
project/
├── server.js
├── package.json
├── public/
│   ├── index.html
│   ├── style.css
│   ├── app.js
│   └── favicon.svg
├── downloads/ (سيتم إنشاؤه تلقائياً)
└── yt-dlp.exe
```

### 2. **تحديث package.json**

تأكد من وجود script للبداية:
```json
{
  "scripts": {
    "start": "node server.js"
  }
}
```

### 3. **النشر على Railway**

#### الطريقة 1: من خلال Git
```bash
# 1. رفع الكود على GitHub
git add .
git commit -m "Deploy to Railway"
git push origin main

# 2. اذهب إلى railway.app
# 3. اضغط "New Project"
# 4. اختر "Deploy from GitHub repo"
# 5. اختر repository الخاص بك
```

#### الطريقة 2: من خلال Railway CLI
```bash
# 1. تثبيت Railway CLI
npm install -g @railway/cli

# 2. تسجيل الدخول
railway login

# 3. رفع المشروع
railway init
railway up
```

### 4. **متغيرات البيئة (Environment Variables)**

في لوحة تحكم Railway، أضف:
```
PORT=3001
NODE_ENV=production
```

### 5. **ملفات Cookies**

⚠️ **مهم جداً:** لن تعمل Instagram/Facebook بدون cookies!

**خيارات الحل:**

#### الخيار 1: رفع ملفات Cookies (غير موصى به للأمان)
```bash
# أضف الملفات إلى .gitignore أولاً، ثم ارفعها يدوياً من لوحة Railway
cookies.txt
Instgram_cookies.txt
facebook_cookies.txt
```

#### الخيار 2: استخدام Cookies من المتصفح (الموصى به)
حدّث `server.js`:
```javascript
// بدلاً من --cookies cookies.txt
args.push('--cookies-from-browser', 'chrome');
```

---

## 🌐 النشر على Render

### 1. اذهب إلى [render.com](https://render.com)
### 2. اضغط "New +" ثم "Web Service"
### 3. ربط حساب GitHub
### 4. اختر repository
### 5. ضبط الإعدادات:
```
Build Command: npm install
Start Command: npm start
```

---

## ⚙️ النشر على Vercel (محدود)

⚠️ **ملاحظة:** Vercel لا يدعم تنفيذ ملفات `.exe` مثل yt-dlp.

**البديل:** استخدم Docker أو Railway/Render.

---

## 🧪 اختبار الموقع بعد النشر

### 1. **افتح رابط الموقع**
```
https://your-app-name.railway.app
```

### 2. **جرب تحميل فيديو**
- TikTok ✅
- YouTube ✅
- Facebook ⚠️ (يحتاج cookies)
- Instagram ⚠️ (يحتاج cookies)

### 3. **تحقق من التحميل**
عند الضغط على "Download Video"، يجب أن:
1. يظهر شريط التقدم
2. يتم التحميل تلقائياً إلى جهازك
3. **لا يفتح في متصفح جديد**

---

## 🐛 استكشاف الأخطاء

### المشكلة: الفيديو يفتح في المتصفح بدلاً من التحميل
**الحل:** تأكد من أن التحديثات الأخيرة تم تطبيقها:
- ✅ `server.js` محدث مع `Content-Disposition: attachment`
- ✅ `public/app.js` محدث مع التحميل المحسّن

### المشكلة: Instagram/Facebook لا يعمل
**الحل:** راجع `INSTAGRAM_COOKIES_GUIDE.md`

### المشكلة: yt-dlp لا يعمل على Vercel
**الحل:** استخدم Railway أو Render بدلاً من Vercel

---

## 📊 مقارنة منصات الاستضافة

| المنصة | السعر | دعم yt-dlp | سهولة الاستخدام | الموصى به |
|--------|-------|-----------|-----------------|-----------|
| **Railway** | Free tier | ✅ نعم | ⭐⭐⭐⭐⭐ | ✅ **الأفضل** |
| **Render** | Free tier | ✅ نعم | ⭐⭐⭐⭐ | ✅ جيد |
| **Vercel** | Free tier | ❌ لا | ⭐⭐⭐⭐⭐ | ❌ غير مناسب |
| **Heroku** | مدفوع | ✅ نعم | ⭐⭐⭐ | ⚠️ باهظ |

---

## ✅ قائمة التحقق النهائية

قبل النشر، تأكد من:
- [ ] تم تحديث `server.js` مع headers التحميل
- [ ] تم تحديث `public/app.js` مع الروابط الديناميكية
- [ ] تم اختبار الموقع محلياً
- [ ] تم رفع الكود على Git
- [ ] تم إنشاء المشروع على Railway
- [ ] تم اختبار التحميل من الرابط المباشر

**الآن المشروع جاهز للنشر والاستخدام! 🎉**
