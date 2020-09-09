---
description: sp_syscollector_create_collection_set (Transact-SQL)
title: sp_syscollector_create_collection_set (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_create_collection_set_TSQL
- sp_syscollector_create_collection_set
dev_langs:
- TSQL
helpviewer_keywords:
- data collector [SQL Server], stored procedures
- sp_syscollector_create_collection_set
ms.assetid: 69e9ff0f-c409-43fc-89f6-40c3974e972c
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5c2f62ec06ebda9c7c22ec381f4b9b5a3011cc4f
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89547359"
---
# <a name="sp_syscollector_create_collection_set-transact-sql"></a>sp_syscollector_create_collection_set (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Erstellt einen neuen Sammlungssatz. Sie können diese gespeicherte Prozedur verwenden, um einen benutzerdefinierten Sammlungssatz für die Datensammlung zu erstellen.  
  
> [!WARNING]  
>  Falls das als Proxy konfigurierte Windows-Konto einem nicht interaktiven oder interaktiven Benutzer entspricht, der noch nicht angemeldet ist, ist das Profilverzeichnis nicht vorhanden, und die Erstellung des Stagingverzeichnisses schlägt in dem Fall fehl. Verwenden Sie ein Proxykonto auf einem Domänencontroller, müssen Sie also ein interaktives Konto angeben, das mindestens einmal verwendet wurde. So lässt sich sicherstellen, dass das Profilverzeichnis erstellt wurde.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syscollector_create_collection_set   
      [ @name = ] 'name'  
    , [ [ @target = ] 'target' ]  
    , [ [ @collection_mode = ] collection_mode ]  
    , [ [ @days_until_expiration = ] days_until_expiration ]  
    , [ [ @proxy_id = ] proxy_id ]  
    , [ [ @proxy_name = ] 'proxy_name' ]  
    , [ [ @schedule_uid = ] 'schedule_uid' ]  
    , [ [ @schedule_name = ] 'schedule_name' ]  
    , [ [ @logging_level = ] logging_level ]  
    , [ [ @description = ] 'description' ]  
    , [ @collection_set_id = ] collection_set_id OUTPUT   
    , [ [ @collection_set_uid = ] 'collection_set_uid' OUTPUT ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @name = ] 'name'` Der Name des Sammlungs Satzes. *Name ist vom Datentyp* **vom Datentyp sysname** und darf keine leere Zeichenfolge oder NULL sein.  
  
 der *Name* muss eindeutig sein. Wenn Sie eine Liste der aktuellen Namen von Sammlungssätzen abrufen möchten, fragen Sie die syscollector_collection_sets-Systemsicht ab.  
  
`[ @target = ] 'target'` Reserviert für zukünftige Verwendung. *Name ist vom Datentyp* **nvarchar (128)** und hat den Standardwert NULL.  
  
`[ @collection_mode = ] collection_mode` Gibt die Art und Weise an, in der die Daten gesammelt und gespeichert werden. *collection_mode* ist vom Datentyp **smallint** und kann einen der folgenden Werte aufweisen:  
  
 0 - Modus mit Zwischenspeicherung. Für Datensammlung und -upload werden separate Zeitpläne verwendet. Geben Sie den Modus mit Zwischenspeicherung für eine fortlaufende Sammlung an.  
  
 1 - Modus ohne Zwischenspeicherung. Für Datensammlung und -upload wird der gleiche Zeitplan verwendet. Geben Sie den Modus ohne Zwischenspeicherung für eine Ad-hoc-Sammlung oder eine Momentaufnahmesammlung an.  
  
 Der Standardwert für *collection_mode* ist 0 (null). Wenn *collection_mode* 0 ist, müssen *schedule_uid* oder *schedule_name* angegeben werden.  
  
`[ @days_until_expiration = ] days_until_expiration` Gibt an, wie viele Tage die gesammelten Daten im Verwaltungs Data Warehouse gespeichert werden. *days_until_expiration* ist vom Datentyp **smallint** und hat den Standardwert 730 (zwei Jahre). *days_until_expiration* muss 0 oder eine positive ganze Zahl sein.  
  
`[ @proxy_id = ] proxy_id` Ist der eindeutige Bezeichner für ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Proxy Konto des-Agents. *proxy_id* ist vom Datentyp **int** und hat den Standardwert NULL. Wenn angegeben, muss *proxy_name* NULL sein. Fragen Sie die sysproxies-Systemtabelle ab, um *proxy_id*abzurufen. Die feste Datenbankrolle dc_admin muss über die Berechtigung für den Zugriff auf den Proxy verfügen. Weitere Informationen finden Sie unter [Erstellen eines SQL Server-Agent Proxys](../../ssms/agent/create-a-sql-server-agent-proxy.md).  
  
`[ @proxy_name = ] 'proxy_name'` Der Name des Proxy Kontos. *proxy_name* ist vom **Datentyp vom Datentyp sysname** und hat den Standardwert NULL. Wenn angegeben, muss *proxy_id* NULL sein. Fragen Sie die sysproxies-Systemtabelle ab, um *proxy_name*abzurufen.  
  
`[ @schedule_uid = ] 'schedule_uid'` Der GUID, der auf einen Zeitplan zeigt. *schedule_uid* ist vom Datentyp **uniqueidentifier** und hat den Standardwert NULL. Wenn angegeben, muss *schedule_name* NULL sein. Fragen Sie die syszeitpläne-Systemtabelle ab, um *schedule_uid*abzurufen.  
  
 Wenn *collection_mode* auf 0 festgelegt ist, muss *schedule_uid* oder *schedule_name* angegeben werden. Wenn *collection_mode* auf 1 festgelegt ist, wird *schedule_uid* oder *schedule_name* ignoriert, wenn angegeben.  
  
`[ @schedule_name = ] 'schedule_name'` Der Name des Zeitplans. *schedule_name* ist vom **Datentyp vom Datentyp sysname** und hat den Standardwert NULL. Wenn angegeben, muss *schedule_uid* NULL sein. Fragen Sie die syszeitpläne-Systemtabelle ab, um *schedule_name*abzurufen.  
  
`[ @logging_level = ] logging_level` Der Protokolliergrad. *LOGGING_LEVEL* ist vom Datentyp **smallint** und hat einen der folgenden Werte:  
  
 0 – Informationen zur Protokollausführung und zu den [!INCLUDE[ssIS](../../includes/ssis-md.md)]-Ereignissen, die Folgendes nachverfolgen:  
  
-   Starten/Beenden von Samlungssätzen  
  
-   Starten/Beenden von Paketen  
  
-   Fehlerinformationen  
  
 1 - Protokollierung Stufe 0 und:  
  
-   Ausführungsstatistiken  
  
-   Kontinuierliche Ausführung der Sammlung  
  
-   Warnungsereignisse von [!INCLUDE[ssIS](../../includes/ssis-md.md)]  
  
 2 – Protokollierung Stufe 1 sowie ausführliche Ereignisinformationen von [!INCLUDE[ssIS](../../includes/ssis-md.md)].  
  
 Der Standardwert für *LOGGING_LEVEL* ist 1.  
  
`[ @description = ] 'description'` Die Beschreibung des Sammlungs Satzes. die *Beschreibung* ist vom Datentyp **nvarchar (4000)** und hat den Standardwert NULL.  
  
`[ @collection_set_id = ] collection_set_id` Der eindeutige lokale Bezeichner für den Sammlungs Satz. *collection_set_id* ist vom Datentyp **int** mit Output und ist erforderlich.  
  
`[ @collection_set_uid = ] 'collection_set_uid'` Die GUID für den Sammlungs Satz. *collection_set_uid* ist vom Datentyp **uniqueidentifier** mit der Ausgabe mit dem Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 sp_syscollector_create_collection_set muss im Kontext der msdb-Systemdatenbank ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Damit diese Prozedur ausgeführt werden kann, ist die Mitgliedschaft in der festen Datenbankrolle dc_admin (mit EXECUTE-Berechtigung) erforderlich.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-creating-a-collection-set-by-using-default-values"></a>A. Erstellen eines Sammlungssatzes mit Standardwerten  
 Im folgenden Beispiel wird ein Sammlungssatz erstellt, indem nur die erforderlichen Parameter angegeben werden. `@collection_mode` ist nicht erforderlich, aber für den Standardauflistmodus (zwischengespeichert) muss eine Zeitplan-ID oder ein Zeitplanname angegeben werden.  
  
```  
USE msdb;  
GO  
DECLARE @collection_set_id int;  
EXECUTE dbo.sp_syscollector_create_collection_set  
    @name = N'Simple collection set test 1',  
    @description = N'This is a test collection set that runs in non-cached mode.',  
    @collection_mode = 1,  
    @collection_set_id = @collection_set_id OUTPUT;  
GO  
```  
  
### <a name="b-creating-a-collection-set-by-using-specified-values"></a>B. Erstellen eines Sammlungssatzes mit angegebenen Werten  
 Im folgenden Beispiel wird ein Sammlungssatz erstellt, indem Werte für mehrere Parameter angegeben werden.  
  
```  
USE msdb;  
GO  
DECLARE @collection_set_id int;  
DECLARE @collection_set_uid uniqueidentifier;  
SET @collection_set_uid = NEWID();  
EXEC dbo.sp_syscollector_create_collection_set  
    @name = N'Simple collection set test 2',  
    @collection_mode = 0,  
    @days_until_expiration = 365,  
    @description = N'This is a test collection set that runs in cached mode.',  
    @logging_level = 2,  
    @schedule_name = N'CollectorSchedule_Every_30min',  
    @collection_set_id = @collection_set_id OUTPUT,  
    @collection_set_uid = @collection_set_uid OUTPUT;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datensammlung](../../relational-databases/data-collection/data-collection.md)   
 [Erstellen eines benutzerdefinierten Sammlungssatzes, der einen generischen T-SQL-Abfragesammlertyp verwendet &#40;Transact-SQL&#41;](../../relational-databases/data-collection/create-custom-collection-set-generic-t-sql-query-collector-type.md)   
 [Gespeicherte Prozeduren für den Datensammler &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [syscollector_collection_sets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql.md)  
  
  
