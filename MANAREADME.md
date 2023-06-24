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