---
title: Sp_filestream_force_garbage_collection (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/22/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_filestream_force_garbage_collection
- sp_filestream_force_garbage_collection_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- FILESTREAM [SQL Server]
- sp_filestream_force_garbage_collection
ms.assetid: 9d1efde6-8fa4-42ac-80e5-37456ffebd0b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 350c007c8a0153f2dfd0f84d596110b3dea29500
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47733418"
---
# <a name="spfilestreamforcegarbagecollection-transact-sql"></a>sp_filestream_force_garbage_collection (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Erzwingt die Ausführung des FILESTREAM-Garbage Collectors und löscht alle nicht benötigten FILESTREAM-Dateien.  
  
 Ein FILESTREAM-Container kann erst entfernt werden, wenn alle gelöschten Dateien darin vom Garbage Collector bereinigt wurden. Der FILESTREAM Garbage Collector wird automatisch ausgeführt. Allerdings wird bei Bedarf so entfernen Sie einen Container, vor der Garbage Collector ausgeführt wurde, können Sie Sp_filestream_force_garbage_collection der Garbage Collector manuell ausführen.  
  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_filestream_force_garbage_collection  
    [ @dbname = ]  'database_name',  
    [ @filename = ] 'logical_file_name' ]  
```  
  
## <a name="arguments"></a>Argumente  
 **@dbname** = *database_name***'**  
 Gibt den Namen der Datenbank an, für die der Garbage Collector ausgeführt werden soll.  
  
> [!NOTE]  
>  *Dbname* ist **Sysname**. Fehlt die Angabe, wird die aktuelle Datenbank zugrunde gelegt.  
  
 **@filename** = *logical_file_name*  
 Gibt den logischen Namen des FILESTREAM-Containers an, für den der Garbage Collector ausgeführt werden soll. **@filename** ist optional. Wenn kein logischer Dateiname angegeben wird, bereinigt der Garbage Collector alle FILESTREAM-Container in der angegebenen Datenbank.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
  
|||  
|-|-|  
|value|Description|  
|0|Vorgang war erfolgreich.|  
|1|Fehler beim Vorgang.|  
  
## <a name="result-sets"></a>Resultsets  
  
|value|Description|  
|-----------|-----------------|  
|*file_name*|Gibt den Namen des FILESTREAM-Containers an|  
|*num_collected_items*|Gibt die Anzahl der FILESTREAM-Elemente (Dateien/Verzeichnisse) an, die vom Garbage Collector in diesem Container erfasst (gelöscht) wurden.|  
|*num_marked_for_collection_items*|Gibt die Anzahl der FILESTREAM-Elemente (Dateien/Verzeichnisse) an, die für den Garbage Collector in diesem Container markiert wurden. Diese Elemente wurden nicht gelöscht wurde, aber möglicherweise zum Löschen, befolgen die Garbage Collection-Phase.|  
|*num_unprocessed_items*|Gibt die Anzahl der FILESTREAM-Elemente (Dateien oder Verzeichnisse) an, die nicht von der Garbage Collection in diesem FILESTREAM-Container erfasst wurden. Elemente können aus unterschiedlichen Gründen nicht verarbeitet werden:<br /><br /> Dateien, die festgesetzt werden müssen, da noch keine Protokollsicherung oder CheckPoint ausgeführt wurden.<br /><br /> Dateien im FULL- oder BULK_LOGGED-Wiederherstellungsmodell.<br /><br /> Es liegt eine aktive Transaktion mit langer Ausführungszeit vor.<br /><br /> Der Replikationsprotokollleser-Auftrag wurde nicht ausgeführt. Finden Sie im Whitepaper [FILESTREAM-Speicher in SQL Server 2008](http://go.microsoft.com/fwlink/?LinkId=209156) für Weitere Informationen.|  
|*last_collected_xact_seqno*|Gibt die letzte Sequenznummer (LSN) für den entsprechenden FILESTREAM-Container an, bis zu der die Dateien von der Garbage Collection erfasst wurden.|  
  
## <a name="remarks"></a>Hinweise  
 Führt den FILESTREAM-Garbage Collector für die betreffende Datenbank (und den FILESTREAM-Container) vollständig aus. Dateien, die nicht mehr benötigt werden, werden vom Garbage Collection-Prozess entfernt. Die Zeit, die benötigt wird, damit dieser Vorgang abgeschlossen werden kann, hängt vom Umfang der FILESTREAM-Daten in dieser Datenbank oder in diesem Container sowie vom Ausmaß der DML-Aktivität im Zusammenhang mit den FILESTREAM-Daten in jüngster Zeit ab. Diese Vorgang kann auch ausgeführt werden, während die Datenbank online ist. Dies kann sich jedoch aufgrund verschiedener E/A-Aktivitäten im Rahmen der Garbage Collection auf die Leistung der Datenbank auswirken.  
  
> [!NOTE]  
>  Es wird empfohlen, diesen Vorgang nur bei Bedarf und außerhalb der üblichen Betriebsstunden auszuführen.  
  
Mehrere Aufrufe dieser gespeicherten Prozedur können nur in separaten Containern oder separaten Datenbanken gleichzeitig ausgeführt werden.  

2-Phasen-Vorgängen ausgelöst wurden sollte die gespeicherte Prozedur ausgeführt werden, zweimal aus, um tatsächlich zugrunde liegenden Filestream-Dateien gelöscht.  

Garbage Collection (GC) basiert auf Abschneiden des Protokolls. Wenn Dateien in einer Datenbank mithilfe des vollständigen Wiederherstellungsmodells vor kurzem gelöscht wurden, sind daher GC-Ed erst, nachdem eine protokollsicherung der die Transaktion Log Teile stammt, und der Log-Teil wird als inaktiv markiert. In einer Datenbank, das einfache Wiederherstellungsmodell verwendet, tritt ein Abschneiden des Protokolls nach einem `CHECKPOINT` für die Datenbank ausgegeben wurde.  


## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der Datenbankrolle db_owner.  
  
## <a name="examples"></a>Beispiele  
 Die folgenden Beispiele auszuführen, der Garbage Collector für FILESTREAM-Container in der `FSDB` Datenbank.  
  
### <a name="a-specifying-no-container"></a>A. Angeben keines Containers  
  
```sql  
USE FSDB;  
GO  
EXEC sp_filestream_force_garbage_collection @dbname = N'FSDB';  
```  
  
### <a name="b-specifying-a-container"></a>B. Angeben eines Containers  
  
```sql  
USE FSDB;  
GO  
EXEC sp_filestream_force_garbage_collection @dbname = N'FSDB',
    @filename = N'FSContainer';  
```  
  
## <a name="see-also"></a>Siehe auch  
[FileStream](../../relational-databases/blob/filestream-sql-server.md)
<br>[Filetables](../../relational-databases/blob/filetables-sql-server.md)
<br>[Dynamische Verwaltungssichten für Filestream und FileTable (Transact-SQL)](../system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)
<br>[Katalogsichten für Filestream und FileTable (Transact-SQL)](../system-catalog-views/filestream-and-filetable-catalog-views-transact-sql.md)
<br>[Sp_kill_filestream_non_transacted_handles (Transact-SQL)](filestream-and-filetable-sp-kill-filestream-non-transacted-handles.md)
  
  
