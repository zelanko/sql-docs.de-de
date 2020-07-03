---
title: sp_helpdb (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpdb
- sp_helpdb_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpdb
ms.assetid: 4c3e3302-6cf1-4b2b-8682-004049b578c3
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3fda6aba2ce361e814a0196db6138b38f13ce359
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85899570"
---
# <a name="sp_helpdb-transact-sql"></a>sp_helpdb (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt Informationen zu einer angegebenen Datenbank oder zu allen Datenbanken zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpdb [ [ @dbname= ] 'name' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @dbname = ] 'name'`Der Name der Datenbank, für die Informationen gemeldet werden. *Name ist vom Datentyp* **vom Datentyp sysname**und hat keinen Standardwert. Wenn *Name* nicht angegeben wird, **sp_helpdb** Berichte zu allen Datenbanken in der **sys. Datenbanken** -Katalog Sicht.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Datenbankname.|  
|**db_size**|**nvarchar (13)**|Gesamtgröße der Datenbank.|  
|**Eigentor**|**sysname**|Datenbankbesitzer, z. b. **sa**.|  
|**DBID**|**smallint**|Datenbank-ID|  
|**created**|**nvarchar(11)**|Erstellungsdatum der Datenbank.|  
|**status**|**nvarchar (600)**|Eine durch Trennzeichen getrennte Liste mit Werten von Datenbankoptionen, die zurzeit für die Datenbank festgelegt sind.<br /><br /> Optionen mit booleschen Werten werden nur aufgelistet, wenn sie aktiviert sind. Nicht boolesche Optionen werden mit ihren entsprechenden Werten in Form von *option_name* = *Wert*aufgelistet.<br /><br /> Weitere Informationen zu dieser Einstellung finden Sie unter [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md).|  
|**compatibility_level**|**tinyint**|Datenbank-Kompatibilitätsgrad: 60, 65, 70, 80 oder 90.|  
  
 Wenn *Name* angegeben wird, gibt es ein zusätzliches Resultset, das die Datei Zuordnung für die angegebene Datenbank anzeigt.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**name**|**NCHAR (128)**|Logischer Dateiname der Datei.|  
|**FileID**|**smallint**|Die Datei-ID|  
|**filename**|**NCHAR (260)**|Betriebssystem-Dateiname (physischer Dateiname).|  
|**Dateigruppe (filegroup)**|**nvarchar(128)**|Dateigruppe, zu der die Datei gehört.<br /><br /> NULL = Datei ist eine Protokolldatei. Sie gehört nie zu einer Dateigruppe.|  
|**size**|**nvarchar (18)**|Dateigröße in MB.|  
|**MaxSize**|**nvarchar (18)**|Maximale Größe, auf die die Datei vergrößert werden kann. Mit UNLIMITED in diesem Feld kann die Datei so lange vergrößert werden, bis der Datenträger voll ist.|  
|**growth**|**nvarchar (18)**|Vergrößerungsinkrement der Datei. Gibt den Speicherplatz an, der der Datei jedes Mal hinzugefügt wird, wenn neuer Speicherplatz benötigt wird.|  
|**ungs**|**varchar (9)**|Verwendung der Datei. Bei einer Datendatei ist der Wert **' nur Daten** ', und für die Protokolldatei lautet der Wert **' nur protokollieren '**.|  
  
## <a name="remarks"></a>Hinweise  
 Die **Status** -Spalte im Resultset meldet, welche Optionen in der Datenbank auf ON festgelegt wurden. Alle Daten Bankoptionen werden nicht von der **Status** -Spalte gemeldet. Verwenden Sie die **sys.** Database-Katalog Sicht, um eine komplette Liste der aktuellen Einstellungen für die Datenbankoption anzuzeigen.  
  
## <a name="permissions"></a>Berechtigungen  
 Wenn eine einzelne Datenbank angegeben wird, ist die Mitgliedschaft in der **Public** -Rolle in der Datenbank erforderlich. Wenn keine Datenbank angegeben wird, ist die Mitgliedschaft in der **Public** -Rolle in der **Master** -Datenbank erforderlich.  
  
 Wenn auf eine Datenbank nicht zugegriffen werden kann, wird in **sp_helpdb** Fehlermeldung 15622 und so viele Informationen zur Datenbank angezeigt.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-returning-information-about-a-single-database"></a>A. Zurückgeben von Informationen für eine einzelne Datenbank  
 Im folgenden Beispiel werden Informationen zur [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank angezeigt.  
  
```sql  
EXEC sp_helpdb N'AdventureWorks2012';  
```  
  
### <a name="b-returning-information-about-all-databases"></a>B. Zurückgeben von Informationen für alle Datenbanken  
 Im folgenden Beispiel werden Informationen zu allen Datenbanken auf dem Server mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] angezeigt.  
  
```sql  
EXEC sp_helpdb;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys. database_files &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys. File Groups &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [sys. master_files &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
