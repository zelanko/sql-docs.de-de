---
title: Systemanforderungen für Microsoft-Treiber für PHP für SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- requirements
ms.assetid: 5db4b75f-c605-4785-9560-399a533c0fc9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b601d4fbb02b489aca228acb719cfe8bad834dc0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67992569"
---
# <a name="system-requirements-for-the-microsoft-drivers-for-php-for-sql-server"></a>Systemanforderungen für Microsoft-Treiber für PHP für SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Dieses Dokument enthält eine Liste der Komponenten, die auf Ihrem System installiert werden müssen, um mit [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]auf Daten in einem SQL Server oder einer Azure SQL-Datenbank zuzugreifen.

Die Versionen 3,1 und höher der Microsoft PHP-Treiber für SQL Server werden offiziell unterstützt. Ausführliche Informationen zu Support Lebenszyklen und Anforderungen, einschließlich früherer Versionen der PHP-Treiber, finden Sie in der [Support Matrix](../../connect/php/microsoft-php-drivers-for-sql-server-support-matrix.md).

## <a name="php"></a>PHP

Weitere Informationen zum Herunterladen und Installieren von stabilen PHP-Binärdateien finden Sie [auf der PHP-Website](https://php.net).  Die Microsoft-Treiber für PHP für SQL Server erfordern die folgenden Versionen von PHP:

|PHP für SQL Server Treiber Version&#8594;<br />&#8595; PHP-Version|5.6|5.3|5.2|4.3|4.0|3.2|3.1|
|:---:|---|---|---|---|---|---|---|
|7.3|7.3.0+ | | | | | | |
|7.2|7.2+<sup>1</sup>|7.2+<sup>1</sup>|7.2+<sup>1</sup>| | | | |
|7.1|7.1.0+ |7.1.0+ |7.1.0+ |7.1.0+ |       |        |        |
|7.0|       |7.0.0+ |7.0.0+ |7.0.0+ |7.0.0+ |        |        |
|5.6|       |       |       |       |       |5.6.4+  |        |
|5.5|       |       |       |       |       |5.5.16+ |5.5.16+ |
|5.4|       |       |       |       |       |5.4.32  |5.4.32  |

1. Versionen 7.2.1 und höher werden unter Windows unterstützt, während Versionen 7.2.0 und höher unter Linux und macOS unterstützt werden.

-   Eine Version der Treiberdatei muss sich in Ihrem PHP-Erweiterungsverzeichnis befinden. Informationen zu den verschiedenen Treiberdateien finden Sie unter [Treiberversionen](#driver-versions) .  Die Treiber können Sie unter [Download the Microsoft Drivers for PHP for SQL Server (Herunterladen der Microsoft-Treiber für PHP für SQL Server)](../../connect/php/download-drivers-php-sql-server.md) herunterladen. Unter [Loading the Microsoft Drivers for PHP for SQL Server (Laden der Microsoft-Treiber für PHP für SQL Server)](../../connect/php/loading-the-php-sql-driver.md) finden Sie weitere Informationen zur Konfiguration der Treiber für PHP.

-   Ein Webserver ist erforderlich. Ihr Webserver muss für die Ausführung von PHP konfiguriert sein. Weitere Informationen zum Hosting von PHP-Anwendungen mit IIS finden Sie im [Tutorial auf der PHP-Website](http://docs.php.net/manual/da/install.windows.iis7.php).

    [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] wurde auf IIS 10 mit FastCGI getestet.  

    > [!NOTE]  
    > Microsoft bietet lediglich für IIS Support.  

## <a name="odbc-driver"></a>ODBC-Treiber

Die richtige Version des Microsoft ODBC Driver for SQL Server ist auf dem Computer erforderlich, auf dem PHP ausgeführt wird. Auf [dieser Seite](https://docs.microsoft.com/sql/connect/odbc/download-odbc-driver-for-sql-server?view=sql-server-2017)können Sie alle unterstützten Versionen des Treibers für unterstützte Plattformen herunterladen.

Wenn Sie die Windows-Version des Treibers auf einer 64-Bit-Version von Windows herunterladen, installiert der ODBC 64-Bit-Installer sowohl 32-Bit-als auch 64-Bit-ODBC-Treiber. Wenn Sie eine 32-Bit-Version von Windows verwenden, verwenden Sie den ODBC x86-Installer. Auf nicht-Windows-Plattformen sind nur 64-Bit-Versionen des Treibers verfügbar.

|PHP für SQL Server Treiber Version&#8594;<br />&#8595; Version des ODCB-Treibers|5.6|5.3|5.2|4.3|4.0|3.2|3.1|
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|ODBC-Treiber 17 und höher |J|J|J| | | | |
|ODBC-Treiber 13.1|J|J|J|J|J| | |
|ODBC-Treiber 13  | | | | |J| | |
|ODBC-Treiber 11  |J|J|J|J|J|J|J|

Wenn Sie den sqlsrv-Treiber verwenden, gibt [sqlsrv_client_info](../../connect/php/sqlsrv-client-info.md) Informationen darüber zurück, welche [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version von Microsoft ODBC Driver for SQL Server von der [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]verwendet wird. Fall Sie den PDO_SQLSRV-Treiber verwenden, können Sie die Version mithilfe von [PDO::getAttribute](../../connect/php/pdo-getattribute.md) abrufen.  

## <a name="sql-server"></a>SQL Server

Azure SQL-Datenbanken werden unterstützt. Weitere Informationen finden Sie unter [Connecting to Microsoft Azure SQL Database (Herstellen einer Verbindung mit Microsoft Azure SQL-Datenbank)](../../connect/php/connecting-to-microsoft-azure-sql-database.md).

|PHP für SQL Server Treiber Version&#8594;<br />&#8595; SQL Server-Version|5.6|5.3|5.2|4.3|4.0|3.2|3.1|
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Azure SQL-Datenbank        |J|J|J|J| | | |
|Verwaltete Azure SQL-Instanz|J|J|J|J| | | |
|Azure SQL Data Warehouse  |J|J|J|J| | | |
|SQL Server 2017           |J|J|J|J| | | |
|SQL Server 2016           |J|J|J|J|J| | |
|SQLServer 2014           |J|J|J|J|J|J|J|
|SQL Server 2012           |J|J|J|J|J|J|J|
|SQL Server 2008 R2        |J|J|J|J|J|J|J|
|SQL Server 2008           | | | | |J|J|J|

## <a name="operating-systems"></a>Betriebssysteme
Folgende Betriebssysteme werden für jede Version des Treibers unterstützt:

|PHP für SQL Server Treiber Version&#8594;<br />&#8595; Betriebssystem|5.6|5.3|5.2|4.3|4.0|3.2|3.1|
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Windows Server 2016                 |J  |J  |J  |J  |   |   |   |
|Windows Server 2012 R2              |J  |J  |J  |J  |J  |J  |J  |
|Windows Server 2012                 |J  |J  |J  |J  |J  |J  |J  |
|Windows Server 2008 R2 SP1          |   |   |   |   |J  |J  |J  |
|Windows Server 2008 SP2             |   |   |   |   |J  |J  |J  |
|Windows 10                          |J  |J  |J  |J  |J  |   |   |
|Windows 8.1                         |J  |J  |J  |J  |J  |J  |J  |
|Windows 8                           |   |   |   |J  |J  |J  |J  |
|Windows 7 SP1                       |   |   |   |   |J  |J  |J  |
|Windows Vista SP2                   |   |   |   |   |J  |J  |J  |
|Ubuntu 18.10 (64 Bit)               |J  |   |   |   |   |   |   |
|Ubuntu 18.04 (64 Bit)               |J  |J  |   |   |   |   |   |
|Ubuntu 17.10 (64 Bit)               |   |J  |J  |   |   |   |   |
|Ubuntu 16.04 (64 Bit)               |J  |J  |J  |J  |J  |   |   |
|Ubuntu 15.10 (64 Bit)               |   |   |   |J  |   |   |   |
|Ubuntu 15.04 (64 Bit)               |   |   |   |   |J  |   |   |
|Debian 9 (64 Bit)                   |J  |J  |J  |   |   |   |   |
|Debian 8 (64 Bit)                   |J  |J  |J  |J  |   |   |   |
|Red Hat Enterprise Linux 7 (64-Bit) |J  |J  |J  |J  |J  |   |   |
|SuSE Enterprise Linux 15 (64 Bit)   |J  |   |   |   |   |   |   |
|SuSE Enterprise Linux 12 (64 Bit)   |J  |J  |J  |   |   |   |   |
|macOS (64 Bit)               |J  |   |   |   |   |   |   |
|macOS High Sierra (64 Bit)          |J  |J  |   |   |   |   |   |
|macOS Sierra (64 Bit)               |J  |J  |J  |J  |   |   |   |
|macOS El Capitan (64 Bit)           |   |J  |J  |J  |   |   |   |

## <a name="driver-versions"></a>Treiberversionen  
In diesem Abschnitt werden die Treiberdateien aufgelistet, die in den [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]einzelnen Versionen von enthalten sind. Jedes Installationspaket enthält sqlsrv-und PDO_SQLSRV-Treiberdateien in Thread-und nicht-Thread-Varianten. Unter Windows sind Sie auch in 32-Bit-und 64-Bit-Varianten verfügbar. Um den Treiber für die Verwendung mit der PHP-Laufzeit zu konfigurieren, befolgen Sie die Installationsanweisungen unter [Laden der Microsoft-Treiber für PHP für SQL Server](../../connect/php/loading-the-php-sql-driver.md).

Unter den unterstützten Versionen von Linux und MacOS können die entsprechenden Treiber mithilfe von PHP das PECL-Paketsystem installiert werden. Befolgen Sie [hierzu die Anweisungen zur Installation von Linux und MacOS](../../connect/php/installation-tutorial-linux-mac.md). Alternativ können Sie vorgefertigte Binärdateien für Ihre Plattform von der Seite [Microsoft Drivers for PHP for SQL Server](https://github.com/Microsoft/msphpsql/releases) GitHub Project herunterladen. in den folgenden Tabellen sind die Dateien aufgelistet, die in den vorgefertigten Binärpaketen enthalten sind.

**Microsoft-Treiber 5.6 für PHP für SQL Server:**  

Unter Windows sind die folgenden Versionen des Treibers enthalten:

|Treiberdatei|PHP-Version|Threadsicher?|Zu verwendende PHP .dll|  
|---------------|:---------------:|:----------------:|---------------------|  
|32-Bit php_sqlsrv_71_nts. dll<br />32-Bit-Version von „php_pdo_sqlsrv_71_nts.dll“|7.1|nein |32-Bit Php7. dll|  
|32-Bit php_sqlsrv_71_ts. dll <br />32-Bit-Version von „php_pdo_sqlsrv_71_ts.dll“ |7.1|ja|32-Bit php7ts. dll|  
|64-Bit php_sqlsrv_71_nts. dll<br />64-Bit-Version von „php_pdo_sqlsrv_71_nts.dll“|7.1|nein |64-Bit Php7. dll|  
|64-Bit php_sqlsrv_71_ts. dll <br />64-Bit-Version von „php_pdo_sqlsrv_71_ts.dll“ |7.1|ja|64-Bit php7ts. dll|   
|32-Bit php_sqlsrv_72_nts. dll<br />32-Bit-php_pdo_sqlsrv_72_nts.dll|7.2|nein |32-Bit Php7. dll|  
|32-Bit php_sqlsrv_72_ts. dll <br />32-bit php_pdo_sqlsrv_72_ts.dll |7.2|ja|32-Bit php7ts. dll|  
|64-Bit php_sqlsrv_72_nts. dll<br />64-bit php_pdo_sqlsrv_72_nts.dll|7.2|nein |64-Bit Php7. dll|  
|64-Bit php_sqlsrv_72_ts. dll <br />64-bit php_pdo_sqlsrv_72_ts.dll |7.2|ja|64-Bit php7ts. dll|  
|32-Bit php_sqlsrv_73_nts. dll<br />32-bit php_pdo_sqlsrv_73_nts.dll|7.3|nein |32-Bit Php7. dll|  
|32-Bit php_sqlsrv_73_ts. dll <br />32-bit php_pdo_sqlsrv_73_ts.dll |7.3|ja|32-Bit php7ts. dll|  
|64-Bit php_sqlsrv_73_nts. dll<br />64-bit php_pdo_sqlsrv_73_nts.dll|7.3|nein |64-Bit Php7. dll|  
|64-Bit php_sqlsrv_73_ts. dll <br />64-bit php_pdo_sqlsrv_73_ts.dll |7.3|ja|64-Bit php7ts. dll|  

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
|32-Bit php_sqlsrv_7_nts. dll <br />32-bit php_pdo_sqlsrv_7_nts.dll |7.0|nein |32-Bit Php7. dll|
|32-Bit php_sqlsrv_7_ts. dll  <br />32-bit php_pdo_sqlsrv_7_ts.dll  |7.0|ja|32-Bit php7ts. dll|
|64-Bit php_sqlsrv_7_nts. dll <br />64-bit php_pdo_sqlsrv_7_nts.dll |7.0|nein |64-Bit Php7. dll|  
|64-Bit php_sqlsrv_7_ts. dll  <br />64-bit php_pdo_sqlsrv_7_ts.dll  |7.0|ja|64-Bit php7ts. dll|
|32-Bit php_sqlsrv_71_nts. dll<br />32-Bit-Version von „php_pdo_sqlsrv_71_nts.dll“|7.1|nein |32-Bit Php7. dll|  
|32-Bit php_sqlsrv_71_ts. dll <br />32-Bit-Version von „php_pdo_sqlsrv_71_ts.dll“ |7.1|ja|32-Bit php7ts. dll|  
|64-Bit php_sqlsrv_71_nts. dll<br />64-Bit-Version von „php_pdo_sqlsrv_71_nts.dll“|7.1|nein |64-Bit Php7. dll|  
|64-Bit php_sqlsrv_71_ts. dll <br />64-Bit-Version von „php_pdo_sqlsrv_71_ts.dll“ |7.1|ja|64-Bit php7ts. dll|   
|32-Bit php_sqlsrv_72_nts. dll<br />32-Bit-php_pdo_sqlsrv_72_nts.dll|7.2|nein |32-Bit Php7. dll|  
|32-Bit php_sqlsrv_72_ts. dll <br />32-bit php_pdo_sqlsrv_72_ts.dll |7.2|ja|32-Bit php7ts. dll|  
|64-Bit php_sqlsrv_72_nts. dll<br />64-bit php_pdo_sqlsrv_72_nts.dll|7.2|nein |64-Bit Php7. dll|  
|64-Bit php_sqlsrv_72_ts. dll <br />64-bit php_pdo_sqlsrv_72_ts.dll |7.2|ja|64-Bit php7ts. dll|  

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
|32-Bit php_sqlsrv_7_nts. dll <br />32-bit php_pdo_sqlsrv_7_nts.dll |7.0|nein |32-Bit Php7. dll|
|32-Bit php_sqlsrv_7_ts. dll  <br />32-bit php_pdo_sqlsrv_7_ts.dll  |7.0|ja|32-Bit php7ts. dll|
|64-Bit php_sqlsrv_7_nts. dll <br />64-bit php_pdo_sqlsrv_7_nts.dll |7.0|nein |64-Bit Php7. dll|  
|64-Bit php_sqlsrv_7_ts. dll  <br />64-bit php_pdo_sqlsrv_7_ts.dll  |7.0|ja|64-Bit php7ts. dll|
|32-Bit php_sqlsrv_71_nts. dll<br />32-Bit-Version von „php_pdo_sqlsrv_71_nts.dll“|7.1|nein |32-Bit Php7. dll|  
|32-Bit php_sqlsrv_71_ts. dll <br />32-Bit-Version von „php_pdo_sqlsrv_71_ts.dll“ |7.1|ja|32-Bit php7ts. dll|  
|64-Bit php_sqlsrv_71_nts. dll<br />64-Bit-Version von „php_pdo_sqlsrv_71_nts.dll“|7.1|nein |64-Bit Php7. dll|  
|64-Bit php_sqlsrv_71_ts. dll <br />64-Bit-Version von „php_pdo_sqlsrv_71_ts.dll“ |7.1|ja|64-Bit php7ts. dll|   
|32-Bit php_sqlsrv_72_nts. dll<br />32-Bit-php_pdo_sqlsrv_72_nts.dll|7.2|nein |32-Bit Php7. dll|  
|32-Bit php_sqlsrv_72_ts. dll <br />32-bit php_pdo_sqlsrv_72_ts.dll |7.2|ja|32-Bit php7ts. dll|  
|64-Bit php_sqlsrv_72_nts. dll<br />64-bit php_pdo_sqlsrv_72_nts.dll|7.2|nein |64-Bit Php7. dll|  
|64-Bit php_sqlsrv_72_ts. dll <br />64-bit php_pdo_sqlsrv_72_ts.dll |7.2|ja|64-Bit php7ts. dll|  

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
|32-Bit php_sqlsrv_7_nts. dll <br />32-bit php_pdo_sqlsrv_7_nts.dll |7.0|nein |32-Bit Php7. dll|
|32-Bit php_sqlsrv_7_ts. dll  <br />32-bit php_pdo_sqlsrv_7_ts.dll  |7.0|ja|32-Bit php7ts. dll|
|64-Bit php_sqlsrv_7_nts. dll <br />64-bit php_pdo_sqlsrv_7_nts.dll |7.0|nein |64-Bit Php7. dll|  
|64-Bit php_sqlsrv_7_ts. dll  <br />64-bit php_pdo_sqlsrv_7_ts.dll  |7.0|ja|64-Bit php7ts. dll|
|32-Bit php_sqlsrv_71_nts. dll<br />32-Bit-Version von „php_pdo_sqlsrv_71_nts.dll“|7.1|nein |32-Bit Php7. dll|  
|32-Bit php_sqlsrv_71_ts. dll <br />32-Bit-Version von „php_pdo_sqlsrv_71_ts.dll“ |7.1|ja|32-Bit php7ts. dll|  
|64-Bit php_sqlsrv_71_nts. dll<br />64-Bit-Version von „php_pdo_sqlsrv_71_nts.dll“|7.1|nein |64-Bit Php7. dll|  
|64-Bit php_sqlsrv_71_ts. dll <br />64-Bit-Version von „php_pdo_sqlsrv_71_ts.dll“ |7.1|ja|64-Bit php7ts. dll|   

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
|php_sqlsrv_7_nts_x86.dll<br />php_pdo_sqlsrv_7_nts_x86.dll|7.0|nein|32-Bit Php7. dll|  
|php_sqlsrv_7_ts_x86.dll<br />php_pdo_sqlsrv_7_ts_x86.dll|7.0|ja|32-Bit php7ts. dll|  
|php_sqlsrv_7_nts_x64.dll<br />php_pdo_sqlsrv_7_nts_x64.dll|7.0|nein|64-Bit Php7. dll|  
|php_sqlsrv_7_ts_x64.dll<br />php_pdo_sqlsrv_7_ts_x64.dll|7.0|ja|64-Bit php7ts. dll|   

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

**Microsoft-Treiber 3.1 für PHP für SQL Server:**  

Unter Windows sind die folgenden Versionen des Treibers enthalten:

|Treiberdatei|PHP-Version|Threadsicher?|Zu verwendende PHP .dll|  
|---------------|:---------------:|:----------------:|---------------------|  
|php_sqlsrv_54_nts.dll<br />php_pdo_sqlsrv_54_nts.dll|5.4|nein|php5.dll|  
|php_sqlsrv_54_ts.dll<br />php_pdo_sqlsrv_54_ts.dll|5.4|ja|php5ts.dll|  
|php_sqlsrv_55_nts.dll<br />php_pdo_sqlsrv_55_nts.dll|5.5|nein|php5.dll|  
|php_sqlsrv_55_ts.dll<br />php_pdo_sqlsrv_55_ts.dll|5.5|ja|php5ts.dll|  

## <a name="see-also"></a>Weitere Informationen  
[Getting Started with the Microsoft Drivers for PHP for SQL Server (Erste Schritte mit dem Microsoft-Treiber für PHP für SQL Server)](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Programmierhandbuch für die Microsoft-Treiber für PHP für SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[API-Referenz für den SQLSRV-Treiber](../../connect/php/sqlsrv-driver-api-reference.md)

[API-Referenz für den PDO_SQLSRV-Treiber](../../connect/php/pdo-sqlsrv-driver-reference.md)  
