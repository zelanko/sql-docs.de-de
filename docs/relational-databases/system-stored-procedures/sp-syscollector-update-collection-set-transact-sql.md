---
title: sp_syscollector_update_collection_set (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_update_collection_set_TSQL
- sp_syscollector_update_collection_set
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_update_collection_set
- data collector [SQL Server], stored procedures
ms.assetid: 2dccc3cd-0e93-4e3e-a4e5-8fe89b31bd63
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8ed9fe58317d1dbe1cb3de59b11f556bc96b1d9f
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85892827"
---
# <a name="sp_syscollector_update_collection_set-transact-sql"></a>sp_syscollector_update_collection_set (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Wird verwendet, um die Eigenschaften eines benutzerdefinierten Sammlungssatzes zu ändern oder einen benutzerdefinierten Sammlungssatz umzubenennen.  
  
> [!WARNING]  
>  Falls das als Proxy konfigurierte Windows-Konto einem nicht interaktiven oder interaktiven Benutzer entspricht, der noch nicht angemeldet ist, ist das Profilverzeichnis nicht vorhanden, und die Erstellung des Stagingverzeichnisses schlägt in dem Fall fehl. Verwenden Sie ein Proxykonto auf einem Domänencontroller, müssen Sie also ein interaktives Konto angeben, das mindestens einmal verwendet wurde. So lässt sich sicherstellen, dass das Profilverzeichnis erstellt wurde.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syscollector_update_collection_set   
    [ [ @collection_set_id = ] collection_set_id ]  
    , [ [ @name = ] 'name' ]  
    , [ [ @new_name = ] 'new_name' ]  
    , [ [ @target = ] 'target' ]  
    , [ [ @collection_mode = ] collection_mode ]  
    , [ [ @days_until_expiration = ] days_until_expiration ]  
    , [ [ @proxy_id = ] proxy_id ]  
    , [ [ @proxy_name = ] 'proxy_name' ]  
    ,[ [ @schedule_uid = ] 'schedule_uid' ]  
    ,[ [ @schedule_name = ] 'schedule_uid' ]  
    , [ [ @logging_level = ] logging_level ]  
    , [ [ @description = ] 'description' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @collection_set_id = ] collection_set_id`Der eindeutige lokale Bezeichner für den Sammlungs Satz. *collection_set_id* ist vom *Datentyp* **int** und muss über einen Wert verfügen, wenn Name NULL ist.  
  
`[ @name = ] 'name'`Der Name des Sammlungs Satzes. *Name ist vom Datentyp* **vom Datentyp sysname** und muss über einen Wert verfügen, wenn *collection_set_id* NULL ist.  
  
`[ @new_name = ] 'new_name'`Der neue Name für den Sammlungs Satz. *new_name* ist vom **Datentyp vom Datentyp sysname**und kann, wenn verwendet, keine leere Zeichenfolge sein. *new_name* muss eindeutig sein. Wenn Sie eine Liste der aktuellen Namen von Sammlungssätzen abrufen möchten, fragen Sie die syscollector_collection_sets-Systemsicht ab.  
  
`[ @target = ] 'target'`Reserviert für zukünftige Verwendung.  
  
`[ @collection_mode = ] collection_mode`Der Typ der zu verwendenden Datensammlung. *collection_mode* ist vom Datentyp **smallint** und kann einen der folgenden Werte aufweisen:  
  
 0 - Modus mit Zwischenspeicherung. Für Datensammlung und -upload werden separate Zeitpläne verwendet. Geben Sie den Modus mit Zwischenspeicherung für eine fortlaufende Sammlung an.  
  
 1 - Modus ohne Zwischenspeicherung. Für Datensammlung und -upload wird der gleiche Zeitplan verwendet. Geben Sie den Modus ohne Zwischenspeicherung für eine Ad-hoc-Sammlung oder eine Momentaufnahmesammlung an.  
  
 Wenn Sie vom Modus ohne Zwischenspeicherung in den Modus mit Zwischenspeicherung (0) wechseln, müssen Sie auch *schedule_uid* oder *schedule_name*angeben.  
  
`[ @days_until_expiration = ] days_until_expiration`Gibt an, wie viele Tage die gesammelten Daten im Verwaltungs Data Warehouse gespeichert werden. *days_until_expiration* ist vom Datentyp **smallint**. *days_until_expiration* muss 0 oder eine positive ganze Zahl sein.  
  
`[ @proxy_id = ] proxy_id`Ist der eindeutige Bezeichner für ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Proxy Konto des-Agents. *proxy_id* ist vom Datentyp **int**.  
  
`[ @proxy_name = ] 'proxy_name'`Der Name des Proxys. *proxy_name* ist vom **Datentyp vom Datentyp sysname** und lässt NULL-Werte zu.  
  
`[ @schedule_uid = ] 'schedule_uid'`Der GUID, der auf einen Zeitplan zeigt. *schedule_uid* ist vom Datentyp **uniqueidentifier**.  
  
 Fragen Sie die syszeitpläne-Systemtabelle ab, um *schedule_uid*abzurufen.  
  
 Wenn *collection_mode* auf 0 festgelegt ist, muss *schedule_uid* oder *schedule_name* angegeben werden. Wenn *collection_mode* auf 1 festgelegt ist, wird *schedule_uid* oder *schedule_name* ignoriert, wenn angegeben.  
  
`[ @schedule_name = ] 'schedule_name'`Der Name des Zeitplans. *schedule_name* ist vom **Datentyp vom Datentyp sysname** und lässt NULL-Werte zu. Wenn angegeben, muss *schedule_uid* NULL sein. Fragen Sie die syszeitpläne-Systemtabelle ab, um *schedule_name*abzurufen.  
  
`[ @logging_level = ] logging_level`Der Protokolliergrad. *LOGGING_LEVEL* ist vom Datentyp **smallint** und hat einen der folgenden Werte:  
  
 0 - Informationen zur Protokollausführung und zu den [!INCLUDE[ssIS](../../includes/ssis-md.md)]-Ereignissen, die Folgendes nachverfolgen:  
  
-   Starten/Beenden von Samlungssätzen  
  
-   Starten/Beenden von Paketen  
  
-   Fehlerinformationen  
  
 Protokollierung von 1 Ebene 0 und:  
  
-   Ausführungsstatistiken  
  
-   Kontinuierliche Ausführung der Sammlung  
  
-   Warnungsereignisse von [!INCLUDE[ssIS](../../includes/ssis-md.md)]  
  
 2 - Protokollierung Stufe 1 sowie ausführliche Ereignisinformationen von [!INCLUDE[ssIS](../../includes/ssis-md.md)].  
  
 Der Standardwert für *LOGGING_LEVEL* ist 1.  
  
`[ @description = ] 'description'`Die Beschreibung des Sammlungs Satzes. die *Beschreibung* ist **nvarchar (4000)**.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 sp_syscollector_update_collection_set muss im Kontext der msdb-Systemdatenbank ausgeführt werden.  
  
 Entweder *collection_set_id* oder *Name* muss einen Wert aufweisen, beide dürfen nicht NULL sein. Um diese Werte abzurufen, fragen Sie die syscollector_collection_sets-Systemsicht ab.  
  
 Wenn der Sammlungs Satz ausgeführt wird, können Sie nur *schedule_uid* und *Beschreibungen*aktualisieren. Verwenden Sie [sp_syscollector_stop_collection_set](../../relational-databases/system-stored-procedures/sp-syscollector-stop-collection-set-transact-sql.md), um den Sammlungs Satz zu verhindern.  
  
## <a name="permissions"></a>Berechtigungen  
 Damit dieser Vorgang ausgeführt werden kann, ist die Mitgliedschaft in der festen Datenbankrolle dc_admin oder dc_operator (mit EXECUTE-Berechtigung) erforderlich. Obwohl die dc_operator-Rolle diese gespeicherte Prozedur ausführen kann, können die Eigenschaften von den Mitgliedern dieser Rolle nur begrenzt geändert werden. Die folgenden Eigenschaften können nur von dc_admin geändert werden:  
  
-   @new_name  
  
-   @target  
  
-   @proxy_id  
  
-   @description  
  
-   @collection_mode  
  
-   @days_until_expiration  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-renaming-a-collection-set"></a>A. Umbenennen eines Sammlungssatzes  
 Im folgenden Beispiel wird ein benutzerdefinierter Sammlungssatz umbenannt.  
  
```  
USE msdb;  
GO  
EXECUTE dbo.sp_syscollector_update_collection_set  
@name = N'Simple collection set test 1',  
@new_name = N'Collection set test 1 in cached mode';  
GO  
```  
  
### <a name="b-changing-the-collection-mode-from-non-cached-to-cached"></a>B. Wechseln vom Auflistmodus ohne Zwischenspeicherung in den Modus mit Zwischenspeicherung  
 Im folgenden Beispiel wird vom Sammlungsmodus ohne Zwischenspeicherung in den Modus mit Zwischenspeicherung gewechselt. Für diesen Wechsel müssen Sie eine Zeitplan-ID oder einen Zeitplannamen angeben.  
  
```  
USE msdb;  
GO  
EXECUTE dbo.sp_syscollector_update_collection_set  
@name = N'Collection set test 1 in cached mode',  
@collection_mode = 0,  
@schedule_uid = 'C7022AF3-51B8-4011-B159-64C47C88FF70';  
-- alternatively, use @schedule_name.  
-- @schedule_name = N'CollectorSchedule_Every_15min;  
GO  
```  
  
### <a name="c-changing-other-collection-set-parameters"></a>C. Ändern von anderen Sammlungssatzparametern  
 Im folgenden Beispiel werden verschiedene Eigenschaften des Sammlungssatzes "Simple collection set test 2" aktualisiert.  
  
```  
USE msdb;  
GO  
EXEC dbo.sp_syscollector_update_collection_set  
@name = N'Simple collection set test 2',  
@collection_mode = 1,  
@days_until_expiration = 5,  
@description = N'This is a test collection set that runs in noncached mode.',  
@logging_level = 0;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Datensammlung](../../relational-databases/data-collection/data-collection.md)   
 [syscollector_collection_sets &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql.md)   
 [dbo.sysZeitpläne &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/dbo-sysschedules-transact-sql.md)  
  
  
