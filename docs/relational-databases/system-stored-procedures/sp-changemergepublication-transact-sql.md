---
title: Sp_changemergepublication (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changemergepublication_TSQL
- sp_changemergepublication
helpviewer_keywords:
- sp_changemergepublication
ms.assetid: 81fe1994-7678-4852-980b-e02fedf1e796
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6ca4142ca78d0842b535036e99464b9a1b7dc2c9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62997122"
---
# <a name="spchangemergepublication-transact-sql"></a>sp_changemergepublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert die Eigenschaften einer Mergeveröffentlichung. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_changemergepublication [ @publication= ] 'publication'  
    [ , [ @property= ] 'property' ]  
    [ , [ @value= ] 'value' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
`[ @property = ] 'property'` Die Eigenschaft, für die angegebene Veröffentlichung geändert werden soll. *Eigenschaft* ist **Sysname**, und kann einen der Werte im aufgeführt, die folgende Tabelle.  
  
`[ @value = ] 'value'` Der neue Wert für die angegebene Eigenschaft. *Wert* ist **nvarchar(255)**, und kann einen der Werte im aufgeführt, die folgende Tabelle.  
  
 Diese Tabelle beschreibt die Eigenschaften der Veröffentlichung, die geändert werden kann, und werden Einschränkungen für die Werte für diese Eigenschaften beschrieben.  
  
|Eigenschaft|Wert|Description|  
|--------------|-----------|-----------------|  
|**allow_anonymous**|**true**|Anonyme Abonnements sind zulässig.|  
||**false**|Anonyme Abonnements sind nicht zulässig.|  
|**allow_partition_realignment**|**true**|Löschvorgänge werden an den Abonnenten gesendet, um die Ergebnisse einer Partitionsänderung widerzuspiegeln, indem Daten entfernt werden, die nicht mehr Bestandteil der Partition des Abonnenten sind. Dies ist das Standardverhalten.|  
||**false**|Daten einer alten Partition verbleiben auf dem Abonnenten. Änderungen an diesen Daten auf dem Verleger werden nicht an diesen Abonnenten repliziert. Stattdessen werden auf dem Abonnenten vorgenommene Änderungen an den Verleger repliziert. Auf diese Weise werden Daten in einem Abonnement aus einer alten Partition beibehalten, wenn die Daten noch benötigt werden.|  
|**allow_pull**|**true**|Pullabonnements sind für die angegebene Veröffentlichung zulässig.|  
||**false**|Pullabonnements sind für die angegebene Veröffentlichung nicht zulässig.|  
|**allow_push**|**true**|Pushabonnements sind für die angegebene Veröffentlichung zulässig.|  
||**false**|Pushabonnements sind für die angegebene Veröffentlichung nicht zulässig.|  
|**allow_subscriber_initiated_snapshot**|**true**|Der Abonnent kann den Momentaufnahmeprozess initiieren.|  
||**false**|Der Abonnent kann den Momentaufnahmeprozess nicht initiieren.|  
|**allow_subscription_copy**|**true**|Sie können die Abonnementdatenbanken kopieren, die diese Veröffentlichung abonniert haben.|  
||**false**|Sie können die Abonnementdatenbanken, die diese Veröffentlichung abonniert haben, nicht kopieren.|  
|**allow_synctoalternate**|**true**|Lässt einen alternativen Synchronisierungspartner für die Synchronisierung mit diesem Verleger zu.|  
||**false**|Lässt keinen alternativen Synchronisierungspartner für die Synchronisierung mit diesem Verleger zu.|  
|**allow_web_synchronization**|**true**|Abonnements können über HTTPS synchronisiert werden.|  
||**false**|Abonnements können nicht über HTTPS synchronisiert werden.|  
|**alt_snapshot_folder**||Gibt den Speicherort des alternativen Ordners für die Momentaufnahme an.|  
|**automatic_reinitialization_policy**|**1**|Änderungen werden vor der Neuinitialisierung vom Abonnenten hochgeladen.|  
||**0**|Das Abonnement wird erneut initialisiert, ohne die Änderungen vorher hochzuladen.|  
|**centralized_conflicts**|**true**|Alle Konfliktdatensätze werden auf dem Verleger gespeichert. Wenn Sie diese Eigenschaft ändern, müssen vorhandene Abonnenten erneut initialisiert werden.|  
||**false**|Konfliktdatensätze werden auf dem Server gespeichert, der bei der Konfliktauflösung verloren hat. Wenn Sie diese Eigenschaft ändern, müssen vorhandene Abonnenten erneut initialisiert werden.|  
|**compress_snapshot**|**true**|Die Momentaufnahme in einem alternativen Momentaufnahmeordner wird in das CAB-Format komprimiert. Die Momentaufnahme im Standard-Momentaufnahmeordner kann nicht komprimiert werden. Für das Ändern dieser Eigenschaft ist eine neue Momentaufnahme erforderlich.|  
||**false**|Standardmäßig wird die Momentaufnahme nicht komprimiert. Für das Ändern dieser Eigenschaft ist eine neue Momentaufnahme erforderlich.|  
|**conflict_logging**|**publisher**|Die Konfliktdatensätze werden auf dem Verleger gespeichert.|  
||**subscriber**|Die Konfliktdatensätze werden auf dem Abonnenten gespeichert, der den Konflikt verursacht hat. Nicht unterstützt für [!INCLUDE[ssEW](../../includes/ssew-md.md)] Abonnenten *.*|  
||**both**|Die Konfliktdatensätze werden auf dem Verleger und auf dem Abonnenten gespeichert.|  
|**conflict_retention**||Ein **Int** , die gibt der Beibehaltungsdauer in Tagen, für die Konflikte beibehalten werden. Festlegen von *Conflict_retention* zu **0** bedeutet, dass kein konfliktcleanup notwendig ist.|  
|**description**||Beschreibung der Veröffentlichung.|  
|**dynamic_filters**|**true**|Die Veröffentlichung wird anhand einer dynamischen Klausel gefiltert.|  
||**false**|Die Veröffentlichung wird nicht dynamisch gefiltert.|  
|**enabled_for_internet**|**true**|Die Veröffentlichung ist für das Internet aktiviert. File Transfer Protocol (FTP) kann verwendet werden, um die Momentaufnahmedateien an einen Abonnenten zu übertragen. Die Synchronisierungsdateien für die Veröffentlichung werden im Verzeichnis C:\Programme\Microsoft SQL Server\MSSQL\Repldata\ftp gespeichert.|  
||**false**|Die Veröffentlichung ist nicht für das Internet aktiviert.|  
|**ftp_address**||Die Netzwerkadresse des FTP-Diensts für den Verteiler. Gibt an, wo die Momentaufnahmedateien für die Veröffentlichung gespeichert werden.|  
|**ftp_login**||Der Benutzername, der für die Verbindung mit dem FTP-Dienst verwendet wird.|  
|**ftp_password**||Das Benutzerkennwort, das für die Verbindung mit dem FTP-Dienst verwendet wird.|  
|**ftp_port**||Die Portnummer des FTP-Diensts für den Verteiler. Gibt die TCP-Anschlussnummer der FTP-Site an, in der die Momentaufnahmedateien für die Veröffentlichung gespeichert werden.|  
|**ftp_subdirectory**||Gibt an, wo die Momentaufnahmedateien erstellt werden, wenn die Veröffentlichung das Verteilen von Momentaufnahmen mithilfe von FTP unterstützt.|  
|**generation_leveling_threshold**|**int**|Gibt die Anzahl der Änderungen, die in einer Generierung enthalten sind. Eine Generierung ist eine Auflistung von Änderungen, die an einen Verleger oder Abonnenten übermittelt werden.|  
|**keep_partition_changes**|**true**|Die Synchronisierung wird optimiert, und es sind nur Abonnenten betroffen, die über Zeilen in den geänderten Partitionen verfügen. Für das Ändern dieser Eigenschaft ist eine neue Momentaufnahme erforderlich.|  
||**false**|Die Synchronisierung wird nicht optimiert, und die an Abonnenten gesendeten Partitionen werden überprüft, wenn sich Daten in einer Partition ändern. Für das Ändern dieser Eigenschaft ist eine neue Momentaufnahme erforderlich.|  
|**max_concurrent_merge**||Dies ist ein **Int** , das darstellt, der maximalen Anzahl gleichzeitiger Mergeprozesse, die für eine Mergeveröffentlichung ausgeführt werden können. Bei 0 gibt es keine Beschränkung. Wenn die gleichzeitige Ausführung von mehr Mergeprozessen geplant ist, werden die überschüssigen Aufträge in eine Warteschlange eingereiht, in der diese darauf warten, dass ein aktuell ausgeführter Mergeprozess beendet wird.|  
|**max_concurrent_dynamic_snapshots**||Dies ist ein **Int** , stellt die maximale Anzahl gleichzeitiger momentaufnahmesitzungen zum Generieren einer gefilterten Daten Momentaufnahme können gleichzeitig ausgeführt werden, für eine Mergeveröffentlichung, die verwendet parametrisierte Zeilenfilter. Wenn **0**, es gibt keine Beschränkung. Wenn die gleichzeitige Ausführung von mehr Momentaufnahmeprozessen geplant ist, werden die überschüssigen Aufträge in eine Warteschlange eingereiht, bis ein aktueller Mergeprozess beendet wird.|  
|**post_snapshot_script**||Gibt einen Zeiger auf ein **.sql** Dateispeicherort. Der Verteilungs-Agent oder der Merge-Agent führt post_snapshot_script aus, nachdem alle andere Skripts für replizierte Objekte und Daten während der Erstsynchronisierung angewendet wurden. Für das Ändern dieser Eigenschaft ist eine neue Momentaufnahme erforderlich.|  
|**pre_snapshot_script**||Gibt einen Zeiger auf ein **.sql** Dateispeicherort. Der Merge-Agent führt das vor der Momentaufnahme ausgeführte Skript vor allen Skripts für replizierte Objekte aus, wenn die Momentaufnahme auf einem Abonnenten angewendet wird. Für das Ändern dieser Eigenschaft ist eine neue Momentaufnahme erforderlich.|  
|**publication_compatibility_level**|**100RTM**|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
||**90RTM**|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|  
|**publish_to_activedirectory**|**true**|Dieser Parameter wurde als veraltet markiert und wird nur zum Sicherstellen der Abwärtskompatibilität von Skripts unterstützt. Sie können Active Directory nicht länger Veröffentlichungsinformationen hinzufügen.|  
||**false**|Entfernt die Veröffentlichungsinformationen aus Active Directory.|  
|**replicate_ddl**|**1**|Anweisungen von Data Definition Language (DDL), die auf dem Verleger ausgeführt werden, werden repliziert.|  
||**0**|DDL-Anweisungen werden nicht repliziert.|  
|**retention**||Dies ist ein **Int** , die die Anzahl der *Retention_period_unit* Einheiten für die Änderungen für die angegebene Veröffentlichung gespeichert werden. Wenn das Abonnement nicht innerhalb der Beibehaltungsdauer synchronisiert wird und die ausstehenden Änderungen von einem Cleanupvorgang auf dem Verteiler entfernt wurden, läuft das Abonnement ab und muss erneut initialisiert werden. Die maximal zulässige Beibehaltungsdauer entspricht der Anzahl von Tagen zwischen dem 31. Dezember 9999 und dem aktuellen Datum.<br /><br /> Hinweis: Für die Beibehaltungsdauer von Mergeveröffentlichungen gilt eine Kulanzfrist von 24 Stunden, um Abonnenten in verschiedenen Zeitzonen zu unterstützen.|  
|**retention_period_unit**|**day**|Die Beibehaltungsdauer wird in Tagen angegeben.|  
||**week**|Die Beibehaltungsdauer wird in Wochen angegeben.|  
||**month**|Die Beibehaltungsdauer wird in Monaten angegeben.|  
||**year**|Die Beibehaltungsdauer wird in Jahren angegeben.|  
|**snapshot_in_defaultfolder**|**true**|Momentaufnahmedateien werden im Standardmomentaufnahmeordner gespeichert.|  
||**false**|Momentaufnahmedateien werden gespeichert, in den alternativen Speicherort, der von angegebene *Alt_snapshot_folder*. Diese Kombination gibt an, dass die Momentaufnahmedateien sowohl im Standardspeicherort als auch in alternativen Speicherorten gespeichert werden.|  
|**snapshot_ready**|**true**|Die Momentaufnahme für die Veröffentlichung ist verfügbar.|  
||**false**|Die Momentaufnahme für die Veröffentlichung ist nicht verfügbar.|  
|**status**|**active**|Die Veröffentlichung weist einen aktiven Status auf.|  
||**inactive**|Die Veröffentlichung weist einen inaktiven Status auf.|  
|**sync_mode**|**Native** oder<br /><br /> **systemeigene bcp**|Massenkopierprogramm-Ausgabe aller Tabellen im einheitlichen Modus wird für die Anfangsmomentaufnahme verwendet.|  
||**character**<br /><br /> oder **Bcp-Zeichen**|Massenkopierprogramm-Ausgabe aller Tabellen im Zeichenmodus wird für die Anfangsmomentaufnahme verwendet. Dies ist für alle Nicht-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Abonnenten erforderlich.|  
|**use_partition_groups**<br /><br /> Hinweis: Nach der Verwendung von Partition_groups, wenn Sie wieder in den mit **Setupbelongs**, und legen Sie **Use_partition_groups = "false"** in **Changemergearticle**, dies ist möglicherweise nicht ordnungsgemäß übernommen, nachdem eine Momentaufnahme erstellt wurde. Die Trigger, die von der Momentaufnahme generiert werden, sind mit Partitionsgruppen kompatibel.<br /><br /> Die problemumgehung für dieses Szenario besteht darin, den Status auf inaktiv festlegen, ändern Sie die **Use_partition_groups**, und legen Sie dann in den aktiven Status.|**true**|Die Veröffentlichung verwendet vorausberechnete Partitionen.|  
||**false**|Die Veröffentlichung verwendet keine vorausberechneten Partitionen.|  
|**validate_subscriber_info**||Listet die Funktionen auf, die zum Abrufen von Abonnenteninformationen verwendet werden. Überprüft anschließend die dynamischen Filterkriterien, die für den Abonnenten verwendet werden, um zu überprüfen, dass die Informationen konsistent partitioniert werden.|  
|**web_synchronization_url**||Der Standardwert für die Internet-URL, die für die Websynchronisierung verwendet wird.|  
|NULL (Standard)||Gibt die Liste der unterstützten Werte für *Eigenschaft*.|  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot` Bestätigt, dass die von dieser gespeicherten Prozedur ausgeführte Aktion eine vorhandene Momentaufnahme für ungültig erklären kann. *Force_invalidate_snapshot* ist eine **Bit**, hat den Standardwert **0**.  
  
 **0** gibt an, dass Änderungen an der Veröffentlichung nicht die Momentaufnahme ungültig wird. Wenn die gespeicherte Prozedur erkennt, dass die Änderungen eine neue Momentaufnahme erfordern, tritt ein Fehler auf und es werden keine Änderungen vorgenommen.  
  
 **1** gibt an, dass der Wert der Momentaufnahme-möglicherweise Änderungen an der Veröffentlichung. Wenn es Abonnements, die eine neue Momentaufnahme erfordern sind, können über die Berechtigung für die vorhandene Momentaufnahme als veraltet markiert werden und für eine neue Momentaufnahme generiert werden soll.  
  
 Weitere Informationen zu den Eigenschaften, bei deren Änderung die Generierung einer neuen Momentaufnahme erforderlich ist, finden Sie im Abschnitt mit den Hinweisen.  
  
`[ @force_reinit_subscription = ] force_reinit_subscription` Bestätigt, dass die von dieser gespeicherten Prozedur ausgeführte Aktion möglicherweise eine erneute Initialisierung vorhandener Abonnements erfordern. *Force_reinit_subscription* ist eine **Bit** hat den Standardwert **0**.  
  
 **0** gibt an, dass Änderungen an der Veröffentlichung nicht erfordert, dass Abonnements erneut initialisiert werden. Wenn die gespeicherte Prozedur erkennt, dass die Änderung die Neuinitialisierung vorhandener Abonnements erfordert, tritt ein Fehler auf, und es werden keine Änderungen durchgeführt.  
  
 **1** gibt, dass Änderungen die Veröffentlichung bewirkt, dass vorhandene Abonnements erneut initialisiert werden und die Berechtigung für den erneuten abonnementinitialisierung erteilt.  
  
 Weitere Informationen zu den Eigenschaften, bei deren Änderung die erneute Initialisierung aller vorhandenen Abonnements erforderlich ist, finden Sie im Abschnitt "Hinweise".  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_changemergepublication** wird bei der Mergereplikation verwendet.  
  
 Das Ändern der folgenden Eigenschaften erfordert die Generierung einer neuen Momentaufnahme. Geben Sie einen Wert von **1** für die *Force_invalidate_snapshot* Parameter.  
  
-   **alt_snapshot_folder**  
  
-   **compress_snapshot**  
  
-   **dynamic_filters**  
  
-   **ftp_address**  
  
-   **ftp_login**  
  
-   **ftp_password**  
  
-   **ftp_port**  
  
-   **ftp_subdirectory**  
  
-   **post_snapshot_script**  
  
-   **Wert von Publication_compatibility_level** (um **80SP3** nur)  
  
-   **pre_snapshot_script**  
  
-   **snapshot_in_defaultfolder**  
  
-   **sync_mode**  
  
-   **use_partition_groups**  
  
 Für das Ändern der folgenden Eigenschaften ist eine erneute Initialisierung von vorhandenen Abonnements erforderlich. Geben Sie einen Wert von **1** für die *Force_reinit_subscription* Parameter.  
  
-   **dynamic_filters**  
  
-   **validate_subscriber_info**  
  
 Zum Auflisten von veröffentlichungsobjekten in Active Directory mithilfe der *Publish_to_active_directory*, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Objekt muss bereits in Active Directory erstellt werden.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_changemergepublication](../../relational-databases/replication/codesnippet/tsql/sp-changemergepublicatio_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_changemergepublication**.  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen und Ändern von Veröffentlichungseigenschaften](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Ändern von Veröffentlichungs- und Artikeleigenschaften](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)   
 [sp_dropmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql.md)   
 [sp_helpmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
