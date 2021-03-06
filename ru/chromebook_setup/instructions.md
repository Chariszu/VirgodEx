Можешь [пропустить этот раздел](http://tutorial.djangogirls.org/en/installation/#install-python), если ты не используешь Chromebook. Если же у тебя Chromebook, процесс установки будет немного иным. Вы можете игнорировать остальные инструкции по установке.

### Cloud9

Cloud 9 is a tool that gives you a code editor and access to a computer running on the Internet where you can install, write, and run the software. На протяжении всего курса Cloud9 будет выступать в качестве вашего *локального сервера*. Вы будете работать в терминале (так же, как и ваши одноклассники на OS X, Ubuntu или Windows), но ваш терминал будет подключен к компьютеру где-нибудь в Нидерландах или Германии, которых Cloud9 установили специально для вас.

1. Установка Cloud9 из [Интернет-магазина Chrome](https://chrome.google.com/webstore/detail/cloud9/nbdmccoknlfggadpfkmcpnamfnbkmkcp)
2. Перейти на [c9.io](https://c9.io)
3. Зарегистрируйте учетную запись
4. Нажмите кнопку *создать новую рабочую область (Create a New Workspace)*
5. Назовите его *django-girls*
6. Выберите *blank* (второй справа в нижней строке с оранжевым логотипом)

Теперь вы должны увидеть интерфейс боковой панели, большое главное окно с текстом и небольшое окно в нижней части, которая выглядит примерно так:

{% filename %}Cloud 9{% endfilename %}

    yourusername:~/workspace $
    

This bottom area is your *terminal*, where you will give the computer Cloud 9 has prepared for your instructions. You can resize that window to make it a bit bigger.

### Виртуальное окружение

Виртуальное окружение (также называемое virtualenv или venv) является "коробкой", куда мы можем сложить полезные для нашей программы вещи. Мы используем его, чтобы держать различные биты кода, которые мы хотим использовать для нашего проекта отдельно, не смешивая с другими проектами.

В вашем терминале в нижней части интерфейса Cloud9 выполните следующую команду:

{% filename %}Cloud 9{% endfilename %}

    sudo apt update
    sudo apt install python3.6-venv
    

Если это по-прежнему не работает, спросите вашего наставника помочь.

Далее запустите:

{% filename %}Cloud 9{% endfilename %}

    mkdir djangogirls
    cd djangogirls
    python3.6 -mvenv myvenv
    source myvenv/bin/activate
    pip install django~=1.11.0
    

(обратите внимание, что в последней строке мы используем знак равенства после знака тильды: ~=).

### GitHub

Создайте аккаунт на [GitHub](https://github.com)

### PythonAnywhere

Django Girls пособие включает в себя раздел о "развертывании" - процессе публикации вашего сайта в Интернете.

Эта часть является немного странной, когда у нас Chromebook, поскольку мы используем компьютер, который находится в Интернете (в отличие от, скажем, ноутбука). Однако, это все равно необходимо. Представьте, что Cloud9 - средство для нашей работы, а PythonAnywhere - место для показа.

Зарегистрируйся на [www.pythonanywhere.com](https://www.pythonanywhere.com).