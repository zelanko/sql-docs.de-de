---
title: sp_syscollector_create_collection_item (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_create_collection_item
- sp_syscollector_create_collection_item_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_create_collection_item
- data collector [SQL Server], stored procedures
ms.assetid: 60dacf13-ca12-4844-b417-0bc0a8bf0ddb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c5973cd5560f9c12bc38f58002cd6707fe71c714
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85725607"
---
# <a name="sp_syscollector_create_collection_item-transact-sql"></a>sp_syscollector_create_collection_item (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Erstellt ein Sammelelement in einem benutzerdefinierten Sammlungssatz. Ein Sammelelement definiert die zu sammelnden Daten und die Häufigkeit, mit der die Daten gesammelt werden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syscollector_create_collection_item   
      [ @collection_set_id = ] collection_set_id   
    , [ @collector_type_uid = ] 'collector_type_uid'  
    , [ @name = ] 'name'   
    , [ [ @frequency = ] frequency ]  
    , [ @parameters = ] 'parameters'  
    , [ @collection_item_id = ] collection_item_id OUTPUT  
```  
  
## <a name="arguments"></a>Argumente  
 [ @collection_set_id =] *collection_set_id*  
 Der eindeutige lokale Bezeichner für den Sammlungssatz. *collection_set_id* ist vom Datentyp **int**.  
  
 [ @collector_type_uid =] '*collector_type_uid*'  
 Der GUID, der den Sammlertyp identifiziert, der für dieses Element verwendet werden soll *collector_type_uid* ist vom Datentyp **uniqueidentifier** und hat keinen Standardwert. Um eine Liste von Sammlertypen zu erhalten, fragen Sie die syscollector_collector_types-Systemsicht ab.  
  
 [ @name =] '*Name*'  
 Der Name des Sammelelements. *Name ist vom Datentyp* **vom Datentyp sysname** und darf keine leere Zeichenfolge oder NULL sein.  
  
 der *Name* muss eindeutig sein. Wenn Sie eine Liste der aktuellen Namen von Sammelelementen abrufen möchten, fragen Sie die syscollector_collection_items-Systemsicht ab.  
  
 [ @frequency =] *Häufigkeit*  
 Mithilfe dieses Parameters wird angegeben (in Sekunden), wie häufig Daten durch dieses Sammelelement aufgezeichnet werden. *Frequency* ist vom Datentyp **int**und hat den Standardwert 5. Der minimale Wert, der angegeben werden kann, ist 5 Sekunden.  
  
 Wenn der Sammlungssatz auf den Modus ohne Zwischenspeicherung festgelegt ist, wird die Häufigkeit ignoriert, da dieser Modus bewirkt, dass sowohl die Datensammlung als auch der Datenupload dem Zeitplan entsprechend stattfinden, der für den Sammlungssatz angegeben wurde. Um den Sammlungs Modus des Sammlungs Satzes anzuzeigen, Fragen Sie die [syscollector_collection_sets](../../relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql.md) Systemsicht ab.  
  
 [ @parameters =] '*Parameter*'  
 Die Eingabeparameter für den Sammlertyp. *Parameter* ist vom Typ **XML** und hat den Standardwert NULL. Das *Parameter* Schema muss dem Parameter Schema des Sammler Typs entsprechen.  
  
 [ @collection_item_id =] *collection_item_id*  
 Der eindeutige Bezeichner für das Sammlungssatzelement. *collection_item_id* ist vom Datentyp **int** und hat eine Ausgabe.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 sp_syscollector_create_collection_item muss im Kontext der msdb-Systemdatenbank ausgeführt werden.  
  
 Der Sammlungssatz, dem das Sammelelement hinzugefügt wird, muss beendet werden, bevor das Sammelelement erstellt wird. Systemsammlungssätzen können keine Sammelelemente hinzugefügt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Damit diese Prozedur ausgeführt werden kann, ist die Mitgliedschaft in der festen Datenbankrolle dc_admin (mit EXECUTE-Berechtigung) erforderlich.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird ein Sammelelement auf Grundlage des Sammlungstyps `Generic T-SQL Query Collector Type` erstellt und dem Sammlungssatz `Simple collection set test 2` hinzugefügt. Um den angegebenen Sammlungs Satz zu erstellen, führen Sie Beispiel B in [sp_syscollector_create_collection_set &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-set-transact-sql.md)aus.  
  
```  
USE msdb;  
GO  
DECLARE @collection_item_id int;  
DECLARE @collection_set_id int = (SELECT collection_set_id   
                                  FROM syscollector_collection_sets  
                                  WHERE name = N'Simple collection set test 2');  
DECLARE @collector_type_uid uniqueidentifier =   
    (SELECT collector_type_uid  
     FROM syscollector_collector_types  
     WHERE name = N'Generic T-SQL Query Collector Type');  
DECLARE @params xml =   
    CONVERT(xml, N'\<ns:TSQLQueryCollector xmlns:ns="DataCollectorType">  
            <Query>  
                <Value>SELECT * FROM sys.objects</Value>  
                <OutputTable>MyOutputTable</OutputTable>  
            </Query>  
            <Databases>   
                <Database> UseSystemDatabases = "true"   
                           UseUserDatabases = "true"  
                </Database>  
            </Databases>  
         \</ns:TSQLQueryCollector>');  
  
EXEC sp_syscollector_create_collection_item  
    @collection_set_id = @collection_set_id,  
    @collector_type_uid = @collector_type_uid,  
    @name = 'My custom TSQL query collector item',  
    @frequency = 6000,  
    @parameters = @params,  
    @collection_item_id = @collection_item_id OUTPUT;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Datensammlung](../../relational-databases/data-collection/data-collection.md)   
 [sp_syscollector_update_collection_item &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-update-collection-item-transact-sql.md)   
 [sp_syscollector_delete_collection_item &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-delete-collection-item-transact-sql.md)   
 [syscollector_collector_types &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/syscollector-collector-types-transact-sql.md)   
 [sp_syscollector_create_collection_set &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-set-transact-sql.md)   
 [syscollector_collection_items &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-collection-items-transact-sql.md)  
  
  
