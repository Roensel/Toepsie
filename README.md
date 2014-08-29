Toepsie — Studentenrooster
==========================

[Toepsie](https://toepsie.nl) is een open-source roostersysteem, gebaseerd op het waanzinnige werk van Fontys ICT studenten. Het is onze visie, hoe het eigenlijk zou moeten. Het systeem dat door Fontys zelf aangeboden wordt, is in onze ogen verouderd, wij vinden het eruit zien en werken alsof het in de jaren '80 is gemaakt door een stelletje communisten. Kom op. Framesets, Comic Sans en zelfs GIF-jes met glitters. No joke.

Toepsie is retesnel, overzichtelijk en werkt op al je favoriete apparaten. Zelfs op je **slimme koelkast**. Het past zich automatisch aan de schermgrootte aan, waardoor je in één oogopslag de planning kunt zien, alsmede de docent en het lokaal waar je moet zijn. Ook biedt Toepsie een 'cheatsheet' en een overzicht van de aankomende vakanties. Mét een handige teller, zodat je ook kunt zien hoe lang dat nog duurt.

Uiteraard kan het altijd beter. Tips, feedback en verbeteringen zijn worden met open armen ontvangen. Stuur een mailtje naar [Jeroen](mailto:bofh@toepsie.nl) of maak een issue aan op Github.

# Installatie

Dit project heeft de volgende systeemeisen:

- PHP 5.4+
    + CURL module
- PostgreSQL
- nginx

Na het clonen van dit project kun je in `app/config/app.php` o.a. de URL veranderen en in `app/config/database.php` de database settings aanpassen. Voer daarna `composer install` uit.

Om de database tabellen aan te maken en het rooster eenmalig binnen te halen gebruik je het volgende command:
```shell
php artisan migrate --seed
```

Om het rooster weer te verversen:
```shell
php artisan db:seed
```

# Cronjob

Op de Toepsie site hebben we 3 cronjobs draaien die om `07:30`, `12:00` en `17:00` elke dag het rooster verversen. Dit ziet er zo uit:

```shell
30 7    * * *   www-data    /usr/bin/php /var/www/artisan db:seed >> /var/www/app/storage/logs/cron.log
00 12   * * *   www-data    /usr/bin/php /var/www/artisan db:seed >> /var/www/app/storage/logs/cron.log
00 17   * * *   www-data    /usr/bin/php /var/www/artisan db:seed >> /var/www/app/storage/logs/cron.log
```
# Credits

De mensen achter Toepsie:

- [Jeroen](https://roe.nnie.nl) - BofH
- [Kees](https://www.webduck.nl) - Originele dev
- [Bram](http://www.mashed-creative.nl) - Fundering ontwerp front-end

Voor het rooster systeem maken we gebruik van de volgende projecten:

- [Laravel](http://laravel.com/) - PHP framework
- [Vagrant](http://www.vagrantup.com/) - Virtual Machine management
- [Grunt](http://gruntjs.com/) - JS task runner
- [Bower](http://bower.io/) - Front-end package management
- [jQuery](http://jquery.com/) - JS framework (*duh*)
- [Foundation](http://foundation.zurb.com/) - CSS framework
- [SASS](http://sass-lang.com/) - *CSS with superpowers*
