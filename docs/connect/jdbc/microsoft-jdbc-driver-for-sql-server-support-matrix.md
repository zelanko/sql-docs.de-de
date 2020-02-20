---
title: Supportmatrix für den Microsoft JDBC-Treiber für SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c5769e67-99f7-4bc1-a4fa-8941dad33d35
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 950fa902d2772d131f5ecd626653ad58c97c0fb1
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "69027895"
---
# <a name="microsoft-jdbc-driver-for-sql-server-support-matrix"></a>Supportmatrix für den Microsoft JDBC-Treiber für SQL Server
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Auf dieser Seite finden Sie die Unterstützungsmatrix und die Support Lifecycle-Richtlinie für den Microsoft JDBC-Treiber für SQL Server.  
  
## <a name="microsoft-jdbc-driver-support-lifecycle-matrix-and-policy"></a>Support Lifecycle-Matrix und -Richtlinie für Microsoft JDBC-Treiber  
 Die Microsoft Support Lifecycle-Richtlinie (MLS) bietet transparente, vorhersagbare Informationen hinsichtlich der Supportdauer bei Microsoft-Produkten. Für die Versionen 3.0, 4.x, 6.x und 7.x des JDBC-Treibers wird ab dem Veröffentlichungsdatum fünf Jahre grundlegender Support (Mainstream-Support) geleistet. Die Definition für den grundlegenden Support finden Sie auf der Website der Microsoft Support Lifecycle-Richtlinie.  
  
 Erweiterte und benutzerdefinierte Support-Optionen sind für den Microsoft JDBC-Treiber nicht verfügbar.  
    
 Die folgenden Microsoft JDBC-Treiber werden bis zum angegebenen Supportende unterstützt.  
  
|Treibername|Version des Treiberpakets|Zutreffende JAR-Datei(en)|Ende des grundlegenden Supports|
|-|-|-|-|  
|Microsoft JDBC-Treiber 7.4 für SQL Server|7.4|mssql-jdbc-7.4.1.jre12.jar<br> mssql-jdbc-7.4.1.jre11.jar<br> mssql-jdbc-7.4.1.jre8.jar|2\. August 2024|
|Microsoft JDBC-Treiber 7.2 für SQL Server|7.2|mssql-jdbc-7.2.2.jre11.jar<br> mssql-jdbc-7.2.2.jre8.jar|16. April 2024|
|Microsoft JDBC-Treiber 7.0 für SQL Server|7.0|mssql-jdbc-7.0.0.jre10.jar<br> mssql-jdbc-7.0.0.jre8.jar|31. Juli 2023|  
|Microsoft JDBC-Treiber 6.4 für SQL Server|6.4|mssql-jdbc-6.4.0.jre9.jar<br> mssql-jdbc-6.4.0.jre8.jar<br> mssql-jdbc-6.4.0.jre7.jar|27. Februar 2023|    
|Microsoft JDBC-Treiber 6.2 für SQL Server|6.2|mssql-jdbc-6.2.2.jre8.jar<br> mssql-jdbc-6.2.2.jre7.jar|30. Juni 2022|    
|Microsoft JDBC-Treiber 6.0 für SQL Server|6.0|sqljdbc42.jar<br>sqljdbc41.jar|14. Juli 2021|    
|Der Microsoft JDBC-Treiber 4.2 für SQL Server|4,2|sqljdbc42.jar<br>sqljdbc41.jar|24. August 2020|  
|Microsoft JDBC-Treiber 4.1 für SQL Server|4,1|sqljdbc41.jar|12. Dezember 2019|  
  
 Die folgenden Microsoft JDBC-Treiber werden nicht länger unterstützt.  
 
|Treibername|Version des Treiberpakets|Ende des grundlegenden Supports|  
|-|-|-|
|Microsoft JDBC-Treiber 4.0 für SQL Server|4,0|6\. März 2017|  
|Microsoft SQL Server JDBC Driver 3.0|3.0|23. April 2015|  
|Microsoft SQL Server JDBC Driver 2.2|2.0|31. Dezember 2012|  
|Microsoft SQL Server 2005 JDBC Driver 1.2|1.2|25. Juni 2011|  
|Microsoft SQL Server 2005 JDBC Driver 1.1|1.1|25. Juni 2011|  
|Microsoft SQL Server 2005 JDBC Driver 1.0|1.0|25. Juni 2011|  
|Microsoft SQL Server 2000 JDBC Driver|2000|9\. Juli 2010|  
  
## <a name="sql-version-compatibility"></a>SQL-Versionskompatibilität  
  
|Treiberversion|SQL Server 2008|SQL Server 2008R2|SQL Server 2012|Azure SQL-Datenbank|PDW 2008R2 AU3<sup>4</sup>|SQL Server 2014|SQL Server 2016|SQL Server 2017|SQL Server 2019|  
|-|-|-|-|-|-|-|-|-|-|-|
|7.4|N|N|J|J|J|J|J|J|J|
|7.2|N|J|J|J|J|J|J|J|N| 
|7.0|N|J|J|J|J|J|J|J|N| 
|6.4|N|J|J|J|J|J|J|J|N| 
|6.2|J|J|J|J|J|J|J|J|N|
|6.1|J|J|J|J|J|J|J|N|N|
|6.0|J|J|J|J|J|J|J|N|N|
|4,2|J|J|J|J|J|J|J|N|N|
|4,1|J|J|J|J|J|J|J|N|N|
|4,0|J|J|J|J|J|J|J|N|N|
|3.0|J|J|J<sup>1</sup>|J<sup>2</sup>|N|J<sup>5</sup>|N|N|N|
|2.0|J<sup>3</sup>|J<sup>3</sup>|N|N|N|N|N|N|N|
|1.2|J<sup>3</sup>|N|N|N|N|N|N|N|N|
|1.1|N|N|N|N|N|N|N|N|N|  
|1.0|N|N|N|N|N|N|N|N|N|  
|2000|N|N|N|N|N|N|N|N|N|  
  
 <sup>1</sup>Die Version 3.0 des Treibers Microsoft SQL Server JDBC Driver kann sich als kompatibler Client mit SQL Server 2012 verbinden.  
  
 <sup>2</sup>Die Unterstützung für Azure SQL-Datenbank wurde in Version 3.0 als Hotfix eingeführt. Es wird empfohlen, dass Azure SQL-Datenbank-Kunden die neuesten Treiber verwenden.  
  
 <sup>3</sup>Die Version 2.0 des Treibers Microsoft SQL Server JDBC Driver und die Version 2.1 des Treibers Microsoft SQL Server 2005 JDBC kann als Client eine abwärtskompatible Verbindung mit SQL Server 2008 herstellen. Sind abwärtskompatible Konvertierungen erlaubt, kann die Anwendung Abfragen ausführen und Aktualisierungen auf die neuen Datentypen von SQL Server 2008 durchführen, wie z. B. „time“, „date“, „datetime2“, „datetimeoffset“ und FILESTREAM. Weitere Informationen zur Verwendung dieser neuen Datentypen mit dem JDBC-Treiber finden Sie unter  [Verwenden der Date/Time-Datentypen in SQL Server 2008 mithilfe eines JDBC-Treibers](https://go.microsoft.com/fwlink/?LinkId=145198) und unter  [Verwenden von Filestream in SQL Server 2008 mithilfe eines JDBC-Treibers](https://go.microsoft.com/fwlink/?LinkId=145199). Weitere Informationen zur Abwärtskompatibilität dieser neuen Datentypen finden Sie in den Themen  [Verwenden von Datums- und Zeitdaten](https://go.microsoft.com/fwlink/?LinkId=145211)und  [FILESTREAM-Unterstützung](https://go.microsoft.com/fwlink/?LinkId=145212) in der SQL Server-Onlinedokumentation  
  
 <sup>4</sup>Die Unterstützung von Verbindungen zwischen dem Microsoft JDBC-Treiber und Parallel Data Warehouse wurde erstmals in Microsoft JDBC-Treiber 4.0 für SQL Server und in Microsoft SQL Server 2008 R2 Parallel Data Warehouse Appliance Update 3 bereitgestellt.  
  
 <sup>5</sup>Version 3.0 des JDBC-Treibers für Microsoft SQL Server kann sich als kompatibler Client mit SQL Server 2014 verbinden.  
  
## <a name="java-and-jdbc-specification-support"></a>Unterstützung der Java- und JDBC-Spezifikation  
  
|Version des JDCB-Treibers|JRE-Version|JDBC-API-Version| 
|-|-|-|  
|7.4|1.8, 11, 12|4.2, 4.3 (teilweise)|
|7.2|1.8, 11|4.2, 4.3 (teilweise)|
|7.0|1.8, 10|4.2, 4.3 (teilweise)|
|6.4|1.7, 1.8, 9|4.1, 4.2, 4.3 (teilweise)|  
|6.2|1.7, 1.8|4.1, 4.2|  
|6.1|1.7, 1.8|4.1, 4.2|  
|6.0|1.7, 1.8|4.1, 4.2|  
|4,2|1.7, 1.8|4.1, 4.2|  
|4,1|1.7|4,0|  
|4,0|1.5, 1.6, 1.7|3.0, 4.0|  
|3.0|1.5, 1.6,|3.0, 4.0|  
|2.0|1.5, 1.6|3.0, 4.0|  
|1.2|1.4, 1.5, 1.6|3.0|  
|1.1|1.4|3.0|  
|1.0|1.4|3.0|  
|2000|1.4|3.0|  
  
## <a name="supported-operating-systems"></a>Unterstützte Betriebssysteme  
 Der JDBC-Treiber ist für die Verwendung mit allen Betriebssystemen konzipiert, die die Java Virtual Machine (JVM) unterstützen. Einige weitverbreitete Plattformen enthalten Windows 10, Windows 8.1, Windows 8, Windows 7, Windows Server 2008 R2, Windows Vista, Linux, Unix, AIX, Mac OS und andere.  
  
 Das JDBC-Produktteam testet unsern Treiber unter Windows, Sun Solaris, SUSE Linux und RedHat Linux.  Der Kundendienst steht dem Kunden auf allen Plattformen zur Verfügung. Jedoch kann es vorkommen, dass Sie gebeten werden, Ihr Problem auf einer anderen Plattform, z. B. auf Windows, zu reproduzieren.  
  
## <a name="application-server-support"></a>Support für Anwendungsserver  
 Der Microsoft JDBC-Treiber für SQL Server wird mit verschiedenen Anwendungsservern getestet.  Wenden Sie sich an den Anbieter Ihres Anwendungsserver, um detaillierte Informationen über die zu seinem Produkt kompatible Treiberversion zu erhalten.
 
 
