# آشنایی با HTML

ممکن است بپرسید تمپلیت چیست؟

تمپلیت (به معنی قالب) فایلی است که می‌توانیم بارها از آن استفاده کنیم و اطلاعات مختلفی را به کمک آن و در یک فرمت ثابت ارائه کنیم. مثلاً شما می‌توانید از یک تمپلیت کمک بگیرید و یک نامه بنویسید چرا که با اینکه هر نامه‌ای پیغام و آدرس متفاوتی دارد، اما از فرمت مشابهی استفاده می‌کند.

یک تمپلیت جنگو توسط زبانی به نام HTML تعریف می‌شود (همان HTML که در بخش اول، **اینترنت چگونه کار می‌کند**، به آن اشاره کرده بودیم).

## HTML چیست؟

HTML نوعی از کد است که توسط مرورگر وب، مانند کروم و فایرفاکس یا سافاری، تفسیر و اجرا می‌شود تا یک صفحه وب را نشان دهد.

HTML مخفف عبارت "HyperText Markup Language" است. **HyperText** به این معنی است که نوعی از نوشته است که هایپرلینک بین صفحات را پشتیبانی می‌کند. **Markup** یعنی ما یک متن را برمی‌داریم و آن را علامت گذاری می‌کنیم تا به سیستم دیگری (مثلاً در اینجا مرورگر وب) بگوییم چطور آن را تفسیر کند. کدهای HTML با **tag** ها ساخته شده اند که هرکدام با `>` آغاز و با `<` پایان می‌یابند. این تگ‌ها **المان‌های** نشانه گذاری هستند.

## اولین تمپلیت شما!

ساختن یک تمپلیت یعنی ساختن یک فایل تمپلیت. هرچیزی، یک فایل است، درست است؟ احتمالاً تا الان این موضوع را متوجه شده اید.

تمپلیت‌ها در دایرکتوری `blog/templates/blog` ذخیره می‌شوند. بنابراین اول یک دایرکتوری به نام `templates` در دایرکتوری وبلاگ بسازید. سپس دایرکتوری دیگری به نام `blog` در داخل آن بسازید:

    blog
    └───templates
        └───blog
    

(ممکن است فکر کنید که چرا دوتا دایرکتوری به نام `blog` لازم داریم. همانطور که بعدتر خواهیم دید این یک سیستم نامگذاری کارآمد برای وقتی است که اوضاع پیچیده‌تر می‌شود.)

حالا یک فایل `post_list.html` (که فعلاً خالی باشد) در دایرکتوری بسازید `blog/templates/blog`.

نگاه کنید که الان وبسایت شما چه شکلی شده است: http://127.0.0.1:8000/

> اگر هنوز پیغام خطا `TemplateDoesNotExist` را می‌بینید، یک بار سرور را قطع و بعد دوباره فعال کنید. به خط فرمان بروید سرور را با زدن Ctrl+C (کلید کنترل و کلید C باهم) قطع کنید و با اجرای دستور `python manage.py runserver` مجدداً فعال کنید.

![تصویر 11.1](images/step1.png)

پیغام خطایی نیست! تبریک :) با اینحال وبسایت شما هنوز چیزی به غیر از یک صفحه خالی نشان نمی‌دهد برای اینکه تمپلیت شما خالی است. لازم است که آن را اصلاح کنیم.

فایل جدید را در ویرایشگر کد باز کنید و موارد زیر را به آن اضافه کنید:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
<!DOCTYPE html>
<html>
<body>
    <p>Hi there!</p>
    <p>It works!</p>
</body>
</html>
```

الان وبسایت شما چطور به نظر می‌رسد؟ به آن سری بزنید تا بفهمید: http://127.0.0.1:8000/

![تصویر 11.2](images/step3.png)

کار می‌کند! خوب شد! :)

* خط `<!DOCTYPE html>` یک تگ HTML نیست. این عبارت فقط نوع فایل را مشخص می‌کند. در اینجا این عبارت به مرورگر اعلام می‌کند که نوع فایل [HTML5](https://html.spec.whatwg.org/#the-doctype) است. همیشه شروع هر نوع فایل HTML5 با همین عبارت شروع می‌شود.
* `<html>` پایه‌ای‌ترین تگ و معمولاً اولین تگ در ابتدای صفحه است و تگ `</html>` معمولاً در انتهای صفحه می‌آید. همانطور که می‌بینید، تمام محتوای وبسایت بین تگ `<html>` در ابتدا و تگ `</html>` در انتها قرار می‌گیرند
* تگ `<p>` برای پاراگراف‌ها به کار می‌رود و تگ `</p>` پایان هر پاراگراف را مشخص می‌کند

## Head and body

هر صفحه HTML همچنین به دو بخش اصلی تقسیم می‌شود: **head** و **body**.

* **head** عنصری است که شامل اطلاعاتی در مورد هر فایل می‌شود که در صفحه نشان داده نمی‌شوند.

* **body** عنصری است که شامل هر چیزی است که در صفحه وبسایت نمایش داده می‌شوند.

ما از `<head>` استفاده می‌کنیم تا در مورد تنظیمات فایل به مرورگر اطلاعاتی بدهیم و `<body>` نشان می‌دهد که چه چیزی واقعاً در صفحه وجود دارد.

برای مثال شما می‌توانید تگ عنوان یا title را به شکل زیر در `<head>`، قرار دهید:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Ola's blog</title>
    </head>
    <body>
        <p>Hi there!</p>
        <p>It works!</p>
    </body>
</html>
```

این فایل‎ را ذخیره کنید و وبسایت خود را دوباره بارگذاری کنید.

![تصویر 11.3](images/step4.png)

توجه کنید که چگونه مرورگر متوجه شد که "Ola's blog" عنوان صفحه شماست؟ مرورگر عبارت `<title>Ola's blog</title>` را تفسیر کرده و آن را به عنوان نام صفحه، در نوار نام صفحه مرورگر قرار داده است (البته عنوان در جاهای دیگری مانند bookmark کردن هم استفاده می‌شود).

احتمالاً تا الان توجه کرده‌اید که هر تگ شروع به همراه یک *تگ پایان* و علامت `/` می‌آید و عوامل در آن نیز *nested* می‌شوند (یعنی شما نمی‌توانید یک تگ را ببندید مگر آنکه تمام تگ‌های درون آن را بسته باشید).

شبیه گذاشتن چیزها در جعبه است. شما یک جعبه بزرگ دارید، `<html></html>`؛ درون آن یک جعبه دیگر `<body></body>`، و این همینطور ادامه دارد تا به کوچکترین جعبه برسد: `<p></p>`.

شما باید از این قوانین *بستن تگ‌ها* و نیز *nesting*، پیروی کنید. اگر این قوانین رعایت نشوند مرورگر ممکن است نتواند فایل شما را درست تفسیر کند و صفحه HTML درست نمایش داده نخواهد شد.

## تنظیم کردن تمپلیت

الان می‌توانید کمی تفریح کنید و تلاش کنید تا تمپلیت خود را تنظیم کنید! در اینجا تعدادی تگ مفید معرفی شده:

* `<h1>heading</h1>` یک تیتر برای عنوان‌های مهم
* `<h2>sub-heading</h2>` یک تیتر برای عنوان‌های کم اهمیت‌تر
* `<h3>sub-sub-heading</h3>` یک زیر عنوان که تا `<h6>` درجه اهمیت آن کمتر می‌شود
* `<p>پاراگراف</p>پاراگرافی از نوشته‌ها`
* `<em>تاکید</em>` بر نوشته شما تاکید می‌کند
* `<strong>تاکید</strong>` تاکید بیشتر روی متن
* `<br>` به خط بعد می‌رود (شما نمی‌توانید چیزی درون تگ br بگذارید و علاوه بر این br، تگِ پایانی ندارد)
* `<a href="https://djangogirls.org">لینک</a>` یک لینک می‌سازد
* `<ul><li>آیتم اول</li><li>آیتم دوم</li></ul>` یک لیست، دقیقاً مانند همین لیست درست می‌کند!
* `<div></div>` یک بخش جدید در صفحه تعریف می‌کند
* `<nav></nav>` مجموعه‌ای از لینک‌های دسترسی را تعریف می‌کند
* `<article></article>`محتوای مستقل و فارق از محیط را مشخص می‌کند
* `<section></section>` یک بخش را در فایل مشخص می‌کند
* `<header></header>` بخش سربرگ یک صفحه را مشخص می‌کند
* `<main></main>` بخش محتوای اصلی صفحه را مشخص می‌کند
* `<aside></aside>` محتوای جانبی نسبت به جایی که در آن قرار گرفته را مشخص می‌کند (مانند منوی کناری)
* `<footer></footer>` بخش پاورقی یک سند را مشخص می‌کند
* `<time></time>` بک زمان (یا تاریخ و زمان) را مشخص می‌کند

اینجا نمونه‌ای از یک تمپلیت کامل داریم. آن را در فایل `blog/templates/blog/post_list.html` کپی کنید:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Django Girls blog</title>
    </head>
    <body>
        <header>
            <h1><a href="/">Django Girls Blog</a></h1>
        </header>

        <article>
            <time>published: 14.06.2014, 12:14</time>
            <h2><a href="">My first post</a></h2>
            <p>Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum. Donec id elit non mi porta gravida at eget metus. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa justo sit amet risus.</p>
        </article>

        <article>
            <time>published: 14.06.2014, 12:14</time>
            <h2><a href="">My second post</a></h2>
            <p>Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum. Donec id elit non mi porta gravida at eget metus. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut f.</p>
        </article>
    </body>
</html>
```

ما اینجا یک بخش `header` و دو بخش 0>article</code> ایجاد کردیم.

* بخش `header` شامل عنوان مقاله وبلاگ ماست - یک عنوان و یک لینک
* دو عنصر `article` شامل پست‌های وبلاگ ما به همراه تاریخ انتشار در یک عنصر `time`، یک عنصر`h2` با عنوان مقاله که قابل کلیک کردن است و عنصر `p` (paragraph) که برای متن مقاله استفاده شده است.

چنین نتیجه ای به ما می‌دهد:

![تصویر 11.4](images/step6.png)

واای! ولی تا اینجا تمپلیت ما دقیقاً **اطلاعات یکسانی** را نمایش می‌دهد درحالیکه قبل‌تر در مورد این صحبت کردیم که تمپلیت به ما اجازه می‌دهد **اطلاعات متفاوتی** را در **قالب یکسان** نمایش دهیم.

آن چیزی که واقعاً می‌خواهیم این است که پست‌های واقعی که در جنگو ادمین اضافه کرده‌ایم را نمایش دهد و این همان چیزی است که در ادامه سراغ آن خواهیم رفت.

## فقط یک چیز دیگر: دیپلوی!

خیلی خوب خواهد بود که همه اینها را به صورت آنلاین بر روی اینترنت ببینیم، درست است؟ پس بیایید یک بار دیگر به کمک PythonAnywhere وبسایت را منتشر کنیم:

### کامیت کنید و کد را بر روی گیتهاب پوش کنید

اول از همه ببینیم کدام فایل ها را به نسبت آخرین انتشار، تغییر داده ایم (این دستور را بر روی کامپیوتر خود اجرا کنید و نه در PythonAnywhere):

{% filename %}خط فرمان{% endfilename %}

    $ git status
    

مطمئن باشید که در دایرکتوری `djangogirls` هستید و به `گیت` اجازه دهید تمام تغییرات ایجاد شده در این دایرکتوری را در نظر بگیرد:

{% filename %}خط فرمان{% endfilename %}

    $ git add .
    

قبل از آنکه همه فایل‌ها را آپلود کنیم بگذارید ببینیم که `گیت` چه فایل‌هایی را آپلود خواهد کرد (تمام فایل‌هایی که `گیت` آپلود خواهد کرد الان سبز رنگ دیده می‌شوند):

{% filename %}خط فرمان{% endfilename %}

    $ git status
    

حالا وقت آن است که بگوییم تمام این تغییرات را در سابقه خودش ذخیره کند. الان می‌خواهیم یک "commit message" یا پیغام کامیت تعریف کنیم که تغییرات ما را توضیح می‌دهد. هرچیزی که دلتان بخواهد می‌توانید تایپ کنید، اما بهتر است توضیحاتی را بنویسید که بعداً متوجه شوید در این مرحله چه تغییراتی داده‌اید.

{% filename %}خط فرمان{% endfilename %}

    $ git commit -m "Changed the HTML for the site."
    

> **نکته** مطمئن باشید که از علامت نقل قول دوتایی در اطراف پیغام مربوط به کامیت استفاده کنید.

وقتی این کار را انجام دادیم تغییرات را در گیتهاب آپلود (push) می‌کنیم:

{% filename %}خط فرمان{% endfilename %}

    $ git push
    

### فایل‌های جدیدتان را بر روی PythonAnywhere ببرید و صفحه وبسایت را دوباره بارگذاری کنید

* سپس دوباره به صفحه **Bash console** خود در [PythonAnywhere](https://www.pythonanywhere.com/consoles/) بروید (یا یک کنسول خط فرمان جدید باز کنید) و دستورات زیر را اجرا کنید:

{% filename %}PythonAnywhere command-line{% endfilename %}

    $ cd ~/<your-pythonanywhere-domain>.pythonanywhere.com
    $ git pull
    [...]
    

یادتان باشد که `<your-pythonanywhere-domain>` را با زیر دامنه اصلی خود در PythonAnywhere عوض کنید البته بدون آکولادها. نام زیردامنه شما معمولاً همان نام کاربری شما در PythonAnywhere است اما در مواردی ممکن است کمی متفاوت باشد (مثلاً اگر نام کاربری شما دارای حروف بزرگ باشد). اگر این دستور کار نکرد از `ls` (لیست کردن فایل‌ها) استفاده کنید تا زیردامنه خود را پیدا کنید و سپس با دستور `cd` به آن دایرکتوری بروید.

حالا منتظر شوید تا فایل‌های شما دانلود شوند. اگر می‌خواهید بدانید که فایل‌ها رسیده اند یا نه به صفحه **"Files"** بروید و کدهای خود بر روی PythonAnywhere را ببینید (شما میتوانید به بقیه فایل‌های خود در PythonAnywhere، از طریق کلید منو در کنسول دسترسی پیدا کنید).

* سرانجام به صفحه ["Web"](https://www.pythonanywhere.com/web_app_setup/) بروید و **Reload** را بزنید.

تغییرات شما آنلاین شده اند! صفحه وبسایت خود را در مرورگرتان دوباره بارگذاری کنید. تغییرات دیده خواهند شد. :)