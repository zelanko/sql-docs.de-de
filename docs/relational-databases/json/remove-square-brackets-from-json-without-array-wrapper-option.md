---
description: Entfernen von rechteckigen Klammern von JSON-Ausgabe mit der Option WITHOUT_ARRAY_WRAPPER
title: Entfernen von rechteckigen Klammern von JSON-Ausgabe mit der Option WITHOUT_ARRAY_WRAPPER
ms.date: 06/03/2020
ms.prod: sql
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- WITHOUT_ARRAY_WRAPPER
ms.assetid: aa86c2d1-458e-465f-abfa-75470137d054
author: jovanpop-msft
ms.author: jovanpop
ms.reviewer: jroth
ms.custom: seo-dt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1140277ee7bb6c1375f7c1f19cbed92da9f19f3a
ms.sourcegitcommit: 28fecbf61ae7b53405ca378e2f5f90badb1a296a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96595203"
---
# <a name="remove-square-brackets-from-json---without_array_wrapper-option"></a>Entfernen von rechteckigen Klammern von JSON-Ausgabe mit der Option WITHOUT_ARRAY_WRAPPER
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sqlserver2016-asdb.md)]

Geben Sie zum standardmäßigen Entfernen der rechteckigen Klammern, die die JSON-Ausgabe der **FOR JSON** -Klausel umgeben, die Option **WITHOUT_ARRAY_WRAPPER** an. Verwenden Sie diese Option mit einem einzeiligen Resultat, um ein einzelnes JSON-Objekt als Ausgabe anstelle eines Arrays mit einem einzelnen Element zu generieren.

Wenn Sie diese Option mit einem mehrzeiligen Resultat verwenden, ist die resultierende Ausgabe aufgrund von mehreren Elementen und fehlenden eckigen Klammern in keinem gültigen JSON-Format.  
  
## <a name="example-single-row-result"></a>Beispiel (einzeiliges Resultat)  
Die folgende Tabelle zeigt die Ausgabe der **FOR JSON** -Klausel mit und ohne Option **WITHOUT_ARRAY_WRAPPER** an.  
  
 **Abfrage**  
  
```sql  
SELECT 2015 as year, 12 as month, 15 as day  
FOR JSON PATH, WITHOUT_ARRAY_WRAPPER 
```  

 **Ergebnis** with the **WITHOUT_ARRAY_WRAPPER** -Option  
  
```json  
{
    "year": 2015,
    "month": 12,
    "day": 15
} 
```  
  
 **Ergebnis** (Standard) ohne die **WITHOUT_ARRAY_WRAPPER**-Option  
  
```json  
[{
    "year": 2015,
    "month": 12,
    "day": 15
}]
```  

## <a name="example-multiple-row-result"></a>Beispiel (mehrzeiliges Resultat)
Hier finden Sie ein weiteres Beispiel für eine **FOR JSON** -Klausel mit und ohne Option **WITHOUT_ARRAY_WRAPPER** an. In diesem Beispiel wird ein mehrzeiliges Resultat erzeugt. Die Ausgabe ist wegen mehrerer Elemente und fehlenden eckigen Klammern kein gültiges JSON.
  
 **Abfrage**  
  
```sql  
SELECT TOP 3 SalesOrderNumber, OrderDate, Status  
FROM Sales.SalesOrderHeader  
ORDER BY ModifiedDate  
FOR JSON PATH, WITHOUT_ARRAY_WRAPPER 
```  
  
 **Ergebnis** with the **WITHOUT_ARRAY_WRAPPER** -Option  
  
```json  
{
    "SalesOrderNumber": "SO43662",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}, {
    "SalesOrderNumber": "SO43661",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}, {
    "SalesOrderNumber": "SO43660",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
} 
```  
  
 **Ergebnis** (Standard) ohne die **WITHOUT_ARRAY_WRAPPER**-Option  
  
```json  
[{
    "SalesOrderNumber": "SO43662",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}, {
    "SalesOrderNumber": "SO43661",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}, {
    "SalesOrderNumber": "SO43660",
    "OrderDate": "2011-05-31T00:00:00",
    "Status": 5
}]
```  

## <a name="learn-more-about-json-in-sql-server-and-azure-sql-database"></a>Weitere Informationen zu JSON in SQL Server und Azure SQL-Datenbank  
  
### <a name="microsoft-videos"></a>Microsoft-Videos

Eine visuelle Einführung in die JSON-Unterstützung, die in SQL Server und Azure SQL-Datenbank integriert ist, finden Sie in den folgenden Videos:

-   [SQL Server 2016 and JSON Support](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support)

-   [Using JSON in SQL Server 2016 and Azure SQL Database](https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database)

-   [JSON as a bridge between NoSQL and relational worlds](https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds)
  
## <a name="see-also"></a>Weitere Informationen  
 [FOR-Klausel &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)  
  
  
