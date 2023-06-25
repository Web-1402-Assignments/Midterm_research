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

به طور کلی GORM هر struct را به یک table در relational model تبدیل می‌کند. به این نحو که همواره در صورت وجود فیلد ```ID``` آن را به عنوان کلید اصلی در جدول در نظر می‌گیرد و همچنین به عنوان اسم هر table، از اسم struct مربوطه استفاده کرده آما آنرا به فرمت ```snake_case``` در می‌آورد. برای نام ستون‌های table هم که در اصل همان فیلد های struct ما هستند همین‌گونه عمل می‌کند.
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

<img src="tags.png" display="block" margin="auto" alt="Tags in GORM" width="80%" height="100%">

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

<h2>Connecting To A Database</h2>
<hr>

GORM می‌تواند با استفاده از پکچ ```database/sql``` connection pool را کنترل کرده و محدودیت هایی روی ماکسیمم تعداد انواع دسترسی‌ها به دیتابیس بگذارد:

```go
sqlDB, err := db.DB()

// SetMaxIdleConns sets the maximum number of connections in the idle connection pool.
sqlDB.SetMaxIdleConns(10)

// SetMaxOpenConns sets the maximum number of open connections to the database.
sqlDB.SetMaxOpenConns(100)

// SetConnMaxLifetime sets the maximum amount of time a connection may be reused.
sqlDB.SetConnMaxLifetime(time.Hour)
```

</div>
