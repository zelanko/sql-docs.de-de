---
title: Systemanforderungen für Microsoft-Treiber für PHP für SQL Server
ms.custom: ''
ms.date: 03/23/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- requirements
ms.assetid: 5db4b75f-c605-4785-9560-399a533c0fc9
caps.latest.revision: 93
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1941388b2bd7b0bb21e0da5a55876166c378c01e
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42787396"
---
# <a name="system-requirements-for-the-microsoft-drivers-for-php-for-sql-server"></a>Systemanforderungen für Microsoft-Treiber für PHP für SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Dieses Dokument Listet die Komponenten, die auf Ihrem System für den Datenzugriff in einer SQL Server oder Azure SQL-Datenbank mit installiert werden, müssen die [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].

-Versionen 3.1 und höher von Microsoft PHP Drivers for SQL Server werden offiziell unterstützt. Ausführliche Informationen zu Supportlebenszyklen und Anforderungen, einschließlich früherer Versionen von PHP-Treibern finden Sie unter den [Unterstützungsmatrix](../../connect/php/microsoft-php-drivers-for-sql-server-support-matrix.md).

## <a name="php"></a>PHP

Weitere Informationen zum Herunterladen und Installieren von stabilen PHP-Binärdateien finden Sie [auf der PHP-Website](http://php.net).  Microsoft Drivers for PHP for SQL Server erfordern die folgenden Versionen von PHP:

|PHP für SQL Server-Treiberversion&#8594;<br />&#8595; PHP-Version|5.3 und 5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|
|---|---|---|---|---|---|
|7.2|7.2.1 und höher unter Windows<br/>7.2.0+ auf anderen Plattformen | | | | |
|7.1|7.1.0+ |7.1.0+ |       |        |        |
|7.0|7.0.0+ |7.0.0+ |7.0.0+ |        |        |
|5.6|       |       |       |5.6.4 +  |        |
|5.5|       |       |       |5.5.16 + |5.5.16 + |
|5.4|       |       |       |5.4.32  |5.4.32  |

-   Eine Version der Treiberdatei muss sich in Ihrem PHP-Erweiterungsverzeichnis befinden. Finden Sie unter [Treiberversionen](#driver-versions) Informationen zu den verschiedenen Treiberdateien.  Die Treiber können Sie unter [Download the Microsoft Drivers for PHP for SQL Server (Herunterladen der Microsoft-Treiber für PHP für SQL Server)](download-drivers-php-sql-server.md) herunterladen. Unter [Loading the Microsoft Drivers for PHP for SQL Server (Laden der Microsoft-Treiber für PHP für SQL Server)](../../connect/php/loading-the-php-sql-driver.md) finden Sie weitere Informationen zur Konfiguration der Treiber für PHP.

-   Ein Webserver ist erforderlich. Ihr Webserver muss für die Ausführung von PHP konfiguriert sein. Informationen zum Hosten von PHP-Anwendungen mit IIS finden Sie unter den [Lernprogramm auf PHPs-Website](http://php.net/manual/fa/install.windows.iis.php).  

    [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] wurde auf IIS 10 mit FastCGI getestet.  

    > [!NOTE]  
    > Microsoft bietet lediglich für IIS Support.  

-   Version 5.3 von Microsoft Drivers for PHP for SQL Server werden die letzten, die PHP-7.0 unterstützt.

## <a name="odbc-driver"></a>ODBC-Treiber

Die richtige Version des Microsoft ODBC-Treibers für SQL Server muss auf dem Computer, auf dem PHP ausgeführt wird. Sie können alle unterstützte Versionen des Treibers für unterstützte Plattformen für [auf dieser Seite](https://docs.microsoft.com/en-us/sql/connect/odbc/download-odbc-driver-for-sql-server?view=sql-server-2017).

Wenn Sie die Windows-Version des Treibers auf einer 64-Bit-Version von Windows heruntergeladen haben, installiert der ODBC-64-Bit-Installer sowohl 32-Bit- und 64-Bit-ODBC-Treiber. Wenn Sie eine 32-Bit-Version von Windows verwenden, verwenden Sie die ODBC-X86 Installer. Auf nicht-Windows-Plattformen sind nur 64-Bit-Versionen des Treibers verfügbar.

|PHP für SQL Server-Treiberversion&#8594;<br />&#8595;ODBC-Treiberversion|5.3<br />&nbsp;|5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|
|---|---|---|---|---|---|---|
|ODBC-Treiber 17 und höher |J|J| | | | |
|ODBC-Treiber 13.1|J|J|J|J| | |
|ODBC-Treiber 13  | | | |J| | |
|ODBC-Treiber 11  |J|J|J|J|J|J|

Wenn Sie den SQLSRV-Treiber verwenden [Sqlsrv_client_info](../../connect/php/sqlsrv-client-info.md) sieht in Bezug auf die Version der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird von Microsoft ODBC-Treiber für SQL Server verwendet die [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]. Fall Sie den PDO_SQLSRV-Treiber verwenden, können Sie die Version mithilfe von [PDO::getAttribute](../../connect/php/pdo-getattribute.md) abrufen.  

## <a name="sql-server"></a>SQL Server

Azure SQL-Datenbanken werden unterstützt. Weitere Informationen finden Sie unter [Connecting to Microsoft Azure SQL Database (Herstellen einer Verbindung mit Microsoft Azure SQL-Datenbank)](../../connect/php/connecting-to-microsoft-azure-sql-database.md).

|PHP für SQL Server-Treiberversion&#8594;<br />&#8595; SQL Server-Version|5.3<br />&nbsp;|5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|
|---|---|---|---|---|---|---|
|Azure SQL-Datenbank        |J|J|J| | | |
|Verwaltete Azure SQL-Instanz|J|J|J| | | |
|Azure SQL Data Warehouse  |J|J|J| | | |
|SQL Server 2017           |J|J|J| | | |
|SQL Server 2016           |J|J|J|J| | |
|SQLServer 2014           |J|J|J|J|J|J|
|SQL Server 2012           |J|J|J|J|J|J|
|SQL Server 2008 R2        |J|J|J|J|J|J|
|SQL Server 2008           | | | |J|J|J|

## <a name="operating-systems"></a>Betriebssysteme
Unterstützte Betriebssysteme für die Versionen des Treibers lauten wie folgt aus:

|PHP für SQL Server-Treiberversion&#8594;<br />&#8595; Betriebssystem|5.3<br />&nbsp;|5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|
|---|---|---|---|---|---|---|
|Windows Server 2016                      |J|J|J| | | |
|Windows Server 2012 R2                   |J|J|J|J|J|J|
|Windows Server 2012                      |J|J|J|J|J|J|
|Windows Server 2008 R2 SP1               | | | |J|J|J|
|Windows Server 2008 SP2                  | | | |J|J|J|
|Windows 10                               |J|J|J|J| | |
|Windows 8.1                              |J|J|J|J|J|J|
|Windows 8                                | | |J|J|J|J|
|Windows 7 SP1                            | | | |J|J|J|
|Windows Vista SP2                        | | | |J|J|J|
|Ubuntu 18.04 (64-Bit)                    |J| | | | | |
|Ubuntu 17.10 (64-Bit)                    |J|J| | | | |
|Ubuntu 16.04 (64-Bit)                    |J|J|J|J| | |
|Ubuntu 15.10 (64-Bit)                    | | |J| | | |
|Ubuntu 15.04 (64-Bit)                    | | | |J| | |
|Debian 9 (64-Bit)                        |J|J| | | | |
|Debian 8 (64-Bit)                        |J|J|J| | | |
|Red Hat Enterprise Linux 7 (64-Bit)      |J|J|J|J| | |
|SuSE Enterprise Linux 12 (64-Bit)        |J|J| | | | |
|MacOS High Sierra (64-Bit)               |J| | | | | |
|MacOS Sierra (64-Bit)                    |J|J|J| | | |
|MacOS El Capitan (64-Bit)                |J|J|J| | | |

## <a name="driver-versions"></a>Treiberversionen  
Dieser Abschnitt enthält die Treiberdateien, die mit jeder Version von enthalten sind die [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]. Jedem Installationspaket enthält die SQLSRV- und PDO_SQLSRV-Treiber-Dateien in Threads und nicht-Thread-Varianten. Auf Windows sind sie auch in der 32-Bit und 64-Bit-Variante verfügbar. Führen Sie zum Konfigurieren der Treiber für die Verwendung mit der PHP-Laufzeit die installationsanweisungen im [Loading the Microsoft Drivers for PHP für SQL Server](../../connect/php/loading-the-php-sql-driver.md).

Auf unterstützten Versionen von Linux und MacOS, die richtigen Treiber installiert werden können mithilfe von PHP PECL-Paket-System nach dem [Installationshinweise für Linux und MacOS](../../connect/php/installation-tutorial-linux-mac.md). Alternativ können Sie vorab erstellte Binärdateien herunterladen, für Ihre Plattform aus der [Microsoft Drivers for PHP for SQL Server](https://github.com/Microsoft/msphpsql/releases) Projektseite auf Github – die folgenden Tabellen enthalten die vordefinierten Pakete für die binären Dateien.

**Microsoft-Treiber 5.3 für PHP für SQL Server:**  

Auf Windows dazu gehören die folgenden Versionen des Treibers:

|Treiberdatei|PHP-Version|Threadsicher?|Zu verwendende PHP .dll|  
|---------------|---------------|----------------|---------------------|  
|32-Bit-php_sqlsrv_7_nts.dll <br />32-Bit-php_pdo_sqlsrv_7_nts.dll |7.0|nein |32-Bit-php7.dll|
|32-Bit-php_sqlsrv_7_ts.dll  <br />32-Bit-php_pdo_sqlsrv_7_ts.dll  |7.0|ja|32-Bit-php7ts.dll|
|64-Bit-php_sqlsrv_7_nts.dll <br />64-Bit-php_pdo_sqlsrv_7_nts.dll |7.0|nein |64-Bit-php7.dll|  
|64-Bit-php_sqlsrv_7_ts.dll  <br />64-Bit-php_pdo_sqlsrv_7_ts.dll  |7.0|ja|64-Bit-php7ts.dll|
|32-Bit-php_sqlsrv_71_nts.dll<br />32-Bit-php_pdo_sqlsrv_71_nts.dll|7.1|nein |32-Bit-php7.dll|  
|32-Bit-php_sqlsrv_71_ts.dll <br />32-Bit-php_pdo_sqlsrv_71_ts.dll |7.1|ja|32-Bit-php7ts.dll|  
|64-Bit-php_sqlsrv_71_nts.dll<br />64-Bit-php_pdo_sqlsrv_71_nts.dll|7.1|nein |64-Bit-php7.dll|  
|64-Bit-php_sqlsrv_71_ts.dll <br />64-Bit-php_pdo_sqlsrv_71_ts.dll |7.1|ja|64-Bit-php7ts.dll|   
|32-Bit-php_sqlsrv_72_nts.dll<br />32-Bit-php_pdo_sqlsrv_72_nts.dll|7.2|nein |32-Bit-php7.dll|  
|32-Bit-php_sqlsrv_72_ts.dll <br />32-Bit-php_pdo_sqlsrv_72_ts.dll |7.2|ja|32-Bit-php7ts.dll|  
|64-Bit-php_sqlsrv_72_nts.dll<br />64-Bit-php_pdo_sqlsrv_72_nts.dll|7.2|nein |64-Bit-php7.dll|  
|64-Bit-php_sqlsrv_72_ts.dll <br />64-Bit-php_pdo_sqlsrv_72_ts.dll |7.2|ja|64-Bit-php7ts.dll|  

Unter Linux sind die folgenden Versionen des Treibers enthalten:

|Treiberdatei|PHP-Version|Threadsicher?|
|---------------|---------------|----------------|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|nein |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|ja|
|php_sqlsrv_71_nts.so<br />php_pdo_sqlsrv_71_nts.so|7.1|nein |
|php_sqlsrv_71_ts.so <br />php_pdo_sqlsrv_71_ts.so |7.1|ja|  
|php_sqlsrv_72_nts.so<br />php_pdo_sqlsrv_72_nts.so|7.2|nein |
|php_sqlsrv_72_ts.so <br />php_pdo_sqlsrv_72_ts.so |7.2|ja|

**Microsoft-Treiber 5.2 für PHP für SQL Server:**  

Auf Windows dazu gehören die folgenden Versionen des Treibers:

|Treiberdatei|PHP-Version|Threadsicher?|Zu verwendende PHP .dll|  
|---------------|---------------|----------------|---------------------|  
|32-Bit-php_sqlsrv_7_nts.dll <br />32-Bit-php_pdo_sqlsrv_7_nts.dll |7.0|nein |32-Bit-php7.dll|
|32-Bit-php_sqlsrv_7_ts.dll  <br />32-Bit-php_pdo_sqlsrv_7_ts.dll  |7.0|ja|32-Bit-php7ts.dll|
|64-Bit-php_sqlsrv_7_nts.dll <br />64-Bit-php_pdo_sqlsrv_7_nts.dll |7.0|nein |64-Bit-php7.dll|  
|64-Bit-php_sqlsrv_7_ts.dll  <br />64-Bit-php_pdo_sqlsrv_7_ts.dll  |7.0|ja|64-Bit-php7ts.dll|
|32-Bit-php_sqlsrv_71_nts.dll<br />32-Bit-php_pdo_sqlsrv_71_nts.dll|7.1|nein |32-Bit-php7.dll|  
|32-Bit-php_sqlsrv_71_ts.dll <br />32-Bit-php_pdo_sqlsrv_71_ts.dll |7.1|ja|32-Bit-php7ts.dll|  
|64-Bit-php_sqlsrv_71_nts.dll<br />64-Bit-php_pdo_sqlsrv_71_nts.dll|7.1|nein |64-Bit-php7.dll|  
|64-Bit-php_sqlsrv_71_ts.dll <br />64-Bit-php_pdo_sqlsrv_71_ts.dll |7.1|ja|64-Bit-php7ts.dll|   
|32-Bit-php_sqlsrv_72_nts.dll<br />32-Bit-php_pdo_sqlsrv_72_nts.dll|7.2|nein |32-Bit-php7.dll|  
|32-Bit-php_sqlsrv_72_ts.dll <br />32-Bit-php_pdo_sqlsrv_72_ts.dll |7.2|ja|32-Bit-php7ts.dll|  
|64-Bit-php_sqlsrv_72_nts.dll<br />64-Bit-php_pdo_sqlsrv_72_nts.dll|7.2|nein |64-Bit-php7.dll|  
|64-Bit-php_sqlsrv_72_ts.dll <br />64-Bit-php_pdo_sqlsrv_72_ts.dll |7.2|ja|64-Bit-php7ts.dll|  

Unter Linux sind die folgenden Versionen des Treibers enthalten:

|Treiberdatei|PHP-Version|Threadsicher?|
|---------------|---------------|----------------|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|nein |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|ja|
|php_sqlsrv_71_nts.so<br />php_pdo_sqlsrv_71_nts.so|7.1|nein |
|php_sqlsrv_71_ts.so <br />php_pdo_sqlsrv_71_ts.so |7.1|ja|  
|php_sqlsrv_72_nts.so<br />php_pdo_sqlsrv_72_nts.so|7.2|nein |
|php_sqlsrv_72_ts.so <br />php_pdo_sqlsrv_72_ts.so |7.2|ja|

**Microsoft-Treiber 4.3 für PHP für SQL Server:**  

Auf Windows dazu gehören die folgenden Versionen des Treibers:

|Treiberdatei|PHP-Version|Threadsicher?|Zu verwendende PHP .dll|  
|---------------|---------------|----------------|---------------------|  
|32-Bit-php_sqlsrv_7_nts.dll <br />32-Bit-php_pdo_sqlsrv_7_nts.dll |7.0|nein |32-Bit-php7.dll|
|32-Bit-php_sqlsrv_7_ts.dll  <br />32-Bit-php_pdo_sqlsrv_7_ts.dll  |7.0|ja|32-Bit-php7ts.dll|
|64-Bit-php_sqlsrv_7_nts.dll <br />64-Bit-php_pdo_sqlsrv_7_nts.dll |7.0|nein |64-Bit-php7.dll|  
|64-Bit-php_sqlsrv_7_ts.dll  <br />64-Bit-php_pdo_sqlsrv_7_ts.dll  |7.0|ja|64-Bit-php7ts.dll|
|32-Bit-php_sqlsrv_71_nts.dll<br />32-Bit-php_pdo_sqlsrv_71_nts.dll|7.1|nein |32-Bit-php7.dll|  
|32-Bit-php_sqlsrv_71_ts.dll <br />32-Bit-php_pdo_sqlsrv_71_ts.dll |7.1|ja|32-Bit-php7ts.dll|  
|64-Bit-php_sqlsrv_71_nts.dll<br />64-Bit-php_pdo_sqlsrv_71_nts.dll|7.1|nein |64-Bit-php7.dll|  
|64-Bit-php_sqlsrv_71_ts.dll <br />64-Bit-php_pdo_sqlsrv_71_ts.dll |7.1|ja|64-Bit-php7ts.dll|   

Unter Linux sind die folgenden Versionen des Treibers enthalten:

|Treiberdatei|PHP-Version|Threadsicher?|
|---------------|---------------|----------------|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|nein |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|ja|
|php_sqlsrv_71_nts.so<br />php_pdo_sqlsrv_71_nts.so|7.1|nein |
|php_sqlsrv_71_ts.so <br />php_pdo_sqlsrv_71_ts.so |7.1|ja|  

**Microsoft-Treiber 4.0 für PHP für SQL Server:**  

Auf Windows dazu gehören die folgenden Versionen des Treibers:

|Treiberdatei|PHP-Version|Threadsicher?|Zu verwendende PHP .dll|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_7_nts_x86.dll<br />php_pdo_sqlsrv_7_nts_x86.dll|7.0|nein|32-Bit-php7.dll|  
|php_sqlsrv_7_ts_x86.dll<br />php_pdo_sqlsrv_7_ts_x86.dll|7.0|ja|32-Bit-php7ts.dll|  
|php_sqlsrv_7_nts_x64.dll<br />php_pdo_sqlsrv_7_nts_x64.dll|7.0|nein|64-Bit-php7.dll|  
|php_sqlsrv_7_ts_x64.dll<br />php_pdo_sqlsrv_7_ts_x64.dll|7.0|ja|64-Bit-php7ts.dll|   

Unter Linux sind die folgenden Versionen des Treibers enthalten:

|Treiberdatei|PHP-Version|Threadsicher?|
|---------------|---------------|----------------|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|nein |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|ja|

**Microsoft-Treiber 3.2 für PHP für SQL Server:**  

Auf Windows dazu gehören die folgenden Versionen des Treibers:

|Treiberdatei|PHP-Version|Threadsicher?|Zu verwendende PHP .dll|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_54_nts.dll<br />php_pdo_sqlsrv_54_nts.dll|5.4|nein|php5.dll|  
|php_sqlsrv_54_ts.dll<br />php_pdo_sqlsrv_54_ts.dll|5.4|ja|php5ts.dll|  
|php_sqlsrv_55_nts.dll<br />php_pdo_sqlsrv_55_nts.dll|5.5|nein|php5.dll|  
|php_sqlsrv_55_ts.dll<br />php_pdo_sqlsrv_55_ts.dll|5.5|ja|php5ts.dll|  
|php_sqlsrv_56_nts.dll<br />php_pdo_sqlsrv_56_nts.dll|5.6|nein|php5.dll|  
|php_sqlsrv_56_ts.dll<br />php_pdo_sqlsrv_56_ts.dll|5.6|ja|php5ts.dll|  

**Microsoft-Treiber 3.1 für PHP für SQL Server:**  

Auf Windows dazu gehören die folgenden Versionen des Treibers:

|Treiberdatei|PHP-Version|Threadsicher?|Zu verwendende PHP .dll|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_54_nts.dll<br />php_pdo_sqlsrv_54_nts.dll|5.4|nein|php5.dll|  
|php_sqlsrv_54_ts.dll<br />php_pdo_sqlsrv_54_ts.dll|5.4|ja|php5ts.dll|  
|php_sqlsrv_55_nts.dll<br />php_pdo_sqlsrv_55_nts.dll|5.5|nein|php5.dll|  
|php_sqlsrv_55_ts.dll<br />php_pdo_sqlsrv_55_ts.dll|5.5|ja|php5ts.dll|  

## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Erste Schritte mit der Microsoft-Treiber für PHP für SQLServer](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Programmierhandbuch für den Microsoft-Treiber für PHP für SQLServer](../../connect/php/programming-guide-for-php-sql-driver.md)

[API-Referenz für den SQLSRV-Treiber](../../connect/php/sqlsrv-driver-api-reference.md)

[API-Referenz für den PDO_SQLSRV-Treiber](../../connect/php/pdo-sqlsrv-driver-reference.md)  
