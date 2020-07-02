---
title: sp_changemergearticle (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/09/2015
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changemergearticle_TSQL
- sp_changemergearticle
helpviewer_keywords:
- sp_changemergearticle
ms.assetid: 0dc3da5c-4af6-45be-b5f0-074da182def2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 97c6a7d309578ebe0cc6e93b5408ad6d9fad6296
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85771505"
---
# <a name="sp_changemergearticle-transact-sql"></a>sp_changemergearticle (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Ändert die Eigenschaften eines Mergeartikels. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_changemergearticle [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
    [ , [ @property = ] 'property' ]  
    [ , [ @value = ] 'value' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung, in der der Artikel vorhanden ist. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @article = ] 'article'`Der Name des Artikels, der geändert werden soll. der *Artikel* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @property = ] 'property'`Die Eigenschaft, die für den angegebenen Artikel und die angegebene Veröffentlichung geändert werden soll. die *Eigenschaft* ist vom Datentyp **nvarchar (30)**, und es kann sich um einen der in der Tabelle aufgeführten Werte handeln.  
  
`[ @value = ] 'value'`Der neue Wert für die angegebene Eigenschaft. der Wert ist vom Datentyp **nvarchar (1000)**. der *Wert* kann einer der in der Tabelle aufgeführten Werte sein.  
  
 Diese Tabelle beschreibt die Eigenschaften von Artikeln und die Werte für diese Eigenschaften.  
  
|Eigenschaft|Werte|BESCHREIBUNG|  
|--------------|------------|-----------------|  
|**allow_interactive_resolver**|**true**|Aktiviert die Verwendung eines interaktiven Konfliktlösers für den Artikel.|  
||**false**|Deaktiviert die Verwendung eines interaktiven Konfliktlösers für den Artikel.|  
|**article_resolver**||Benutzerdefinierter Konfliktlöser für den Artikel Gilt nur für einen Tabellen Artikel.|  
|**check_permissions** (Bitmap)|**0x00**|Berechtigungen auf Tabellenebene werden nicht überprüft.|  
||**0x10**|Berechtigungen auf Tabellenebene werden beim Verleger überprüft, bevor beim Abonnenten ausgeführte INSERT-Anweisungen auf den Verleger angewendet werden.|  
||**0x20**|Berechtigungen auf Tabellenebene werden beim Verleger überprüft, bevor beim Abonnenten ausgeführte UPDATE-Anweisungen auf den Verleger angewendet werden.|  
||**0x40**|Berechtigungen auf Tabellenebene werden beim Verleger überprüft, bevor DELETE-Anweisungen beim Abonnenten auf den Verleger angewendet werden.|  
|**column_tracking**|**true**|Aktiviert die Protokollierung auf Spaltenebene. Gilt nur für einen Tabellen Artikel.<br /><br /> Hinweis: die Nachverfolgung auf Spaltenebene kann nicht verwendet werden, wenn Tabellen mit mehr als 246 Spalten veröffentlicht werden.|  
||**false**|Deaktiviert die Protokollierung auf Spaltenebene und belässt die Konflikterkennung auf der Zeilenebene. Gilt nur für einen Tabellen Artikel.|  
|**compensate_for_errors**|**true**|Wenn bei der Synchronisierung Fehler auftreten, werden kompensierende Aktionen ausgeführt. Weitere Informationen finden Sie unter [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md).|  
||**false**|Es werden keine kompensierenden Aktionen ausgeführt. Dies ist das Standardverhalten. Weitere Informationen finden Sie unter [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md).<br /><br /> Wichtig Obwohl die Daten in den betroffenen Zeilen möglicherweise nicht übereinstimmen, sobald Sie Fehler beheben, können Änderungen übernommen werden, und die Daten werden konvergiert. ** \* \* \* \* ** Wenn die Quell Tabelle für einen Artikel bereits in einer anderen Veröffentlichung veröffentlicht wurde, muss der Wert von *compensate_for_errors* für beide Artikel identisch sein.|  
|**creation_script**||Pfad und Name eines optionalen Artikelschemaskripts, mit dem der Artikel in der Abonnementdatenbank erstellt wurde|  
|**delete_tracking**|**true**|DELETE-Anweisungen werden repliziert. Dies ist das Standardverhalten.|  
||**false**|DELETE-Anweisungen werden nicht repliziert.<br /><br /> Eine ** \* \* wichtige \* Einstellung \* ** **delete_tracking** **false** führt zu einer nicht Konvergenz, und gelöschte Zeilen müssen manuell entfernt werden.|  
|**description**||Beschreibungseintrag für den Artikel.|  
|**destination_owner**||Der Name des Besitzers des Objekts in der Abonnement Datenbank, wenn es sich nicht um **dbo**handelt.|  
|**identity_range**||**bigint** , das die beim Zuweisen neuer Identitäts Werte zu verwendende Bereichs Größe angibt, wenn für den Artikel **identityrangemanagementoption** auf **Auto** oder **auto_identity_range** auf **true**festgelegt ist. Gilt nur für einen Tabellenartikel. Weitere Informationen finden Sie im Abschnitt "Mergereplikation" unter [Replizieren von Identitäts Spalten](../../relational-databases/replication/publish/replicate-identity-columns.md).|  
|**identityrangemanagementoption**|**Manuell**|Deaktiviert die automatische Verwaltung des Identitätsbereichs. Kennzeichnet Identitätsspalten mithilfe von NOT FOR REPLICATION, um die manuelle Handhabung des Identitätsbereichs zu aktivieren. Weitere Informationen finden Sie unter [Replizieren von Identitätsspalten](../../relational-databases/replication/publish/replicate-identity-columns.md).|  
||**keine**|Deaktiviert die gesamte Verwaltung des Identitätsbereichs.|  
|**logical_record_level_conflict_detection**|**true**|Ein Konflikt wird erkannt, wenn an einer beliebigen Stelle im logischen Datensatz Änderungen vorgenommen werden. Erfordert, dass **logical_record_level_conflict_resolution** auf **true**festgelegt werden.|  
||**false**|Die Standard Konflikterkennung wird wie durch **column_tracking**angegeben verwendet.|  
|**logical_record_level_conflict_resolution**|**true**|Der gesamte gewinnende logische Datensatz überschreibt den verlierenden logischen Datensatz.|  
||**false**|Die Gewinnerzeilen sind nicht auf den logischen Datensatz eingeschränkt.|  
|**partition_options**|**0**|Das Filtern für den Artikel ist entweder statisch oder ergibt keine eindeutige Teilmenge von Daten für jede Partition, d. h. eine "überlappende" Partition.|  
||**1**|Die Partitionen überlappen, und beim Abonnenten vorgenommene DML-Updates können nicht die Partition ändern, zu der eine Zeile gehört.|  
||**2**|Das Filtern für den Artikel ergibt nicht überlappende Partitionen. Mehrere Abonnenten können jedoch die gleiche Partition erhalten.|  
||**3**|Das Filtern für den Artikel ergibt nicht überlappende Partitionen, die für jedes Abonnement eindeutig sind.<br /><br /> Hinweis: Wenn Sie für **partition_options**den Wert **3** angeben, kann in diesem Artikel nur ein einzelnes Abonnement für jede Daten Partition vorhanden sein. Wird ein zweites Abonnement erstellt, in dem das Filterkriterium des neuen Abonnements die gleiche Partition ergibt wie das vorhandene Abonnement, wird das vorhandene Abonnement gelöscht.|  
|**pre_creation_command**|**keine**|Wenn die Tabelle bereits auf dem Abonnenten vorhanden ist, wird keine Aktion ausgeführt.|  
||**delete**|Ein Löschvorgang wird auf der Grundlage der WHERE-Klausel im Teilmengenfilter ausgegeben.|  
||**Dropdown**|Die Tabelle wird vor dem erneuten Erstellen gelöscht.|  
||**TRUNCATE**|Schneidet die Zieltabelle ab.|  
|**processing_order**||**int** , der die Verarbeitungsreihenfolge von Artikeln in einer Mergeveröffentlichung angibt.|  
|**pub_identity_range**||**bigint** , das die Bereichs Größe angibt, die einem Abonnenten mit einem Server Abonnement zugewiesen wird, wenn für den Artikel **identityrangemanagementoption** auf **Auto** oder **auto_identity_range** auf **true**festgelegt ist. Dieser Identitätsbereich ist für einen Wiederveröffentlichungsabonnenten für die Zuordnung zu dessen Abonnenten reserviert. Gilt nur für einen Tabellenartikel. Weitere Informationen finden Sie im Abschnitt "Mergereplikation" unter [Replizieren von Identitäts Spalten](../../relational-databases/replication/publish/replicate-identity-columns.md).|  
|**published_in_tran_pub**|**true**|Der Artikel wird zusätzlich in einer Transaktionsveröffentlichung veröffentlicht.|  
||**false**|Der Artikel wird nicht zusätzlich in einer Transaktionsveröffentlichung veröffentlicht.|  
|**resolver_info**||Wird für die Angabe zusätzlicher Informationen verwendet, die für einen benutzerdefinierten Konfliktlöser erforderlich sind. Einige der [!INCLUDE[msCoName](../../includes/msconame-md.md)]-Konfliktlöser erfordern eine Spalte, die als Eingabe für den Konfliktlöser dient. **resolver_info** ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL. Weitere Informationen finden Sie unter [Microsoft COM-basierte Konfliktlöser](../../relational-databases/replication/merge/advanced-merge-replication-conflict-com-based-resolvers.md).|  
|**schema_option** (Bitmap)||Weitere Informationen finden Sie im Abschnitt mit den Hinweisen weiter unten in diesem Thema.|  
||**0x00**|Deaktiviert die Skripterstellung durch den Momentaufnahmen-Agent und verwendet das Skript, das in **creation_script**bereitgestellt wird.|  
||**0x01**|Generiert das Objekterstellungsskript (CREATE TABLE, CREATE PROCEDURE usw.).|  
||**0x10**|Generiert einen entsprechenden gruppierten Index.|  
||**0x20**|Konvertiert benutzerdefinierte Datentypen auf dem Abonnenten in Basisdatentypen. Die Option kann nicht verwendet werden, wenn eine CHECK- oder DEFAULT-Einschränkung für eine Spalte von einem benutzerdefinierten Typ ( User-defined Type, UDT) vorhanden ist, wenn eine UDT-Spalte Teil des Primärschlüssels ist oder wenn eine berechnete Spalte auf eine UDT-Spalte verweist.|  
||**0x40**|Generiert entsprechende nicht gruppierte Indizes.|  
||**0x80**|Schließt die deklarative referenzielle Integrität für die Primärschlüssel ein.|  
||**0x100**|Repliziert Benutzertrigger für einen Tabellenartikel, wenn definiert.|  
||**0x200**|Repliziert FOREIGN KEY-Einschränkungen. Wenn die Tabelle, auf die verwiesen wird, nicht Teil einer Veröffentlichung ist, werden für eine veröffentlichte Tabelle keine FOREIGN KEY-Einschränkungen repliziert.|  
||**0x400**|Repliziert Check-Einschränkungen.|  
||**0x800**|Repliziert Standards.|  
||**0x1000**|Repliziert die Sortierung auf Spaltenebene.|  
||**0x2000**|Repliziert erweiterte Eigenschaften, die dem Quellobjekt des veröffentlichten Artikels zugeordnet sind.|  
||**0x4000**|Repliziert eindeutige Schlüssel, wenn auf einem Tabellenartikel definiert.|  
||**0x8000**|Generiert ALTER TABLE-Anweisungen beim Erstellen von Skripts mit Einschränkungen.|  
||**0x10000**|Repliziert CHECK-Einschränkungen als NOT FOR REPLICATION, sodass die Einschränkungen während der Synchronisierung nicht erzwungen werden.|  
||**0x20000**|Repliziert FOREIGN KEY-Einschränkungen als NOT FOR REPLICATION, sodass diese Einschränkungen bei der Synchronisierung nicht erzwungen werden.|  
||**0x40000**|Repliziert Dateigruppen, die mit einer partitionierten Tabelle oder einem Index verbunden sind.|  
||**0x80000**|Repliziert das Partitionsschema für eine partitionierte Tabelle.|  
||**0x100000**|Repliziert das Partitionsschema für einen partitionierten Index.|  
||**0x200000**|Repliziert Tabellenstatistiken.|  
||**0x400000**|Repliziert Standard Bindungen.|  
||**0x800000**|Repliziert Regelbindungen.|  
||**0x1000000**|Repliziert den Volltextindex.|  
||**0x2000000**|An **XML** -Spalten gebundene XML-Schema Auflistungen werden nicht repliziert.|  
||**0x4000000**|Repliziert Indizes für **XML** -Spalten.|  
||**0x8000000**|Legt Schemas an, die auf dem Abonnent noch nicht vorhanden sind.|  
||**0x10000000**|Konvertiert **XML** -Spalten in **ntext** auf dem Abonnenten.|  
||**0x20000000**|Konvertiert große Objekt Datentypen (**nvarchar (max)**, **varchar (max)** und **varbinary (max)**), die in eingeführt wurden, in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Datentypen, die in unterstützt werden [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] .|  
||**0x40000000**|Berechtigungen für die Replikation.|  
||**0x80000000**|Der Versuch, Abhängigkeiten für Objekte zu löschen, die nicht Teil der Veröffentlichung sind.|  
||**0x100000000**|Verwenden Sie diese Option, um das FILESTREAM-Attribut zu replizieren, wenn es für **varbinary (max)** -Spalten angegeben wird. Geben Sie diese Option nicht an, wenn Sie Tabellen auf [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]-Abonnenten replizieren. Das Replizieren von Tabellen mit FILESTREAM-Spalten auf [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Abonnenten wird unabhängig davon, wie diese Schema Option festgelegt ist, nicht unterstützt. Siehe Verwandte Option **0x800000000**.|  
||**0x200000000**|Konvertiert Datums-und Uhrzeit Datentypen (**Date**, **time**, **DateTimeOffset**und **datetime2**), die in eingeführt wurden, in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Datentypen, die in früheren Versionen von unterstützt werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
||**0x400000000**|Repliziert die Komprimierungsoption für Daten und Indizes. Weitere Informationen finden Sie unter [Data Compression](../../relational-databases/data-compression/data-compression.md).|  
||**0x800000000**|Legen Sie diese Option fest, um FILESTREAM-Daten in einer eigenen Dateigruppe auf dem Abonnenten zu speichern. Wenn diese Option nicht festgelegt wird, werden FILESTREAM-Daten in der Standarddateigruppe gespeichert. Bei der Replikation werden keine Dateigruppen erstellt. Daher müssen Sie beim Festlegen dieser Option die Dateigruppe erstellen, bevor Sie die Momentaufnahme auf dem Abonnenten anwenden. Weitere Informationen zum Erstellen von Objekten vor dem Anwenden der Momentaufnahme finden Sie unter [Ausführen von Skripts vor und nach dem Anwenden der](../../relational-databases/replication/snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied)Momentaufnahme.<br /><br /> Siehe Verwandte Option **0x100000000**.|  
||**0x1000000000**|Konvertiert Common Language Runtime (CLR)-benutzerdefinierten Typen (User-Defined Types, UDTs) in **varbinary (max)** , sodass Spalten vom Typ UDT auf Abonnenten repliziert werden können, auf denen ausgeführt wird [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .|  
||**0x2000000000**|Konvertiert den **hierarchyid** -Datentyp in **varbinary (max)** , sodass Spalten vom Typ **hierarchyid** auf Abonnenten repliziert werden können, auf denen ausgeführt wird [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] . Weitere Informationen zur Verwendung von **hierarchyid** -Spalten in replizierten Tabellen finden Sie unter [hierarchyid &#40;Transact-SQL-&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md).|  
||**0x4000000000**|Repliziert die gefilterten Indizes in der Tabelle. Weitere Informationen zu gefilterten Indizes finden Sie unter [Erstellen von gefilterten Indizes](../../relational-databases/indexes/create-filtered-indexes.md).|  
||**0x8000000000**|Konvertiert den **geography** -Datentyp und den **Geometry** -Datentyp in **varbinary (max)** , sodass Spalten dieser Typen auf Abonnenten repliziert werden können, auf denen ausgeführt wird [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .|  
||**0x10000000000**|Repliziert Indizes für Spalten vom Typ **geography** und **Geometry**.|  
||NULL|Das System generiert automatisch eine gültige Schemaoption für den Artikel.|  
|**status**|**active**|Das Anfangsverarbeitungsskript zur Veröffentlichung der Tabelle wird ausgeführt.|  
||**unsynced**|Das Anfangsverarbeitungsskript zum Veröffentlichen der Tabelle wird ausgeführt, wenn der Momentaufnahme-Agent das nächste Mal ausgeführt wird.|  
|**stream_blob_columns**|**true**|Beim Replizieren von BLOB-Spalten (Binary Large Object) wird eine Datenstromoptimierung verwendet. Bestimmte Funktionalitäten der Mergereplikation, wie z. B. logische Datensätze, können jedoch weiterhin verhindern, dass die Datenstromoptimierung verwendet wird. *stream_blob_columns* ist auf true festgelegt, wenn FILESTREAM aktiviert ist. Dadurch werden die Replikation der FILESTREAM-Daten optimal ausgeführt und die Arbeitsspeicherauslastung reduziert. Um FILESTREAM-Tabellen Artikel zu zwingen, kein BLOB-Streaming zu verwenden, legen Sie *stream_blob_columns* auf false fest.<br /><br /> Wichtig die Aktivierung dieser Speicher Optimierung kann die Leistung der Merge-Agent während der Synchronisierung beeinträchtigen. ** \* \* \* \* ** Die Option sollte nur verwendet werden, wenn Spalten mit Megabytes von Daten repliziert werden.|  
||**false**|Beim Replizieren von BLOB-Spalten (Binary Large Object) wird die Optimierung nicht verwendet.|  
|**subscriber_upload_options**|**0**|Keine Einschränkungen für Updates, die bei einem Abonnenten mit einem Clientabonnement vorgenommen werden. Änderungen werden auf den Verleger hochgeladen. Für das Ändern dieser Eigenschaft ist möglicherweise eine erneute Initialisierung von vorhandenen Abonnenten erforderlich.|  
||**1**|Änderungen sind bei einem Abonnenten mit einem Clientabonnement zulässig, werden jedoch nicht auf den Verleger hochgeladen.|  
||**2**|Änderungen sind bei einem Abonnenten mit einem Clientabonnement nicht zulässig.|  
|**subset_filterclause**||WHERE-Klausel für das horizontale Filtern. Gilt nur für einen Tabellen Artikel.<br /><br /> Wichtig aus Leistungsgründen wird empfohlen, dass Sie keine Funktionen auf Spaltennamen in parametrisierten Zeilen Filter Klauseln anwenden, wie z. b.. ** \* \* \* \* ** `LEFT([MyColumn]) = SUSER_SNAME()` Wenn Sie [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) in einer Filter Klausel verwenden und den HOST_NAME Wert überschreiben, müssen Sie möglicherweise Datentypen mithilfe von [Convert](../../t-sql/functions/cast-and-convert-transact-sql.md)konvertieren. Weitere Informationen zu bewährten Methoden für diesen Fall finden Sie im Abschnitt "Überschreiben des HOST_NAME ()-Werts" in [parametrisierten Zeilen filtern](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).|  
|**threshold**||Prozentwert, der für Abonnenten verwendet wird, die [!INCLUDE[ssEW](../../includes/ssew-md.md)] oder frühere Versionen von ausführen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . **Schwellenwert** steuert, wenn der Merge-Agent einen neuen Identitäts Bereich zuweist. Wenn der im Schwellenwert angegebene Prozentsatz verwendet wird, erstellt der Merge-Agent einen neuen Identitätsbereich. Wird verwendet, wenn " **identityrangemanagementoption** " auf " **Auto** " oder " **auto_identity_range** auf" **true**"festgelegt ist. Gilt nur für einen Tabellenartikel. Weitere Informationen finden Sie im Abschnitt "Mergereplikation" unter [Replizieren von Identitäts Spalten](../../relational-databases/replication/publish/replicate-identity-columns.md).|  
|**verify_resolver_signature**|**1**|Die digitale Signatur in einem benutzerdefinierten Konfliktlöser wird überprüft, um festzustellen, ob er aus einer vertrauenswürdigen Quelle stammt.|  
||**0**|Die digitale Signatur in einem benutzerdefinierten Konfliktlöser wird nicht überprüft, um festzustellen, ob er aus einer vertrauenswürdigen Quelle stammt.|  
|NULL (Standard)||Gibt die Liste der unterstützten Werte für die- *Eigenschaft*zurück.|  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot`Bestätigt, dass die von dieser gespeicherten Prozedur ausgeführte Aktion eine vorhandene Momentaufnahme für ungültig erklären kann. *force_invalidate_snapshot* ist ein **Bit**, der Standardwert ist **0**.  
  
 der Wert **0** gibt an, dass Änderungen am Mergeartikel nicht bewirken, dass die Momentaufnahme ungültig wird. Wenn die gespeicherte Prozedur erkennt, dass die Änderungen eine neue Momentaufnahme erfordern, tritt ein Fehler auf und es werden keine Änderungen vorgenommen.  
  
 **1** bedeutet, dass Änderungen am Mergeartikel bewirken können, dass die Momentaufnahme ungültig ist, und wenn Abonnements vorhanden sind, die eine neue Momentaufnahme erfordern, wird die Berechtigung erteilt, die vorhandene Momentaufnahme als veraltet zu markieren und eine neue Momentaufnahme zu generieren.  
  
 Weitere Informationen zu den Eigenschaften, bei deren Änderung die Generierung einer neuen Momentaufnahme erforderlich ist, finden Sie im Abschnitt "Hinweise".  
  
`[ @force_reinit_subscription = ] force_reinit_subscription`Bestätigt, dass die von dieser gespeicherten Prozedur ausgeführte Aktion möglicherweise erfordert, dass vorhandene Abonnements erneut initialisiert werden. *force_reinit_subscription* ist ein **Bit**, der Standardwert ist **0**.  
  
 der Wert **0** gibt an, dass Änderungen am Mergeartikel nicht bewirken, dass das Abonnement erneut initialisiert wird. Wenn die gespeicherte Prozedur erkennt, dass die Änderung die Neuinitialisierung vorhandener Abonnements erfordert, tritt ein Fehler auf, und es werden keine Änderungen durchgeführt.  
  
 **1** bedeutet, dass Änderungen am Mergeartikel bewirken, dass vorhandene Abonnements erneut initialisiert werden, und es wird die Berechtigung für die erneute Initialisierung des Abonnements erteilt.  
  
 Weitere Informationen zu den Eigenschaften, bei deren Änderung die erneute Initialisierung aller vorhandenen Abonnements erforderlich ist, finden Sie im Abschnitt "Hinweise".  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_changemergearticle** wird bei der Mergereplikation verwendet.  
  
 Da **sp_changemergearticle** zum Ändern von Artikeleigenschaften verwendet wird, die anfänglich mit [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)angegeben wurden, finden Sie unter [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) Weitere Informationen zu diesen Eigenschaften.  
  
 Das Ändern der folgenden Eigenschaften erfordert, dass eine neue Momentaufnahme generiert wird, und Sie müssen für den *force_invalidate_snapshot* Parameter den Wert **1** angeben:  
  
-   **check_permissions**  
  
-   **column_tracking**  
  
-   **destination_owner**  
  
-   **pre_creation_command**  
  
-   **schema_options**  
  
-   **subset_filterclause**  
  
 Zum Ändern der folgenden Eigenschaften müssen vorhandene Abonnements erneut initialisiert werden, und Sie müssen für den *force_reinit_subscription* Parameter den Wert **1** angeben:  
  
-   **check_permissions**  
  
-   **column_tracking**  
  
-   **destination_owner**  
  
-   **pre_creation_command**  
  
-   **identityrangemanagementoption**  
  
-   **subscriber_upload_options**  
  
-   **subset_filterclause**  
  
-   **creation_script**  
  
-   **schema_option**  
  
-   **logical_record_level_conflict_detection**  
  
-   **logical_record_level_conflict_resolution**  
  
 Wenn Sie für **partition_options**den Wert 3 angeben, werden die Metadaten immer dann bereinigt, wenn die Merge-Agent ausgeführt wird und die partitionierte Momentaufnahme schneller abläuft. Beim Verwenden dieser Option sollten Sie in Erwägung ziehen, vom Abonnenten angeforderte partitionierte Momentaufnahmen zu aktivieren. Weitere Informationen finden Sie unter [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
 Wenn Sie die **column_tracking** -Eigenschaft festlegen und die Tabelle bereits in anderen Mergeveröffentlichungen veröffentlicht ist, muss die Spalten Nachverfolgung mit dem Wert identisch sein, der von vorhandenen Artikeln basierend auf dieser Tabelle verwendet wird. Dieser Parameter ist nur für Tabellenartikel spezifisch.  
  
 Wenn mehrere Veröffentlichungen Artikel basierend auf derselben zugrunde liegenden Tabelle veröffentlichen, bewirkt das Ändern der **delete_tracking** -Eigenschaft oder der **compensate_for_errors** -Eigenschaft für einen Artikel, dass die gleichen Änderungen an den anderen Artikeln vorgenommen werden, die auf derselben Tabelle basieren.  
  
 Wenn der vom Mergeprozess verwendete Benutzername bzw. das Benutzerkonto auf dem Verleger nicht über die entsprechenden Tabellenberechtigungen verfügt, werden die ungültigen Änderungen als Konflikte protokolliert.  
  
 Wenn der Wert **schema_option**geändert wird, führt das System kein bitweises Update aus. Dies bedeutet, dass beim Festlegen von **schema_option** mithilfe **sp_changemergearticle**möglicherweise vorhandene Biteinstellungen ausgeschaltet werden. Um die vorhandenen Einstellungen beizubehalten, sollten Sie [& (Bitweises and)](../../t-sql/language-elements/bitwise-and-transact-sql.md) zwischen dem Wert, den Sie festlegen, und dem aktuellen Wert von *schema_option*ausführen, der durch Ausführen von [sp_helpmergearticle](../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md)bestimmt werden kann.  
  
> [!CAUTION]  
>  Wenn Sie viele (vielleicht Hunderte) Artikel in einer Veröffentlichung haben und **sp_changemergearticle** für einen der Artikel ausführen, kann es eine lange Zeit dauern, bis die Ausführung abgeschlossen ist.  
  
## <a name="valid-schema-option-table"></a>Tabelle gültiger Schemaoptionen  
 In der folgenden Tabelle werden die zulässigen *schema_option*Werte in Abhängigkeit vom Artikeltyp beschrieben.  
  
|Artikeltyp|Schemaoptionswerte|  
|------------------|--------------------------|  
|**func schema only**|**0x01** und **0x2000**|  
|**indexed view schema only**|**0x01**, **0x040**, **0x0100**, **0x2000**, **0x40000**, **0x1000000**und **0x200000**|  
|**proc schema only**|**0x01** und **0x2000**|  
|**Tabelle**|Alle Optionen|  
|**view schema only**|**0x01**, **0x040**, **0x0100**, **0x2000**, **0x40000**, **0x1000000**und **0x200000**|  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_changemergearticle](../../relational-databases/replication/codesnippet/tsql/sp-changemergearticle-tr_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_changemergearticle**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen und Ändern von Artikeleigenschaften](../../relational-databases/replication/publish/view-and-modify-article-properties.md)   
 [Ändern von Veröffentlichungs-und Artikeleigenschaften](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addmergearticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)   
 [sp_dropmergearticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql.md)   
 [sp_helpmergearticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
