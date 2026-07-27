<div dir="rtl">

# سامانه خرید و اجاره املاک

یک وب‌اپلیکیشن فول‌استک فارسی برای ثبت، مدیریت، بررسی و نمایش آگهی‌های املاک است. کاربران می‌توانند حساب کاربری بسازند، وارد پنل خود شوند و آگهی جدید ثبت، ویرایش یا حذف کنند. آگهی ثبت‌شده ابتدا در انتظار تأیید مدیر قرار می‌گیرد و پس از تأیید، در بخش عمومی سایت نمایش داده می‌شود.

این پروژه با **Next.js 13 و App Router** توسعه داده شده و برای ذخیره اطلاعات از **MongoDB**، برای مدیریت مدل‌ها از **Mongoose** و برای احراز هویت از **NextAuth.js** استفاده می‌کند.

---

## فهرست مطالب

- [امکانات پروژه](#امکانات-پروژه)
- [فناوری‌های استفاده‌شده](#فناوریهای-استفادهشده)
- [معماری و نحوه عملکرد](#معماری-و-نحوه-عملکرد)
- [پیش‌نیازها](#پیشنیازها)
- [نصب و اجرای پروژه](#نصب-و-اجرای-پروژه)
- [تنظیم متغیرهای محیطی](#تنظیم-متغیرهای-محیطی)
- [ساخت کاربر مدیر](#ساخت-کاربر-مدیر)
- [راهنمای استفاده](#راهنمای-استفاده)
- [صفحات و مسیرها](#صفحات-و-مسیرها)
- [APIهای پروژه](#apiهای-پروژه)
- [مدل‌های پایگاه داده](#مدلهای-پایگاه-داده)
- [ساختار پوشه‌ها](#ساختار-پوشهها)
- [اسکریپت‌های قابل اجرا](#اسکریپتهای-قابل-اجرا)
- [نکات امنیتی](#نکات-امنیتی)
- [سناریوی پیشنهادی ارائه](#سناریوی-پیشنهادی-ارائه)
- [خطاهای رایج](#خطاهای-رایج)
- [پیشنهادهای توسعه آینده](#پیشنهادهای-توسعه-آینده)

---

## امکانات پروژه

### بخش عمومی

- نمایش صفحه اصلی فارسی و راست‌چین
- نمایش دسته‌بندی‌های آپارتمان، ویلا، مغازه و دفتر
- مشاهده فهرست آگهی‌های تأییدشده
- فیلتر آگهی‌ها بر اساس دسته‌بندی
- مشاهده صفحه جزئیات هر آگهی
- نمایش عنوان، آدرس، توضیحات، قیمت و تاریخ ساخت
- نمایش امکانات رفاهی و قوانین ملک
- نمایش اطلاعات بنگاه و شماره تماس
- تبدیل اعداد انگلیسی به فارسی در رابط کاربری
- نمایش تاریخ‌ها با تقویم فارسی
- کپی‌کردن لینک آگهی برای اشتراک‌گذاری

### احراز هویت

- ثبت‌نام کاربر با ایمیل و رمز عبور
- بررسی تکراری نبودن ایمیل
- هش‌کردن رمز عبور با `bcryptjs`
- ورود با روش `Credentials`
- نگهداری نشست کاربر به روش `JWT`
- جلوگیری از ورود کاربران لاگین‌شده به صفحات ورود و ثبت‌نام
- محافظت از پنل کاربری و پنل مدیریت
- امکان خروج از حساب کاربری

### پنل کاربری

- نمایش ایمیل و تاریخ عضویت کاربر
- ثبت آگهی جدید
- افزودن چند امکان رفاهی و چند قانون برای هر ملک
- انتخاب تاریخ ساخت با تقویم شمسی
- مشاهده تمام آگهی‌های ثبت‌شده توسط کاربر
- ویرایش آگهی
- حذف آگهی
- نمایش وضعیت آگهی پیش از تأیید مدیر

### پنل مدیریت

- تشخیص نقش مدیر از طریق فیلد `role`
- جلوگیری از دسترسی کاربران عادی به مسیر مدیریت
- مشاهده آگهی‌های در انتظار تأیید
- انتشار آگهی پس از بررسی مدیر
- نمایش آگهی تأییدشده در بخش عمومی سایت

---

## فناوری‌های استفاده‌شده

| فناوری | کاربرد |
|---|---|
| `Next.js 13.4` | فریم‌ورک اصلی و پیاده‌سازی Front-end و Back-end |
| `React 18` | ساخت رابط کاربری کامپوننت‌محور |
| `App Router` | مدیریت صفحات، Layoutها، مسیرهای پویا و API Routeها |
| `MongoDB` | پایگاه داده NoSQL پروژه |
| `Mongoose` | تعریف Schema، Model و ارتباط با MongoDB |
| `NextAuth.js` | احراز هویت و مدیریت Session |
| `bcryptjs` | هش و بررسی رمز عبور |
| `CSS Modules` | استایل‌دهی مجزا به کامپوننت‌ها |
| `react-hot-toast` | نمایش پیام موفقیت و خطا |
| `react-icons` | آیکون‌های رابط کاربری |
| `react-multi-date-picker` | انتخاب تاریخ با تقویم شمسی |
| `react-copy-to-clipboard` | کپی لینک آگهی |
| `next/font` | بارگذاری بهینه فونت فارسی یکان‌بخ |

---

## معماری و نحوه عملکرد

پروژه از معماری **Full-stack Next.js** استفاده می‌کند؛ بنابراین صفحات رابط کاربری و APIهای سمت سرور هر دو در یک پروژه قرار دارند.

### لایه نمایش

صفحات در مسیر `src/app` و کامپوننت‌ها در مسیر `src/components` قرار گرفته‌اند. کامپوننت‌ها به سه گروه تقسیم شده‌اند:

- `layout`: اجزای ثابت مانند Header، Footer و Sidebar پنل
- `template`: ساختار اصلی هر صفحه
- `module`: اجزای کوچک‌تر و قابل استفاده مجدد مانند Card، Input و Loader

### لایه منطق سرور

Route Handlerهای موجود در `src/app/api` درخواست‌های ثبت‌نام و عملیات آگهی‌ها را دریافت می‌کنند. این APIها مسئول اعتبارسنجی اولیه، بررسی Session، کنترل سطح دسترسی و ارتباط با پایگاه داده هستند.

### لایه داده

دو مدل اصلی در پروژه وجود دارد:

- `User`: اطلاعات حساب کاربری و نقش کاربر
- `Profile`: اطلاعات آگهی ملک

هر آگهی از طریق فیلد `userId` به کاربر سازنده خود متصل می‌شود.

### جریان انتشار آگهی

1. کاربر ثبت‌نام و وارد حساب خود می‌شود.
2. کاربر از پنل خود یک آگهی جدید ثبت می‌کند.
3. آگهی با مقدار پیش‌فرض `published: false` در MongoDB ذخیره می‌شود.
4. مدیر آگهی را در صفحه مدیریت مشاهده می‌کند.
5. مدیر روی دکمه انتشار کلیک می‌کند.
6. مقدار `published` به `true` تغییر می‌کند.
7. آگهی در صفحه عمومی آگهی‌ها قابل مشاهده می‌شود.

---

## پیش‌نیازها

پیش از اجرای پروژه موارد زیر باید نصب یا آماده باشند:

- `Node.js` نسخه `16.8` یا بالاتر؛ نسخه `18 LTS` پیشنهاد می‌شود.
- `npm`
- یک پایگاه داده MongoDB محلی یا حساب رایگان MongoDB Atlas
- یک ویرایشگر مانند VS Code

برای بررسی نسخه‌های نصب‌شده:

</div>

```bash
node --version
npm --version
```

<div dir="rtl">

---

## نصب و اجرای پروژه

### ۱. دریافت پروژه

اگر پروژه را از Git دریافت می‌کنید:

</div>

```bash
git clone <repository-url>
cd real-state-main
```

<div dir="rtl">

اگر فایل پروژه را به‌صورت ZIP دریافت کرده‌اید، آن را Extract کرده و Terminal را در پوشه اصلی پروژه باز کنید.

### ۲. نصب وابستگی‌ها

</div>

```bash
npm install
```

<div dir="rtl">

در صورتی که می‌خواهید دقیقاً نسخه‌های ثبت‌شده در `package-lock.json` نصب شوند، می‌توانید از دستور زیر استفاده کنید:

</div>

```bash
npm ci
```

<div dir="rtl">

### ۳. ساخت فایل متغیرهای محیطی

در ریشه پروژه فایل `.env.local` بسازید و متغیرهای بخش بعد را داخل آن قرار دهید.

### ۴. اجرای حالت توسعه

</div>

```bash
npm run dev
```

<div dir="rtl">

سپس آدرس زیر را در مرورگر باز کنید:

</div>

```text
http://localhost:3000
```

<div dir="rtl">

---

## تنظیم متغیرهای محیطی

نمونه فایل `.env.local`:

</div>

```env
NEXTAUTH_URL=http://localhost:3000
NEXTAUTH_SECRET=your-long-random-secret
MONGO_URI=mongodb+srv://USERNAME:PASSWORD@CLUSTER/DATABASE_NAME
```

<div dir="rtl">

### توضیح متغیرها

| متغیر | توضیح |
|---|---|
| `NEXTAUTH_URL` | آدرس اصلی اجرای برنامه؛ در محیط توسعه برابر `http://localhost:3000` است. |
| `NEXTAUTH_SECRET` | کلید محرمانه برای امضای داده‌های احراز هویت و Session |
| `MONGO_URI` | رشته اتصال کامل به پایگاه داده MongoDB |

برای تولید یک Secret تصادفی می‌توانید از دستور زیر استفاده کنید:

</div>

```bash
openssl rand -base64 32
```

<div dir="rtl">

> متغیرهای `MONGO_USER` و `MONGO_PASS` تنها در صورتی لازم هستند که رشته اتصال را با استفاده از آن‌ها بسازید. در پیاده‌سازی فعلی پروژه، اتصال مستقیماً از `MONGO_URI` خوانده می‌شود.

### نمونه اتصال به MongoDB محلی

</div>

```env
MONGO_URI=mongodb://127.0.0.1:27017/real-estate
```

<div dir="rtl">

### نمونه اتصال به MongoDB Atlas

</div>

```env
MONGO_URI=mongodb+srv://myUser:myPassword@cluster0.example.mongodb.net/real-estate
```

<div dir="rtl">

در MongoDB Atlas باید IP سیستم خود را در بخش Network Access مجاز کنید و نام کاربری و رمز عبور Database User را در رشته اتصال قرار دهید.

---

## ساخت کاربر مدیر

تمام کاربران جدید به‌صورت پیش‌فرض با نقش `USER` ساخته می‌شوند. برای دسترسی به پنل مدیریت، ابتدا از طریق سایت یک حساب عادی ایجاد کنید و سپس نقش آن را در MongoDB به `ADMIN` تغییر دهید.

### روش اول: MongoDB Compass

1. وارد دیتابیس پروژه شوید.
2. Collection مربوط به `users` را باز کنید.
3. کاربر موردنظر را بر اساس ایمیل پیدا کنید.
4. مقدار فیلد `role` را از `USER` به `ADMIN` تغییر دهید.
5. یک‌بار از حساب خارج شده و دوباره وارد شوید.

نمونه سند مدیر:

</div>

```json
{
  "email": "admin@example.com",
  "password": "<hashed-password>",
  "role": "ADMIN"
}
```

<div dir="rtl">

### روش دوم: اجرای Query در MongoDB

</div>

```javascript
db.users.updateOne(
  { email: "admin@example.com" },
  { $set: { role: "ADMIN" } }
)
```

<div dir="rtl">

پس از ورود با کاربر مدیر، گزینه «در انتظار تأیید» در Sidebar پنل نمایش داده می‌شود و مسیر `/admin` قابل دسترسی خواهد بود.

---

## راهنمای استفاده

### ثبت‌نام و ورود

1. از Header روی گزینه «ورود» کلیک کنید.
2. اگر حساب ندارید، وارد صفحه ثبت‌نام شوید.
3. ایمیل، رمز عبور و تکرار رمز عبور را وارد کنید.
4. پس از ثبت‌نام موفق، وارد صفحه ورود شوید.
5. با ایمیل و رمز عبور خود وارد حساب شوید.

### ثبت آگهی

1. وارد پنل کاربری شوید.
2. گزینه «ثبت آگهی» را انتخاب کنید.
3. اطلاعات زیر را وارد کنید:
   - عنوان آگهی
   - توضیحات
   - آدرس
   - شماره تماس
   - قیمت به تومان
   - نام بنگاه
   - دسته‌بندی ملک
   - امکانات رفاهی
   - قوانین
   - تاریخ ساخت
4. روی دکمه «ثبت آگهی» کلیک کنید.
5. آگهی در بخش «آگهی‌های من» نمایش داده می‌شود، اما تا زمان تأیید مدیر عمومی نیست.

### ویرایش و حذف آگهی

- در صفحه «آگهی‌های من»، دکمه «ویرایش» فرم همان آگهی را باز می‌کند.
- پس از تغییر اطلاعات، دکمه «ویرایش آگهی» اطلاعات را ذخیره می‌کند.
- دکمه «حذف آگهی» آگهی را از پایگاه داده حذف می‌کند.
- API سمت سرور بررسی می‌کند که فقط سازنده آگهی اجازه ویرایش یا حذف آن را داشته باشد.

### تأیید آگهی توسط مدیر

1. با حساب دارای نقش `ADMIN` وارد شوید.
2. وارد بخش «در انتظار تأیید» شوید.
3. آگهی‌های منتشرنشده را بررسی کنید.
4. روی «انتشار» کلیک کنید.
5. آگهی در صفحه عمومی `/buy-residential` نمایش داده می‌شود.

### مشاهده و فیلتر آگهی‌ها

- از Header وارد بخش «آگهی‌ها» شوید.
- با Sidebar، دسته‌بندی موردنظر را انتخاب کنید.
- با کلیک روی «مشاهده آگهی»، جزئیات کامل ملک نمایش داده می‌شود.
- دکمه اشتراک‌گذاری، آدرس صفحه فعلی را در Clipboard کپی می‌کند.

---

## صفحات و مسیرها

| مسیر | دسترسی | کاربرد |
|---|---|---|
| `/` | عمومی | صفحه اصلی، خدمات، دسته‌بندی‌ها و شهرهای پربازدید |
| `/signin` | مهمان | ورود به حساب کاربری |
| `/signup` | مهمان | ایجاد حساب کاربری |
| `/buy-residential` | عمومی | مشاهده آگهی‌های تأییدشده و فیلتر دسته‌بندی |
| `/buy-residential/[profileId]` | عمومی | نمایش جزئیات یک آگهی |
| `/dashboard` | کاربر واردشده | صفحه اصلی پنل و تاریخ عضویت |
| `/dashboard/add` | کاربر واردشده | ثبت آگهی جدید |
| `/dashboard/my-profiles` | کاربر واردشده | مشاهده آگهی‌های کاربر |
| `/dashboard/my-profiles/[profileId]` | کاربر واردشده | ویرایش آگهی |
| `/admin` | فقط مدیر | بررسی و انتشار آگهی‌های تأییدنشده |

پارامتر فیلتر دسته‌بندی به شکل زیر در Query String قرار می‌گیرد:

</div>

```text
/buy-residential?category=apartment
```

<div dir="rtl">

مقادیر معتبر دسته‌بندی:

- `apartment`: آپارتمان
- `villa`: ویلا
- `store`: مغازه
- `office`: دفتر

---

## APIهای پروژه

### احراز هویت

| متد | مسیر | کاربرد |
|---|---|---|
| `POST` | `/api/auth/signup` | ایجاد حساب کاربری جدید |
| `GET/POST` | `/api/auth/[...nextauth]` | مدیریت ورود، خروج و Session توسط NextAuth |

نمونه Body ثبت‌نام:

</div>

```json
{
  "email": "user@example.com",
  "password": "strong-password"
}
```

<div dir="rtl">

### مدیریت آگهی

| متد | مسیر | سطح دسترسی | کاربرد |
|---|---|---|---|
| `GET` | `/api/profile` | عمومی | دریافت آگهی‌های منتشرشده |
| `POST` | `/api/profile` | کاربر واردشده | ایجاد آگهی |
| `PATCH` | `/api/profile` | مالک آگهی | ویرایش آگهی |
| `DELETE` | `/api/profile/delete/[profileId]` | مالک آگهی | حذف آگهی |
| `PATCH` | `/api/profile/publish/[profileId]` | مدیر | انتشار آگهی |

نمونه Body ایجاد یا ویرایش آگهی:

</div>

```json
{
  "title": "آپارتمان دو خوابه",
  "description": "آپارتمان نورگیر و بازسازی‌شده",
  "location": "تهران، سعادت‌آباد",
  "phone": "09121234567",
  "realState": "خانه ایرانی",
  "price": 8500000000,
  "constructionDate": "2021-03-21T00:00:00.000Z",
  "category": "apartment",
  "amenities": ["آسانسور", "پارکینگ", "انباری"],
  "rules": ["امکان نگهداری حیوان خانگی وجود ندارد"]
}
```

<div dir="rtl">

در عملیات ویرایش، فیلد `_id` نیز باید همراه اطلاعات ارسال شود.

### کدهای وضعیت مهم

| کد | مفهوم در پروژه |
|---|---|
| `200` | درخواست با موفقیت انجام شده است. |
| `201` | حساب یا آگهی با موفقیت ایجاد شده است. |
| `400` | اطلاعات آگهی ناقص یا نامعتبر است. |
| `401` | کاربر وارد حساب نشده است. |
| `403` | کاربر اجازه انجام عملیات را ندارد. |
| `404` | کاربر یا داده موردنظر پیدا نشده است. |
| `422` | اطلاعات ثبت‌نام نامعتبر یا ایمیل تکراری است. |
| `500` | خطای داخلی سرور یا خطای اتصال به پایگاه داده |

---

## مدل‌های پایگاه داده

### مدل User

فایل مدل: `src/models/User.js`

| فیلد | نوع | توضیح |
|---|---|---|
| `email` | `String` | ایمیل کاربر |
| `password` | `String` | رمز عبور هش‌شده |
| `role` | `String` | نقش کاربر؛ مقدار پیش‌فرض `USER` |
| `createdAt` | `Date` | تاریخ ایجاد حساب |

### مدل Profile

فایل مدل: `src/models/Profile.js`

| فیلد | نوع | توضیح |
|---|---|---|
| `title` | `String` | عنوان آگهی |
| `description` | `String` | توضیحات کامل |
| `location` | `String` | آدرس ملک |
| `phone` | `String` | شماره تماس |
| `realState` | `String` | نام بنگاه املاک |
| `price` | `Number` | قیمت به تومان |
| `constructionDate` | `Date` | تاریخ ساخت |
| `category` | `String` | نوع ملک |
| `amenities` | `[String]` | امکانات رفاهی |
| `rules` | `[String]` | قوانین ملک |
| `userId` | `ObjectId` | شناسه کاربر سازنده آگهی |
| `published` | `Boolean` | وضعیت تأیید و انتشار |
| `createdAt` | `Date` | زمان ایجاد آگهی |
| `updatedAt` | `Date` | زمان آخرین ویرایش |

مقادیر مجاز فیلد `category` در Schema:

</div>

```javascript
["villa", "apartment", "store", "office"]
```

<div dir="rtl">

---

## ساختار پوشه‌ها

</div>

```text
real-state-main/
├── public/
│   ├── fonts/                    # فونت‌های محلی یکان‌بخ
│   └── images/                   # تصاویر دسته‌بندی املاک
├── src/
│   ├── app/
│   │   ├── (auth)/
│   │   │   ├── signin/          # صفحه ورود
│   │   │   └── signup/          # صفحه ثبت‌نام
│   │   ├── admin/               # پنل تأیید آگهی مدیر
│   │   ├── api/
│   │   │   ├── auth/            # API ثبت‌نام و NextAuth
│   │   │   └── profile/         # API ایجاد، دریافت، ویرایش، حذف و انتشار
│   │   ├── buy-residential/     # فهرست و جزئیات آگهی‌ها
│   │   ├── dashboard/           # پنل کاربری و مدیریت آگهی‌ها
│   │   ├── globals.css          # استایل عمومی
│   │   ├── layout.js            # Layout اصلی برنامه
│   │   └── page.js              # صفحه اصلی
│   ├── components/
│   │   ├── layout/              # Header، Footer و DashboardSidebar
│   │   ├── module/              # کامپوننت‌های کوچک و قابل استفاده مجدد
│   │   └── template/            # قالب اصلی صفحات
│   ├── constants/               # متن‌ها و آیکون‌های ثابت
│   ├── models/                  # مدل‌های User و Profile
│   ├── providers/               # SessionProvider مربوط به NextAuth
│   └── utils/                   # اتصال DB، احراز هویت، فونت و تبدیل اعداد
├── .env.local                   # متغیرهای محرمانه محیطی
├── jsconfig.json                # Aliasهای مسیر import
├── next.config.js               # تنظیمات Next.js
├── package.json                 # وابستگی‌ها و Scriptها
└── README.md
```

<div dir="rtl">

### Aliasهای تعریف‌شده

برای کوتاه‌تر و خواناتر شدن Importها، Aliasهای زیر در `jsconfig.json` تعریف شده‌اند:

| Alias | مسیر |
|---|---|
| `@/app/*` | `src/app/*` |
| `@/api/*` | `src/app/api/*` |
| `@/models/*` | `src/models/*` |
| `@/utils/*` | `src/utils/*` |
| `@/layout/*` | `src/components/layout/*` |
| `@/module/*` | `src/components/module/*` |
| `@/template/*` | `src/components/template/*` |
| `@/providers/*` | `src/providers/*` |
| `@/constants/*` | `src/constants/*` |
| `@/public/*` | `public/*` |

---

## اسکریپت‌های قابل اجرا

| دستور | کاربرد |
|---|---|
| `npm run dev` | اجرای پروژه در حالت توسعه |
| `npm run build` | ساخت نسخه Production |
| `npm run start` | اجرای نسخه Production پس از Build |
| `npm run lint` | بررسی کدها با ESLint |

برای اجرای نسخه Production:

</div>

```bash
npm run build
npm run start
```

<div dir="rtl">

---

## نکات امنیتی

- رمز عبور کاربران به‌صورت خام ذخیره نمی‌شود و با ضریب `12` توسط `bcryptjs` هش می‌شود.
- عملیات ایجاد، ویرایش و حذف آگهی نیازمند Session معتبر است.
- هنگام ویرایش و حذف، شناسه مالک آگهی با شناسه کاربر فعلی مقایسه می‌شود.
- انتشار آگهی تنها برای کاربر دارای نقش `ADMIN` مجاز است.
- مقدار `NEXTAUTH_SECRET` باید طولانی، تصادفی و محرمانه باشد.
- فایل‌های `.env` نباید در Repository عمومی Commit شوند.
- اطلاعات واقعی پایگاه داده، رمزها و Secretها نباید در README یا کد قرار گیرند.
- در محیط Production باید `NEXTAUTH_URL` برابر دامنه اصلی برنامه باشد.
- برای پروژه واقعی بهتر است اعتبارسنجی قوی‌تر ایمیل، رمز عبور، شماره تماس و ورودی‌های آگهی اضافه شود.

> نکته مهم: اگر فایل `.env` قبلاً وارد Git شده است، فقط اضافه‌کردن آن به `.gitignore` کافی نیست. باید Secretها و رمز پایگاه داده را تغییر دهید و فایل را از تاریخچه یا Tracking گیت نیز خارج کنید.

---

## سناریوی پیشنهادی ارائه

برای یک ارائه منظم می‌توانید مراحل زیر را اجرا کنید:

1. **معرفی مسئله:** نیاز به یک سامانه متمرکز برای ثبت و مشاهده آگهی‌های املاک
2. **معرفی فناوری‌ها:** Next.js، React، MongoDB، Mongoose و NextAuth
3. **نمایش صفحه اصلی:** معرفی دسته‌بندی‌ها، خدمات و رابط فارسی
4. **ثبت‌نام کاربر:** نمایش اعتبارسنجی تکرار رمز و ایجاد حساب
5. **ورود کاربر:** توضیح Credentials Provider، JWT و Session
6. **ثبت آگهی:** تکمیل فرم، انتخاب دسته‌بندی، امکانات و تاریخ شمسی
7. **نمایش پنل کاربر:** مشاهده آگهی ثبت‌شده و قابلیت ویرایش یا حذف
8. **توضیح Workflow انتشار:** بیان اینکه آگهی ابتدا `published: false` است
9. **ورود مدیر:** نمایش آگهی‌های در انتظار و تأیید یک آگهی
10. **نمایش عمومی:** مشاهده آگهی تأییدشده، فیلتر و صفحه جزئیات
11. **نمایش کد:** معرفی پوشه‌های `app`، `api`، `models` و `components`
12. **جمع‌بندی:** امنیت، کنترل دسترسی و پیشنهادهای توسعه آینده

### نکات کلیدی برای توضیح شفاهی

- Next.js امکان پیاده‌سازی Front-end و Back-end را در یک پروژه فراهم کرده است.
- Server Componentها برای دریافت مستقیم اطلاعات و Client Componentها برای تعاملات کاربر استفاده شده‌اند.
- NextAuth مدیریت Session را انجام می‌دهد و MongoDB اطلاعات کاربران و آگهی‌ها را نگهداری می‌کند.
- ارتباط کاربر و آگهی از طریق `userId` برقرار می‌شود.
- کنترل مالکیت مانع ویرایش یا حذف آگهی یک کاربر توسط کاربر دیگر می‌شود.
- نقش `ADMIN` یک سطح کنترل جداگانه برای انتشار محتوا ایجاد می‌کند.

---

## خطاهای رایج

### خطای اتصال به MongoDB

- مقدار `MONGO_URI` را بررسی کنید.
- نام کاربری و رمز MongoDB Atlas را بررسی کنید.
- IP سیستم را در Network Access اطلس مجاز کنید.
- اگر رمز شامل کاراکترهایی مانند `@` یا `/` است، آن را URL Encode کنید.

### خطای NextAuth یا Session

- وجود `NEXTAUTH_SECRET` را بررسی کنید.
- در محیط توسعه مقدار `NEXTAUTH_URL` باید `http://localhost:3000` باشد.
- پس از تغییر متغیرهای محیطی، سرور توسعه را متوقف و دوباره اجرا کنید.

### نمایش‌ندادن آگهی در صفحه عمومی

- آگهی‌های جدید به‌صورت پیش‌فرض منتشر نمی‌شوند.
- با حساب مدیر وارد شوید و آگهی را از مسیر `/admin` تأیید کنید.
- مقدار `published` سند آگهی را در MongoDB بررسی کنید.

### بازنشدن صفحه آگهی‌ها روی پورت دیگر

در فایل `src/app/buy-residential/page.js` آدرس API به‌صورت ثابت روی `http://localhost:3000/api/profile` نوشته شده است. بنابراین اجرای پروژه روی پورت یا دامنه دیگر نیازمند تغییر این آدرس یا جایگزینی دریافت API با Query مستقیم از پایگاه داده است.

### اشغال‌بودن پورت 3000

</div>

```bash
npm run dev -- -p 3001
```

<div dir="rtl">

در این حالت، علاوه بر تغییر `NEXTAUTH_URL`، نکته مربوط به آدرس ثابت API نیز باید در نظر گرفته شود.

---

## پیشنهادهای توسعه آینده

- افزودن آپلود تصویر برای آگهی‌ها
- جست‌وجو بر اساس عنوان، شهر یا محدوده
- فیلتر پیشرفته بر اساس قیمت و تاریخ ساخت
- صفحه‌بندی یا Infinite Scroll
- افزودن وضعیت رد آگهی و دلیل رد توسط مدیر
- امکان لغو انتشار آگهی
- افزودن تأیید ایمیل و بازیابی رمز عبور
- اعتبارسنجی ورودی‌ها با `Zod` یا کتابخانه مشابه
- افزودن Rate Limiting به APIهای احراز هویت
- افزودن تست‌های Unit، Integration و End-to-End
- طراحی کاملاً Responsive برای تمام صفحات پنل و جزئیات
- حذف آدرس ثابت `localhost` و استفاده از روش سازگار با Production
- استفاده از متغیر محیطی برای آدرس پایه API
- افزودن صفحه خطای اختصاصی، Loading UI و Not Found
- بهینه‌سازی Queryها و ایجاد Index برای ایمیل و فیلدهای جست‌وجو

---

## جمع‌بندی

این پروژه یک نمونه کامل از وب‌اپلیکیشن فول‌استک با Next.js است که مفاهیم مهمی مانند Routing، Server و Client Component، API Route، احراز هویت، Session، نقش‌های کاربری، اتصال به MongoDB، مدل‌سازی داده و عملیات CRUD را در یک سامانه واقعی املاک پیاده‌سازی می‌کند.

</div>

---

<div dir="ltr">

# Real Estate Buying and Rental Platform

A full-stack Persian web application for creating, managing, reviewing, and displaying real estate listings. Users can create an account, sign in to their dashboard, and add, edit, or delete property listings. Every newly created listing remains pending until an administrator reviews and publishes it, after which it becomes visible in the public listings section.

This project is built with **Next.js 13 and the App Router**. It uses **MongoDB** for data storage, **Mongoose** for data modeling, and **NextAuth.js** for authentication and session management.

---

## Table of Contents

- [Project Features](#project-features)
- [Technologies](#technologies)
- [Architecture and Application Flow](#architecture-and-application-flow)
- [Prerequisites](#prerequisites)
- [Installation and Setup](#installation-and-setup)
- [Environment Variables](#environment-variables)
- [Creating an Administrator](#creating-an-administrator)
- [Usage Guide](#usage-guide)
- [Pages and Routes](#pages-and-routes)
- [Project APIs](#project-apis)
- [Database Models](#database-models)
- [Project Structure](#project-structure)
- [Available Scripts](#available-scripts)
- [Security Notes](#security-notes)
- [Suggested Presentation Scenario](#suggested-presentation-scenario)
- [Common Errors](#common-errors)
- [Future Improvements](#future-improvements)

---

## Project Features

### Public Section

- Persian and right-to-left user interface
- Property categories for apartments, villas, stores, and offices
- Public list of approved property listings
- Filtering listings by property category
- Dedicated details page for every listing
- Displaying the title, address, description, price, and construction date
- Displaying property amenities and rules
- Displaying real estate agency information and phone number
- Converting English digits to Persian digits in the user interface
- Displaying dates in the Persian calendar format
- Copying the current listing URL for sharing

### Authentication

- User registration with email and password
- Duplicate email detection
- Password hashing with `bcryptjs`
- Authentication through a NextAuth `Credentials` provider
- JWT-based session management
- Redirecting authenticated users away from sign-in and sign-up pages
- Protecting the user dashboard and administrator panel
- Signing out from the current account

### User Dashboard

- Displaying the user's email and registration date
- Creating new property listings
- Adding multiple amenities and rules to a property
- Selecting the construction date with a Persian calendar
- Viewing all listings created by the current user
- Editing an existing listing
- Deleting a listing
- Keeping new listings pending until administrator approval

### Administrator Panel

- Identifying administrators through the `role` field
- Preventing regular users from accessing administrator routes
- Viewing listings awaiting approval
- Publishing listings after review
- Making approved listings available in the public section

---

## Technologies

| Technology | Purpose |
|---|---|
| `Next.js 13.4` | Main framework for the front end and back end |
| `React 18` | Component-based user interface development |
| `App Router` | Pages, layouts, dynamic routes, and API Route Handlers |
| `MongoDB` | NoSQL database |
| `Mongoose` | Schemas, models, and MongoDB communication |
| `NextAuth.js` | Authentication and session management |
| `bcryptjs` | Password hashing and verification |
| `CSS Modules` | Component-scoped styling |
| `react-hot-toast` | Success and error notifications |
| `react-icons` | User interface icons |
| `react-multi-date-picker` | Persian calendar date selection |
| `react-copy-to-clipboard` | Copying listing URLs |
| `next/font` | Optimized loading of the local Yekan Bakh font |

---

## Architecture and Application Flow

The project follows a **full-stack Next.js** architecture. Both the user interface and server-side APIs are implemented inside the same application.

### Presentation Layer

Application pages are located in `src/app`, while reusable user interface components are stored in `src/components`. Components are divided into three main groups:

- `layout`: Shared page elements such as the Header, Footer, and dashboard Sidebar
- `template`: The main structure of each page
- `module`: Smaller reusable components such as cards, inputs, lists, and loaders

### Server Logic Layer

Route Handlers inside `src/app/api` process registration and property listing requests. These APIs handle initial validation, session verification, authorization, and database communication.

### Data Layer

The application contains two primary database models:

- `User`: Stores account information and user roles
- `Profile`: Stores property listing information

Every property listing is connected to its creator through the `userId` field.

### Listing Publication Flow

1. A visitor creates an account and signs in.
2. The user creates a new property listing from the dashboard.
3. The listing is stored in MongoDB with the default value `published: false`.
4. An administrator views the pending listing in the administrator panel.
5. The administrator selects the publish action.
6. The `published` value changes to `true`.
7. The approved listing becomes visible on the public listings page.

---

## Prerequisites

Before running the project, make sure the following requirements are available:

- `Node.js` version `16.8` or newer; Node.js `18 LTS` is recommended.
- `npm`
- A local MongoDB database or a free MongoDB Atlas account
- A code editor such as Visual Studio Code

Check the installed versions with:

</div>

```bash
node --version
npm --version
```

<div dir="ltr">

---

## Installation and Setup

### 1. Get the Project

If the project is hosted in a Git repository:

</div>

```bash
git clone <repository-url>
cd real-state-main
```

<div dir="ltr">

If you received the project as a ZIP archive, extract it and open a terminal in the project root directory.

### 2. Install Dependencies

</div>

```bash
npm install
```

<div dir="ltr">

To install exactly the dependency versions recorded in `package-lock.json`, use:

</div>

```bash
npm ci
```

<div dir="ltr">

### 3. Create the Environment File

Create a `.env.local` file in the project root and add the variables described in the next section.

### 4. Run the Development Server

</div>

```bash
npm run dev
```

<div dir="ltr">

Open the following address in your browser:

</div>

```text
http://localhost:3000
```

<div dir="ltr">

---

## Environment Variables

Example `.env.local` file:

</div>

```env
NEXTAUTH_URL=http://localhost:3000
NEXTAUTH_SECRET=your-long-random-secret
MONGO_URI=mongodb+srv://USERNAME:PASSWORD@CLUSTER/DATABASE_NAME
```

<div dir="ltr">

### Variable Descriptions

| Variable | Description |
|---|---|
| `NEXTAUTH_URL` | Main application URL; use `http://localhost:3000` during local development. |
| `NEXTAUTH_SECRET` | Private key used to sign authentication and session data |
| `MONGO_URI` | Complete MongoDB connection string |

Generate a random NextAuth secret with:

</div>

```bash
openssl rand -base64 32
```

<div dir="ltr">

> The `MONGO_USER` and `MONGO_PASS` variables are only necessary if you use them to construct the database connection string. The current implementation connects directly through `MONGO_URI`.

### Local MongoDB Example

</div>

```env
MONGO_URI=mongodb://127.0.0.1:27017/real-estate
```

<div dir="ltr">

### MongoDB Atlas Example

</div>

```env
MONGO_URI=mongodb+srv://myUser:myPassword@cluster0.example.mongodb.net/real-estate
```

<div dir="ltr">

When using MongoDB Atlas, allow your current IP address in Network Access and include the correct Database User credentials in the connection string.

---

## Creating an Administrator

Every newly registered account receives the default `USER` role. To access the administrator panel, first register a regular account through the application and then change its role to `ADMIN` in MongoDB.

### Method 1: MongoDB Compass

1. Open the project's database.
2. Open the `users` collection.
3. Find the desired user by email address.
4. Change the `role` field from `USER` to `ADMIN`.
5. Sign out of the application and sign in again.

Example administrator document:

</div>

```json
{
  "email": "admin@example.com",
  "password": "<hashed-password>",
  "role": "ADMIN"
}
```

<div dir="ltr">

### Method 2: MongoDB Query

</div>

```javascript
db.users.updateOne(
  { email: "admin@example.com" },
  { $set: { role: "ADMIN" } }
)
```

<div dir="ltr">

After signing in with an administrator account, the pending approval option becomes visible in the dashboard Sidebar and the `/admin` route becomes accessible.

---

## Usage Guide

### Registration and Sign-In

1. Select the sign-in option in the Header.
2. If you do not have an account, navigate to the registration page.
3. Enter an email address, password, and password confirmation.
4. After successful registration, navigate to the sign-in page.
5. Sign in with the registered email and password.

### Creating a Listing

1. Sign in and open the user dashboard.
2. Select the add listing option.
3. Enter the following information:
   - Listing title
   - Description
   - Property address
   - Phone number
   - Price in Tomans
   - Real estate agency name
   - Property category
   - Amenities
   - Property rules
   - Construction date
4. Select the submit listing button.
5. The listing appears in the user's listings page but remains unavailable publicly until administrator approval.

### Editing and Deleting a Listing

- On the user's listings page, the edit button opens the form with the current listing data.
- After changing the information, the update listing button saves the changes.
- The delete listing button removes the listing from the database.
- The server-side API verifies that only the listing owner can edit or delete it.

### Approving a Listing as an Administrator

1. Sign in with an account that has the `ADMIN` role.
2. Open the pending approval section.
3. Review the unpublished listings.
4. Select the publish button.
5. The listing becomes available at `/buy-residential`.

### Viewing and Filtering Listings

- Use the Header to open the public listings page.
- Select a property category from the Sidebar.
- Select the view listing link to open the full property details.
- The share button copies the current page URL to the Clipboard.

---

## Pages and Routes

| Route | Access | Purpose |
|---|---|---|
| `/` | Public | Home page, services, property categories, and popular cities |
| `/signin` | Guest | Sign in to an existing account |
| `/signup` | Guest | Create a new user account |
| `/buy-residential` | Public | View approved listings and filter by category |
| `/buy-residential/[profileId]` | Public | View the details of a property listing |
| `/dashboard` | Authenticated user | Dashboard home and registration date |
| `/dashboard/add` | Authenticated user | Create a new property listing |
| `/dashboard/my-profiles` | Authenticated user | View the current user's listings |
| `/dashboard/my-profiles/[profileId]` | Authenticated user | Edit a property listing |
| `/admin` | Administrator only | Review and publish pending listings |

The category filter is provided through the Query String:

</div>

```text
/buy-residential?category=apartment
```

<div dir="ltr">

Supported category values:

- `apartment`: Apartment
- `villa`: Villa
- `store`: Store
- `office`: Office

---

## Project APIs

### Authentication

| Method | Route | Purpose |
|---|---|---|
| `POST` | `/api/auth/signup` | Create a new user account |
| `GET/POST` | `/api/auth/[...nextauth]` | Handle sign-in, sign-out, and sessions through NextAuth |

Example registration request body:

</div>

```json
{
  "email": "user@example.com",
  "password": "strong-password"
}
```

<div dir="ltr">

### Property Listing Management

| Method | Route | Access Level | Purpose |
|---|---|---|---|
| `GET` | `/api/profile` | Public | Retrieve published listings |
| `POST` | `/api/profile` | Authenticated user | Create a listing |
| `PATCH` | `/api/profile` | Listing owner | Update a listing |
| `DELETE` | `/api/profile/delete/[profileId]` | Listing owner | Delete a listing |
| `PATCH` | `/api/profile/publish/[profileId]` | Administrator | Publish a listing |

Example request body for creating or updating a listing:

</div>

```json
{
  "title": "Two-Bedroom Apartment",
  "description": "A bright and recently renovated apartment",
  "location": "Saadat Abad, Tehran",
  "phone": "09121234567",
  "realState": "Iranian Home",
  "price": 8500000000,
  "constructionDate": "2021-03-21T00:00:00.000Z",
  "category": "apartment",
  "amenities": ["Elevator", "Parking", "Storage"],
  "rules": ["Pets are not allowed"]
}
```

<div dir="ltr">

The `_id` field must also be included when updating an existing listing.

### Important HTTP Status Codes

| Code | Meaning in This Project |
|---|---|
| `200` | The request completed successfully. |
| `201` | A user account or listing was created successfully. |
| `400` | The listing information is incomplete or invalid. |
| `401` | The user is not authenticated. |
| `403` | The user is not authorized to perform the operation. |
| `404` | The requested user or resource was not found. |
| `422` | Registration data is invalid or the email already exists. |
| `500` | An internal server or database connection error occurred. |

---

## Database Models

### User Model

Model file: `src/models/User.js`

| Field | Type | Description |
|---|---|---|
| `email` | `String` | User email address |
| `password` | `String` | Hashed password |
| `role` | `String` | User role; defaults to `USER` |
| `createdAt` | `Date` | Account creation date |

### Profile Model

Model file: `src/models/Profile.js`

| Field | Type | Description |
|---|---|---|
| `title` | `String` | Listing title |
| `description` | `String` | Full property description |
| `location` | `String` | Property address |
| `phone` | `String` | Contact phone number |
| `realState` | `String` | Real estate agency name |
| `price` | `Number` | Price in Tomans |
| `constructionDate` | `Date` | Property construction date |
| `category` | `String` | Property type |
| `amenities` | `[String]` | Property amenities |
| `rules` | `[String]` | Property rules |
| `userId` | `ObjectId` | Identifier of the listing creator |
| `published` | `Boolean` | Approval and publication status |
| `createdAt` | `Date` | Listing creation time |
| `updatedAt` | `Date` | Last update time |

Allowed `category` values in the Schema:

</div>

```javascript
["villa", "apartment", "store", "office"]
```

<div dir="ltr">

---

## Project Structure

</div>

```text
real-state-main/
├── public/
│   ├── fonts/                    # Local Yekan Bakh font files
│   └── images/                   # Property category images
├── src/
│   ├── app/
│   │   ├── (auth)/
│   │   │   ├── signin/          # Sign-in page
│   │   │   └── signup/          # Registration page
│   │   ├── admin/               # Administrator approval panel
│   │   ├── api/
│   │   │   ├── auth/            # Registration and NextAuth APIs
│   │   │   └── profile/         # Listing CRUD and publication APIs
│   │   ├── buy-residential/     # Public listing and details pages
│   │   ├── dashboard/           # User dashboard and listing management
│   │   ├── globals.css          # Global styles
│   │   ├── layout.js            # Root application layout
│   │   └── page.js              # Home page
│   ├── components/
│   │   ├── layout/              # Header, Footer, and DashboardSidebar
│   │   ├── module/              # Small reusable components
│   │   └── template/            # Main page templates
│   ├── constants/               # Static text and icons
│   ├── models/                  # User and Profile models
│   ├── providers/               # NextAuth SessionProvider
│   └── utils/                   # DB connection, auth, fonts, and digit helpers
├── .env.local                   # Private environment variables
├── jsconfig.json                # Import path aliases
├── next.config.js               # Next.js configuration
├── package.json                 # Dependencies and scripts
└── README.md
```

<div dir="ltr">

### Configured Import Aliases

The following aliases are defined in `jsconfig.json` to keep imports shorter and easier to read:

| Alias | Path |
|---|---|
| `@/app/*` | `src/app/*` |
| `@/api/*` | `src/app/api/*` |
| `@/models/*` | `src/models/*` |
| `@/utils/*` | `src/utils/*` |
| `@/layout/*` | `src/components/layout/*` |
| `@/module/*` | `src/components/module/*` |
| `@/template/*` | `src/components/template/*` |
| `@/providers/*` | `src/providers/*` |
| `@/constants/*` | `src/constants/*` |
| `@/public/*` | `public/*` |

---

## Available Scripts

| Command | Purpose |
|---|---|
| `npm run dev` | Run the application in development mode |
| `npm run build` | Create a production build |
| `npm run start` | Start the production server after building |
| `npm run lint` | Check the source code with ESLint |

Run the production version with:

</div>

```bash
npm run build
npm run start
```

<div dir="ltr">

---

## Security Notes

- User passwords are never stored as plain text and are hashed by `bcryptjs` with a cost factor of `12`.
- Creating, updating, and deleting property listings requires a valid session.
- During update and deletion operations, the listing owner identifier is compared with the current user identifier.
- Only accounts with the `ADMIN` role can publish listings.
- `NEXTAUTH_SECRET` must be long, random, and private.
- Environment files must not be committed to a public repository.
- Real database credentials, passwords, and secrets must never be placed in the README or source code.
- In production, `NEXTAUTH_URL` must match the application's public domain.
- A production-ready version should implement stronger validation for email addresses, passwords, phone numbers, and listing inputs.

> Important: If an `.env` file has already been tracked by Git, adding it to `.gitignore` is not sufficient. Rotate all exposed secrets and database credentials, then remove the file from Git tracking and, if necessary, repository history.

---

## Suggested Presentation Scenario

The following order provides a clear project demonstration:

1. **Problem introduction:** The need for a centralized system to create and browse real estate listings
2. **Technology overview:** Next.js, React, MongoDB, Mongoose, and NextAuth
3. **Home page demonstration:** Categories, services, and the Persian interface
4. **User registration:** Password confirmation validation and account creation
5. **User sign-in:** Credentials Provider, JWT, and session management
6. **Listing creation:** Form fields, category selection, amenities, and Persian date picker
7. **User dashboard:** Viewing, editing, and deleting the newly created listing
8. **Publication workflow:** Explaining why a new listing starts with `published: false`
9. **Administrator sign-in:** Reviewing and approving a pending listing
10. **Public listing demonstration:** Viewing the approved listing, filtering, and opening its details
11. **Code structure:** Introducing the `app`, `api`, `models`, and `components` directories
12. **Conclusion:** Security, authorization, and possible future improvements

### Key Points for an Oral Presentation

- Next.js makes it possible to implement the front end and back end in the same project.
- Server Components are used for server-side data retrieval, while Client Components handle user interactions.
- NextAuth manages sessions, while MongoDB stores user accounts and property listings.
- The `userId` field creates the relationship between users and their listings.
- Ownership verification prevents one user from editing or deleting another user's listing.
- The `ADMIN` role provides a separate authorization level for content publication.

---

## Common Errors

### MongoDB Connection Error

- Verify the value of `MONGO_URI`.
- Check the MongoDB Atlas username and password.
- Allow your current IP address in Atlas Network Access.
- URL-encode passwords containing special characters such as `@` or `/`.

### NextAuth or Session Error

- Verify that `NEXTAUTH_SECRET` exists.
- During local development, `NEXTAUTH_URL` should be `http://localhost:3000`.
- Restart the development server after changing environment variables.

### A Listing Does Not Appear Publicly

- New listings are unpublished by default.
- Sign in as an administrator and approve the listing through `/admin`.
- Check the listing's `published` value in MongoDB.

### The Listings Page Does Not Open on Another Port

The API URL in `src/app/buy-residential/page.js` is hard-coded as `http://localhost:3000/api/profile`. Running the application on a different port or domain therefore requires updating this URL or replacing the API request with a direct database query.

### Port 3000 Is Already in Use

</div>

```bash
npm run dev -- -p 3001
```

<div dir="ltr">

When using another port, update `NEXTAUTH_URL` and consider the hard-coded API URL described above.

---

## Future Improvements

- Add image uploading for property listings
- Add search by title, city, or neighborhood
- Add advanced filtering by price and construction date
- Add pagination or Infinite Scroll
- Add a rejected status and rejection reason for administrators
- Allow administrators to unpublish listings
- Add email verification and password recovery
- Validate inputs with `Zod` or a similar library
- Add Rate Limiting to authentication APIs
- Add Unit, Integration, and End-to-End tests
- Make every dashboard and details page fully responsive
- Remove the hard-coded `localhost` URL and use a production-compatible approach
- Use an environment variable for the API base URL
- Add custom error, Loading UI, and Not Found pages
- Optimize database queries and add indexes for email and searchable fields

---

## Conclusion

This project is a complete example of a full-stack Next.js application. It demonstrates important concepts such as Routing, Server and Client Components, API Route Handlers, authentication, sessions, user roles, MongoDB integration, data modeling, authorization, and CRUD operations in a practical real estate platform.

</div>
