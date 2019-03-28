---
title: Sp_helpfilegroup (Transact-SQL) | Microsoft-Dokumentation
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a01132d30a293bca084669a733834c7d034048e4
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58538182"
---
# <a name="sphelpfilegroup-transact-sql"></a>sp_helpfilegroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt die Namen und Attribute von Dateigruppen zurück, die der aktuellen Datenbank zugeordnet sind.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpfilegroup [ [ @filegroupname = ] 'name' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @filegroupname = ] 'name'` Ist der logische Name einer Dateigruppe in der aktuellen Datenbank. *name* ist vom Datentyp **sysname**und hat den Standardwert NULL. Wenn *name* nicht angegeben ist, werden alle Dateigruppen in der aktuellen Datenbank aufgelistet, und nur das erste Resultset im Resultsetabschnitt wird angezeigt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**groupname**|**sysname**|Name der Dateigruppe.|  
|**groupid**|**smallint**|Numerischer Dateigruppenbezeichner.|  
|**filecount**|**int**|Die Anzahl von Dateien in der Dateigruppe.|  
  
 Wenn *name* angegeben ist, wird eine Zeile für jede Datei in der Dateigruppe zurückgegeben.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**file_in_group**|**sysname**|Der logische Name der Datei in der Dateigruppe.|  
|**fileid**|**smallint**|Numerischer Dateibezeichner.|  
|**filename**|**nchar(260)**|Der physische Name der Datei, einschließlich des Verzeichnispfades.|  
|**size**|**nvarchar(15)**|Die Dateigröße in KB.|  
|**maxsize**|**nvarchar(15)**|Die maximale Größe der Datei.<br /><br /> Dies ist die maximale Größe, auf die die Datei vergrößert werden kann. Mit UNLIMITED in diesem Feld kann die Datei so lange vergrößert werden, bis der Datenträger voll ist.|  
|**growth**|**nvarchar(15)**|Vergrößerungsinkrement der Datei. Dies zeigt den Speicherplatz an, der jedes Mal der Datei hinzugefügt wird, wenn neuer Speicherplatz benötigt wird.<br /><br /> 0 = Die Datei weist eine feste Größe auf und wird nicht vergrößert.|  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine gespeicherten Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_helpfile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpfile-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [sys.filegroups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Datenbankdateien und Dateigruppen](../../relational-databases/databases/database-files-and-filegroups.md)  
  
  
