---
title: So konvertiert FOR JSON SQL Server-Datentypen in JSON-Datentypen
ms.date: 06/03/2020
ms.prod: sql
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- FOR JSON, data type conversion
ms.assetid: da356f06-efd0-4ea3-8157-77395bf790d7
author: jovanpop-msft
ms.author: jovanpop
ms.reviewer: jroth
ms.custom: seo-dt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 56ef56aa22a67a3286b544211d161568dae5e8d9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85722293"
---
# <a name="how-for-json-converts-sql-server-data-types-to-json-data-types-sql-server"></a>So konvertiert FOR JSON SQL Server-Datentypen in JSON-Datentypen (SQL Server)
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Die **FOR JSON** -Klausel verwendet die folgenden Regeln, um SQL Server-Datentypen in JSON-Typen in der JSON-Ausgabe zu konvertieren.  
  
|Category|SQL Server-Datentyp|JSON-Datentyp|  
|--------------|--------------|---------------|  
|Zeichen- und Zeichenfolgetypen|char, nchar, varchar, nvarchar|string|  
|Numerische Typen|int, bigint, float, decimal, numeric|number|  
|Bit-Typ|bit|Boolesche Werte ("true" oder "false")|  
|Datum- und Uhrzeittypen|date, datetime, datetime2, time, datetimeoffset|string|  
|Binärtypen|varbinary, binary, image, timestamp, rowversion|BASE64-codierte Zeichenfolge|  
|CLR-Typen|geometry, geography, andere CLR-Typen|Wird nicht unterstützt. Diese Typen geben einen Fehler zurück.<br /><br /> Verwenden Sie in der SELECT-Anweisung CAST oder CONVERT, oder verwenden Sie eine CLR-Eigenschaft oder -Methode, um die Quelldaten in einen SQL Server-Datentyp zu konvertieren, der erfolgreich in einen JSON-Typ konvertiert werden kann. Verwenden Sie z.B. **STAsText()** für den Geometrietyp oder **ToString()** für alle CLR-Typen. Der Typ des JSON-Ausgabewerts wird dann abgeleitet aus dem Rückgabetyp der Konvertierung, die Sie auf die SELECT-Anweisung anwenden.|  
|Andere Typen|uniqueidentifier, money|string|  

## <a name="learn-more-about-json-in-sql-server-and-azure-sql-database"></a>Weitere Informationen zu JSON in SQL Server und Azure SQL-Datenbank  
  
### <a name="microsoft-videos"></a>Microsoft-Videos

Eine visuelle Einführung in die JSON-Unterstützung, die in SQL Server und Azure SQL-Datenbank integriert ist, finden Sie in den folgenden Videos:

-   [SQL Server 2016 and JSON Support](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support)

-   [Using JSON in SQL Server 2016 and Azure SQL Database](https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database)

-   [JSON as a bridge between NoSQL and relational worlds](https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds)
  
## <a name="see-also"></a>Weitere Informationen  
 [Format Query Results as JSON with FOR JSON &#40;SQL Server&#41; (Formatieren von Abfrageergebnissen als JSON mit FOR JSON [SQL Server])](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
  
  
