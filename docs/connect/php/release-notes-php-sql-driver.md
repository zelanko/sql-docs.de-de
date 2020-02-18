---
title: Anmerkungen zu dieser Version für die Microsoft-Treiber für PHP für SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/31/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: v-dapugl, kenvh
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- what's new in version 1.1
ms.assetid: 91cca3d2-ba99-4a6d-b0de-beb9699cb3f8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5e279ba446e790a2262e5f0effe160632065dcba
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "76941210"
---
# <a name="release-notes-for-the-microsoft-drivers-for-php-for-sql-server"></a>Versionshinweise für die Microsoft-Treiber für PHP für SQL Server

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Auf dieser Seite wird erläutert, welche Funktionen in den verschiedenen Versionen der [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] hinzugefügt wurden.  

<!--
Hello, We are standardizing the format of content inside our Release Notes (or What's New) articles.
Instead of bullets (or paragraphs), we have shifted to the 2-column format you see for H2 **What's New in Version 5.6**.
It is not necessary to reformat all the older H2 sections in this Release Notes file, but.....

Going forward, please be sure to use the 2-column format.

Also, all Release Notes .md file names now must begin with 'release-notes-*.md'.  And no filler words.
The 5.6 edition of this file is being renamed.....
FROM:  'release-notes-for-the-php-sql-driver.md'
TO  :  'release-notes-php-sql-driver.md'

For any questions, ask GeneMi or CraigG.
Thanks a lot.  2019-03-28  (DevO= 1467988)
-->

## <a name="whats-new-in-version-58"></a>Neuerungen in Version 5.8

| Neues Element | Details |
| :------- | :------ |
| Unterstützung für PHP 7.4 hinzugefügt. | &nbsp; |
| Unterstützung für PHP 7.1 eingestellt. | &nbsp; |
| Unterstützung für Microsoft ODBC-Treiber 17.5 auf allen Plattformen hinzugefügt. | &nbsp; |
| Unterstützung für Debian 10 und Red Hat 8 hinzugefügt. | Für beide Systeme ist der ODBC-Treiber 17.4 oder höher erforderlich. |
| Unterstützung für macOS Catalina, Alpine Linux 3.11<sup>1</sup> und Ubuntu 19.10 hinzugefügt. | Für alle Systeme ist der ODBC-Treiber 17.5 oder höher erforderlich. |
| Unterstützung für SQL Server 2008 R2, macOS Sierra, Ubuntu 18.10 und Ubuntu 19.04 wurde eingestellt. | &nbsp; |
| Unterstützung für die Sprachoption bei Verbindung mit SQL Server. | &nbsp; |
| Unterstützung für erweiterte PHP-Zeichenfolgentypen, die in PHP 7.2 eingeführt wurden. | &nbsp; |
| Unterstützung für den Abruf von Sensitivitätsmetadaten der Datenklassifizierung. | Für diese Funktion ist SQL Server 2019 und der ODBC-Treiber 17.4.2 oder höher erforderlich. |
| Unterstützung für Always Encrypted mit Secure Enclaves | Für diese Funktion ist der ODBC-Treiber 17.4 oder höher erforderlich. |
| Unterstützung von konfigurierbaren Optionen für Gebietsschemaeinstellungen in Linux und macOS. |
| Verbesserte Leistung durch das Zwischenspeichern von Metadaten beim Abruf und den Wegfall redundanter Aufrufe. | &nbsp; |
| &nbsp; | &nbsp; |

<sup>1</sup> Experimentelle Unterstützung von Alpine Linux in Version 5.8.

## <a name="whats-new-in-version-56"></a>Neues in Version 5.6

| Neues Element | Details |
| :------- | :------ |
| Unterstützung für PHP 7.3. | &nbsp; |
| Unterstützung für PHP 7.0 eingestellt. | &nbsp; |
| Unterstützung für Microsoft ODBC-Treiber 17.3 auf allen Plattformen. | &nbsp; |
| Unterstützung für macOS Mojave. | Für diese Funktion ist der ODBC-Treiber 17.3 oder höher erforderlich. |
| Unterstützung für Ubuntu 18.10 und Suse Linux 15. | Für beide Systeme ist der ODBC-Treiber 17.3 oder höher erforderlich. |
| Die Unterstützung für Linux Ubuntu 17.10 und macOS El Capitan wurde eingestellt. | &nbsp; |
| Unterstützung für Azure AD-Zugriffstoken. | Unter Linux und macOS ist der ODBC-Treiber 17.2 oder höher sowie unixODBC 2.3.6 oder höher erforderlich. |
| Unterstützung für die Authentifizierung mit Azure AD unter Verwendung verwalteter Identitäten für Azure-Ressourcen. | Für diese Funktion ist der ODBC-Treiber 17.3 oder höher erforderlich. |
| Neue Abruffunktionen | &bull; &nbsp; Neues Kennzeichen PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE, damit pdo_sqlsrv datetime als Objekt zurückgibt.<br/><br/>&bull; &nbsp; Neue ReturnDatesAsStrings-Option auf Anweisungsebene für sqlsrv.<br/><br/>&bull; &nbsp; Neue Optionen auf Verbindungs- und Anweisungsebene für beide Treiber, um Dezimalwerte in den abgerufenen Ergebnissen zu formatieren. |
| Unterstützung für die statische Kompilierung von Treibern, wenn Benutzer die Erstellung aus der Quelle auswählen. | &nbsp; |
| Verbesserte Leistung durch das Zwischenspeichern von Metadaten beim Abruf und eine schnellere Konvertierung von Unicode-Zeichenfolgen. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="whats-new-in-version-53"></a>Neues in Version 5.3

- Unterstützung für Microsoft ODBC-Treiber 17.2 auf allen Plattformen
- Unterstützung für macOS High Sierra (erfordert ODBC-Treiber 17 und höher)
- Unterstützung von Azure Key Vault für Always Encrypted für grundlegende CRUD-Funktionalität, sodass die Always Encrypted-Funktion für alle unterstützten Windows-, Linux- oder macOS-Plattformen verfügbar ist. [Verwenden von Always Encrypted mit den PHP-Treibern für SQL Server](../../connect/php/using-always-encrypted-php-drivers.md)
- Unterstützung für Ubuntu 18.04 LTS (ODBC-Treiber 17.2 erforderlich)
- Unterstützung für Verbindungsresilienz unter Linux oder macOS (ODBC-Treiber 17.2 erforderlich)

## <a name="whats-new-in-version-52"></a>Neues in Version 5.2

- Unterstützung für PHP 7.2.1 und höher unter Windows sowie Version 7.2.0 und höher auf allen anderen Plattformen
- Unterstützung für Microsoft ODBC-Treiber 17
  - Version 17 ist nun der Standard auf allen Plattformen
- Unterstützung für Ubuntu 17.10, Debian 9 und Suse Enterprise Linux 12
- Unterstützung für Ubuntu 15.10 eingestellt
- Unterstützung für Always Encrypted mit CRUD-Funktionalität unter Windows. Weitere Informationen finden Sie unter [Verwenden von Always Encrypted mit den PHP-Treibern für SQL Server](../../connect/php/using-always-encrypted-php-drivers.md).
  - Unterstützung für den Windows-Zertifikatspeicher
  - Always Encrypted wird nur mit Microsoft ODBC-Treiber 17 und höher unterstützt
- Unterstützung für Nicht-UTF-8-Gebietsschemas unter Linux und macOS
  - Nicht-UTF-8-Gebietsschemas werden unter Linux und macOS nur mit Microsoft ODBC-Treiber 17 und höher unterstützt
- Unterstützung für Azure SQL Data Warehouse
- Unterstützung für verwaltete Azure SQL-Datenbank-Instanzen

## <a name="whats-new-in-version-43"></a>Neues in Version 4.3

- Unterstützung für PHP 7.1
- Unterstützung für macOS Sierra und macOS El Capitan
- Unterstützung für Ubuntu 15.10 und Debian 8
- Unterstützung für Ubuntu 15.04 eingestellt
- Unterstützung für Always On-Verfügbarkeitsgruppen über die transparente Netzwerk-IP-Adressauflösung. Weitere Informationen finden Sie unter [Connection Options](../../connect/php/connection-options.md).
- Eingeschränkte Unterstützung für den sql_variant-Datentyp hinzugefügt.
- Unterstützung für Resilienz von Verbindungen im Leerlauf unter Windows. Weitere Informationen finden Sie unter [Connection Options](../../connect/php/connection-options.md).
- Unterstützung für Verbindungspooling unter Linux und macOS. Weitere Informationen finden Sie unter [Verbindungspooling](../../connect/php/connection-pooling-microsoft-drivers-for-php-for-sql-server.md).
- Unterstützung für Azure Active Directory-Authentifizierung mit ActiveDirectoryPassword und SqlPassword. Weitere Informationen finden Sie unter [Connection Options](../../connect/php/connection-options.md).

## <a name="whats-new-in-version-40"></a>Neues in Version 4.0

- Unterstützung für PHP 7.0  
- Vollständige 64-Bit-Unterstützung
- Unterstützung für Ubuntu 15.04, Ubuntu 16.04 und RedHat 7

## <a name="whats-new-in-version-32"></a>Neuerungen in Version 3.2

- Unterstützung für PHP 5.6   
- Enthält die neuesten Updates für vorherige PHP-Versionen 5.5 und 5.4   
- Erfordert Microsoft ODBC Driver 11 for SQL Server  

## <a name="whats-new-in-version-31"></a>Neuerungen in Version 3.1

- Unterstützung für PHP 5.5  
- Erfordert Microsoft ODBC Driver 11 for SQL Server Frühere Versionen benötigten SQL Native Client.  

## <a name="whats-new-in-version-30"></a>Neuerungen in Version 3.0  

- Unterstützung für PHP 5.4  PHP 5.2 wird in Version 3 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]nicht unterstützt.  
- Verbindungsoption AttachDBFileName wurde hinzugefügt. Weitere Informationen finden Sie unter [Connection Options](../../connect/php/connection-options.md).  
- Unterstützung für LocalDB, (ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]). Weitere Informationen finden Sie unter [Unterstützung für LocalDB](../../connect/php/php-driver-for-sql-server-support-for-localdb.md).
- Verbindungsoption AttachDBFileName wurde hinzugefügt. Weitere Informationen finden Sie unter [Connection Options](../../connect/php/connection-options.md).  
- Unterstützung für Hochverfügbarkeit und Notfallwiederherstellung Weitere Informationen finden Sie unter [Unterstützung für hohe Verfügbarkeit, Notfallwiederherstellung](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).
- Unterstützung für clientseitige Cursor (Zwischenspeichern eines Resultsets im Arbeitsspeicher). Weitere Informationen finden Sie unter [Cursortypen &#40;SQLSRV-Treiber&#41;](../../connect/php/cursor-types-sqlsrv-driver.md) und [Cursortypen &#40;PDO_SQLSRV-Treiber&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).
- Das Attribut PDO::ATTR_EMULATE_PREPARES- wurde hinzugefügt. Weitere Informationen finden Sie unter [PDO::prepare](../../connect/php/pdo-prepare.md).  

## <a name="whats-new-in-version-20"></a>Neuerungen in Version 2.0

In Version 2.0 wurde Unterstützung für den PDO_SQLSRV-Treiber hinzugefügt. Weitere Informationen finden Sie in der [PDO_SQLSRV-Treiberreferenz](../../connect/php/pdo-sqlsrv-driver-reference.md).  

## <a name="see-also"></a>Weitere Informationen

[Overview of the Microsoft Drivers for PHP for SQL Server (Übersicht über die Microsoft-Treiber für PHP für SQL Server)](../../connect/php/overview-of-the-php-sql-driver.md)
