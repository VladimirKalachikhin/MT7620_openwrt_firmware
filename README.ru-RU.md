# Прошивка OpenWRT для wi-fi маршрутизатора на базе MT7620A с GSM модемом[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)
**openwrt 19.07.2**

## Торговые марки
Маршрутизатор выпускается под именем ZBT WE1026, ZBT WE826 и присутствует на Aliexpress под этими и многими другими названиями ([см. ниже](#how-to-buy))  
![hardware](img/IMG_20190309_020856_1600x1200.jpg)   

## Оборудование
128-256MB memory  
16MB FLASH  
HUAWEI ME909 LTE modem  
LAN  
WAN  
USB  
micro SDcard reader

## Описание
Прошивка пытается превратить маршрутизатор в сервер общего назначения в локальной сети, не требующий администрирования.

### Прошивка содержит:  
* Обычный интерфейс OpenWRT с необходимыми дополнениями
* Все коммуникационные возможности OpenWRT: ssh, vpn, routing, firevall и т.д.
* Блокировку рекламы на уровне DNS запросов
* Автоматическое монтирование usb и flash накопителей, с поддержкой в том числе и файловых систем Windows
* Midnight Commander
* Веб-сервер NGINX
* PHP7
* Поддержку разнообразных usb устройств
* Поддержку приёмников GNSS, приёмников AIS и другого, что может [gpsd](https://gpsd.io/). (Однако, в некоторых случаях потребуется дополнительная конфигурация.)

### Прошивка не содержит:
* Возможности установить дополнительное базовое программное обеспечение

### Что работает:
Всё

### Что не работает:
Некоторые LED индикаторы

## Установка прошивки
Лучше всего воспользоваться средствами графического интерфейса OpenWRT, но можно выполнить следующее:  

1. Подключиться к маршрутизатору по ssh.
2. Убедиться, что каталог `/tmp` имеет по крайней мере 16MB свободного пространства, при необходимости - очистить.
3. Смонтировать usb накопитель с прошивкой:  
```
mkdir /mnt/extUSB
mount /dev/sda1 /mnt/extUSB
```
4. Запустить установку прошивки:
```
sysupgrade -v /mnt/extUSB/*.bin
```
эта команда скопирует прошивку в `/tmp` и установит её с сохранением настроек.

## Использование
Веб-приложения и данные должны располагаться на накопителе SD-card, а веб-сервер NGINX должен быть соответствующим образом сконфигурирован. Так, установка навигационного приложения [GaladrielMap](http://galadrielmap.hs-yachten.at/) описана в [/emergencykit/nginx_galadrielmap_conf/README.txt](https://github.com/VladimirKalachikhin/Galadriel-map/tree/master/emergencykit) Другие приложения могут быть установлены аналогично.  
Чтобы заработал приёмник глобального позиционирования -- просто включите его в usb порт.

## Где взять маршрутизатор
Конечно, у китайцев. Вот некоторые продавцы на AliExpress:  
[aliexpress.com/item/32842622527.html](https://www.aliexpress.com/item/32842622527.html)  
[aliexpress.com/item/32802136305.html](https://www.aliexpress.com/item/32802136305.html)  
[aliexpress.com/item/33003636964.html](https://www.aliexpress.com/item/33003636964.html)  
[aliexpress.com/item/32956443588.html](https://www.aliexpress.com/item/32956443588.html)  
[aliexpress.com/item/33011561091.html](https://www.aliexpress.com/item/33011561091.html)  
[aliexpress.com/item/32795180047.html](https://www.aliexpress.com/item/32795180047.html)  
[aliexpress.com/item/32954175411.html](https://www.aliexpress.com/item/32954175411.html)  
разумеется, существует и множество других.  

При покупке убедитесь, что покупаете вариант с 16MB FLASH, HUAWEI ME909 LTE модемом и прошивкой OpenWRT (не SDK). Несоблюдение этих условий потребует изменения конфигурации и последующей самостоятельной сборки прошивки.  
Желателен вариант маршрутизатора с 256NB RAM (обычно 128).

## Самостоятельная сборка прошивки
Вы можете самостоятельно собрать прошивку для маршрутизатора с 32MB FLASH или с другим модемом, пользуясь оригинальной [инструкцией](https://openwrt.org/docs/guide-developer/build-system/start). Файл `diffconfig` с отличиями прилагается.

## Поддержка
Консультации по сборке и/или установке прошивки и веб-приложений можно получить за чашку кофе через [YandexMoney](https://yasobe.ru/na/galadrielmap) или [PayPal](https://paypal.me/VladimirKalachikhin) по адресу [galadrielmap@gmail.com](mailto:galadrielmap@gmail.com)  
Также можно заказать сконфигурированный маршрутизатор с установленными [GaladrielMap](https://github.com/VladimirKalachikhin/Galadriel-map) и [GaladrielCache](https://github.com/VladimirKalachikhin/Galadriel-cache).