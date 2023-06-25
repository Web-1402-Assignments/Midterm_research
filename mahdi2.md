<h1>GORM</h1>

<div dir="rtl" >

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

<h2>Logger</h2>

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

<h2>Generic database interface sql.DB</h2>
<hr>

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

<h2>Performance</h2>
<hr>

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

<h2>Customize Data Types</h2>
<hr>

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

<h2>Scopes</h2>
<hr>

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
<h2>Conventions</h2>
<hr>

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

<h2>Settings</h2>

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
</div>

