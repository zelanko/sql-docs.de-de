---
title: sp_helpfilegroup (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpfilegroup_TSQL
- sp_helpfilegroup
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpfilegroup
ms.assetid: 619716b5-95dc-4538-82ae-4b90b9da8ebc
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 52032429764fe55a636e91cca59ed59b733bfc3a
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85881546"
---
# <a name="sp_helpfilegroup-transact-sql"></a>sp_helpfilegroup (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt die Namen und Attribute von Dateigruppen zurück, die der aktuellen Datenbank zugeordnet sind.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpfilegroup [ [ @filegroupname = ] 'name' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @filegroupname = ] 'name'`Der logische Name einer beliebigen Datei Gruppe in der aktuellen Datenbank. *name* ist vom Datentyp **sysname**und hat den Standardwert NULL. Wenn *name* nicht angegeben ist, werden alle Dateigruppen in der aktuellen Datenbank aufgelistet, und nur das erste Resultset im Resultsetabschnitt wird angezeigt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**GroupName**|**sysname**|Name der Dateigruppe.|  
|**groupID**|**smallint**|Numerischer Dateigruppenbezeichner.|  
|**filecount**|**int**|Die Anzahl von Dateien in der Dateigruppe.|  
  
 Wenn *name* angegeben ist, wird eine Zeile für jede Datei in der Dateigruppe zurückgegeben.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**file_in_group**|**sysname**|Der logische Name der Datei in der Dateigruppe.|  
|**FileID**|**smallint**|Numerischer Dateibezeichner.|  
|**filename**|**NCHAR (260)**|Der physische Name der Datei, einschließlich des Verzeichnispfades.|  
|**size**|**nvarchar (15)**|Die Dateigröße in KB.|  
|**MaxSize**|**nvarchar (15)**|Die maximale Größe der Datei.<br /><br /> Dies ist die maximale Größe, auf die die Datei vergrößert werden kann. Mit UNLIMITED in diesem Feld kann die Datei so lange vergrößert werden, bis der Datenträger voll ist.|  
|**growth**|**nvarchar (15)**|Vergrößerungsinkrement der Datei. Dies zeigt den Speicherplatz an, der jedes Mal der Datei hinzugefügt wird, wenn neuer Speicherplatz benötigt wird.<br /><br /> 0 = Die Datei weist eine feste Größe auf und wird nicht vergrößert.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-returning-all-filegroups-in-a-database"></a>A. Zurückgeben aller Dateigruppen in einer Datenbank  
 Im folgenden Beispiel werden Informationen zu den Dateigruppen in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Beispieldatenbank zurückgegeben.  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_helpfilegroup;  
GO  
```  
  
### <a name="b-returning-all-files-in-a-filegroup"></a>B. Zurückgeben aller Dateien in einer Dateigruppe  
 Im folgenden Beispiel werden Informationen zu allen Dateien in der `PRIMARY` -Dateigruppe der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Beispieldatenbank zurückgegeben.  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_helpfilegroup 'PRIMARY';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_helpfile &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpfile-transact-sql.md)   
 [sys. database_files &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys. master_files &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [sys. File Groups &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Datenbankdateien und Dateigruppen](../../relational-databases/databases/database-files-and-filegroups.md)  
  
  
