---
title: sp_adddynamicsnapshot_job (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_adddynamicsnapshot_job
- sp_adddynamicsnapshot_job_TSQL
helpviewer_keywords:
- sp_adddynamicsnapshot_job
ms.assetid: ef50ccf6-e360-4e4b-91b9-6706b8fabefa
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 48f94f7fcf823a9ed9acc519e393369e44b45302
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771340"
---
# <a name="spadddynamicsnapshotjob-transact-sql"></a>sp_adddynamicsnapshot_job (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Erstellt einen Agentauftrag, der eine Momentaufnahme gefilterter Daten für eine Veröffentlichung mit parametrisierten Zeilenfiltern generiert. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt. Ein Administrator kann diese gespeicherte Prozedur verwenden, um manuell Aufträge für Momentaufnahmen gefilterter Daten für Abonnenten zu erstellen.  
  
> [!NOTE]  
>  Damit ein Auftrag für eine Momentaufnahme gefilterter Daten erstellt werden kann, muss bereits ein Auftrag für eine Standardmomentaufnahme für die Veröffentlichung vorhanden sein.  
  
 Weitere Informationen finden Sie unter [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_adddynamicsnapshot_job [ @publication = ] 'publication'   
    [ , [ @suser_sname = ] 'suser_sname' ]   
    [ , [ @host_name = ] 'host_name' ]   
    [ , [ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname' OUTPUT ]   
    [ , [ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid' OUTPUT ]   
    [ , [ @frequency_type= ] frequency_type ]  
    [ , [ @frequency_interval= ] frequency_interval ]  
    [ , [ @frequency_subday= ] frequency_subday ]  
    [ , [ @frequency_subday_interval= ] frequency_subday_interval ]  
    [ , [ @frequency_relative_interval= ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor= ] frequency_recurrence_factor ]  
    [ , [ @active_start_date= ] active_start_date ]  
    [ , [ @active_end_date= ] active_end_date ]  
    [ , [ @active_start_time_of_day= ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day= ] active_end_time_of_day ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung, der der Auftrag für die Momentaufnahme gefilterter Daten hinzugefügt wird. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @suser_sname = ] 'suser_sname'`Der verwendete Wert beim Erstellen einer Momentaufnahme gefilterter Daten für ein Abonnement, das nach dem Wert der [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) -Funktion auf dem Abonnenten gefiltert wird. *SUSER_SNAME* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. *SUSER_SNAME* sollte NULL sein, wenn diese Funktion nicht zum dynamischen Filtern der Veröffentlichung verwendet wird.  
  
`[ @host_name = ] 'host_name'`Der verwendete Wert beim Erstellen einer Momentaufnahme gefilterter Daten für ein Abonnement, das nach dem Wert der [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) -Funktion auf dem Abonnenten gefiltert wird. *HOST_NAME* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. *HOST_NAME* sollte NULL sein, wenn diese Funktion nicht zum dynamischen Filtern der Veröffentlichung verwendet wird.  
  
`[ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname'`Der Name des erstellten Auftrags für eine Momentaufnahme gefilterter Daten. *dynamic_snapshot_jobname* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL, und ist ein optionaler OUTPUT-Parameter. Wenn angegeben, muss *dynamic_snapshot_jobname* auf einen eindeutigen Auftrag auf dem Verteiler aufgelöst werden. Wird das Argument nicht angegeben, wird automatisch ein Auftragsname generiert und im Resultset zurückgegeben, wo der Name folgendermaßen erstellt wird:  
  
```  
'dyn_' + <name of the standard snapshot job> + <GUID>  
```  
  
> [!NOTE]  
>  Wenn Sie den Namen des Auftrags für eine dynamische Momentaufnahme generieren, können Sie den Namen des Auftrags für eine Standardmomentaufnahme abschneiden.  
  
`[ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid'`Ein Bezeichner für den erstellten Auftrag für die Momentaufnahme gefilterter Daten. *dynamic_snapshot_jobid* ist vom Datentyp **uniqueidentifier**. der Standardwert ist NULL, und ist ein optionaler OUTPUT-Parameter.  
  
`[ @frequency_type = ] frequency_type`Die Häufigkeit, mit der der Auftrag für die Momentaufnahme gefilterter Daten geplant werden soll. *frequency_type* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Einmal|  
|**2**|Bedarfsgesteuert|  
|**4** (Standard)|Täglich|  
|**8**|Wöchentlicher Zeitplan|  
|**16**|Monatlicher Zeitplan|  
|**32**|Monatlich, relativ|  
|**64**|Autostart|  
|**128**|Wiederholt|  
  
`[ @frequency_interval = ] frequency_interval`Der Zeitraum (in Tagen), in dem der Auftrag für die Momentaufnahme gefilterter Daten ausgeführt wird. *frequency_interval* ist vom Datentyp **int**. der Standardwert ist 1, und der Wert hängt vom Wert von *frequency_type*ab.  
  
|Wert von *frequency_type*|Auswirkung auf *frequency_interval*|  
|--------------------------------|-------------------------------------|  
|**1**|*frequency_interval* wird nicht verwendet.|  
|**4** (Standard)|Alle *frequency_interval* Tage, der Standardwert ist täglich.|  
|**8**|*frequency_interval* ist eine oder mehrere der folgenden (kombiniert mit einem [ &#124; &#40;bitweisen or&#41; &#40;-Operator von Transact-&#41; SQL](../../t-sql/language-elements/bitwise-or-transact-sql.md) ):<br /><br /> **1** = Sonntag &#124; **2** = Montag &#124; **4** = Dienstag &#124; **8** = Mittwoch &#124; **16** = Donnerstag &#124; **32** = Freitag &#124; **64** = Samstag|  
|**16**|Am *frequency_interval* Tag des Monats.|  
|**32**|*frequency_interval* ist einer der folgenden:<br /><br /> **1** = Sonntag &#124; **2** = Montag &#124; **3** = Dienstag &#124; **4** = Mittwoch &#124; **5** = Donnerstag &#124; **6** = Freitag &#124; **7** = Samstag &#124; **8** = Tag &#124; **9** = Weekday &#124; **10** = Wochenendtag|  
|**64**|*frequency_interval* wird nicht verwendet.|  
|**128**|*frequency_interval* wird nicht verwendet.|  
  
`[ @frequency_subday = ] frequency_subday`Gibt die Einheiten für *frequency_subday_interval*an. *frequency_subday* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Einmal|  
|**2**|Zweimal|  
|**4** (Standard)|Minute|  
|**8**|Hour|  
  
`[ @frequency_subday_interval = ] frequency_subday_interval`Die Anzahl der *frequency_subday* Zeiträume, die zwischen den einzelnen Ausführungen des Auftrags auftreten. *frequency_subday_interval* ist vom Datentyp **int**und hat den Standardwert 5.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval`Das Vorkommen des Auftrags für eine Momentaufnahme gefilterter Daten in jedem Monat. Dieser Parameter wird verwendet, wenn *frequency_type* auf **32** (monatlich, relativ) festgelegt ist. *frequency_relative_interval* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**1** (Standard)|Erster|  
|**2**|Zweimal|  
|**4**|Dritter|  
|**8**|Vierter|  
|**16**|Letzter|  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor`Der von *frequency_type*verwendete Wiederholungs Faktor. *frequency_recurrence_factor* ist vom Datentyp **int**und hat den Standardwert 0.  
  
`[ @active_start_date = ] active_start_date`Das Datum, an dem der Auftrag für die Momentaufnahme gefilterter Daten zum ersten Mal geplant wird (Format: YYYYMMDD) *active_start_date* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @active_end_date = ] active_end_date`Das Datum, an dem der Auftrag für die Momentaufnahme gefilterter Daten nicht mehr geplant ist, formatiert als YYYYMMDD. *active_end_date* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day`Die Tageszeit, zu der der Auftrag für die Momentaufnahme gefilterter Daten zum ersten Mal geplant wird (als HHMMSS formatiert). *active_start_time_of_day* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day`Die Tageszeit, zu der der Auftrag für die Momentaufnahme gefilterter Daten nicht mehr geplant ist. dabei wird das Format HHMMSS verwendet. *active_end_time_of_day* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
## <a name="result-set"></a>Resultset  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Identifiziert den Auftrag für eine Momentaufnahme gefilterter Daten in der [MSdynamicsnapshotjobs](../../relational-databases/system-tables/msdynamicsnapshotjobs-transact-sql.md) -Systemtabelle.|  
|**dynamic_snapshot_jobname**|**sysname**|Name des Auftrags für eine Momentaufnahme gefilterter Daten.|  
|**dynamic_snapshot_jobid**|**uniqueidentifier**|Identifiziert den [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Auftrag auf dem Verteiler eindeutig.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_adddynamicsnapshot_job** wird bei der Mergereplikation für Veröffentlichungen verwendet, die einen parametrisierten Filter verwenden.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_MergeDynamicPubPlusPartition](../../relational-databases/replication/codesnippet/tsql/sp-adddynamicsnapshot-jo_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_adddynamicsnapshot_job**ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer Momentaufnahme für eine Mergeveröffentlichung mit parametrisierten Filtern](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)   
 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)   
 [sp_dropdynamicsnapshot_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdynamicsnapshot-job-transact-sql.md)   
 [sp_helpdynamicsnapshot_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdynamicsnapshot-job-transact-sql.md)  
  
  
