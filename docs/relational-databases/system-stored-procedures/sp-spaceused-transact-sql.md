---
title: Sp_spaceused (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_spaceused_TSQL
- sp_spaceused
dev_langs:
- TSQL
helpviewer_keywords:
- sp_spaceused
ms.assetid: c6253b48-29f5-4371-bfcd-3ef404060621
caps.latest.revision: 62
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6dc2878c9a913b5bb95ef32c9f00a6e7b1e94520
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43089383"
---
# <a name="spspaceused-transact-sql"></a>sp_spaceused (Transact-SQL)
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

Für [!INCLUDE[sssdw-md](../../includes/sssdw-md.md)] und [!INCLUDE[sspdw-md](../../includes/sspdw-md.md)], `sp_spaceused` müssen benannten Parameter angeben (z. B. `sp_spaceused (@objname= N'Table1');` statt nach der Position von Parametern. 

 [ **@objname=**] **'***objname***'** 
   
 Der qualifizierte oder nicht qualifizierte Name der Tabelle, indizierten Sicht oder Warteschlange, für die Informationen zur Speicherverwendung angefordert werden. Anführungszeichen sind nur erforderlich, wenn ein qualifizierter Objektname angegeben wird. Bei Angabe eines vollqualifizierten Objektnamens (einschließlich eines Datenbanknamens) muss der Datenbankname der Name der aktuellen Datenbank sein.  
Wenn *Objname* nicht angegeben ist, werden die Ergebnisse für die gesamte Datenbank zurückgegeben.  
*Objname* ist **nvarchar(776)**, hat den Standardwert NULL.  
> [!NOTE]  
> [!INCLUDE[sssdw-md](../../includes/sssdw-md.md)] und [!INCLUDE[sspdw-md](../../includes/sspdw-md.md)] unterstützen nur die Datenbank und Tabelle.
  
 [ **@updateusage=**] **'***updateusage***'**  
 Gibt an, dass DBCC UPDATEUSAGE ausgeführt werden soll, um die Informationen zur Speicherplatzverwendung zu aktualisieren. Wenn *Objname* ist nicht angegeben ist, die Anweisung wird für die gesamte Datenbank ausgeführt; andernfalls wird die Anweisung ausgeführt, auf *Objname*. Werte sind möglich **"true"** oder **"false"**. *UPDATEUSAGE* ist **varchar(5)**, hat den Standardwert **"false"**.  
  
 [ **@mode=**] **'***mode***'**  
 Gibt den Bereich der Ergebnisse an. Für eine gestreckte Tabelle oder Datenbank die *Modus* -Parameter können Sie ein- oder Ausschließen von des remote-Teils des Objekts. Weitere Informationen finden Sie unter [Stretch Database](../../sql-server/stretch-database/stretch-database.md).  
  
 Die *Modus* Argument kann die folgenden Werte haben:  
  
|value|Description|  
|-----------|-----------------|  
|ALL|Gibt die Statistiken der Speicher des Objekts oder der Datenbank, einschließlich der remote-Teil und den lokalen Teil.|  
|LOCAL_ONLY|Gibt die Speicher-Statistiken, nur den lokalen Teil des Objekts oder der Datenbank. Wenn das Objekt oder die Datenbank nicht für Stretch aktiviert ist, gibt diese statistischen Daten wie @mode = ALL.|  
|REMOTE_ONLY|Gibt die Statistiken der Speicher nur für den remote Teil des Objekts oder der Datenbank. Diese Option löst einen Fehler auf, wenn eine der folgenden Bedingungen zutrifft:<br /><br /> In der Tabelle ist nicht für die Streckung aktiviert.<br /><br /> In der Tabelle für Stretch aktiviert ist, aber Sie niemals die Datenmigration aktiviert haben. In diesem Fall die Remotetabelle noch ein Schema keinen.<br /><br /> Der Benutzer wurde die Remotetabelle manuell gelöscht werden.<br /><br /> Die Bereitstellung von der remote Data Archive Status erfolgreich zurückgegeben, aber in der Tat fehlgeschlagen ist.|  
  
 *Modus* ist **varchar(11)**, hat den Standardwert **kann "**.  
  
 [ **@oneresultset=**] *oneresultset*  
 Gibt an, ob ein einzelnes Resultset zurückgeben. Die *Oneresultset* Argument kann die folgenden Werte haben:  
  
|value|Description|  
|-----------|-----------------|  
|0|Wenn *@objname* ist null oder nicht angegeben ist, werden zwei Resultsets zurückgegeben. Zwei Resultsets ist das Standardverhalten.|  
|1|Wenn *@objname* = Null ' oder ' ist nicht angegeben ist, wird ein einzelnes Resultset zurückgegeben.|  
  
 *Oneresultset* ist **Bit**, hat den Standardwert **0**.  

[ **@include_total_xtp_storage**] **"***Include_total_xtp_storage***"**  
**Gilt für:** [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)], [!INCLUDE[sssds-md](../../includes/sssds-md.md)].  
  
 Wenn @oneresultset= 1, der Parameter @include_total_xtp_storage bestimmt, ob das Resultset der einzelne Spalten für die MEMORY_OPTIMIZED_DATA-Speicher enthält. Der Standardwert 0 (null), ist standardmäßig (wenn der Parameter nicht angegeben ist) die XTP-Spalten sind nicht im Resultset enthalten.  

## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Wenn *Objname* ausgelassen wird und der Wert der *Oneresultset* 0 ist, werden die folgenden Resultsets zurückgegeben, um aktuelle Informationen zur Datenbankgröße bereitzustellen.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|Der Name der aktuellen Datenbank.|  
|**database_size**|**varchar(18)**|Die Größe der aktuellen Datenbank in Megabyte. **Database_size** umfasst sowohl Daten-und Protokolldateien.|  
|**nicht zugewiesener Speicherplatz**|**varchar(18)**|Speicherplatz in der Datenbank, der nicht für Datenbankobjekte zugeordnet wurde.|  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**Reserviert**|**varchar(18)**|Gesamter von Objekten in der Datenbank zugeordneter Speicherplatz.|  
|**data**|**varchar(18)**|Gesamter für Daten verwendeter Speicherplatz.|  
|**index_size**|**varchar(18)**|Gesamter für Indizes verwendeter Speicherplatz.|  
|**nicht verwendete**|**varchar(18)**|Gesamter für Objekte in der Datenbank zugeordneter, aber noch nicht verwendeter Speicherplatz.|  
  
 Wenn *Objname* ausgelassen wird und der Wert der *Oneresultset* 1 ist, die folgenden einzelnen Resultset wird zurückgegeben, um aktuelle Informationen zur Datenbankgröße bereitzustellen.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|Der Name der aktuellen Datenbank.|  
|**database_size**|**varchar(18)**|Die Größe der aktuellen Datenbank in Megabyte. **Database_size** umfasst sowohl Daten-und Protokolldateien.|  
|**nicht zugewiesener Speicherplatz**|**varchar(18)**|Speicherplatz in der Datenbank, der nicht für Datenbankobjekte zugeordnet wurde.|  
|**Reserviert**|**varchar(18)**|Gesamter von Objekten in der Datenbank zugeordneter Speicherplatz.|  
|**data**|**varchar(18)**|Gesamter für Daten verwendeter Speicherplatz.|  
|**index_size**|**varchar(18)**|Gesamter für Indizes verwendeter Speicherplatz.|  
|**nicht verwendete**|**varchar(18)**|Gesamter für Objekte in der Datenbank zugeordneter, aber noch nicht verwendeter Speicherplatz.|  
  
 Wenn *Objname* angegeben ist, wird das folgende Resultset wird zurückgegeben, für das angegebene Objekt.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar(128)**|Name des Objekts, für das Informationen zur Speicherverwendung angefordert wurden.<br /><br /> Der Schemaname des Objekts wird nicht zurückgegeben. Wenn der Schemaname erforderlich ist, verwenden Sie die [Sys. dm_db_partition_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-partition-stats-transact-sql.md) oder [Sys. dm_db_index_physical_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md) dynamische Verwaltungssichten für die entsprechende Größeninformationen abrufen.|  
|**rows**|**char(20)**|Anzahl der Zeilen in der Tabelle. Wenn es sich bei dem angegebenen Objekt um eine [!INCLUDE[ssSB](../../includes/sssb-md.md)]-Warteschlange handelt, wird in dieser Spalte die Anzahl der in der Warteschlange vorhandenen Nachrichten angegeben.|  
|**Reserviert**|**varchar(18)**|Gesamtmenge des reservierten Speicherplatzes für *Objname*.|  
|**data**|**varchar(18)**|Gesamtmenge des Speicherplatzes ein, die Daten in *Objname*.|  
|**index_size**|**varchar(18)**|Gesamtmenge des Speicherplatzes durch Indizes in *Objname*.|  
|**nicht verwendete**|**varchar(18)**|Gesamtmenge des Speicherplatzes für reserviert *Objname* jedoch noch nicht verwendet.|  
 
Dies ist der Standardmodus, wenn keine Parameter angegeben werden. Die folgenden Resultsets werden mit Größeninformationen der Datenbank zurückgegeben. 

|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|Der Name der aktuellen Datenbank.|  
|**database_size**|**varchar(18)**|Die Größe der aktuellen Datenbank in Megabyte. **Database_size** umfasst sowohl Daten-und Protokolldateien. Wenn die Datenbank über eine MEMORY_OPTIMIZED_DATA-Dateigruppe aufweist, enthält dieser die Gesamtgröße auf dem Datenträger, der alle Prüfpunktdateien in der Dateigruppe.|  
|**nicht zugewiesener Speicherplatz**|**varchar(18)**|Speicherplatz in der Datenbank, der nicht für Datenbankobjekte zugeordnet wurde. Wenn die Datenbank über eine MEMORY_OPTIMIZED_DATA-Dateigruppe aufweist, enthält dieser die Gesamtgröße auf dem Datenträger, der mit dem Status vorab erstellten Dateien Prüfpunktdateien in der Dateigruppe.|  

Von Tabellen in der Datenbank belegter Speicherplatz: (dieses Resultset wird nicht angezeigt und speicheroptimierten Tabellen, wie es keine tabellenbasierte Kontoführung der Datenträgerverwendung ist) 

|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**Reserviert**|**varchar(18)**|Gesamter von Objekten in der Datenbank zugeordneter Speicherplatz.|  
|**data**|**varchar(18)**|Gesamter für Daten verwendeter Speicherplatz.|  
|**index_size**|**varchar(18)**|Gesamter für Indizes verwendeter Speicherplatz.|  
|**nicht verwendete**|**varchar(18)**|Gesamter für Objekte in der Datenbank zugeordneter, aber noch nicht verwendeter Speicherplatz.|

Das folgende Resultset wird zurückgegeben, **nur, wenn** die Datenbank verfügt über eine MEMORY_OPTIMIZED_DATA-Dateigruppe mit mindestens einen Container: 

|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**xtp_precreated**|**varchar(18)**|Die Gesamtgröße von Prüfpunktdateien mit vorab erstellten Dateien in KB. Die Anzahl für den freien Speicherplatz in der Datenbank als Ganzes. [Z. B. bei 600.000 KB vorab erstellte Prüfpunktdateien wird diese Spalte enthält 600000 "KB"]|  
|**xtp_used**|**varchar(18)**|Die Gesamtgröße von Prüfpunktdateien mit Status UNDER CONSTRUCTION, ACTIVE und MERGE TARGET in KB. Dies ist der Speicherplatz auf dem Datenträger für Daten in speicheroptimierten Tabellen aktiv verwendet.|  
|**xtp_pending_truncation**|**varchar(18)**|Die Gesamtgröße von Prüfpunktdateien, die mit dem Status WAITING_FOR_LOG_TRUNCATION, in KB. Dies ist der Speicherplatz für die Prüfpunktdateien, die Bereinigung, nachdem die protokollkürzung erfolgt warten verwendet.|

Wenn *Objname* wird weggelassen, ist der Wert des Oneresultset 1, und *Include_total_xtp_storage* 1 ist, die folgenden einzelnen Resultset wird zurückgegeben, um aktuelle Informationen zur Datenbankgröße bereitzustellen. Wenn `include_total_xtp_storage` ist 0 (Standard), die letzten drei Spalten ausgelassen werden. 

|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|Der Name der aktuellen Datenbank.|  
|**database_size**|**varchar(18)**|Die Größe der aktuellen Datenbank in Megabyte. **Database_size** umfasst sowohl Daten-und Protokolldateien. Wenn die Datenbank über eine MEMORY_OPTIMIZED_DATA-Dateigruppe aufweist, enthält dieser die Gesamtgröße auf dem Datenträger, der alle Prüfpunktdateien in der Dateigruppe.|
|**nicht zugewiesener Speicherplatz**|**varchar(18)**|Speicherplatz in der Datenbank, der nicht für Datenbankobjekte zugeordnet wurde. Wenn die Datenbank über eine MEMORY_OPTIMIZED_DATA-Dateigruppe aufweist, enthält dieser die Gesamtgröße auf dem Datenträger, der mit dem Status vorab erstellten Dateien Prüfpunktdateien in der Dateigruppe.|  
|**Reserviert**|**varchar(18)**|Gesamter von Objekten in der Datenbank zugeordneter Speicherplatz.|  
|**data**|**varchar(18)**|Gesamter für Daten verwendeter Speicherplatz.|  
|**index_size**|**varchar(18)**|Gesamter für Indizes verwendeter Speicherplatz.|  
|**nicht verwendete**|**varchar(18)**|Gesamter für Objekte in der Datenbank zugeordneter, aber noch nicht verwendeter Speicherplatz.|
|**xtp_precreated**|**varchar(18)**|Die Gesamtgröße von Prüfpunktdateien mit vorab erstellten Dateien in KB. Dieser Option für den freien Speicherplatz in der Datenbank als Ganzes gezählt. Gibt NULL zurück, wenn die Datenbank nicht mit eine Memory_optimized_data-Dateigruppe mit mindestens einen Container verfügt. *Diese Spalte ist nur enthalten, wenn @include_total_xtp_storage= 1*.| 
|**xtp_used**|**varchar(18)**|Die Gesamtgröße von Prüfpunktdateien mit Status UNDER CONSTRUCTION, ACTIVE und MERGE TARGET in KB. Dies ist der Speicherplatz auf dem Datenträger für Daten in speicheroptimierten Tabellen aktiv verwendet. Gibt NULL zurück, wenn die Datenbank nicht mit eine Memory_optimized_data-Dateigruppe mit mindestens einen Container verfügt. *Diese Spalte ist nur enthalten, wenn @include_total_xtp_storage= 1*.| 
|**xtp_pending_truncation**|**varchar(18)**|Die Gesamtgröße von Prüfpunktdateien, die mit dem Status WAITING_FOR_LOG_TRUNCATION, in KB. Dies ist der Speicherplatz für die Prüfpunktdateien, die Bereinigung, nachdem die protokollkürzung erfolgt warten verwendet. Gibt NULL zurück, wenn die Datenbank nicht mit eine Memory_optimized_data-Dateigruppe mit mindestens einen Container verfügt. Diese Spalte ist nur enthalten, wenn `@include_total_xtp_storage=1`.|

## <a name="remarks"></a>Hinweise  
 **Database_size** ist immer größer als die Summe der **reservierte** + **verfügbaren Speicherplatz** , da es sich um die Größe der Protokolldateien, enthält aber **reserviert**und **Unallocated_space** nur Datenseiten berücksichtigt.  
  
 Die XML-Indizes und Volltextindizes verwendeten Seiten befinden sich im **Index_size** beiden Resultsets. Wenn *Objname* angegeben ist, werden die Seiten für die XML-Indizes und Volltextindizes für das Objekt werden auch in den Gesamtwert gezählt **reservierte** und **Index_size** Ergebnisse.  
  
 Wenn der Speicherplatz berechnet wird, für eine Datenbank oder ein Objekt, das einen räumlichen Index, der die Spalten mit Größenangaben, z. b. **Database_size**, **reservierte**, und **Index_size**, einschließen die Größe des räumlichen Indexes.  
  
 Wenn *Updateusage* angegeben wird, die [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] scannt die Daten in der Datenbank Seiten und macht alle erforderlichen Korrekturen an der **Sys. allocation_units** und **sys.partitions** Katalogsichten in Bezug auf den Speicherplatz, der von den Tabellen verwendeten. In einigen Situationen, z. B. nachdem ein Index gelöscht wurde, entsprechen die Speicherplatzinformationen für die Tabelle möglicherweise nicht dem aktuellen Stand. *UPDATEUSAGE* dauert eine Weile bei großen Tabellen oder Datenbanken ausgeführt. Verwendung *Updateusage* nur wenn Sie vermuten, dass falsche Werte zurückgegeben werden, und wenn die nicht nachteilig auf andere Benutzer oder Prozesse in der Datenbank haben. DBCC UPDATEUSAGE kann auch separat ausgeführt werden.  
  
> [!NOTE]  
>  Beim Löschen oder großer Indizes Neuerstellen, oder löschen oder Abschneiden von großen Tabellen die [!INCLUDE[ssDE](../../includes/ssde-md.md)] verzögert die tatsächlichen aufgehobenen seitenzuordnungen sowie deren zugeordneten sperren, bis die Transaktion ein Commit ausgeführt. Bei verzögerten Löschvorgängen wird der zugeordnete Speicherplatz nicht sofort freigegeben. Aus diesem Grund die Rückgabewerte **Sp_spaceused** unmittelbar nach dem Löschen oder Abschneiden eines großen Objekts nicht den tatsächlich verfügbaren Speicherplatz wider.  
  
## <a name="permissions"></a>Berechtigungen  
 Die Berechtigung zum Ausführen von **sp_spaceused** wird der **public** -Rolle erteilt. Nur Mitglieder der festen Datenbankrolle **db_owner** können den Parameter **@updateusage** angeben.  
  
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
  
### <a name="c-displaying-space-usage-information-about-the-remote-table-associated-with-a-stretch-enabled-table"></a>C. Anzeigen von Informationen zur Speicherplatzverwendung über die remote-Tabelle zugeordnet, dass eine Stretch-aktivierte Tabelle  
 Im folgende Beispiel werden zusammengefasst, den von der Remotetabelle, die eine Stretch-aktivierte Tabelle zugeordnet sind, mithilfe von belegten Speicherplatz dem **@mode** Argument, um dem Remoteziel anzugeben. Weitere Informationen finden Sie unter [Stretch Database](../../sql-server/stretch-database/stretch-database.md).  
  
```sql  
USE StretchedAdventureWorks2016  
GO  
EXEC sp_spaceused N'Purchasing.Vendor', @mode = 'REMOTE_ONLY'  
```  
  
### <a name="d-displaying-space-usage-information-for-a-database-in-a-single-result-set"></a>D. Anzeigen von Informationen zur Speicherplatzverwendung für eine Datenbank in ein einzelnes Ergebnis festlegen  
 Im folgende Beispiel werden die Speicherplatzverwendung für die aktuelle Datenbank in einem einzigen Resultset zusammengefasst.  
  
```sql  
USE AdventureWorks2016  
GO  
EXEC sp_spaceused @oneresultset = 1  
```  

### <a name="e-displaying-space-usage-information-for-a-database-with-at-least-one-memoryoptimized-file-group-in-a-single-result-set"></a>E. Anzeigen von Informationen zur Speicherplatzverwendung für eine Datenbank mit mindestens eine Speicheroptimierte Dateigruppe in einem einzelnen Resultset 
 Im folgende Beispiel werden die Speicherplatzverwendung für die aktuelle Datenbank mit mindestens eine Speicheroptimierte Dateigruppe in einem einzigen Resultset zusammengefasst.
 
```sql
USE WideWorldImporters
GO
EXEC sp_spaceused @updateusage = 'FALSE', @mode = 'ALL', @oneresultset = '1', @include_total_xtp_storage = '1';
GO
``` 

### <a name="f-displaying-space-usage-information-for-a-memoryoptimized-table-object-in-a-database"></a>F. Anzeigen von Informationen zur Speicherplatzverwendung für ein MEMORY_OPTIMIZED-Table-Objekt in einer Datenbank aus.
 Im folgende Beispiel werden die Speicherplatzverwendung für ein MEMORY_OPTIMIZED-Table-Objekt in der aktuellen Datenbank mit mindestens eine Speicheroptimierte Dateigruppe zusammengefasst.
 
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
  
  
