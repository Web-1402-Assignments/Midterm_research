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
<h3>Hibernate :</h3>
Hibernate ORM (یا به سادگی Hibernate) یک ابزار ORM برای زبان برنامه نویسی جاوا است که یک framework برای نگاشت یک مدل دامنه شی گرا به یک پایگاه داده رابطه ای فراهم می کند.
<br>ویژگی اصلی Hibernate نگاشت از کلاس های جاوا به جداول پایگاه داده و نگاشت از انواع داده جاوا به انواع داده های SQL است. Hibernate همچنین امکانات پرس و جو و بازیابی داده را فراهم می کند. SQL call  ایجاد می‌کند و توسعه‌دهنده دیگر نیاز نیست مدیریت دستی و تبدیل the result set object را انجام دهد.</br>
<br>از مشکلات Hibernate میتوان به عدم تطابق امپدانس شی-رابطه ای با جایگزینی دسترسی های مستقیم و دائمی پایگاه داده با توابع مدیریت شی سطح بالا اشاره کرد.</br>
<br>تاریخچه و سیر تکامل:</br>
Hibernate در سال 2001 توسط Gavin King و همکارانش از Cirrus Technologies به عنوان جایگزینی برای استفاده از existing EJB2-style beans آغاز شد. هدف اولیه ارائه قابلیت‌های ماندگاری، بهتر از آنهایی که توسط EJB2 ارائه شده بود، بود( با ساده سازی پیچیدگی ها و تکمیل برخی ویژگی ها).
<br>در اوایل سال 2003، تیم توسعه Hibernate نسخه های Hibernate2 را آغاز کرد که پیشرفت های قابل توجهی را نسبت به نسخه اول ارائه کرد.</br>
<br> سال 2005، Hibernate نسخه 3.0 منتشر شد. ویژگی های کلیدی شامل معماری جدید Interceptor/Callback، فیلترهای تعریف شده توسط کاربر و حاشیه نویسی JDK 5.0 (Java metadata feature) بود.
از سال 2010، Hibernate 3 (نسخه 3.5.0 و بالاتر) یک پیاده سازی تایید شده از مشخصات Java Persistence API 2.0 از طریق یک پوشش برای ماژول Core بود که مطابقت با استاندارد JSR 317 را فراهم می کرد.<br> دسامبر 2011، Hibernate Core 4.0.0 Final منتشر شد. این نسخه شامل ویژگی‌های جدیدی مانند پشتیبانی چند اجاره‌ای (multi-tenancy support)، معرفی ServiceRegistry (تغییر عمده در نحوه ساخت و مدیریت سرویس‌های Hibernate)، باز کردن بهتر جلسه از SessionFactory، ادغام بهبود یافته از طریق org.hibernate.integrator.spi.Integrator و کشف خودکار، پشتیبانی بین المللی، کدهای پیام در ورود به سیستم، و تمایز بیشتر بین API، SPI یا کلاس های پیاده سازی بود.<br> دسامبر 2012، Hibernate ORM 4.1.9 Final منتشر شد.<br> مارس 2013، Hibernate ORM 4.2 Final منتشر شد.<br> دسامبر 2013، Hibernate ORM 4.3.0 Final منتشر شد(دارای Java Persistence API 2.1).<br> سپتامبر 2015، Hibernate ORM 5.0.2 Final منتشر شد که پشتیبانی bootstrapping، hibernate-java8، hibernate-spatial، Karaf را بهبود بخشید.<br> نوامبر 2018، Hibernate ORM 5.1.17 Final منتشر شد. این آخرین نسخه از سری 5.1 است.<br> اکتبر 2018، Hibernate ORM 5.3 Final منتشر شد که قابلیت legacy cache Java Persistence API 2.2 را داشت.<br> دسامبر 2018، Hibernate ORM 5.4.0 Final منتشر شد.<br> اکتبر 2022، Hibernate ORM 6.1.4 Final منتشر شد.</br>
<br></br>
<h3>ActiveRecord (Ruby on Rails) :</h3>
ActiveRecord یک framework ORM است که در چارچوب توسعه وب Ruby on Rails ایجاد شده است. این framework از اصل contract- over-configuration پیروی می کند و مجموعه ای غنی از روش ها را برای عملیات پایگاه داده ارائه می دهد. ActiveRecord به دلیل سادگی و بهره وری که به توسعه دهندگان Ruby on Rails ارائه می دهد محبوبیت پیدا کرد.
<br>الگوی ActiveRecord به این صورت است که یک جدول یا نمای پایگاه داده در یک کلاس پیچیده شده است. بنابراین، یک نمونه شی به یک ردیف در جدول گره خورده است. پس از ایجاد یک شی، یک ردیف جدید به جدول اضافه می شود. هر شیء بارگذاری شده اطلاعات خود را از پایگاه داده دریافت می کند. هنگامی که یک شی به روز می شود، ردیف مربوطه در جدول نیز به روز می شود. کلاس wrapper، متدها یا ویژگی های دسترسی را برای هر ستون در جدول یا view پیاده سازی می کند<br>Martin Fowler در سال ۲۰۰۳ در کتاب Patterns of Enterprise Application Architecture از آن نام برده است.<br>از مشکلات این نوع framework میتوان به موارد زیر اشاره کرد:</br>
<br>آزمایش پذیری (testability) :
به دلیل جفت شدن تعامل پایگاه داده و منطق برنامه هنگام استفاده از الگوی active record، unit test  یک شی active record  بدون پایگاه داده دشوار می شود.</br>
<br>اصل مسئولیت واحد و تفکیک نگرانی ها (The principle of single responsibility and separation of concerns) :
مشکل دیگر این الگو این است که، به دلیل جفت شدن قوی تعامل پایگاه داده و منطق برنامه، یک شی active record  از اصل مسئولیت واحد و جداسازی نگرانی ها پیروی نمی کند (برخلاف معماری چند لایه که به درستی به این شیوه ها رسیدگی می کند). به همین دلیل، الگوی active record بهتر است در برنامه‌های کاربردی ساده استفاده شود که همگی یا به صورت forms over data با عملکرد CRUD باشند یا فقط به عنوان بخشی از یک معماری هستند.</br>
<br>سیستم های توزیع شده (distributed systems) :
الگوهای مبتنی بر record در سیستم‌های توزیع‌شده ضعیف عمل می‌کنند، به‌خصوص در مواردی که همروندی (concurrency) غیرممکن است (مثلاً حالت offline). یعنی دو آپدیت هر دو ممکن است یک فیلد صحیح داشته باشند اما فقط یکی از دو رکورد می تواند برنده شود.</br>
<br></br>
<h3>Entity Framework :</h3>
Entity Framework یک چارچوب ORM است که توسط مایکروسافت برای اکوسیستم دات نت توسعه یافته است.  در ابتدا به عنوان بخشی جدایی ناپذیر از NET Framework. عرضه شد، اما با شروع نسخه 6.0 Entity Framework به طور جداگانه از NET Framework. تحویل داده شد. 
برخی از ویژگی هایی که ارائه می دهد عبارتند از: تولید خودکار طرحواره (automatic schema generation)، پرس و جو (querying)، ردیابی تغییر (change tracking)، و مدیریت تراکنش (transaction management)<br>Entity Framework در طول زمان تکامل یافته است و هر نسخه ویژگی ها و پیشرفت های جدیدی را ارائه می دهد.<br>Entity Framework 6.4 آخرین نسخه از framework کلاسیک بود. اگرچه Entity Framework 6 هنوز پشتیبانی می‌شود، اما دیگر در حال توسعه نیست و فقط مشکلات امنیتی اش رفع می شوند.<br>framework جدیدی به نام Entity Framework Core (EF Core) در سال 2016 با ویژگی های مشابه اما نه کامل معرفی شد. شماره گذاری نسخه این framework از 1.0 مجدداً شروع شد و آخرین نسخه آن EF Core 7.0 است.</br>
<br></br>
<h3>Django ORM :</h3>
Django ORM ORM یک built-in ORM برای framework وب جنگو در پایتون است و یک API سطح بالا برای عملیات پایگاه داده ارائه می دهد که به توسعه دهندگان این امکان را می دهد تا مدل ها را تعریف کرده و با استفاده از کد پایتون کوئری ها را انجام دهند. Django ORM به دلیل سهولت استفاده و ادغام دقیق با ویژگی های توسعه وب جنگو شناخته شده است. <br>جنگو در پاییز 2003 تولید شد، زمانی که برنامه نویسان وب در روزنامه Lawrence Journal-World، Adrian Holovaty و Simon Willison، شروع به استفاده از Python برای ساخت برنامه کردند. در جولای 2005 تحت مجوز BSD به صورت عمومی منتشر شد. این چارچوب به افتخار گیتاریست جانگو راینهارت نامگذاری شد.
در ژوئن 2008، اعلام شد که یک بنیاد نرم افزاری جنگو (DSF) که به تازگی تشکیل شده است، جنگو را در آینده حفظ خواهد کرد.
<br></br>
<h3>GORM (GO) :</h3>
GORM یک کتابخانه ORM برای زبان برنامه نویسی Go است که از ActiveRecord از Ruby on Rails الهام گرفته شده است. ویژگی هایی مانند ایجاد جدول خودکار (automatic table creation)، پرس و جو (queries)، انجمن ها (forums) و مدیریت تراکنش ها (transaction management) را ارائه می دهد. همچنین توسط یک API بصری و رسا عملیات پایگاه داده را ساده می کند و boilerplate code را کاهش می دهد.<br>تاریخچه GORM به سال 2013 برمی گردد و توسط توسعه دهنده ای به نام Jinzhu ساخته شد. هدف اصلی آن ساده سازی عملیات پایگاه داده در Go و ارائه سطح بالاتری از انتزاع (abstraction) برای کار با پایگاه داده بود.
<br>GORM از زمان آغاز به کار به دلیل سادگی، انعطاف‌پذیری، ویژگی‌های قدرتمند و پشتیبانی از انواع مختلف پایگاه داده از جمله MySQL، PostgreSQL، SQLite و غیره محبوبیت قابل توجهی در جامعه Go به دست آورد و
در طول سال‌ها، توسط توسعه دهندگان زیادی تکامل یافت و تبدیل به یک ORM پرکاربرد در اکوسیستم Go شد.
<br></br>
انواع دیگر ORM ها:
<li>Java Persistence API</li>
<li>Apache OpenJPA</li>
<li>EclipseLink </li>
<li>RedBeanPHP </li>
<li>JOOQ Object Oriented Querying </li>
<li>Dapper ORM </li>
<li>SQLObject </li>
<li>Doctrine </li>
<li>Propel </li>
<li>Ebean </li>
<li>TopLink </li>
<li>Hibernate search </li>
<br></br>

<h2>راه اندازی و آغاز به کار</h2>
<hr></hr>

<li>قبل از شروع به کاری کردن با GORM طبیعتا لازم است که دانشی متوسط از زبان go داشته باشید. همچنین باید با دانش دیتابیس آشنایی داشته باشید و درک درستی از محیط‌های ER و Relational Model ها داشته باشید.
</li>

<br>
<li>برای نصب و راه‌اندازی gorm کافی است که در کامندلاین یا ترمینال خود دستورات زیر را وارد کنید تا لایبرری های مورد نظر دانلود و نصب شوند.</li>

```go
go get -u gorm.io/gorm
go get -u gorm.io/driver/sqlite
```

<br></br>

<h2>تعریف Model ها</h2>
<hr></hr>

مدل ها در اصل struct هایی هستند که درون آنها می‌توان فیلدهایی با دیتاتایپ های نرمال زبان Go و پوینترهای آنها قرار داد. به عنوان یک مثال از struct هایی که استفاده آنها هنگام استفاده از GORM متداول است به نمونه کد زیر توجه کنید:
<br>

```go
type User struct {
  ID           uint
  Name         string
  Email        *string
  Age          uint8
  Birthday     *time.Time
  CreatedAt    time.Time
  UpdatedAt    time.Time
}
```
<h2>قرارادهای از پیش تعیین شده</h2>
<hr>

به طور کلی GORM هر struct را به یک table در relational model تبدیل می‌کند. به این نحو که همواره در صورت وجود فیلد ```ID``` آن را به عنوان کلید اصلی در جدول در نظر می‌گیرد و همچنین به عنوان اسم هر table، از اسم struct مربوطه استفاده کرده آما آنرا به فرمت ```snake_cases``` در می‌آورد. برای نام ستون‌های table هم که در اصل همان فیلد های struct ما هستنداز فرمت ```snake_case``` استفاده می‌کند.
همچنین gorm به طور خودکار در صورت وجود فیلد های ```CreatedAt``` و ```UpdatedAt``` در struct ما، خود این فیلد ها را مقدار دهی کرده و در table نیز ثبت می‌کند.
در صورتی که نمی‌خواهید table های دیتابیس شما طبق این قرار دادها ساخته و آپدیت شوند، توانایی این را دارید که تغییرشان دهید که در بخش‌های بعدی به آن اشاره می‌کنم.

<h2>gorm.Model</h2>
<hr>

یک struct از پیش ساخته شده تویط GORM به نام gorm.Model وجود دارد که دارای فیلدهای ```ID``` ```CreatedAt``` ```UpdatedAt``` ```DeletedAt``` است. این استراکت به صورت زیر است:

```go
type Model struct {
  ID        uint           `gorm:"primaryKey"`
  CreatedAt time.Time
  UpdatedAt time.Time
  DeletedAt gorm.DeletedAt `gorm:"index"`
}
```
می‌توان این struct را در داخل هر struvt دیگری که خودتان می‌سازید  قرار بدهید(embedded structs). برای این کار کافی است در داخل struct خود فیلدی به نام ```gorm.Model``` داشته باشید.
از این روش برای embed کردن struct های دیگر هم می‌توانید استفاده کنید که در بخش‌ بعدی به آن می‌پردازم.

<h2>Embedded Structs</h2>
<hr>

برای embed کردن struct های از پیش ساخته شده تو سط GORM و ناشناس می‌توان از روش زیر استفاده کرد:

```go
type User struct {
  gorm.Model
  Name string
}
```

که این تکه کد در اصل برابر با تکه کد پایین خواهد بود:

```go
type User struct {
  ID        uint           `gorm:"primaryKey"`
  CreatedAt time.Time
  UpdatedAt time.Time
  DeletedAt gorm.DeletedAt `gorm:"index"`
  Name string
}
```


<h3>نکته</h3>

همان‌طور که گفته شد به طور پیشفرض، در صورت وجود فیلدهای ```CreatedAt``` و ```UpdatedAt``` در یک استراکت GORM از این فیلد ها برای آپدیت کردن زمانی که هر استراکت ساخته شده و یا تغییر داده شده است استفاده می‌کند. اطلاعات زمانی به ثانیه ذخیره می‌شوند. در صورتی که می‌خواهید این اطلاعات به صورت میلی‌ثانیه ذخیره شوند کافی است که دیتا تایپ این فیلد ها را به ```int``` تغییر بدهید.
همچنین در صورتی که می‌خواهید فیلد هایی که خودتان تعیین کردید برای آپدیت خودکار زمان توسط GORM استفاده شوند باید از تگ ```autoUpdateTime``` استفاده کنید.

```go
type User struct {
  CreatedAt time.Time // Set to current time if it is zero on creating
  UpdatedAt int       // Set to current unix seconds on updating or if it is zero on creating
  Updated   int64 `gorm:"autoUpdateTime:nano"` // Use unix nano seconds as updating time
  Updated   int64 `gorm:"autoUpdateTime:milli"`// Use unix milli seconds as updating time
  Created   int64 `gorm:"autoCreateTime"`      // Use unix seconds as creating time
}
```


اگر می‌خواهید یکی از struct هایی که خودتان ساخته اید را در دیگری embed کنید، می‌توانید فیلدی از جنس آن استراکتی که می‌خواهید embed کنید در استراکت دیگری قرار دهید و سپس جلوی آن از تگ ```embedded``` استفاده کنید.
برای مثال به نمونه زیر که در آن استراکت Author را در استراکت Blog جا داده ایم نگاه کنید:

```go
type Author struct {
  Name  string
  Email string
}

type Blog struct {
  ID      int
  Author  Author `gorm:"embedded"`
  Upvotes int32
}
```
که این تکه کد دقیقا برابر با تکه کد پایین می‌شود:

```go
type Blog struct {
  ID    int64
  Name  string
  Email string
  Upvotes  int32
}
```

اما خب ممکن است شما بخواهید فیلدهای ```Name``` و ```Email``` که در داخل استراکت Author به خوبی منظور را به نام های خودشان می‌رسانند را  در داخل استراکت Blog جداگانه و به منظور دیگری به کار ببرید. مثلا ممکن است بخواهید فیلدی به اسم ```Name``` داشته باشید و در آن نام بلاگ خود را ذخیره کنید.
یک راهکار می‌تواند این باشد که در داخل استراکت parent که اینجا استراکت Author است، اسم این فیلدها را تغییر دهید اما این نام‌های مختصر به خوب یمنظور را در استراکت Author می‌رسانند و با این کار برای هر استراکت parent پیچیدگی بیشتری اعمال می‌کنیم و همچنین این نکته هم پابرجاست که ما از ابتدا نمی‌دانیم کدام استراکت ها را قرار است به عنوان parent استفاده کنیم. 
برای حل این مشکل کافی است تگی که در جلوی فیلد از جنس استراکت parent قرار می‌دهیم را کمی تغییر دهیم:

```go
type Blog struct {
  ID      int
  Author  Author `gorm:"embedded;embeddedPrefix:author_"`
  Upvotes int32
}
```

در این صورت، فیلدهای ما در اصل به شکل زیر تغییر پیدا خواهند کرد:

```go
type Blog struct {
  ID          int64
  AuthorName  string
  AuthorEmail string
  Upvotes     int32
}
```

<h2>GORM Tags</h2>
<hr>

در بخش‌های بالا مثال‌هایی از استفاده از تگ‌های GORM دیدید. به طور کلی تگ‌هایی که برای مشخص کردن اطلاعات درون هر table استفاده می‌شوند در جدول زیر آورده شده‌اند:

<img src="tags.png" alt="Tags in GORM" width="80%" height="100%">

<h2>Connecting To A Database</h2>
<hr>

GORM از پایگاه  داده‌های MySQL - PostgreSQL - SQLite - SQL Server - TiDB پشتیبانی می‌کند.
در زیر برای هر کدام از دیتابیس‌ها روش اتصال به آن از طریق GORM آورده شده است:

<h3 dir="ltr">MySQL</h3>

برای ساختن یک سرور دیتابیس جدید در MySQL باید اینگونه عمل کنید:
```go
import (
  "gorm.io/driver/mysql"
  "gorm.io/gorm"
)

func main() {
  dsn := "user:pass@tcp(127.0.0.1:3306)/dbname?charset=utf8mb4&parseTime=True&loc=Local"
  db, err := gorm.Open(mysql.Open(dsn), &gorm.Config{})
}
```

در MySQL در صورتی که بخواهید یک سری تنظیمات را خودتان تعیین کنید در هنگام ساختن یک سرور می‌توانید این گونه این تنظیمات را اعمال کنید:

```go
db, err := gorm.Open(mysql.New(mysql.Config{
  DSN: "gorm:gorm@tcp(127.0.0.1:3306)/gorm?charset=utf8&parseTime=True&loc=Local", // data source name
  DefaultStringSize: 256, // default size for string fields
  DisableDatetimePrecision: true, // disable datetime precision, which not supported before MySQL 5.6
  DontSupportRenameIndex: true, // drop & create when rename index, rename index not supported before MySQL 5.7, MariaDB
  DontSupportRenameColumn: true, // `change` when rename column, rename column not supported before MySQL 8, MariaDB
  SkipInitializeWithVersion: false, // auto configure based on currently MySQL version
}), &gorm.Config{})
```

که در آن سایز دیفالت برای فیلدهای String را می‌توانید تعیین کنید و محدودیت‌های دیگری را ست کنید.

اگر نخواهید یک سرور دیتابیس جدید بسازید و می‌خواهید به یک سرور از پیش ساخته شده با استفاده از GORM وصل شوید باید طبق کد زیر رفتار کرده و ابتدا از پکج ```database/sql``` برای وصل شدن به سرور MySQL با دستور ```sql.Open``` استفاده کنید و سپس با GORM به این سرور دیتابیس کانکت شوید.

```go
import (
  "database/sql"
  "gorm.io/driver/mysql"
  "gorm.io/gorm"
)

sqlDB, err := sql.Open("mysql", "mydb_dsn")
gormDB, err := gorm.Open(mysql.New(mysql.Config{
  Conn: sqlDB,
}), &gorm.Config{})
```

<h3 dir="ltr">PostgreSQL</h3>


برای ساختن یک سرور دیتابیس جدید در PostgreSQL باید اینگونه عمل کنید:

```go
import (
  "gorm.io/driver/postgres"
  "gorm.io/gorm"
)

dsn := "host=localhost user=gorm password=gorm dbname=gorm port=9920 sslmode=disable TimeZone=Asia/Shanghai"
db, err := gorm.Open(postgres.Open(dsn), &gorm.Config{})
```

در صورتی که بخواهید به یک سرور دیتابیس از قبل ساخته شده از طریق GORM دسترسی داشته باشید باید بار دیگر از دستور ```sql.Open``` استفاده کنید و سپس با استفاده از GORM این دستابیس را open کنید:

```go
import (
  "database/sql"
  "gorm.io/driver/postgres"
  "gorm.io/gorm"
)

sqlDB, err := sql.Open("pgx", "mydb_dsn")
gormDB, err := gorm.Open(postgres.New(postgres.Config{
  Conn: sqlDB,
}), &gorm.Config{})
```

<h3 dir="ltr">SQLite</h3>


برای دسترسی به یک سرور SQL از طریق GORM دسترسی داشته باشید باید به ننحو زیر عمل کنید:

```go
import (
  "gorm.io/driver/sqlite" 
  "gorm.io/gorm"
)

db, err := gorm.Open(sqlite.Open("gorm.db"), &gorm.Config{})
```

<h3>نکته</h3>

اگر می‌خواهید که دیتابیس به جای اینکه در حافظه اصلی ساخته شود در مموری ایجاد شود باید به جای اسم فایل + نشانی آن از عبارت ```file::memory:?cache=shared``` استفاده کنید.

<h3 dir="ltr">SQL Server</h3>


برای دسترسی به یک سرور دیتابیس SQL Server از طریق GORM باید طبق  نمونه کد زیر پیش بروید:

```go
import (
  "gorm.io/driver/sqlserver"
  "gorm.io/gorm"
)

dsn := "sqlserver://gorm:LoremIpsum86@localhost:9930?database=gorm"
db, err := gorm.Open(sqlserver.Open(dsn), &gorm.Config{})
```

<h2>Connection Pool</h2>
<hr>

GORM می‌تواند با استفاده از پکچ ```database/sql``` کانکشن ها را را کنترل کرده و محدودیت هایی روی ماکسیمم تعداد انواع دسترسی‌ها به دیتابیس بگذارد:

```go
sqlDB, err := db.DB()

// SetMaxIdleConns sets the maximum number of connections in the idle connection pool.
sqlDB.SetMaxIdleConns(10)

// SetMaxOpenConns sets the maximum number of open connections to the database.
sqlDB.SetMaxOpenConns(100)

// SetConnMaxLifetime sets the maximum amount of time a connection may be reused.
sqlDB.SetConnMaxLifetime(time.Hour)
```
<br></br>
<hr>
<h2 style="text-align:center">CRUD interface</h2>
<hr></hr>
GRUD interface به مجموعه ای از عملیات ها اشاره دارد که می توانند بر روی یک پایگاه داده با استفاده از کتابخانه GORM انجام شوند. CRUD مخفف Create، Read، Update و Delete است که عملیات های اساسی در کار با داده های پایدار هستند.
<br></br>
<h2><li>Create :</li></h2>
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
در GORM، hook یک مکانیزم است که به ما اجازه می دهد تا function هایی را تعریف کنیم که به صورت اتوماتیک در نقاط خاصی از lifecycle یک آبجکت اجرا می شوند. Hook ها کمک می کنند تا یک logic هایی مانند creating، updating، deleting یا querying را اضافه کنیم. <br>حال در GORM این اجازه به ما داده می شود تا hook هایی که کاربر تعریف میکند، برای BeforeSave, BeforeCreate, AfterSave و AfterCreate پیاده سازی شوند. این متد hook زمانی که یک رکورد درست میکنیم فراخوانی می شود. کد زیر مثالی از این نمونه است:

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
<h2><li>Query :</h2>
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
<h2><li>Advanced Query :</li></h2>
<br>
<h3>Smart Select Fields</h3>
smart select fields در GORM, یک قابلیت است که در آن, یک select به صورت اتوماتیک, با فیلدهای خاصی, تولید می شود. (هنگام جستجو در دیتابیس). این ویژگی این امکان را به ما می دهد تا فیلدهای خاص و موردنظرمان را از جدول بازیابی کنیم (به جای دریافت همه ستون ها). به طور مثال کد زیر را درنظر بگیرید:

<br>

```go
type User struct {
  ID     uint
  Name   string
  Age    int
  Gender string
}

type APIUser struct {
  ID   uint
  Name string
}

// Select `id`, `name` automatically when querying
db.Model(&User{}).Limit(10).Find(&APIUser{})
```
در کد بالا, دو struct User و  APIUser داریم که این دومین struct, فیلدهای موردنظر ما ینی name و id را مشخص میکند. سپس در خط آخر, با محدودیت ۱۰ خروجی, تمام فیدهای id و name را از User جستجو کرده و خروجی می دهد.
<br></br>
<h3>SubQuery</h3>
SubQuery در GORM, به یک جستجو داخل جستجویی دیگر گفته می شود. این ویژگی به ما اجازه می دهد که نتیجه یک جستجو را به عنوان ورودی یا شرط برای جستجویی دیگر درنظر بگیریم, درنتیجه قادر به جستجوهای پیچیده تری خواهیم بود. کد زیر نمونه ای از یک SubQuery است:

<br>

```go
db.Where("amount > (?)", db.Table("orders").Select("AVG(amount)")).Find(&orders)
// SELECT * FROM "orders" WHERE amount > (SELECT AVG(amount) FROM "orders");
```
در کد بالا, جستجوی اصلی بخش <code>db.Where("amount > (?)", subquery).Find(&orders)</code> است و subquery در این عبارت, بخش <code>db.Table("orders").Select("AVG(amount)")</code> است. جستجوی اصلی در این تکه کد, این است که رکوردهایی را از جدول orders به ما بدهد که amount آنها بیشتر از میانگین amount حساب شده در subquery باشد.
<br></br>
<h3>Pluck</h3>
در این روش, یک ستون از دیتابیس را جستجو می کنیم, سپس آن را در یک قطعه (slice), scan می کنیم. کد زیر نمونه ای از این روش است:

<br>

```go
var ages []int64
db.Model(&users).Pluck("age", &ages)
```
در کد بالا مقادیر ستون age را بازیابی کرده (از جدول users) و آنها را در قطعه (slice) ages ذخیره می کنیم.

<br>
اگر بخواهیم چندین ستون را جستجو کنیم, از select با scan استفاده  می کنیم (به جای Select و Pluck), مانند کد زیر:

<br>

```go
db.Select("name", "age").Scan(&users)
```
<br></br>
<h3>Scopes</h3>
Scope ها این امکان را به ما می دهند تا جستجوهای پرکاربرد را مشخص کنیم. Scope ها معمولا به صورت توابع فراخوانی می شوند. مثال:

<br>

```go
func AmountGreaterThan1000(db *gorm.DB) *gorm.DB {
  return db.Where("amount > ?", 1000)
}

func PaidWithCreditCard(db *gorm.DB) *gorm.DB {
  return db.Where("pay_mode_sign = ?", "C")
}
db.Scopes(AmountGreaterThan1000, PaidWithCreditCard).Find(&orders)
// Find all credit card orders and amount greater than 1000
```
در کد بالا تابع <code>AmountGreaterThan1000</code> یک تابع scope است که خروجی و ورودی آن از جنس <code>*gorm.DB</code> هستند. در بخش <code>db.Scopes(AmountGreaterThan1000, PaidWithCreditCard).Find(&orders)</code>, شروط موجود در دو scope (<code>AmountGreaterThan1000</code> و <code>PaidWithCreditCard</code>) را باهم ادغام می کنیم و رکوردهای موردنظر را به توجه به این شرایط خروجی می دهیم.
<br></br>
<h3>Count</h3>
Count در GORM, تعداد رکوردهایی را که در شرایط خاصی صدق می کنند را به ما می دهد. تابع Count این مقدار را بدون اینکه آن رکوردها را خروجی دهد به ما می دهد.
کد زیر مثالی از این روش است:

<br>

```go
var count int64
db.Model(&User{}).Where("age > ?", 18).Count(&count)
```

<br></br>
<h2><li>Update :</li></h2>
<br>
<h3>Save All Fields</h3>
اگر در SQL, به روزرسانی کنیم, save همه فیلدها را ذخیره خواهد کرد:

<br>

```go
db.First(&user)

user.Name = "jinzhu 2"
user.Age = 100
db.Save(&user)
// UPDATE users SET name='jinzhu 2', age=100, birthday='2016-01-01', updated_at = '2013-11-17 21:34:10' WHERE id=111;
```
<br></br>
<h3>Update single column</h3>
استفاده از update باید به همراه شرط (condition) باشد, در غیر این صورت ارور <code>ErrMissingWhereClause</code> می دهد. کد زیر مثالی از update با شرط است:

<br>

```go
db.Model(&User{}).Where("active = ?", true).Update("name", "hello")
// UPDATE users SET name='hello', updated_at='2013-11-17 21:34:10' WHERE active=true;
```
<br></br>
<h3>Update multiple columns</h3>
برای اینکه چندین ستون را update کنیم, باید از <code>struct</code> یا <code>map[string]interface{}</code> استفاده کنیم,مانند کد زیر:

<br>

```go
db.Model(&user).Updates(User{Name: "hello", Age: 18, Active: false})
// UPDATE users SET name='hello', age=18, updated_at = '2013-11-17 21:34:10' WHERE id = 111;

db.Model(&user).Updates(map[string]interface{}{"name": "hello", "age": 18, "active": false})
// UPDATE users SET name='hello', age=18, active=false, updated_at='2013-11-17 21:34:10' WHERE id=111;
```
نکته: اگر از <code>struct</code> استفاده می کنیم, باید توجه داشته باشیم که فقط فیلدهای non-zero آپدیت خواهند شد.
<br></br>
<h3>Batch Updates</h3>
اگر در Model, رکوردی که دارای primary key است را مشخص نکرده باشیم, GORM یک batch update انجام می دهد, مانند کد زیر:

<br>

```go
// Update with struct
db.Model(User{}).Where("role = ?", "admin").Updates(User{Name: "hello", Age: 18})
// UPDATE users SET name='hello', age=18 WHERE role = 'admin';

// Update with map
db.Table("users").Where("id IN ?", []int{10, 11}).Updates(map[string]interface{}{"name": "hello", "age": 18})
// UPDATE users SET name='hello', age=18 WHERE id IN (10, 11);
```

<br></br>
<h2><li>Delete :</li></h2>
<br>
<h3>Delete a Record</h3>
در هنگام حذف کردن یک رکورد, مقداری که می خواهیم حذف شود باید primary key داشته باشد در غیر این صورت, یک batch delete صورت می گیرد که در ادامه توضیح می دهیم. کد زیر یک نمونه delete است:

<br>

```go
// Delete with additional conditions
db.Where("name = ?", "jinzhu").Delete(&email)
// DELETE from emails where id = 10 AND name = "jinzhu";
```
<br></br>
<h3>Batch Delete</h3>
همانطور که گفته شد, اگر مقدار مشخص شده برای حذف, primary key نداشته باشد, GORM تمام رکوردهایی که با شرایط صدق می کنند را حذف خواهد کرد, مانند کد زیر:

<br>

```go
db.Delete(&Email{}, "email LIKE ?", "%jinzhu%")
// DELETE from emails where email LIKE "%jinzhu%";
```
<br></br>
<h3>Soft Delete</h3>
اگر مدل ما دارای فیلد <code>gorm.DeletedAt</code> باشد, به طور اتوماتیک قابلیت soft delete را خواهد داشت.<br> زمانی که ما Delete را فراخوانی می کنیم, رکورد موردنظر از دیتابیس حذف نمی شود, بلکه GORM مقدار DeletedAt را روی زمان فعلی تنظیم می کند و در این صورت, دیتای ما, دیگر با روش های عادی Query قابل یافتن نخواهد بود:

<br>

```go
// user's ID is `111`
db.Delete(&user)
// UPDATE users SET deleted_at="2013-10-29 10:23" WHERE id = 111;
// Soft deleted records will be ignored when querying
db.Where("age = 20").Find(&user)
// SELECT * FROM users WHERE age = 20 AND deleted_at IS NULL;
```

<br></br>
<h2><li>Raw SQL and SQL Builder :</li></h2>
<br>
<h3>Raw SQL</h3>
Raw SQL در GORM به ما این امکان را می دهد تا دستورات را به صورت دستورات SQL وارد کنیم. مانند کد زیر:

<br>

```go
type Result struct {
  ID   int
  Name string
  Age  int
}

var result Result
db.Raw("SELECT id, name, age FROM users WHERE id = ?", 3).Scan(&result)
```
همانطور که در کد بالا می بینیم, دستور SQL که <code>SELECT id, name, age FROM users WHERE id = ?</code> است را به صورت string به تابع Raw می دهیم و خروجی دقیقا همان خروجی SQL این کد خواهد بود که در نهایت Scan شده است.
<br></br>
<h3>Row and Rows</h3>
اگر بخواهیم خروجی کدمان از جنس <code>*sql.Row</code> باشد, می توانیم مانند یکی از دو حالت زیر عمل کنیم:

<br>

```go
// Use GORM API build SQL
row := db.Table("users").Where("name = ?", "jinzhu").Select("name", "age").Row()
row.Scan(&name, &age)

// Use Raw SQL
row := db.Raw("select name, age, email from users where name = ?", "jinzhu").Row()
row.Scan(&name, &age, &email)
```
<br></br>
<h3>Scan <code>*sql.Rows</code> into struct</h3>
می توانیم خروجی ای را که جنس آن از <code>*sql.Row</code> است, در یک struct اسکن (Scan) کنیم. برای این منظور, باید از تابع <code>ScanRows</code> استفاده کنیم که ورودی های آن, پوینتری از یوزر و rows هست. کد زیر نمونه ای از این عملکرد است:

<br>

```go
rows, err := db.Model(&User{}).Where("name = ?", "jinzhu").Select("name, age, email").Rows() // (*sql.Rows, error)
defer rows.Close()

var user User
for rows.Next() {
  // ScanRows scan a row into user
  db.ScanRows(rows, &user)

  // do something
}
```
<br></br>
<hr>
<h2 style="text-align:center" >Associations</h2>
<hr>

در این بخش به سراغ ارتباطات میان موجودیت ها و طریقه نشان دادن آن‌ها با استفاده از GORM می‌رویم. چند نوع ارتباط را در زیر با هم برری می‌کنیم و برای هر کدام طریقه به کاربردنشان را در تکه‌ای کد نمایان می‌کنیم.

<h2>Belongs To</h2>
<hr>

ارتباط ```belongs to``` یک ارتباط یک به یک میان دو مدل(موجودیت) است که مشخص می‌کند هر نمونه از یک مدل به مدل دیگری "تعلق دارد". این ارتباط با استفاده از کلید خارجی(foreign key) انجام می‌شود. به طور خودکار، در صورتی وجود فیلدی به نام اسم مدلی که قرار است این مدل به آن تعلق داشته باشد + نام کلید اصلی آن مدل(این دو نام به هم دیگه میچسبند) GORM این فیلد را کلید خارجی در نظر می‌گیرد.
برای مثال، شرکتی را فرض کنید که تعدادی کارمند دارد، برای هر کدام از این کارمندها میخواهیم ارتباط ```belongs to``` را اعمال کنیم. در این صورت به شیوه کد زیر عمل می‌کنیم:

```go
type User struct {
  gorm.Model
  Name      string
  CompanyID int
  Company   Company
}

type Company struct {
  ID   int
  Name string
}
```

در این مثال هر User متعلق به Company است و ```CompanyID``` به طور پیشفرض کلید خارجی مدل User است. توجه کنید که همواره هنگام اعمال رابطه ```belongs to``` نیاز به embed کردن مدل parent در مدل دیگر است برای همین نیز فیلدی از جنس Company در داخل مدل User قرار داده‌ایم.

<br></br>
1- حال در صورتی که بخواهیم نام کلید خارجی را خودمان تعیین کنیم باید از تگ ```foreignKey``` در جلوی فیلد company استفاده کنیم. به شکل زیر:

```go
type User struct {
  gorm.Model
  Name         string
  CompanyRefer int
  Company      Company `gorm:"foreignKey:CompanyRefer"`
}

type Company struct {
  ID   int
  Name string
}
```

در این صورت در اصل فیلد CompanyRefer خواهد بود که کلید خارجی ما خواهد بود.
<br></br>

2- اگر بخواهیم کلید خارجی داخل مدلمان لزوما به کلید اصلی مدل parent اشاره نکند و یک فیلد دیگر از parent به عنوان کلید خارجی برای مدلمان انتخاب شود نیز GORM برای این کار راهکاری قرار داده است. کافی است از تگ ```refrences``` جلوی فیلد از جنس مدل parent در مدلمان استفاده کنیم. به عنوان مثال، این تغییر در مدل User و Company ما بدین شکل انجام می‌شود:

```go
type User struct {
  gorm.Model
  Name      string
  CompanyID string
  Company   Company `gorm:"references:Code"` 
}

type Company struct {
  ID   int
  Code string
  Name string
}
```

در این مثال به مدل Company خود یک فیلد دیگر به نام Code اضافه کرده و در مدل User تعیین می‌کنیم که کلید خارجی مان به جای فیلد ID که کلید اصلی مدل Company ما است به این فیلد refrence بدهد.

<h3>محدودیت‌های کلید خارجی</h3>

در صورتی که بخواهیم محدودیت‌های متداول کلید خارجی در relational model را اعمال کنیم، GORM به ما این اجازه را می‌دهد که با استفاده از تگ‌هایی در جلوی فیلد از جنس parent، این محدودیت‌ها از قبیل محدودیت‌های ```OnDelete```  و ```OnUpdate``` را اعمال کنیم:

```go
type User struct {
  gorm.Model
  Name      string
  CompanyID int
  Company   Company `gorm:"constraint:OnUpdate:CASCADE,OnDelete:SET NULL;"`
}

type Company struct {
  ID   int
  Name string
}
```

مشاهده می‌کنید که در مثال بالا تعیین کردیم هر گاه مدل Company آپدیت شد، کلید خارجی نیز برای تمام User ها آپدیت شود و هر گاه مدل Company حذف شد، فیلد تمام User های متعلق به آن شرکت NULL شوند.


<h2>Has One</h2>
<hr>

ارتباط ```has one``` یک ارتباط یک به یک میان دو مدل است که مشخص میکند یک نمونه از مدل دقیقا یک نمونه از یک مدل دیگر را "دارد". این ارتباط در واقع همان ارتباط ```belongs to``` است و در relational model نیز تفاوتی میان این دو وجود ندارد. تنها تفاوتی که این دو ارتباط دارند این است که این بار یک فیلد از جنس مدل دوم در مدل parent خواهیم داشت. این تفاوت باعث تفاوت در query زدن می‌شود.
هر گاه می‌خواهیم به ازای model1 نمونه ای از model2 که آن را دارا است را به دست آوریم بهتر است از ارتباط has one استفاده کنیم. چون در این صورت فیلدی از جنس model2 در model1 خواهیم داشت و query ما در O(1) انجام می‌شود. درصورتی که اگر از ارتباط ```belongs to``` استفاده کرده بودیم، باید تمام نمونه‌های model2 را بررسی کرده و ببینیم مالک هر کدام کدام است و در نهایت اگر مالک model1 بود آنگاه نمونه مورد نظر از model2 خود را پیدا کرده ایم اما این بار این query در O(n) انجام شده است.
پس در این صورت با استفاده از این نوع ارتباط، در تعداد مجاسبات در هر query صرف جویی کرده ایم. اما در عوض از آنجایی که در ابتدا مکن است هر نفر یک نمونه از model2 نداشته باشد و بعدا به آن اضافه شود، باید در آینده یک عمل insert انجام دهیم که هزینه خودش را دارد.
پس با توجه به relational model و استفاده‌هایمان از هر مدل و این که بیشتر عمل query زدن را انجام می‌دهیم یا عمل درج کردن را و در نهایت چگونه می‌خواهیم هزینه محاسبات بدهیم باید از بین ارتباط ```belongs to```  و ```has one``` یکی را انتخاب کنیم.

در زیر نمونه ای از ارتباط ```has one``` که مشخص می‌کند هر کارمند یک کارت بانکی دارد را مشاهده می‌کنید:

```go
// User has one CreditCard, UserID is the foreign key
type User struct {
  gorm.Model
  CreditCard CreditCard
}

type CreditCard struct {
  gorm.Model
  Number string
  UserID uint
}
```

>توجه کنید که ایین بار یک فیلد از جنس CreditCard است که در مدل User قرار گرفته است

در اینجا مانند ارتباط قبلی، یک فیلد از جنس کلید اصلی مدل parent به همراه نام گذاری‌ای که به آن پرداخته شد به عنوان کلید خارجی انتخاب شده است. 

1- می‌توان فیلدی که به عنوان کلید خارجی از آن یاد می‌شود را تغییر داد. اینکار را با استفاده از تگ ```foreignKey``` انجام می‌دهیم:

```go
type User struct {
  gorm.Model
  CreditCard CreditCard `gorm:"foreignKey:UserName"`
}

type CreditCard struct {
  gorm.Model
  Number   string
  UserRefer uint
}
```

در این جا کلید خارجی ما در اصل UserRefer که به فیلد ID از User اشاره می‌کند است.

2- حال اگر بخواهیم فیلدی که در مدل User به آن رفرنس داده می‌شود را نیز تغییر دهیم این کار را به سادگی با استفاده از تگ ```refrences``` انجام می‌دهیم. همچنین چون ارتباط یک به یک است می‌توانیم در جلوی فیلد مود نظر از تگ ```index``` استفاده کنیم که query زدن را در آینده برای ما راحت تر می‌کند:

```go
type User struct {
  gorm.Model
  Code       string     `gorm:"index"`
  CreditCard CreditCard `gorm:"foreignKey:UserCode;references:Code"`
}

type CreditCard struct {
  gorm.Model
  Number   string
  UserCode string
}
```

در اینجا فیلد جدید Code را ایجاد کرده و کلید به عنوان کلید خارجی برای مدل CreditCard به کار می‌بریم.

<h3>محدودیت‌های کلید خارجی</h3>

در صورتی که بخواهیم محدودیت‌های متداول کلید خارجی در relational model را اعمال کنیم، GORM به ما این اجازه را می‌دهد که با استفاده از تگ‌هایی در جلوی فیلد از جنس parent، این محدودیت‌ها از قبیل محدودیت‌های ```OnDelete```  و ```OnUpdate``` را اعمال کنیم:

```go
type User struct {
  gorm.Model
  CreditCard CreditCard `gorm:"constraint:OnUpdate:CASCADE,OnDelete:SET NULL;"`
}

type CreditCard struct {
  gorm.Model
  Number string
  UserID uint
}
```

مشاهده می‌کنید که در مثال بالا تعیین کردیم هر گاه مدل User آپدیت شد، کلید خارجی نیز برای تمام CreditCard ها آپدیت شود و هر گاه مدل User حذف شد، فیلد تمام CreditCard های متعلق به آن شرکت NULL شوند.


<h2>Has Many</h2>
<hr>

ارتباط ```has many``` یک ارتباط  1 به n میان دو موجودیت است که مشخص می‌کند هر نمونه از یک مدل می‌تواند با n نمونه از مدل دیگر ارتباط داشته باشد. در این ارتباط، مالک می‌توان 0 یا بیشتر ارتباط با نمونه‌های مدل دیگر داشته باشد. تفاوت اصلی این ارتباط با ارتباط ```has one``` دقیقا همین تفاوت در تعداد است که در کد این تفاوت به صورت تغییر جنس فیلد به آرایه‌ای از آن جنس نمایان می‌شود. مثال قبلی میان کارمند و کارت بانکی را به یاد بیارید. حال اینجا تفاوت این است که هر کارمند می‌تواند چند کارت بانکی داشته باشد:

```go
type User struct {
  gorm.Model
  CreditCards []CreditCard
}

type CreditCard struct {
  gorm.Model
  Number string
  UserID uint
}
```
1- در اینجا نیز می‌توان نام فیلدی که در مدل CreditCard به عنوان کلید خارجی وجود دارد را با تگ ```foreignKey``` تغییر داد:

```go
type User struct {
  gorm.Model
  CreditCards []CreditCard `gorm:"foreignKey:UserRefer"`
}

type CreditCard struct {
  gorm.Model
  Number    string
  UserRefer uint
}
```

مشاهده می‌کنید که این بار فیدل UserRefer در مدل CreditCard است که دز نقش کلید خارجی قرار دارد و به کلید اصلی مدل User یعنی ID رفرنس می‌دهد. این تغییر را با استفاده از تگ ```foreignKey``` در مقابل فیلد از جنس CreditCard در مدل مالک مشخص کرده‌ایم.

2- اگر بخواهیم فیلدی که کلید خارجی به آن رفرنس می‌دهد کلید اصلی مالک نباشد و یک فیلد دیگر از مالک باشه نیز این کار را با استفاده از تگ ```refrences``` انجام می‌دهیم:


```go
type User struct {
  gorm.Model
  MemberNumber string
  CreditCards  []CreditCard `gorm:"foreignKey:UserNumber;references:MemberNumber"`
}

type CreditCard struct {
  gorm.Model
  Number     string
  UserNumber string
}
```

مشاهده می‌کنید که این بار کلید خارجی در مدل CreditCard که فیلد UserNumber است به فیلد جدید ایجاد شده در مدل User به نام MemberNumber ارجاع می‌دهد.

<h3>محدودیت‌های کلید خارجی</h3>

در صورتی که بخواهیم محدودیت‌های متداول کلید خارجی در relational model را اعمال کنیم، GORM به ما این اجازه را می‌دهد که با استفاده از تگ‌هایی در جلوی فیلد از جنس parent، این محدودیت‌ها از قبیل محدودیت‌های ```OnDelete```  و ```OnUpdate``` را اعمال کنیم:

```go
type User struct {
  gorm.Model
  CreditCards []CreditCard `gorm:"constraint:OnUpdate:CASCADE,OnDelete:SET NULL;"`
}

type CreditCard struct {
  gorm.Model
  Number string
  UserID uint
}
```

مشاهده می‌کنید که در مثال بالا تعیین کردیم هر گاه مدل User آپدیت شد، کلید خارجی نیز برای تمام CreditCard ها آپدیت شود و هر گاه مدل User حذف شد، فیلد تمام CreditCard های متعلق به آن شرکت NULL شوند.

<h2>Many To Many</h2>
<hr>

ارتباط ```many to many``` یک ارتباط چند به چند یا n به  m است که مشخص می‌کند هر نمونه از یک مدل می‌تواند با m نمونه از مدل دیگر ارتباط داشته باشد و بالعکس. برای مثال فرض کنید در شرکت شما کارمندان هر کدام به چند زبان می‌توانند صحبت کنند. از طرفی هر زبان هم خود می‌تواند توسط چندین کارمند صحبت شود و این یک نمونه از ارتباط ```many to many``` خواهد بود که نمونه‌ای از آن در زیر آمده است:

```go
type User struct {
  gorm.Model
  Languages []Language `gorm:"many2many:user_languages;"`
}

type Language struct {
  gorm.Model
  Name string
}
```

در این نوع ارتباط‌ها، ویژگی‌های رابطه را نمی‌توان در table یکی یا هردو از مدل‌ها گنجاند و در نتیجه GORM از یک جدول با اسم join table برای نگهداری اطلاعات این ارتباط استفاده می‌کند. نام این table را باید با استفاده از تگ ```many2many``` در هر کدام از مدل‌ها تعیین کنیم:

```go
type User struct {
  gorm.Model
  Languages []*Language `gorm:"many2many:user_languages;"`
}

type Language struct {
  gorm.Model
  Name string
  Users []*User `gorm:"many2many:user_languages;"`
}
```

در join table ایجاد شده توسط GORM برای این دومدل، دو کلید خارجی هر کدام برای یکی از مدل‌ها خواهیم داشت و هر کدام از این کلیدها به کلید اصلی مدل مربوط به خود ارجاع می‌دهند. از آنجایی که join table را خود GORM می‌سازد ما آن را در کد نمی‌بینیم اما کلیت وضعیت کلیدهای خارجی برای مثال بالا چنین است:

```go
// Join Table: user_languages
//   foreign key: user_id, reference: users.id
//   foreign key: language_id, reference: languages.id
```

البته که می‌توان نام فیلدهای کلید خارجی و فیلدهایی که به آنها ارجاع می‌دهند را تغییر داد و اینکار را با استفااده از یک سری تگ‌های ```foreignKey``` ```refrences``` ```joinForeignKey``` ```joinRefrences``` انجام می‌دهیم:

```go
type User struct {
  gorm.Model
  Profiles []Profile `gorm:"many2many:user_languages;foreignKey:Refer;joinForeignKey:UserReferID;References:UserRefer;joinReferences:LanguageRefer"`
  Refer    uint      `gorm:"index:,unique"`
}

type Language struct {
  gorm.Model
  Name      string
  UserRefer uint `gorm:"index:,unique"`
}
```
در اینجا فیلد کلید خارجی مربوط به مدل User نام user_refer_id را خواهد داشت(به یاد بیاورید که GORM برای ثبت در SQL نام‌ها را به شکل snake_case در می‌آورد) و به فیلد Refer ارجاع می‌دهد.
همچنین فیلد کلید خارجی مربوط به مدل Language نام language_refer را خواهد داشت و به فیلد UserRefer ارجاع می‌دهد

درنهایت کلیدهای خارجی در join table چنین وضعیتی خواهند داشت:

```go
// Which creates join table: user_languages
//   foreign key: user_refer_id, reference: users.refer
//   foreign key: language_refer, reference: languages.user_refer
```

<h3>Customize JoinTable</h2>

می‌توان join table را تغییر داد و مثلا فیدهایی به آن اضافه کرد و محدودیت‌هایی برای آن فیلدها گذاشت(مانند هر table دیگر). مثلا می‌توان به جدول UserLanguage در فیلدهای زیر را اضافه کرد:

```go
type UserLanguage struct {
  UserID  int `gorm:"primaryKey"`
  LanguageID int `gorm:"primaryKey"`
  CreatedAt time.Time
  DeletedAt gorm.DeletedAt
}
```
<h3>محدودیت‌های کلید خارجی</h3>

>در این نوع ارتباط، محدودیت‌های کلید خارجی را در هنگام migrate کردن(در ادامه در مورد آن توضیح می‌دهم) انجام می‌دهیم.

<br></br>
<hr>
<h2 style="text-align:center">GORM Tutorial</h2>
<hr></hr>
<h2>Context :</h2>
Context در GORM, برای مدیریت lifecycle یک درخواست یا عملیات استفاده می شود. به عبارتی دیگر, context می تواند عملیات هایی را که شامل جستجو یا transaction در دیتابیس هستند مدیریت کند. همچنین به ما کمک می کند تا timeout ها, cancellation ها و  request-scoped value ها را مدیریت کنیم.<br>تابع مربوط به context, <code>WithContex</code> است.
<br></br>
<h3>Single Session Mode</h3>
این حالت معمولا زمانی استفاده می شود که  بخواهیم فقط ۱ عملیات انجام دهیم.<br>مثال:

<br>

```go
db.WithContext(ctx).Find(&users)
```
<br></br>
<h3>Continuous session mode</h3>
این حالت معمولا زمانی استفاده می شود که بخواهیم گروهی از عملیات ها را انجام دهیم.<br>مثال:

<br>

```go
tx := db.WithContext(ctx)
tx.First(&user, 1)
tx.Model(&user).Update("role", "admin")
```
در کد بالا, با استفاده از یک context به اسم <code>ctx</code>, یک transaction ساخته ایم و آن را در tx ذخیره کرده ایم. سپس بخش های <code>tx.First(&user, 1)</code> و <code>tx.Model(&user).Update("role", "admin")</code>, عملیات دیتابیس را داخل transaction انجام می دهند.
<br></br>
<h3>Context timeout</h3>
Context timeout در GORM به ما این امکان را می دهد تا حداکثر زمان مجاز انجام یک عملیات دیتابیس را مشخص کنیم. همچنین کمک می کند تا از اجرای طولانی یا هنگ کردن یک جستجو جلوگیری کنیم. کد زیر مثالی از این روش است:

<br>

```go
ctx, cancel := context.WithTimeout(context.Background(), 2*time.Second)
defer cancel()

db.WithContext(ctx).Find(&users)
```
به طور مثال در کد بالا, زمان timeout روی ۲ ثانیه تنظیم شده است.
<br></br>
<h2>Error Handling :</h2>
مدیریت خطاها در GO بسیار مهم است. همچنین باید توجه داشته باشیم که مدیریت خطاها در GORM, به علت زنجیره ای بودن API, با مدیریت خطاها در GO متفاوت است. انواع حالات مدیریت خطا در GORM را توضیح خواهیم داد.
<br>اگر خطایی رخ دهد, GORM قسمت <code>*gorm.DB</code> خطا را تنظیم می کند. این بخش را باید به صورت زیر بررسی کرد:

<br>

```go
if err := db.Where("name = ?", "jinzhu").First(&user).Error; err != nil {
  // error handling...
}
```
<br>یا

</br>

```go
if result := db.Where("name = ?", "jinzhu").First(&user); result.Error != nil {
  // error handling...
}
```
<br></br>
<h3>ErrRecordNotFound</h3>
اگر GORM نتواند در حین عملیات های Find, Last و Take, دیتای موردنظر را پیدا کند, <code>ErrRecordNotFound</code> را خروجی می دهد.<br>اگر هم چندین خطا در برنامه داشته باشیم, می توانیم با استفاده از <code>errors.Is</code> خطای <code>ErrRecordNotFound</code> را بررسی کنیم. به این منظور, به صورت زیر عمل می کنیم:

<br>

```go
err := db.First(&user, 100).Error
errors.Is(err, gorm.ErrRecordNotFound)
```
<br></br>
<h3>Dialect Translated Errors</h3>
اگر بخواهیم دقیقا خطای به وجود آمده برایمان نوشته شود (مثلا ErrDuplicatedKey), می توانیم <code>TranlateError</code> flag را در ابتدای باز کردن ارتباط db فعال کنیم:

<br>

```go
db, err := gorm.Open(postgres.Open(postgresDSN), &gorm.Config{TranslateError: true})
```
<br></br>
<h2>Method Chaining :</h2>
GORM اجازه استفاده از توابع به صورت زنجیره ای را به ما می دهد. مانند:

```go
db.Where("name = ?", "jinzhu").Where("age = ?", 18).First(&user)
```
در GORM, ۳ نوع تابع داریم:
<br>1. Chain Method
<br>2. Finisher Method
<br>3. New Session Method
<br></br>
<h3>Chain Method</h3>
Chain Method ها برای اصلاح یا اضافه کردن Cluases به Statement فعلی هستند, مانند:
<br><code>Where</code>, <code>Select</code>, <code>Omit</code>, <code>Joins</code>, <code>Scopes</code>, <code>Preload</code>, <code>Raw</code>...
<br></br>
<h3>Finisher Method</h3>
Finisher method ها, تابع های فوری هستند که callback های ثبت شده را اجرا می کنند (تولید و اجرای SQL), مانند:
<br><code>Create</code>, <code>First</code>, <code>Find</code>, <code>Take</code>, <code>Save</code>, <code>Update</code>, <code>Delete</code>, <code>Scan</code>, <code>Row</code>, <code>Rows</code> ...
<h3>New Session Method</h3>
تابع های <code>Session</code>, <code>WithContext</code> و <code>Debug</code> در GORM به عنوان new session method شناخته می شوند.
<br></br>
<h2>Session :</h2>
یک نوع تابع New Session Method است که امکان ایجاد یک session جدید با حالت configuration را به ما می دهد. با session می توانیم چندین عملیات دیتابیس را در یک واحد منطقی گروه بندی کنیم. برخی از این واحدهای منطقی به این صورت هستند:

<br>

```go
// Session Configuration
type Session struct {
  DryRun                   bool
  PrepareStmt              bool
  NewDB                    bool
  Initialized              bool
  SkipHooks                bool
  SkipDefaultTransaction   bool
  DisableNestedTransaction bool
  AllowGlobalUpdate        bool
  FullSaveAssociations     bool
  QueryFields              bool
  Context                  context.Context
  Logger                   logger.Interface
  NowFunc                  func() time.Time
  CreateBatchSize          int
}
```
<h3>DryRun</h3>
به طور مثال, <code>DryRun</code> به صورت زیر است که در خود کد توضیح داده شده است:

<br>

```go
// session mode
stmt := db.Session(&Session{DryRun: true}).First(&user, 1).Statement
stmt.SQL.String() //=> SELECT * FROM `users` WHERE `id` = $1 ORDER BY `id`
stmt.Vars         //=> []interface{}{1}

// globally mode with DryRun
db, err := gorm.Open(sqlite.Open("gorm.db"), &gorm.Config{DryRun: true})

// different databases generate different SQL
stmt := db.Find(&user, 1).Statement
stmt.SQL.String() //=> SELECT * FROM `users` WHERE `id` = $1 // PostgreSQL
stmt.SQL.String() //=> SELECT * FROM `users` WHERE `id` = ?  // MySQL
stmt.Vars         //=> []interface{}{1}
```
کد بالا, یک SQL را بدون اجرا, تولید می کند. این عملکرد می تواند به ما در آماده کردن یا تست کردن SQL تولیدشده کمک کند.
<br>در ادامه کد بالا, برای تولید SQL نهایی باید از کد زیر استفاده کنیم:

<br>

```go
// NOTE: the SQL is not always safe to execute, GORM only uses it for logs, it might cause SQL injection
db.Dialector.Explain(stmt.SQL.String(), stmt.Vars...)
// SELECT * FROM `users` WHERE `id` = 1
```
<br>
<h3>Skip Hooks</h3>
اگر بخواهیم توابع hook را درنظر نگیریم (Skip کنیم), باید از SkipHooks که یک نوع session mode است استفاده کنیم, مثلا:

<br>

```go
DB.Session(&gorm.Session{SkipHooks: true}).Create(&user)

DB.Session(&gorm.Session{SkipHooks: true}).Model(User{}).Where("age > ?", 18).Updates(&user)
```
<h3>Context</h3>
با context, می توانیم برای عملیات SQL ای که قرار است اجرا شود, context تنظیم کنیم, مانند کد زیر:

<br>

```go
timeoutCtx, _ := context.WithTimeout(context.Background(), time.Second)
tx := db.Session(&Session{Context: timeoutCtx})

tx.First(&user) // query with context timeoutCtx
tx.Model(&user).Update("role", "admin") // update with context timeoutCtx
```
<h3>CreateBatchSize</h3>
default batch size:

<br>

```go
users = [5000]User{{Name: "jinzhu", Pets: []Pet{pet1, pet2, pet3}}...}

db.Session(&gorm.Session{CreateBatchSize: 1000}).Create(&users)
// INSERT INTO users xxx (5 batches)
// INSERT INTO pets xxx (15 batches)
```
توضیحات کد بالا را قبلا داده بودیم.
<br></br>
<h2>Hooks :</h2>
hook ها توابعی هستند که قبل یا بعد creation, querying, updating و deletion فراخوانی می شوند.
<br>حالت کلی توابع hoop به این صورت است:
<code>func(*gorm.DB) error</code>
<br></br>
<h3>Creating an object</h3>
hook های موجود برای درست کردن یک object:

<br>

```
BeforeSave
BeforeCreate
AfterCreate
AfterSave
```
قبل و بعد از ساخت یک user, مراحل زیر را باید انجام دهیم:
<br>
نکته: <code>BeforeCreate</code> و <code>AfterCreate</code>, توابع hook هستند.

<br>

```go
func (u *User) BeforeCreate(tx *gorm.DB) (err error) {
  u.UUID = uuid.New()

  if !u.IsValid() {
    err = errors.New("can't save invalid data")
  }
  return
}

func (u *User) AfterCreate(tx *gorm.DB) (err error) {
  if u.ID == 1 {
    tx.Model(u).Update("role", "admin")
  }
  return
}
```
در کد بالا, تابع <code>BeforeCreate</code>, یک uuid برای instance user می سازد (قبل از ساخته شدن یوزر). پس از ساخته شدن یوزر, تابع <code>AfterCreate</code> برای چک کردن uuid و دیگر عملکردهایی که در کد مشخص اند, فراخوانی می شود.
<br></br>
<h3>Updating an object</h3>
hook های موجود برای update کردن یک object:

<br>

```
BeforeSave
BeforeUpdate
AfterUpdate
AfterSave
```
کد نمونه برای update کردن یک object به صورت زیر است:

<br>

```go
func (u *User) BeforeUpdate(tx *gorm.DB) (err error) {
  if u.readonly() {
    err = errors.New("read only user")
  }
  return
}

// Updating data in same transaction
func (u *User) AfterUpdate(tx *gorm.DB) (err error) {
  if u.Confirmed {
    tx.Model(&Address{}).Where("user_id = ?", u.ID).Update("verfied", true)
  }
  return
}
```
<br></br>
<h3>Deleting an object</h3>
hook های موجود برای حذف کردن یک object:

<br>

```
BeforeDelete
AfterDelete
```
برای این بخش, باید به طور کلی مانند کد زیر عمل کنیم:

<br>

```go
// Updating data in same transaction
func (u *User) AfterDelete(tx *gorm.DB) (err error) {
  if u.Confirmed {
    tx.Model(&Address{}).Where("user_id = ?", u.ID).Update("invalid", false)
  }
  return
}
```
<br></br>
<h3>Querying an object</h3>
hook های موجود برای جستجو کردن یک object:

<br>

```
AfterFind
```
استفاده از <code>AfterFind</code> به صورت زیر خواهد بود:

<br>

```go
func (u *User) AfterFind(tx *gorm.DB) (err error) {
  if u.MemberShip == "" {
    u.MemberShip = "user"
  }
  return
}
```
<br></br>
<h2>Transactions :</h2>
برای اینکه مجموعه ای از عملیات ها را در یک transaction انجام دهیم, به طور کلی باید مانند کد زیر عمل کنیم:

<br>

```go
db.Transaction(func(tx *gorm.DB) error {
  // do some database operations in the transaction (use 'tx' from this point, not 'db')
  if err := tx.Create(&Animal{Name: "Giraffe"}).Error; err != nil {
    // return any error will rollback
    return err
  }

  if err := tx.Create(&Animal{Name: "Lion"}).Error; err != nil {
    return err
  }
  // return nil will commit the whole transaction
  return nil
})
```
<br></br>
<h3>Nested Transactions</h3>
ما در GORM می توانیم زیرمجموعه ای از عملیات های انجام شده در یک scope از یک transaction بزرگتر رابه عقب برگردانیم. کد زیر این عملیات را انجام می دهد:

<br>

```go
db.Transaction(func(tx *gorm.DB) error {
  tx.Create(&user1)

  tx.Transaction(func(tx2 *gorm.DB) error {
    tx2.Create(&user2)
    return errors.New("rollback user2") // Rollback user2
  })

  tx.Transaction(func(tx2 *gorm.DB) error {
    tx2.Create(&user3)
    return nil
  })

  return nil
})
```
<br></br>
<h3>SavePoint, RollbackTo</h3>
GORM به ما این امکان را می دهد تا با استفاده از <code>SavePoint</code> و <code>RollbackTo</code>, نقاط و roll back یک savepoint را ذخیره کنیم, برای این منظور, مانند کد زیر عمل می کنیم:

<br>

```go 
tx := db.Begin()
tx.Create(&user1)

tx.SavePoint("sp1")
tx.Create(&user2)
tx.RollbackTo("sp1") // Rollback user2

tx.Commit() // Commit user1
```
<br></br>
<h2>Migration :</h2>
Migration به روند مدیریت الگو و شکل دیتابیس, که در طول زمان تغییر میکند, می گویند. این عملیات ها شامل creating, modifying و deleting برای جدول ها, ستون ها و دیگر اشیا مربوط به شکل دیتابیس هستند.
<br>
<h3>Auto Migration</h3>
برای اینکه schemaی کلی به روز بماند, باید از <code>AutoMigrate</code> استفاده کنیم. 
<br><code>AutoMigrate</code>, جداول، کلیدهای خارجی از دست رفته، محدودیت‌ها، ستون‌ها و فهرست‌ها را ایجاد می‌کند. در صورتی که اندازه، precision و nullable آن تغییر کند، نوع ستون موجود را تغییر خواهد داد.
<br><code>AutoMigrate</code> برای محافظت از داده ها, ستون های استفاده نشده را حذف نمی کند. 
<br> به این منظور, باید مانند کد زیر عمل کنیم:

<br>

```go
db.AutoMigrate(&User{})
db.AutoMigrate(&User{}, &Product{}, &Order{})

// Add table suffix when creating tables
db.Set("gorm:table_options", "ENGINE=InnoDB").AutoMigrate(&User{})
```
به طور مثال در این روش  عملیات روی جدول ها به صورت زیر خواهد بود:

<br>

```go
// Create table for `User`
db.Migrator().CreateTable(&User{})

// Append "ENGINE=InnoDB" to the creating table SQL for `User`
db.Set("gorm:table_options", "ENGINE=InnoDB").Migrator().CreateTable(&User{})

// Rename old table to new table
db.Migrator().RenameTable(&User{}, &UserInfo{})
db.Migrator().RenameTable("users", "user_infos")
```

عملیات رو ستون ها:

<br>

```go
type User struct {
  Name string
}

// Add name field
db.Migrator().AddColumn(&User{}, "Name")
// Drop name field
db.Migrator().DropColumn(&User{}, "Name")
// Alter name field
db.Migrator().AlterColumn(&User{}, "Name")
// Check column exists
db.Migrator().HasColumn(&User{}, "Name")
```

عملیات روی Constraints:

<br>

```go
type UserIndex struct {
  Name  string `gorm:"check:name_checker,name <> 'jinzhu'"`
}

// Create constraint
db.Migrator().CreateConstraint(&User{}, "name_checker")

// Check constraint exists
db.Migrator().HasConstraint(&User{}, "name_checker")
```
<br></br>
</li>
<h2>Logger :</h2>

GORM به صورت پیشفرض در درون خود یک logger دارد که Slow SQL و ارور ها را چاپ می‌کند:

```go
newLogger := logger.New(
  log.New(os.Stdout, "\r\n", log.LstdFlags), // io writer
  logger.Config{
    SlowThreshold:              time.Second,   // Slow SQL threshold
    LogLevel:                   logger.Silent, // Log level
    IgnoreRecordNotFoundError: true,           // Ignore ErrRecordNotFound error for logger
    ParameterizedQueries:      true,           // Don't include params in the SQL log
    Colorful:                  false,          // Disable color
  },
)

// Globally mode
db, err := gorm.Open(sqlite.Open("test.db"), &gorm.Config{
  Logger: newLogger,
})

// Continuous session mode
tx := db.Session(&Session{Logger: newLogger})
tx.First(&user)
tx.Model(&user).Update("Age", 18)
```

در این لاگر می‌توانید آپشن هایی مانند محدوده و سطح لاگ را تعیین کنید و محدودیت‌هایی را برای آن در نظر بگیرید.

<h3>Log Levels</h3>

در GORM به طور کلی 4 سطح لاگ داریم که Silent - Error - Warn - Info هستند که میزان حساسیت لاگ را تعیین میکنند و این حساسیت از چپ به راست افزایش پیدا می‌کند. نحوه تعیین لول در هنگام دستیابی به یک دیتابیس هم مانند کد پایین تعیین می‌شود:

```go
db, err := gorm.Open(sqlite.Open("test.db"), &gorm.Config{
  Logger: logger.Default.LogMode(logger.Silent),
})
```

<h3>Debug</h3>

برای دیباگ کردن می‌توان از دستور زیر استفاده کرد. فقط باید توجه کنید که قبلش باید سطج لاگ را به logger.info تغییر داده باشید.

```go
db.Debug().Where("name = ?", "jinzhu").First(&User{})
```

<h3>Customize Logger</h3>

می‌توانید لاگر خودتان با تنظیمات مطلوب خود را درست کنید. لازم است برای اینکار اینترفیس زیر را در لاگر خود شامل کنید.

```go
type Interface interface {
  LogMode(LogLevel) Interface
  Info(context.Context, string, ...interface{})
  Warn(context.Context, string, ...interface{})
  Error(context.Context, string, ...interface{})
  Trace(ctx context.Context, begin time.Time, fc func() (sql string, rowsAffected int64), err error)
}
```
<br></br>
<h2>Generic database interface sql.DB :</h2>

یکی از متودهایی که در بطن GORM قرار دارد، متود DB است. این متود یک اینترفیس از جنس ```*sql.DB``` از شیء ```*gorm.DB``` می‌سازد.

```go
// Get generic database object sql.DB to use its functions
sqlDB, err := db.DB()

// Ping
sqlDB.Ping()

// Close
sqlDB.Close()

// Returns database statistics
sqlDB.Stats()
```

<h4>نکته</h4>

اگر دیتابیس کانکشنی که آبجکت ```*gorm.DB``` تعیین کرده است از نوع SQL نباشد تمام این دستورات ارور می‌دهند.


<h3>Connection Pool</h3>

طبیعتا حالا که یک آبجکت از جنس ```*sql.DB``` داریم می‌توانیم از طریق آن connection pool را آنطور که می‌خواهیم تنظیم کنیم.

```go
// Get generic database object sql.DB to use its functions
sqlDB, err := db.DB()

// SetMaxIdleConns sets the maximum number of connections in the idle connection pool.
sqlDB.SetMaxIdleConns(10)

// SetMaxOpenConns sets the maximum number of open connections to the database.
sqlDB.SetMaxOpenConns(100)

// SetConnMaxLifetime sets the maximum amount of time a connection may be reused.
sqlDB.SetConnMaxLifetime(time.Hour)
```
<br></br>
<h2>Performance :</h2>

GORM یک سری از optimization ها را خود انجام می‌دهد اما همچنان امکان تغییر تنظیمات مربوط به آن برای بهینه کردن preformance را به شما می‌دهد.

<li>Disable Default Transaction</li>

GORM عمیات‌های create / update / delete را همواره در یک transaction انجام می‌دهد. این کار علیرغم حفظ یکپارچگی داده‌ها باعث افت سرعت و کاهش کارایی می‌شود. شما می‌توانید این خاصیت را در زمان بازکردن دسترسی به یک دیتابیس لغو کنید.

```go
db, err := gorm.Open(sqlite.Open("gorm.db"), &gorm.Config{
  SkipDefaultTransaction: true,
})
```

<li>Caches Prepared Statement</li>

این کار یک statement از قبل اماده شده را در هنگام انجام هر عملیات SQL درست کرده و آن را برای استفاده‌های بعدی cache می‌کند که باعث نیاز کمتر به دسترسی به خود دیتابیس شده و سرعت را افزایش می‌دهد.
می‌توان این تنظیمات را در ابتدا و در هنگام ایجاد دسترسی به دیتابیس تعیین کرد.

```go
// Globally mode
db, err := gorm.Open(sqlite.Open("gorm.db"), &gorm.Config{
  PrepareStmt: true,
})
```

همچنین می‌توان این خاصیت را در هر session به وجود آورد.

```go
// Session mode
tx := db.Session(&Session{PrepareStmt: true})
tx.First(&user, 1)
tx.Find(&users)
tx.Model(&user).Update("Age", 18)
```

<li>SQL Builder with PreparedStmt</li>

می‌توان statement از قبل آماده شده را در هنگام استفاده از RAW SQL نیز به کار برد.

```go
db, err := gorm.Open(sqlite.Open("gorm.db"), &gorm.Config{
  PrepareStmt: true,
})

db.Raw("select sum(age) from users where role = ?", "admin").Scan(&age)
```

<h3>Select Fields</h3>

اگر هنگام انجام یک query فیلدی را مشخص نکنید، SQL تمام فیلدهارا در نظر گرفته و پاسخ را برای تمام آنها به شما بر می‌گرداند.
برای انتخاب فیلدها باید چنین عمل کنید:

```go
db.Select("Name", "Age").Find(&Users{})
```

به جای این کار می‌توانید یک استراکت API درست کنید و خاصیت smart select fields که بالاتر به آن اشاره شد query خود را انجام دهید.

```go
type User struct {
  ID     uint
  Name   string
  Age    int
  Gender string
  // hundreds of fields
}

type APIUser struct {
  ID   uint
  Name string
}

// Select `id`, `name` automatically when query
db.Model(&User{}).Limit(10).Find(&APIUser{})
// SELECT `id`, `name` FROM `users` LIMIT 10
```

<h3>Index Hints</h3>

یکی از را‌ه‌های سرعت بخشی به انجام query ها indexing و استفاده از hint های مربوطه است. Index hints این اجازه را به شما می‌دهد که تعیین کنید کدام indexها انتخاب شده و چگونه به کار بروند. در ذیل چند استفاده از hints و گونه‌ای که دستور select را تغییر می‌دهند به شکل کامنت مشاهده می‌کنید.

```go
import "gorm.io/hints"

db.Clauses(hints.UseIndex("idx_user_name")).Find(&User{})
// SELECT * FROM `users` USE INDEX (`idx_user_name`)

db.Clauses(hints.ForceIndex("idx_user_name", "idx_user_id").ForJoin()).Find(&User{})
// SELECT * FROM `users` FORCE INDEX FOR JOIN (`idx_user_name`,`idx_user_id`)"

db.Clauses(
  hints.ForceIndex("idx_user_name", "idx_user_id").ForOrderBy(),
  hints.IgnoreIndex("idx_user_name").ForGroupBy(),
).Find(&User{})
// SELECT * FROM `users` FORCE INDEX FOR ORDER BY (`idx_user_name`,`idx_user_id`) IGNORE INDEX FOR GROUP BY (`idx_user_name`)"
```
<br></br>
<h2>Customize Data Types :</h2>

GORM از طریق یک سری از اینترفیس‌ها این اجازه را تا حدی به شما می‌دهد که دیتا تایپ‌های مورد نظر خود را معرفی کرده و آن‌ها را به کار ببرید. 

<h3>Implementing Customized Data Types</h3>

<li>Using Scanner/Valuer interfaces
در این روش، دیتا تایپ خودساخته باید اینترفیس‌های Scanner و Valuer را ایمپلیمنت کرده باشد. یک نمونه از این روش برای استفاده از دیتا تایپ json در میان فیدهای یک مدل آورده شده است.

```go
type JSON json.RawMessage

// Scan scan value into Jsonb, implements sql.Scanner interface
func (j *JSON) Scan(value interface{}) error {
  bytes, ok := value.([]byte)
  if !ok {
    return errors.New(fmt.Sprint("Failed to unmarshal JSONB value:", value))
  }

  result := json.RawMessage{}
  err := json.Unmarshal(bytes, &result)
  *j = JSON(result)
  return err
}

// Value return json value, implement driver.Valuer interface
func (j JSON) Value() (driver.Value, error) {
  if len(j) == 0 {
    return nil, nil
  }
  return json.RawMessage(j).MarshalJSON()
}
```

دیتا تایپ‌هایی وجود دارند که در کامیونیتی ساخته شده و در درون خود پکج‌های Scanner  و Valuer را ایمپلیمنت کرده‌اند. در نتیجه با GORM همگام هستند و می‌توان از آن‌ها برای تایپ‌های فیلدهای مدل‌هایمان استفاده کرد. مثلا می‌توان به تایپ‌های ```uuid```  و ```pq``` اشاره کرد:

```go
import (
  "github.com/google/uuid"
  "github.com/lib/pq"
)

type Post struct {
  ID     uuid.UUID `gorm:"type:uuid;default:uuid_generate_v4()"`
  Title  string
  Tags   pq.StringArray `gorm:"type:text[]"`
}
```
<li>GormDataTypeInterface</li>

در صورتی که استراکت ما اینترفیس GormDataTypeInterface  یا GormDBDataTypeInterface را ایمپلیمنت کرده باشد، GORM از خروجی آن به عنوان دیتا تایپ مورد نظر استفاده می‌کند. بدنه این اینترفیس‌ها در حالت کلی بدین شکل است:

```go
type GormDataTypeInterface interface {
  GormDataType() string
}

type GormDBDataTypeInterface interface {
  GormDBDataType(*gorm.DB, *schema.Field) string
}
```
یکی از فایده‌های معرفی دیتاتایپ‌ها به این شکل قابلیت استفاده از آن‌ها در هنگام نوشتن hook ها است که بالاتر با آن‌ها آشنا شدید.
به این مثال تووجه کنید:

```go
func (JSON) GormDataType() string {
  return "json"
}

type User struct {
  Attrs JSON
}

func (user User) BeforeCreate(tx *gorm.DB) {
  field := tx.Statement.Schema.LookUpField("Attrs")
  if field.DataType == "json" {
    // do something
  }
}
```

>در صورتی که از استراکتی به عنوان دیتاتایپ استفاده کنید که در درون خود هیچکدام از دو اینترفیس نامبرده را ایمپلیمنت نکرده باشد، GORM به طور خودکار تایپ آن فیلد را تایپ اولین فیلد استراکت استفاده شده به عنوان دیتاتایپ در نظر می‌گیرد

```go
type NullString struct {
  String string // use the first field's data type
  Valid  bool
}

type User struct {
  Name NullString // data type will be string
}
```

<li>GormValuerInterface

یکی از اینترفیس‌های درون GORM، اینترفیس ```GormValuerInterface```  است. که این اجازه را به شما می‌دهد تا اینبار از طریق context عملیات‌های create/update را انجام دهید یا اینکه از SQL Expr استفاده کنید. خود این اینترفیس بدنه‌ای به شکل زیر دارد:

```go
type GormValuerInterface interface {
  GormValue(ctx context.Context, db *gorm.DB) clause.Expr
}
```

<li>Create/Update from SQL Expr</li>

در اینجا مثالی از استفاده از SQL Expr برای تشکیل و آپدیت کردن table ها میبینید.

```go
type Location struct {
  X, Y int
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

// Scan implements the sql.Scanner interface
func (loc *Location) Scan(v interface{}) error {
  // Scan a value into struct from database driver
}

type User struct {
  ID       int
  Name     string
  Location Location
}

db.Create(&User{
  Name:     "jinzhu",
  Location: Location{X: 100, Y: 100},
})
// INSERT INTO `users` (`name`,`point`) VALUES ("jinzhu",ST_PointFromText("POINT(100 100)"))

db.Model(&User{ID: 1}).Updates(User{
  Name:  "jinzhu",
  Location: Location{X: 100, Y: 100},
})
// UPDATE `user_with_points` SET `name`="jinzhu",`location`=ST_PointFromText("POINT(100 100)") WHERE `id` = 1

```

در مثال بالا دیتا تایپ Location را برای استفاده به عنوان جنس فیلدها به وجود آوردیم و برای ساخت و آپدیت یک نمونه از مدل User که درون خود فیلدی از جنس Location دارد از ```clause.Expr```  در اینترفیس GormValue استفاده کردیم.

<li>Value based on Context</li>
 یکی دیگر از راه‌های انجام عملیات‌های create/update از طریق اینترفیس GormValuer این است که این عملیات‌ها را بر اساس context انجام دهیم.

 ```go
type EncryptedString struct {
  Value string
}

func (es EncryptedString) GormValue(ctx context.Context, db *gorm.DB) (expr clause.Expr) {
  if encryptionKey, ok := ctx.Value("TenantEncryptionKey").(string); ok {
    return clause.Expr{SQL: "?", Vars: []interface{}{Encrypt(es.Value, encryptionKey)}}
  } else {
    db.AddError(errors.New("invalid encryption key"))
  }

  return
}
 ```
</li>
<br></br>
<h2>Scopes :</h2>

اسکوپ‌ها در اصل توابعی هستند که عملیات‌های منطقی پرکاربرد را در درون خود داشته و بر اساس آنها یک آبجکت ```*gorm.DB``` خروجی می‌دهند که محدودیتی را روی دیتابیس بر اساس عملیات‌های منطقی آورده شده در این توابع اعمال کرده و با توجه به نوع خواسته ما از این محدودیت استفاده می‌شود. در اصل استفاده از اسکوپ‌ها برای جلوگیری از code cuplication در مواقعی است که عملیات‌های منطقی متدوالی تکرار زیاد در استفاده‌های ما دارند.
از اسکوپ‌ها در چندجا استفاده می‌شود.

<h3>Query</h3>


```go
func AmountGreaterThan1000(db *gorm.DB) *gorm.DB {
  return db.Where("amount > ?", 1000)
}

func PaidWithCreditCard(db *gorm.DB) *gorm.DB {
  return db.Where("pay_mode = ?", "card")
}

func PaidWithCod(db *gorm.DB) *gorm.DB {
  return db.Where("pay_mode = ?", "cod")
}

func OrderStatus(status []string) func (db *gorm.DB) *gorm.DB {
  return func (db *gorm.DB) *gorm.DB {
    return db.Scopes(AmountGreaterThan1000).Where("status IN (?)", status)
  }
}

db.Scopes(AmountGreaterThan1000, PaidWithCreditCard).Find(&orders)
// Find all credit card orders and amount greater than 1000

db.Scopes(AmountGreaterThan1000, PaidWithCod).Find(&orders)
// Find all COD orders and amount greater than 1000

db.Scopes(AmountGreaterThan1000, OrderStatus([]string{"paid", "shipped"})).Find(&orders)
// Find all paid, shipped orders that amount greater than 1000
```

مشاهده می‌کنید که امکان ترکیب چند اسکوپ با هم هم وجود دارد و در نتیجه بسیار از میزان کدی که لازم است بنویسیم کم می‌شود.

<h3>Pagination</h3>

```go
func Paginate(r *http.Request) func(db *gorm.DB) *gorm.DB {
  return func (db *gorm.DB) *gorm.DB {
    q := r.URL.Query()
    page, _ := strconv.Atoi(q.Get("page"))
    if page <= 0 {
      page = 1
    }

    pageSize, _ := strconv.Atoi(q.Get("page_size"))
    switch {
    case pageSize > 100:
      pageSize = 100
    case pageSize <= 0:
      pageSize = 10
    }

    offset := (page - 1) * pageSize
    return db.Offset(offset).Limit(pageSize)
  }
}

db.Scopes(Paginate(r)).Find(&users)
db.Scopes(Paginate(r)).Find(&articles)
```

<h3>Pagination</h3>

```go
func Paginate(r *http.Request) func(db *gorm.DB) *gorm.DB {
  return func (db *gorm.DB) *gorm.DB {
    q := r.URL.Query()
    page, _ := strconv.Atoi(q.Get("page"))
    if page <= 0 {
      page = 1
    }

    pageSize, _ := strconv.Atoi(q.Get("page_size"))
    switch {
    case pageSize > 100:
      pageSize = 100
    case pageSize <= 0:
      pageSize = 10
    }

    offset := (page - 1) * pageSize
    return db.Offset(offset).Limit(pageSize)
  }
}

db.Scopes(Paginate(r)).Find(&users)
db.Scopes(Paginate(r)).Find(&articles)
```

<h3>Dynamically Table</h3>

در اینجا از اسکوپ‌ها برای تعیین کردن query tableها به صورت پویا استفاده می‌شود.

```go
func TableOfYear(user *User, year int) func(db *gorm.DB) *gorm.DB {
  return func(db *gorm.DB) *gorm.DB {
    tableName := user.TableName() + strconv.Itoa(year)
    return db.Table(tableName)
  }
}

DB.Scopes(TableOfYear(user, 2019)).Find(&users)
// SELECT * FROM users_2019;

DB.Scopes(TableOfYear(user, 2020)).Find(&users)
// SELECT * FROM users_2020;

// Table form different database
func TableOfOrg(user *User, dbName string) func(db *gorm.DB) *gorm.DB {
  return func(db *gorm.DB) *gorm.DB {
    tableName := dbName + "." + user.TableName()
    return db.Table(tableName)
  }
}

DB.Scopes(TableOfOrg(user, "org1")).Find(&users)
// SELECT * FROM org1.users;

DB.Scopes(TableOfOrg(user, "org2")).Find(&users)
// SELECT * FROM org2.users;
```

<h3>Updates</h3>

از اسکوپ‌ها برای آپدیت کردن و حذف کردن گروهی از رکوردها و نمونه‌ها بر اساس یک سری محدودیت خاص نیز می‌توان استفاده کرد.

```go
func CurOrganization(r *http.Request) func(db *gorm.DB) *gorm.DB {
  return func (db *gorm.DB) *gorm.DB {
    org := r.Query("org")

    if org != "" {
      var organization Organization
      if db.Session(&Session{}).First(&organization, "name = ?", org).Error == nil {
        return db.Where("org_id = ?", organization.ID)
      }
    }

    db.AddError("invalid organization")
    return db
  }
}

db.Model(&article).Scopes(CurOrganization(r)).Update("Name", "name 1")
// UPDATE articles SET name = "name 1" WHERE org_id = 111
db.Scopes(CurOrganization(r)).Delete(&Article{})
// DELETE FROM articles WHERE org_id = 111
```
<br></br>
<h2>Conventions :</h2>

پیشتر در ابتدا در باره‌ی برخی از قرار دادهای از پیش تعیین شده توسط GORM پرداختیم. حال اینجا با جزئیات بیشتری سراغ آنها می‌روم.

<h3>ID as Primary Key</h3>

در این باره صحبت کردیم که GORM به طور پیشفرض در صورت وجود فیلد ```ID``` آن را به عنوان کلید اصلی مدل ما در جدول در نظر می‌گیرد.

```go
type User struct {
  ID   string // field named `ID` will be used as a primary field by default
  Name string
}
```

همچنین با استفاده از تگ ```primaryKey``` می‌توان هر فیلد دلخواه دیگری را برای این منظور در نظر گرفت.

```go
type Animal struct {
  ID     int64
  UUID   string `gorm:"primaryKey"`
  Name   string
  Age    int64
}
```

که در اینجا ما فیلد UUID را به عنوان کلید اصلی در جدول Animals در دیتابیس قرار داده‌ایم.

<h3>Pluralized Table Name</h3>

نکته دیگر این است که GORM هنگام نامگذاری برای tableها، نام استراکتی که مربوط به آن table است را گرفته و به فرمت ```snake_cases``` درآورده و table را نامگذاری می‌کند.
برای مثال اگر استراکتی به نام User، داشته باشیم، اسم table آن در دیتابیس Users خواهد بود

<h4>TableName</h4>

با ایمپلیمنت کرد تابع ```TableName``` برای استراکتمان، می‌توان به شکل زیر برای table مربوط به آن اسم دلخواه گذاشت.

```go
type Tabler interface {
  TableName() string
}

// TableName overrides the table name used by User to `profiles`
func (User) TableName() string {
  return "profiles"
}
```

در اینجا ما اسم دل به خواه profiles را برای table مربوط به استراکت User قرار می‌دهیم.


<h4>Temporarily specify a name</h4>

شما می‌توانید برای یک استراکتی که معرفی کرده‌اید چندین table داشته باشید(به جز آن جدول اولیه‌ای که خود GORM می‌سازد). در این صورت شما باید از دستور ```Table``` استفاده کنید. در هنگام استفاده از این دستور اما شما اجاره دارید که اسمی موقت برای آن جدول ذکر کنید. برای نمونه به مثال زیر توجه کنید:

```go
// Create table `deleted_users` with struct User's fields
db.Table("deleted_users").AutoMigrate(&User{})

// Query data from another table
var deletedUsers []User
db.Table("deleted_users").Find(&deletedUsers)
// SELECT * FROM deleted_users;

db.Table("deleted_users").Where("name = ?", "jinzhu").Delete(&User{})
// DELETE FROM deleted_users WHERE name = 'jinzhu';
```

مشاهده کردید که در این مثال از روی استراکت User جدول deleted_users را ساختیم و روی آن query زده و بخشی از آن را نیز حذف کردیم.

<h3>Column Name</h3>

همانطور که می‌دانید طریقه نامگذاری GORM برای ستون‌های هر جدول، فرمت کردن فیلدهای استراکت به صورت ```snake_case``` و سپس قرار دادن اسم‌های فرمت شده به عنوان نام ستون است.

```go
type User struct {
  ID        uint      // column name is `id`
  Name      string    // column name is `name`
  Birthday  time.Time // column name is `birthday`
  CreatedAt time.Time // column name is `created_at`
}
```

ابلته که می‌توانید با استفاده از تگ ```column``` در جلوی هر فیلد، نام ستونی که از روی آن فیلد قرار است ساخته شود را خودتان تعیین کنید.

```go
type Animal struct {
  AnimalID int64     `gorm:"column:beast_id"`         // set name to `beast_id`
  Birthday time.Time `gorm:"column:day_of_the_beast"` // set name to `day_of_the_beast`
  Age      int64     `gorm:"column:age_of_the_beast"` // set name to `age_of_the_beast`
}
```

<h3>Timestamp Tracking</h3>

همانطور که گفته شد، GORM به طور پیشفرض در صورت وجود فیلدهای CreatedAt و UpdatedAt در استراکت شما، از این فیلدها برای آپدیت کردن زمان ایجاد و یا تغییر مدل استفاده می‌کند.

<h4>CreatedAt</h4>

نمونه‌ای از ست شدن فیلد CreatedAt در هنگام ساختن جداول را در نمونه کد زیر می‌توانید مشاهده کنید. مشاهده کنید که درصورتی که نمونه‌ای را از قبل ساخته باشیم بعد از دستور ```Create``` دیگر فیلد CreatedAt آن تغییری نمی‌کند. همچنین می‌توان به صورت دستی این فیلد را بعدا "Update" کرده و مقدار آن را تغییر داد.



```go
db.Create(&user) // set `CreatedAt` to current time

user2 := User{Name: "jinzhu", CreatedAt: time.Now()}
db.Create(&user2) // user2's `CreatedAt` won't be changed

// To change its value, you could use `Update`
db.Model(&user).Update("CreatedAt", time.Now())
```

درصورتی که بخواهیم این خاصیت پر شدن فیلد CreatedAt به صورت خودکار را لغو کنیم کافی است از تگ ```autoCreateTime``` استفاده کنیم.

```go
type User struct {
  CreatedAt time.Time `gorm:"autoCreateTime:false"`
}
```




<h4>UpdatedAt</h4>

در هنگام آپدیت کردن هر رکورد از یک مدل، درصورت وجود فیلد UpdatedAt در آن استراکت، آخرین تایم تغییر در این فیلد ذخیره می‌شود.  مشاهده کنید که در صورت استفاده از هر کدام از دستورات آپدیت به صورتی که واقعا در جدول تغییری ایجاد نشود مقداری فیلد UpdatedAt را تغییری نمی‌دهد. 
همچنین این فیلد بعد از عمل create کردن تغییری نمی‌کند. اما همواره پس از عمل Save تغییر می‌کند.

```go
db.Save(&user) // set `UpdatedAt` to current time

db.Model(&user).Update("name", "jinzhu") // will set `UpdatedAt` to current time

db.Model(&user).UpdateColumn("name", "jinzhu") // `UpdatedAt` won't be changed

user2 := User{Name: "jinzhu", UpdatedAt: time.Now()}
db.Create(&user2) // user2's `UpdatedAt` won't be changed when creating

user3 := User{Name: "jinzhu", UpdatedAt: time.Now()}
db.Save(&user3) // user3's `UpdatedAt` will change to current time when updating

```

درصورتی که می‌خواهید این ویژگی تعیین خودکار مقدار این فیلد پس از هر تغییر لغو شود کافی است از تگ ```autoUpdateTime``` به صورت زیر استفاده کنید.

```go
type User struct {
  UpdatedAt time.Time `gorm:"autoUpdateTime:false"`
}
```
<br></br>
<h2>Settings :</h2>

GORM متودهای Get - Set - InstanceGet - InstanceSet را برای پاس دادن مقادیر به hookها و توابع دیگر به وجود آورده است.
نمونه‌هایی از این استفاده‌ها را در تکه‌هایی از کد مشاهده خواهید کرد.

<h3>Get - Set</h3>

```go
type User struct {
  gorm.Model
  CreditCard CreditCard
  // ...
}

func (u *User) BeforeCreate(tx *gorm.DB) error {
  myValue, ok := tx.Get("my_value")
  // ok => true
  // myValue => 123
}

type CreditCard struct {
  gorm.Model
  // ...
}

func (card *CreditCard) BeforeCreate(tx *gorm.DB) error {
  myValue, ok := tx.Get("my_value")
  // ok => true
  // myValue => 123
}

myValue := 123
db.Set("my_value", myValue).Create(&User{})
```

<h3>InstanceGet - InstanceSet</h3>

```go
type User struct {
  gorm.Model
  CreditCard CreditCard
  // ...
}

func (u *User) BeforeCreate(tx *gorm.DB) error {
  myValue, ok := tx.InstanceGet("my_value")
  // ok => true
  // myValue => 123
}

type CreditCard struct {
  gorm.Model
  // ...
}

// When creating associations, GORM creates a new `*Statement`, so can't read other instance's settings
func (card *CreditCard) BeforeCreate(tx *gorm.DB) error {
  myValue, ok := tx.InstanceGet("my_value")
  // ok => false
  // myValue => nil
}

myValue := 123
db.InstanceSet("my_value", myValue).Create(&User{})
```
<br></br>
<hr>
<h2 style="text-align:center">منابع</h2>
<hr></hr>
<br>
<li> https://gorm.io/docs/
<li> https://www.theserverside.com/definition/object-relational-mapping-ORM
<li> https://maetl.net/talks/rise-and-fall-of-orm
<li> https://en.wikipedia.org/
</div>