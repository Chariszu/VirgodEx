# Django admin

การ เพิ่ม, แก้ไข และ ลบโพสต์ที่เราเพิ่งสร้างโมเดลไปนั้น เราจะทำโดยใช้ Django admin

Let's open the `blog/admin.py` file in the code editor and replace its contents with this:

{% filename %}blog/admin.py{% endfilename %}

```python
from django.contrib import admin
from .models import Post

admin.site.register(Post)
```

อย่างที่คุณเห็น เรามีการ import (รวม) โมเดลโพสต์ที่เราได้ทำในบทที่แล้วมาด้วย การทำให้โมเดลของเราปรากฎในหน้า admin เราต้องทำการลงทะเบียนโมเดลของเรา โดยใช้ `admin.site.register(Post)`.

เอาล่ะ มาดูกันว่าโมเดลโพสต์ของเราหน้าตาเป็นไง อย่าลืมรัน `python manage.py runserver` ในคอนโซลเพื่อเปิดใช้เว็บเซิร์ฟเวอร์ ไปยังเบราว์เซอร์ของคุณ และพิมพ์ http://127.0.0.1:8000/admin/ คุณจะเห็นหน้าเข้าสู่ระบบ แบบนี้:

![หน้าล็อกอิน](images/login_page2.png)

การเข้าสู่ระบบ คุณต้องสร้าง *superuser* - ซึ่งสามารถควบคุมทุกอย่างบนเว็บนี้ได้ กลับไปยัง command line หรือบรรทัดคำสั่ง พิมพ์ `python manage.py createsuperuser` จากนั้นกด enter

> โปรดจำไว้ว่า ในการเขียนคำสั่งใหม่ในขณะที่เว๊บเซอร์เวอร์กำลังรันอยู่นั้น ให้เปิดหน้าต่างเทอร์มินัลใหม่และเปิดใช้งาน virtualenv เราสามารถตรวจสอบวิธีการเขียนคำสั่งใหม่ในบท **โปรเจ็ค Django แรกของคุณ!** ในส่วน ** การเริ่มต้นเว็บเซิร์ฟเวอร์ </ 0></p> </blockquote> 
> 
> {% filename %}Mac OS X or Linux:{% endfilename %}
> 
>     (myvenv) ~/djangogirls$ python manage.py createsuperuser
>     
> 
> {% filename %}Windows:{% endfilename %}
> 
>     (myvenv) C:\Users\Name\djangogirls> python manage.py createsuperuser
>     
> 
> เมื่อได้รับแจ้ง ให้พิมพ์ username (ด้วยตัวพิมพ์เล็ก ไม่เว้นช่องว่าง) อีเมล์ และรหัสผ่าน **Don't worry that you can't see the password you're typing in – that's how it's supposed to be.** Type it in and press `enter` to continue. ผมลัพธ์ควรมีหน้าตาแบบนี้ (username และอีเมล์ควรจะเป็นของคุณเอง)
> 
>     Username: ola
>     Email address: ola@example.com
>     Password:
>     Password (again):
>     Superuser created successfully.
>     
> 
> กลับไปยังเบราว์เซอร์ของคุณ เข้าระบบด้วยบัญชีที่คุณเพิ่งสร้างเมื่อสักครู่ คุณก็จะเห็นหน้าแดชบอร์ดของ Django admin แล้วตอนนี้
> 
> ![Django admin](images/django_admin3.png)
> 
> Go to Posts and experiment a little bit with it. Add five or six blog posts. Don't worry about the content –- it's only visible to you on your local computer -- you can copy-paste some text from this tutorial to save time. :)
> 
> ตรวจสอบให้แน่ใจว่า อย่างน้อยสองหรือสามโพสต์ (แต่ไม่ต้องทั้งหมด) มีการตั้งค่าวันที่เผยแพร่ เราจะใช้ประโยชน์จากส่วนนี้ในภายหลัง
> 
> ![Django admin](images/edit_post3.png)
> 
> If you want to know more about Django admin, you should check Django's documentation: https://docs.djangoproject.com/en/2.2/ref/contrib/admin/
> 
> ตอนนี้น่าจะเป็นช่วงเวลาจิบกาแฟ (หรือชา) หรือหาอะไรทานเพื่อเพิ่มพลัง คุณได้สร้างโมเดล Django แรกของคุณ - และคุณสมควรที่จะได้พักบ้าง!