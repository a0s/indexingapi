# Google Indexing API
**Рад, что вы нашли это репозитарий. Если считаете инструмент полезным, можете угостить меня кофе на Buy Me A Coffee :)**

<a href="https://www.buymeacoffee.com/marekfoltas" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy Me A Coffee" style="height: 41px !important;width: 174px !important;box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;" ></a>

Инструмент позволяет массово отправлять адреса для индексации с помощью Indexing API. Если вы не знаете, что такое Indexing API, то больше информации найдете [здесь](https://developers.google.com/search/apis/indexing-api/v3/quickstart).

Почему стоит использовать этот метод и чем он лучше, чем отправка адресов через Google Search Console?

* можно отправить до 200 адресов в день
* можно отправить до 100 адресов за раз
* адреса, отправленные таким образом, появляются в индексе значительно быстрее, чем при использовании обычных методов

Вот что пишет об этом Google:

> Рекомендуем использовать интерфейс Indexing API вместо карт сайта, так как это обеспечивает более быстрое индексирование страниц Googlebot, чем при обновлении карты сайта и > сигнализации об этом системам Google.

Я использую это на различных сайтах (новых, старых), и каждый раз индексация происходит мгновенно. Обычно все адреса (например, 200 новых подстраниц) появляются в индексе в течение 24 часов после отправки запроса на индексацию.

![indexing api](https://bootcampy.pl/wp-content/uploads/2022/03/18.png "График проиндексированных URL-адресов")

![indexing api](https://bootcampy.pl/wp-content/uploads/2022/03/19.png "График проиндексированных URL-адресов")

## Хорошо, но как это запустить?

### Создайте аккаунт службы в Google Cloud Platform

Чтобы использовать интерфейс Indexing API, сначала нужно создать аккаунт службы в Google Cloud Platform:

* Перейдите по адресу [https://console.developers.google.com/iam-admin/serviceaccounts](https://console.developers.google.com/iam-admin/serviceaccounts)

* Нажмите **СОЗДАТЬ ПРОЕКТ**

  ![создать проект](https://bootcampy.pl/wp-content/uploads/2022/03/1.png "Создать проект")

* Введите название вашего проекта и нажмите **СОЗДАТЬ**

  ![создать](https://bootcampy.pl/wp-content/uploads/2022/03/2.png "Создать")

* Нажмите **СОЗДАТЬ АККАУНТ СЛУЖБЫ**

  ![создать аккаунт службы](https://bootcampy.pl/wp-content/uploads/2022/03/3.png "Создать аккаунт службы")

* Введите название аккаунта, остальное можно пропустить

  ![название аккаунта](https://bootcampy.pl/wp-content/uploads/2022/03/4.png "Введите название аккаунта")

* Сохраните название (E-mail) аккаунта службы, так как вам придется добавить его в GSC

* Рядом с вашим аккаунтом службы нажмите на три точки и выберите **Управление ключами**

  ![управление ключами](https://bootcampy.pl/wp-content/uploads/2022/03/5.png "Управление ключами")

* Создайте новый ключ

  ![создать новый ключ](https://bootcampy.pl/wp-content/uploads/2022/03/6.png "Создать новый ключ")

* Тип ключа JSON

  ![тип ключа JSON](https://bootcampy.pl/wp-content/uploads/2022/03/7.png "Тип ключа JSON")

* Ключ должен сохраниться на диске (файл json)

  ![скачивание ключа на диск](https://bootcampy.pl/wp-content/uploads/2022/03/8.png "Скачивание ключа на диск")


Скачанный файл с ключом будет использован позже, он необходим для правильной работы инструмента.

### Добавьте к проекту интерфейс Indexing API

* Перейдите в библиотеку интерфейсов API

  ![библиотека интерфейсов API](https://bootcampy.pl/wp-content/uploads/2022/03/9.png "Библиотека интерфейсов API")

* Введите в поиске “indexing api”

  ![поиск](https://bootcampy.pl/wp-content/uploads/2022/03/10.png "Введите в поиске indexing API")

* выберите из списка Indexing API

  ![Indexing API](https://bootcampy.pl/wp-content/uploads/2022/03/11.png "Indexing API")

* включите интерфейс

  ![включить интерфейс](https://bootcampy.pl/wp-content/uploads/2022/03/12.png "Включить интерфейс")


### Добавьте аккаунт службы в GSC

Как только у вас будет создан аккаунт службы, добавьте его как **владельца** в Google Search Console:

* войдите в Центр для вебмастеров - [ссылка](https://www.google.com/webmasters/verification/home)
* выберите услугу, к которой хотите добавить аккаунт
* добавьте ранее созданный аккаунт службы

  ![gsc](https://bootcampy.pl/wp-content/uploads/2022/03/13.png "Добавить аккаунт службы в GSC")

### Запустите инструмент

Чтобы запустить инструмент, вам потребуется установленный Node.js и npm, скачать можно [здесь](https://nodejs.org/en/).

Как только вы все настроите, скачайте репозиторий. В папке находится файл service_account.json, он только для примера. Удалите его и вставьте на его место ранее скачанный файл json с ключом. Переименуйте файл в service_account.json.

Откройте проект, например, в Visual Studio Code ([ссылка](https://code.visualstudio.com/)) и в терминале введите:

![npm install](https://bootcampy.pl/wp-content/uploads/2022/03/16.png "npm install")

После завершения установки введите в терминале:


![npm install](https://bootcampy.pl/wp-content/uploads/2022/03/17.png "npm install")

Таким образом вы запустите инструмент, он будет доступен по адресу [http://localhost:8000/](http://localhost:8000/)

В форму вставьте адреса, которые хотите отправить на индексацию.

![форма](https://bootcampy.pl/wp-content/uploads/2022/03/14.png "Форма")

Если все сделано правильно, после отправки формы вы получите ответ с кодом 200. При большом количестве адресов удобнее это просмотреть в консоли браузера.

![response](https://bootcampy.pl/wp-content/uploads/2022/03/15.png "Ответ")
