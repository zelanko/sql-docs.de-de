---
title: Tutorial zur Linux- und macOS-Installation für die Microsoft-Treiber für PHP für SQL Server | Microsoft-Dokumentation
ms.date: 05/09/2019
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: ulvii
ms.author: v-ulibra
manager: v-mabarw
ms.openlocfilehash: 2e1e6e6773644b12b6259349c522113ec66a0d43
ms.sourcegitcommit: e4794943ea6d2580174d42275185e58166984f8c
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65502768"
---
# <a name="linux-and-macos-installation-tutorial-for-the-microsoft-drivers-for-php-for-sql-server"></a>Tutorial zur Linux- und macOS-Installation für die Microsoft-Treiber für PHP für SQL Server
Die folgenden Anweisungen gehen von einer sauberen Umgebung aus und zeigen, wie PHP 7.x, der Microsoft ODBC-Treiber, Apache und die Microsoft-Treiber für PHP für SQL Server unter Ubuntu 16.04, 18.04 und 18.10, Red Hat 7, Debian 8 und 9, Suse 12 und 15 sowie macOS 10.12, 10.13 und 10.14 installiert werden. In dieser Anleitung wird empfohlen, die Treiber mit PECL zu installieren, aber Sie können die vorab erstellten Binärdateien auch von der GitHub-Projektseite [Microsoft Drivers for PHP for SQL Server](https://github.com/Microsoft/msphpsql/releases) (Microsoft-Treiber für PHP für SQL Server) herunterladen und gemäß den Anweisungen unter [Loading the Microsoft Drivers for PHP for SQL Server](../../connect/php/loading-the-php-sql-driver.md) (Laden der Microsoft-Treiber für PHP für SQL Server) installieren. Eine Beschreibung des Ladevorgangs von Erweiterungen und die Gründe, warum die Erweiterungen nicht zur php.ini-Datei hinzugefügt werden, finden Sie im Abschnitt zum [Laden der Treiber](../../connect/php/loading-the-php-sql-driver.md##loading-the-driver-at-php-startup).

Beim Ausführen dieser Anweisungen wird PHP 7.3 standardmäßig installiert. Beachten Sie, dass einige unterstützte Linux-Distributionen standardmäßig PHP 7.0 oder eine frühere Version verwenden, die für die PHP-Treiber für SQL Server nicht unterstützt werden. Achten Sie daher auf die Hinweise am Anfang jedes Abschnitts, um stattdessen PHP 7.1 oder 7.2 zu installieren.

## <a name="contents-of-this-page"></a>Inhalt dieser Seite:

- [Installieren der Treiber unter Ubuntu 16.04, 18.04 und 18.10](#installing-the-drivers-on-ubuntu-1604-1804-and-1810)
- [Installieren der Treiber unter Red Hat 7](#installing-the-drivers-on-red-hat-7)
- [Installieren der Treiber unter Debian 8 und 9](#installing-the-drivers-on-debian-8-and-9)
- [Installieren der Treiber unter Suse 12 und 15](#installing-the-drivers-on-suse-12-and-15)
- [Installieren der Treiber unter macOS Sierra, High Sierra und Mojave](#installing-the-drivers-on-macos-sierra-high-sierra-and-mojave)

## <a name="installing-the-drivers-on-ubuntu-1604-1804-and-1810"></a>Installieren der Treiber unter Ubuntu 16.04, 18.04 und 18.10

> [!NOTE]
> Ersetzen Sie zum Installieren von PHP 7.1 oder 7.2 in den folgenden Befehlen die Versionsnummer 7.3 durch 7.1 oder 7.2.

### <a name="step-1-install-php"></a>Schritt 1: Installieren von PHP
```
sudo su
add-apt-repository ppa:ondrej/php -y
apt-get update
apt-get install php7.3 php7.3-dev php7.3-xml -y --allow-unauthenticated
```
### <a name="step-2-install-prerequisites"></a>Schritt 2: Installieren der erforderlichen Komponenten
Installieren Sie den ODBC-Treiber für Ubuntu, indem Sie den Anweisungen auf der [Seite zur Installation von Linux und macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) folgen.

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Schritt 3: Installieren der PHP-Treiber für Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/30-pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/20-sqlsrv.ini
exit
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Schritt 4. Installieren von Apache und Konfigurieren des Treiberladevorgangs
```
sudo su
apt-get install libapache2-mod-php7.3 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.3
echo "extension=pdo_sqlsrv.so" >> /etc/php/7.3/apache2/conf.d/30-pdo_sqlsrv.ini
echo "extension=sqlsrv.so" >> /etc/php/7.3/apache2/conf.d/20-sqlsrv.ini
exit
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Schritt 5. Neustarten von Apache und Testen des Beispielskripts
```
sudo service apache2 restart
```
Hinweise zum [Testen der Installation](#testing-your-installation) finden Sie am Ende dieses Dokuments.

## <a name="installing-the-drivers-on-red-hat-7"></a>Installieren der Treiber unter Red Hat 7

> [!NOTE]
> Ersetzen Sie zum Installieren von PHP 7.1 oder 7.2 in den folgenden Befehlen „remi-php73“ durch „remi-php71“ bzw. „remi-php72“.

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
Installieren Sie den ODBC-Treiber für Red Hat 7, indem Sie den Anweisungen auf der [Seite zur Installation von Linux und macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) folgen.

Die Kompilierung der PHP-Treiber mit PECL mit PHP 7.2 oder 7.3 erfordert eine neuere GCC als die Standardversion:
```
sudo yum-config-manager --enable rhel-server-rhscl-7-rpms
sudo yum install devtoolset-7
scl enable devtoolset-7 bash
```
### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Schritt 3: Installieren der PHP-Treiber für Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/30-pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/20-sqlsrv.ini
exit
```
Ein Problem in PECL kann die korrekte Installation der neuesten Version der Treiber verhindern, selbst wenn Sie ein GCC-Upgrade ausgeführt haben. Zur Installation laden Sie die Pakete herunter und kompilieren sie manuell (ähnliche Schritte für pdo_sqlsrv):
```
pecl download sqlsrv
tar xvzf sqlsrv-5.6.1.tgz
cd sqlsrv-5.6.1/
phpize
./configure --with-php-config=/usr/bin/php-config
make
sudo make install
```
Alternativ können Sie die vorab erstellten Binärdateien von der [GitHub-Projektseite](https://github.com/Microsoft/msphpsql/releases) herunterladen oder aus dem Remi-Repository installieren:
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
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Schritt 5. Neustarten von Apache und Testen des Beispielskripts
```
sudo apachectl restart
```
Hinweise zum [Testen der Installation](#testing-your-installation) finden Sie am Ende dieses Dokuments.

## <a name="installing-the-drivers-on-debian-8-and-9"></a>Installieren der Treiber unter Debian 8 und 9

> [!NOTE]
> Ersetzen Sie zum Installieren von PHP 7.1 oder 7.2 in den folgenden Befehlen die Versionsnummer 7.3 durch 7.1 oder 7.2.

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
Installieren Sie den ODBC-Treiber für Debian, indem Sie den Anweisungen auf der [Seite zur Installation von Linux und macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) folgen. 

Möglicherweise müssen Sie auch das richtige Gebietsschema generieren, damit die PHP-Ausgabe in einem Browser korrekt angezeigt wird. Führen Sie zum Beispiel für das Gebietsschema „en_US UTF-8“ die folgenden Befehle aus:
```
sudo su
sed -i 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/g' /etc/locale.gen
locale-gen
```

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Schritt 3: Installieren der PHP-Treiber für Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/30-pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/20-sqlsrv.ini
exit
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Schritt 4. Installieren von Apache und Konfigurieren des Treiberladevorgangs
```
sudo su
apt-get install libapache2-mod-php7.3 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.3
echo "extension=pdo_sqlsrv.so" >> /etc/php/7.3/apache2/conf.d/30-pdo_sqlsrv.ini
echo "extension=sqlsrv.so" >> /etc/php/7.3/apache2/conf.d/20-sqlsrv.ini
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Schritt 5. Neustarten von Apache und Testen des Beispielskripts
```
sudo service apache2 restart
```
Hinweise zum [Testen der Installation](#testing-your-installation) finden Sie am Ende dieses Dokuments.

## <a name="installing-the-drivers-on-suse-12-and-15"></a>Installieren der Treiber unter Suse 12 und 15

> [!NOTE]
> Ersetzen Sie in den folgenden Anweisungen <SuseVersion> durch Ihre Version von Suse: Wenn Sie Suse Enterprise Linux 15 verwenden, lautet diese SLE_15 oder SLE_15_SP1 (gleichermaßen für andere Versionen). Nicht alle PHP-Versionen sind für alle Versionen von Suse Linux verfügbar. Unter `http://download.opensuse.org/repositories/devel:/languages:/php` erfahren Sie, welche Versionen von Suse über die Standardversion von PHP verfügen, und unter `http://download.opensuse.org/repositories/devel:/languages:/php:/`, welche anderen Versionen von PHP für welche Versionen von Suse verfügbar sind.

> [!NOTE]
> Pakete für PHP 7.3 sind für Suse 12 nicht verfügbar. Zur Installation von PHP 7.1 ersetzen Sie die unten gezeigte Repository-URL durch folgende URL: `https://download.opensuse.org/repositories/devel:/languages:/php:/php71/<SuseVersion>/devel:languages:php:php71.repo`.
> Zur Installation von PHP 7.2 ersetzen Sie die unten gezeigte Repository-URL durch folgende URL: `https://download.opensuse.org/repositories/devel:/languages:/php:/php72/<SuseVersion>/devel:languages:php:php72.repo`.

### <a name="step-1-install-php"></a>Schritt 1: Installieren von PHP
```
sudo su
zypper -n ar -f https://download.opensuse.org/repositories/devel:languages:php/<SuseVersion>/devel:languages:php.repo
zypper --gpg-auto-import-keys refresh
zypper -n install php7 php7-pear php7-devel php7-openssl
```
### <a name="step-2-install-prerequisites"></a>Schritt 2: Installieren der erforderlichen Komponenten
Installieren Sie den ODBC-Treiber für Suse, indem Sie den Anweisungen auf der [Seite zur Installation von Linux und macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) folgen.

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Schritt 3: Installieren der PHP-Treiber für Microsoft SQL Server
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
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Schritt 5. Neustarten von Apache und Testen des Beispielskripts
```
sudo systemctl restart apache2
```
Hinweise zum [Testen der Installation](#testing-your-installation) finden Sie am Ende dieses Dokuments.

## <a name="installing-the-drivers-on-macos-sierra-high-sierra-and-mojave"></a>Installieren der Treiber unter macOS Sierra, High Sierra und Mojave

Falls noch nicht vorhanden, installieren Sie Brew wie folgt:
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

> [!NOTE]
> Ersetzen Sie zum Installieren von PHP 7.1 oder 7.2 in den folgenden Befehlen php@7.3 durch php@7.1 oder php@7.2.

### <a name="step-1-install-php"></a>Schritt 1: Installieren von PHP

```
brew tap
brew tap homebrew/core
brew install php@7.3
```
PHP sollte jetzt in dem Pfad vorhanden sein. Führen Sie `php -v` aus, um zu überprüfen, ob Sie die richtige PHP-Version verwenden. Falls PHP nicht in dem Pfad zu finden ist oder nicht die richtige Version aufweist, führen Sie Folgendes aus:
```
brew link --force --overwrite php@7.3
```

### <a name="step-2-install-prerequisites"></a>Schritt 2: Installieren der erforderlichen Komponenten
Installieren Sie den ODBC-Treiber für macOS, indem Sie den Anweisungen auf der [Seite zur Installation von Linux und macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) folgen. 

Darüber hinaus kann es erforderlich sein, die GNU-Erstellungstools zu installieren:
```
brew install autoconf automake libtool
```

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Schritt 3: Installieren der PHP-Treiber für Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Schritt 4. Installieren von Apache und Konfigurieren des Treiberladevorgangs
```
brew install apache2
```
Führen Sie folgenden Befehl aus, um nach der Apache-Konfigurationsdatei für die Apache-Installation zu suchen: 
```
apachectl -V | grep SERVER_CONFIG_FILE
``` 
Ersetzen Sie dann den Pfad für `httpd.conf` in den folgenden Befehlen:
```
echo "LoadModule php7_module /usr/local/opt/php@7.3/lib/httpd/modules/libphp7.so" >> /usr/local/etc/httpd/httpd.conf
(echo "<FilesMatch .php$>"; echo "SetHandler application/x-httpd-php"; echo "</FilesMatch>";) >> /usr/local/etc/httpd/httpd.conf
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Schritt 5. Neustarten von Apache und Testen des Beispielskripts
```
sudo apachectl restart
```
Hinweise zum [Testen der Installation](#testing-your-installation) finden Sie am Ende dieses Dokuments.

## <a name="testing-your-installation"></a>Testen der Installation

Wenn Sie dieses Beispielskript testen möchten, erstellen Sie eine Datei namens „testsql.php“ im Dokumentenstamm Ihres Systems. Unter Ubuntu, Debian und Red Hat ist dies `/var/www/html/`, unter Suse `/srv/www/htdocs` und unter macOS `/usr/local/var/www`. Kopieren Sie folgendes Skript und fügen Sie es dort ein, indem Sie ggf. Server, Datenbank, Benutzername und Kennwort ersetzen.
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
