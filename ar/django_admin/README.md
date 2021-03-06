# دجانغو المشرف

لإضافة وتعديل وحذف المشاركات التي قمنا بإضافتها، سوف نستخدم دجانغو المشرف.

دعونا نفتح `blog/admin.py` ونغير محتواه بهذا:

{% filename %}blog/admin.py{% endfilename %}

```python
from django.contrib import admin
from .models import Post

admin.site.register(Post)
```

كما ترون، نقوم باستيراد (تضمين) نموذج المشاركة المحدد في الفصل السابق. لجعل نموذجنا مرئيا على صفحة المشرف، نحن بحاجة إلى تسجيل النموذج مع `admin.site.register(Post)`.

حسنا حان الوقت للنظر في نموذجنا. تذكر أن تقوم بتشغيل `python manage.py runserver` في وحدة التحكم لتشغيل خادم ويب. اذهب إلى المتصفح واكتب http://127.0.0.1:8000/admin/. ستظهر لك صفحة تسجيل دخول مثل هذه:

![صفحة تسجيل الدّخول](images/login_page2.png)

لتسجيل الدخول، تحتاج إلى إنشاء مستخدم *superuser*-حساب مستخدم له السيطرة على كل شيء في الموقع. ارجع إلى سطر الأوامر، واكتب `python manage.py createsuperuser`,، ثم اضغط على إنتر.

> تذكر، لكتابة الأوامر الجديدة أثناء تشغيل خادم الويب، إفتح نافذة جديدة وفعل البيئة الإفتراضية الخاصة بك. علينا إعادة النظر في كيفية كتابة أوامر جديدة خلال فصل **أول مشروع جانغو لك!** ، في المقطع **بدء تشغيل خادم ويب**.

{% filename %}Mac OS X or Linux:{% endfilename %}

    (myvenv) ~/djangogirls$ python manage.py createsuperuser
    

{% filename %}Windows:{% endfilename %}

    (myvenv) C:\Users\Name\djangogirls> python manage.py createsuperuser
    

عند الطلب، اكتب اسم المستخدم (أحرف صغيرة، لا مسافات)، وعنوان البريد الإلكتروني، وكلمة المرور. **لا تقلق أن كنت لا تستطيع رؤية كلمة المرور التي تكتبها – هكذا يجب ان تعمل-** اكتب فقط واضغط `إدخال` للمواصلة. يجب أن يظهر الناتج على هذا النحو (حيث يجب أن يكون اسم المستخدم والبريد الإلكتروني هو اسم المستخدم الخاص بك):

    Username: admin
    Email address: admin@admin.com
    Password:
    Password (again):
    Superuser created successfully.
    

ارجع إلى المتصفح. سجل الدخول باستخدام بيانات اعتماد المستخدم الخارق التي اخترتها؛ يجب أن ترى لوحة قيادة دجانغو المشرف.

![دجانغو المشرف](images/django_admin3.png)

انتقل إلى المشاركات وقم ببعض الإختبارات هناك. أضف خمس أو ست مشاركات مدونة. لا تقلق بشأن المحتوى - يمكنك ببساطة نسخ ولصق بعض النص من هذا البرنامج التعليمي لتوفير الوقت. :)

تأكد من أن اثنين أو ثلاث مشاركات على الأقل (ليس جميعها) لها تاريخ نشر. سوف يكون هذا مفيد لنا في وقت لاحق.

![دجانغو المشرف](images/edit_post3.png)

إعرف المزيد حول لوحة تحكم دجانغو من خلال قراءة الوثائق الرسمية: https://docs.djangoproject.com/en/1.11/ref/contrib/admin/

ربما تكون هذه لحظة جيدة لشرب كوب من القهوة (أو الشاي) أو لتناول الطعام لإعادة تنشيط نفسك. لقد قمت بإنشاء أول نموذج جانغو خاص بك أنت تستحق الإستراحة قليلا!