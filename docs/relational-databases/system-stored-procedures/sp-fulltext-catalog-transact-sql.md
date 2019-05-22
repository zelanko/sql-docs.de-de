---
title: Sp_fulltext_catalog (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_catalog_TSQL
- sp_fulltext_catalog
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_catalog
ms.assetid: e49b98e4-d1f1-42b2-b16f-eb2fc7aa1cf5
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 528ba1cb776124c72fcb2d6f1d1e97c0b25ea2f9
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65983115"
---
# <a name="spfulltextcatalog-transact-sql"></a>sp_fulltext_catalog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Erstellt und löscht einen Volltextkatalog und startet und beendet die Indizierung eines Katalogs. Für eine Datenbank können mehrere Volltextkataloge erstellt werden.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwendung [CREATE FULLTEXT CATALOG](../../t-sql/statements/create-fulltext-catalog-transact-sql.md), [ALTER FULLTEXT CATALOG](../../t-sql/statements/alter-fulltext-catalog-transact-sql.md), und [DROP FULLTEXT CATALOG](../../t-sql/statements/drop-fulltext-catalog-transact-sql.md) stattdessen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_fulltext_catalog [ @ftcat= ] 'fulltext_catalog_name' ,   
     [ @action= ] 'action'   
     [ , [ @path= ] 'root_directory' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @ftcat = ] 'fulltext_catalog_name'` Ist der Name der Volltext-Katalog. Katalognamen müssen für jede Datenbank eindeutig sein. *Fulltext_catalog_name* ist **Sysname**.  
  
`[ @action = ] 'action'` Ist die Aktion ausgeführt werden. *action* ist vom Datentyp **varchar(20)**. Die folgenden Werte sind möglich:  
  
> [!NOTE]  
>  Volltextkataloge können bei Bedarf erstellt, gelöscht und geändert werden. Vermeiden Sie es jedoch, Schemaänderungen an mehreren Katalogen gleichzeitig auszuführen. Diese Aktionen können ausgeführt werden, mithilfe der **Sp_fulltext_table** gespeicherte Prozedur, die die empfohlene Methode ist.  
  
|Wert|Description|  
|-----------|-----------------|  
|**Erstellen**|Erstellt einen leeren, neuen Volltextkatalog im Dateisystem und fügt eine entsprechende Zeile in **Sysfulltextcatalogs** mit der *Fulltext_catalog_name* und *Root_directory*, Wenn Sie vorhanden ist, Werte. *Fulltext_catalog_name* muss innerhalb der Datenbank eindeutig sein.|  
|**Drop**|Löscht *Fulltext_catalog_name* aus dem Dateisystem entfernt wird, und löschen die zugehörige Zeile in **Sysfulltextcatalogs**. Diese Aktion schlägt fehl, wenn der Katalog Indizes für eine oder mehrere Tabellen enthält. **Sp_fulltext_table** "*Table_name*', 'drop' sollte ausgeführt werden, um die Tabellen aus dem Katalog zu löschen.<br /><br /> Wenn der Katalog nicht vorhanden ist, wird ein Fehler gemeldet.|  
|**start_incremental**|Startet eine inkrementelle Auffüllung für *Fulltext_catalog_name*. Wenn der Katalog nicht vorhanden ist, wird ein Fehler gemeldet. Wenn bereits eine Auffüllaktion für den Volltextindex aktiv ist, wird eine Warnung angezeigt und keine weitere Auffüllaktion durchgeführt. Beim inkrementellen Auffüllen werden nur geänderte Zeilen für die Volltextindizierung, abgerufen, vorausgesetzt, es ist ein **Zeitstempel** Spalte, die in der Tabelle vorhanden Volltextindex indiziert.|  
|**start_full**|Startet ein vollständiges Auffüllen für *Fulltext_catalog_name*. Alle Zeilen aller Tabellen, die diesem Volltextkatalog zugeordnet sind, werden für die Volltextindizierung abgerufen, auch wenn sie bereits indiziert wurden.|  
|**Beenden**|Beendet eine indexauffüllung für *Fulltext_catalog_name*. Wenn der Katalog nicht vorhanden ist, wird ein Fehler gemeldet. Wenn das Auffüllen bereits beendet wurde, wird keine Warnung angezeigt.|  
|**Neu erstellen**|Neu *Fulltext_catalog_name*. Bei der Neuerstellung eines Katalogs wird der vorhandene Katalog gelöscht und an seiner Stelle ein neuer Katalog erstellt. Alle Tabellen, in denen Referenzen für die Volltextindizierung vorhanden sind, werden dem neuen Katalog zugeordnet. Durch das erneute Erstellen werden die Volltextmetadaten in den Datenbanksystemtabellen zurückgesetzt.<br /><br /> Wenn die Änderungsnachverfolgung OFF ist, wird durch das erneute Erstellen keine Neuauffüllung des neu erstellten Volltextkatalogs verursacht. In diesem Fall führen Sie zum Katalog erneut aufzufüllen, **Sp_fulltext_catalog** mit der **Start_full** oder **Start_incremental** Aktion.|  
  
`[ @path = ] 'root_directory'` Ist das Stammverzeichnis (nicht der vollständige physische Pfad) für eine **erstellen** Aktion. *Root_directory* ist **nvarchar(100)** und hat den Standardwert NULL, womit die Verwendung der beim Setup angegebene Standardspeicherort. Dies ist das Unterverzeichnis Ftdata im Mssql-Verzeichnis. Beispiel: C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\MSSQL\FTData. Das angegebene Stammverzeichnis muss sich auf einem Laufwerk des gleichen Computers befinden, es darf nicht nur aus dem Laufwerkbuchstaben bestehen und darf kein relativer Pfad sein. Netzlaufwerke, austauschbare Laufwerke, Disketten und UNC-Pfade werden nicht unterstützt. Volltextkataloge müssen auf einer lokalen Festplatte des Computers erstellt werden, auf dem eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird.  
  
 **@path** ist nur gültig, wenn *Aktion* ist **erstellen**. Für andere Aktionen als **erstellen** (**beenden**, **rebuild**und so weiter), **@path** muss NULL sein oder ausgelassen.  
  
 Falls es sich bei der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] um einen virtuellen Server in einem Cluster handelt, muss das Katalogverzeichnis auf einem freigegebenen Datenträgerlaufwerk angegeben sein, von dem die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Ressource abhängt. Wenn @path nicht angegeben ist, der Speicherort des standardkatalogverzeichnisses auf den freigegebenen Datenträger in das Verzeichnis, das bei der Installation des virtuellen Servers angegeben wurde.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 Die **Start_full** Aktion dient dem Erstellen Sie einer vollständigen Momentaufnahme der Volltext-Daten in *Fulltext_catalog_name*. Die **Start_incremental** Aktion wird verwendet, um nur die geänderten Zeilen in der Datenbank neu zu indizieren. Inkrementelle Auffüllung kann angewendet werden, nur, wenn die Tabelle eine Spalte des Typs **Zeitstempel**. Wenn eine Tabelle in der Volltextkatalog nicht über eine Spalte des Typs enthält **Zeitstempel**, in der Tabelle vollständig aufgefüllt.  
  
 Volltextkatalog- und Indexdaten werden in Dateien gespeichert, die in einem Volltextkatalogverzeichnis erstellt werden. Der Volltextkatalog-Verzeichnis wird erstellt, als Unterverzeichnis des Verzeichnisses im angegebenen **@path** oder im Standard-Volltextkatalog Serververzeichnis Wenn **@path** nicht angegeben. Der Name des Volltextkatalogverzeichnisses wird so erstellt, dass er auf dem Server eindeutig ist. Deshalb können alle Volltextkatalogverzeichnisse auf einem Server denselben Pfad verwenden.  
  
## <a name="permissions"></a>Berechtigungen  
 Der Aufrufer muss Mitglied der **Db_owner** Rolle. Abhängig von der angeforderten Aktion der Aufrufer sollte nicht verweigert werden Alter- oder CONTROL-Berechtigungen (die **Db_owner** hat) auf der Ziel-Volltextkatalog.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-create-a-full-text-catalog"></a>A. Erstellen eines Volltextkatalogs  
 In diesem Beispiel wird einen leeren Volltextkatalog **Cat_Desc**in die **AdventureWorks2012** Datenbank.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'create';  
GO  
```  
  
### <a name="b-to-rebuild-a-full-text-catalog"></a>B. So erstellen Sie einen Volltextkatalog erneut  
 In diesem Beispiel wird einen vorhandenen Volltextkatalog neu erstellt. **Cat_Desc**in die **AdventureWorks2012** Datenbank.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'rebuild';  
GO  
```  
  
### <a name="c-start-the-population-of-a-full-text-catalog"></a>C. Starten des Auffüllens eines Volltextkatalogs  
 In diesem Beispiel wird eine vollständige Auffüllung des der **Cat_Desc** Katalog.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'start_full';  
GO  
```  
  
### <a name="d-stop-the-population-of-a-full-text-catalog"></a>D. Beenden des Auffüllens eines Volltextkatalogs  
 In diesem Beispiel beendet die Auffüllung des der **Cat_Desc** Katalog.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'stop';  
GO  
```  
  
### <a name="e-to-remove-a-full-text-catalog"></a>E. Entfernen eines Volltextkatalogs  
 In diesem Beispiel wird die **Cat_Desc** Katalog.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'drop';  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md)   
 [sp_fulltext_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-database-transact-sql.md)   
 [sp_help_fulltext_catalogs &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-transact-sql.md)   
 [sp_help_fulltext_catalogs_cursor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-cursor-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Volltextsuche](../../relational-databases/search/full-text-search.md)  
  
  
