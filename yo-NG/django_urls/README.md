# Àwọn URL Django

A ti fẹ́ kọ́ ojú-ìwé ayélujára àkọ́kọ́ wa: ojú-ìwé ìbẹ̀rẹ̀ kan fún blog wa! Ṣùgbọ́n lákọ̀ọ́kọ́ ná, jẹ́ ká kẹ́kọ̀ọ́ díẹ̀ nípa àwọn URL Django.

## Kíni URL kan?

URL kan jẹ́ àdírẹ́ẹ̀sì ayélujára kan. O lè rí URL kan ní gbogbo ìgbà tí o bá ṣèbẹ̀wò ààyè ayélujára kan – ó fojú hàn nínú pẹpẹ àdírẹ́ẹ̀sì ti aṣàwákiri rẹ. (Bẹ́ẹ̀ ni! `127.0.0.1:8000` jẹ́ URL kan! Àti pé `https://djangogirls.org` tún jẹ́ URL kan.)

![URL](images/url.png)

Gbogbo ojú-ìwé lórí Íńtánẹ́ẹ̀tì náà ló nílò URL tirẹ̀. Lọ́nà yìí, ètò rẹ yíò mọ ohun tó yẹ kó gbé jáde fún aṣàmúlò kan tó bá ṣí URL yẹn. Ní Django, a máa n lo nnkan kan tí a n pè ní `URLconf` (URL configuration - ìṣètò URL). URLconf jẹ́ àpapọ̀ àwọn àpẹẹrẹ kan tí Django yíò gbìyànjú láti báramu pẹ̀lú URL tí a béèrè fún náà láti wá ohun tó tọ́ láti ṣàfihàn.

## Báwo ni àwọn URL ṣé n ṣiṣẹ́ ní Django?

Jẹ́ ká ṣí fáìlì `mysite/urls.py` náà sílẹ̀ nínú olóòtú kóòdù tó wù ẹ kí a wo bó ṣe rí:

{% filename %}mysite/urls.py{% endfilename %}

```python
"""mysite URL Configuration

[...]
"""
from django.contrib import admin
from django.urls import path

urlpatterns = [
    path('admin/', admin.site.urls),
]
```

Gẹ́gẹ́ bó o ṣe ríi, Django ti gbé nnkan kan síbí fún wa tẹ́lẹ̀.

Àwọn ìlà tó wà láàrín àwọn àmì àyọlò mẹ́ta (`'''` or `"""`) ní a n pè ní docstrings – o lè kọ wọ́n sókè fáìlì, kíláàsì tàbí ọ̀nà kan láti ṣàpèjúwe ohun tó n ṣe. Wọn kò ní jẹ́ ṣíṣe nípasẹ̀ Python.

URL alábòójútó náà, èyí tí o ṣèbẹ̀wò sí nínú àkòrí tó ṣáájú náà, tí wà níbí:

{% filename %}mysite/urls.py{% endfilename %}

```python
    path('admin/', admin.site.urls),
```

Ìlà yìí túmọ̀ sí pé fún gbogbo URL tó bá bẹ̀rẹ̀ pẹ̀lú `admin/`, Django yíò wá *view* tó bá á mu kan. Ní irú ìṣẹ̀lẹ̀ yìí, a n ṣàfikún ọ̀pọ̀lọpọ̀ àwọn URL alábòójútó kí a má bàa kó gbogbo rẹ̀ sínú fáìlì kékeré yìí – ó ṣeé kà dáadáa ó sì wà létòlétò.

## URL Django àkọ́kọ́ rẹ!

Àkókò láti ṣẹ̀dá URL àkọ́kọ́ wa! A fẹ́ kí 'http://127.0.0.1:8000/' jẹ́ ojú-ìwé ìbẹ̀rẹ̀ ti blog wa kó sì ṣàfihàn àkójọ àwọn àròkọ kan.

A tún fẹ́ mú fáìlì `mysite/urls.py` náà wà létòlétò, nítorí náà a máa ṣàgbéwọlé àwọn URL láti ètò `blog` wa sí fáìlì `mysite/urls.py` gangan náà.

Tẹ̀síwájú, ṣàfikún ìlà kan tí yíò ṣàgbéwọlé `blog.urls`. Ìwọ yíò tún nílò láti ṣàyípadà ìlà `from django.urls…` náà nítorí pé a n lo iṣẹ́ `include` náà níbí, nítorí náà ìwọ yíò nílò láti ṣàfikún àgbéwọlé yẹn sí ìlà náà.

Ó yẹ kí fáìlì `mysite/urls.py` rẹ rí báyìí:

{% filename %}mysite/urls.py{% endfilename %}

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('blog.urls')),
]
```

Django yíò máa darí gbogbo nnkan tó bá wá sínú 'http://127.0.0.1:8000/' padà sí `blog.urls` tí yíò sì máa wá àwọn ìtọ́sọ́nà míì níbẹ̀.

## blog.urls

Ṣẹ̀dá fáìlì òfìfo tuntun kan tó ń jẹ́ `urls.py` nínú àkójọpọ̀ fáìlì `blog` náà, kí o sì ṣí nínú olóòtú kóòdù náà. Ó dáa! Ṣàfikún àwọn ìlà méjì àkọ́kọ́ wọ̀nyí:

{% filename %}blog/urls.py{% endfilename %}

```python
from django.urls import path
from . import views
```

Níbí yìí, a n ṣàgbéwọlé iṣẹ́ `path` ti Django àti gbogbo `views` wa láti ètò `blog` náà. (A kò tíì ní èyíkéyìí, ṣùgbọ́n a óò débẹ̀ láàárín ìṣẹ́jú kan!)

Lẹ́yìn ìyẹn, a lè ṣàfikún àpẹẹrẹ URL àkọ́kọ́ wa:

{% filename %}blog/urls.py{% endfilename %}

```python
urlpatterns = [
    path('', views.post_list, name='post_list'),
]
```

Gẹ́gẹ́ bó o ṣe ríi, a tí n yan `view` kan tí a n pè ní `post_list` sí URL ìpìlẹ̀ náà báyìí. This URL pattern will match an empty string and the Django URL resolver will ignore the domain name (i.e., http://127.0.0.1:8000/) that prefixes the full URL path. Àpẹẹrẹ yìí yíò sọ fún Django pé `views.post_list` jẹ́ ààyè tó tọ́ láti lọ tí ẹnìkan bá wọ inú ààyè ayélujára rẹ láti àdírẹ́ẹ̀sì 'http://127.0.0.1:8000/' náà.

Apá ìkẹhìn náà, `name='post_list'`, jẹ́ orúkọ URL náà tí yíò máa jẹ́ lílò láti dá view náà mọ̀. Èyí lè jẹ́ bákannáà pẹ̀lú orúkọ view náà ṣùgbọ́n ó tún lè jẹ́ nnkan kan tó yàtọ̀ pátápátá. A ó máa lo àwọn URL tí a fún lórúko tó bá yá nínú iṣé náà, nítorí náà ó ṣe pàtàkì láti fún URL kọ̀ọ̀kan tó wà nínú ètò náà lórúko. Ó yẹ ká tún gbìyànjú láti mú kí orúkọ àwọn URL náà jẹ́ àkànṣe kó sì rọrùn láti rántí.

Tí o bá gbìyànjú láti ṣèbẹ̀wò http://127.0.0.1:8000/ ní báyìí, ìwọ yíò rí oríṣi àwọn ìròyìn 'ojú-ìwé ayélujára kò sí lárọ̀ọ́wọ́tó' kan. Èyí jẹ́ nítorí pé server náà (rántí títẹ `runserver`?) kò ṣiṣẹ́ mọ́. Ṣàyẹ̀wò fèrèsé console server rẹ láti ṣèwádìí ohun tó fà á.

![Àṣìṣe](images/error1.png)

Console rẹ n ṣàfihàn àṣìṣe kan, ṣùgbọ́n má dààmú – ó wúlò púpọ̀ gan-an: ó n sọ fún ọ pé **no attribute 'post_list'**. Ìyẹn jẹ́ orúkọ *view* tí Django n gbìyànjú láti ṣàwárí fún lílò, ṣùgbọ́n a kò tíì ṣẹ̀dá rẹ̀. Níbi tí a dé yìí, `/admin/` rẹ kò tún ní ṣiṣẹ́. Kò sí ìdààmú – a ó dé ibẹ̀. Tí o bá rí ìròyìn àṣìṣe tó yàtọ̀ kan, gbìyànjú láti tún server ayélujára rẹ bẹ̀rẹ̀. To do that, in the console window that is running the web server, stop it by pressing Ctrl+C (the Control and C keys together). On Windows, you might have to press Ctrl+Break. Then you need to restart the web server by running a `python manage.py runserver` command.

> If you want to know more about Django URLconfs, look at the official documentation: https://docs.djangoproject.com/en/2.2/topics/http/urls/