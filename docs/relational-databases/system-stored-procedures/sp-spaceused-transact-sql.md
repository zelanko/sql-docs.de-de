---
title: sp_spaceused (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_spaceused_TSQL
- sp_spaceused
dev_langs:
- TSQL
helpviewer_keywords:
- sp_spaceused
ms.assetid: c6253b48-29f5-4371-bfcd-3ef404060621
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6b0bd2f253dede1c427eda826eba0e998a144736
ms.sourcegitcommit: c426c7ef99ffaa9e91a93ef653cd6bf3bfd42132
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252021"
---
# <a name="sp_spaceused-transact-sql"></a>sp_spaceused (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Gibt die Anzahl der Zeilen sowie den zugeordneten und verwendeten Speicherplatz für eine bestimmte Tabelle, eine indizierte Sicht oder eine [!INCLUDE[ssSB](../../includes/sssb-md.md)]-Warteschlange in der aktuellen Datenbank bzw. den zugeordneten und verwendeten Speicherplatz für die gesamte Datenbank an.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_spaceused [[ @objname = ] 'objname' ]   
[, [ @updateusage = ] 'updateusage' ]  
[, [ @mode = ] 'mode' ]  
[, [ @oneresultset = ] oneresultset ]  
[, [ @include_total_xtp_storage = ] include_total_xtp_storage ]
```  
  
## <a name="arguments"></a>Argumente  

Bei [!INCLUDE[sssdw-md](../../includes/sssdw-md.md)] und [!INCLUDE[sspdw-md](../../includes/sspdw-md.md)] müssen `sp_spaceused` benannte Parameter angeben (z. b. `sp_spaceused (@objname= N'Table1');`, anstatt sich auf die Ordinalposition von Parametern zu verlassen. 

`[ @objname = ] 'objname'`
   
 Der qualifizierte oder nicht qualifizierte Name der Tabelle, indizierten Sicht oder Warteschlange, für die Informationen zur Speicherverwendung angefordert werden. Anführungszeichen sind nur erforderlich, wenn ein qualifizierter Objektname angegeben wird. Bei Angabe eines vollqualifizierten Objektnamens (einschließlich eines Datenbanknamens) muss der Datenbankname der Name der aktuellen Datenbank sein.  
Wenn *objname* nicht angegeben wird, werden die Ergebnisse für die gesamte Datenbank zurückgegeben.  
*objname ist vom Datentyp* **nvarchar (776)** und hat den Standardwert NULL.  
> [!NOTE]  
> [!INCLUDE[sssdw-md](../../includes/sssdw-md.md)] und [!INCLUDE[sspdw-md](../../includes/sspdw-md.md)] unterstützen nur Datenbank-und Tabellen Objekte.
  
`[ @updateusage = ] 'updateusage'` gibt an, dass DBCC UPDATEUSAGE ausgeführt werden soll, um Speicherplatz Verwendungs Informationen zu aktualisieren. Wenn *objname* nicht angegeben wird, wird die-Anweisung für die gesamte Datenbank ausgeführt. Andernfalls wird die-Anweisung auf *objname*ausgeführt. Die Werte können " **true** " oder " **false**" sein. *UPDATEUSAGE* ist vom Datentyp **varchar (5)** und hat den Standardwert **false**.  
  
`[ @mode = ] 'mode'` gibt den Bereich der Ergebnisse an. Bei einer gestreckten Tabelle oder Datenbank können Sie mit dem *Modusparameter* den Remote Teil des Objekts einschließen bzw. ausschließen. Weitere Informationen finden Sie unter [Stretch Database](../../sql-server/stretch-database/stretch-database.md).  
  
 Das *Mode* -Argument kann die folgenden Werte aufweisen:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|ALL|Gibt die Speicher Statistik des Objekts oder der Datenbank zurück, einschließlich des lokalen Teils und des Remote Teils.|  
|LOCAL_ONLY|Gibt die Speicher Statistiken für nur den lokalen Teil des Objekts oder der Datenbank zurück. Wenn das Objekt oder die Datenbank nicht Stretch-aktiviert ist, gibt dieselbe Statistik zurück, als wenn @mode = all.|  
|REMOTE_ONLY|Gibt die Speicher Statistiken für nur den Remote Teil des Objekts oder der Datenbank zurück. Diese Option löst einen Fehler aus, wenn eine der folgenden Bedingungen zutrifft:<br /><br /> Die Tabelle ist nicht für Stretch aktiviert.<br /><br /> Die Tabelle ist für Stretch aktiviert, aber Sie haben die Datenmigration nie aktiviert. In diesem Fall verfügt die Remote Tabelle noch nicht über ein Schema.<br /><br /> Der Benutzer hat die Remote Tabelle manuell gelöscht.<br /><br /> Die Bereitstellung des Remote Datenarchivs hat den Status "erfolgreich" zurückgegeben, aber tatsächlich ist ein Fehler aufgetreten.|  
  
 der *Modus* ist vom Datentyp **varchar (11)** und hat den Standardwert **n ' all '** .  
  
`[ @oneresultset = ] oneresultset` gibt an, ob ein einzelnes Resultset zurückgegeben werden soll. Das *oneresultset* -Argument kann die folgenden Werte aufweisen:  
  
|Wert|Description|  
|-----------|-----------------|  
|0|Wenn *\@objname* NULL ist oder nicht angegeben ist, werden zwei Resultsets zurückgegeben. Zwei Resultsets sind das Standardverhalten.|  
|1|Wenn *\@objname* = NULL oder nicht angegeben ist, wird ein einzelnes Resultset zurückgegeben.|  
  
 *oneresultset* ist vom Typ **Bit**. der Standardwert ist **0**.  

`[ @include_total_xtp_storage] 'include_total_xtp_storage'` @ no__t-1**gilt für:** [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)], [!INCLUDE[sssds-md](../../includes/sssds-md.md)].  
  
 Wenn @oneresultset = 1, bestimmt der Parameter @include_total_xtp_storage, ob das einzelne Resultset Spalten für den MEMORY_OPTIMIZED_DATA-Speicher enthält. Der Standardwert ist 0, d. h., wenn der-Parameter ausgelassen wird, sind die XTP-Spalten nicht im Resultset enthalten.  

## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Wenn *objname* ausgelassen wird und der Wert von *oneresultset* den Wert 0 hat, werden die folgenden Resultsets zurückgegeben, um aktuelle Informationen zur Datenbankgröße bereitzustellen.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|Der Name der aktuellen Datenbank.|  
|**database_size**|**varchar(18)**|Die Größe der aktuellen Datenbank in Megabyte. **database_size** schließt sowohl Daten-als auch Protokolldateien ein.|  
|**nicht zugewiesener Speicherplatz**|**varchar(18)**|Speicherplatz in der Datenbank, der nicht für Datenbankobjekte zugeordnet wurde.|  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**bleiben**|**varchar(18)**|Gesamter von Objekten in der Datenbank zugeordneter Speicherplatz.|  
|**data**|**varchar(18)**|Gesamter für Daten verwendeter Speicherplatz.|  
|**index_size**|**varchar(18)**|Gesamter für Indizes verwendeter Speicherplatz.|  
|**genutzt**|**varchar(18)**|Gesamter für Objekte in der Datenbank zugeordneter, aber noch nicht verwendeter Speicherplatz.|  
  
 Wenn *objname* ausgelassen wird und der Wert von *oneresultset* 1 ist, wird das folgende einzelne Resultset zurückgegeben, um aktuelle Informationen zur Datenbankgröße bereitzustellen.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|Der Name der aktuellen Datenbank.|  
|**database_size**|**varchar(18)**|Die Größe der aktuellen Datenbank in Megabyte. **database_size** schließt sowohl Daten-als auch Protokolldateien ein.|  
|**nicht zugewiesener Speicherplatz**|**varchar(18)**|Speicherplatz in der Datenbank, der nicht für Datenbankobjekte zugeordnet wurde.|  
|**bleiben**|**varchar(18)**|Gesamter von Objekten in der Datenbank zugeordneter Speicherplatz.|  
|**data**|**varchar(18)**|Gesamter für Daten verwendeter Speicherplatz.|  
|**index_size**|**varchar(18)**|Gesamter für Indizes verwendeter Speicherplatz.|  
|**genutzt**|**varchar(18)**|Gesamter für Objekte in der Datenbank zugeordneter, aber noch nicht verwendeter Speicherplatz.|  
  
 Wenn *objname* angegeben ist, wird das folgende Resultset für das angegebene Objekt zurückgegeben.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar(128)**|Name des Objekts, für das Informationen zur Speicherverwendung angefordert wurden.<br /><br /> Der Schemaname des Objekts wird nicht zurückgegeben. Wenn der Schema Name erforderlich ist, verwenden Sie die dynamischen Verwaltungs Sichten [sys. DM _db_partition_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-partition-stats-transact-sql.md) oder [sys. DM _db_index_physical_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md) , um entsprechende Größen Informationen zu erhalten.|  
|**rows**|**char (20)**|Anzahl der Zeilen in der Tabelle. Wenn es sich bei dem angegebenen Objekt um eine [!INCLUDE[ssSB](../../includes/sssb-md.md)]-Warteschlange handelt, wird in dieser Spalte die Anzahl der in der Warteschlange vorhandenen Nachrichten angegeben.|  
|**bleiben**|**varchar(18)**|Gesamtmenge des reservierten Speicherplatzes für *objname*.|  
|**data**|**varchar(18)**|Gesamtmenge des Speicherplatzes, der von Daten in *objname*verwendet wird.|  
|**index_size**|**varchar(18)**|Gesamtmenge des Speicherplatzes, der von Indizes in *objname*verwendet wird.|  
|**genutzt**|**varchar(18)**|Gesamtmenge des für *objname* reservierten Speicherplatzes, aber noch nicht verwendet.|  
 
Dies ist der Standardmodus, wenn keine Parameter angegeben werden. Die folgenden Resultsets werden in Detailinformationen zur Datenbankgröße auf dem Datenträger zurückgegeben. 

|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|Der Name der aktuellen Datenbank.|  
|**database_size**|**varchar(18)**|Die Größe der aktuellen Datenbank in Megabyte. **database_size** schließt sowohl Daten-als auch Protokolldateien ein. Wenn die Datenbank über eine MEMORY_OPTIMIZED_DATA-Datei Gruppe verfügt, schließt dies die Gesamtgröße aller Prüf Punkt Dateien in der Datei Gruppe auf dem Datenträger ein.|  
|**nicht zugewiesener Speicherplatz**|**varchar(18)**|Speicherplatz in der Datenbank, der nicht für Datenbankobjekte zugeordnet wurde. Wenn die Datenbank über eine MEMORY_OPTIMIZED_DATA-Datei Gruppe verfügt, schließt dies die Gesamtgröße der Prüf Punkt Dateien auf dem Datenträger ein, deren Status in der Datei Gruppe vorab erstellt wurde.|  

Speicherplatz, der von Tabellen in der Datenbank verwendet wird: (dieses Resultset spiegelt keine Speicher optimierten Tabellen wider, da es keine Tabellen übergreifende Erfassung der Datenträger Verwendung gibt) 

|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**bleiben**|**varchar(18)**|Gesamter von Objekten in der Datenbank zugeordneter Speicherplatz.|  
|**data**|**varchar(18)**|Gesamter für Daten verwendeter Speicherplatz.|  
|**index_size**|**varchar(18)**|Gesamter für Indizes verwendeter Speicherplatz.|  
|**genutzt**|**varchar(18)**|Gesamter für Objekte in der Datenbank zugeordneter, aber noch nicht verwendeter Speicherplatz.|

Das folgende Resultset wird **nur** zurückgegeben, wenn die Datenbank über eine MEMORY_OPTIMIZED_DATA-Datei Gruppe mit mindestens einem Container verfügt: 

|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**xtp_precreated**|**varchar(18)**|Gesamtgröße der Prüf Punkt Dateien, für die der Status vorab erstellt wurde, in KB. Wird in Bezug auf den nicht zugeordneten Speicherplatz in der Datenbank als Ganzes gezählt. [Wenn z. b. 600.000 KB vorab erstellte Prüf Punkt Dateien vorhanden sind, enthält diese Spalte "600000 KB"].|  
|**xtp_used**|**varchar(18)**|Gesamtgröße der Prüf Punkt Dateien mit Zuständen, die in Bearbeitung, aktiv und Zusammenschluss Ziel in KB liegen. Dies ist der Speicherplatz, der für Daten in Speicher optimierten Tabellen aktiv verwendet wird.|  
|**xtp_pending_truncation**|**varchar(18)**|Gesamtgröße der Prüf Punkt Dateien mit dem Status WAITING_FOR_LOG_TRUNCATION in KB. Dies ist der Speicherplatz, der für Prüf Punkt Dateien verwendet wird, die auf eine Bereinigung warten, sobald das Abschneiden des Protokolls erfolgt ist.|

Wenn *objname* weggelassen wird, ist der Wert von oneresultset 1, und *include_total_xtp_storage* ist 1. das folgende einzelne Resultset wird zurückgegeben, um aktuelle Informationen zur Datenbankgröße bereitzustellen. Wenn `include_total_xtp_storage` 0 (Standard) ist, werden die letzten drei Spalten weggelassen. 

|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|Der Name der aktuellen Datenbank.|  
|**database_size**|**varchar(18)**|Die Größe der aktuellen Datenbank in Megabyte. **database_size** schließt sowohl Daten-als auch Protokolldateien ein. Wenn die Datenbank über eine MEMORY_OPTIMIZED_DATA-Datei Gruppe verfügt, schließt dies die Gesamtgröße aller Prüf Punkt Dateien in der Datei Gruppe auf dem Datenträger ein.|
|**nicht zugewiesener Speicherplatz**|**varchar(18)**|Speicherplatz in der Datenbank, der nicht für Datenbankobjekte zugeordnet wurde. Wenn die Datenbank über eine MEMORY_OPTIMIZED_DATA-Datei Gruppe verfügt, schließt dies die Gesamtgröße der Prüf Punkt Dateien auf dem Datenträger ein, deren Status in der Datei Gruppe vorab erstellt wurde.|  
|**bleiben**|**varchar(18)**|Gesamter von Objekten in der Datenbank zugeordneter Speicherplatz.|  
|**data**|**varchar(18)**|Gesamter für Daten verwendeter Speicherplatz.|  
|**index_size**|**varchar(18)**|Gesamter für Indizes verwendeter Speicherplatz.|  
|**genutzt**|**varchar(18)**|Gesamter für Objekte in der Datenbank zugeordneter, aber noch nicht verwendeter Speicherplatz.|
|**xtp_precreated**|**varchar(18)**|Gesamtgröße der Prüf Punkt Dateien, für die der Status vorab erstellt wurde, in KB. Dies zählt in Bezug auf den nicht zugeordneten Speicherplatz in der Datenbank als Ganzes. Gibt NULL zurück, wenn die Datenbank nicht über eine memory_optimized_data-Datei Gruppe mit mindestens einem Container verfügt. *Diese Spalte ist nur enthalten, wenn @include_total_xtp_storage = 1 ist*.| 
|**xtp_used**|**varchar(18)**|Gesamtgröße der Prüf Punkt Dateien mit Zuständen, die in Bearbeitung, aktiv und Zusammenschluss Ziel in KB liegen. Dies ist der Speicherplatz, der für Daten in Speicher optimierten Tabellen aktiv verwendet wird. Gibt NULL zurück, wenn die Datenbank nicht über eine memory_optimized_data-Datei Gruppe mit mindestens einem Container verfügt. *Diese Spalte ist nur enthalten, wenn @include_total_xtp_storage = 1 ist*.| 
|**xtp_pending_truncation**|**varchar(18)**|Gesamtgröße der Prüf Punkt Dateien mit dem Status WAITING_FOR_LOG_TRUNCATION in KB. Dies ist der Speicherplatz, der für Prüf Punkt Dateien verwendet wird, die auf eine Bereinigung warten, sobald das Abschneiden des Protokolls erfolgt ist. Gibt NULL zurück, wenn die Datenbank nicht über eine memory_optimized_data-Datei Gruppe mit mindestens einem Container verfügt. Diese Spalte ist nur enthalten, wenn `@include_total_xtp_storage=1`.|

## <a name="remarks"></a>Hinweise  
 **database_size** ist immer größer als die Summe von **reserviertem** + **nicht zugeordnetem Speicherplatz** , da Sie die Größe der Protokolldateien enthält, aber **reserviert** und **unallocated_space** nur Datenseiten berücksichtigt.  
  
 Seiten, die von XML-Indizes und Volltextindizes verwendet werden, sind in **index_size** für beide Resultsets enthalten. Wenn *objname* angegeben ist, werden die Seiten für die XML-Indizes und Volltextindizes für das Objekt auch in den Ergebnissen für **reservierte** und **index_size** Gesamt gezählt.  
  
 Wenn die Speicherplatz Verwendung für eine Datenbank oder ein Objekt mit einem räumlichen Index berechnet wird, enthalten die Spalten mit der Größe des Speicherplatzes, wie z. b. **database_size**, **reserved**und **index_size**, die Größe des räumlichen Indexes.  
  
 Wenn *UPDATEUSAGE* angegeben ist, durchsucht der [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] die Datenseiten in der Datenbank und nimmt alle erforderlichen Korrekturen an den Katalog Sichten **sys. allocation_units** und **sys. Partitions** in Bezug auf den Speicherplatz vor, der von den einzelnen Tabellen verwendet wird. In einigen Situationen, z. B. nachdem ein Index gelöscht wurde, entsprechen die Speicherplatzinformationen für die Tabelle möglicherweise nicht dem aktuellen Stand. die Ausführung von *UPDATEUSAGE* kann für große Tabellen oder Datenbanken einige Zeit in Anspruch nehmen. Verwenden Sie *UPDATEUSAGE* nur dann, wenn Sie vermuten, dass falsche Werte zurückgegeben werden, und wenn der Prozess keine negativen Auswirkungen auf andere Benutzer oder Prozesse in der Datenbank hat. DBCC UPDATEUSAGE kann auch separat ausgeführt werden.  
  
> [!NOTE]  
>  Wenn Sie große Indizes löschen oder neu erstellen bzw. wenn Sie große Tabellen löschen oder abschneiden, verzögert [!INCLUDE[ssDE](../../includes/ssde-md.md)] die Aufhebung der aktuellen Seitenzuordnungen sowie die zugehörigen Sperren, bis für die Transaktion ein Commit ausgeführt wird. Bei verzögerten Löschvorgängen wird der zugeordnete Speicherplatz nicht sofort freigegeben. Daher spiegeln die von **sp_spaceused** zurückgegebenen Werte unmittelbar nach dem Löschen oder Abschneiden eines großen Objekts möglicherweise nicht den tatsächlich verfügbaren Speicherplatz wider.  
  
## <a name="permissions"></a>Berechtigungen  
 Die Berechtigung zum Ausführen von **sp_spaceused** wird der **public** -Rolle erteilt. Nur Mitglieder der Daten Bank Rolle **db_owner** können den Parameter **\@updateusage** angeben.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-displaying-disk-space-information-about-a-table"></a>A. Anzeigen von Speicherplatzinformationen für eine Tabelle  
 Im folgenden Beispiel werden Speicherplatzinformationen für die `Vendor`-Tabelle und deren Indizes abgerufen.  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_spaceused N'Purchasing.Vendor';  
GO  
```  
  
### <a name="b-displaying-updated-space-information-about-a-database"></a>B. Anzeigen aktualisierter Speicherplatzinformationen für eine Datenbank  
 Das folgende Beispiel ermöglicht eine Zusammenfassung des in der aktuellen Datenbank verwendeten Speicherplatzes. Durch Verwendung des optionalen Parameters `@updateusage` wird sichergestellt, dass aktuelle Werte zurückgegeben werden.  
  
```sql  
USE AdventureWorks008R2;  
GO  
EXEC sp_spaceused @updateusage = N'TRUE';  
GO  
```  
  
### <a name="c-displaying-space-usage-information-about-the-remote-table-associated-with-a-stretch-enabled-table"></a>C. Anzeigen von Speicherplatz Verwendungs Informationen über die Remote Tabelle, die einer Stretch-aktivierten Tabelle zugeordnet ist  
 Im folgenden Beispiel wird der von der Remote Tabelle, die einer Stretch-fähigen Tabelle zugeordnet ist, verwendete Speicherplatz zusammengefasst, indem das **-Argument \@mode** verwendet wird, um das Remote Ziel anzugeben. Weitere Informationen finden Sie unter [Stretch Database](../../sql-server/stretch-database/stretch-database.md).  
  
```sql  
USE StretchedAdventureWorks2016  
GO  
EXEC sp_spaceused N'Purchasing.Vendor', @mode = 'REMOTE_ONLY'  
```  
  
### <a name="d-displaying-space-usage-information-for-a-database-in-a-single-result-set"></a>D. Anzeigen von Speicherplatz Verwendungs Informationen für eine Datenbank in einem einzelnen Resultset  
 Im folgenden Beispiel wird die Speicherplatz Verwendung für die aktuelle Datenbank in einem einzelnen Resultset zusammengefasst.  
  
```sql  
USE AdventureWorks2016  
GO  
EXEC sp_spaceused @oneresultset = 1  
```  

### <a name="e-displaying-space-usage-information-for-a-database-with-at-least-one-memory_optimized-file-group-in-a-single-result-set"></a>E. Anzeigen von Speicherplatz Verwendungs Informationen für eine Datenbank mit mindestens einer MEMORY_OPTIMIZED-Datei Gruppe in einem einzelnen Resultset 
 Im folgenden Beispiel wird die Speicherplatz Verwendung für die aktuelle Datenbank mit mindestens einer MEMORY_OPTIMIZED-Datei Gruppe in einem einzelnen Resultset zusammengefasst.
 
```sql
USE WideWorldImporters
GO
EXEC sp_spaceused @updateusage = 'FALSE', @mode = 'ALL', @oneresultset = '1', @include_total_xtp_storage = '1';
GO
``` 

### <a name="f-displaying-space-usage-information-for-a-memory_optimized-table-object-in-a-database"></a>F. Anzeigen von Informationen zur Speicherplatz Verwendung für ein MEMORY_OPTIMIZED Table-Objekt in einer Datenbank.
 Im folgenden Beispiel wird die Speicherplatz Verwendung für ein MEMORY_OPTIMIZED Table-Objekt in der aktuellen Datenbank mit mindestens einer MEMORY_OPTIMIZED-Datei Gruppe zusammengefasst.
 
```sql
USE WideWorldImporters
GO
EXEC sp_spaceused
@objname = N'VehicleTemparatures',
@updateusage = 'FALSE',
@mode = 'ALL',
@oneresultset = '0',
@include_total_xtp_storage = '1';
GO
```  

## <a name="see-also"></a>Siehe auch  
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [DBCC UPDATEUSAGE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-updateusage-transact-sql.md)   
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)   
 [sys.allocation_units &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
