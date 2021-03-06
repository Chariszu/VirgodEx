# Администрирование Django

Чтобы добавлять, редактировать и удалять записи, для которых мы только сделали модель, нам потребуется использовать права администратора в Django.

Откройте файл `blog/admin.py` в редакторе кода и замените его содержимое на:

{% filename %}command-line{% endfilename %}

```python
from django.contrib import admin
from .models import Post

admin.site.register(Post)
```

Как ты можешь заметить, мы импортировали (включили) модель Post, которая была определена в предыдущей главе. Чтобы наша модель стала доступна на странице администрирования, нам нужно зарегистрировать её при помощи `admin.site.register(Post)`.

Хорошо, теперь нам нужно взглянуть на модель Post. Не забудь запустить веб-сервер командой `python manage.py runserver`. Перейдите в ваш браузер и введите адрес http://127.0.0.1:8000/admin /. Ты увидишь страничку авторизации:

![Страница авторизации](images/login_page2.png)

Чтобы залогиниться, тебе сначала нужно создать суперпользователя *superuser* - пользователя, который имеет полный доступ к управлению сайтом. Вернись к консоли, напечатай `python manage.py createsuperuser`, и нажми Enter.

> Помните о том, что вводить новые команды нужно в режиме работающего сервера, откройте новое окно терминала и активируйте ваше вируальное окружение (virtualenv). Мы рассмотрели, как писать новые команды **вашего первого проекта Django!** главе, в разделе **Запуск веб-сервера**.

{% filename %}Mac OS X или Linux:{% endfilename %}

    (myvenv) ~/djangogirls$ python manage.py createsuperuser
    

{% filename %}Windows:{% endfilename %}

    (myvenv) C:\Users\Name\djangogirls> python manage.py createsuperuser
    

При появлении запроса введи имя пользователя (строчными буквами, без пробелов), адрес электронной почты и пароль. **Не беспокойся, что ты не видишь печатаемый пароль - так и должно быть.** Напечатай его и нажми `enter` чтобы продолжить. Результат должен выглядеть следующим образом (имя пользователя и почта соответственно будут твоими):

    Username: ola
    Email address: ola@example.com
    Password:
    Password (again):
    Superuser created successfully.
    

Вернись в браузер и войди в систему при помощи имени пользователя и пароля, которые ты только что выбрала. Ты должна попасть в панель управления Django.

![Django admin](images/django_admin3.png)

Перейди к записям (Post) и поэкспериментируй немного с ними. Добавь 5-6 записей в блог. Не переживай за контент - он видим тебе только на твоем локальном компьютере - ты можешь скопировать-вставить текст из этого туториала, чтобы сэкономить время. :)

Убедитесь, чтобы хотя бы у двух-трёх постов (но не у всех) была дата публикации. Это может быть полезным в будущем.

![Django admin](images/edit_post3.png)

Если ты хочешь узнать больше об администрировании Django, то ознакомься с этим разделом официальной документации: https://docs.djangoproject.com/en/2.2/ref/contrib/admin/

Сейчас, вероятно, подходящий момент, чтобы порадовать себя кружечкой кофе (или чая), а также съесть чего-нибудь для пополнения энергии. Ты только что создал(а) свою первую Django модель и заслужил(а) перерыв!