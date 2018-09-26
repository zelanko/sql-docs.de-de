---
title: Sp_estimate_data_compression_savings (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_estimate_data_compression_savings_TSQL
- sp_estimate_data_compression_savings
dev_langs:
- TSQL
helpviewer_keywords:
- compression [SQL Server], estimating
- sp_estimate_data_compression_savings
ms.assetid: 6f6c7150-e788-45e0-9d08-d6c2f4a33729
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 70efe047d1fae61f9755c2dbeecf9627de5b5a79
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2018
ms.locfileid: "46713952"
---
# <a name="spestimatedatacompressionsavings-transact-sql"></a>sp_estimate_data_compression_savings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt die aktuelle Größe des angeforderten Objekts zurück und schätzt die Objektgröße für den angeforderten Komprimierungsstatus. Die Komprimierung kann für ganze Tabellen oder Teile von Tabellen ermittelt werden. Dazu gehören Heaps, gruppierte Indizes, nicht gruppierte Indizes, columnstore-Indizes, indizierte Sichten, Tabelle und Indexpartitionen. Die Objekte können mithilfe der Zeile, Seite, columnstore- oder columnstore-archivkomprimierung komprimiert werden. Wenn die Tabelle, der Index oder die Partition bereits komprimiert ist, können Sie mithilfe dieser Prozedur die Größe der erneut komprimierten Tabelle, des erneut komprimierten Index oder der erneut komprimierten Partition einschätzen.  
  
> [!NOTE]  
>  Komprimierung und **Sp_estimate_data_compression_savings** sind nicht verfügbar in jeder Edition von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Eine Liste der Funktionen, die von den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Editionen unterstützt werden, finden Sie unter [Von den SQL Server 2016-Editionen unterstützte Funktionen](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 Um die Größe des Objekts bei Verwendung der angeforderten Komprimierungseinstellung einzuschätzen, fragt diese gespeicherte Prozedur das Quellobjekt ab und lädt diese Daten in eine entsprechende Tabelle und einen entsprechenden Index in tempdb. Die Tabelle oder der Index, die bzw. der in tempdb erstellt wurde, wird anschließend entsprechend der angeforderten Einstellung komprimiert, und die Komprimierungseinsparungen werden berechnet.  
  
 So ändern Sie den Komprimierungsstatus der eine Tabelle, Index oder Partition, die Verwendung der [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) oder [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md) Anweisungen. Allgemeine Informationen zur Komprimierung finden Sie unter [Datenkomprimierung](../../relational-databases/data-compression/data-compression.md).  
  
> [!NOTE]  
>  Wenn die vorhandenen Daten fragmentiert sind, können Sie ihre Größe möglicherweise ohne Komprimierung verringern, indem Sie den Index neu erstellen. Für Indizes wird der Füllfaktor während der Neuerstellung des Indexes angewendet. Dadurch könnte die Größe des Indexes zunehmen.  

 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_estimate_data_compression_savings   
     [ @schema_name = ] 'schema_name'    
   , [ @object_name = ] 'object_name'   
   , [@index_id = ] index_id   
   , [@partition_number = ] partition_number   
   , [@data_compression = ] 'data_compression'   
[;]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @schema_name=] '*Schema_name*"  
 Der Name des Datenbankschemas, das die Tabelle oder die indizierte Sicht enthält. *Schema_name* ist **Sysname**. Wenn *Schema_name* NULL ist, wird das Standardschema des aktuellen Benutzers verwendet.  
  
 [ @object_name=] '*Object_name*"  
 Der Name der Tabelle oder der indizierten Sicht des Indexes. *database_name* ist vom Datentyp **sysname**.  
  
 [ @index_id=] '*Index_id*"  
 Die ID des Indexes. *Index_id* ist **Int**, und kann einen der folgenden Werte: die ID eines Indexes, NULL oder 0, wenn *Object_id* ein Heap ist. Geben Sie NULL an, wenn Informationen zu allen Indizes für eine Basistabelle oder Sicht zurückgegeben werden sollen. Wenn Sie NULL angeben, müssen Sie auch angeben, auf NULL für *Partition_number*.  
  
 [ @partition_number=] '*Partition_number*"  
 Die Partitionsnummer im Objekt. *Partition_number* ist **Int**, und kann einen der folgenden Werte: die Partitionsnummer eines Indexes oder Heaps, NULL oder 1 für einen nicht partitionierten Index oder Heap.  
  
 Sie können auch angeben, um die Partition anzugeben, die [$partition](../../t-sql/functions/partition-transact-sql.md) Funktion. Geben Sie NULL an, wenn Informationen zu allen Partitionen des besitzenden Objekts zurückgegeben werden sollen.  
  
 [ @data_compression=] '*Data_compression*"  
 Der Typ der Komprimierung, die ausgewertet werden soll. *DATA_COMPRESSION* kann eine der folgenden Werte: keine, Zeile, Seite, COLUMNSTORE und COLUMNSTORE_ARCHIVE.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Das folgende Resultset wird zurückgegeben, damit Informationen zur aktuellen und geschätzten Größe von Tabelle, Index oder Partition bereitgestellt werden.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|object_name|**sysname**|Der Name der Tabelle oder indizierten Sicht.|  
|schema_name|**sysname**|Das Schema der Tabelle oder indizierten Sicht.|  
|index_id|**int**|Index-ID eines Index:<br /><br /> 0 = Heap<br /><br /> 1 = Gruppierter Index<br /><br /> > 1 = Nicht gruppierter Index|  
|partition_number|**int**|Partitionsnummer. Gibt 1 für eine nicht partitionierte Tabelle oder einen Index zurück.|  
|size_with_current_compression_setting (KB)|**bigint**|Die Größe der angeforderten, vorhandenen Tabelle, des Indexes oder der Partition.|  
|size_with_requested_compression_setting (KB)|**bigint**|Die geschätzte Größe der Tabelle, des Indexes oder der Partition, die bzw. der die angeforderte Komprimierungseinstellung verwendet, und der vorhandene Füllfaktor (sofern zutreffend). Zudem wird vorausgesetzt, dass keine Fragmentierung vorliegt.|  
|sample_size_with_current_compression_setting (KB)|**bigint**|Die Größe der Stichprobe mit der aktuellen Komprimierungseinstellung. Dies beinhaltet jegliche Fragmentierung.|  
|sample_size_with_requested_compression_setting (KB)|**bigint**|Die Größe der Stichprobe, die mithilfe der angeforderten Komprimierungseinstellung erstellt wird, mit vorhandenem Füllfaktor (sofern zutreffend) und ohne Fragmentierung.|  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie Sp_estimate_data_compression_savings, um die einsparungen abschätzen, die auftreten können, wenn Sie eine Tabelle oder Partition für die Zeile, Seite, columnstore- oder columnstore-archivkomprimierung aktivieren. Wenn beispielsweise die durchschnittliche Größe der Zeile um 40 Prozent verringert werden kann, können Sie die Größe des Objekts potenziell um 40 Prozent verringern. Möglicherweise erzielen Sie keine Platzeinsparung, weil dies vom Füllfaktor und von der Zeilengröße abhängt. Wenn eine Zeile beispielsweise 8000 Bytes lang ist und Sie die Größe um 40 Prozent verringern, passt weiterhin nur eine Zeile auf eine Datenseite. Daher werden keine Einsparungen erzielt.  
  
 Wenn die Ergebnisse der Ausführung von sp_estimate_data_compression_savings darauf hindeuten, dass sich die Tabelle vergrößert, bedeutet dies, dass für viele Zeilen in der Tabelle fast die gesamte Genauigkeit der Datentypen verwendet wird, und der geringe zusätzliche Verarbeitungsaufwand für das komprimierte Format ist größer als die Einsparungen durch die Komprimierung. Aktivieren Sie in diesem seltenen Fall die Komprimierung nicht.  
  
 Wenn eine Tabelle für eine Komprimierung aktiviert ist, verwenden Sie sp_estimate_data_compression_savings, um die durchschnittliche Größe der Zeile bei nicht komprimierter Tabelle einzuschätzen.  
  
 Eine (IS)-Sperre wird während dieses Vorgangs für die Tabelle abgerufen. Wenn keine (IS)-Sperre abgerufen werden kann, wird die Prozedur blockiert. Die Tabelle wird unter der Read Committed-Isolationsstufe gescannt.  
  
 Wenn die angeforderte Komprimierungseinstellung mit der aktuellen Komprimierungseinstellung identisch ist, gibt die gespeicherte Prozedur die geschätzte Größe ohne Fragmentierung und mit dem vorhandenen Füllfaktor zurück.  
  
 Wenn die Index- oder die Partitions-ID nicht vorhanden ist, werden keine Ergebnisse zurückgegeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die SELECT-Berechtigung für die Tabelle.  
  
## <a name="limitations-and-restrictions"></a>Einschränkungen  
 Vor SQL Server-2019 dieses Verfahren wurde nicht für columnstore-Indizes angewendet, und daher die datenkomprimierungsparameter COLUMNSTORE und COLUMNSTORE_ARCHIVE nicht akzeptiert hat.  Ab SQL Server-2019, können columnstore-Indizes ein Quellobjekt, für die Schätzung, sowohl als einen Typ für die angeforderte komprimierungseinstellung verwendet werden.

## <a name="considerations-for-columnstore-indexes"></a>Überlegungen für columnstore-Indizes
 Beginnend mit SQL Server-2019, Sp_estimate_compression_savings unterstützt das Schätzen der sowohl für columnstore-als auch für columnstore-archivkomprimierung. Im Gegensatz zu Seiten- und zeilenkomprimierung erfordert das Anwenden von columnstore-Komprimierung auf ein Objekt einen neuen columnstore-Index. Aus diesem Grund bei Verwendung der Optionen COLUMNSTORE und COLUMNSTORE_ARCHIVE dieses Verfahrens bestimmt der Typ des Quellobjekts bereitgestellt, um die Prozedur den Typ des columnstore-Index für die komprimierte größenschätzung verwendet. Die folgende Tabelle zeigt den Verweis Objekten, die zum Schätzen der komprimierungseinsparungen für jedes Objekt verwendet werden. Geben Sie bei der @data_compression Parameter auf columnstore- oder die COLUMNSTORE_ARCHIVE festgelegt ist.

 |Quellobjekt|Verweis-Objekt|
 |-----------------|---------------|
 |Heap|Gruppierter Columnstore-Index|
 |Gruppierter Index|Gruppierter Columnstore-Index|
 |Nicht gruppierter index|Nicht gruppierte columnstore-Index (einschließlich der Schlüsselspalten und des angegebenen nicht gruppierten Indexes eingeschlossen Spalten sowie die Partitionsspalte der Tabelle, sofern vorhanden)|
 |Nicht gruppierter columnstore-Index|Nicht gruppierte columnstore-Index (einschließlich die gleichen Spalten wie der angegebene nicht gruppierte columnstore-Index)|
 |Gruppierter Columnstore-Index|Gruppierter Columnstore-Index|

> [!NOTE]  
> Wenn der columnstore-Komprimierung von einem Rowstore-Quellobjekt (gruppierter Index, nicht gruppierten Index oder Heap) zu schätzen, wenn es werden alle Spalten im Quellobjekt, die einen Datentyp aufweisen, der nicht in einem columnstore-Index Sp_estimate_compression_ unterstützt wird Fehler bei der einsparungen.

 Auf ähnliche Weise, wenn die @data_compression Parameter ist auf NONE, ROW oder PAGE festgelegt und das Quellobjekt ein columnstore-Index, in der folgende Tabelle wird beschrieben, die Verweisobjekte verwendet.

 |Quellobjekt|Verweis-Objekt|
 |-----------------|---------------|
 |Gruppierter Columnstore-Index|Heap|
 |Nicht gruppierter columnstore-Index|Nicht gruppierte Index (einschließlich ggf. als eingeschlossene Spalte in den nicht gruppierten columnstore-Index als Schlüsselspalten und die Partitionsspalte der Tabelle enthaltenen Spalten)|

> [!NOTE]  
> Wenn von einem columnstore-Quellobjekt Rowstore-Komprimierung (NONE, Zeile oder Seite) zu schätzen, achten Sie darauf, dass der Quellindex nicht mehr als 32 Spalten enthält, wie dadurch das Limit in einen Rowstore-Index (nicht gruppiert) unterstützt wird.
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Größe der `Production.WorkOrderRouting`-Tabelle geschätzt, wenn sie mit der `ROW`-Komprimierung komprimiert wird.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_estimate_data_compression_savings 'Production', 'WorkOrderRouting', NULL, NULL, 'ROW' ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [sys.partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [Datenbank-Engine gespeicherten Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Implementierung von Unicode-Komprimierung](../../relational-databases/data-compression/unicode-compression-implementation.md)  
  
  
