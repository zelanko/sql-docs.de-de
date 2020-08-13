---
title: sp_datatype_info_90 (SQL Data Warehouse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/13/2017
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 1d043964-dc6e-4c3e-ab61-bc444d5e25ae
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: aef742c3dd6993830e1402a041979ca73a2a4ea0
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2020
ms.locfileid: "88180179"
---
# <a name="sp_datatype_info_90-sql-data-warehouse"></a>sp_datatype_info_90 (SQL Data Warehouse)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Gibt Informationen zu den von der aktuellen Umgebung unterstützten Datentypen zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_datatype_info_90 [ [ @data_type = ] data_type ]   
     [ , [ @ODBCVer = ] odbc_version ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @data_type = ] data_type`Die Codenummer für den angegebenen Datentyp. Um eine Liste aller Datentypen abzurufen, lassen Sie diesen Parameter weg. *data_type* ist vom Datentyp **int**und hat den Standardwert 0.  
  
`[ @ODBCVer = ] odbc_version`Die verwendete ODBC-Version. *odbc_version* ist vom Datentyp **tinyint**. der Standardwert ist 2.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Keiner  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|TYPE_NAME|**sysname**|Der DBMS-abhängige Datentyp.|  
|DATA_TYPE|**smallint**|Der Code für den ODBC-Datentyp, dem alle Spalten dieses Datentyps zugeordnet sind.|  
|PRECISION|**int**|Die maximale Genauigkeit des Datentyps bezüglich der Datenquelle. NULL wird für Datentypen zurückgegeben, auf die die Genauigkeit nicht anwendbar ist. Der Rückgabewert für die PRECISION-Spalte hat die Basis 10.|  
|LITERAL_PREFIX|**varchar (** 32 **)**|Das oder die Zeichen, die einer Konstante vorangestellt werden. Zum Beispiel ein einzelnes Anführungszeichen (**'**) für Zeichen Typen und 0x für Binärdateien.|  
|LITERAL_SUFFIX|**varchar (** 32 **)**|Das oder die Zeichen, die eine Konstante beenden. Zum Beispiel ein einzelnes Anführungszeichen (**'**) für Zeichen Typen und keine Anführungszeichen für Binärdateien.|  
|CREATE_PARAMS|**varchar (** 32 **)**|Die Beschreibung der Erstellungsparameter für diesen Datentyp. Beispielsweise ist " **Decimal** ", "Scale", " **float** is NULL" und " **varchar** " "max_length".|  
|NULLABLE|**smallint**|Gibt die NULL-Zulässigkeit an.<br /><br /> 1 = Lässt NULL-Werte zu.<br /><br /> 0 = NULL ist nicht zulässig.|  
|CASE_SENSITIVE|**smallint**|Gibt die Unterscheidung nach Groß-/Kleinschreibung an.<br /><br /> 1 = Bei allen Spalten dieses Typs wird nach Groß-/Kleinschreibung unterschieden (für Sortierungen).<br /><br /> 0 = Bei allen Spalten dieses Typs wird nicht nach Groß-/Kleinschreibung unterschieden.|  
|DURCHSUCHBAR|**smallint**|Gibt die Suchfunktion des Spaltentyps an:<br /><br /> 1 = Kann nicht durchsucht werden.<br /><br /> 2 = Durchsuchbar mit LIKE<br /><br /> 3 = Durchsuchbar mit WHERE<br /><br /> 4 = Durchsuchbar mit WHERE oder LIKE|  
|UNSIGNED_ATTRIBUTE|**smallint**|Gibt das Vorzeichen des Datentyps an.<br /><br /> 1 = Datentyp ohne Vorzeichen<br /><br /> 0 = Datentyp mit Vorzeichen|  
|MONEY|**smallint**|Gibt den **Money** -Datentyp an.<br /><br /> 1 = **Money** -Datentyp.<br /><br /> 0 = kein **Money** -Datentyp.|  
|AUTO_INCREMENT|**smallint**|Gibt die automatische Inkrementierung an.<br /><br /> 1 = Automatische Inkrementierung<br /><br /> 0 = Keine automatische Inkrementierung<br /><br /> NULL = Attribut nicht zutreffend.<br /><br /> Eine Anwendung kann zwar Werte in eine Spalte einfügen, die dieses Attribut aufweist, kann jedoch die Werte in der Spalte nicht aktualisieren. Mit Ausnahme des **Bit** -Datentyps ist AUTO_INCREMENT nur für Datentypen gültig, die zu den genauen numerischen und ungefähren numerischen Datentyp Kategorien gehören.|  
|LOCAL_TYPE_NAME|**sysname**|Lokalisierte Version des von der Datenquelle abhängigen Datentypamens. Beispielsweise lautet DECIMAL auf Französisch DECIMALE. NULL wird zurückgegeben, wenn ein lokalisierter Name nicht von der Datenquelle unterstützt wird.|  
|MINIMUM_SCALE|**smallint**|Die minimalen Dezimalstellen des Datentyps bezüglich der Datenquelle. Wenn für einen Datentyp feste Dezimalstellen definiert wurden, enthalten die Spalten MINIMUM_SCALE und MAXIMUM_SCALE denselben Wert. NULL wird zurückgegeben, wenn Dezimalstellen auf den Datentyp nicht anwendbar sind.|  
|MAXIMUM_SCALE|**smallint**|Die maximalen Dezimalstellen des Datentyps bezüglich der Datenquelle. Wenn die maximalen Dezimalstellen für die Datenquelle nicht separat definiert wurden und stattdessen definiert wurde, dass sie der maximalen Genauigkeit entsprechen, enthält diese Spalte denselben Wert wie die PRECISION-Spalte.|  
|SQL_DATA_TYPE|**smallint**|Der Wert des SQL-Datentyps, wie er im TYPE-Feld des Deskriptors angezeigt wird. Diese Spalte ist mit Ausnahme der Datentypen **DateTime** und ANSI **Interval** identisch mit der Spalte data_type. Dieses Feld gibt immer einen Wert zurück.|  
|SQL_DATETIME_SUB|**smallint**|der **DateTime** -oder ANSI- **Intervall** -Subcode, wenn der Wert von SQL_DATA_TYPE SQL_DATETIME oder SQL_INTERVAL ist. Bei anderen Datentypen als **DateTime** und ANSI **Interval**ist dieses Feld NULL.|  
|NUM_PREC_RADIX|**int**|Die Anzahl der Bits oder Stellen für das Berechnen der höchsten Zahl, die eine Spalte enthalten kann. Wenn es sich um einen ungefähren numerischen Datentyp handelt, enthält diese Spalte den Wert 2 für mehrere Bits. Bei exakten numerischen Datentypen enthält diese Spalte den Wert 10 für mehrere Dezimalstellen. Andernfalls ist diese Spalte NULL. Aus der Kombination von Genauigkeit und Basis kann die Anwendung die höchste Zahl berechnen, die die Spalte enthalten kann.|  
|INTERVAL_PRECISION|**smallint**|Wert der Intervall führenden Genauigkeit, *data_type* Wenn data_type **Intervall**ist. andernfalls NULL.|  
|USERTYPE|**smallint**|**usertype** -Wert aus der systypes-Tabelle.|  
  
## <a name="remarks"></a>Bemerkungen  
 sp_datatype_info entspricht sqlgettypeingefo in ODBC. Die zurückgegebenen Ergebnisse sind zuerst nach DATA_TYPE und dann nach der Übereinstimmung des Datentyps mit dem entsprechenden ODBC SQL-Datentyp geordnet.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der public-Rolle.  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Im folgenden Beispiel werden Informationen für die Datentypen **vom Datentyp sysname** und **nvarchar** abgerufen, indem der *data_type* Wert angegeben wird `-9` .  
  
```sql  
USE master;  
GO  
EXEC sp_datatype_info_90 -9;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren SQL Data Warehouse](../../relational-databases/system-stored-procedures/sql-data-warehouse-stored-procedures.md)   
 [Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
  
  

