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
manager: jroth
ms.openlocfilehash: b17e45fee91b293524cca39037f15fac15cd881e
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66797076"
---
# <a name="release-notes-for-the-microsoft-drivers-for-php-for-sql-server"></a>Versionshinweise für die Microsoft-Treiber für PHP für SQL Server

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Auf dieser Seite wird erläutert, was in jeder Version hinzugefügt wurde die [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  

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
| Keine Unterstützung mehr für PHP 7.0. | &nbsp; |
| Unterstützung für Microsoft ODBC-Treiber 17.3 auf allen Plattformen. | &nbsp; |
| Unterstützung für MacOS Mojave. | ODBC-Treiber 17.3 erfordert oder höher. |
| Unterstützung für Ubuntu 18.10 und Suse Linux 15. | Sowohl die ODBC-Treiber 17.3 erfordern oder höher. |
| Unterstützung für die Ubuntu 17.10 Linux und MacOS El Capitan wird gelöscht. | &nbsp; |
| Unterstützung für Azure AD-Zugriffstoken. | Sind Sie in Linux und MacOS-ODBC-Treiber 17.2 + "und" UnixODBC 2.3.6+ erforderlich. |
| Unterstützung für die Authentifizierung mit Azure AD mithilfe der verwalteten Dienstidentität für Azure-Ressourcen. | Erfordert die ODBC-Treiber 17.3 +. |
| Neue Fetch-Funktionen | &bull; &nbsp; Neue PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE-Flag für die Pdo_sqlsrv "DateTime" als Objekte zurückgegeben.<br/><br/>&bull; &nbsp; Fügen Sie ReturnDatesAsStrings-Option auf Anweisungsebene für Sqlsrv.<br/><br/>&bull; &nbsp; Neue Optionen auf Verbindungs- und Ebenen für beide Treiber für die Formatierung der Dezimalwerte in die abgerufenen Ergebnisse. |
| Unterstützung für statische Kompilierung von Treibern, wenn Benutzer sich entscheiden, die von der Quelle erstellen. | &nbsp; |
| Verbesserte Leistung durch Zwischenspeichern von Metadaten in Abrufvorgängen und Unicode-zeichenfolgenkonvertierungen beschleunigen. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="whats-new-in-version-53"></a>Neues in Version 5.3

- Unterstützung für Microsoft ODBC-Treiber 17.2 auf allen Plattformen
- Unterstützung für MacOS High Sierra (erfordert ODBC Driver 17 und höher)
- Unterstützung für Azure Key Vault für Always Encrypted für eine solche grundlegende CRUD-Funktionen, die Always Encrypted-Feature für alle verfügbar ist, unterstützt Windows, Linux oder MacOS-Plattformen [Using Always Encrypted, mit der PHP-Treiber für SQL Server](../../connect/php/using-always-encrypted-php-drivers.md)
- Unterstützung von Ubuntu 18.04 LTS (erfordert die ODBC-Treiber 17.2)
- Unterstützung für Resilienz von Verbindungen unter Linux oder MacOS auch (erfordert die ODBC-Treiber 17.2)

## <a name="whats-new-in-version-52"></a>Neues in Version 5.2

- Unterstützung für PHP 7.2.1 und unter Windows und 7.2.0 und auf anderen Plattformen
- Unterstützung für Microsoft ODBC Driver 17
  - Version 17 wird nun als Standard für alle Plattformen
- Unterstützung für die Ubuntu 17.10, Debian 9 und Suse Enterprise Linux 12
- Keine Unterstützung mehr für Ubuntu 15.10
- Unterstützung für Always Encrypted mit CRUD-Funktionen in Windows. Weitere Informationen finden Sie unter [Using Always Encrypted with the ODBC Driver for SQL Server (Verwenden von Always Encrypted mit dem ODBC Driver for SQL Server)](../../connect/php/using-always-encrypted-php-drivers.md).
  - Unterstützung für Windows Certificate Store
  - Immer verschlüsselt nur mit Microsoft ODBC Driver 17 und höher unterstützt
- Unterstützung für nicht-UTF8-Sprachversionen unter Linux und macOS
  - Nicht-UTF8-Gebietsschemas unter Linux und MacOS werden nur mit Microsoft ODBC Driver 17 und höher unterstützt.
- Unterstützung für Azure SQL Data Warehouse
- Unterstützung für verwaltete Azure SQL-Instanzen (verlängerte private Vorschau)

## <a name="whats-new-in-version-43"></a>Neues in Version 4.3

- Unterstützung für PHP 7.1
- Unterstützung für MacOS Sierra und MacOS El Capitan
- Unterstützung für Ubuntu 15.10 und Debian 8
- Keine Unterstützung mehr für Ubuntu 15.04
- Unterstützung für Always On-Verfügbarkeitsgruppen über transparente Netzwerk-IP-Adressauflösung. Weitere Informationen finden Sie unter [Connection Options](../../connect/php/connection-options.md).
- Unterstützung für Sql_variant-Datentyp mit der Einschränkung hinzugefügt.
- Idle Connection Resiliency-Unterstützung in Windows. Weitere Informationen finden Sie unter [Connection Options](../../connect/php/connection-options.md).
- Unterstützung für Linux und MacOS-Verbindungspooling. Weitere Informationen finden Sie unter [Verbindungspooling](../../connect/php/connection-pooling-microsoft-drivers-for-php-for-sql-server.md).
- Unterstützung für Azure Active Directory-Authentifizierung mit ActiveDirectoryPassword und "sqlpassword". Weitere Informationen finden Sie unter [Connection Options](../../connect/php/connection-options.md).

## <a name="whats-new-in-version-40"></a>Neues in Version 4.0

- Unterstützung für PHP 7.0  
- 64-Bit-Unterstützung
- Unterstützung für Ubuntu 15.04, Ubuntu 16.04 und Red Hat 7

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
- Unterstützung für LocalDB, (ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]). Weitere Informationen finden Sie unter [-Unterstützung für LocalDB](../../connect/php/php-driver-for-sql-server-support-for-localdb.md).
- Verbindungsoption AttachDBFileName wurde hinzugefügt. Weitere Informationen finden Sie unter [Connection Options](../../connect/php/connection-options.md).  
- Unterstützung für Hochverfügbarkeit und Notfallwiederherstellung Weitere Informationen finden Sie unter [Unterstützung für hohe Verfügbarkeit, Wiederherstellung im Notfall](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).
- Unterstützung für clientseitige Cursor (Zwischenspeichern eines Resultsets im Arbeitsspeicher). Weitere Informationen finden Sie unter [Cursortypen &#40;SQLSRV-Treiber&#41;](../../connect/php/cursor-types-sqlsrv-driver.md) und [Cursortypen &#40;PDO_SQLSRV-Treiber&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).
- Das Attribut PDO::ATTR_EMULATE_PREPARES- wurde hinzugefügt. Weitere Informationen finden Sie unter [PDO::prepare](../../connect/php/pdo-prepare.md).  

## <a name="whats-new-in-version-20"></a>Neuerungen in Version 2.0

In Version 2.0 wurde Unterstützung für den PDO_SQLSRV-Treiber hinzugefügt. Weitere Informationen finden Sie in der [PDO_SQLSRV-Treiberreferenz](../../connect/php/pdo-sqlsrv-driver-reference.md).  

## <a name="see-also"></a>Weitere Informationen

[Overview of the Microsoft Drivers for PHP for SQL Server (Übersicht über die Microsoft-Treiber für PHP für SQL Server)](../../connect/php/overview-of-the-php-sql-driver.md)
