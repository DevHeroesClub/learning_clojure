آموزش کلوژر ۶ - دیتا
-

در [تاپیک قبل](ch5/index.md) با انواع دیتا آشنا شدیم.
در این تاپیک قصد دارم بیشتر درمورد دیتاها صحبت کنیم.

دیتاها هیچ وقت در کامپیوتر به شکل خام و پایه‌ای (شکلی که در تاپیک قبل دیدید) وجود ندارند.
در این تاپیک، با Keyword، symbol، list، vector، map و set آشنا میشیم.
توابعی در کلوژر برای کار کردن با این نوع دیتا وجود داره (مثلا اضافه کردن یک مورد به انتهای یک لیست یا سرچ دنبال یک مورد خاص درون یک مپ) که در تاپیک بعدی به طور مفصل درموردشون صحبت میشه.


keyword
-
کی‌وردها به عنوان نام برای اشاره به مقادیر استفاده میشوند. مثلا در hash-map و sorted-map.
```clojure
:my_keyword
:username
``` 
symbol
--
سمبل قبلا توی [آموزش کلوژر ۲](ch2/index.md) یه مقدار توضیح داده شد.
[quote="lxsameer, post:1, topic:1610"]
سمبل ها فقط شناسنده هستند و بس. یه سمبل یه اسم هست که به چیزی اشاره می کنه. برای مثال اسمی که به یه بایندیگ یا یه فانکشن اشاره می کنه.
[/quote]
[quote="lxsameer, post:9, topic:1610"]
symbol رو می تونی به عنوان یه اسم در نظر بگیری. مثلا نقی یه اسم هست. که می تونه به یه ادم اشاره کنه. اما خود اون ادم نیست. فقط یه اسم هست.
[/quote]

به عنوان مثال وقتی ما یه binding ایجاد میکنیم و یه تابع رو به یه کلمه‌ای بایند میکنیم (یا یه متن یا یه عدد رو به یه کلمه بایند میکنیم) اون کلمه‌ای که بعدا میتونیم برای اشاره به اون تابع (یا هر دیتای دیگه‌ای) استفاده کنیم، یک سمبل هست.

```clojure
(def my-function []
    (println "I don't do much yet."))

(def the-answer 42)

(def the-answer 73)
```
اینجا `my-function` و `the-answer` سمبل هستند.
همونطور که اشاره شد، «سمبل یک اسم هست که به یه چیز اشاره میکنه» ما میتونیم سمبل رو به یک چیز جدید بایند کنیم (در خط سوم مثال بالا اینکار انجام شد) و در این صورت، دیتای قبلی از دست میره و زمانی که سمبل‌مون رو صدا بزنیم دیتای جدید رو دریافت میکنیم.


---
لیست:
-
یک یا چند چیز (یا هیچ‌چیز) که داخل یک پرانتز قرار گرفته باشه و با space از هم جدا شده باشن، لیست نامیده میشن.
برای جدا کردن عناصر لیست، عموما از space استفاده میشه. استفاده از ویرگول (`,`) آپشنال هست و کلوژر ویرگول‌ها رو مثل space میبینه. عموما فقط از space استفاده میشه.

```clojure
()
(my-function)
(my-function 2 3 4)
(+ 23 47 (* (- 4 1)))
'(0 1 1 2 3 5 8 13 21)
```
خط اول، ما یک EmptyList داریم. (برابر با nil نیست!)
خط دوم یک لیست که اسم یک function داخلش قرار داره.
خط سوم یک لیست که اولین عنصرش function هست و موارد بعدی، چیزهایی که به اون تابع فرستاده میشه.
خط چهارم مشابه خط دوم، با این تفاوت که چندتا لیست تودرتو داریم. (همونطور که در تاپیک قبلی گفتم، از داخلی ترین پرانتز شروع میشه به evaluate شدن.)
و خط پنجم یک لیست که فقط شامل یک سری اعداد هست.

در کلوژر، از لیست‌ها برای صدا زدن توابع استفاده میشه. همونطور که در خط ۲ تا ۴ مشاهده کردید. روش کار اینه که عنصر اول لیست، یک تابع هست و عناصر بعدی، دیتا یا توابعی که (به عنوان آرگومان) به تابع اول ارسال میشن.
> توضیح:
توابع در کلوژر، First class هستند. به این معنا که میشه اونها رو به عنوان آرگومان به توابع دیگه داد و یا به عنوان return از یه تابع خروجی گرفت.
در تاپیک‌های بعدی بیشتر درمورد این مساله صحبت میشه.

همچنین، میشه از لیست برای نگهداری «لیستی از چیزها» استفاده کرد. برای اینکه به کلوژر بگیم «این لیست رو evaluate نکن و به شکل دیتا باهاش برخورد کن» باید قبل از پرانتز، single quote بذاریم. مثل خط پنجم. به این‌کار، quote کردن گفته میشه.

> توضیح:
در کلوژر، CODE is DATA & DATA is CODE
شاید در نگاه اول عجیب باشه ولی این ویژگی قابلیتهای خیلی زیادی (Meta Programming) به کلوژر میده که خیلی از زبانهای برنامه نویسی بهش حسادت میکنن. در تاپیکهای پیشرفته به این موضوع میپردازیم.

---

وکتور
-
برای نگهداری دیتا معمولا از وکتور استفاده میشه.
وکتورها سینتکسی شبیه لیست دارن با این تفاوت که داخل `[]` قرار میگیرن. (نیازی به ویرگول گذاشتن نیست)

```clojure
[]
["some string" 2 3 4]
[my-function "Hello World"]
[:some_keyword, "some string" 1234 0]
```
خط سوم، یک وکتور هست که شامل یک تابع و یک string هست. (تابع اجرا نمیشه)
وکتورها صرفا برای نگهداری دیتا استفاده میشوند. و بر خلاف لیست، evaluate نمیشوند.

---
map
-
مپ در کلوژر به صورت `{key value}` وجود دارد و بین هر key-value با key-valueی بعدی، یک ویرگول (آپشنال) قرار دارد
دو نوع map در کلوژر وجود داره.
* hash map
* sorted map
تفاوت hash-map و sorted-map در اینست که در sorted-map بر اساس کلید مرتب شده ولی در hash-map ترتیب اهمیتی ندارد.

hash map
-
```clojure
{}
{:a "string" :z 42 :d \s}
{:a "string", :z 42, :d \s}
{"string as keyword" "value", "the answer" 42}
{:name "Pouya", :age 24, :salary 0, :company "DevHeroes", :last-login "2018-01-02"}
```

sorted map
-
```clojure
{:a 1, :b 2, :z 3}
```
نیاز به مثال دیگه‌ای نیست چون از نظر سینتکس دقیقا مثل hash-map هست.

---

set
--
اگر از زبانهای برنامه نویسی دیگه اومده باشید، احتمالا با `ست`  آشنایی دارید.

> لیستی از دیتاهای unique

به همین سادگی.

```clojure
#{1 3 2 5 12 0)
#{"some string" 2r1001001}
#{[:two 2] [:three 3] [:one 1]}
#{[:two 2] [:three 3] [:one 1] [:two 1234]}
```
توجه کنید که در خط چهارم ما دوتا وکتور با keyword یکسان داریم. set به نوع دیتا توجه نمیکنه (که بخواد unique بودن رو بر اساس keyword تعیین کنه) به همین حاطر منطقا `[:two 2] != [:two 1234]`

>کلوژر همیشه به روش ساده و بدون فکر کردن با دیتا برخورد میکنه.
برای کلوژر فرقی نمیکنه دیتای ما چی باشه و تابع ما چی باشه. «این دیتا رو بفرستم به این تابع نتیجشو برگردونم؟ چشم. انجامش میدم.»
این باعث سادگی بیشتر (پیچیده نبودن) کار میشه.
برای کلوژر حتی تفاوتی بین توابع داخلی و توابعی که ما تعریف میکنیم وجود نداره. فرقی بین `+` و `println` با `my-function` نیست.

