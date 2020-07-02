---
title: sp_addmergearticle (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergearticle
- sp_addmergearticle_TSQL
helpviewer_keywords:
- sp_addmergearticle
ms.assetid: 0df654ea-24e2-4c61-a75a-ecaa7a140a6c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ebb47597b5d08e0f14d37490304001811d0b33e6
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85786275"
---
# <a name="sp_addmergearticle-transact-sql"></a>sp_addmergearticle (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Fügt einer vorhandenen Mergeveröffentlichung einen Artikel hinzu. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addmergearticle [ @publication = ] 'publication'   
        , [ @article = ] 'article'   
        , [ @source_object = ] 'source_object'   
    [ , [ @type = ] 'type' ]   
    [ , [ @description = ] 'description' ]   
    [ , [ @column_tracking = ] 'column_tracking' ]   
    [ , [ @status = ] 'status' ]   
    [ , [ @pre_creation_cmd = ] 'pre_creation_cmd' ]   
    [ , [ @creation_script = ] 'creation_script' ]   
    [ , [ @schema_option = ] schema_option ]   
    [ , [ @subset_filterclause = ] 'subset_filterclause' ]   
    [ , [ @article_resolver = ] 'article_resolver' ]   
    [ , [ @resolver_info = ] 'resolver_info' ]   
    [ , [ @source_owner = ] 'source_owner' ]   
    [ , [ @destination_owner = ] 'destination_owner' ]   
    [ , [ @vertical_partition = ] 'vertical_partition' ]   
    [ , [ @auto_identity_range = ] 'auto_identity_range' ]   
    [ , [ @pub_identity_range = ] pub_identity_range ]   
    [ , [ @identity_range = ] identity_range ]   
    [ , [ @threshold = ] threshold ]   
    [ , [ @verify_resolver_signature = ] verify_resolver_signature ]   
    [ , [ @destination_object = ] 'destination_object' ]   
    [ , [ @allow_interactive_resolver = ] 'allow_interactive_resolver' ]   
    [ , [ @fast_multicol_updateproc = ] 'fast_multicol_updateproc' ]   
    [ , [ @check_permissions = ] check_permissions ]   
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @published_in_tran_pub = ] 'published_in_tran_pub' ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @logical_record_level_conflict_detection = ] 'logical_record_level_conflict_detection' ]  
    [ , [ @logical_record_level_conflict_resolution = ] 'logical_record_level_conflict_resolution' ]  
    [ , [ @partition_options = ] partition_options ]  
    [ , [ @processing_order = ] processing_order ]  
    [ , [ @subscriber_upload_options = ] subscriber_upload_options ]  
    [ , [ @identityrangemanagementoption = ] 'identityrangemanagementoption' ]  
    [ , [ @delete_tracking = ] delete_tracking ]  
    [ , [ @compensate_for_errors = ] 'compensate_for_errors' ]   
    [ , [ @stream_blob_columns = ] 'stream_blob_columns' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung, die den Artikel enthält. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @article = ] 'article'`Der Name des Artikels. Der Name muss innerhalb der Veröffentlichung eindeutig sein. der *Artikel* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. der *Artikel* muss sich auf dem lokalen Computer befinden, auf dem ausgeführt wird [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , und muss den Regeln für Bezeichner entsprechen.  
  
`[ @source_object = ] 'source_object'`Das Datenbankobjekt, das veröffentlicht werden soll. *source_object* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Weitere Informationen zu den Objekttypen, die mithilfe der Mergereplikation veröffentlicht werden können, finden Sie unter [Veröffentlichen von Daten und Datenbankobjekten](../../relational-databases/replication/publish/publish-data-and-database-objects.md).  
  
`[ @type = ] 'type'`Der Typ des Artikels. *Type ist vom Datentyp* **vom Datentyp sysname**. der Standardwert ist **Table**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**Tabelle** (Standard)|Tabelle mit Schema und Daten. Die Replikation überwacht die Tabelle, um die zu replizierenden Daten zu ermitteln.|  
|**func schema only**|Funktion vom Typ schema only.|  
|nur **indiziertes Sicht** **Schema**|Indizierte Sicht vom Typ schema only.|  
|**proc schema only**|Nur gespeicherte Prozedur mit Schema|  
|**nur Synonym Schema**|Nur Synonym mit Schema|  
|**view schema only**|Sicht vom Typ schema only.|  
  
`[ @description = ] 'description'`Ist eine Beschreibung des Artikels. die *Beschreibung* ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL.  
  
`[ @column_tracking = ] 'column_tracking'`Die Einstellung für die Nachverfolgung auf Spaltenebene. *column_tracking* ist vom Datentyp **nvarchar (10)** und hat den Standardwert false. **true**schaltet die Spalten Nachverfolgung ein. **false** deaktiviert die Spalten Nachverfolgung und lässt die Konflikterkennung auf Zeilenebene zu. Wenn die Tabelle bereits in anderen Mergereplikationen veröffentlicht ist, müssen Sie denselben Wert für die Spaltenprotokollierung verwenden, der von bereits bestehenden Artikeln für diese Tabelle verwendet wird. Dieser Parameter ist nur für Tabellenartikel spezifisch.  
  
> [!NOTE]  
>  Falls die Zeilennachverfolgung zur Konflikterkennung verwendet wird (Standardeinstellung), kann die Basistabelle maximal 1.024 Spalten enthalten. Die Spalten müssen jedoch im Artikel gefiltert werden, sodass maximal 246 Spalten veröffentlicht werden. Wenn Spaltennachverfolgung verwendet wird, kann die Basistabelle maximal 246 Spalten enthalten.  
  
`[ @status = ] 'status'`Der Status des Artikels. *Status* ist vom Datentyp **nvarchar (10)** und hat den Standardwert **unsynchronisiert**. Wenn **aktiv**, wird das Anfangs Verarbeitungs Skript zum Veröffentlichen der Tabelle ausgeführt. Wenn die **Synchronisierungs Datei nicht synchronisiert**ist, wird das Anfangs Verarbeitungs Skript zum Veröffentlichen der Tabelle beim nächsten Ausführen des Momentaufnahmen-Agent ausgeführt.  
  
`[ @pre_creation_cmd = ] 'pre_creation_cmd'`Gibt an, was das System tun soll, wenn die Tabelle beim Anwenden der Momentaufnahme auf dem Abonnenten vorhanden ist. *pre_creation_cmd* ist vom Datentyp **nvarchar (10)**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**keine**|Wenn die Tabelle bereits auf dem Abonnenten vorhanden ist, wird keine Aktion ausgeführt.|  
|**delete**|Ein Löschvorgang wird auf der Grundlage der WHERE-Klausel im Teilmengenfilter ausgegeben.|  
|**Drop** (Standard)|Die Tabelle wird vor dem erneuten Erstellen gelöscht. Erforderlich zur Unterstützung von- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEW](../../includes/ssew-md.md)] Abonnenten.|  
|**TRUNCATE**|Schneidet die Zieltabelle ab.|  
  
`[ @creation_script = ] 'creation_script'`Der Pfad und der Name eines optionalen Artikel Schema Skripts, mit dem der Artikel in der Abonnement Datenbank erstellt wird. *creation_script* ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Erstellungsskripts werden auf [!INCLUDE[ssEW](../../includes/ssew-md.md)]-Abonnenten nicht ausgeführt.  
  
`[ @schema_option = ] schema_option`Ist eine Bitmap der Schema Generierungs Option für den angegebenen Artikel. *schema_option* ist **Binär (8)** und kann das [| (Bitweises OR)](../../t-sql/language-elements/bitwise-or-transact-sql.md) Produkt mindestens eines der folgenden Werte.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**0x00**|Deaktiviert die Skripterstellung durch den Momentaufnahmen-Agent und verwendet das in *creation_script*definierte Skript für die vorab Erstellung von Schemas.|  
|**0x01**|Generiert die Objekterstellung (CREATE TABLE, CREATE PROCEDURE usw.). Dieser Wert ist der Standardwert für alle Artikel mit gespeicherten Prozeduren.|  
|**0x10**|Generiert einen entsprechenden gruppierten Index. Auch wenn diese Option nicht festgelegt ist, werden Indizes bezüglich der Primärschlüssel und der UNIQUE-Einschränkungen generiert, falls diese für eine veröffentlichte Tabelle bereits definiert sind.|  
|**0x20**|Konvertiert benutzerdefinierte Datentypen (UDT) auf dem Abonnenten in Basisdatentypen. Diese Option kann nicht verwendet werden, wenn eine CHECK- oder DEFAULT-Einschränkung für eine UDT-Spalte vorhanden ist, wenn eine UDT-Spalte Teil des Primärschlüssels ist oder wenn eine berechnete Spalte auf eine UDT-Spalte verweist.|  
|**0x40**|Generiert entsprechende nicht gruppierte Indizes. Auch wenn diese Option nicht festgelegt ist, werden Indizes bezüglich der Primärschlüssel und der UNIQUE-Einschränkungen generiert, falls diese für eine veröffentlichte Tabelle bereits definiert sind.|  
|**0x80**|Repliziert PRIMARY KEY-Einschränkungen. Alle Indizes im Zusammenhang mit der Einschränkung werden ebenfalls repliziert, auch wenn die Optionen **0x10** und **0x40** nicht aktiviert sind.|  
|**0x100**|Repliziert Benutzertrigger für einen Tabellenartikel, wenn definiert.|  
|**0x200**|Repliziert FOREIGN KEY-Einschränkungen. Wenn die Tabelle, auf die verwiesen wird, nicht Teil einer Veröffentlichung ist, werden für eine veröffentlichte Tabelle keine FOREIGN KEY-Einschränkungen repliziert.|  
|**0x400**|Repliziert Check-Einschränkungen.|  
|**0x800**|Repliziert Standards.|  
|**0x1000**|Repliziert die Sortierung auf Spaltenebene.|  
|**0x2000**|Repliziert erweiterte Eigenschaften, die dem Quellobjekt des veröffentlichten Artikels zugeordnet sind.|  
|**0x4000**|Repliziert UNIQUE-Einschränkungen. Alle Indizes im Zusammenhang mit der Einschränkung werden ebenfalls repliziert, auch wenn die Optionen **0x10** und **0x40** nicht aktiviert sind.|  
|**0x8000**|Diese Option ist für Verleger, auf denen [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höher ausgeführt wird, nicht gültig.|  
|**0x10000**|Repliziert CHECK-Einschränkungen als NOT FOR REPLICATION, sodass die Einschränkungen während der Synchronisierung nicht erzwungen werden.|  
|**0x20000**|Repliziert FOREIGN KEY-Einschränkungen als NOT FOR REPLICATION, sodass diese Einschränkungen bei der Synchronisierung nicht erzwungen werden.|  
|**0x40000**|Repliziert Dateigruppen, die mit einer partitionierten Tabelle oder einem Index verbunden sind.|  
|**0x80000**|Repliziert das Partitionsschema für eine partitionierte Tabelle.|  
|**0x100000**|Repliziert das Partitionsschema für einen partitionierten Index.|  
|**0x200000**|Repliziert Tabellenstatistiken.|  
|**0x400000**|Repliziert Standardbindungen.|  
|**0x800000**|Repliziert Regel Bindungen.|  
|**0x1000000**|Repliziert den Volltextindex.|  
|**0x2000000**|An **XML** -Spalten gebundene XML-Schema Auflistungen werden nicht repliziert.|  
|**0x4000000**|Repliziert Indizes für **XML** -Spalten.|  
|**0x8000000**|Erstellt Schemas, die noch nicht auf dem Abonnenten vorhanden sind.|  
|**0x10000000**|Konvertiert **XML** -Spalten in **ntext** auf dem Abonnenten.|  
|**0x20000000**|Konvertiert große Objekt Datentypen (**nvarchar (max)**, **varchar (max)** und **varbinary (max)**), die in eingeführt wurden, in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Datentypen, die in unterstützt werden [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] .|  
|**0x40000000**|Repliziert Berechtigungen.|  
|**0x80000000**|Versucht, Abhängigkeiten von Objekten zu löschen, die nicht Teil der Veröffentlichung sind.|  
|**0x100000000**|Verwenden Sie diese Option, um das FILESTREAM-Attribut zu replizieren, wenn es für **varbinary (max)** -Spalten angegeben wird. Geben Sie diese Option nicht an, wenn Sie Tabellen auf [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]-Abonnenten replizieren. Das Replizieren von Tabellen mit FILESTREAM-Spalten auf [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Abonnenten wird unabhängig davon, wie diese Schema Option festgelegt ist, nicht unterstützt. Siehe Verwandte Option **0x800000000**.|  
|**0x200000000**|Konvertiert Datums-und Uhrzeit Datentypen (**Date**, **time**, **DateTimeOffset**und **datetime2**), die in eingeführt wurden [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] , in Datentypen, die in früheren Versionen von unterstützt werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|**0x400000000**|Repliziert die Komprimierungsoption für Daten und Indizes. Weitere Informationen finden Sie unter [Data Compression](../../relational-databases/data-compression/data-compression.md).|  
|**0x800000000**|Legen Sie diese Option fest, um FILESTREAM-Daten in einer eigenen Dateigruppe auf dem Abonnenten zu speichern. Wenn diese Option nicht festgelegt wird, werden FILESTREAM-Daten in der Standarddateigruppe gespeichert. Bei der Replikation werden keine Dateigruppen erstellt. Daher müssen Sie beim Festlegen dieser Option die Dateigruppe erstellen, bevor Sie die Momentaufnahme auf dem Abonnenten anwenden. Weitere Informationen zum Erstellen von Objekten vor dem Anwenden der Momentaufnahme finden Sie unter [Ausführen von Skripts vor und nach dem Anwenden der](../../relational-databases/replication/snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied)Momentaufnahme.<br /><br /> Siehe Verwandte Option **0x100000000**.|  
|**0x1000000000**|Konvertiert Common Language Runtime (CLR)-benutzerdefinierten Typen (User-Defined Types, UDTs) in **varbinary (max)** , sodass Spalten vom Typ UDT auf Abonnenten repliziert werden können, auf denen ausgeführt wird [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .|  
|**0x2000000000**|Konvertiert den **hierarchyid** -Datentyp in **varbinary (max)** , sodass Spalten vom Typ **hierarchyid** auf Abonnenten repliziert werden können, auf denen ausgeführt wird [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] . Weitere Informationen zur Verwendung von **hierarchyid** -Spalten in replizierten Tabellen finden Sie unter [hierarchyid &#40;Transact-SQL-&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md).|  
|**0x4000000000**|Repliziert die gefilterten Indizes in der Tabelle. Weitere Informationen zu gefilterten Indizes finden Sie unter [Erstellen von gefilterten Indizes](../../relational-databases/indexes/create-filtered-indexes.md).|  
|**0x8000000000**|Konvertiert den **geography** -Datentyp und den **Geometry** -Datentyp in **varbinary (max)** , sodass Spalten dieser Typen auf Abonnenten repliziert werden können, auf denen ausgeführt wird [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .|  
|**0x10000000000**|Repliziert Indizes für Spalten vom Typ **geography** und **Geometry**.|  
  
 Bei einem Wert von NULL generiert das System automatisch eine gültige Schemaoption für den Artikel. Die **Standard Schema-Options** Tabelle im Abschnitt "Hinweise" zeigt den Wert an, der basierend auf dem Artikeltyp ausgewählt wird. Außerdem sind nicht alle *schema_option* Werte für alle Replikations-und Artikeltypen gültig. Die in den Hinweisen angegebene **gültige Schema Options** Tabelle zeigt die Optionen an, die für einen bestimmten Artikeltyp angegeben werden können.  
  
> [!NOTE]  
>  Der *schema_option* Parameter wirkt sich nur auf Replikations Optionen für die Anfangs Momentaufnahme aus. Nachdem das ursprüngliche Schema vom Momentaufnahmen-Agent generiert und auf dem Abonnenten angewendet wurde, erfolgt die Replikation von Veröffentlichungs Schema Änderungen auf dem Abonnenten basierend auf den Regeln für die Schema Änderungs Replikation und der in [sp_addmergepublication](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)angegebenen *replicate_ddl* Parametereinstellung. Weitere Informationen finden Sie unter [Vornehmen von Schemaänderungen in Veröffentlichungsdatenbanken](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).  
  
`[ @subset_filterclause = ] 'subset_filterclause'`Eine WHERE-Klausel, die das horizontale Filtern eines Tabellen Artikels ohne das Wort enthält, in dem er enthalten ist. *subset_filterclause* ist vom Datentyp **nvarchar (1000)**. der Standardwert ist eine leere Zeichenfolge.  
  
> [!IMPORTANT]  
>  Aus Leistungsgründen ist es empfehlenswert, keine Funktionen auf Spaltennamen in Klauseln für parametrisierte Zeilenfilter anzuwenden, wie z. B. `LEFT([MyColumn]) = SUSER_SNAME()`. Wenn Sie [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) in einer Filter Klausel verwenden und den HOST_NAME Wert überschreiben, müssen Sie möglicherweise Datentypen mithilfe von [Convert](../../t-sql/functions/cast-and-convert-transact-sql.md)konvertieren. Weitere Informationen zu bewährten Methoden für diesen Fall finden Sie im Abschnitt "Überschreiben des HOST_NAME ()-Werts" in [parametrisierten Zeilen filtern](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
`[ @article_resolver = ] 'article_resolver'`Ist der com-basierte Konflikt Löser, der zum Auflösen von Konflikten im Tabellen Artikel verwendet wird, oder die .NET Framework Assembly, die aufgerufen wurde, um benutzerdefinierte Geschäftslogik für den Tabellen Artikel auszuführen. *article_resolver* ist vom Datentyp **varchar (255)** und hat den Standardwert NULL. Verfügbare Werte für diesen Parameter sind im Abschnitt zu benutzerdefinierten Konfliktlösern von [!INCLUDE[msCoName](../../includes/msconame-md.md)] aufgelistet. Wenn der bereitgestellte Wert nicht zu den Konfliktlösern von [!INCLUDE[msCoName](../../includes/msconame-md.md)] zählt, dann verwendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den angegebenen Konfliktlöser anstelle des vom System bereitgestellten Konfliktlösers. Verwenden Sie **sp_enumcustomresolvers** , um die Liste der verfügbaren benutzerdefinierten Resolver aufzulisten. Weitere Informationen finden Sie unter [Ausführen von Geschäftslogik während der Mergesynchronisierung](../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md) und [Erweiterte Konflikterkennung und-Lösung bei der Mergereplikation](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
`[ @resolver_info = ] 'resolver_info'`Wird verwendet, um zusätzliche Informationen anzugeben, die von einem benutzerdefinierten Konflikt Löser benötigt werden. Einige der [!INCLUDE[msCoName](../../includes/msconame-md.md)]-Konfliktlöser erfordern eine Spalte, die als Eingabe für den Konfliktlöser dient. *resolver_info* ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL. Weitere Informationen finden Sie unter [Microsoft COM-basierte Konfliktlöser](../../relational-databases/replication/merge/advanced-merge-replication-conflict-com-based-resolvers.md).  
  
`[ @source_owner = ] 'source_owner'`Der Name des Besitzers der *source_object*. *source_owner* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Bei NULL wird der aktuelle Benutzer als Besitzer angenommen.  
  
`[ @destination_owner = ] 'destination_owner'`Der Besitzer des Objekts in der Abonnement Datenbank, wenn es sich nicht um ' dbo ' handelt. *destination_owner* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Bei NULL wird dbo als Besitzer angenommen.  
  
`[ @vertical_partition = ] 'column_filter'`Aktiviert und deaktiviert die Spalten Filterung für einen Tabellen Artikel. *vertical_partition* ist vom Datentyp **nvarchar (5)** und hat den Standardwert false.  
  
 **false** gibt an, dass keine vertikale Filterung vorhanden ist und alle Spalten veröffentlicht werden.  
  
 **true** löscht alle Spalten außer den deklarierten Primärschlüssel-und ROWGUID-Spalten. Spalten werden mit **sp_mergearticlecolumn**hinzugefügt.  
  
`[ @auto_identity_range = ] 'automatic_identity_range'`Aktiviert und deaktiviert die automatische Behandlung von Identitäts Bereichen für diesen Tabellen Artikel zu einer Veröffentlichung zu dem Zeitpunkt, zu dem Sie erstellt wird. *auto_identity_range* ist vom Datentyp **nvarchar (5)** und hat den Standardwert false. **true** aktiviert die automatische Handhabung von Identitäts Bereichen, während **false** Sie deaktiviert.  
  
> [!NOTE]  
>  *auto_identity_range* wurde als veraltet markiert und wird nur aus Gründen der Abwärtskompatibilität bereitgestellt. Sie sollten die *identityrangemanagementoption* zum Angeben der Optionen für die Identitäts Bereichs Verwaltung verwenden. Weitere Informationen finden Sie unter [Replizieren von Identitätsspalten](../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
`[ @pub_identity_range = ] pub_identity_range`Steuert die Größe des Identitäts Bereichs, der einem Abonnenten mit einem Server Abonnement zugewiesen wird, wenn die automatische Identitäts Bereichs Verwaltung verwendet wird. Dieser Identitätsbereich ist für einen Wiederveröffentlichungsabonnenten für die Zuordnung zu dessen Abonnenten reserviert. *pub_identity_range* ist vom Datentyp **bigint**und hat den Standardwert NULL. Sie müssen diesen Parameter angeben, wenn " *identityrangemanagementoption* " auf " **Auto** " festgelegt ist, oder wenn *auto_identity_range* **true**ist  
  
`[ @identity_range = ] identity_range`Steuert die Größe des Identitäts Bereichs, der dem Verleger und dem Abonnenten zugeordnet wird, wenn die automatische Identitäts Bereichs Verwaltung verwendet wird. *identity_range* ist vom Datentyp **bigint**und hat den Standardwert NULL. Sie müssen diesen Parameter angeben, wenn " *identityrangemanagementoption* " auf " **Auto** " festgelegt ist, oder wenn *auto_identity_range* **true**ist  
  
> [!NOTE]  
>  *identity_range* steuert die Größe des Identitäts Bereichs bei der Wiederveröffentlichung von Abonnenten, die frühere Versionen von verwenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
`[ @threshold = ] threshold`Prozentwert, der steuert, wann der Merge-Agent einen neuen Identitäts Bereich zuweist. Wenn der in *Schwellenwert* angegebene Prozentsatz der Werte verwendet wird, erstellt der Merge-Agent einen neuen Identitäts Bereich. der *Schwellenwert* ist vom Datentyp **int**und hat den Standardwert NULL. Sie müssen diesen Parameter angeben, wenn " *identityrangemanagementoption* " auf " **Auto** " festgelegt ist, oder wenn *auto_identity_range* **true**ist  
  
`[ @verify_resolver_signature = ] verify_resolver_signature`Gibt an, ob eine digitale Signatur überprüft wird, bevor ein Konflikt Löser bei der Mergereplikation verwendet wird. *verify_resolver_signature* ist vom Datentyp **int**und hat den Standardwert 1.  
  
 der Wert **0** gibt an, dass die Signatur nicht überprüft wird.  
  
 der Wert **1** gibt an, dass die Signatur überprüft wird, um festzustellen, ob Sie aus einer vertrauenswürdigen Quelle ist.  
  
`[ @destination_object = ] 'destination_object'`Der Name des Objekts in der Abonnement Datenbank. *destination_object* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert was in ** \@ source_object**. Dieser Parameter kann nur angegeben werden, wenn der Artikel vom Typ schema only ist, wie z. B. ein Artikel für gespeicherte Prozeduren, Sichten und UDFs. Wenn es sich bei dem angegebenen Artikel um einen Tabellen Artikel handelt, überschreibt der Wert in *@source_object* den Wert in *destination_object*.  
  
`[ @allow_interactive_resolver = ] 'allow_interactive_resolver'`Aktiviert oder deaktiviert die Verwendung des interaktiven Konflikt Lösers für einen Artikel. *allow_interactive_resolver* ist vom Datentyp **nvarchar (5)** und hat den Standardwert false. **true** aktiviert die Verwendung des interaktiven Konflikt Lösers für den Artikel. **false** deaktiviert es.  
  
> [!NOTE]  
>  Der interaktive Konfliktlöser wird von [!INCLUDE[ssEW](../../includes/ssew-md.md)]-Abonnenten nicht unterstützt.  
  
`[ @fast_multicol_updateproc = ] 'fast_multicol_updateproc'`Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten.  
  
`[ @check_permissions = ] check_permissions`Ist eine Bitmap der Berechtigungen auf Tabellenebene, die überprüft werden, wenn die Merge-Agent Änderungen auf den Verleger anwendet. Wenn der vom Mergeprozess verwendete Benutzername bzw. das Benutzerkonto auf dem Verleger nicht über die entsprechenden Tabellenberechtigungen verfügt, werden die ungültigen Änderungen als Konflikte protokolliert. *check_permissions* ist vom Datentyp **int**und kann das [| (Bitweises OR)](../../t-sql/language-elements/bitwise-or-transact-sql.md) Produkt mindestens eines der folgenden Werte.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**0x00** (Standard)|Berechtigungen werden nicht überprüft.|  
|**0x10**|Überprüft Berechtigungen auf dem Verleger, bevor auf einem Abonnenten ausgeführte Einfügevorgänge hochgeladen werden können.|  
|**0x20**|Überprüft Berechtigungen auf dem Verleger, bevor auf einem Abonnenten ausgeführte Updatevorgänge hochgeladen werden können.|  
|**0x40**|Überprüft Berechtigungen auf dem Verleger, bevor auf einem Abonnenten ausgeführte Löschvorgänge hochgeladen werden können.|  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot`Bestätigt, dass die von dieser gespeicherten Prozedur ausgeführte Aktion eine vorhandene Momentaufnahme für ungültig erklären kann. *force_invalidate_snapshot* ist ein **Bit**, der Standardwert ist 0.  
  
 **0** gibt an, dass das Hinzufügen eines Artikels nicht dazu führt, dass die Momentaufnahme ungültig wird. Wenn die gespeicherte Prozedur erkennt, dass die Änderungen eine neue Momentaufnahme erfordern, tritt ein Fehler auf und es werden keine Änderungen vorgenommen.  
  
 **1** gibt an, dass das Hinzufügen eines Artikels möglicherweise dazu führt, dass die Momentaufnahme ungültig ist, und wenn Abonnements vorhanden sind, die eine neue Momentaufnahme erfordern, erteilt die Berechtigung, dass die vorhandene Momentaufnahme als veraltet markiert und eine neue Momentaufnahme generiert wird. *force_invalidate_snapshot* wird auf **1** festgelegt, wenn ein Artikel einer Veröffentlichung mit einer vorhandenen Momentaufnahme hinzugefügt wird.  
  
`[ @published_in_tran_pub = ] 'published_in_tran_pub'`Gibt an, dass ein Artikel in einer Mergeveröffentlichung auch in einer Transaktions Veröffentlichung veröffentlicht wird. *published_in_tran_pub* ist vom Datentyp **nvarchar (5)** und hat den Standardwert false. **true** gibt an, dass der Artikel auch in einer Transaktions Veröffentlichung veröffentlicht wird.  
  
`[ @force_reinit_subscription = ] force_reinit_subscription`Bestätigt, dass die von dieser gespeicherten Prozedur ausgeführte Aktion möglicherweise erfordert, dass vorhandene Abonnements erneut initialisiert werden. *force_reinit_subscription* ist ein **Bit**, der Standardwert ist 0.  
  
 der Wert **0** gibt an, dass das Hinzufügen eines Artikels nicht dazu führt, dass das Abonnement erneut initialisiert wird. Wenn die gespeicherte Prozedur erkennt, dass die Änderung die Neuinitialisierung vorhandener Abonnements erfordert, tritt ein Fehler auf, und es werden keine Änderungen durchgeführt.  
  
 **1** bedeutet, dass Änderungen am Mergeartikel bewirken, dass vorhandene Abonnements erneut initialisiert werden, und es wird die Berechtigung für die erneute Initialisierung des Abonnements erteilt. *force_reinit_subscription* wird auf **1** festgelegt, wenn *subset_filterclause* einen parametrisierten Zeilen Filter angibt.  
  
`[ @logical_record_level_conflict_detection = ] 'logical_record_level_conflict_detection'`Gibt die Ebene der Konflikterkennung für einen Artikel an, der Mitglied eines logischen Datensatzes ist. *logical_record_level_conflict_detection* ist vom Datentyp **nvarchar (5)** und hat den Standardwert false.  
  
 **true** gibt an, dass ein Konflikt erkannt wird, wenn Änderungen an einer beliebigen Stelle im logischen Datensatz vorgenommen werden.  
  
 **false** gibt an, dass die Standard Konflikterkennung verwendet wird, wie in *column_tracking*angegeben. Weitere Informationen finden Sie unter [Gruppieren von Änderungen an verknüpften Zeilen mithilfe von logischen Datensätzen](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
> [!NOTE]  
>  Da logische Datensätze von Abonnenten nicht unterstützt werden [!INCLUDE[ssEW](../../includes/ssew-md.md)] , müssen Sie für *logical_record_level_conflict_detection* den Wert **false** angeben, um diese Abonnenten zu unterstützen.  
  
`[ @logical_record_level_conflict_resolution = ] 'logical_record_level_conflict_resolution'`Gibt die Ebene der Konfliktlösung für einen Artikel an, der Mitglied eines logischen Datensatzes ist. *logical_record_level_conflict_resolution* ist vom Datentyp **nvarchar (5)** und hat den Standardwert false.  
  
 **true** gibt an, dass der gesamte gewinnende logische Datensatz den verlorenen logischen Datensatz überschreibt.  
  
 **false** gibt an, dass gewinnende Zeilen nicht auf den logischen Datensatz beschränkt sind. Wenn *logical_record_level_conflict_detection* **true**ist, muss *logical_record_level_conflict_resolution* auch auf **true**festgelegt werden. Weitere Informationen finden Sie unter [Gruppieren von Änderungen an verknüpften Zeilen mithilfe von logischen Datensätzen](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
> [!NOTE]  
>  Da logische Datensätze von Abonnenten nicht unterstützt werden [!INCLUDE[ssEW](../../includes/ssew-md.md)] , müssen Sie für *logical_record_level_conflict_resolution* den Wert **false** angeben, um diese Abonnenten zu unterstützen.  
  
`[ @partition_options = ] partition_options`Definiert die Art und Weise, in der Daten im Artikel partitioniert werden. Dies ermöglicht Leistungsoptimierungen, wenn alle Zeilen nur zu einer einzigen Partition oder zu einem einzigen Abonnement gehören. *partition_options* ist vom Datentyp **tinyint**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**0** (Standardwert)|Das Filtern für den Artikel ist entweder statisch oder ergibt keine eindeutige Untermenge von Daten für jede Partition, d. h. eine "überlappende" Partition.|  
|**1**|Die Partitionen überlappen, und beim Abonnenten vorgenommene Updates der Datenbearbeitungssprache (DML, Data Manipulation Language) können nicht die Partition ändern, zu der eine Zeile gehört.|  
|**2**|Das Filtern für den Artikel ergibt nicht überlappende Partitionen. Mehrere Abonnenten können jedoch die gleiche Partition erhalten.|  
|**3**|Das Filtern für den Artikel ergibt nicht überlappende Partitionen, die für jedes Abonnement eindeutig sind.|  
  
> [!NOTE]  
>  Wenn die Quell Tabelle für einen Artikel bereits in einer anderen Veröffentlichung veröffentlicht wurde, muss der Wert von *partition_options* für beide Artikel identisch sein.  
  
`[ @processing_order = ] processing_order`Gibt die Verarbeitungsreihenfolge von Artikeln in einer Mergeveröffentlichung an. *processing_order* ist vom Datentyp **int**und hat den Standardwert 0. **0** gibt an, dass der Artikel nicht sortiert ist, und jeder andere Wert stellt den Ordinalwert der Verarbeitungsreihenfolge für diesen Artikel dar. Artikel werden in der Reihenfolge vom niedrigsten zum höchsten Wert verarbeitet. Wenn zwei Artikel denselben Wert aufweisen, wird die Verarbeitungsreihenfolge durch die Reihenfolge der Artikel Spitzname in der [sysmergearticles](../../relational-databases/system-tables/sysmergearticles-transact-sql.md) -Systemtabelle bestimmt. Weitere Informationen finden Sie unter [Specify Merge Replication properties (Angeben von Mergereplikationseigenschaften)](../../relational-databases/replication/merge/specify-merge-replication-properties.md).  
  
`[ @subscriber_upload_options = ] subscriber_upload_options`Definiert Einschränkungen für Updates, die auf einem Abonnenten mit einem Client Abonnement vorgenommen werden. Weitere Informationen finden Sie unter [Optimieren der Leistung der Mergereplikation durch nur herunterladbare Artikel](../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md). *subscriber_upload_options* ist vom Datentyp **tinyint**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**0** (Standardwert)|Keine Einschränkungen. Auf dem Abonnenten vorgenommene Änderungen werden auf den Verleger hochgeladen.|  
|**1**|Änderungen sind auf dem Abonnenten zulässig, werden jedoch nicht auf den Verleger hochgeladen.|  
|**2**|Änderungen sind auf dem Abonnenten nicht zulässig.|  
  
 Zum Ändern *subscriber_upload_options* muss das Abonnement erneut initialisiert werden, indem [sp_reinitmergepullsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-reinitmergepullsubscription-transact-sql.md)aufgerufen wird.  
  
> [!NOTE]  
>  Wenn die Quell Tabelle für einen Artikel bereits in einer anderen Veröffentlichung veröffentlicht wurde, muss der Wert *subscriber_upload_options* für beide Artikel identisch sein.  
  
`[ @identityrangemanagementoption = ] identityrangemanagementoption`Gibt an, wie die Identitäts Bereichs Verwaltung für den Artikel behandelt wird. die *identityrangemanagementoption* ist vom Datentyp **nvarchar (10)**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**keine**|Deaktiviert die Verwaltung des Identitätsbereichs.|  
|**Manuell**|Markiert die Identitätsspalte mithilfe von NOT FOR REPLICATION, um die manuelle Identitätsbereichsverwaltung zu ermöglichen.|  
|**auto**|Gibt die automatisierte Verwaltung von Identitätsbereichen an.|  
|NULL (Standard)|Der Standardwert ist **None**, wenn der Wert von *auto_identity_range* nicht **true**ist.|  
  
 Aus Gründen der Abwärtskompatibilität, wenn der Wert von *identityrangemanagementoption* NULL ist, wird der Wert *auto_identity_range* geprüft. Wenn der Wert von *identityrangemanagementoption* jedoch nicht NULL ist, wird der Wert *auto_identity_range* ignoriert. Weitere Informationen finden Sie unter [Replizieren von Identitätsspalten](../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
`[ @delete_tracking = ] 'delete_tracking'`Gibt an, ob Löschvorgänge repliziert werden. *delete_tracking* ist vom Datentyp **nvarchar (5)** und hat den Standardwert true. **false** gibt an, dass Löschvorgänge nicht repliziert werden, und **true** gibt an, dass Löschvorgänge repliziert werden. Dies ist das übliche Verhalten der Mergereplikation Wenn *delete_tracking* auf **false**festgelegt ist, müssen auf dem Abonnenten gelöschte Zeilen manuell auf dem Verleger entfernt werden, und auf dem Verleger gelöschte Zeilen müssen manuell auf dem Abonnenten entfernt werden.  
  
> [!IMPORTANT]  
>  Wenn *delete_tracking* auf **false** festgelegt wird, führt dies zu einer nicht Konvergenz. Wenn die Quell Tabelle für einen Artikel bereits in einer anderen Veröffentlichung veröffentlicht wurde, muss der Wert von *delete_tracking* für beide Artikel identisch sein.  
  
> [!NOTE]  
>  *delete_tracking* Optionen können nicht über den **Assistenten für neue Veröffentlichung** oder das Dialogfeld **Veröffentlichungs Eigenschaften** festgelegt werden.  
  
`[ @compensate_for_errors = ] 'compensate_for_errors'`Gibt an, ob kompensierende Aktionen ausgeführt werden, wenn während der Synchronisierung Fehler auftreten. *compensate_for_errors i*s **nvarchar (5)**. der Standardwert ist false. Wenn diese Einstellung auf " **true**" festgelegt ist, führen Änderungen, die während der Synchronisierung nicht auf einen Abonnenten oder Verleger angewendet werden können, immer zu kompensierenden Aktionen, um ein falsch konfigurierter Abonnent, der einen Fehler generiert, kann jedoch dazu führen, dass Änderungen auf anderen Abonnenten und Verlegern rückgängig gemacht werden. **false** deaktiviert diese kompensierenden Aktionen. die Fehler werden jedoch weiterhin mit der Kompensierung protokolliert, und nachfolgende Zusammenführungen versuchen weiterhin, die Änderungen zu übernehmen, bis Sie erfolgreich sind.  
  
> [!IMPORTANT]  
>  Möglicherweise hat es den Anschein, dass Daten in den betroffenen Zeilen nicht konvergent sind. Beheben Sie jedoch ggf. aufgetretene Fehler, können Änderungen übernommen werden, und die Daten konvergieren. Wenn die Quell Tabelle für einen Artikel bereits in einer anderen Veröffentlichung veröffentlicht wurde, muss der Wert von *compensate_for_errors* für beide Artikel identisch sein.  
  
`[ @stream_blob_columns = ] 'stream_blob_columns'`Gibt an, dass eine Datenstrom Optimierung beim Replizieren Binary Large Object Spalten verwendet werden soll. *stream_blob_columns* ist vom Datentyp **nvarchar (5)** und hat den Standardwert false. " **true** " bedeutet, dass die Optimierung versucht wird. *stream_blob_columns* ist auf true festgelegt, wenn FILESTREAM aktiviert ist. Dadurch werden die Replikation der FILESTREAM-Daten optimal ausgeführt und die Arbeitsspeicherauslastung reduziert. Um FILESTREAM-Tabellen Artikel zu zwingen, kein BLOB-Streaming zu verwenden, verwenden Sie **sp_changemergearticle** , um *stream_blob_columns* auf false festzulegen.  
  
> [!IMPORTANT]  
>  Durch Aktivieren dieser Arbeitsspeicheroptimierung kann die Leistung des Merge-Agents bei der Synchronisierung beeinträchtigt werden. Die Option sollte nur verwendet werden, wenn Spalten mit Megabytes von Daten repliziert werden.  
  
> [!NOTE]  
>  Bestimmte Funktionen für die Mergereplikation, z. b. logische Datensätze, können weiterhin verhindern, dass die Datenstrom Optimierung beim Replizieren von binären großen Objekten verwendet wird, auch wenn *stream_blob_columns* auf **true**festgelegt  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_addmergearticle** wird bei der Mergereplikation verwendet.  
  
 Wenn Sie Objekte veröffentlichen, werden ihre Definitionen auf Abonnenten kopiert. Wenn Sie ein Datenbankobjekt veröffentlichen, das von mindestens einem anderen Objekt abhängig ist, müssen Sie alle Objekte veröffentlichen, auf die verwiesen wird. Wenn Sie beispielsweise eine Sicht veröffentlichen, die von einer Tabelle abhängt, muss auch die Tabelle veröffentlicht werden.  
  
 Wenn Sie für *partition_options*den Wert **3** angeben, kann in diesem Artikel nur ein einzelnes Abonnement für jede Daten Partition vorhanden sein. Wird ein zweites Abonnement erstellt, in dem das Filterkriterium des neuen Abonnements die gleiche Partition ergibt wie das vorhandene Abonnement, wird das vorhandene Abonnement gelöscht.  
  
 Wenn Sie für *partition_options*den Wert 3 angeben, werden die Metadaten immer dann bereinigt, wenn die Merge-Agent ausgeführt wird und die partitionierte Momentaufnahme schneller abläuft. Beim Verwenden dieser Option sollten Sie in Erwägung ziehen, vom Abonnenten angeforderte partitionierte Momentaufnahmen zu aktivieren. Weitere Informationen finden Sie unter [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
 Wenn Sie einen Artikel mit einem statischen horizontalen Filter mithilfe von *subset_filterclause*zu einer vorhandenen Veröffentlichung mit Artikeln mit parametrisierten Filtern hinzufügen, müssen die Abonnements erneut initialisiert werden.  
  
 Wenn Sie *processing_order*angeben, empfiehlt es sich, Lücken zwischen den Werten der Artikel Reihenfolge zu belassen, sodass neue Werte in Zukunft leichter festgelegt werden können. Wenn Sie z. b. drei Artikel Article1, article2 und Article3 haben, legen Sie *processing_order* auf 10, 20 und 30 anstelle von 1, 2 und 3 fest. Weitere Informationen finden Sie unter [Specify Merge Replication properties (Angeben von Mergereplikationseigenschaften)](../../relational-databases/replication/merge/specify-merge-replication-properties.md).  
  
## <a name="default-schema-option-table"></a>Tabelle der Standardschemaoptionen  
 In dieser Tabelle wird der Standardwert beschrieben, der von der gespeicherten Prozedur festgelegt wird, wenn ein NULL-Wert für *schema_option*angegeben wird, der vom Artikeltyp abhängig ist.  
  
|Artikeltyp|Schemaoptionswert|  
|------------------|-------------------------|  
|**func schema only**|**0x01**|  
|**indexed view schema only**|**0x01**|  
|**proc schema only**|**0x01**|  
|**Tabelle**|**0x0c034und** höher  -  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] kompatible Veröffentlichungen mit einer Momentaufnahme im einheitlichen Modus.<br /><br /> **0x08034FF1**  -  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und spätere kompatible Veröffentlichungen mit einer Momentaufnahme im Zeichenmodus.|  
|**view schema only**|**0x01**|  
  
> [!NOTE]  
>  Wenn die Veröffentlichung frühere Versionen von unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ist die Standardschema Option für die- **Tabelle** **0x30034FF1**.  
  
## <a name="valid-schema-option-table"></a>Tabelle gültiger Schemaoptionen  
 In der folgenden Tabelle werden die zulässigen Werte *schema_option* je nach Artikeltyp beschrieben.  
  
|Artikeltyp|Schemaoptionswerte|  
|------------------|--------------------------|  
|**func schema only**|**0x01** und **0x2000**|  
|**indexed view schema only**|**0x01**, **0x040**, **0x0100**, **0x2000**, **0x40000**, **0x1000000**und **0x200000**|  
|**proc schema only**|**0x01** und **0x2000**|  
|**Tabelle**|Alle Optionen|  
|**view schema only**|**0x01**, **0x040**, **0x0100**, **0x2000**, **0x40000**, **0x1000000**und **0x200000**|  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_AddMergeArticle](../../relational-databases/replication/codesnippet/tsql/sp-addmergearticle-trans_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Definieren eines Artikels](../../relational-databases/replication/publish/define-an-article.md)   
 [Veröffentlichen von Daten und Datenbankobjekten](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Replizieren von Identitäts Spalten](../../relational-databases/replication/publish/replicate-identity-columns.md)   
 [sp_changemergearticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)   
 [sp_dropmergearticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql.md)   
 [sp_helpmergearticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
