# 🚀 دليل النشر على Railway - خطوة بخطوة

## ✅ تم إصلاح مشكلة localhost!

تم تحديث الكود ليعمل تلقائياً على أي استضافة بدون تعديل.

---

## 📋 خطوات النشر

### 1️⃣ **تحضير الكود**

قبل الرفع، تأكد من:

```bash
# تحديث جميع التغييرات
git add .
git commit -m "Fix: Use dynamic API URLs for Railway deployment"
git push origin main
```

### 2️⃣ **إنشاء مشروع على Railway**

1. اذهب إلى [railway.app](https://railway.app)
2. اضغط **"Start a New Project"**
3. اختر **"Deploy from GitHub repo"**
4. اختر repository الخاص بك
5. انتظر حتى ينتهي Build (2-3 دقائق)

### 3️⃣ **ضبط إعدادات المشروع**

في لوحة تحكم Railway:

#### Settings → Environment Variables:
```
PORT=3001
NODE_ENV=production
```

#### Settings → Networking:
- احصل على الرابط العام للموقع
- مثل: `https://vitroapps-production-f037.up.railway.app`

### 4️⃣ **رفع ملفات Cookies (للInstagram/Facebook)**

⚠️ **مهم:** Instagram و Facebook يحتاجان ملفات cookies

**الطريقة الآمنة:**

1. في Railway Dashboard → **Files**
2. ارفع الملفات يدوياً:
   - `Instgram_cookies.txt`
   - `facebook_cookies.txt`

**أو استخدم Railway CLI:**
```bash
railway login
railway link
railway run bash
# ثم ارفع الملفات
```

---

## ✅ **التحقق من نجاح النشر**

### 1. افتح رابط موقعك:
```
https://your-app-name.railway.app
```

### 2. جرب تحميل فيديو:
- **TikTok** ✅ يعمل بدون cookies
- **YouTube** ✅ يعمل بدون cookies
- **Facebook** ⚠️ يحتاج cookies
- **Instagram** ⚠️ يحتاج cookies

### 3. تحقق من التحميل:
- عند الضغط "Download Video"
- يجب أن يبدأ **التحميل مباشرة**
- **لا يفتح** في تاب جديد

---

## 🐛 حل المشاكل الشائعة

### ❌ المشكلة: `ERR_CONNECTION_REFUSED`
**السبب:** الكود يستخدم `localhost` بدلاً من رابط Railway

**الحل:** تم إصلاحه! الكود الآن يستخدم:
```javascript
const API_BASE = window.location.origin;
```

### ❌ المشكلة: `yt-dlp: command not found`
**السبب:** ملف `yt-dlp.exe` غير موجود على السيرفر

**الحل:** استخدم النسخة Linux من yt-dlp:

1. احذف `yt-dlp.exe` من المشروع
2. أضف إلى `package.json`:
```json
{
  "scripts": {
    "postinstall": "curl -L https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp -o yt-dlp && chmod +x yt-dlp",
    "start": "node server.js"
  }
}
```

3. حدّث `server.js`:
```javascript
// استخدم yt-dlp بدلاً من yt-dlp.exe
const ytDlpPath = path.join(__dirname, 'yt-dlp');
```

### ❌ المشكلة: Instagram/Facebook لا يعمل
**السبب:** ملفات cookies غير موجودة

**الحل:** راجع الخطوة 4️⃣ أعلاه

---

## 🔒 أمان ملفات Cookies

⚠️ **تحذير:** ملفات cookies تحتوي على بيانات تسجيل دخولك!

### احمِ ملفاتك:

1. **أضف إلى `.gitignore`:**
```
cookies.txt
Instgram_cookies.txt
facebook_cookies.txt
*.txt
```

2. **استخدم متغيرات البيئة (الأفضل):**

في Railway → Environment Variables:
```
INSTAGRAM_COOKIES=base64_encoded_cookies_here
FACEBOOK_COOKIES=base64_encoded_cookies_here
```

ثم في الكود:
```javascript
// Read from environment variable
const instagramCookies = process.env.INSTAGRAM_COOKIES;
if (instagramCookies) {
    const cookiesBuffer = Buffer.from(instagramCookies, 'base64');
    fs.writeFileSync('temp_cookies.txt', cookiesBuffer);
    args.push('--cookies', 'temp_cookies.txt');
}
```

---

## 📊 مراقبة الأداء

### في Railway Dashboard:

1. **Metrics** → انظر إلى:
   - CPU Usage
   - Memory Usage
   - Network Traffic

2. **Logs** → راقب الأخطاء:
```bash
railway logs
```

3. **Deployments** → تاريخ النشر

---

## 🎯 Checklist النهائية

قبل إطلاق الموقع:

- [ ] تم رفع الكود على GitHub
- [ ] تم إنشاء مشروع على Railway
- [ ] تم ضبط Environment Variables
- [ ] تم رفع ملفات Cookies
- [ ] تم اختبار TikTok ✅
- [ ] تم اختبار YouTube ✅
- [ ] تم اختبار Facebook ⚠️
- [ ] تم اختبار Instagram ⚠️
- [ ] التحميل يعمل بدون فتح تاب جديد ✅

---

## 🚀 إطلاق الموقع!

كل شيء جاهز! شارك الرابط:
```
https://your-app-name.railway.app
```

**🎉 مبروك! موقعك الآن متاح للعالم!**

---

## 📞 الدعم

إذا واجهت أي مشكلة:
1. تحقق من Logs في Railway
2. راجع `INSTAGRAM_COOKIES_GUIDE.md`
3. راجع `DEPLOYMENT_GUIDE.md`

**حظاً موفقاً! 🚀**
