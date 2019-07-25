---
title: Anmerkungen zu dieser Version für die Microsoft-Treiber für PHP für SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/12/2019
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
ms.openlocfilehash: 23ac53a8515f55dfc0cad282fd14294e5f285af9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67935919"
---
# <a name="release-notes-for-the-microsoft-drivers-for-php-for-sql-server"></a>Versionshinweise für die Microsoft-Treiber für PHP für SQL Server

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Auf dieser Seite wird erläutert, was in den [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]einzelnen Versionen von hinzugefügt wurde.  

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

## <a name="whats-new-in-version-56"></a>Neues in Version 5.6

| Neues Element | Details |
| :------- | :------ |
| Unterstützung für PHP 7.3. | &nbsp; |
| Die Unterstützung für php 7,0 wurde verworfen. | &nbsp; |
| Unterstützung für Microsoft ODBC Driver 17,3 auf allen Plattformen. | &nbsp; |
| Unterstützung für macOS. | Erfordert den ODBC-Treiber 17,3 oder höher. |
| Unterstützung für Ubuntu 18,10 und SuSE Linux 15. | Beide erfordern den ODBC-Treiber 17,3 oder höher. |
| Die Unterstützung für Linux Ubuntu 17,10 und macOS El Capitan wurde verworfen. | &nbsp; |
| Unterstützung für Azure AD Zugriffs Token. | Unter Linux und macOS ist der ODBC-Treiber 17.2 + und unixODBC 2.3.6 + erforderlich. |
| Unterstützung für die Authentifizierung mit Azure AD mithilfe der verwalteten Identität für Azure-Ressourcen. | Erfordert den ODBC-Treiber 17.3 und höher. |
| Neue Abruf Funktionen | &bull;&nbsp; Neues PDO:: SQLSRV_ATTR_FETCHES_DATETIME_TYPE-Flag für pdo_sqlsrv, um DateTime als Objekte zurückzugeben.<br/><br/>&bull;&nbsp; Fügen Sie die ReturnDatesAsStrings-Option der Anweisungs Ebene für sqlsrv hinzu.<br/><br/>&bull;&nbsp; Neue Optionen auf Verbindungs-und Anweisungs Ebene für beide Treiber zum Formatieren von Dezimalwerten in den abgerufenen Ergebnissen. |
| Unterstützung für die statische Kompilierung von Treibern, wenn Benutzer die Erstellung aus der Quelle auswählen. | &nbsp; |
| Verbesserte Leistung durch Zwischenspeichern von Metadaten beim Abrufen und beschleunigen von Unicode-Zeichen folgen Konvertierungen. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="whats-new-in-version-53"></a>Neues in Version 5.3

- Unterstützung für Microsoft ODBC Driver 17,2 auf allen Plattformen
- Unterstützung für macOS High Sierra (erfordert ODBC Driver 17 und höher)
- Unterstützung für Azure Key Vault für Always Encrypted für grundlegende CRUD-Funktionen, sodass Always Encrypted Feature für alle unterstützten Windows-, Linux-oder macOS-Plattformen [mit Always Encrypted mit den PHP-Treibern für](../../connect/php/using-always-encrypted-php-drivers.md) verfügbar ist SQL Server
- Unterstützung von Ubuntu 18,04 LTS (erfordert ODBC Driver 17,2)
- Unterstützung für verbindungsresilienz unter Linux oder macOS (erfordert den ODBC-Treiber 17,2)

## <a name="whats-new-in-version-52"></a>Neues in Version 5.2

- Unterstützung für php 7.2.1 and up on Windows und 7.2.0 and up auf anderen Plattformen
- Unterstützung für Microsoft ODBC Driver 17
  - Version 17 ist nun die Standardeinstellung auf allen Plattformen.
- Unterstützung für Ubuntu 17,10, Debian 9 und SuSE Enterprise Linux 12
- Gelöschte Unterstützung für Ubuntu 15,10
- Unterstützung für Always Encrypted mit CRUD-Funktionen unter Windows. Weitere Informationen finden Sie unter [Verwenden von Always Encrypted mit den PHP-Treibern für SQL Server](../../connect/php/using-always-encrypted-php-drivers.md).
  - Unterstützung für den Windows-Zertifikat Speicher
  - Always Encrypted wird nur mit Microsoft ODBC Driver 17 und höher unterstützt.
- Unterstützung für nicht-UTF8-Gebiets Schemas unter Linux und macOS
  - Nicht-UTF8-Gebiets Schemas unter Linux und macOS werden nur mit Microsoft ODBC Driver 17 und höher unterstützt.
- Unterstützung für Azure SQL Data Warehouse
- Unterstützung für verwaltete Azure SQL-Instanzen (verlängerte private Vorschau)

## <a name="whats-new-in-version-43"></a>Neues in Version 4.3

- Unterstützung für PHP 7.1
- Unterstützung für macOS Sierra und macOS El Capitan
- Unterstützung für Ubuntu 15,10 und Debian 8
- Gelöschte Unterstützung für Ubuntu 15,04
- Unterstützung für Always on Verfügbarkeits Gruppen über transparente Netzwerk-IP-Auflösung. Weitere Informationen finden Sie unter [Connection Options](../../connect/php/connection-options.md).
- Unterstützung für den sql_variant-Datentyp mit Einschränkung hinzugefügt.
- Unterstützung der resilienzverbindungen im Leerlauf in Windows. Weitere Informationen finden Sie unter [Connection Options](../../connect/php/connection-options.md).
- Unterstützung für Verbindungspooling für Linux und macOS. Weitere Informationen finden Sie unter [Verbindungspooling](../../connect/php/connection-pooling-microsoft-drivers-for-php-for-sql-server.md).
- Unterstützung für Azure Active Directory Authentifizierung mit activedirectorypassword und sqlpassword. Weitere Informationen finden Sie unter [Connection Options](../../connect/php/connection-options.md).

## <a name="whats-new-in-version-40"></a>Neues in Version 4.0

- Unterstützung für PHP 7.0  
- Vollständige 64-Bit-Unterstützung
- Unterstützung für Ubuntu 15,04, Ubuntu 16,04 und RedHat 7

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
- Unterstützung für LocalDB, (ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]). Weitere Informationen finden Sie [unter Unterstützung für localdb](../../connect/php/php-driver-for-sql-server-support-for-localdb.md).
- Verbindungsoption AttachDBFileName wurde hinzugefügt. Weitere Informationen finden Sie unter [Connection Options](../../connect/php/connection-options.md).  
- Unterstützung für Hochverfügbarkeit und Notfallwiederherstellung Weitere Informationen finden Sie unter [Unterstützung für hohe Verfügbarkeit, Notfallwiederherstellung](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).
- Unterstützung für clientseitige Cursor (Zwischenspeichern eines Resultsets im Arbeitsspeicher). Weitere Informationen finden Sie unter [Cursortypen &#40;SQLSRV-Treiber&#41;](../../connect/php/cursor-types-sqlsrv-driver.md) und [Cursortypen &#40;PDO_SQLSRV-Treiber&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).
- Das Attribut PDO::ATTR_EMULATE_PREPARES- wurde hinzugefügt. Weitere Informationen finden Sie unter [PDO::prepare](../../connect/php/pdo-prepare.md).  

## <a name="whats-new-in-version-20"></a>Neuerungen in Version 2.0

In Version 2.0 wurde Unterstützung für den PDO_SQLSRV-Treiber hinzugefügt. Weitere Informationen finden Sie in der [PDO_SQLSRV-Treiberreferenz](../../connect/php/pdo-sqlsrv-driver-reference.md).  

## <a name="see-also"></a>Weitere Informationen

[Overview of the Microsoft Drivers for PHP for SQL Server (Übersicht über die Microsoft-Treiber für PHP für SQL Server)](../../connect/php/overview-of-the-php-sql-driver.md)
