# Alábòójútó Django

Láti ṣàfikún, ṣàtúnṣe àti ṣe ìyọkúrò àwọn àròkọ tí a ṣẹ̀ṣẹ̀ ṣe àwòṣe rẹ̀, a máa lo alábòójútó Django.

Jẹ́ ká ṣí fáìlì `blog/admin.py` náà nínú olóòtú kóòdù náà kí a sì rọ́pò àwọn àkóónú rẹ̀ pẹ̀lú èyí:

{% filename %}blog/admin.py{% endfilename %}

```python
from django.contrib import admin
from .models import Post

admin.site.register(Post)
```

Gẹ́gẹ́ bó o ṣe ríi, a ṣàgbéwọlé (ṣàfikún) àwòṣe Post tí a ṣàlàyé nínú àkòrí tó ṣáájú náà. Láti mú àwòṣe wa fojú hàn lórí ojú-ìwé alábòójútó náà, a nílò láti ṣe àkọsílẹ̀ àwòṣe náà pẹ̀lú `admin.site.register(Post)`.

Ó dáa, àkókò láti ṣàyẹ̀wò àwòṣe Post wa. Rántí láti ṣe `python manage.py runserver` nínú console náà láti bẹ̀rẹ̀ server ayélujára náà. Lọ sí aṣàwákiri rẹ kí o tẹ àdírẹ́ẹ̀sì http://127.0.0.1:8000/admin/. Ìwọ yíò rí ojú-ìwé ìwọlé kan báyìí:

![Ojú-ìwé ìwọlé](images/login_page2.png)

Láti wọlé, o nílò láti ṣẹ̀dá *superuser* kan - account aṣàmúlò kan tó ní àkóso lórí gbogbo nnkan lórí ààyè náà. Padà sí ìlà ìpàṣẹ náà, tẹ `python manage.py createsuperuser`, kí o sì tẹ enter.

> Rántí, láti kọ àwọn àṣẹ tuntun nígbà tí server ayélujára náà bá n ṣiṣẹ́, ṣí fèrèsé èbúté tuntun kan kí o sì mú virtualenv rẹ ṣiṣẹ́. A ti ṣàgbéyẹ̀wò bí a ṣe lè kọ àwọn àṣẹ tuntun nínú àkòrí **Iṣẹ́ Django àkọ́kọ́ rẹ!**, nínú abala **Bíbẹ̀rẹ̀ server ayélujára náà**.

{% filename %}Mac OS X or Linux:{% endfilename %}

    (myvenv) ~/djangogirls$ python manage.py createsuperuser
    

{% filename %}Windows:{% endfilename %}

    (myvenv) C:\Users\Name\djangogirls> python manage.py createsuperuser
    

Nígbà tó bá rí ìbéèrè, tẹ orúkọ aṣàmúlò (lẹ́tà kékeré, láìsí àlàfo), àdírẹ́ẹ̀sì ímeèlì, àti ọ̀rọ̀ aṣínà rẹ. **Má dààmú pé ìwọ kò lè rí ọ̀rọ̀ aṣínà tí o n tẹ̀ wọlé náà – bó ṣe yẹ kí ó rí nìyẹn.** Tẹ̀ ẹ́ wọlé kí o sì tẹ `enter` láti tẹ̀síwájú. Ó yẹ kí èsì náà rí báyìí (níbi tí orúkọ aṣàmúlò àti ímeèlì yíò jẹ́ tìrẹ):

    Username: ola
    Email address: ola@example.com
    Password:
    Password (again):
    Superuser created successfully.
    

Padà sí aṣàwákiri rẹ. Wọlé pẹ̀lú àwọn ẹ̀rí superuser tí o yàn náà; ó yẹ kí o rí pánẹ́ẹ̀lì ìdarí alábòójútó Django náà.

![Alábòójútó Django](images/django_admin3.png)

Lọ sí Posts kí o sì ṣe ìdánrawò díẹ̀ pẹ̀lú rẹ̀. Ṣàfikún àwọn àròkọ blog márùn-ún tàbí mẹ́fà. Má dààmú nípa àkóónú náà – ó fojú hàn sí ìwọ nìkan lórí kọ̀mpútà rẹ -- o lè ṣàdàkọ àwọn ọ̀rọ̀ kan lára àlàyé yìí láti dín àkókò kù. :)

Rí dájú pé ó kéré jù àwọn àròkọ méjì tàbí mẹ́ta (ṣùgbọ́n kìí ṣe gbogbo rẹ̀) ló ní ọjọ́ ìtẹ̀jáde náà. Yíò wúlò tó bá yá.

![Alábòójútó Django](images/edit_post3.png)

If you want to know more about Django admin, you should check Django's documentation: https://docs.djangoproject.com/en/2.2/ref/contrib/admin/

Èyí lè jẹ́ àkókò tó dára láti nawọ́ mú ife kọfí kan (tàbí tíì) tàbí oúnjẹ láti tún fún ara rẹ lókun. O ti ṣẹ̀dá àwòṣe Django àkọ́kọ́ rẹ – o tọ́ sí ìsinmi díẹ̀ kan!