---
title: sp_datatype_info (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/25/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_datatype_info_TSQL
- sp_datatype_info
dev_langs:
- TSQL
helpviewer_keywords:
- sp_datatype_info
ms.assetid: 045f3b5d-6bb7-4748-8b4c-8deb4bc44147
author: stevestein
ms.author: sstein
ms.openlocfilehash: 39e8f688c23cffb1512be1cd1142d38c010668a7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68108304"
---
# <a name="sp_datatype_info-transact-sql"></a>sp_datatype_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  Gibt Informationen zu den von der aktuellen Umgebung unterstützten Datentypen zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_datatype_info [ [ @data_type = ] data_type ]   
     [ , [ @ODBCVer = ] odbc_version ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @data_type = ] data_type`Die Codenummer für den angegebenen Datentyp. Um eine Liste aller Datentypen abzurufen, lassen Sie diesen Parameter weg. *data_type* ist vom Datentyp **int**und hat den Standardwert 0.  
  
`[ @ODBCVer = ] odbc_version`Die verwendete ODBC-Version. *odbc_version* ist vom Datentyp **tinyint**. der Standardwert ist 2.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Keine  
  
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
|SEARCHABLE|**smallint**|Gibt die Suchfunktion des Spaltentyps an:<br /><br /> 1 = Kann nicht durchsucht werden.<br /><br /> 2 = Durchsuchbar mit LIKE<br /><br /> 3 = Durchsuchbar mit WHERE<br /><br /> 4 = Durchsuchbar mit WHERE oder LIKE|  
|UNSIGNED_ATTRIBUTE|**smallint**|Gibt das Vorzeichen des Datentyps an.<br /><br /> 1 = Datentyp ohne Vorzeichen<br /><br /> 0 = Datentyp mit Vorzeichen|  
|MONEY|**smallint**|Gibt den **Money** -Datentyp an.<br /><br /> 1 = **Money** -Datentyp.<br /><br /> 0 = kein **Money** -Datentyp.|  
|AUTO_INCREMENT|**smallint**|Gibt die automatische Inkrementierung an.<br /><br /> 1 = Automatische Inkrementierung<br /><br /> 0 = Keine automatische Inkrementierung<br /><br /> NULL = Attribut nicht zutreffend.<br /><br /> Eine Anwendung kann zwar Werte in eine Spalte einfügen, die dieses Attribut aufweist, kann jedoch die Werte in der Spalte nicht aktualisieren. Mit Ausnahme des **Bit** -Datentyps ist AUTO_INCREMENT nur für Datentypen gültig, die zu den genauen numerischen und ungefähren numerischen Datentyp Kategorien gehören.|  
|LOCAL_TYPE_NAME|**sysname**|Lokalisierte Version des von der Datenquelle abhängigen Datentypamens. Beispielsweise lautet DECIMAL auf Französisch DECIMALE. NULL wird zurückgegeben, wenn ein lokalisierter Name nicht von der Datenquelle unterstützt wird.|  
|MINIMUM_SCALE|**smallint**|Die minimalen Dezimalstellen des Datentyps bezüglich der Datenquelle. Wenn für einen Datentyp feste Dezimalstellen definiert wurden, enthalten die Spalten MINIMUM_SCALE und MAXIMUM_SCALE denselben Wert. NULL wird zurückgegeben, wenn Dezimalstellen auf den Datentyp nicht anwendbar sind.|  
|MAXIMUM_SCALE|**smallint**|Die maximalen Dezimalstellen des Datentyps bezüglich der Datenquelle. Wenn die maximalen Dezimalstellen für die Datenquelle nicht separat definiert wurden und stattdessen definiert wurde, dass sie der maximalen Genauigkeit entsprechen, enthält diese Spalte denselben Wert wie die PRECISION-Spalte.|  
|SQL_DATA_TYPE|**smallint**|Der Wert des SQL-Datentyps, wie er im TYPE-Feld des Deskriptors angezeigt wird. Diese Spalte ist mit Ausnahme der Datentypen **DateTime** und ANSI **Interval** identisch mit der Spalte data_type. Dieses Feld gibt immer einen Wert zurück.|  
|SQL_DATETIME_SUB|**smallint**|der **DateTime** -oder ANSI- **Intervall** -Subcode, wenn der Wert von SQL_DATA_TYPE SQL_DATETIME oder SQL_INTERVAL ist. Bei anderen Datentypen als **DateTime** und ANSI **Interval**ist dieses Feld NULL.|  
|NUM_PREC_RADIX|**int**|Die Anzahl der Bits oder Stellen für das Berechnen der höchsten Zahl, die eine Spalte enthalten kann. Wenn es sich um einen ungefähren numerischen Datentyp handelt, enthält diese Spalte den Wert 2 für mehrere Bits. Bei exakten numerischen Datentypen enthält diese Spalte den Wert 10 für mehrere Dezimalstellen. Andernfalls ist diese Spalte NULL. Aus der Kombination von Genauigkeit und Basis kann die Anwendung die höchste Zahl berechnen, die die Spalte enthalten kann.|  
|INTERVAL_PRECISION|**smallint**|Wert der Intervall führenden Genauigkeit, ** Wenn data_type **Intervall**ist. andernfalls NULL.|  
|USERTYPE|**smallint**|**usertype** -Wert aus der systypes-Tabelle.|  
  
## <a name="remarks"></a>Bemerkungen  
 sp_datatype_info entspricht sqlgettypeingefo in ODBC. Die zurückgegebenen Ergebnisse sind zuerst nach DATA_TYPE und dann nach der Übereinstimmung des Datentyps mit dem entsprechenden ODBC SQL-Datentyp geordnet.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der public-Rolle.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden Informationen für die Datentypen **vom Datentyp sysname** und **nvarchar** abgerufen, indem der *data_type* Wert angegeben `-9`wird.  
  
```  
USE master;  
GO  
EXEC sp_datatype_info -9;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
