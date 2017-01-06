My City Selector Joomla Extension
=================================

Package:     component + module + plugins<br>
Version:     2.0.22

##Системные требования

Joomla >= 3.3.0<br>
PHP >= 5.5

## Общие сведения

My City Selector (MCS) - это расширение для CMS Joomla, позволяющее отображать разную информацию для разных городов.

<img src="https://raw.githubusercontent.com/art-programming-team/mycityselector/develop/doc_images/image-1.jpg" alt="" />


В новой 2й версии основной упор сделан на использование поддоменов для разных городов, так как это самый
лучший способ разделять контент с точки зрения поисковиков.

> *!* Ваш домен должен быть настроен так, чтобы любой произвольный поддомен открывал основной сайт.
> Не нужно создавать много сайтов :) это неверно. Подробнее о настройках домена можно прочитать [тут](https://github.com/art-programming-team/mycityselector/blob/develop/configure_domain.md).

*Примечание: все изображения приводимые здесь основаны на версии Joomla 3.6.x

## Установка

Скачиваете отсюда: https://github.com/art-programming-team/mycityselector/releases

(Предыдущая версия 1.8 доступна здесь https://github.com/art-programming-team/mycityselector/tree/v1.8.x/builder/package)

Расширение включает в себя два плагина (system/plgmycityselector & editors-xtd/mcsinsert), компонент (com_mycityselector) и модуль (mod_mycityselector). Все они ставяться одним пакетом,
поэтому загруженный архив распаковывать не нужно. Устанавливайте как есть.

## Настройка

Для того, чтобы начать пользоваться расширением, необходимо сделать две вещи:

 - Включить модуль "My City Selector MOD" и настроить его.
 - Прописать в настройках компонента "MyCitySelector" базовый домен вашего сайта.
 
<img src="https://raw.githubusercontent.com/art-programming-team/mycityselector/develop/doc_images/config.jpg" alt="" />

После чего, при определенном уровне удачи все должно заработать :)

## Как это использовать?

Расширение позволяет создавать заготовленные тексты для разных городов и в зависимости от
выбранного пользователем города, подставлять их в страницу. Каждому городу на сайте будет
соответствовать свой поддомен, а главный домен будет соответствовать вашему городу
(который вы можете указать в настройках).
Например, ваш сайт krakozyabra.org для вашего родного города по умолчанию. А остальные
города на поддоменах:<br>
spb.krakozyabra.org<br>
minsk.krakozyabra.org<br>
kiev.krakozyabra.org<br>
и так далее в соответствии с настройками.
Позже мы добавим (вернем) возможность указывать для городов не только поддомены но и страницы (в рамках одного домена).

Управление текстами происходит через компонент MyCitySelector в админке, там же и управление
списком городов и настройки компонента.

<img src="https://raw.githubusercontent.com/art-programming-team/mycityselector/develop/doc_images/image-2.png" alt="" />

Часть настроек находится в модуле, который отвечает за отображаемое окно выбора города на сайте.

Для вставки заготовленных текстов на страницы сайта используются специальные маркеры (теги).
Всего есть два вида маркеров:

 - [city Город] текст [/city] - из первой версии
 - {mcs-N} - новый маркер, появился во второй версии.

Тег [city] удобен для небольших надписей или сообщений (и для небольшего количества городов).
Но если городов много и информация для каждого своя, то лучше воспользоваться компонентом
MSC в админке. Основной недостаток этих тегов в том, что на одной странице все теги взаимосвязаны
и отобразить разную информацию в нескольких местах страницы может быть невозможным.
Но в то же время, они могут быть незаменимы, если вам нужно включать разные позиции
модулей для разных городов.
Например так:

```
[city Омск]<jdoc:include type="modules" name="demo1" style="" />[/city]
[city Чита]<jdoc:include type="modules" name="demo2" style="" />[/city]
```

В этом случае, при выборе города "Омск" будут отображаться все модули из позиции "demo1",
а при выборе города "Чита" - из "demo2". Советуем использовать их только при необходимости.

Маркеры {mcs-ID} более продвинутые. Их может быть много на одной странице
и у каждого свои условия по городам. Кроме того, вам не нужно вводить их вручную.
В редакторе Вы можете найти кнопку для вставки маркера в текущую позицию курсора.

<img src="https://raw.githubusercontent.com/art-programming-team/mycityselector/develop/doc_images/image-3.jpg" alt="" />

Просто выбираете нужный контент из списка и вставляете маркер в текст. Все просто.

Перейдем к рассмотрению компонента "MyCitySelector". Откройте подпункт "Страны".

<img src="https://raw.githubusercontent.com/art-programming-team/mycityselector/develop/doc_images/image-5.png" alt="" />

При клике по ссылке "регионы" вы сможете открыть список регионов, относящихся к данной стране. Аналогично и в списке
регионов, так есть ссылка "города". Делая элементы списков неактывными, вы запрещаете их отображение в окне выбора города.
Ничего сложного.

*Примечание*: Регионы Украины и Беларусии еще не заполнены...просим прощения, мы не смогли в георгафию :P Дополним в ближайшее вреееемя.
 Но не расстраивайтесь, Вы ведь можете заполнить их сами, просто используйте кнопку "создать".

Перейдем к управлению текстами. Что тут у нас...?

<img src="https://raw.githubusercontent.com/art-programming-team/mycityselector/develop/doc_images/image-6.jpg" alt="" />

эммм...ну тут собственно пусто. Самое время что-нибудь создать. Предположим (совершенно точно), нам нужно для разных
городов отображать разные адреса и контакты.
Создадим новый текст с названием "Контакты". В качестве текста "по умолчанию" укажем адрес для
основного города. А для остальных городов необходимо воспользоваться
кнопкой "Добавить поле". В добавленное поле вбиваем желаемый город и вводим для него
текст (адрес).

<img src="https://raw.githubusercontent.com/art-programming-team/mycityselector/develop/doc_images/image-7.jpg" alt="" />



## Кастомизация

Изменить внешний вид шаблона модуля можно двумя способами:

 - переопределение шаблона модуля из админки
 - создание своего шаблона
 
Первый способ достаточно прост, необходимо зайти в менеджер шаблонов сайта, кликнуть по названию своего текущего шаблона перейти во вкладку "Переопределение", найти в списке модуль "mod_mycityselector" и кликнуть по нему. После чего в папке шаблона сайта появится копия шаблона модуля. Его можно будет менять как вам вздумается.

Второй способ в общем-то делается также как и первый, но после дублирования также необходимо переименовать файлы шаблона (придумать свое имя для шаблона) и на основе данной копии сделать свой шаблон.

Примечание: javascript файл подключаемый в шаблоне заточен под его верстку, следовательно, его придется корректировать под свою верстку.


*Если вам кажется, что некоторые моменты можно бы было описать лучше или где-то закралась неточность, то можете написать мне об этом на почту или сделать pull request.*


##Благодарности

Спасибо [Vlad-Online](https://github.com/Vlad-Online) за огромную помощь в написании второй версии расширения!

Спасибо [Renderlife](https://github.com/renderlife) за новый дизайн модуля.

И конечно же, спасибо всем, кто помогал в тестировании и/или делал пожертвования.

## Хотите помочь с разработкой?

Краткая информация для разработчиков в [dev.md](DEV.md)