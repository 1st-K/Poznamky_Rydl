
#### **L** = **<u>L</u>inux (prostredi)
#### A = <U>A</u>pache (WEB server)
#### M = <u>M</u>ySQL/ <u>M</u>ariaDB (spravce SQL databaze)
#### P = <u>P</u>HP/<u>P</u>ython (generator HTML stranky)
---
# balicky
`apache` - web server
`mariadb` - SQL server
`php` - php interpreter
`php-apache` - extenstion pro propojeni apache a PHP

---
## konfigurace apache

``` bash
sudo systemctl start httpd
sudo systemctl enable httpd
```

`httpd` = **daemon Apache Web Serveru**, na pozadí, poslouchá na portu **80** nebo **443**.
`apachectl` = **nástroj k ovládání httpd**, např. pro restart, test konfigurace, nebo stop služby.

``` bash
sudo nano /etc/httpd/conf/httpd.conf
```

**mod_php funguje jen s mpm_prefork**, takze
zakomentovat `LoadModule mpm_event_module modules/mod_mpm_event.so`
odkomentovat `#LoadModule mpm_prefork_module modules/mod_mpm_prefork.so`
odkomentovat, nebo pridat `LoadModule php_module modules/libphp.so`

pridat path ke svemu serveru `DocumentRoot` (`/srv/http/wordpress`) 
nakonec pridat : 
``` config
AddHandler php-script .php
Include conf/extra/php_module.conf
DirectoryIndex index.php index.html
```

``` bash
sudo apachectl configtest # otestuje sytnax souboru
```

---
## konfigurace mariadb

``` bash
sudo mariadb-install-db --user=mysql --basedir=/usr --datadir=/var/lib/mysql

sudo systemctl start mariadb
sudo systemctl enable mariadb
```

``` bash
sudo mariadb
```

``` sql

CREATE DATABASE <nazev_databaze>; -- kdyz zobrazi '->' chybi ';'
-- vysledek by mel byt Query OK, 1 row affected
GRANT ALL ON <database_name>.* TO '<user>'@'<server>' IDENTIFIED BY '<password>' WITH GRANT OPTION;

-- GRANT ALL = dava uzivateli vsechna opravneni
-- ON <database_name>.* = opravneni plati pro vsechny tabulky databaze
-- '<user>'@'<server>' = novy uzivatel <user> ze <server> (e.g. localhost)
-- IDENTIFIED BY '<password>' = nastavuje heslo
-- WITH GRANT OPTION = umoznuje uzivateli pridavat prava ostatnim uzivatelum
EXIT;
```

``` bash
sudo mariadb -u <user> -p # prihlasujes se novym uzivatelem, zepta se na heslo
```

``` sql
SHOW DATABASES; -- kontrola, ze databaze existuje
EXIT;
```

---
## konfigurace WordPressu

``` bash
cd /srv/http # presun se do DocumentRoot (viz /etc/httpd/conf/httpd.conf)
sudo wget https://wordpress.org/latest.tar.gz
sudo tar -xzf latest.tar.gz
sudo rm latest.tar.gz
sudo chown -R http:http wordpress
cd wordpress
sudo cp wp-config-sample.php wp-config.php # zachovame puvodni template
sudo nano wp-config.php # zacneme konfigurovat kopii
```

soubor bude vypadat zhruba takhle:
``` php
define( 'DB_NAME', 'wordpress_database' ); // databáze, kam WordPress ukládá data
define( 'DB_USER', 'wp_administrator' ); // uživatel, k připojení k databázi.
define( 'DB_PASSWORD', 'adminpassword' ); // heslo k uzivateli
define( 'DB_HOST', 'localhost' ); // kde je databáze, vetsinou localhost
define( 'DB_CHARSET', 'utf8' ); // kódování databáze, většinou utf8
define( 'DB_COLLATE', '' ); // způsob řazení znaků, většinou prázdné (vychozi)
```

dale jsou tam autentizacni klice (`AUTH_KEY`, `SECURE_AUTH_KEY`, `LOGGED_IN_KEY`, `NONCE_KEY`, `AUTH_SALT`, `SECURE_AUTH_SALT`, `LOGGED_IN_SALT` a `NONCE_SALT`)

> klice by mely byt unikatni

vyuzijeme [Wordpress Secret key generator](https://api.wordpress.org/secret-key/1.1/salt/)

na adrese `localhost` by se nam mela objevit administratorska konzole nebo registrace (zalezi, jestli uz jsme wordpress pouzivali)

---
# tvorba prvniho PHP serveru

`cd /srv/http` (eventuelne muzes zmenit opravneni slozky pro zapis bez `sudo`)

**doporuceny prvni prikaz**:
``` php
<?php phpinfo(); ?>
```

vysledek uvidime na `localhost`.

---

# publikovani mimo localhosta

``` bash
sudo nano /etc/httpd/conf/httpd.conf
```
pridej `Listen <port>` na kterem portu chces poslouchat
pridej:
``` php
<VirtualHost *:4000>
    ServerName localhost
    DocumentRoot "/srv/http/wordpress"

    <Directory "/srv/http/wordpress">
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog "/var/log/httpd/wordpress_4000_error.log"
    CustomLog "/var/log/httpd/wordpress_4000_access.log" combined
</VirtualHost>
```

``` bash
sudo apachectl configtest
sudo systemctl restart httpd
```

---

# sprava SQL

``` bash
sudo mariadb
```
### smazani uzivatele

``` sql
DROP USER '<user>'@'<server>';
FLUSH PRIVILEGES;
```

### zmena hesla

``` sql
ALTER USER '<user>'@'<server>' IDENTIFIED BY '<nove_heslo>';
FLUSH PRIVILEGES;
```

pak aktualizace wordpressu:
``` php
define( 'DB_PASSWORD', '<nove_heslo>' );
```

### zmena username

jednodussi - novy uzivatel
pokrocilejsi:
``` sql
USE wordpress_database;

UPDATE wp_users
SET user_login = '<novy_nazev>'
WHERE user_login = '<stary_nazev>';
```

### vypis uzivatelu

``` sql
SELECT User, Host FROM mysql.user;
```

### typy uzivatelu

| *otazka*                  | *typ uzivatele* |
| ------------------------- | --------------- |
| prihlaseni do `/wp-admin` | WordPress       |
| WordPress  k DB           | MariaDB         |
| SSH                       | Linux           |
| apache cte soubory        | Linux (`http`)  |

---



[[SSH port forwarding]]
