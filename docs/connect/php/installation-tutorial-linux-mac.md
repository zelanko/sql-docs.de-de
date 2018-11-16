---
title: Linux und MacOS-Installation-Tutorial für Microsoft Drivers for PHP for SQL Server | Microsoft-Dokumentation
ms.date: 07/20/2018
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: ulvii
ms.author: v-ulibra
manager: v-mabarw
ms.openlocfilehash: af05ede442133465e7f268665bac4cd11a17f653
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51604600"
---
# <a name="linux-and-macos-installation-tutorial-for-the-microsoft-drivers-for-php-for-sql-server"></a>Linux und MacOS-Installation-Tutorial für Microsoft Drivers for PHP for SQL Server
Die folgenden Anweisungen wird davon ausgegangen eine saubere Umgebung und zeigen, wie Sie PHP 7.x, den Microsoft ODBC-Treiber, Apache und Microsoft Drivers for SQL Server unter Ubuntu 16.04, 17.10 und 18.04, Red Hat 7, Debian 8 und 9, Suse 12 und MacOS 10.11 für PHP installieren , 10.12 und 10.13. Diese Anweisungen empfehlen die Verwendung von PECL Treiber installieren, aber Sie können auch die vorab erstellte Binärdateien aus dem [Microsoft Drivers for PHP for SQL Server](https://github.com/Microsoft/msphpsql/releases) Github-Projektseite und installieren sie die Anweisungen im [ Laden die Microsoft-Treiber für PHP für SQLServer](../../connect/php/loading-the-php-sql-driver.md). Eine Erläuterung der Erweiterung laden, und warum wir nicht die Erweiterungen "PHP.ini" hinzugefügt werden, finden Sie im Abschnitt für [Laden der Treiber](../../connect/php/loading-the-php-sql-driver.md##loading-the-driver-at-php-startup).

Diese Anweisungen-Install-PHP 7.2 standardmäßig – finden Sie unter den Hinweisen am Anfang jeder Abschnitt zum Installieren von PHP 7.0 oder 7.1.

## <a name="contents-of-this-page"></a>Inhalt dieser Seite:

- [Installieren die Treiber auf Ubuntu 16.04, 17.10 und 18.04](#installing-the-drivers-on-ubuntu-1604-1710-and-1804)
- [Installation des Treibers auf Red Hat 7](#installing-the-drivers-on-red-hat-7)
- [Installieren die Treiber für Debian 8 und 9](#installing-the-drivers-on-debian-8-and-9)
- [Installieren die Treiber unter Suse 12](#installing-the-drivers-on-suse-12)
- [Installation des Treibers auf MacOS El Capitan "," Sierra "und" High Sierra](#installing-the-drivers-on-macos-el-capitan-sierra-and-high-sierra)

## <a name="installing-the-drivers-on-ubuntu-1604-1710-and-1804"></a>Installieren die Treiber auf Ubuntu 16.04 17.10 und 18.04

> [!NOTE]
> Ersetzen Sie zum Installieren von PHP 7.0 oder 7.1, 7.2, durch 7.0 oder 7.1 in den folgenden Befehlen.
> Für Ubuntu-18.04 ist so fügen Sie das Repository Ondrej nicht erforderlich, es sei denn, Sie PHP 7.0 oder 7.1 ist erforderlich. Allerdings Installieren von PHP 7.0 oder 7.1 in Ubuntu 18.04 funktioniert möglicherweise nicht wie stammen von Paketen aus dem Repository Ondrej mit Abhängigkeiten, die mit einer Basis, installieren Sie Ubuntu 18.04, Konflikt kann.

### <a name="step-1-install-php"></a>Schritt 1: Installieren von PHP
```
sudo su
add-apt-repository ppa:ondrej/php -y
apt-get update
apt-get install php7.2 php7.2-dev php7.2-xml -y --allow-unauthenticated
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
a2enmod php7.2
echo "extension=pdo_sqlsrv.so" >> /etc/php/7.2/apache2/conf.d/30-pdo_sqlsrv.ini
echo "extension=sqlsrv.so" >> /etc/php/7.2/apache2/conf.d/20-sqlsrv.ini
exit
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Schritt 5. Starten Sie Apache neu, und Testen Sie das Beispielskript
```
sudo service apache2 restart
```
Um die Installation testen zu können, finden Sie unter [Testen Ihrer Installation](#testing-your-installation) am Ende dieses Dokuments.

## <a name="installing-the-drivers-on-red-hat-7"></a>Installation des Treibers auf Red Hat 7

> [!NOTE]
> Ersetzen Sie zum Installieren von PHP 7.0 oder 7.1 Remi-php72 Remi-php70 oder Remi-php71 bzw. in den folgenden Befehlen.

### <a name="step-1-install-php"></a>Schritt 1: Installieren von PHP

```
sudo su
wget https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
wget https://rpms.remirepo.net/enterprise/remi-release-7.rpm
rpm -Uvh remi-release-7.rpm epel-release-latest-7.noarch.rpm
subscription-manager repos --enable=rhel-7-server-optional-rpms
yum-config-manager --enable remi-php72
yum update
yum install php php-pdo php-xml php-pear php-devel re2c gcc-c++ gcc
```
### <a name="step-2-install-prerequisites"></a>Schritt 2: Installieren der erforderlichen Komponenten
Installieren Sie den ODBC-Treiber für Red Hat 7 mithilfe der Anweisungen auf der [Linux und MacOS-Installationsseite](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

Kompilieren die PHP-Treiber mit PECL PHP 7.2 erfordert eine neuere GCC als den Standardwert:
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
tar xvzf sqlsrv-5.3.0.tgz
cd sqlsrv-5.3.0/
phpize
./configure --with-php-config=/usr/bin/php-config
make
sudo make install
```
Sie können alternativ die vorab erstellte Binärdateien aus dem [Projektseite auf Github](https://github.com/Microsoft/msphpsql/releases), oder installieren Sie aus dem Repository Remi:
```
sudo yum install php-sqlsrv php-pdo_sqlsrv
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
> Ersetzen Sie zum Installieren von PHP 7.0 oder 7.1, 7.2, in den folgenden Befehlen durch 7.0 oder 7.1 ein.

### <a name="step-1-install-php"></a>Schritt 1: Installieren von PHP
```
sudo su
apt-get install curl apt-transport-https
wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list
apt-get update
apt-get install -y php7.2 php7.2-dev php7.2-xml
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
apt-get install libapache2-mod-php7.2 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.2
echo "extension=pdo_sqlsrv.so" >> /etc/php/7.2/apache2/conf.d/30-pdo_sqlsrv.ini
echo "extension=sqlsrv.so" >> /etc/php/7.2/apache2/conf.d/20-sqlsrv.ini
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Schritt 5. Starten Sie Apache neu, und Testen Sie das Beispielskript
```
sudo service apache2 restart
```
Um die Installation testen zu können, finden Sie unter [Testen Ihrer Installation](#testing-your-installation) am Ende dieses Dokuments.

## <a name="installing-the-drivers-on-suse-12"></a>Installieren die Treiber unter Suse 12

> [!NOTE]
> Zum Installieren von PHP 7.0, ist das Überspringen Sie den folgenden Befehl Hinzufügen der Repository - 7.0 der PHP-Standard unter Suse 12.
> Zum Installieren von PHP-7.1, ersetzen Sie die unten angegebene Repository-URL mit der folgenden URL: `https://download.opensuse.org/repositories/devel:/languages:/php:/php71/SLE_12/devel:languages:php:php71.repo`

### <a name="step-1-install-php"></a>Schritt 1: Installieren von PHP
```
sudo su
zypper -n ar -f https://download.opensuse.org/repositories/devel:languages:php/SLE_12/devel:languages:php.repo
zypper --gpg-auto-import-keys refresh
zypper -n install php7 php7-pear php7-devel
```
### <a name="step-2-install-prerequisites"></a>Schritt 2: Installieren der erforderlichen Komponenten
Installieren Sie den ODBC-Treiber für Suse 12, mithilfe der Anweisungen auf der [Linux und MacOS-Installationsseite](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Schritt 3: Installieren Sie die PHP-Treiber für Microsoft SQL Server
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

## <a name="installing-the-drivers-on-macos-el-capitan-sierra-and-high-sierra"></a>Installation des Treibers auf MacOS El Capitan "," Sierra "und" High Sierra

Wenn Sie es noch nicht, installieren Sie Brew wie folgt:
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

> [!NOTE]
> Ersetzen Sie zum Installieren von PHP 7.0 oder 7.1 php@7.2 mit php@7.0 oder php@7.1 bzw. in den folgenden Befehlen.

### <a name="step-1-install-php"></a>Schritt 1: Installieren von PHP

```
brew tap
brew tap homebrew/core
brew install php@7.2
```
PHP muss nun in Ihrem Pfad – führen Sie `php -v` , stellen Sie sicher, dass Sie die richtige Version von PHP ausgeführt werden. Wenn PHP nicht in Ihrem Pfad befindet ist, oder es nicht die richtige Version ist, führen Sie die folgenden Schritte aus:
```
brew link --force --overwrite php@7.2
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

## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Erste Schritte mit der Microsoft-Treiber für PHP für SQLServer](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Loading the Microsoft Drivers for PHP for SQL Server (Laden von Microsoft-Treibern für PHP für SQL Server)](../../connect/php/loading-the-php-sql-driver.md)

[Systemanforderungen für Microsoft-Treiber für PHP für SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md)
