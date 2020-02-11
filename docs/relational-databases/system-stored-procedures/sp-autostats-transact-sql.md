---
title: sp_autostats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_autostats_TSQL
- sp_autostats
dev_langs:
- TSQL
helpviewer_keywords:
- sp_autostats
ms.assetid: d1df8c15-ee73-49eb-9d13-6e98943c3e38
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e3fdb095ed869ba2e8f060bdba7a3dc9db81a405
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "70026246"
---
# <a name="sp_autostats-transact-sql"></a>sp_autostats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Zeigt die AUTO_UPDATE_STATISTICS-Option zum automatischen Statistikupdate für einen Index, ein Statistikobjekt, eine Tabelle oder eine indizierte Sicht an oder ändert sie.  
  
 Weitere Informationen zur AUTO_UPDATE_STATISTICS-Option finden Sie unter [ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md) und [Statistics](../../relational-databases/statistics/statistics.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_autostats [ @tblname = ] 'table_or_indexed_view_name'   
    [ , [ @flagc = ] 'stats_flag' ]   
    [ , [ @indname = ] 'statistics_name' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @tblname = ] 'table_or_indexed_view_name'`Der Name der Tabelle oder indizierten Sicht, für die die AUTO_UPDATE_STATISTICS Option angezeigt werden soll. *table_or_indexed_view_name* ist vom Datentyp **nvarchar (776)** und hat keinen Standardwert.  
  
`[ @flagc = ] 'stats_flag'`Aktualisiert die AUTO_UPDATE_STATISTICS Option auf einen der folgenden Werte:  
  
 **on** = on  
  
 **Off** = aus  
  
 Wenn *stats_flag* nicht angegeben ist, zeigen Sie die aktuelle AUTO_UPDATE_STATISTICS Einstellung an. *stats_flag* ist vom Datentyp **varchar (10)** und hat den Standardwert NULL.  
  
`[ @indname = ] 'statistics_name'`Der Name der Statistik, in der die AUTO_UPDATE_STATISTICS Option angezeigt oder aktualisiert werden soll. Um die Statistik für einen Index anzuzeigen, können Sie den Namen des Indexes verwenden. Ein Index und das dazugehörige Statistikobjekt verfügen über den gleichen Namen.  
  
 *statistics_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Wenn *stats_flag* angegeben wird, meldet **sp_autostats** die ausgeführte Aktion, aber es wird kein Resultset zurückgegeben.  
  
 Wenn *stats_flag* nicht angegeben ist, gibt **sp_autostats** das folgende Resultset zurück.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**Indexname**|**varchar(60)**|Der Name des Indexes oder der Statistik.|  
|**AUTOSTATS**|**varchar (3)**|Aktueller Wert für die AUTO_UPDATE_STATISTICS-Option.|  
|**Zuletzt aktualisiert**|**datetime**|Das Datum des letzten Statistikupdates.|  
  
 Das Resultset für eine Tabelle oder indizierte Sicht enthält Statistiken, die für Indizes erstellt wurden, einspaltige Statistiken, die mit der Option AUTO_CREATE_STATISTICS generiert wurden, und Statistiken, die mit der [CREATE STATISTICS](../../t-sql/statements/create-statistics-transact-sql.md) -Anweisung erstellt  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn der angegebene Index deaktiviert ist oder die angegebene Tabelle einen deaktivierten gruppierten Index enthält, wird eine Fehlermeldung angezeigt.  
  
 AUTO_UPDATE_STATISTICS ist für speicheroptimierte Tabellen immer auf OFF festgelegt.  
  
## <a name="permissions"></a>Berechtigungen  
 Zum Ändern der AUTO_UPDATE_STATISTICS Option ist die Mitgliedschaft in der **db_owner** Fixed-Daten Bank Rolle oder die ALTER-Berechtigung für *table_name*erforderlich. Zum Anzeigen der Option AUTO_UPDATE_STATISTICS ist die Mitgliedschaft in der **Public** -Rolle erforderlich.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-display-the-status-of-all-statistics-on-a-table"></a>A. Anzeigen des Status aller Statistiken für eine Tabelle  
 Das folgende Beispiel zeigt den Status aller Statistiken für die `Product`-Tabelle an.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_autostats 'Production.Product';  
GO  
```  
  
### <a name="b-enable-auto_update_statistics-for-all-statistics-on-a-table"></a>B. Aktivieren von AUTO_UPDATE_STATISTICS für alle Statistiken zu einer Tabelle  
 Im folgenden Beispiel wird die AUTO_UPDATE_STATISTICS-Option für alle Statistiken zur `Product`-Tabelle aktiviert.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_autostats 'Production.Product', 'ON';  
GO  
```  
  
### <a name="c-disable-auto_update_statistics-for-a-specific-index"></a>C. Deaktivieren von AUTO_UPDATE_STATISTICS für einen bestimmten Index  
 Im folgenden Beispiel wird die AUTO_UPDATE_STATISTICS-Option für den `AK_Product_Name`-Index der `Product`-Tabelle deaktiviert.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_autostats 'Production.Product', 'OFF', AK_Product_Name;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Statistiken](../../relational-databases/statistics/statistics.md)   
 [ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Erstellen von Statistiken &#40;Transact-SQL-&#41;](../../t-sql/statements/create-statistics-transact-sql.md)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/drop-statistics-transact-sql.md)   
 [sp_createstats &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-createstats-transact-sql.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
