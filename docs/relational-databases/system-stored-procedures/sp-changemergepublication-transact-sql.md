---
title: sp_changemergepublication (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ba7a6785952152632a9435269bc7b4a9b236ad38
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85872517"
---
# <a name="sp_changemergepublication-transact-sql"></a>sp_changemergepublication (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Ändert die Eigenschaften einer Mergeveröffentlichung. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_changemergepublication [ @publication= ] 'publication'  
    [ , [ @property= ] 'property' ]  
    [ , [ @value= ] 'value' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @property = ] 'property'`Die Eigenschaft, die für die angegebene Veröffentlichung geändert werden soll. *Property* ist vom **Datentyp vom Datentyp sysname**. die folgenden Werte sind in der folgenden Tabelle aufgeführt.  
  
`[ @value = ] 'value'`Der neue Wert für die angegebene Eigenschaft. der Wert ist vom Datentyp **nvarchar (255)**. der *Wert* kann einer der in der folgenden Tabelle aufgelisteten Werte sein.  
  
 Diese Tabelle beschreibt die Eigenschaften der Veröffentlichung, die geändert werden können, und beschreibt die Einschränkungen der Werte für diese Eigenschaften.  
  
|Eigenschaft|Wert|Beschreibung|  
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
||**Abonnenten**|Die Konfliktdatensätze werden auf dem Abonnenten gespeichert, der den Konflikt verursacht hat. Wird für Abonnenten nicht unterstützt [!INCLUDE[ssEW](../../includes/ssew-md.md)] *.*|  
||**zwar**|Die Konfliktdatensätze werden auf dem Verleger und auf dem Abonnenten gespeichert.|  
|**conflict_retention**||Ein **int** -Wert, der die Beibehaltungs Dauer (in Tagen) angibt, für die Konflikte beibehalten werden. Das Festlegen von *conflict_retention* auf **0** bedeutet, dass keine Konflikt Bereinigung erforderlich ist.|  
|**description**||Die Beschreibung der Veröffentlichung.|  
|**dynamic_filters**|**true**|Die Veröffentlichung wird anhand einer dynamischen Klausel gefiltert.|  
||**false**|Die Veröffentlichung wird nicht dynamisch gefiltert.|  
|**enabled_for_internet**|**true**|Die Veröffentlichung ist für das Internet aktiviert. File Transfer Protocol (FTP) kann verwendet werden, um die Momentaufnahmedateien an einen Abonnenten zu übertragen. Die Synchronisierungsdateien für die Veröffentlichung werden im Verzeichnis C:\Programme\Microsoft SQL Server\MSSQL\Repldata\ftp gespeichert.|  
||**false**|Die Veröffentlichung ist nicht für das Internet aktiviert.|  
|**ftp_address**||Die Netzwerkadresse des FTP-Dienstanbieter für den Verteiler. Gibt an, wo die Momentaufnahmedateien für die Veröffentlichung gespeichert werden.|  
|**ftp_login**||Der Benutzername, der zum Herstellen der Verbindung mit dem FTP-Dienst verwendet wird.|  
|**ftp_password**||Das Benutzer Kennwort, das zum Herstellen einer Verbindung mit dem FTP-Dienst verwendet wird.|  
|**ftp_port**||Die Portnummer des FTP-Dienstanbieter für den Verteiler. Gibt die TCP-Anschlussnummer der FTP-Site an, in der die Momentaufnahmedateien für die Veröffentlichung gespeichert werden.|  
|**ftp_subdirectory**||Gibt an, wo die Momentaufnahmedateien erstellt werden, wenn die Veröffentlichung das Verteilen von Momentaufnahmen mithilfe von FTP unterstützt.|  
|**generation_leveling_threshold**|**int**|Gibt die Anzahl der Änderungen an, die in einer Generierung enthalten sind. Eine Generierung ist eine Auflistung von Änderungen, die an einen Verleger oder Abonnenten übermittelt werden.|  
|**keep_partition_changes**|**true**|Die Synchronisierung wird optimiert, und es sind nur Abonnenten betroffen, die über Zeilen in den geänderten Partitionen verfügen. Für das Ändern dieser Eigenschaft ist eine neue Momentaufnahme erforderlich.|  
||**false**|Die Synchronisierung wird nicht optimiert, und die an Abonnenten gesendeten Partitionen werden überprüft, wenn sich Daten in einer Partition ändern. Für das Ändern dieser Eigenschaft ist eine neue Momentaufnahme erforderlich.|  
|**max_concurrent_merge**||Dabei handelt es sich um einen **int** -Wert, der die maximale Anzahl gleichzeitiger Mergeprozesse darstellt, die für eine Veröffentlichung ausgeführt werden können. Bei 0 gibt es keine Beschränkung. Wenn die gleichzeitige Ausführung von mehr Mergeprozessen geplant ist, werden die überschüssigen Aufträge in eine Warteschlange eingereiht, in der diese darauf warten, dass ein aktuell ausgeführter Mergeprozess beendet wird.|  
|**max_concurrent_dynamic_snapshots**||Dies ist ein **int** -Wert, der die maximale Anzahl von Momentaufnahme Sitzungen darstellt, um eine gefilterte Daten Momentaufnahme zu generieren, die gleichzeitig für eine Mergeveröffentlichung mit parametrisierten Zeilen filtern ausgeführt werden kann. Wenn der Wert **0**ist, gibt es keine Begrenzung. Wenn die gleichzeitige Ausführung von mehr Momentaufnahmeprozessen geplant ist, werden die überschüssigen Aufträge in eine Warteschlange eingereiht, bis ein aktueller Mergeprozess beendet wird.|  
|**post_snapshot_script**||Gibt einen Zeiger auf einen Speicherort für **SQL** -Dateien an. Der Verteilungs-Agent oder der Merge-Agent führt post_snapshot_script aus, nachdem alle andere Skripts für replizierte Objekte und Daten während der Erstsynchronisierung angewendet wurden. Für das Ändern dieser Eigenschaft ist eine neue Momentaufnahme erforderlich.|  
|**pre_snapshot_script**||Gibt einen Zeiger auf einen Speicherort für **SQL** -Dateien an. Der Merge-Agent führt das vor der Momentaufnahme ausgeführte Skript vor allen Skripts für replizierte Objekte aus, wenn die Momentaufnahme auf einem Abonnenten angewendet wird. Für das Ändern dieser Eigenschaft ist eine neue Momentaufnahme erforderlich.|  
|**publication_compatibility_level**|**100RTM**|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
||**90RTM**|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|  
|**publish_to_activedirectory**|**true**|Dieser Parameter wurde als veraltet markiert und wird nur zum Sicherstellen der Abwärtskompatibilität von Skripts unterstützt. Sie können Active Directory nicht länger Veröffentlichungsinformationen hinzufügen.|  
||**false**|Entfernt die Veröffentlichungsinformationen aus Active Directory.|  
|**replicate_ddl**|**1**|Auf dem Verleger ausgeführte DDL-Anweisungen (Data Definition Language, Datendefinitionssprache) werden repliziert.|  
||**0**|DDL-Anweisungen werden nicht repliziert.|  
|**zurück**||Dabei handelt es sich um einen **int** -Wert, der die Anzahl der *retention_period_unit* Einheiten darstellt, für die Änderungen für die angegebene Veröffentlichung gespeichert werden sollen. Wenn das Abonnement nicht innerhalb der Beibehaltungsdauer synchronisiert wird und die ausstehenden Änderungen von einem Cleanupvorgang auf dem Verteiler entfernt wurden, läuft das Abonnement ab und muss erneut initialisiert werden. Die maximal zulässige Beibehaltungsdauer entspricht der Anzahl von Tagen zwischen dem 31. Dezember 9999 und dem aktuellen Datum.<br /><br /> Hinweis: die Beibehaltungs Dauer für Mergeveröffentlichungen hat eine 24-Stunden-Toleranz Periode, um Abonnenten in unterschiedlichen Zeitzonen zu berücksichtigen.|  
|**retention_period_unit**|**day**|Die Beibehaltungsdauer wird in Tagen angegeben.|  
||**week**|Die Beibehaltungsdauer wird in Wochen angegeben.|  
||**month**|Die Beibehaltungsdauer wird in Monaten angegeben.|  
||**year**|Die Beibehaltungsdauer wird in Jahren angegeben.|  
|**snapshot_in_defaultfolder**|**true**|Momentaufnahmedateien werden im Standardmomentaufnahmeordner gespeichert.|  
||**false**|Momentaufnahme Dateien werden an dem alternativen Speicherort gespeichert, der durch *alt_snapshot_folder*angegeben wird. Diese Kombination gibt an, dass die Momentaufnahmedateien sowohl im Standardspeicherort als auch in alternativen Speicherorten gespeichert werden.|  
|**snapshot_ready**|**true**|Die Momentaufnahme für die Veröffentlichung ist verfügbar.|  
||**false**|Die Momentaufnahme für die Veröffentlichung ist nicht verfügbar.|  
|**status**|**active**|Die Veröffentlichung weist einen aktiven Status auf.|  
||**inactive**|Die Veröffentlichung weist einen inaktiven Status auf.|  
|**sync_mode**|**native** oder<br /><br /> **bcp Native**|Massenkopierprogramm-Ausgabe aller Tabellen im einheitlichen Modus wird für die Anfangsmomentaufnahme verwendet.|  
||**Art**<br /><br /> oder **bcp-Zeichen**|Massenkopierprogramm-Ausgabe aller Tabellen im Zeichenmodus wird für die Anfangsmomentaufnahme verwendet. Dies ist für alle Nicht-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Abonnenten erforderlich.|  
|**use_partition_groups**<br /><br /> Hinweis: Wenn Sie partition_groups verwenden, die Verwendung von **setupes**wiederherstellen und **use_partition_groups = false** im **changemergearticle**festlegen, wird dies möglicherweise nicht ordnungsgemäß wiedergegeben, nachdem eine Momentaufnahme erstellt wurde. Die Trigger, die von der Momentaufnahme generiert werden, sind mit Partitionsgruppen kompatibel.<br /><br /> Die Problem Umgehung für dieses Szenario besteht darin, den Status auf "inaktiv" festzulegen, die **use_partition_groups**zu ändern und dann den Status "aktiv" festzulegen.|**true**|Die Veröffentlichung verwendet vorausberechnete Partitionen.|  
||**false**|Die Veröffentlichung verwendet keine vorausberechneten Partitionen.|  
|**validate_subscriber_info**||Listet die Funktionen auf, die zum Abrufen von Abonnenteninformationen verwendet werden. Überprüft anschließend die dynamischen Filterkriterien, die für den Abonnenten verwendet werden, um zu überprüfen, dass die Informationen konsistent partitioniert werden.|  
|**web_synchronization_url**||Der Standardwert für die Internet-URL, die für die Websynchronisierung verwendet wird.|  
|NULL (Standard)||Gibt die Liste der unterstützten Werte für die- *Eigenschaft*zurück.|  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot`Bestätigt, dass die von dieser gespeicherten Prozedur ausgeführte Aktion eine vorhandene Momentaufnahme für ungültig erklären kann. *force_invalidate_snapshot* ist ein **Bit**, der Standardwert ist **0**.  
  
 der Wert **0** gibt an, dass die Momentaufnahme durch eine Änderung der Veröffentlichung nicht ungültig wird. Wenn die gespeicherte Prozedur erkennt, dass die Änderungen eine neue Momentaufnahme erfordern, tritt ein Fehler auf und es werden keine Änderungen vorgenommen.  
  
 der Wert **1** gibt an, dass das Ändern der Veröffentlichung die Momentaufnahme möglicherweise nicht überprüft Wenn Abonnements vorhanden sind, die eine neue Momentaufnahme erfordern, wird die Berechtigung erteilt, die vorhandene Momentaufnahme als veraltet zu markieren und eine neue Momentaufnahme zu generieren.  
  
 Weitere Informationen zu den Eigenschaften, bei deren Änderung die Generierung einer neuen Momentaufnahme erforderlich ist, finden Sie im Abschnitt mit den Hinweisen.  
  
`[ @force_reinit_subscription = ] force_reinit_subscription`Bestätigt, dass die von dieser gespeicherten Prozedur ausgeführte Aktion möglicherweise erfordert, dass vorhandene Abonnements erneut initialisiert werden. *force_reinit_subscription* ist ein **Bit** mit einem Standardwert von **0**.  
  
 der Wert **0** gibt an, dass das Ändern der Veröffentlichung nicht erfordert, dass Abonnements erneut initialisiert werden. Wenn die gespeicherte Prozedur erkennt, dass die Änderung die Neuinitialisierung vorhandener Abonnements erfordert, tritt ein Fehler auf, und es werden keine Änderungen durchgeführt.  
  
 der Wert **1** gibt an, dass das Ändern der Veröffentlichung bewirkt, dass vorhandene Abonnements erneut initialisiert werden, und erteilt die Berechtigung für die erneute Initialisierung des Abonnements.  
  
 Weitere Informationen zu den Eigenschaften, bei deren Änderung die erneute Initialisierung aller vorhandenen Abonnements erforderlich ist, finden Sie im Abschnitt "Hinweise".  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_changemergepublication** wird bei der Mergereplikation verwendet.  
  
 Das Ändern der folgenden Eigenschaften erfordert die Generierung einer neuen Momentaufnahme. Sie müssen den Wert **1** für den *force_invalidate_snapshot* -Parameter angeben.  
  
-   **alt_snapshot_folder**  
  
-   **compress_snapshot**  
  
-   **dynamic_filters**  
  
-   **ftp_address**  
  
-   **ftp_login**  
  
-   **ftp_password**  
  
-   **ftp_port**  
  
-   **ftp_subdirectory**  
  
-   **post_snapshot_script**  
  
-   **publication_compatibility_level** (nur bis **80SP3** )  
  
-   **pre_snapshot_script**  
  
-   **snapshot_in_defaultfolder**  
  
-   **sync_mode**  
  
-   **use_partition_groups**  
  
 Für das Ändern der folgenden Eigenschaften ist eine erneute Initialisierung von vorhandenen Abonnements erforderlich. Sie müssen den Wert **1** für den *force_reinit_subscription* -Parameter angeben.  
  
-   **dynamic_filters**  
  
-   **validate_subscriber_info**  
  
 Zum Auflisten von Veröffentlichungs Objekten, die mit dem *publish_to_active_directory*Active Directory werden sollen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] muss das Objekt bereits in Active Directory erstellt werden.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_changemergepublication](../../relational-databases/replication/codesnippet/tsql/sp-changemergepublicatio_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_changemergepublication**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen und Ändern von Veröffentlichungseigenschaften](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Ändern von Veröffentlichungs-und Artikeleigenschaften](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addmergepublication &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)   
 [sp_dropmergepublication &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql.md)   
 [sp_helpmergepublication &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
