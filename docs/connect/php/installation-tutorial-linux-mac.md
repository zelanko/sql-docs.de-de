---
title: Linux und MacOS-Installation-Tutorial für Microsoft Drivers for PHP for SQL Server | Microsoft-Dokumentation
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: ulvii
ms.author: v-ulibra
manager: v-mabarw
ms.openlocfilehash: a31b17b8fbe2130b84b27be08d1a6218d697f9f2
ms.sourcegitcommit: 958cffe9288cfe281280544b763c542ca4025684
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 02/23/2019
ms.locfileid: "56744630"
---
# <a name="linux-and-macos-installation-tutorial-for-the-microsoft-drivers-for-php-for-sql-server"></a>Linux und MacOS-Installation-Tutorial für Microsoft Drivers for PHP for SQL Server
Die folgenden Anweisungen wird davon ausgegangen eine saubere Umgebung und zeigen, wie zum Installieren von PHP 7.x, den Microsoft ODBC-Treiber, Apache und Microsoft Drivers for PHP for SQL Server unter Ubuntu 16.04, 18.04 und 18.10, Red Hat 7 Debian 8 und 9, Suse 12 und 15 und MacOS 10.12 , 10.13 und 10.14. Diese Anweisungen empfehlen die Verwendung von PECL Treiber installieren, aber Sie können auch die vorab erstellte Binärdateien aus dem [Microsoft Drivers for PHP for SQL Server](https://github.com/Microsoft/msphpsql/releases) Github-Projektseite und installieren sie die Anweisungen im [ Laden die Microsoft-Treiber für PHP für SQLServer](../../connect/php/loading-the-php-sql-driver.md). Eine Erläuterung der Erweiterung laden, und warum wir nicht die Erweiterungen "PHP.ini" hinzugefügt werden, finden Sie im Abschnitt für [Laden der Treiber](../../connect/php/loading-the-php-sql-driver.md##loading-the-driver-at-php-startup).

Diese Anweisungen PHP 7.3 standardmäßig installiert werden. Beachten Sie, dass einige unterstützten Linux-Distributionen werden standardmäßig mit PHP 7.0 oder früher, dies wird nicht für die PHP-Treiber für SQL Server – unterstützt finden Sie Hinweise am Anfang jedes Abschnitts PHP 7.1 oder 7.2 stattdessen zu installieren.

## <a name="contents-of-this-page"></a>Inhalt dieser Seite:

- [Installieren die Treiber auf Ubuntu 16.04, 18.04 und 18.10](#installing-the-drivers-on-ubuntu-1604-1804-and-1810)
- [Installation des Treibers auf Red Hat 7](#installing-the-drivers-on-red-hat-7)
- [Installieren die Treiber für Debian 8 und 9](#installing-the-drivers-on-debian-8-and-9)
- [Installieren die Treiber unter Suse 12 und 15](#installing-the-drivers-on-suse-12-and-15)
- [Installieren die Treiber unter MacOS Sierra High Sierra und Mojave](#installing-the-drivers-on-macos-sierra-high-sierra-and-mojave)

## <a name="installing-the-drivers-on-ubuntu-1604-1804-and-1810"></a>Installieren die Treiber auf Ubuntu 16.04, 18.04 und 18.10

> [!NOTE]
> Ersetzen Sie zum Installieren von PHP-7.1 oder 7.2, 7.3, 7.1 oder 7.2, in den folgenden Befehlen.

### <a name="step-1-install-php"></a>Schritt 1: Installieren von PHP
```
sudo su
add-apt-repository ppa:ondrej/php -y
apt-get update
apt-get install php7.3 php7.3-dev php7.3-xml -y --allow-unauthenticated
```
### <a name="step-2-install-prerequisites"></a>Schritt 2: Installieren der erforderlichen Komponenten
Installieren Sie den ODBC-Treiber für Ubuntu, mithilfe der Anweisungen auf der [Linux und MacOS-Installationsseite](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Schritt 3: Installieren Sie die PHP-Treiber für Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/30-pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/20-sqlsrv.ini
exit
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Schritt 4. Installieren von Apache, und konfigurieren Sie die Treiber laden
```
sudo su
apt-get install libapache2-mod-php7.2 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.3
echo "extension=pdo_sqlsrv.so" >> /etc/php/7.3/apache2/conf.d/30-pdo_sqlsrv.ini
echo "extension=sqlsrv.so" >> /etc/php/7.3/apache2/conf.d/20-sqlsrv.ini
exit
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Schritt 5. Starten Sie Apache neu, und Testen Sie das Beispielskript
```
sudo service apache2 restart
```
Um die Installation testen zu können, finden Sie unter [Testen Ihrer Installation](#testing-your-installation) am Ende dieses Dokuments.

## <a name="installing-the-drivers-on-red-hat-7"></a>Installation des Treibers auf Red Hat 7

> [!NOTE]
> Ersetzen Sie zum Installieren von PHP-7.1 oder 7.2, Remi-php73 Remi-php71 oder Remi-php72 bzw. in den folgenden Befehlen.

### <a name="step-1-install-php"></a>Schritt 1: Installieren von PHP

```
sudo su
wget https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
wget https://rpms.remirepo.net/enterprise/remi-release-7.rpm
rpm -Uvh remi-release-7.rpm epel-release-latest-7.noarch.rpm
subscription-manager repos --enable=rhel-7-server-optional-rpms
yum install yum-utils
yum-config-manager --enable remi-php73
yum update
yum install php php-pdo php-xml php-pear php-devel re2c gcc-c++ gcc
```
### <a name="step-2-install-prerequisites"></a>Schritt 2: Installieren der erforderlichen Komponenten
Installieren Sie den ODBC-Treiber für Red Hat 7 mithilfe der Anweisungen auf der [Linux und MacOS-Installationsseite](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

Kompilieren die PHP-Treiber mit PECL mit PHP 7.2 oder 7.3 erfordert eine neuere GCC als den Standardwert:
```
sudo yum-config-manager --enable rhel-server-rhscl-7-rpms
sudo yum install devtoolset-7
scl enable devtoolset-7 bash
```
### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Schritt 3: Installieren Sie die PHP-Treiber für Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/30-pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/20-sqlsrv.ini
exit
```
Ein Problem in PECL möglicherweise korrekte Installation der neuesten Version der Treiber zu verhindern, dass selbst wenn Sie GCC aktualisiert haben. Zum Installieren, die Pakete herunterladen und manuell kompilieren (ähnliche Schritte für Pdo_sqlsrv):
```
pecl download sqlsrv
tar xvzf sqlsrv-5.6.0.tgz
cd sqlsrv-5.6.0/
phpize
./configure --with-php-config=/usr/bin/php-config
make
sudo make install
```
Sie können alternativ die vorab erstellte Binärdateien aus dem [Projektseite auf Github](https://github.com/Microsoft/msphpsql/releases), oder installieren Sie aus dem Repository Remi:
```
sudo yum install php-sqlsrv
```
### <a name="step-4-install-apache"></a>Schritt 4. Installieren von Apache
```
sudo yum install httpd
```
SELinux wird standardmäßig installiert, und klicken Sie im anwenden-Modus ausgeführt. Um Apache für die Verbindung mit Datenbanken über SELinux zu ermöglichen, führen Sie den folgenden Befehl aus:
```
sudo setsebool -P httpd_can_network_connect_db 1
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Schritt 5. Starten Sie Apache neu, und Testen Sie das Beispielskript
```
sudo apachectl restart
```
Um die Installation testen zu können, finden Sie unter [Testen Ihrer Installation](#testing-your-installation) am Ende dieses Dokuments.

## <a name="installing-the-drivers-on-debian-8-and-9"></a>Installieren die Treiber für Debian 8 und 9

> [!NOTE]
> Ersetzen Sie zum Installieren von PHP-7.1 oder 7.2, 7.3 in den folgenden Befehlen durch 7.1 oder 7.2 ein.

### <a name="step-1-install-php"></a>Schritt 1: Installieren von PHP
```
sudo su
apt-get install curl apt-transport-https
wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list
apt-get update
apt-get install -y php7.3 php7.3-dev php7.3-xml
```
### <a name="step-2-install-prerequisites"></a>Schritt 2: Installieren der erforderlichen Komponenten
Installieren Sie den ODBC-Treiber für Debian, mithilfe der Anweisungen auf der [Linux und MacOS-Installationsseite](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md). 

Sie müssen möglicherweise auch das richtige Gebietsschema zum Abrufen der PHP-Ausgabe korrekt in einem Browser angezeigt zu generieren. Führen Sie für das Gebietsschema "en_US" UTF-8, z. B. die folgenden Befehle aus:
```
sudo su
sed -i 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/g' /etc/locale.gen
locale-gen
```

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Schritt 3: Installieren Sie die PHP-Treiber für Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/30-pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/20-sqlsrv.ini
exit
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Schritt 4. Installieren von Apache, und konfigurieren Sie die Treiber laden
```
sudo su
apt-get install libapache2-mod-php7.3 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.3
echo "extension=pdo_sqlsrv.so" >> /etc/php/7.3/apache2/conf.d/30-pdo_sqlsrv.ini
echo "extension=sqlsrv.so" >> /etc/php/7.3/apache2/conf.d/20-sqlsrv.ini
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Schritt 5. Starten Sie Apache neu, und Testen Sie das Beispielskript
```
sudo service apache2 restart
```
Um die Installation testen zu können, finden Sie unter [Testen Ihrer Installation](#testing-your-installation) am Ende dieses Dokuments.

## <a name="installing-the-drivers-on-suse-12-and-15"></a>Installieren die Treiber unter Suse 12 und 15

> [!NOTE]
> Ersetzen Sie in den folgenden Anweisungen ist <SuseVersion> mit Ihrer Version von Suse: bei Verwendung von Suse Enterprise Linux 15, sie werden SLE_15 oder SLE_15_SP1, und klicken Sie auf ähnliche Weise für andere Versionen. Nicht alle Versionen von PHP stehen für alle Versionen von Suse Linux - `http://download.opensuse.org/repositories/devel:/languages:/php` ermitteln, welche Versionen von Suse die Standard-Version verfügbar ist, PHP oder `http://download.opensuse.org/repositories/devel:/languages:/php:/` welcher anderen PHP-Versionen sind verfügbar, für welche Versionen von Suse.

> [!NOTE]
> Pakete für die PHP-7.3 sind nicht verfügbar, für die Suse 12. Zum Installieren von PHP-7.1, ersetzen Sie die unten angegebene Repository-URL mit der folgenden URL: `https://download.opensuse.org/repositories/devel:/languages:/php:/php71/<SuseVersion>/devel:languages:php:php71.repo`.
> Zum Installieren von PHP 7.2, ersetzen Sie die unten angegebene Repository-URL mit der folgenden URL: `https://download.opensuse.org/repositories/devel:/languages:/php:/php72/<SuseVersion>/devel:languages:php:php72.repo`.

### <a name="step-1-install-php"></a>Schritt 1: Installieren von PHP
```
sudo su
zypper -n ar -f https://download.opensuse.org/repositories/devel:languages:php/<SuseVersion>/devel:languages:php.repo
zypper --gpg-auto-import-keys refresh
zypper -n install php7 php7-pear php7-devel php7-openssl
```
### <a name="step-2-install-prerequisites"></a>Schritt 2: Installieren der erforderlichen Komponenten
Installieren Sie den ODBC-Treiber für Suse gemäß die Anweisungen auf der [Linux und MacOS-Installationsseite](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Schritt 3: Installieren Sie die PHP-Treiber für Microsoft SQL Server
> [!NOTE]
> Wenn Sie eine Meldung von Fehler erhalten `Connection to 'pecl.php.net:443' failed: Unable to find the socket transport "ssl"`, das Skript Pecl /usr/bin/pecl bearbeiten und Entfernen der `-n` in der letzten Zeile wechseln. Diese Option wird verhindert, dass PECL Ini-Dateien laden, wenn PHP aufgerufen wird, die verhindert, dass die OpenSSL-Erweiterung laden.

```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/sqlsrv.ini
exit
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Schritt 4. Installieren von Apache, und konfigurieren Sie die Treiber laden
```
sudo su
zypper install apache2 apache2-mod_php7
a2enmod php7
echo "extension=sqlsrv.so" >> /etc/php7/apache2/php.ini
echo "extension=pdo_sqlsrv.so" >> /etc/php7/apache2/php.ini
exit
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Schritt 5. Starten Sie Apache neu, und Testen Sie das Beispielskript
```
sudo systemctl restart apache2
```
Um die Installation testen zu können, finden Sie unter [Testen Ihrer Installation](#testing-your-installation) am Ende dieses Dokuments.

## <a name="installing-the-drivers-on-macos-sierra-high-sierra-and-mojave"></a>Installieren die Treiber unter MacOS Sierra High Sierra und Mojave

Wenn Sie es noch nicht, installieren Sie Brew wie folgt:
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

> [!NOTE]
> Ersetzen Sie zum Installieren von PHP-7.1 oder 7.2, php@7.3 mit php@7.1 oder php@7.2 bzw. in den folgenden Befehlen.

### <a name="step-1-install-php"></a>Schritt 1: Installieren von PHP

```
brew tap
brew tap homebrew/core
brew install php@7.3
```
PHP muss nun in Ihrem Pfad – führen Sie `php -v` , stellen Sie sicher, dass Sie die richtige Version von PHP ausgeführt werden. Wenn PHP nicht in Ihrem Pfad befindet ist, oder es nicht die richtige Version ist, führen Sie die folgenden Schritte aus:
```
brew link --force --overwrite php@7.3
```

### <a name="step-2-install-prerequisites"></a>Schritt 2: Installieren der erforderlichen Komponenten
Installieren Sie den ODBC-Treiber für MacOS mithilfe der Anweisungen auf der [Linux und MacOS-Installationsseite](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md). 

Darüber hinaus müssen Sie die GNU stellen Tools zu installieren:
```
brew install autoconf automake libtool
```

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Schritt 3: Installieren Sie die PHP-Treiber für Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Schritt 4. Installieren von Apache, und konfigurieren Sie die Treiber laden
```
brew install apache2
```
Führen Sie zum Ermitteln der Apache-Konfigurationsdatei für die Apache-installation 
```
apachectl -V | grep SERVER_CONFIG_FILE
``` 
und Ersetzen Sie den Pfad für `httpd.conf` in den folgenden Befehlen:
```
echo "LoadModule php7_module /usr/local/opt/php@7.2/lib/httpd/modules/libphp7.so" >> /usr/local/etc/httpd/httpd.conf
(echo "<FilesMatch .php$>"; echo "SetHandler application/x-httpd-php"; echo "</FilesMatch>";) >> /usr/local/etc/httpd/httpd.conf
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Schritt 5. Starten Sie Apache neu, und Testen Sie das Beispielskript
```
sudo apachectl restart
```
Um die Installation testen zu können, finden Sie unter [Testen Ihrer Installation](#testing-your-installation) am Ende dieses Dokuments.

## <a name="testing-your-installation"></a>Testen der Installation

Um das folgende Skript zu testen, erstellen Sie in eine Datei namens testsql.php Dokumentstamm des Systems. Dies ist `/var/www/html/` unter Ubuntu, Debian und Redhat, `/srv/www/htdocs` unter SUSE oder `/usr/local/var/www` unter MacOS. Kopieren Sie das folgende Skript, ersetzen den Server, Datenbank, Benutzernamen und das Kennwort nach Bedarf.
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
Zeigen Sie im Browser https://localhost/testsql.php (https://localhost:8080/testsql.php unter MacOS). Sie sollten jetzt mit Ihrer SQL Server/Azure SQL-Datenbank herstellen können.

## <a name="see-also"></a>Weitere Informationen  
[Erste Schritte mit der Microsoft-Treiber für PHP für SQLServer](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Loading the Microsoft Drivers for PHP for SQL Server (Laden von Microsoft-Treibern für PHP für SQL Server)](../../connect/php/loading-the-php-sql-driver.md)

[Systemanforderungen für Microsoft-Treiber für PHP für SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md)
