---
title: Tutorial zur Linux- und macOS-Installation für die Microsoft-Treiber für PHP für SQL Server | Microsoft-Dokumentation
ms.date: 12/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: ulvii
ms.author: v-ulibra
manager: v-mabarw
ms.openlocfilehash: aca4ce5392b9cbac7903666b13e7a9cf544f1004
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "76918378"
---
# <a name="linux-and-macos-installation-tutorial-for-the-microsoft-drivers-for-php-for-sql-server"></a>Tutorial zur Linux- und macOS-Installation für die Microsoft-Treiber für PHP für SQL Server
Die folgende Anleitung setzt eine saubere Umgebung voraus und zeigt, wie PHP 7.x, der Microsoft ODBC-Treiber, der Apache-Webserver und die Microsoft-Treiber für PHP für SQL Server unter Ubuntu 16.04, 18.04 und 19.10, Red Hat 7 und 8, Debian 8, 9, und 10, SUSE 12 und 15, Alpine 3.11 (experimentell) sowie macOS 10.13, 10.14 und 10.15 installiert werden. In dieser Anleitung wird empfohlen, die Treiber mit PECL zu installieren, aber Sie können auch die vorab erstellten Binärdateien von der GitHub-Projektseite [Microsoft Drivers for PHP for SQL Server](https://github.com/Microsoft/msphpsql/releases) (Microsoft-Treiber für PHP für SQL Server) herunterladen und gemäß den Anweisungen unter [Laden der Microsoft-Treiber für PHP für SQL Server](../../connect/php/loading-the-php-sql-driver.md) installieren. Eine Beschreibung des Ladevorgangs von Erweiterungen und die Gründe, warum die Erweiterungen nicht zur php.ini-Datei hinzugefügt werden, finden Sie im Abschnitt zum [Laden der Treiber](../../connect/php/loading-the-php-sql-driver.md#loading-the-driver-at-php-startup).

Mit diesen Anweisungen wird standardmäßig PHP 7.4 installiert. Beachten Sie, dass einige unterstützte Linux-Distributionen standardmäßig PHP 7.1 oder eine frühere Version verwenden, die für die neueste Version der PHP-Treiber für SQL Server nicht unterstützt werden. Achten Sie daher auf die Hinweise am Anfang jedes Abschnitts, um stattdessen PHP 7.2 oder 7.3 zu installieren.

In dieser Anleitung sind auch Anweisungen zum Installieren von PHP FastCGI Process Manager (PHP-FPM) unter Ubuntu enthalten. Dieser ist bei Verwendung des nginx-Webservers anstelle von Apache erforderlich.

## <a name="contents-of-this-page"></a>Inhalt dieser Seite:

- [Installieren der Treiber unter Ubuntu 16.04, 18.04 und 19.10](#installing-the-drivers-on-ubuntu-1604-1804-and-1910)
- [Installieren der Treiber mit PHP-FPM unter Ubuntu](#installing-the-drivers-with-php-fpm-on-ubuntu)
- [Installieren der Treiber unter Red Hat 7 und 8](#installing-the-drivers-on-red-hat-7-and-8)
- [Installieren der Treiber unter Debian 8, 9 und 10](#installing-the-drivers-on-debian-8-9-and-10)
- [Installieren der Treiber unter Suse 12 und 15](#installing-the-drivers-on-suse-12-and-15)
- [Installieren der Treiber unter Alpine 3.11](#installing-the-drivers-on-alpine-311)
- [Installieren der Treiber unter macOS High Sierra, Mojave und Catalina](#installing-the-drivers-on-macos-high-sierra-mojave-and-catalina)

## <a name="installing-the-drivers-on-ubuntu-1604-1804-and-1910"></a>Installieren der Treiber unter Ubuntu 16.04, 18.04 und 19.10

> [!NOTE]
> Ersetzen Sie zum Installieren von PHP 7.2 oder 7.3 in den folgenden Befehlen die Versionsnummer 7.4 durch die Nummer 7.2 oder 7.3.

### <a name="step-1-install-php"></a>Schritt 1: Installieren von PHP
```bash
sudo su
add-apt-repository ppa:ondrej/php -y
apt-get update
apt-get install php7.4 php7.4-dev php7.4-xml -y --allow-unauthenticated
```
### <a name="step-2-install-prerequisites"></a>Schritt 2: Installieren der erforderlichen Komponenten
Installieren Sie den ODBC-Treiber für Ubuntu, indem Sie den Anweisungen auf der [Seite zur Installation von Linux und macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) folgen.

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Schritt 3: Installieren der PHP-Treiber für Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
printf "; priority=20\nextension=sqlsrv.so\n" > /etc/php/7.4/mods-available/sqlsrv.ini
printf "; priority=30\nextension=pdo_sqlsrv.so\n" > /etc/php/7.4/mods-available/pdo_sqlsrv.ini
exit
sudo phpenmod -v 7.4 sqlsrv pdo_sqlsrv
```

Wenn nur eine PHP-Version im System vorhanden ist, kann der letzte Schritt zu `phpenmod sqlsrv pdo_sqlsrv` vereinfacht werden.

### <a name="step-4-install-apache-and-configure-driver-loading"></a>Schritt 4. Installieren von Apache und Konfigurieren des Treiberladevorgangs
```
sudo su
apt-get install libapache2-mod-php7.4 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.4
exit
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Schritt 5: Neustarten von Apache und Testen des Beispielskripts
```
sudo service apache2 restart
```
Hinweise zum [Testen der Installation](#testing-your-installation) finden Sie am Ende dieses Dokuments.

## <a name="installing-the-drivers-with-php-fpm-on-ubuntu"></a>Installieren der Treiber mit PHP-FPM unter Ubuntu

> [!NOTE]
> Ersetzen Sie zum Installieren von PHP 7.2 oder 7.3 in den folgenden Befehlen die Versionsnummer 7.4 durch die Nummer 7.2 oder 7.3.

### <a name="step-1-install-php"></a>Schritt 1: Installieren von PHP
```bash
sudo su
add-apt-repository ppa:ondrej/php -y
apt-get update
apt-get install php7.4 php7.4-dev php7.4-xml php7.4-fpm -y --allow-unauthenticated
```
Überprüfen des Status des PHP-FPM-Diensts durch Ausführen von
```
systemctl status php7.4-fpm
```
### <a name="step-2-install-prerequisites"></a>Schritt 2: Installieren der erforderlichen Komponenten
Installieren Sie den ODBC-Treiber für Ubuntu, indem Sie den Anweisungen auf der [Seite zur Installation von Linux und macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) folgen.

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Schritt 3: Installieren der PHP-Treiber für Microsoft SQL Server
```
sudo pecl config-set php_ini /etc/php/7.3/fpm/php.ini
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
printf "; priority=20\nextension=sqlsrv.so\n" > /etc/php/7.4/mods-available/sqlsrv.ini
printf "; priority=30\nextension=pdo_sqlsrv.so\n" > /etc/php/7.4/mods-available/pdo_sqlsrv.ini
exit
sudo phpenmod -v 7.4 sqlsrv pdo_sqlsrv
```
Wenn nur eine PHP-Version im System vorhanden ist, kann der letzte Schritt zu `phpenmod sqlsrv pdo_sqlsrv` vereinfacht werden.

Überprüfen Sie, ob `sqlsrv.ini` und `pdo_sqlsrv.ini` sich in `/etc/php/7.4/fpm/conf.d/` befinden:
```
ls /etc/php/7.4/fpm/conf.d/*sqlsrv.ini
```
Starten Sie den PHP-FPM-Dienst neu:
```
sudo systemctl restart php7.4-fpm
```

### <a name="step-4-install-and-configure-nginx"></a>Schritt 4. Installieren und Konfigurieren von nginx
```
sudo apt-get update
sudo apt-get install nginx
sudo systemctl status nginx
```
Zum Konfigurieren von nginx müssen Sie die Datei `/etc/nginx/sites-available/default` bearbeiten. Fügen Sie `index.php` zu der Liste unterhalb des Abschnitts `# Add index.php to the list if you are using PHP` hinzu:
```
# Add index.php to the list if you are using PHP
index index.html index.htm index.nginx-debian.html index.php;
```
Ändern Sie als Nächstes den Abschnitt nach `# pass PHP scripts to FastCGI server` wie folgt:
```
# pass PHP scripts to FastCGI server
#
location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/run/php/php7.4-fpm.sock;
}
```
### <a name="step-5-restart-nginx-and-test-the-sample-script"></a>Schritt 5: Neustarten von nginx und Testen des Beispielskripts
```
sudo systemctl restart nginx.service
```
Hinweise zum [Testen der Installation](#testing-your-installation) finden Sie am Ende dieses Dokuments.

## <a name="installing-the-drivers-on-red-hat-7-and-8"></a>Installieren der Treiber unter Red Hat 7 und 8

### <a name="step-1-install-php"></a>Schritt 1: Installieren von PHP

Führen Sie zum Installieren von PHP unter Red Hat 7 Folgendes aus:
> [!NOTE]
> Ersetzen Sie zum Installieren von PHP 7.2 oder 7.3 in den folgenden Befehlen die Zeichenfolge „remi-php74“ durch „remi-php72“ bzw. „remi-php73“.
```
sudo su
yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
yum install https://rpms.remirepo.net/enterprise/remi-release-7.rpm
subscription-manager repos --enable=rhel-7-server-optional-rpms
yum install yum-utils
yum-config-manager --enable remi-php74
yum update
yum install php php-pdo php-xml php-pear php-devel re2c gcc-c++ gcc
```

Führen Sie zum Installieren von PHP unter Red Hat 8 Folgendes aus:
> [!NOTE]
> Ersetzen Sie zum Installieren von PHP 7.2 oder 7.3 in den folgenden Befehlen die Zeichenfolge „remi-7.4“ durch „remi-7.2“ bzw. „remi-7.3“.
```
sudo su
dnf install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm
dnf install https://rpms.remirepo.net/enterprise/remi-release-8.rpm
dnf install yum-utils
dnf module reset php
dnf module install php:remi-7.4
subscription-manager repos --enable codeready-builder-for-rhel-8-x86_64-rpms
dnf update
dnf install php-pdo php-pear php-devel
```

### <a name="step-2-install-prerequisites"></a>Schritt 2: Installieren der erforderlichen Komponenten
Installieren Sie den ODBC-Treiber für Red Hat 7 oder 8, indem Sie den Anweisungen auf der [Installationsseite für Linux und macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) folgen.

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Schritt 3: Installieren der PHP-Treiber für Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/30-pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/20-sqlsrv.ini
exit
```

Alternativ dazu können Sie die Treiber auch aus dem Remi-Repository installieren:
```
sudo yum install php-sqlsrv
```
### <a name="step-4-install-apache"></a>Schritt 4. Installieren von Apache
```
sudo yum install httpd
```
SELinux wird standardmäßig installiert und im Modus „Erzwingen“ ausgeführt. Damit Apache über SELinux eine Verbindung mit Datenbanken herstellen kann, führen Sie den folgenden Befehl aus:
```
sudo setsebool -P httpd_can_network_connect_db 1
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Schritt 5: Neustarten von Apache und Testen des Beispielskripts
```
sudo apachectl restart
```
Hinweise zum [Testen der Installation](#testing-your-installation) finden Sie am Ende dieses Dokuments.

## <a name="installing-the-drivers-on-debian-8-9-and-10"></a>Installieren der Treiber unter Debian 8, 9 und 10

> [!NOTE]
> Ersetzen Sie zum Installieren von PHP 7.2 oder 7.3 in den folgenden Befehlen die Versionsnummer 7.4 durch die Nummer 7.2 oder 7.3.

### <a name="step-1-install-php"></a>Schritt 1: Installieren von PHP
```
sudo su
apt-get install curl apt-transport-https
wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list
apt-get update
apt-get install -y php7.4 php7.4-dev php7.4-xml php7.4-intl
```
### <a name="step-2-install-prerequisites"></a>Schritt 2: Installieren der erforderlichen Komponenten
Installieren Sie den ODBC-Treiber für Debian, indem Sie den Anweisungen auf der [Seite zur Installation von Linux und macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) folgen. 

Möglicherweise müssen Sie auch das richtige Gebietsschema generieren, damit die PHP-Ausgabe in einem Browser korrekt angezeigt wird. Führen Sie zum Beispiel für das Gebietsschema „en_US UTF-8“ die folgenden Befehle aus:
```
sudo su
sed -i 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/g' /etc/locale.gen
locale-gen
```
Möglicherweise müssen Sie `/usr/sbin` zu `$PATH` hinzufügen, da sich die ausführbare Datei `locale-gen` dort befindet.

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Schritt 3: Installieren der PHP-Treiber für Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
printf "; priority=20\nextension=sqlsrv.so\n" > /etc/php/7.4/mods-available/sqlsrv.ini
printf "; priority=30\nextension=pdo_sqlsrv.so\n" > /etc/php/7.4/mods-available/pdo_sqlsrv.ini
exit
sudo phpenmod -v 7.4 sqlsrv pdo_sqlsrv
```

Wenn nur eine PHP-Version im System vorhanden ist, kann der letzte Schritt zu `phpenmod sqlsrv pdo_sqlsrv` vereinfacht werden. Ebenso wie `locale-gen` befindet sich auch `phpenmod` in `/usr/sbin`, daher müssen Sie dieses Verzeichnis möglicherweise zu `$PATH` hinzufügen.

### <a name="step-4-install-apache-and-configure-driver-loading"></a>Schritt 4. Installieren von Apache und Konfigurieren des Treiberladevorgangs
```
sudo su
apt-get install libapache2-mod-php7.4 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.4
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Schritt 5: Neustarten von Apache und Testen des Beispielskripts
```
sudo service apache2 restart
```
Hinweise zum [Testen der Installation](#testing-your-installation) finden Sie am Ende dieses Dokuments.

## <a name="installing-the-drivers-on-suse-12-and-15"></a>Installieren der Treiber unter Suse 12 und 15

> [!NOTE]
> Ersetzen Sie in den folgenden Anweisungen `<SuseVersion>` durch Ihre Version von SUSE. Wenn Sie SUSE Enterprise Linux 15 verwenden, lautet diese SLE_15 oder SLE_15_SP1. Verwenden Sie SLE_12_SP4 (oder höher, sofern zutreffend) für SUSE 12. Nicht alle PHP-Versionen sind für alle Versionen von Suse Linux verfügbar. Unter `http://download.opensuse.org/repositories/devel:/languages:/php` erfahren Sie, welche Versionen von Suse über die Standardversion von PHP verfügen, und unter `http://download.opensuse.org/repositories/devel:/languages:/php:/`, welche anderen Versionen von PHP für welche Versionen von Suse verfügbar sind.

> [!NOTE]
> Pakete für PHP 7.4 sind für SUSE 12 nicht verfügbar. Zur Installation von PHP 7.2 ersetzen Sie die unten gezeigte Repository-URL durch folgende URL: `https://download.opensuse.org/repositories/devel:/languages:/php:/php72/<SuseVersion>/devel:languages:php:php72.repo`.
> Zum Installieren von PHP 7.3 ersetzen Sie die unten gezeigte Repository-URL durch folgende URL: `https://download.opensuse.org/repositories/devel:/languages:/php:/php73/<SuseVersion>/devel:languages:php:php73.repo`.

### <a name="step-1-install-php"></a>Schritt 1: Installieren von PHP
```
sudo su
zypper -n ar -f https://download.opensuse.org/repositories/devel:languages:php/<SuseVersion>/devel:languages:php.repo
zypper --gpg-auto-import-keys refresh
zypper -n install php7 php7-devel php7-openssl
```
### <a name="step-2-install-prerequisites"></a>Schritt 2: Installieren der erforderlichen Komponenten
Installieren Sie den ODBC-Treiber für Suse, indem Sie den Anweisungen auf der [Seite zur Installation von Linux und macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) folgen.

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Schritt 3: Installieren der PHP-Treiber für Microsoft SQL Server
> [!NOTE]
> Wenn die Fehlermeldung „`Connection to 'pecl.php.net:443' failed: Unable to find the socket transport "ssl"`“ angezeigt wird, bearbeiten Sie das pecl-Skript unter /usr/bin/pecl und entfernen in der letzten Zeile den Parameter `-n`. Dieser Parameter verhindert, dass PECL beim Aufruf von PHP INI-Dateien lädt, wodurch das Laden der OpenSSL-Erweiterung verhindert wird.

```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/sqlsrv.ini
exit
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Schritt 4. Installieren von Apache und Konfigurieren des Treiberladevorgangs
```
sudo su
zypper install apache2 apache2-mod_php7
a2enmod php7
echo "extension=sqlsrv.so" >> /etc/php7/apache2/php.ini
echo "extension=pdo_sqlsrv.so" >> /etc/php7/apache2/php.ini
exit
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Schritt 5: Neustarten von Apache und Testen des Beispielskripts
```
sudo systemctl restart apache2
```
Hinweise zum [Testen der Installation](#testing-your-installation) finden Sie am Ende dieses Dokuments.

## <a name="installing-the-drivers-on-alpine-311"></a>Installieren der Treiber unter Alpine 3.11

> [!NOTE]
> Die Unterstützung für Alpine ist experimentell.

> [!NOTE]
> Die Standardversion von PHP ist 7.3. Alternative PHP-Versionen sind für Alpine 3.11 in anderen Repositorys nicht verfügbar. Sie können PHP stattdessen aus der Quelle kompilieren.

### <a name="step-1-install-php"></a>Schritt 1: Installieren von PHP
PHP-Pakete für Alpine finden Sie im Repository `edge/community`. Fügen Sie folgende Zeile zu `/etc/apt/repositories` hinzu, und ersetzen Sie dabei `<mirror>` durch die URL eines Alpine-Repositoryspiegels:
```
http://<mirror>/alpine/edge/community
```
Führen Sie dann Folgendes aus:
```
sudo su
apk update
apk add php7 php7-dev php7-pear php7-pdo php7-openssl autoconf make g++
```
### <a name="step-2-install-prerequisites"></a>Schritt 2: Installieren der erforderlichen Komponenten
Installieren Sie den ODBC-Treiber für Alpine, indem Sie den Anweisungen auf der [Installationsseite für Linux und macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) folgen. 

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Schritt 3: Installieren der PHP-Treiber für Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/10_pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/00_sqlsrv.ini
```
Möglicherweise müssen Sie ein Gebietsschema definieren:
```
export LC_ALL=C
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Schritt 4. Installieren von Apache und Konfigurieren des Treiberladevorgangs
```
sudo apk add php7-apache2 apache2
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Schritt 5: Neustarten von Apache und Testen des Beispielskripts
```
sudo rc-service apache2 restart
```
Hinweise zum [Testen der Installation](#testing-your-installation) finden Sie am Ende dieses Dokuments.


## <a name="installing-the-drivers-on-macos-high-sierra-mojave-and-catalina"></a>Installieren der Treiber unter macOS High Sierra, Mojave und Catalina

Falls noch nicht vorhanden, installieren Sie Brew wie folgt:
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

> [!NOTE]
> Ersetzen Sie zum Installieren von PHP 7.2 oder 7.3 in den folgenden Befehlen php@7.4 durch php@7.2 oder php@7.3.

### <a name="step-1-install-php"></a>Schritt 1: Installieren von PHP

```
brew tap
brew tap homebrew/core
brew install php@7.4
```
PHP sollte jetzt in dem Pfad vorhanden sein. Führen Sie `php -v` aus, um zu überprüfen, ob Sie die richtige PHP-Version verwenden. Falls PHP nicht in dem Pfad zu finden ist oder nicht die richtige Version aufweist, führen Sie Folgendes aus:
```
brew link --force --overwrite php@7.4
```

### <a name="step-2-install-prerequisites"></a>Schritt 2: Installieren der erforderlichen Komponenten
Installieren Sie den ODBC-Treiber für macOS, indem Sie den Anweisungen auf der [Seite zur Installation von Linux und macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) folgen. 

Darüber hinaus kann es erforderlich sein, die GNU-Erstellungstools zu installieren:
```
brew install autoconf automake libtool
```

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Schritt 3: Installieren der PHP-Treiber für Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Schritt 4. Installieren von Apache und Konfigurieren des Treiberladevorgangs
```
brew install apache2
```
Führen Sie folgenden Befehl aus, um nach der Apache-Konfigurationsdatei (`httpd.conf`) für Ihre Apache-Installation zu suchen: 
```
/usr/local/bin/apachectl -V | grep SERVER_CONFIG_FILE
``` 
Mit den folgenden Befehlen wird die erforderliche Konfiguration an `httpd.conf` angefügt. Stellen Sie sicher, dass Sie den vom vorherigen Befehl zurückgegebenen Pfad durch `/usr/local/etc/httpd/httpd.conf` ersetzen:
```
echo "LoadModule php7_module /usr/local/opt/php@7.4/lib/httpd/modules/libphp7.so" >> /usr/local/etc/httpd/httpd.conf
(echo "<FilesMatch .php$>"; echo "SetHandler application/x-httpd-php"; echo "</FilesMatch>";) >> /usr/local/etc/httpd/httpd.conf
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Schritt 5: Neustarten von Apache und Testen des Beispielskripts
```
sudo apachectl restart
```
Hinweise zum [Testen der Installation](#testing-your-installation) finden Sie am Ende dieses Dokuments.

## <a name="testing-your-installation"></a>Testen der Installation

Wenn Sie dieses Beispielskript testen möchten, erstellen Sie eine Datei namens „testsql.php“ im Dokumentenstamm Ihres Systems. Unter Ubuntu, Debian und Red Hat ist dies `/var/www/html/`, unter SUSE `/srv/www/htdocs`, unter Alpine `/var/www/localhost/htdocs` und unter macOS `/usr/local/var/www`. Kopieren Sie folgendes Skript und fügen Sie es dort ein, indem Sie ggf. Server, Datenbank, Benutzername und Kennwort ersetzen. Unter Alpine 3.11 müssen Sie möglicherweise auch im `$connectionOptions`-Array den **CharacterSet** als „UTF-8“ angeben.
```
<?php
$serverName = "yourServername";
$connectionOptions = array(
    "database" => "yourDatabase",
    "uid" => "yourUsername",
    "pwd" => "yourPassword"
);

// Establishes the connection
$conn = sqlsrv_connect($serverName, $connectionOptions);
if ($conn === false) {
    die(formatErrors(sqlsrv_errors()));
}

// Select Query
$tsql = "SELECT @@Version AS SQL_VERSION";

// Executes the query
$stmt = sqlsrv_query($conn, $tsql);

// Error handling
if ($stmt === false) {
    die(formatErrors(sqlsrv_errors()));
}
?>

<h1> Results : </h1>

<?php
while ($row = sqlsrv_fetch_array($stmt, SQLSRV_FETCH_ASSOC)) {
    echo $row['SQL_VERSION'] . PHP_EOL;
}

sqlsrv_free_stmt($stmt);
sqlsrv_close($conn);

function formatErrors($errors)
{
    // Display errors
    echo "Error information: <br/>";
    foreach ($errors as $error) {
        echo "SQLSTATE: ". $error['SQLSTATE'] . "<br/>";
        echo "Code: ". $error['code'] . "<br/>";
        echo "Message: ". $error['message'] . "<br/>";
    }
}
?>
```
Verweisen Sie den Browser auf https://localhost/testsql.php (https://localhost:8080/testsql.php unter macOS). Jetzt sollten Sie eine Verbindung zu Ihrer SQL Server-/Azure SQL-Datenbank herstellen können.

## <a name="see-also"></a>Weitere Informationen  
[Getting Started with the Microsoft Drivers for PHP for SQL Server (Erste Schritte mit dem Microsoft-Treiber für PHP für SQL Server)](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Loading the Microsoft Drivers for PHP for SQL Server (Laden von Microsoft-Treibern für PHP für SQL Server)](../../connect/php/loading-the-php-sql-driver.md)

[Systemanforderungen für Microsoft-Treiber für PHP für SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md)
