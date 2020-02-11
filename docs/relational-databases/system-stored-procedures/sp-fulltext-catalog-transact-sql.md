---
title: sp_fulltext_catalog (Transact-SQL) | Microsoft-Dokumentation
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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4b51e4e38b7587074a39f850c2e56dbd8c09ed6f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "72005970"
---
# <a name="sp_fulltext_catalog-transact-sql"></a>sp_fulltext_catalog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Erstellt und löscht einen Volltextkatalog und startet und beendet die Indizierung eines Katalogs. Für eine Datenbank können mehrere Volltextkataloge erstellt werden.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Verwenden Sie stattdessen [CREATE FULLTEXT CATALOG](../../t-sql/statements/create-fulltext-catalog-transact-sql.md), [ALTER FULLTEXT CATALOG](../../t-sql/statements/alter-fulltext-catalog-transact-sql.md)und [DROP FULLTEXT CATALOG](../../t-sql/statements/drop-fulltext-catalog-transact-sql.md) .  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_fulltext_catalog [ @ftcat= ] 'fulltext_catalog_name' ,   
     [ @action= ] 'action'   
     [ , [ @path= ] 'root_directory' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @ftcat = ] 'fulltext_catalog_name'`Der Name des voll Text Katalogs. Katalognamen müssen für jede Datenbank eindeutig sein. *fulltext_catalog_name* ist vom **Datentyp vom Datentyp sysname**.  
  
`[ @action = ] 'action'`Die auszuführende Aktion. *Action* ist vom Datentyp **varchar (20)**. die folgenden Werte sind möglich:  
  
> [!NOTE]  
>  Volltextkataloge können bei Bedarf erstellt, gelöscht und geändert werden. Vermeiden Sie es jedoch, Schemaänderungen an mehreren Katalogen gleichzeitig auszuführen. Diese Aktionen können mithilfe der gespeicherten Prozedur **sp_fulltext_table** ausgeführt werden. Dies ist die empfohlene Vorgehensweise.  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**Erstellen**|Erstellt einen leeren, neuen voll Text Katalog im Dateisystem und fügt eine zugeordnete Zeile in **sysfulltextkataloge** mit dem *fulltext_catalog_name* und *root_directory*, sofern vorhanden,-Werten hinzu. *fulltext_catalog_name* muss innerhalb der Datenbank eindeutig sein.|  
|**Dropdown**|Löscht *fulltext_catalog_name* durch Entfernen aus dem Dateisystem und Löschen der zugeordneten Zeile in **sysfulltextkataloge**. Diese Aktion schlägt fehl, wenn der Katalog Indizes für eine oder mehrere Tabellen enthält. **sp_fulltext_table** "*table_name*", "Drop", sollte ausgeführt werden, um die Tabellen aus dem Katalog zu löschen.<br /><br /> Wenn der Katalog nicht vorhanden ist, wird ein Fehler gemeldet.|  
|**start_incremental**|Startet eine inkrementelle Auffüllung für *fulltext_catalog_name*. Wenn der Katalog nicht vorhanden ist, wird ein Fehler gemeldet. Wenn bereits eine Auffüllaktion für den Volltextindex aktiv ist, wird eine Warnung angezeigt und keine weitere Auffüllaktion durchgeführt. Beim inkrementellen Auffüllen werden nur geänderte Zeilen für die Volltextindizierung abgerufen, vorausgesetzt, es ist eine **Zeitstempel** -Spalte vorhanden, die in der voll Text indizierten Tabelle enthalten ist.|  
|**start_full**|Startet eine vollständige Auffüllung für *fulltext_catalog_name*. Alle Zeilen aller Tabellen, die diesem Volltextkatalog zugeordnet sind, werden für die Volltextindizierung abgerufen, auch wenn sie bereits indiziert wurden.|  
|**Beenden**|Beendet eine Index Auffüllung für *fulltext_catalog_name*. Wenn der Katalog nicht vorhanden ist, wird ein Fehler gemeldet. Wenn das Auffüllen bereits beendet wurde, wird keine Warnung angezeigt.|  
|**Umgebaut**|Erstellt *fulltext_catalog_name*neu. Bei der Neuerstellung eines Katalogs wird der vorhandene Katalog gelöscht und an seiner Stelle ein neuer Katalog erstellt. Alle Tabellen, in denen Referenzen für die Volltextindizierung vorhanden sind, werden dem neuen Katalog zugeordnet. Durch das erneute Erstellen werden die Volltextmetadaten in den Datenbanksystemtabellen zurückgesetzt.<br /><br /> Wenn die Änderungsnachverfolgung OFF ist, wird durch das erneute Erstellen keine Neuauffüllung des neu erstellten Volltextkatalogs verursacht. Führen Sie in diesem Fall zum erneuten Auffüllen **sp_fulltext_catalog** mit der **start_full** -oder **start_incremental** Aktion aus.|  
  
`[ @path = ] 'root_directory'`Ist das Stammverzeichnis (nicht der gesamte physische Pfad) für eine **Create** -Aktion. *root_directory* ist vom Datentyp **nvarchar (100)** und hat den Standardwert NULL, der angibt, dass der beim Setup angegebene Standard Speicherort verwendet wird. Dies ist das Unterverzeichnis Ftdata im MSSQL-Verzeichnis. Beispiel: c:\Programme\Microsoft SQL server\mssql13. MSSQLSERVER\MSSQL\FTData. Das angegebene Stammverzeichnis muss sich auf einem Laufwerk des gleichen Computers befinden, es darf nicht nur aus dem Laufwerkbuchstaben bestehen und darf kein relativer Pfad sein. Netzlaufwerke, austauschbare Laufwerke, Disketten und UNC-Pfade werden nicht unterstützt. Volltextkataloge müssen auf einer lokalen Festplatte des Computers erstellt werden, auf dem eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird.  
  
 der Pfad ist nur gültig, wenn *Action* **Create**ist. ** \@** Für andere Aktionen als **Create** (**Stopps**, **Rebuild**usw.) muss der ** \@Pfad** NULL oder ausgelassen sein.  
  
 Falls es sich bei der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] um einen virtuellen Server in einem Cluster handelt, muss das Katalogverzeichnis auf einem freigegebenen Datenträgerlaufwerk angegeben sein, von dem die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Ressource abhängt. Wenn @path nicht angegeben ist, befindet sich der Speicherort des Standardkatalog Verzeichnisses auf dem freigegebenen Laufwerk, in dem Verzeichnis, das beim Installieren des virtuellen Servers angegeben wurde.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Die **start_full** Aktion wird verwendet, um eine vollständige Momentaufnahme der voll Text Daten in *fulltext_catalog_name*zu erstellen. Mit der **start_incremental** Aktion werden nur die geänderten Zeilen in der Datenbank neu indiziert. Die inkrementelle Auffüllung kann nur angewendet werden, wenn die Tabelle eine Spalte vom **Zeitstempel**-Typ aufweist. Wenn eine Tabelle im voll Text Katalog keine Spalte vom Typ **Zeitstempel**enthält, wird die Tabelle vollständig aufgefüllt.  
  
 Volltextkatalog- und Indexdaten werden in Dateien gespeichert, die in einem Volltextkatalogverzeichnis erstellt werden. Das voll Text Katalog Verzeichnis wird als Unterverzeichnis des Verzeichnisses erstellt, das im ** \@Pfad** oder im standardmäßigen Server-voll Text Katalog Verzeichnis angegeben ist, wenn ** \@der Pfad** nicht angegeben ist. Der Name des Volltextkatalogverzeichnisses wird so erstellt, dass er auf dem Server eindeutig ist. Deshalb können alle Volltextkatalogverzeichnisse auf einem Server denselben Pfad verwenden.  
  
## <a name="permissions"></a>Berechtigungen  
 Der Aufrufer muss Mitglied der **db_owner** Rolle sein. Abhängig von der angeforderten Aktion sollte dem Aufrufer nicht die Alter-oder CONTROL-Berechtigung verweigert werden (die **db_owner** ), die im Ziel-voll Text Katalog angezeigt wird.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-create-a-full-text-catalog"></a>A. Erstellen eines Volltextkatalogs  
 In diesem Beispiel wird ein leerer voll Text Katalog **Cat_Desc**in der **AdventureWorks2012** -Datenbank erstellt.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'create';  
GO  
```  
  
### <a name="b-to-rebuild-a-full-text-catalog"></a>B. So erstellen Sie einen Volltextkatalog erneut  
 In diesem Beispiel wird ein vorhandener voll Text Katalog **Cat_Desc**in der **AdventureWorks2012** -Datenbank neu erstellt.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'rebuild';  
GO  
```  
  
### <a name="c-start-the-population-of-a-full-text-catalog"></a>C. Starten des Auffüllens eines Volltextkatalogs  
 In diesem Beispiel wird eine vollständige Auffüllung des **Cat_Desc** Katalogs begonnen.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'start_full';  
GO  
```  
  
### <a name="d-stop-the-population-of-a-full-text-catalog"></a>D: Beenden des Auffüllens eines Volltextkatalogs  
 In diesem Beispiel wird die Auffüllung des **Cat_Desc** Katalogs angehalten.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'stop';  
GO  
```  
  
### <a name="e-to-remove-a-full-text-catalog"></a>E. Entfernen eines Volltextkatalogs  
 In diesem Beispiel wird der **Cat_Desc** Katalog entfernt.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'drop';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL-&#41;](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md)   
 [sp_fulltext_database &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-database-transact-sql.md)   
 [sp_help_fulltext_catalogs &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-transact-sql.md)   
 [sp_help_fulltext_catalogs_cursor &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-cursor-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Volltextsuche](../../relational-databases/search/full-text-search.md)  
  
  
