---
title: Sp_helpdb (Transact-SQL) | Microsoft-Dokumentation
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c6d514adfed27693456338ece6fa58638e319475
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47629808"
---
# <a name="sphelpdb-transact-sql"></a>sp_helpdb (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen zu einer angegebenen Datenbank oder zu allen Datenbanken zurück.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpdb [ [ @dbname= ] 'name' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@dbname=** ] **'***name***'**  
 Der Name der Datenbank, für die Informationen ausgegeben werden. *Namen* ist **Sysname**, hat keinen Standardwert. Wenn *Namen* nicht angegeben ist, **Sp_helpdb** Informationen zu allen Datenbanken in der **sys.databases** -Katalogsicht angezeigt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Datenbankname.|  
|**"DB_SIZE"**|**vom Datentyp nvarchar(13)**|Gesamtgröße der Datenbank.|  
|**Besitzer**|**sysname**|Datenbankbesitzer, z. B. **sa**.|  
|**dbid**|**smallint**|Datenbank-ID|  
|**created**|**nvarchar(11)**|Erstellungsdatum der Datenbank.|  
|**status**|**nvarchar(600)**|Eine durch Trennzeichen getrennte Liste mit Werten von Datenbankoptionen, die zurzeit für die Datenbank festgelegt sind.<br /><br /> Optionen mit booleschen Werten werden nur aufgelistet, wenn sie aktiviert sind. Nicht boolesche Optionen werden aufgelistet, durch die entsprechenden Werte in Form von *Optionsname*=*Wert*.<br /><br /> Weitere Informationen zu dieser Einstellung finden Sie unter [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md).|  
|**compatibility_level**|**tinyint**|Datenbank-Kompatibilitätsgrad: 60, 65, 70, 80 oder 90.|  
  
 Wenn *Namen* angegeben wird, gibt es ein zusätzliches Resultset, das die dateizuordnung für die angegebene Datenbank anzeigt.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**name**|**NCHAR(128)**|Logischer Dateiname der Datei.|  
|**fileid**|**smallint**|Die Datei-ID|  
|**Dateiname**|**NCHAR(260)**|Betriebssystem-Dateiname (physischer Dateiname).|  
|**filegroup**|**nvarchar(128)**|Dateigruppe, zu der die Datei gehört.<br /><br /> NULL = Datei ist eine Protokolldatei. Sie gehört nie zu einer Dateigruppe.|  
|**size**|**nvarchar(18)**|Dateigröße in MB.|  
|**maxsize**|**nvarchar(18)**|Maximale Größe, auf die die Datei vergrößert werden kann. Mit UNLIMITED in diesem Feld kann die Datei so lange vergrößert werden, bis der Datenträger voll ist.|  
|**growth**|**nvarchar(18)**|Vergrößerungsinkrement der Datei. Dies gibt an, die Menge des Speicherplatzes der Datei, die jedes Mal neuer Speicherplatz benötigt wird hinzugefügt.|  
|**Verwendung**|**varchar(9)**|Verwendung der Datei. Für eine Datendatei ist der Wert **'nur Daten'** und der Wert ist für die Protokolldatei **'nur protokollieren'**.|  
  
## <a name="remarks"></a>Hinweise  
 Die **Status** Spalte im Resultset Berichte, die die Optionen auf ON wurde, in der Datenbank festgelegt müssen festlegen. Alle Datenbankoptionen werden nicht gemeldet, indem die **Status** Spalte. Um eine vollständige Liste der die aktuellen Einstellungen der Datenbankoptionen anzuzeigen, verwenden die **sys.databases** -Katalogsicht angezeigt.  
  
## <a name="permissions"></a>Berechtigungen  
 Wenn eine einzelne Datenbank angegeben wird, die Mitgliedschaft in der **öffentliche** Rolle in der Datenbank ist erforderlich. Wenn keine Datenbank angegeben ist, Mitgliedschaft in der **öffentliche** -Rolle in der **master** Datenbank ist erforderlich.  
  
 Wenn eine Datenbank kann nicht zugegriffen werden, **Sp_helpdb** zeigt die Fehlermeldung 15622 und alle verfügbaren Informationen über die Datenbank an, wie möglich.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine gespeicherten Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.filegroups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
