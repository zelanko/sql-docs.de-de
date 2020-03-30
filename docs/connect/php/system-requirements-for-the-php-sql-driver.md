---
title: Systemanforderungen für Microsoft-Treiber für PHP für SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/31/2020
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- requirements
ms.assetid: 5db4b75f-c605-4785-9560-399a533c0fc9
author: MightyPen
ms.reviewer: carlrab
ms.author: genemi
ms.openlocfilehash: f384e121d3b4ce0aa7ebcb380ebe5eaaa0ee3d45
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "76917823"
---
# <a name="system-requirements-for-the-microsoft-drivers-for-php-for-sql-server"></a>Systemanforderungen für Microsoft-Treiber für PHP für SQL Server

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

In diesem Artikel werden die Komponenten aufgeführt, die für den Zugriff auf Daten in einer SQL Server- oder Azure SQL-Datenbank-Instanz mithilfe der [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] auf Ihrem System installiert werden müssen.

Die Versionen 3.2 und höher der Microsoft-PHP-Treiber für SQL Server werden offiziell unterstützt. Ausführliche Informationen zu Supportlebenszyklen und Anforderungen der PHP-Treiber finden Sie in der [Unterstützungsmatrix](../../connect/php/microsoft-php-drivers-for-sql-server-support-matrix.md).

## <a name="php"></a>PHP

Weitere Informationen zum Herunterladen und Installieren von stabilen PHP-Binärdateien finden Sie [auf der PHP-Website](https://php.net).  Die Microsoft-PHP-Treiber für SQL Server erfordern die richtigen PHP-Versionen, wie in [Unterstützung von PHP-Versionen](../../connect/php/microsoft-php-drivers-for-sql-server-support-matrix.md#php-version-support) beschrieben.

-   Die richtige Version der Treiberdatei muss mit der entsprechenden PHP-Version aktiviert werden. Weiter unten finden Sie unter [Treiberversionen](#driver-versions) weitere Informationen zu den verschiedenen Treiberdateien.  Die Treiber können Sie unter [Download the Microsoft Drivers for PHP for SQL Server (Herunterladen der Microsoft-Treiber für PHP für SQL Server)](../../connect/php/download-drivers-php-sql-server.md) herunterladen. Unter [Loading the Microsoft Drivers for PHP for SQL Server (Laden der Microsoft-Treiber für PHP für SQL Server)](../../connect/php/loading-the-php-sql-driver.md) finden Sie weitere Informationen zur Konfiguration der Treiber für PHP.

-   Ein Webserver ist erforderlich. Ihr Webserver muss für die Ausführung von PHP konfiguriert sein. Weitere Informationen zum Hosting von PHP-Anwendungen mit IIS finden Sie im [Tutorial auf der PHP-Website](http://docs.php.net/manual/da/install.windows.iis7.php).

    [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] wurde auf IIS 10 mit FastCGI getestet.

    > [!NOTE]
    > Microsoft bietet lediglich für IIS Support.

## <a name="odbc-driver"></a>ODBC-Treiber

Die richtige Version des Microsoft ODBC Driver for SQL Server ist auf dem Computer erforderlich, auf dem PHP ausgeführt wird. Auf [dieser Seite](https://docs.microsoft.com/sql/connect/odbc/download-odbc-driver-for-sql-server?view=sql-server-2017) können Sie alle unterstützten Versionen des Treibers für unterstützte Plattformen herunterladen.

Wenn Sie die Windows-Version des Treibers auf eine 64-Bit-Version von Windows herunterladen, installiert das ODBC-64-Bit-Installationsprogramm sowohl 32-Bit- als auch 64-Bit-ODBC-Treiber. Wenn Sie eine 32-Bit-Version von Windows verwenden, verwenden Sie das ODBC-x86-Installationsprogramm. Auf Nicht-Windows-Plattformen sind nur 64-Bit-Versionen des Treibers verfügbar.

|Version des PHP für SQL Server-Treibers &#8594;<br />&#8595; Version des ODCB-Treibers|5.8|5.6|5.3|5,2|4.3|4,0|3.2|
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|ODBC-Treiber 17 und höher |J|J|J|J| | | |
|ODBC-Treiber 13.1|J|J|J|J|J|J| |
|ODBC-Treiber 13  | | | | | |J| |
|ODBC-Treiber 11  |J|J|J|J|J|J|J|

Falls Sie den SQLSRV-Treiber verwenden, teilt [sqlsrv_client_info](../../connect/php/sqlsrv-client-info.md) Ihnen mit, welche Version des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Microsoft ODBC Driver for SQL Server von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] verwendet wird. Fall Sie den PDO_SQLSRV-Treiber verwenden, können Sie die Version mithilfe von [PDO::getAttribute](../../connect/php/pdo-getattribute.md) abrufen.

## <a name="sql-server"></a>SQL Server

Weitere Informationen zur Verwendung von PHP mit Azure SQL-Datenbank finden Sie unter [Herstellen einer Verbindung mit einer Microsoft Azure SQL-Datenbank](../../connect/php/connecting-to-microsoft-azure-sql-database.md).

|Version des PHP für SQL Server-Treibers &#8594;<br />&#8595; SQL Server-Version|5.8|5.6|5.3|5,2|4.3|4,0|3.2|
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Azure SQL-Datenbank (alle Bereitstellungsoptionen)        |J|J|J|J| | | |
|Azure SQL-Synapse  |J|J|J|J| | | |
|SQL Server 2019           |J|J|J|J| | | |
|SQL Server 2017           |J|J|J|J| | | |
|SQL Server 2016           |J|J|J|J|J| | |
|SQL Server 2014           |J|J|J|J|J|J|J|
|SQL Server 2012           |J|J|J|J|J|J|J|
|SQL Server 2008 R2        | |J|J|J|J|J|J|
|SQL Server 2008           | | | | |J|J|J|

## <a name="operating-systems"></a>Betriebssysteme

Ausführliche Informationen dazu, welche Betriebssysteme unterstützt werden, finden Sie unter [Unterstützte Betriebssysteme](../../connect/php/microsoft-php-drivers-for-sql-server-support-matrix.md#supported-operating-systems).

## <a name="driver-versions"></a>Treiberversionen

Dieser Abschnitt listet die in den einzelnen Versionen von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] enthaltenen Treiber auf. Jedes Installationspaket enthält SQLSRV- und PDO_SQLSRV-Treiberdateien in Varianten mit und ohne Threads. Unter Windows sind auch 32-Bit- und 64-Bit-Varianten verfügbar. Um den Treiber für die Verwendung mit der PHP-Runtime zu konfigurieren, folgen Sie den Installationsanweisungen in [Laden von Microsoft Drivers for PHP for SQL Server](../../connect/php/loading-the-php-sql-driver.md).

Auf den unterstützten Versionen von Linux und macOS können die entsprechenden Treiber mithilfe des PECL-Paketsystems von PHP mit den [Linux- und macOS-Installationsanweisungen](../../connect/php/installation-tutorial-linux-mac.md) installiert werden. Alternativ können Sie vorgefertigte Binärdateien für Ihre Plattform von der GitHub-Projektseite [Microsoft Drivers for PHP for SQL Server](https://github.com/Microsoft/msphpsql/releases) (Microsoft-Treiber für PHP für SQL Server) herunterladen. In den folgenden Tabellen sind die in den vorgefertigten Binärpaketen enthaltenen Dateien aufgelistet.

**Microsoft-Treiber 5.8 für PHP für SQL Server:**

Unter Windows sind die folgenden Versionen des Treibers enthalten:

|Treiberdatei|PHP-Version|Threadsicher?|Zu verwendende PHP .dll|
|---------------|:---------------:|:----------------:|---------------------|
|32-Bit-Version von „php_sqlsrv_72_nts.dll“<br />32-Bit-php_pdo_sqlsrv_72_nts.dll|7.2|nein |32-Bit-Version von „php7.dll“|
|32-Bit-Version von „php_sqlsrv_72_ts.dll“ <br />32-bit php_pdo_sqlsrv_72_ts.dll |7.2|ja|32-Bit-Version von „php7ts.dll“|
|64-Bit-Version von „php_sqlsrv_72_nts.dll“<br />64-bit php_pdo_sqlsrv_72_nts.dll|7.2|nein |64-Bit-Version von „php7.dll“|
|64-Bit-Version von „php_sqlsrv_72_ts.dll“ <br />64-bit php_pdo_sqlsrv_72_ts.dll |7.2|ja|64-Bit-Version von „php7ts.dll“|
|32-Bit-Version von „php_sqlsrv_73_nts.dll“<br />32-bit php_pdo_sqlsrv_73_nts.dll|7.3|nein |32-Bit-Version von „php7.dll“|
|32-Bit-Version von „php_sqlsrv_73_ts.dll“ <br />32-bit php_pdo_sqlsrv_73_ts.dll |7.3|ja|32-Bit-Version von „php7ts.dll“|
|64-Bit-Version von „php_sqlsrv_73_nts.dll“<br />64-bit php_pdo_sqlsrv_73_nts.dll|7.3|nein |64-Bit-Version von „php7.dll“|
|64-Bit-Version von „php_sqlsrv_73_ts.dll“ <br />64-bit php_pdo_sqlsrv_73_ts.dll |7.3|ja|64-Bit-Version von „php7ts.dll“|
|32-Bit-Version von „php_sqlsrv_74_nts.dll“<br />32-Bit-Version von „php_pdo_sqlsrv_74_nts.dll“|7.4|nein |32-Bit-Version von „php7.dll“|
|32-Bit-Version von „php_sqlsrv_74_ts.dll“ <br />32-Bit-Version von „php_pdo_sqlsrv_74_ts.dll“ |7.4|ja|32-Bit-Version von „php7ts.dll“|
|64-Bit-Version von „php_sqlsrv_74_nts.dll“<br />64-Bit-Version von „php_pdo_sqlsrv_74_nts.dll“|7.4|nein |64-Bit-Version von „php7.dll“|
|64-Bit-Version von „php_sqlsrv_74_ts.dll“ <br />64-Bit-Version von „php_pdo_sqlsrv_74_ts.dll |7.4|ja|64-Bit-Version von „php7ts.dll“|

Unter Linux sind die folgenden Versionen des Treibers enthalten:

|Treiberdatei|PHP-Version|Threadsicher?|
|---------------|:---------------:|:----------------:|
|php_sqlsrv_72_nts.so<br />php_pdo_sqlsrv_72_nts.so|7.2|nein |
|php_sqlsrv_72_ts.so <br />php_pdo_sqlsrv_72_ts.so |7.2|ja|
|php_sqlsrv_73_nts.so<br />php_pdo_sqlsrv_73_nts.so|7.3|nein |
|php_sqlsrv_73_ts.so <br />php_pdo_sqlsrv_73_ts.so |7.3|ja|
|php_sqlsrv_74_nts.so<br />php_pdo_sqlsrv_74_nts.so|7.4|nein |
|php_sqlsrv_74_ts.so <br />php_pdo_sqlsrv_74_ts.so |7.4|ja|

**Microsoft-Treiber 5.6 für PHP für SQL Server:**

Unter Windows sind die folgenden Versionen des Treibers enthalten:

|Treiberdatei|PHP-Version|Threadsicher?|Zu verwendende PHP .dll|
|---------------|:---------------:|:----------------:|---------------------|
|32-Bit-Version von „php_sqlsrv_71_nts.dll“<br />32-Bit-Version von „php_pdo_sqlsrv_71_nts.dll“|7.1|nein |32-Bit-Version von „php7.dll“|
|32-Bit-Version von „php_sqlsrv_71_ts.dll“ <br />32-Bit-Version von „php_pdo_sqlsrv_71_ts.dll“ |7.1|ja|32-Bit-Version von „php7ts.dll“|
|64-Bit-Version von „php_sqlsrv_71_nts.dll“<br />64-Bit-Version von „php_pdo_sqlsrv_71_nts.dll“|7.1|nein |64-Bit-Version von „php7.dll“|
|64-Bit-Version von „php_sqlsrv_71_ts.dll“ <br />64-Bit-Version von „php_pdo_sqlsrv_71_ts.dll“ |7.1|ja|64-Bit-Version von „php7ts.dll“|
|32-Bit-Version von „php_sqlsrv_72_nts.dll“<br />32-Bit-php_pdo_sqlsrv_72_nts.dll|7.2|nein |32-Bit-Version von „php7.dll“|
|32-Bit-Version von „php_sqlsrv_72_ts.dll“ <br />32-bit php_pdo_sqlsrv_72_ts.dll |7.2|ja|32-Bit-Version von „php7ts.dll“|
|64-Bit-Version von „php_sqlsrv_72_nts.dll“<br />64-bit php_pdo_sqlsrv_72_nts.dll|7.2|nein |64-Bit-Version von „php7.dll“|
|64-Bit-Version von „php_sqlsrv_72_ts.dll“ <br />64-bit php_pdo_sqlsrv_72_ts.dll |7.2|ja|64-Bit-Version von „php7ts.dll“|
|32-Bit-Version von „php_sqlsrv_73_nts.dll“<br />32-bit php_pdo_sqlsrv_73_nts.dll|7.3|nein |32-Bit-Version von „php7.dll“|
|32-Bit-Version von „php_sqlsrv_73_ts.dll“ <br />32-bit php_pdo_sqlsrv_73_ts.dll |7.3|ja|32-Bit-Version von „php7ts.dll“|
|64-Bit-Version von „php_sqlsrv_73_nts.dll“<br />64-bit php_pdo_sqlsrv_73_nts.dll|7.3|nein |64-Bit-Version von „php7.dll“|
|64-Bit-Version von „php_sqlsrv_73_ts.dll“ <br />64-bit php_pdo_sqlsrv_73_ts.dll |7.3|ja|64-Bit-Version von „php7ts.dll“|

Unter Linux sind die folgenden Versionen des Treibers enthalten:

|Treiberdatei|PHP-Version|Threadsicher?|
|---------------|:---------------:|:----------------:|
|php_sqlsrv_71_nts.so<br />php_pdo_sqlsrv_71_nts.so|7.1|nein |
|php_sqlsrv_71_ts.so <br />php_pdo_sqlsrv_71_ts.so |7.1|ja|
|php_sqlsrv_72_nts.so<br />php_pdo_sqlsrv_72_nts.so|7.2|nein |
|php_sqlsrv_72_ts.so <br />php_pdo_sqlsrv_72_ts.so |7.2|ja|
|php_sqlsrv_73_nts.so<br />php_pdo_sqlsrv_73_nts.so|7.3|nein |
|php_sqlsrv_73_ts.so <br />php_pdo_sqlsrv_73_ts.so |7.3|ja|

**Microsoft-Treiber 5.3 für PHP für SQL Server:**

Unter Windows sind die folgenden Versionen des Treibers enthalten:

|Treiberdatei|PHP-Version|Threadsicher?|Zu verwendende PHP .dll|
|---------------|:---------------:|:----------------:|---------------------|
|32-Bit-Version von „php_sqlsrv_7_nts.dll“ <br />32-bit php_pdo_sqlsrv_7_nts.dll |7.0|nein |32-Bit-Version von „php7.dll“|
|32-Bit-Version von „php_sqlsrv_7_ts.dll“  <br />32-bit php_pdo_sqlsrv_7_ts.dll  |7.0|ja|32-Bit-Version von „php7ts.dll“|
|64-Bit-Version von „php_sqlsrv_7_nts.dll“ <br />64-bit php_pdo_sqlsrv_7_nts.dll |7.0|nein |64-Bit-Version von „php7.dll“|
|64-Bit-Version von „php_sqlsrv_7_ts.dll“  <br />64-bit php_pdo_sqlsrv_7_ts.dll  |7.0|ja|64-Bit-Version von „php7ts.dll“|
|32-Bit-Version von „php_sqlsrv_71_nts.dll“<br />32-Bit-Version von „php_pdo_sqlsrv_71_nts.dll“|7.1|nein |32-Bit-Version von „php7.dll“|
|32-Bit-Version von „php_sqlsrv_71_ts.dll“ <br />32-Bit-Version von „php_pdo_sqlsrv_71_ts.dll“ |7.1|ja|32-Bit-Version von „php7ts.dll“|
|64-Bit-Version von „php_sqlsrv_71_nts.dll“<br />64-Bit-Version von „php_pdo_sqlsrv_71_nts.dll“|7.1|nein |64-Bit-Version von „php7.dll“|
|64-Bit-Version von „php_sqlsrv_71_ts.dll“ <br />64-Bit-Version von „php_pdo_sqlsrv_71_ts.dll“ |7.1|ja|64-Bit-Version von „php7ts.dll“|
|32-Bit-Version von „php_sqlsrv_72_nts.dll“<br />32-Bit-php_pdo_sqlsrv_72_nts.dll|7.2|nein |32-Bit-Version von „php7.dll“|
|32-Bit-Version von „php_sqlsrv_72_ts.dll“ <br />32-bit php_pdo_sqlsrv_72_ts.dll |7.2|ja|32-Bit-Version von „php7ts.dll“|
|64-Bit-Version von „php_sqlsrv_72_nts.dll“<br />64-bit php_pdo_sqlsrv_72_nts.dll|7.2|nein |64-Bit-Version von „php7.dll“|
|64-Bit-Version von „php_sqlsrv_72_ts.dll“ <br />64-bit php_pdo_sqlsrv_72_ts.dll |7.2|ja|64-Bit-Version von „php7ts.dll“|

Unter Linux sind die folgenden Versionen des Treibers enthalten:

|Treiberdatei|PHP-Version|Threadsicher?|
|---------------|:---------------:|:----------------:|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|nein |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|ja|
|php_sqlsrv_71_nts.so<br />php_pdo_sqlsrv_71_nts.so|7.1|nein |
|php_sqlsrv_71_ts.so <br />php_pdo_sqlsrv_71_ts.so |7.1|ja|
|php_sqlsrv_72_nts.so<br />php_pdo_sqlsrv_72_nts.so|7.2|nein |
|php_sqlsrv_72_ts.so <br />php_pdo_sqlsrv_72_ts.so |7.2|ja|

**Microsoft-Treiber 5.2 für PHP für SQL Server:**

Unter Windows sind die folgenden Versionen des Treibers enthalten:

|Treiberdatei|PHP-Version|Threadsicher?|Zu verwendende PHP .dll|
|---------------|:---------------:|:----------------:|---------------------|
|32-Bit-Version von „php_sqlsrv_7_nts.dll“ <br />32-bit php_pdo_sqlsrv_7_nts.dll |7.0|nein |32-Bit-Version von „php7.dll“|
|32-Bit-Version von „php_sqlsrv_7_ts.dll“  <br />32-bit php_pdo_sqlsrv_7_ts.dll  |7.0|ja|32-Bit-Version von „php7ts.dll“|
|64-Bit-Version von „php_sqlsrv_7_nts.dll“ <br />64-bit php_pdo_sqlsrv_7_nts.dll |7.0|nein |64-Bit-Version von „php7.dll“|
|64-Bit-Version von „php_sqlsrv_7_ts.dll“  <br />64-bit php_pdo_sqlsrv_7_ts.dll  |7.0|ja|64-Bit-Version von „php7ts.dll“|
|32-Bit-Version von „php_sqlsrv_71_nts.dll“<br />32-Bit-Version von „php_pdo_sqlsrv_71_nts.dll“|7.1|nein |32-Bit-Version von „php7.dll“|
|32-Bit-Version von „php_sqlsrv_71_ts.dll“ <br />32-Bit-Version von „php_pdo_sqlsrv_71_ts.dll“ |7.1|ja|32-Bit-Version von „php7ts.dll“|
|64-Bit-Version von „php_sqlsrv_71_nts.dll“<br />64-Bit-Version von „php_pdo_sqlsrv_71_nts.dll“|7.1|nein |64-Bit-Version von „php7.dll“|
|64-Bit-Version von „php_sqlsrv_71_ts.dll“ <br />64-Bit-Version von „php_pdo_sqlsrv_71_ts.dll“ |7.1|ja|64-Bit-Version von „php7ts.dll“|
|32-Bit-Version von „php_sqlsrv_72_nts.dll“<br />32-Bit-php_pdo_sqlsrv_72_nts.dll|7.2|nein |32-Bit-Version von „php7.dll“|
|32-Bit-Version von „php_sqlsrv_72_ts.dll“ <br />32-bit php_pdo_sqlsrv_72_ts.dll |7.2|ja|32-Bit-Version von „php7ts.dll“|
|64-Bit-Version von „php_sqlsrv_72_nts.dll“<br />64-bit php_pdo_sqlsrv_72_nts.dll|7.2|nein |64-Bit-Version von „php7.dll“|
|64-Bit-Version von „php_sqlsrv_72_ts.dll“ <br />64-bit php_pdo_sqlsrv_72_ts.dll |7.2|ja|64-Bit-Version von „php7ts.dll“|

Unter Linux sind die folgenden Versionen des Treibers enthalten:

|Treiberdatei|PHP-Version|Threadsicher?|
|---------------|:---------------:|:----------------:|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|nein |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|ja|
|php_sqlsrv_71_nts.so<br />php_pdo_sqlsrv_71_nts.so|7.1|nein |
|php_sqlsrv_71_ts.so <br />php_pdo_sqlsrv_71_ts.so |7.1|ja|
|php_sqlsrv_72_nts.so<br />php_pdo_sqlsrv_72_nts.so|7.2|nein |
|php_sqlsrv_72_ts.so <br />php_pdo_sqlsrv_72_ts.so |7.2|ja|

**Microsoft-Treiber 4.3 für PHP für SQL Server:**

Unter Windows sind die folgenden Versionen des Treibers enthalten:

|Treiberdatei|PHP-Version|Threadsicher?|Zu verwendende PHP .dll|
|---------------|:---------------:|:----------------:|---------------------|
|32-Bit-Version von „php_sqlsrv_7_nts.dll“ <br />32-bit php_pdo_sqlsrv_7_nts.dll |7.0|nein |32-Bit-Version von „php7.dll“|
|32-Bit-Version von „php_sqlsrv_7_ts.dll“  <br />32-bit php_pdo_sqlsrv_7_ts.dll  |7.0|ja|32-Bit-Version von „php7ts.dll“|
|64-Bit-Version von „php_sqlsrv_7_nts.dll“ <br />64-bit php_pdo_sqlsrv_7_nts.dll |7.0|nein |64-Bit-Version von „php7.dll“|
|64-Bit-Version von „php_sqlsrv_7_ts.dll“  <br />64-bit php_pdo_sqlsrv_7_ts.dll  |7.0|ja|64-Bit-Version von „php7ts.dll“|
|32-Bit-Version von „php_sqlsrv_71_nts.dll“<br />32-Bit-Version von „php_pdo_sqlsrv_71_nts.dll“|7.1|nein |32-Bit-Version von „php7.dll“|
|32-Bit-Version von „php_sqlsrv_71_ts.dll“ <br />32-Bit-Version von „php_pdo_sqlsrv_71_ts.dll“ |7.1|ja|32-Bit-Version von „php7ts.dll“|
|64-Bit-Version von „php_sqlsrv_71_nts.dll“<br />64-Bit-Version von „php_pdo_sqlsrv_71_nts.dll“|7.1|nein |64-Bit-Version von „php7.dll“|
|64-Bit-Version von „php_sqlsrv_71_ts.dll“ <br />64-Bit-Version von „php_pdo_sqlsrv_71_ts.dll“ |7.1|ja|64-Bit-Version von „php7ts.dll“|

Unter Linux sind die folgenden Versionen des Treibers enthalten:

|Treiberdatei|PHP-Version|Threadsicher?|
|---------------|:---------------:|:----------------:|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|nein |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|ja|
|php_sqlsrv_71_nts.so<br />php_pdo_sqlsrv_71_nts.so|7.1|nein |
|php_sqlsrv_71_ts.so <br />php_pdo_sqlsrv_71_ts.so |7.1|ja|

**Microsoft-Treiber 4.0 für PHP für SQL Server:**

Unter Windows sind die folgenden Versionen des Treibers enthalten:

|Treiberdatei|PHP-Version|Threadsicher?|Zu verwendende PHP .dll|
|---------------|:---------------:|:----------------:|---------------------|
|php_sqlsrv_7_nts_x86.dll<br />php_pdo_sqlsrv_7_nts_x86.dll|7.0|nein|32-Bit-Version von „php7.dll“|
|php_sqlsrv_7_ts_x86.dll<br />php_pdo_sqlsrv_7_ts_x86.dll|7.0|ja|32-Bit-Version von „php7ts.dll“|
|php_sqlsrv_7_nts_x64.dll<br />php_pdo_sqlsrv_7_nts_x64.dll|7.0|nein|64-Bit-Version von „php7.dll“|
|php_sqlsrv_7_ts_x64.dll<br />php_pdo_sqlsrv_7_ts_x64.dll|7.0|ja|64-Bit-Version von „php7ts.dll“|

Unter Linux sind die folgenden Versionen des Treibers enthalten:

|Treiberdatei|PHP-Version|Threadsicher?|
|---------------|:---------------:|:----------------:|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|nein |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|ja|

**Microsoft-Treiber 3.2 für PHP für SQL Server:**

Unter Windows sind die folgenden Versionen des Treibers enthalten:

|Treiberdatei|PHP-Version|Threadsicher?|Zu verwendende PHP .dll|
|---------------|:---------------:|:----------------:|---------------------|
|php_sqlsrv_54_nts.dll<br />php_pdo_sqlsrv_54_nts.dll|5.4|nein|php5.dll|
|php_sqlsrv_54_ts.dll<br />php_pdo_sqlsrv_54_ts.dll|5.4|ja|php5ts.dll|
|php_sqlsrv_55_nts.dll<br />php_pdo_sqlsrv_55_nts.dll|5.5|nein|php5.dll|
|php_sqlsrv_55_ts.dll<br />php_pdo_sqlsrv_55_ts.dll|5.5|ja|php5ts.dll|
|php_sqlsrv_56_nts.dll<br />php_pdo_sqlsrv_56_nts.dll|5.6|nein|php5.dll|
|php_sqlsrv_56_ts.dll<br />php_pdo_sqlsrv_56_ts.dll|5.6|ja|php5ts.dll|

## <a name="see-also"></a>Weitere Informationen

- [Getting Started with the Microsoft Drivers for PHP for SQL Server (Erste Schritte mit dem Microsoft-Treiber für PHP für SQL Server)](../../connect/php/getting-started-with-the-php-sql-driver.md)
- [Programmierhandbuch für die Microsoft-Treiber für PHP für SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)
- [API-Referenz für den SQLSRV-Treiber](../../connect/php/sqlsrv-driver-api-reference.md)
- [API-Referenz für den PDO_SQLSRV-Treiber](../../connect/php/pdo-sqlsrv-driver-reference.md)
