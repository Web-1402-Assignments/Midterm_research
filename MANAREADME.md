<div dir="rtl">
<h1>GORM</h1>
<h2>نویسندگان</h2>
<li>مانا عباس‌زاده</li>
<li>محمدمهدی اکبر</li>
<li>دانیال غریب</li>
<hr></hr>
<br></br>
<h2>چیست؟ ORM</h2>
<hr></hr>
ORM یا Object-Relational Mapping یک تکنیک برنامه نویسی است که به توسعه دهندگان اجازه می دهد با استفاده از زبان های برنامه نویسی شی گرا با پایگاه های داده تعامل داشته باشند. با نگاشت جداول پایگاه داده به اشیا، سطح بالاتری از انتزاع را فراهم می کند و توسعه دهندگان را قادر می سازد تا عملیات پایگاه داده را با استفاده از پارادایم های شی گرا و بدون نیاز به نوشتن کدهای طولانی SQL انجام دهند. بنابراین هدف اصلی automized کردن آبجت ها است به صورتی که بتوانند در پایگاه داده ذخیره شوند و در عین حال خصوصیات آبجکت ها و روابط آنها حفظ شود تا در صورت نیاز بتوان آنها را به عنوان اشیاء بارگذاری مجدد کرد. آبجکت هایی که روی آنها این قابلیت ذخیره سازی و بازیابی به درستی صورت گیرد، اشیاء (آبجکت های) پایدار هستند. <br>از فواید ORM میتوان به صرفه جویی در زمان و هزینه برنامه نویس اشاره کرد.<br> ORM ها انواع مختلفی دارند که یکی از آنها GORM است. GORM یک کتابخانه ORM برای زبان برنامه نویسی go است. در ادامه به توضیح بیشتر این کتابخانه و دیگر انواع ORM ها می پردازیم.
<br></br>
<h2>تاریخچه ORM</h2>
<hr></hr>
تاریخچه ORM به دهه 1980 برمی گردد، زمانی که محققان و توسعه دهندگان شروع به کشف راه هایی برای پر کردن شکاف بین پایگاه های داده رابطه ای و زبان های برنامه نویسی شی گرا کردند. اولین فریمورک ORM موفق تجاری، TOPLink محصولی از Smalltalk بود که بعدا به نسخه اولیه جاوا منتقل شد. 
<br >TOPLink چیزی را پیاده سازی کرد که در اصطلاح امروزی به آن الگوی نقشه برداری داده (data mapping pattern) می گویند. رقیب اصلی آن، فریمورک Smalltalk دیگری به نام ParcPlace ObjectLens بود.
<br >دیگر چارچوب ها و کتابخانه های جالب آن زمان رویکردی کاملا متفاوت داشتند. به طور  مثال Rogue Wave DBTools در C++ استاندارد Streams را برای ارسال کوئری های SQL به اشیا بارگذاری کرد، در حالی که سیستم عامل اولیه NeXT DbKit را، با مفهوم استاندارد یک لایه انتزاعی  پایگاه داده (database abstraction layer) معرفی کرد.
<br></br>
<h2>انواع ORM</h2>
<hr></hr>
با گذشت زمان، چارچوب‌های ORM به زبان‌های برنامه‌نویسی مختلف نفوذ کردند و به ابزاری رایج در بسیاری از پروژه‌های توسعه نرم‌افزار تبدیل شدند. 
<br>برخی از انواع ORM ها عبارتند از: </br>
<h3><li>Hibernate :</h3>
Hibernate ORM (یا به سادگی Hibernate) یک ابزار ORM برای زبان برنامه نویسی جاوا است که یک framework برای نگاشت یک مدل دامنه شی گرا به یک پایگاه داده رابطه ای فراهم می کند.
<br>ویژگی اصلی Hibernate نگاشت از کلاس های جاوا به جداول پایگاه داده و نگاشت از انواع داده جاوا به انواع داده های SQL است. Hibernate همچنین امکانات پرس و جو و بازیابی داده را فراهم می کند. SQL call  ایجاد می‌کند و توسعه‌دهنده دیگر نیاز نیست مدیریت دستی و تبدیل the result set object را انجام دهد.</br>
<br>از مشکلات Hibernate میتوان به عدم تطابق امپدانس شی-رابطه ای با جایگزینی دسترسی های مستقیم و دائمی پایگاه داده با توابع مدیریت شی سطح بالا اشاره کرد.</br>
<br>تاریخچه و سیر تکامل:</br>
Hibernate در سال 2001 توسط Gavin King و همکارانش از Cirrus Technologies به عنوان جایگزینی برای استفاده از existing EJB2-style beans آغاز شد. هدف اولیه ارائه قابلیت‌های ماندگاری، بهتر از آنهایی که توسط EJB2 ارائه شده بود، بود( با ساده سازی پیچیدگی ها و تکمیل برخی ویژگی ها).
<br>در اوایل سال 2003، تیم توسعه Hibernate نسخه های Hibernate2 را آغاز کرد که پیشرفت های قابل توجهی را نسبت به نسخه اول ارائه کرد.</br>
<br> سال 2005، Hibernate نسخه 3.0 منتشر شد. ویژگی های کلیدی شامل معماری جدید Interceptor/Callback، فیلترهای تعریف شده توسط کاربر و حاشیه نویسی JDK 5.0 (Java metadata feature) بود.
از سال 2010، Hibernate 3 (نسخه 3.5.0 و بالاتر) یک پیاده سازی تایید شده از مشخصات Java Persistence API 2.0 از طریق یک پوشش برای ماژول Core بود که مطابقت با استاندارد JSR 317 را فراهم می کرد.<br> دسامبر 2011، Hibernate Core 4.0.0 Final منتشر شد. این نسخه شامل ویژگی‌های جدیدی مانند پشتیبانی چند اجاره‌ای (multi-tenancy support)، معرفی ServiceRegistry (تغییر عمده در نحوه ساخت و مدیریت سرویس‌های Hibernate)، باز کردن بهتر جلسه از SessionFactory، ادغام بهبود یافته از طریق org.hibernate.integrator.spi.Integrator و کشف خودکار، پشتیبانی بین المللی، کدهای پیام در ورود به سیستم، و تمایز بیشتر بین API، SPI یا کلاس های پیاده سازی بود.<br> دسامبر 2012، Hibernate ORM 4.1.9 Final منتشر شد.<br> مارس 2013، Hibernate ORM 4.2 Final منتشر شد.<br> دسامبر 2013، Hibernate ORM 4.3.0 Final منتشر شد(دارای Java Persistence API 2.1).<br> سپتامبر 2015، Hibernate ORM 5.0.2 Final منتشر شد که پشتیبانی bootstrapping، hibernate-java8، hibernate-spatial، Karaf را بهبود بخشید.<br> نوامبر 2018، Hibernate ORM 5.1.17 Final منتشر شد. این آخرین نسخه از سری 5.1 است.<br> اکتبر 2018، Hibernate ORM 5.3 Final منتشر شد که قابلیت legacy cache Java Persistence API 2.2 را داشت.<br> دسامبر 2018، Hibernate ORM 5.4.0 Final منتشر شد.<br> اکتبر 2022، Hibernate ORM 6.1.4 Final منتشر شد.</br>
<br></br>
<h3><li>ActiveRecord (Ruby on Rails) :</h3>
ActiveRecord یک framework ORM است که در چارچوب توسعه وب Ruby on Rails ایجاد شده است. این framework از اصل contract- over-configuration پیروی می کند و مجموعه ای غنی از روش ها را برای عملیات پایگاه داده ارائه می دهد. ActiveRecord به دلیل سادگی و بهره وری که به توسعه دهندگان Ruby on Rails ارائه می دهد محبوبیت پیدا کرد.
<br>الگوی ActiveRecord به این صورت است که یک جدول یا نمای پایگاه داده در یک کلاس پیچیده شده است. بنابراین، یک نمونه شی به یک ردیف در جدول گره خورده است. پس از ایجاد یک شی، یک ردیف جدید به جدول اضافه می شود. هر شیء بارگذاری شده اطلاعات خود را از پایگاه داده دریافت می کند. هنگامی که یک شی به روز می شود، ردیف مربوطه در جدول نیز به روز می شود. کلاس wrapper، متدها یا ویژگی های دسترسی را برای هر ستون در جدول یا view پیاده سازی می کند<br>Martin Fowler در سال ۲۰۰۳ در کتاب Patterns of Enterprise Application Architecture از آن نام برده است.<br>از مشکلات این نوع framework میتوان به موارد زیر اشاره کرد:</br>
<br>آزمایش پذیری (testability) :
به دلیل جفت شدن تعامل پایگاه داده و منطق برنامه هنگام استفاده از الگوی active record، unit test  یک شی active record  بدون پایگاه داده دشوار می شود.</br>
<br>اصل مسئولیت واحد و تفکیک نگرانی ها (The principle of single responsibility and separation of concerns) :
مشکل دیگر این الگو این است که، به دلیل جفت شدن قوی تعامل پایگاه داده و منطق برنامه، یک شی active record  از اصل مسئولیت واحد و جداسازی نگرانی ها پیروی نمی کند (برخلاف معماری چند لایه که به درستی به این شیوه ها رسیدگی می کند). به همین دلیل، الگوی active record بهتر است در برنامه‌های کاربردی ساده استفاده شود که همگی یا به صورت forms over data با عملکرد CRUD باشند یا فقط به عنوان بخشی از یک معماری هستند.</br>
<br>سیستم های توزیع شده (distributed systems) :
الگوهای مبتنی بر record در سیستم‌های توزیع‌شده ضعیف عمل می‌کنند، به‌خصوص در مواردی که همروندی (concurrency) غیرممکن است (مثلاً حالت offline). یعنی دو آپدیت هر دو ممکن است یک فیلد صحیح داشته باشند اما فقط یکی از دو رکورد می تواند برنده شود.</br>
<br></br>
<h3><li>Entity Framework :</h3>
Entity Framework یک چارچوب ORM است که توسط مایکروسافت برای اکوسیستم دات نت توسعه یافته است.  در ابتدا به عنوان بخشی جدایی ناپذیر از NET Framework. عرضه شد، اما با شروع نسخه 6.0 Entity Framework به طور جداگانه از NET Framework. تحویل داده شد. 
برخی از ویژگی هایی که ارائه می دهد عبارتند از: تولید خودکار طرحواره (automatic schema generation)، پرس و جو (querying)، ردیابی تغییر (change tracking)، و مدیریت تراکنش (transaction management)<br>Entity Framework در طول زمان تکامل یافته است و هر نسخه ویژگی ها و پیشرفت های جدیدی را ارائه می دهد.<br>Entity Framework 6.4 آخرین نسخه از framework کلاسیک بود. اگرچه Entity Framework 6 هنوز پشتیبانی می‌شود، اما دیگر در حال توسعه نیست و فقط مشکلات امنیتی اش رفع می شوند.<br>framework جدیدی به نام Entity Framework Core (EF Core) در سال 2016 با ویژگی های مشابه اما نه کامل معرفی شد. شماره گذاری نسخه این framework از 1.0 مجدداً شروع شد و آخرین نسخه آن EF Core 7.0 است.</br>
<br></br>
<h3><li>Django ORM :</h3>
Django ORM ORM یک built-in ORM برای framework وب جنگو در پایتون است و یک API سطح بالا برای عملیات پایگاه داده ارائه می دهد که به توسعه دهندگان این امکان را می دهد تا مدل ها را تعریف کرده و با استفاده از کد پایتون کوئری ها را انجام دهند. Django ORM به دلیل سهولت استفاده و ادغام دقیق با ویژگی های توسعه وب جنگو شناخته شده است. <br>جنگو در پاییز 2003 تولید شد، زمانی که برنامه نویسان وب در روزنامه Lawrence Journal-World، Adrian Holovaty و Simon Willison، شروع به استفاده از Python برای ساخت برنامه کردند. در جولای 2005 تحت مجوز BSD به صورت عمومی منتشر شد. این چارچوب به افتخار گیتاریست جانگو راینهارت نامگذاری شد.
در ژوئن 2008، اعلام شد که یک بنیاد نرم افزاری جنگو (DSF) که به تازگی تشکیل شده است، جنگو را در آینده حفظ خواهد کرد.
<br></br>
<h3><li>GORM (GO) :</h3>
GORM یک کتابخانه ORM برای زبان برنامه نویسی Go است که از ActiveRecord از Ruby on Rails الهام گرفته شده است. ویژگی هایی مانند ایجاد جدول خودکار (automatic table creation)، پرس و جو (queries)، انجمن ها (forums) و مدیریت تراکنش ها (transaction management) را ارائه می دهد. همچنین توسط یک API بصری و رسا عملیات پایگاه داده را ساده می کند و boilerplate code را کاهش می دهد.<br>تاریخچه GORM به سال 2013 برمی گردد و توسط توسعه دهنده ای به نام Jinzhu ساخته شد. هدف اصلی آن ساده سازی عملیات پایگاه داده در Go و ارائه سطح بالاتری از انتزاع (abstraction) برای کار با پایگاه داده بود.
<br>GORM از زمان آغاز به کار به دلیل سادگی، انعطاف‌پذیری، ویژگی‌های قدرتمند و پشتیبانی از انواع مختلف پایگاه داده از جمله MySQL، PostgreSQL، SQLite و غیره محبوبیت قابل توجهی در جامعه Go به دست آورد و
در طول سال‌ها، توسط توسعه دهندگان زیادی تکامل یافت و تبدیل به یک ORM پرکاربرد در اکوسیستم Go شد.
<br></br>
انواع دیگر ORM ها:
<h3><li>Java Persistence API </h3>
<h3><li>Apache OpenJPA </h3>
<h3><li>EclipseLink </h3>
<h3><li>RedBeanPHP </h3>
<h3><li>JOOQ Object Oriented Querying </h3>
<h3><li>Dapper ORM </h3>
<h3><li>SQLObject </h3>
<h3><li>Doctrine </h3>
<h3><li>Propel </h3>
<h3><li>Ebean </h3>
<h3><li>TopLink </h3>
<h3><li>Hibernate search </h3>
<br></br>
<h2>CRUD interface</h2>
<hr></hr>
GRUD interface به مجموعه ای از عملیات ها اشاره دارد که می توانند بر روی یک پایگاه داده با استفاده از کتابخانه GORM انجام شوند. CRUD مخفف Create، Read، Update و Delete است که عملیات های اساسی در کار با داده های پایدار هستند.
<br></br>
<h3><li>Create :</h3>
<br>
<h3>Create Record</h3>

ما برای درست کردن یک record روش های مختلفی را میتوانیم پیاده سازی کنیم که در ادامه انواع آن توضیح داده شده است.

```go
user := User{Name: "Jinzhu", Age: 18, Birthday: time.Now()}

result := db.Create(&user) // pass pointer of data to Create

user.ID             // returns inserted data's primary key
result.Error        // returns error
result.RowsAffected // returns inserted records count

```
در تکه کد بالا ابتدا یک متغیر user از جنس User میسازیم. این متغیر دارای اسم و سن و زمان تولد است. db یک instance از GORM است. ما پوینتری از اطلاعات یوزر را به تابع Create از GORM می دهیم و نتیجه را در result ذخیره می کنیم. با استفاده از <code>user.ID</code> id یوزر موردنظر به ما داده می شود. <code>result.Error</code> اگر در اجرای تابع Create مشکلی وجود داشته باشد ارور آن را برمی گرداند. <code>result.RowsAffected</code> تعداد سطرهای جدید اضافه شده در اثر اجرای تابع Create را به ما می دهد.<br> همچنین می توانیم به جای یک یوزر چند یوزر داشته باشیم که باید مانند کد زیر عمل کنیم:
‍<br>

```go
users := []*User{
  User{Name: "Jinzhu", Age: 18, Birthday: time.Now()},
  User{Name: "Jackson", Age: 19, Birthday: time.Now()},
}

result := db.Create(users) // pass a slice to insert multiple row

result.Error        // returns error
result.RowsAffected // returns inserted records count
```
<br></br>
<h3>Create Record With Selected Fields</h3>

برای درست کردن یک record برای آبجکت user در دیتابیس میتوانیم ستون های موردنظرمان را select کنیم و به آنها مقدار دهیم. مانند کد زیر:
<br>

```go
db.Select("Name", "Age", "CreatedAt").Create(&user)
// INSERT INTO `users` (`name`,`age`,`created_at`) VALUES ("jinzhu", 18, "2020-07-04 11:05:21.775")
```
<br>
کد زیر برای درست کردن یک record جدید در دیتابیس است که ستون های موردنظر رااز SQL INSERT درنظر نگرفته است. در نهایت SQL موردنظر فقط ستون های مانده را در دیتابیس ذخیره خواهد کرد.

<br>

```go
db.Omit("Name", "Age", "CreatedAt").Create(&user)
// INSERT INTO `users` (`birthday`,`updated_at`) VALUES ("2020-01-01 00:00:00.000", "2020-07-04 11:05:21.775")
```
<br></br>
<h3>Batch insert</h3>
batch insert در GORM یعنی insert کردن چندین رکورد در یک عملیات به جای insert کردن چندین رکورد به صورت تک به تک. از فواید این روش می توان به افزایش درج کارآمدتر داده ها و کاهش هزینه های ناشی از چندین عملیات دیتابیس اشاره کرد. کد زیر نمونه ای از این روش است:

<br>

```go
var users = []User{{Name: "jinzhu1"}, {Name: "jinzhu2"}, {Name: "jinzhu3"}}
db.Create(&users)

for _, user := range users {
  user.ID // 1, 2, 3
}
```
در این تکه کد ابتدا یک struct از User ها به نام users تعریف می کنیم که ۳ یوزر مختلف با اسم هایشان مشخص شده اند. پوینتری از users را به تابع Create می دهیم تا عملیات batch insert را روی آنها اجرا کرده و id هر یوزر را خروجی دهد. سپس در بخش for که روی users می زنیم، id یوزر های مورد نظر به ما خروجی داده می شود.
<br>
اگر تعداد زیادی یوزر داشته باشیم، برای insert کردن آنها در دیتابیس می توانیم این عملیات را در دسته های n تایی انجام دهیم. تقسیم کردن تعداد زیادی یوزر به دسته های کوچک تر باعث می شود کارایی افزایش یابد و استفاده از حافظه کمتر شود. تکه کد زیر با تقسیم یوزر های به دسته های ۱۰۰ تایی و با استفاده از تابع CreateInBatches این روش را پیاده سازی کرده است:

<br>

```go
var users = []User{{Name: "jinzhu_1"}, ...., {Name: "jinzhu_10000"}}
db.CreateInBatches(users, 100)
```
<br>
در کد زیر، دیتا ها را به دسته های ۱۰۰۰ تایی تقسیم می کنیم. سپس یک آرایه ۵۰۰۰ تایی از user ها داریم که هرکدام یک اسم و تعدادی (آرایه ای) از Pets دارند. با صدا زدن تابع Create، یوزر ها در ۵ batch که هرکدام از عملیات ها دارای ۱۰۰۰ یوزر است، در دیتابیس insert می شوند. توجه داشته باشید که insert کردن Pet ها در ۱۵ batch انجام می شود:

<br>

```go
db, err := gorm.Open(sqlite.Open("gorm.db"), &gorm.Config{
  CreateBatchSize: 1000,
})

db := db.Session(&gorm.Session{CreateBatchSize: 1000})

users = [5000]User{{Name: "jinzhu", Pets: []Pet{pet1, pet2, pet3}}...}

db.Create(&users)
// INSERT INTO users xxx (5 batches)
// INSERT INTO pets xxx (15 batches)
```

<br></br>
<h3>Create Hooks</h3>
در GORM، hook یک مکانیزم است که به ما اجازه می دهد تا function هایی را تعریف کنیم که به صورت اوتوماتیک در نقاط خاصی از lifecycle یک آبجکت اجرا می شوند. Hook ها کمک می کنند تا یک logic هایی مانند creating، updating، deleting یا querying را اضافه کنیم. <br>حال در GORM این اجازه به ما داده می شود تا hook هایی که کاربر تعریف میکند، برای BeforeSave, BeforeCreate, AfterSave و AfterCreate پیاده سازی شوند. این متد hook زمانی که یک رکورد درست میکنیم فراخوانی می شود. کد زیر مثالی از این نمونه است:

<br>

```go
func (u *User) BeforeCreate(tx *gorm.DB) (err error) {
  u.UUID = uuid.New()

  if u.Role == "admin" {
    return errors.New("invalid role")
  }
  return
}
```
در کد بالا، BeforeCreate یک hook method است که برای انجام اکشن ها یا اعتبارسنجی قبل از درست کردن یه رکورد جدید از User در دیتابیس پیاده سازی شده است. همانطور که مشخص است یک UUID برای یوزر ست کرده است. سپس چک می کند که role درست است یا خیر. اگر role یوزر admin بود، ارور می دهد و از ساخت یک یوزر با نقش نادرست جلوگیری می کند.

<br>برای در نظر نگرفتن متد hook می توان به صورت زیر عمل کرد:

```go
DB.Session(&gorm.Session{SkipHooks: true}).Create(&user)

DB.Session(&gorm.Session{SkipHooks: true}).Create(&users)

DB.Session(&gorm.Session{SkipHooks: true}).CreateInBatches(users, 100)
```
<br></br>
<h3>Create From Map</h3>
در GORM برای ساختن یک رکورد جدید در دیتابیس به صورت struct می توانیم دیتا را به صورت map در نظر بگیریم (بااستفاده از <code>map[string]interface{}</code> و <code>[]map[string]interface{}{}</code>). کد زیر مثالی از این عملکرد است:

<br>

```go
db.Model(&User{}).Create(map[string]interface{}{
  "Name": "jinzhu", "Age": 18,
})

// batch insert from `[]map[string]interface{}{}`
db.Model(&User{}).Create([]map[string]interface{}{
  {"Name": "jinzhu_1", "Age": 18},
  {"Name": "jinzhu_2", "Age": 20},
})
```
نکته: هنگام استفاده از map برای درست کردن رکورد، hook ها فراخوانی نمی شوند، association ها ذخیره نمی شوند و primary key value ها دوباره پر (filled) نمی شوند.
<br></br>
<h3>Create From SQL Expression/Context Valuer</h3>
روش دیگری برای insert کردن دیتا در GORM با SQL expression, استفاده از <code>map[string]interface{}</code> و  Customized Data Type  ها است. کد زیر هردو روش را پیاده سازی کرده است:

<br>

```go
// Create from map
db.Model(User{}).Create(map[string]interface{}{
  "Name": "jinzhu",
  "Location": clause.Expr{SQL: "ST_PointFromText(?)", Vars: []interface{}{"POINT(100 100)"}},
})
// INSERT INTO `users` (`name`,`location`) VALUES ("jinzhu",ST_PointFromText("POINT(100 100)"));

// Create from customized data type
type Location struct {
  X, Y int
}

// Scan implements the sql.Scanner interface
func (loc *Location) Scan(v interface{}) error {
  // Scan a value into struct from database driver
}

func (loc Location) GormDataType() string {
  return "geometry"
}

func (loc Location) GormValue(ctx context.Context, db *gorm.DB) clause.Expr {
  return clause.Expr{
    SQL:  "ST_PointFromText(?)",
    Vars: []interface{}{fmt.Sprintf("POINT(%d %d)", loc.X, loc.Y)},
  }
}

type User struct {
  Name     string
  Location Location
}

db.Create(&User{
  Name:     "jinzhu",
  Location: Location{X: 100, Y: 100},
})
// INSERT INTO `users` (`name`,`location`) VALUES ("jinzhu",ST_PointFromText("POINT(100 100)"))
```
<br></br>
<h3>Create With Associations</h3>
در درست کردن داده ها با استفاده از association ها, اگر مقدار association آن صفر نباشد, آن association ها اضافه  و متدهای hook فراخوانی خواهند شد. کد زیر این روش را پیاده سازی کرده است:

<br>

```go
type CreditCard struct {
  gorm.Model
  Number   string
  UserID   uint
}

type User struct {
  gorm.Model
  Name       string
  CreditCard CreditCard
}

db.Create(&User{
  Name: "jinzhu",
  CreditCard: CreditCard{Number: "411111111111"}
})
// INSERT INTO `users` ...
// INSERT INTO `credit_cards` ...
```
اگر بخواهیم association ها ذخیره نشوند, باید از <code>Select</code> و <code>Omit</code> استفاده کنیم, مانند کد زیر:

<br>

```go
db.Omit("CreditCard").Create(&user)

// skip all associations
db.Omit(clause.Associations).Create(&user)
```
نکته: در ادامه association ها را توضیح خواهیم داد.
<br></br>
<h3>Default Values</h3>
ما می توانیم با تگ <code>default</code>, برای فیلدهایمان مقداری default تعیین کنیم. در این صورت این default value در زمان insert در دیتابیس برای zero-value fields استفاده خواهد شد:

<br>

```go
type User struct {
  ID   int64
  Name string `gorm:"default:galeone"`
  Age  int64  `gorm:"default:18"`
}
```
نکته: هیچ zero value ای به شکل 0, '', flase برای فیلدهایی که default value تعیین شده اند, در دیتابیس ذخیره نخواهد شد. برای جلوگیری از این مشکل, می توان از pointer یا Scanner/Valuer استفاده کرد, مانند کد زیر:

<br>

```go
type User struct {
  gorm.Model
  Name string
  Age  *int           `gorm:"default:18"`
  Active sql.NullBool `gorm:"default:true"`
}
```
باید تگ default را برای فیلدهایی که دارای مقدار default یا virtual/generated در دیتابیس هستند, تنظیم کنیم. اگر بخواهیم در هنگام migrating, مقدار default را درنظر نگیریم, باید از <code>default:(-)</code> استفاده کنیم, مانند کد زیر:

<br>

```go
type User struct {
  ID        string `gorm:"default:uuid_generate_v3()"` // db func
  FirstName string
  LastName  string
  Age       uint8
  FullName  string `gorm:"->;type:GENERATED ALWAYS AS (concat(firstname,' ',lastname));default:(-);"`
}
```
<br></br>
<h3>Upsert/ On Conflict</h3>
GORM پشتیبانی سازگار Upsert را برای دیتابیس های مختلف فراهم میکند. کد زیر نمونه ای از آن است:

<br>

```go
import "gorm.io/gorm/clause"

// Do nothing on conflict
db.Clauses(clause.OnConflict{DoNothing: true}).Create(&user)

// Update columns to default value on `id` conflict
db.Clauses(clause.OnConflict{
  Columns:   []clause.Column{{Name: "id"}},
  DoUpdates: clause.Assignments(map[string]interface{}{"role": "user"}),
}).Create(&users)
// MERGE INTO "users" USING *** WHEN NOT MATCHED THEN INSERT *** WHEN MATCHED THEN UPDATE SET ***; SQL Server
// INSERT INTO `users` *** ON DUPLICATE KEY UPDATE ***; MySQL

// Use SQL expression
db.Clauses(clause.OnConflict{
  Columns:   []clause.Column{{Name: "id"}},
  DoUpdates: clause.Assignments(map[string]interface{}{"count": gorm.Expr("GREATEST(count, VALUES(count))")}),
}).Create(&users)
// INSERT INTO `users` *** ON DUPLICATE KEY UPDATE `count`=GREATEST(count, VALUES(count));

// Update columns to new value on `id` conflict
db.Clauses(clause.OnConflict{
  Columns:   []clause.Column{{Name: "id"}},
  DoUpdates: clause.AssignmentColumns([]string{"name", "age"}),
}).Create(&users)
// MERGE INTO "users" USING *** WHEN NOT MATCHED THEN INSERT *** WHEN MATCHED THEN UPDATE SET "name"="excluded"."name"; SQL Server
// INSERT INTO "users" *** ON CONFLICT ("id") DO UPDATE SET "name"="excluded"."name", "age"="excluded"."age"; PostgreSQL
// INSERT INTO `users` *** ON DUPLICATE KEY UPDATE `name`=VALUES(name),`age`=VALUES(age); MySQL

// Update all columns to new value on conflict except primary keys and those columns having default values from sql func
db.Clauses(clause.OnConflict{
  UpdateAll: true,
}).Create(&users)
// INSERT INTO "users" *** ON CONFLICT ("id") DO UPDATE SET "name"="excluded"."name", "age"="excluded"."age", ...;
// INSERT INTO `users` *** ON DUPLICATE KEY UPDATE `name`=VALUES(name),`age`=VALUES(age), ...; MySQL
```
نکته: توضیحات بیشتر در بخش Advanced Query داده خواهند شد.

<br></br>
<h3><li>Query :</h3>
<br>
<h3>Retrieving a single object</h3>
GORM متدهای First, Take, Last را برای بازیابی یک شی از پایگاه داده ارائه می دهد، در هنگام پرس و جو از پایگاه داده شرط LIMIT 1 را اضافه می کنیم و اگر رکوردی یافت نشد، خطای ErrRecordNotFound برگردانده می شود. کد زیر این کار را انجام می دهد:

<br>

```go
// Get the first record ordered by primary key
db.First(&user)
// SELECT * FROM users ORDER BY id LIMIT 1;

// Get one record, no specified order
db.Take(&user)
// SELECT * FROM users LIMIT 1;

// Get last record, ordered by primary key desc
db.Last(&user)
// SELECT * FROM users ORDER BY id DESC LIMIT 1;

result := db.First(&user)
result.RowsAffected // returns count of records found
result.Error        // returns error or nil

// check error ErrRecordNotFound
errors.Is(result.Error, gorm.ErrRecordNotFound)
```
نکته: برای جلوگیری از ارور ErrRecordNotFound می توان از تابع Find استفاده کرد. این تابع دیتاهای از نوع struct  و  slice را می پذیرد. مثال: <code>db.Limit(1).Find(&user)</code>
<br>باید دقت کنیم که استفاده از تابع Find بدون محدودیت, در کل جدول پرس و جو (query) می کند و اولین شی را که موردنظر نیست برمی گرداند.
<br>تابع های First و Last اولین و آخرین رکورد (به ترتیب) را مطابق با کلید اصلی (primary key) پیدا می کنند. این تابع ها فقط زمانی کار می کنند که یک pointer به struct مقصد به عنوان آرگومان به تابع ها ارسال شود یا زمانی که مدل با استفاده از <code>db.Model()</code> مشخص شود. علاوه بر این، اگر کلید اولیه برای مدل مربوطه تعریف نشده باشد، مدل با فیلد اول مرتب می شود. کد زیر این روش را پیاده سازی کرده است:

<br>

```go
var user User
var users []User

// works because destination struct is passed in
db.First(&user)
// SELECT * FROM `users` ORDER BY `users`.`id` LIMIT 1

// works because model is specified using `db.Model()`
result := map[string]interface{}{}
db.Model(&User{}).First(&result)
// SELECT * FROM `users` ORDER BY `users`.`id` LIMIT 1

// doesn't work
result := map[string]interface{}{}
db.Table("users").First(&result)

// works with Take
result := map[string]interface{}{}
db.Table("users").Take(&result)

// no primary key defined, results will be ordered by first field (i.e., `Code`)
type Language struct {
  Code string
  Name string
}
db.First(&Language{})
// SELECT * FROM `languages` ORDER BY `languages`.`code` LIMIT 1
```
<br></br>
<h3>Retrieving objects with primary key</h3>
اگر کلید اصلی (primary key) یک عدد باشد, اشیا را می توان با استفاده از کلید اصلی, با استفاده از inline conditions بازیابی کرد. هنگام کار با string ها برای جلوگیری از SQL injection باید بیشتر حواسمان جمع باشد.<br>نکته: inline condition را در ادامه بیشتر توضیح می دهیم.
<br>کد زیر نمونه ای از این بازیابی است:

<br>

```go
db.First(&user, 10)
// SELECT * FROM users WHERE id = 10;

db.First(&user, "10")
// SELECT * FROM users WHERE id = 10;

db.Find(&users, []int{1,2,3})
// SELECT * FROM users WHERE id IN (1,2,3);
```
کلید اصلی در کد بالا, از جنس عدد است. اگر این کلید به صورت string باشد (مثلا uuid) باید به روش زیر عمل کنیم:

<br>

```go
db.First(&user, "id = ?", "1b74413f-f3b8-409f-ac47-e8c062e3472a")
// SELECT * FROM users WHERE id = "1b74413f-f3b8-409f-ac47-e8c062e3472a";
```
اگر شی مقصد primary key داشته باشد, این primary key برای ساختن condition استفاده خواهد شد:

<br>

```go
var user = User{ID: 10}
db.First(&user)
// SELECT * FROM users WHERE id = 10;

var result User
db.Model(User{ID: 10}).First(&result)
// SELECT * FROM users WHERE id = 10;
```
نکته: اگر از فیلدهای خاص GORM مانند <code>gorm.DeletedAt</code> استفاده کنیم, یک query دیگر برای بازیابی شی موردنظرمان اجرا خواهد شد, مانند کد زیر:

<br>

```go
type User struct {
  ID           string `gorm:"primarykey;size:16"`
  Name         string `gorm:"size:24"`
  DeletedAt    gorm.DeletedAt `gorm:"index"`
}

var user = User{ID: 15}
db.First(&user)
//  SELECT * FROM `users` WHERE `users`.`id` = '15' AND `users`.`deleted_at` IS NULL ORDER BY `users`.`id` LIMIT 1
```
<br></br>
<h3>Retrieving all objects</h3>
با استفاده از تابع Find می توانیم تمام رکوردهای مربوط به users را از دیتابیس گرفته و خروجی دهیم. در کد زیر تمام این اطلاعات بازیابی می شوند و همینطور درصورت وجود ارور, این ارور خروجی داده می شود:

<br>

```go
// Get all records
result := db.Find(&users)
// SELECT * FROM users;

result.RowsAffected // returns found records count, equals `len(users)`
result.Error        // returns error
```
<br></br>
<h3>Conditions</h3>
به طور کلی, condition ها به ما این امکان را می دهند تا با استفاده از فیلترها و معیارهای موردنظر, رکوردهای خاصی که مدنظرمان هستند را بازیابی کنیم. بنابراین condition ها مانند دستور WHERE در SQL عمل می کنند. condition ها انواع مختلفی دارند که در ادامه به توضیح هر یک می پردازیم.</br>
<br>1. String Conditions :
<br>در این نوع condition ما می توانیم شرط موردنظر برای بازیابی دیتا را به صورت رشته (string) مشخص کنیم. این روش مانند دستور WHERE در SQL عمل می کند. کد زیر نمونه هایی به همراه خروجی این دستور را به ما نشان می دهد:

<br>

```go
// Get first matched record
db.Where("name = ?", "jinzhu").First(&user)
// SELECT * FROM users WHERE name = 'jinzhu' ORDER BY id LIMIT 1;

// Get all matched records
db.Where("name <> ?", "jinzhu").Find(&users)
// SELECT * FROM users WHERE name <> 'jinzhu';

// IN
db.Where("name IN ?", []string{"jinzhu", "jinzhu 2"}).Find(&users)
// SELECT * FROM users WHERE name IN ('jinzhu','jinzhu 2');

// LIKE
db.Where("name LIKE ?", "%jin%").Find(&users)
// SELECT * FROM users WHERE name LIKE '%jin%';

// AND
db.Where("name = ? AND age >= ?", "jinzhu", "22").Find(&users)
// SELECT * FROM users WHERE name = 'jinzhu' AND age >= 22;

// Time
db.Where("updated_at > ?", lastWeek).Find(&users)
// SELECT * FROM users WHERE updated_at > '2000-01-01 00:00:00';

// BETWEEN
db.Where("created_at BETWEEN ? AND ?", lastWeek, today).Find(&users)
// SELECT * FROM users WHERE created_at BETWEEN '2000-01-01 00:00:00' AND '2000-01-08 00:00:00';
```
همانطور که مشاهده می کنید در کد بالا, انواع حالات مشخص کردن شرط با string و خروجی کدها مشخص شده اند. 
<br></br>
<br>2. Struct and Map Conditions :
<br>این نوع condition به ما اجازه می دهد تا شرط دیتای موردنظر را با استفاده از structured data یا map مشخص کنیم, مانند کد زیر:

<br>

```go
// Struct
db.Where(&User{Name: "jinzhu", Age: 20}).First(&user)
// SELECT * FROM users WHERE name = "jinzhu" AND age = 20 ORDER BY id LIMIT 1;

// Map
db.Where(map[string]interface{}{"name": "jinzhu", "age": 20}).Find(&users)
// SELECT * FROM users WHERE name = "jinzhu" AND age = 20;

// Slice of primary keys
db.Where([]int64{20, 21, 22}).Find(&users)
// SELECT * FROM users WHERE id IN (20, 21, 22);
```
نکته: در GORM زمانی که از struct استفاده می کنیم, فیلدهایمان باید non zero باشند تا عملیات جستجو انجام شود. برای رفع این مشکل, به جای struct باید از map استفاده کنیم. به طور مثال, صفر در کد زیر مشکلی ایجاد نمی کند:

<br>

```go
db.Where(map[string]interface{}{"Name": "jinzhu", "Age": 0}).Find(&users)
// SELECT * FROM users WHERE name = "jinzhu" AND age = 0;
```
اما اگر بخواهیم در این شرایط از struct استفاده کنیم و همچنان مشکلی نداشته باشیم, باید مانند کد زیر عمل کنیم:

<br>

```go
db.Where(&User{Name: "jinzhu"}, "name", "Age").Find(&users)
// SELECT * FROM users WHERE name = "jinzhu" AND age = 0;
```
</br>
<br>3. Inline Condition :
<br>در این نوع شرط ما می توانیم به صورت مستقیم در تابع هایی مانند First و Find شرط موردنظر را بنویسیم:

<br>

```go
db.Find(&users, "name <> ? AND age > ?", "jinzhu", 20)
// SELECT * FROM users WHERE name <> "jinzhu" AND age > 20;

// Struct
db.Find(&users, User{Age: 20})
// SELECT * FROM users WHERE age = 20;

// Map
db.Find(&users, map[string]interface{}{"age": 20})
// SELECT * FROM users WHERE age = 20;
```
</br>
<br>4. Not Conditions :
<br>در این نوع condition, ما می توانیم شروطی را مشخص کنیم که نمی خواهیم رکوردی که به ما خروجی داده می شود, دارای آنها باشد. مانند کد زیر:

<br>

```go
db.Not("name = ?", "jinzhu").First(&user)
// SELECT * FROM users WHERE NOT name = "jinzhu" ORDER BY id LIMIT 1;

// Struct
db.Not(User{Name: "jinzhu", Age: 18}).First(&user)
// SELECT * FROM users WHERE name <> "jinzhu" AND age <> 18 ORDER BY id LIMIT 1;

// Not In slice of primary keys
db.Not([]int64{1,2,3}).First(&user)
// SELECT * FROM users WHERE id NOT IN (1,2,3) ORDER BY id LIMIT 1;
```
</br>
<br>5. Or Conditions :
<br>در این نوع condition می توانیم دو حالت شرط را درنظر بگیریم. کد زیر مثالی از این روش با استفاده از map است:

<br>

```go
// Map
db.Where("name = 'jinzhu'").Or(map[string]interface{}{"name": "jinzhu 2", "age": 18}).Find(&users)
// SELECT * FROM users WHERE name = 'jinzhu' OR (name = 'jinzhu 2' AND age = 18);
```
<br></br>
<h3>Selecting Specific Fields</h3>
Select در GORM به ما این اجازه را می دهد تا field های موردنظرمان را که می خواهیم رکورد خروجی آنها را داشته باشد مشخص کنیم. کد زیر نمونه ساده ای از این روش است:

<br>

```go
db.Select("name", "age").Find(&users)
// SELECT name, age FROM users;
```
<br></br>
<h3>Order</h3>
ما می توانیم ترتیب رکوردهایی را که به ما داده می شوند خودمان مشخص کنیم. برای این کار, از تابع Order در GORM استفاده می کنیم. دو حالت از این روش در کد زیر با توضیحاتشان مشخص شده اند:

<br>

```go
// Multiple orders
db.Order("age desc").Order("name").Find(&users)
// SELECT * FROM users ORDER BY age desc, name;

db.Clauses(clause.OrderBy{
  Expression: clause.Expr{SQL: "FIELD(id,?)", Vars: []interface{}{[]int{1, 2, 3}}, WithoutParentheses: true},
}).Find(&User{})
// SELECT * FROM users ORDER BY FIELD(id,1,2,3)
```
<br></br>
<h3>Limit and Offset</h3>
Limit, بیشترین تعداد رکوردهایی را که می خواهیم مشخص می کند. مانند کد زیر:
<br>Offset تعداد رکوردهایی را که نمیخواهیم خروجی داده شوند (قبل از رکورد کردن) مشخص می کند. کد زیر ترکیبی از این دو حالت است:

<br>

```go
db.Limit(10).Offset(5).Find(&users)
// SELECT * FROM users OFFSET 5 LIMIT 10;
```
اگر بخواهیم Limit را کنسل کنیم, باید از <code>Limit(-1)</code> استفاده کنیم. مانند کد زیر:
<br>

```go
db.Limit(10).Find(&users1).Limit(-1).Find(&users2)
```
<br></br>
<h3>Group By and Having</h3>
با استفاده از Group By می توانیم مجموعه ای از دیتاها را دریافت کنیم و عملیات ها را روی زیرمجموعه ای از سطرها که اطلاعاتی مشترک دارند, انجام دهیم. به طور مثال کد زیر را درنظر بگیرید:

<br>

```go
db.Model(&User{}).Select("name, sum(age) as total").Where("name LIKE ?", "group%").Group("name").First(&result)
```
در این کد ابتدا با <code>db.Model(&User{})</code> مشخص می کنیم که قرار است عملیات موردنظر روی جدول User انجام شود. <code>Select("name, sum(age) as total")</code> در این تکه کد, ابتدا ستون name را انتخاب می کنیم, سپس اعداد ستون age را باهم جمع کرده و داخل متغیر total ذخیره می کنیم. <code>Where("name LIKE ?", "group%")</code> در این بخش براساس ستون name, اسم هایی را که شبیه به هم هستند و با group شروع می شوند را شناسایی می کنیم. با این تکه کد, <code>Group("name")</code>, رکوردها را براساس یکسان بودن اسم هایشان تقسیم بندی می کنیم. و در نهایت با استفاده از کد <code>First(&result)</code> اولین جواب جستجو را با توجه به شروط گفته شده, در result ذخیره می کنیم.<br>نکته: باید توجه داشت که این کد, age ها را برای دیتاهایی که اسم هایشان در شرایط <code>name LIKE "group%</code> صدق می کند با هم جمع می کند.
<br></br>Having نیز نوعی شرط را روی دیتاهای موردنظر مشخص می کند و این امکان را به ما می دهد تا گروه ها را بر اساس محاسبات کل فیلتر کنیم.<br>نکته: Having همواره بعد از Group By می آید.<br>کد زیر را درنظر بگیرید:

<br>

```go
rows, err := db.Table("orders").Select("date(created_at) as date, sum(amount) as total").Group("date(created_at)").Having("sum(amount) > ?", 100).Rows()
defer rows.Close()
for rows.Next() {
  ...
}
```
در کد بالا همانطور که مشاهد می کنید, ابتدا گروه هایی را با شرایط تعیین شده مشخص می کنیم, سپس با استفاده از Having,  آن گروه هایی که جمع ستون های amount آنها از  ۱۰۰ بیشتر است را انتخاب می کنیم.
<br></br>
<h3>Distinct</h3>
این تابع در GORM به ما اجازه می دهد تا رکوردهای منحصر به فرد را از جدول بازیابی کنیم و تکرارها را در نتیجه حذف کنیم. Distinct با Pluck و Count کار می کند (که در ادامه توضیح داده می شوند).<br>در کد زیر, دنبال دیتاهایی هستیم که ترکیب name و age آنها متفاوت است:

<br>

```go
db.Distinct("name", "age").Order("name, age desc").Find(&results)
```
<br></br>
<h3>Joins</h3>
Join این امکان را به ما می دهد تا دیتاها را از چندین جدول, با توجه به شروط موردنظر, ترکیب کنیم. به کد زیر توجه کنید:

<br>

```go
type result struct {
  Name  string
  Email string
}

db.Model(&User{}).Select("users.name, emails.email").Joins("left join emails on emails.user_id = users.id").Scan(&result{})
```
در کد بالا, پس از انتخاب ستون ها از جدول های موردنظر (name از جدول User و email از جدول emails), این دو جدول را بر اساس برابری ستون های user_id در جدول emails و id در جدول users ترکیب می کنیم.
<br>
از انواع join های دیگر می توان به Joins Preloading, Join with conditions و Joins a Derived Table اشاره کرد.
<br></br>
<h3>Scan</h3>
Scan نتایج در یک struct عمکردی مانند Find دارد. کد زیر نمونه ای از این روش است:

<br>

```go
type Result struct {
  Name string
  Age  int
}

var result Result
db.Table("users").Select("name", "age").Where("name = ?", "Antonio").Scan(&result)
```

<br></br>
<h3><li>Advanced Query :</h3>
<br>