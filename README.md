# Онлайн-магазин

Веб-приложение "My shop", в котором:
- можно создать каталог товаров;
- можно сформировать покупательскую корзину с возможностью изменения количства 
товаров в корзине;
- реализована система купонов;
- добавлена платежная система Braintree;
- реализовано динамическое формирование счета в формате .pdf с помощью пакета 
  WeasyPrint;
- реализована отправка уведомлений и счета в формате .pdf о статусе оплаты 
  заказа на электронную почту покупателя;
- реализована интернационализация на английском и русском языках;
- на сайте администрирования реализован экспорт заказов в CSV, а также 
просмотр деталей о заказе и счета в формате .pdf

***

## Стек технологий

Python 3.10.1, Django 4.0.4, Celery 5.2.6, RabbitMQ
***

## Как начать

Необходимо скопировать репозиторий на свой локальный компьютер. Для этого перейти в каталог (например, рабочий стол)
```
cd desktop
```

и выполнить команду
```
git clone https://github.com/rufreedomman/django_online_shop
```

Открыть проект в IDE в новом виртуальном окружении (например, venv), 
активировать его. 
Cкопировать необходимые пакеты, указанные в файле requirements.txt
```
source venv/bin/activate
pip install -r requirements.txt
```

Создать файл .env в корневой папке с содержанием:
```
SECRET_KEY=любой_секретный_ключ_на_ваш_выбор
DEBUG=False
ALLOWED_HOSTS=*,или,ваши,хосты,через,запятые,без,пробелов
```
Перейти в каталог /myshop
```
cd myshop
```
выполнить последовательно команды для активации интернационализации
```
django-admin makemessages --all 
django-admin compilemessages 
```
Выполнить миграцию
```
python manage.py migrate
```
и запустить локальный сервер
```
python manage.py runserver
```

После необходимо создать суперпользователя
```
python manage.py createsuperuser
```
и перейти на сайт администрирования по адресу: http://127.0.0.1:8000/admin/

Далее можно создавать базу данных.

Для подключения онлайн-оплаты Braintree, необходимо зарегистрироваться на 
сайте https://www.braintreepayments.com/sandbox и добавить полученные 
MERCHANT_ID, 
PUBLIC_KEY и PRIVATE_KEY в файл .env
```
BRAINTREE_MERCHANT_ID='XXX' # ID продавца.
BRAINTREE_PUBLIC_KEY='XXX' # Публичный ключ.
BRAINTREE_PRIVATE_KEY='XXX' # Публичный ключ.
```

[![Screenshot-2022-05-27-at-17-29-17.png](https://i.postimg.cc/zfh9fDVp/Screenshot-2022-05-27-at-17-29-17.png)](https://postimg.cc/068tWsGJ)
[![Screenshot-2022-05-27-at-17-32-01.png](https://i.postimg.cc/YqgngDpq/Screenshot-2022-05-27-at-17-32-01.png)](https://postimg.cc/2Vk7NwbP)
[![Screenshot-2022-05-27-at-17-32-21.png](https://i.postimg.cc/bv638KRL/Screenshot-2022-05-27-at-17-32-21.png)](https://postimg.cc/t1xhNvwV)
[![Screenshot-2022-05-27-at-17-35-16.png](https://i.postimg.cc/TYr0hy9K/Screenshot-2022-05-27-at-17-35-16.png)](https://postimg.cc/svg7Ngbz)