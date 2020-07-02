---
title: sp_changearticle (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/28/2015
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changearticle
- sp_changearticle_TSQL
helpviewer_keywords:
- sp_changearticle
ms.assetid: 24c33ca5-f03a-4417-a267-131ca5ba6bb5
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 223f1feb346a48a2afaae9e89437ba1b06bcd2c3
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85717397"
---
# <a name="sp_changearticle-transact-sql"></a>sp_changearticle (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Ändert die Eigenschaften eines Artikels in einer Transaktions- oder Momentaufnahmeveröffentlichung. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_changearticle [ [@publication= ] 'publication' ]  
    [ , [ @article= ] 'article' ]  
    [ , [ @property= ] 'property' ]  
    [ , [ @value= ] 'value' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung, die den Artikel enthält. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @article = ] 'article'`Der Name des Artikels, dessen-Eigenschaft geändert werden soll. der *Artikel* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @property = ] 'property'`Eine zu ändernde Artikel Eigenschaft. die *Eigenschaft* ist vom Datentyp **nvarchar (100)**.  
  
`[ @value = ] 'value'`Der neue Wert der Artikel Eigenschaft. der *Wert* ist **nvarchar (255)**.  
  
 Diese Tabelle beschreibt die Eigenschaften von Artikeln und die Werte für diese Eigenschaften.  
  
|Eigenschaft|Werte|BESCHREIBUNG|  
|--------------|------------|-----------------|  
|**creation_script**||Pfad und Name eines Artikelschemaskripts, mit dem Zieltabellen erstellt werden. Die Standardeinstellung ist NULL.|  
|**del_cmd**||Die auszuführende DELETE-Anweisung; andernfalls wird die Löschoperation aus dem Protokoll hergeleitet.|  
|**description**||Ein neuer Beschreibungseintrag für den Artikel.|  
|**dest_object**||Dieser Parameter wird aus Gründen der Abwärtskompatibilität bereitgestellt. Verwenden Sie **dest_table**.|  
|**dest_table**||Die neue Zieltabelle.|  
|**destination_owner**||Name des Besitzers des Zielobjekts.|  
|**filter**||Die neue gespeicherte Prozedur, mit der die Tabelle gefiltert werden soll (horizontales Filtern). Die Standardeinstellung ist NULL. Kann bei der Peer-zu-Peer-Replikation für Veröffentlichungen nicht geändert werden.|  
|**fire_triggers_on_snapshot**|**true**|Replizierte Benutzertrigger werden ausgeführt, wenn die Anfangsmomentaufnahme angewendet wird.<br /><br /> Hinweis: Wenn Trigger repliziert werden sollen, muss der Bitmasken Wert *schema_option* den Wert **0x100**enthalten.|  
||**false**|Replizierte Benutzertrigger werden nicht ausgeführt, wenn die Anfangsmomentaufnahme angewendet wird.|  
|**identity_range**||Steuert die Größe der zugeordneten Identitätsbereiche, die am Abonnent zugeordnet wurden. Wird für die Peer-zu-Peer-Replikation nicht unterstützt.|  
|**ins_cmd**||Die auszuführende INSERT-Anweisung; andernfalls wird die Operation aus dem Protokoll hergeleitet.|  
|**pre_creation_cmd**||Ein Vorabbefehl, mit dem die Zieltabelle entfernt, gelöscht oder abgeschnitten werden kann, bevor die Synchronisierung angewendet wird.|  
||**keine**|Verwendet keinen Befehl.|  
||**Dropdown**|Entfernt die Zieltabelle.|  
||**delete**|Löscht die Zieltabelle.|  
||**TRUNCATE**|Schneidet die Zieltabelle ab.|  
|**pub_identity_range**||Steuert die Größe der zugeordneten Identitätsbereiche, die am Abonnent zugeordnet wurden. Wird für die Peer-zu-Peer-Replikation nicht unterstützt.|  
|**schema_option**||Gibt die Bitmap der Schemagenerierungsoption für den angegebenen Artikel an. *schema_option* ist **Binär (8)**. Weitere Informationen finden Sie im Abschnitt mit den Hinweisen weiter unten in diesem Thema.|  
||**0x00**|Beschreibt die Skripterstellung durch den Momentaufnahme-Agent.|  
||**0x01**|Generiert die Objekterstellung (CREATE TABLE, CREATE PROCEDURE usw.).|  
||**0x02**|Generiert die gespeicherten Prozeduren, die Änderungen für den Artikel weitergeben (falls definiert).|  
||**0x04**|Die Skripterstellung für Identitätsspalten erfolgt mithilfe der IDENTITY-Eigenschaft.|  
||**0x08**|Replizieren von **Zeitstempel** -Spalten. Wenn nicht festgelegt, werden **Zeitstempel** -Spalten als **Binärdateien**repliziert.|  
||**0x10**|Generiert einen entsprechenden gruppierten Index.|  
||**0x20**|Konvertiert benutzerdefinierte Datentypen (UDT) auf dem Abonnenten in Basisdatentypen. Diese Option kann nicht verwendet werden, wenn eine CHECK- oder DEFAULT-Einschränkung für eine UDT-Spalte vorhanden ist, wenn eine UDT-Spalte Teil des Primärschlüssels ist oder wenn eine berechnete Spalte auf eine UDT-Spalte verweist. Diese Option wird für Oracle-Verleger nicht unterstützt.|  
||**0x40**|Generiert entsprechende nicht gruppierte Indizes.|  
||**0x80**|Schließt die deklarative referenzielle Integrität für die Primärschlüssel ein.|  
||**0x100**|Repliziert Benutzertrigger für einen Tabellenartikel, wenn definiert.|  
||**0x200**|Repliziert FOREIGN KEY-Einschränkungen. Wenn die Tabelle, auf die verwiesen wird, nicht Teil einer Veröffentlichung ist, werden für eine veröffentlichte Tabelle keine FOREIGN KEY-Einschränkungen repliziert.|  
||**0x400**|Repliziert Check-Einschränkungen.|  
||**0x800**|Repliziert Standards.|  
||**0x1000**|Repliziert die Sortierung auf Spaltenebene.|  
||**0x2000**|Repliziert erweiterte Eigenschaften, die dem Quellobjekt des veröffentlichten Artikels zugeordnet sind.|  
||**0x4000**|Repliziert eindeutige Schlüssel, wenn auf einem Tabellenartikel definiert.|  
||**0x8000**|Repliziert den Primärschlüssel und eindeutige Schlüssel eines Tabellenartikels als Einschränkungen mithilfe von ALTER TABLE-Anweisungen.<br /><br /> Hinweis: diese Option ist veraltet. Verwenden Sie stattdessen **0x80** und **0x4000** .|  
||**0x10000**|Repliziert CHECK-Einschränkungen als NOT FOR REPLICATION, sodass die Einschränkungen während der Synchronisierung nicht erzwungen werden.|  
||**0x20000**|Repliziert FOREIGN KEY-Einschränkungen als NOT FOR REPLICATION, sodass diese Einschränkungen bei der Synchronisierung nicht erzwungen werden.|  
||**0x40000**|Repliziert Dateigruppen, die mit einer partitionierten Tabelle oder einem Index verbunden sind.|  
||**0x80000**|Repliziert das Partitionsschema für eine partitionierte Tabelle.|  
||**0x100000**|Repliziert das Partitionsschema für einen partitionierten Index.|  
||**0x200000**|Repliziert Tabellenstatistiken.|  
||**0x400000**|Standard Bindungen|  
||**0x800000**|Regelbindungen|  
||**0x1000000**|Volltextindex|  
||**0x2000000**|An **XML** -Spalten gebundene XML-Schema Auflistungen werden nicht repliziert.|  
||**0x4000000**|Repliziert Indizes für **XML** -Spalten.|  
||**0x8000000**|Legt Schemas an, die auf dem Abonnent noch nicht vorhanden sind.|  
||**0x10000000**|Konvertiert **XML** -Spalten in **ntext** auf dem Abonnenten.|  
||**0x20000000**|Konvertiert große Objekt Datentypen (**nvarchar (max)**, **varchar (max)** und **varbinary (max)**), die in eingeführt wurden, in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Datentypen, die in unterstützt werden [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] .|  
||**0x40000000**|Berechtigungen für die Replikation.|  
||**0x80000000**|Der Versuch, Abhängigkeiten für Objekte zu löschen, die nicht Teil der Veröffentlichung sind.|  
||**0x100000000**|Verwenden Sie diese Option, um das FILESTREAM-Attribut zu replizieren, wenn es für **varbinary (max)** -Spalten angegeben wird. Geben Sie diese Option nicht an, wenn Sie Tabellen auf [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]-Abonnenten replizieren. Das Replizieren von Tabellen mit FILESTREAM-Spalten auf [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Abonnenten wird unabhängig davon, wie diese Schema Option festgelegt ist, nicht unterstützt.<br /><br /> Siehe Verwandte Option **0x800000000**.|  
||**0x200000000**|Konvertiert Datums-und Uhrzeit Datentypen (**Date**, **time**, **DateTimeOffset**und **datetime2**), die in eingeführt wurden, in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Datentypen, die in früheren Versionen von unterstützt werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
||**0x400000000**|Repliziert die Komprimierungsoption für Daten und Indizes. Weitere Informationen finden Sie unter [Data Compression](../../relational-databases/data-compression/data-compression.md).|  
||**0x800000000**|Legen Sie diese Option fest, um FILESTREAM-Daten in einer eigenen Dateigruppe auf dem Abonnenten zu speichern. Wenn diese Option nicht festgelegt wird, werden FILESTREAM-Daten in der Standarddateigruppe gespeichert. Bei der Replikation werden keine Dateigruppen erstellt. Daher müssen Sie beim Festlegen dieser Option die Dateigruppe erstellen, bevor Sie die Momentaufnahme auf dem Abonnenten anwenden. Weitere Informationen zum Erstellen von Objekten vor dem Anwenden der Momentaufnahme finden Sie unter [Ausführen von Skripts vor und nach dem Anwenden der](../../relational-databases/replication/snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied)Momentaufnahme.<br /><br /> Siehe Verwandte Option **0x100000000**.|  
||**0x1000000000**|Konvertiert Common Language Runtime (CLR) benutzerdefinierten Typen (UDTs), die größer als 8000 Bytes sind, in **varbinary (max)** , sodass Spalten vom Typ UDT auf Abonnenten repliziert werden können, auf denen ausgeführt wird [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .|  
||**0x2000000000**|Konvertiert den **hierarchyid** -Datentyp in **varbinary (max)** , sodass Spalten vom Typ **hierarchyid** auf Abonnenten repliziert werden können, auf denen ausgeführt wird [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] . Weitere Informationen zur Verwendung von **hierarchyid** -Spalten in replizierten Tabellen finden Sie unter [hierarchyid &#40;Transact-SQL-&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md).|  
||**0x4000000000**|Repliziert die gefilterten Indizes in der Tabelle. Weitere Informationen zu gefilterten Indizes finden Sie unter [Erstellen von gefilterten Indizes](../../relational-databases/indexes/create-filtered-indexes.md).|  
||**0x8000000000**|Konvertiert den **geography** -Datentyp und den **Geometry** -Datentyp in **varbinary (max)** , sodass Spalten dieser Typen auf Abonnenten repliziert werden können, auf denen ausgeführt wird [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .|  
||**0x10000000000**|Repliziert Indizes für Spalten vom Typ **geography** und **Geometry**.|  
||**0x20000000000**|Repliziert das SPARSE-Attribut für Spalten. Weitere Informationen zu diesem Attribut finden Sie unter [Verwenden von sparsespalten](../../relational-databases/tables/use-sparse-columns.md).|  
||**0x40000000000**|Ermöglicht die Skripterstellung durch den Momentaufnahme-Agent, um eine Speicher optimierte Tabelle auf dem Abonnenten zu erstellen.|  
||**0x80000000000**|Konvertiert den gruppierten Index für Speicher optimierte Artikel in einen nicht gruppierten Index.|  
|**status**||Gibt den neuen Status der Eigenschaft an.|  
||**dts horizontal partitions**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
||**include column names**|Spaltennamen sind in der replizierten INSERT-Anweisung enthalten.|  
||**no column names**|Spaltennamen sind nicht in der replizierten INSERT-Anweisung enthalten.|  
||**no dts horizontal partitions**|Die horizontale Partition für den Artikel wird nicht durch ein transformierbares Abonnement definiert.|  
||**keine**|Löscht alle Status Optionen in der [sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md) -Tabelle und markiert den Artikel als inaktiv.|  
||**parameters**|Änderungen werden an den Abonnenten mit parametrisierten Befehlen weitergegeben. Dies ist die Standardeinstellung für einen neuen Artikel.|  
||**Zeichen folgen Literale**|Änderungen werden an den Abonnenten mit Werten von Literalzeichenfolgen weitergegeben.|  
|**sync_object**||Der Name der Tabelle oder Sicht, mit der eine Synchronisierungsausgabedatei erstellt wird. Die Standardeinstellung ist NULL. Diese Option wird für Oracle-Verleger nicht unterstützt.|  
|**Tabellenbereich**||Gibt den Tabellenbereich an, der von der Protokollierungstabelle für einen Artikel verwendet wird, der von einer Oracle-Datenbank veröffentlicht wird. Weitere Informationen finden Sie unter [Verwalten von Oracle-Tabellenbereichen](../../relational-databases/replication/non-sql/manage-oracle-tablespaces.md).|  
|**threshold**||Der Prozentwert, der steuert, wann der Verteilungs-Agent einen neuen Identitätsbereich zuweist. Wird für die Peer-zu-Peer-Replikation nicht unterstützt.|  
|**type**||Diese Option wird für Oracle-Verleger nicht unterstützt.|  
||**logbased**|Protokollbasierter Artikel.|  
||**logbased manualboth**|Protokollbasierter Artikel mit manuell erstelltem Filter und manuell erstellter Sicht. Diese Option erfordert, dass die Eigenschaften *sync_object* und *Filter* ebenfalls festgelegt werden. Diese Option wird für Oracle-Verleger nicht unterstützt.|  
||**logbased manualfilter**|Protokollbasierter Artikel mit manuell erstelltem Filter. Diese Option erfordert, dass die Eigenschaften *sync_object* und *Filter* ebenfalls festgelegt werden. Diese Option wird für Oracle-Verleger nicht unterstützt.|  
||**logbased manualview**|Protokollbasierter Artikel mit manuell erstellter Sicht. Diese Option erfordert, dass die *sync_object* -Eigenschaft ebenfalls festgelegt wird. Diese Option wird für Oracle-Verleger nicht unterstützt.|  
||**indizierte viewlogbased**|Artikel für protokollbasierte indizierte Sicht. Diese Option wird für Oracle-Verleger nicht unterstützt. Für diesen Artikeltyp muss die Basistabelle nicht separat veröffentlicht werden.|  
||**indizierte viewlogbased manualboth**|Artikel für protokollbasierte indizierte Sicht mit manuell erstelltem Filter und manuell erstellter Sicht. Diese Option erfordert, dass die Eigenschaften *sync_object* und *Filter* ebenfalls festgelegt werden. Für diesen Artikeltyp muss die Basistabelle nicht separat veröffentlicht werden. Diese Option wird für Oracle-Verleger nicht unterstützt.|  
||**indizierter viewlogbased manualfilter**|Artikel für protokollbasierte indizierte Sicht mit manuell erstelltem Filter. Diese Option erfordert, dass die *sync_object* -und *Filter* Eigenschaften ebenfalls festgelegt werden. Für diesen Artikeltyp muss die Basistabelle nicht separat veröffentlicht werden. Diese Option wird für Oracle-Verleger nicht unterstützt.|  
||**indizierte viewlogbased manualview**|Artikel für protokollbasierte indizierte Sicht mit manuell erstellter Sicht. Diese Option erfordert, dass die *sync_object* -Eigenschaft ebenfalls festgelegt wird. Für diesen Artikeltyp muss die Basistabelle nicht separat veröffentlicht werden. Diese Option wird für Oracle-Verleger nicht unterstützt.|  
|**upd_cmd**||Die auszuführende UPDATE-Anweisung; andernfalls wird die Operation aus dem Protokoll hergeleitet.|  
|NULL|NULL|Gibt eine Liste von Artikeleigenschaften zurück, die geändert werden können.|  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot`Bestätigt, dass die von dieser gespeicherten Prozedur ausgeführte Aktion eine vorhandene Momentaufnahme für ungültig erklären kann. *force_invalidate_snapshot* ist ein **Bit**, der Standardwert ist **0**.  
  
 der Wert **0** gibt an, dass Änderungen am Artikel nicht bewirken, dass die Momentaufnahme ungültig wird. Wenn die gespeicherte Prozedur erkennt, dass die Änderungen eine neue Momentaufnahme erfordern, tritt ein Fehler auf und es werden keine Änderungen vorgenommen.  
  
 der Wert **1** gibt an, dass Änderungen am Artikel bewirken können, dass die Momentaufnahme ungültig wird. wenn Abonnements vorhanden sind, die eine neue Momentaufnahme erfordern, wird die Berechtigung erteilt, die vorhandene Momentaufnahme als veraltet zu markieren und eine neue Momentaufnahme zu generieren.  
  
 Weitere Informationen zu den Eigenschaften, bei deren Änderung die Generierung einer neuen Momentaufnahme erforderlich ist, finden Sie im Abschnitt "Hinweise".  
  
`[ @force_reinit_subscription = ]force_reinit_subscription_`Bestätigt, dass die von dieser gespeicherten Prozedur ausgeführte Aktion möglicherweise erfordert, dass vorhandene Abonnements erneut initialisiert werden. *force_reinit_subscription* ist ein **Bit** mit einem Standardwert von **0**.  
  
 der Wert **0** gibt an, dass Änderungen am Artikel nicht bewirken, dass das Abonnement erneut initialisiert wird. Wenn die gespeicherte Prozedur erkennt, dass die Änderung die Neuinitialisierung vorhandener Abonnements erfordert, tritt ein Fehler auf, und es werden keine Änderungen durchgeführt.  
  
 der Wert **1** gibt an, dass Änderungen am Artikel bewirken, dass vorhandene Abonnements erneut initialisiert werden, und erteilt die Berechtigung für die erneute Initialisierung des Abonnements.  
  
 Weitere Informationen zu den Eigenschaften, bei deren Änderung die erneute Initialisierung aller vorhandenen Abonnements erforderlich ist, finden Sie im Abschnitt "Hinweise".  
  
`[ @publisher = ] 'publisher'`Gibt einen nicht-- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger an. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  der *Verleger* sollte nicht verwendet werden, wenn Artikeleigenschaften auf einem Verleger geändert werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_changearticle** wird bei der Momentaufnahme-und Transaktions Replikation verwendet.  
  
 Wenn ein Artikel zu einer Veröffentlichung gehört, die die Peer-zu-Peer-Transaktions Replikation unterstützt, können Sie nur die Eigenschaften **Description**, **ins_cmd**, **upd_cmd**und **del_cmd** ändern.  
  
 Das Ändern der folgenden Eigenschaften erfordert, dass eine neue Momentaufnahme generiert wird, und Sie müssen den Wert **1** für den *force_invalidate_snapshot* -Parameter angeben:  
  
-   **del_cmd**  
  
-   **dest_table**  
  
-   **destination_owner**  
  
-   **ins_cmd**  
  
-   **pre_creation_cmd**  
  
-   **schema_options**  
  
-   **upd_cmd**  
  
 Das Ändern der folgenden Eigenschaften erfordert, dass vorhandene Abonnements erneut initialisiert werden, und Sie müssen den Wert **1** für den *force_reinit_subscription* -Parameter angeben.  
  
-   **del_cmd**  
  
-   **dest_table**  
  
-   **destination_owner**  
  
-   **filter**  
  
-   **ins_cmd**  
  
-   **status**  
  
-   **upd_cmd**  
  
 Innerhalb einer vorhandenen Veröffentlichung können Sie mit **sp_changearticle** einen Artikel ändern, ohne die gesamte Veröffentlichung löschen und neu erstellen zu müssen.  
  
> [!NOTE]  
>  Wenn der Wert *schema_option*geändert wird, führt das System kein bitweises Update aus. Dies bedeutet, dass beim Festlegen von *schema_option* mithilfe **sp_changearticle**möglicherweise vorhandene Biteinstellungen ausgeschaltet werden. Um die vorhandenen Einstellungen beizubehalten, führen Sie [| (Bitweises OR)](../../t-sql/language-elements/bitwise-or-transact-sql.md) zwischen dem Wert, den Sie festlegen, und dem aktuellen Wert von *schema_option*, der durch Ausführen [sp_helparticle](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)bestimmt werden kann.  
  
## <a name="valid-schema-options"></a>Valid Schema Options  
 In der folgenden Tabelle werden die zulässigen Werte von *schema_option* basierend auf dem Replikationstyp (oben dargestellt) und dem Artikeltyp beschrieben (in der ersten Spalte angezeigt).  
  
|Artikeltyp|Replikationstyp||  
|------------------|----------------------|------|  
||Transaktionsreplikation|Snapshot|  
|**logbased**|Alle Optionen|Alle Optionen, aber **0x02**|  
|**logbased manualfilter**|Alle Optionen|Alle Optionen, aber **0x02**|  
|**logbased manualview**|Alle Optionen|Alle Optionen, aber **0x02**|  
|**indexed view logbased**|Alle Optionen|Alle Optionen, aber **0x02**|  
|**indexed view logbased manualfilter **|Alle Optionen|Alle Optionen, aber **0x02**|  
|**indexed view logbased manualview**|Alle Optionen|Alle Optionen, aber **0x02**|  
|**indexed view logbase manualboth**|Alle Optionen|Alle Optionen, aber **0x02**|  
|**proc exec**|**0x01**, **0x20**, **0x2000**, **0x400000**, **0x800000**, **0x2000000**, **0x8000000**, **0x10000000**, **0x20000000**, **0x40000000**und **0x80000000**|**0x01**, **0x20**, **0x2000**, **0x400000**, **0x800000**, **0x2000000**, **0x8000000**, **0x10000000**, **0x20000000**, **0x40000000**und **0x80000000**|  
|**serializable proc exec**|**0x01**, **0x20**, **0x2000**, **0x400000**, **0x800000**, **0x2000000**, **0x8000000**, **0x10000000**, **0x20000000**, **0x40000000**und **0x80000000**|**0x01**, **0x20**, **0x2000**, **0x400000**, **0x800000**, **0x2000000**, **0x8000000**, **0x10000000**, **0x20000000**, **0x40000000**und **0x80000000**|  
|**proc schema only**|**0x01**, **0x20**, **0x2000**, **0x400000**, **0x800000**, **0x2000000**, **0x8000000**, **0x10000000**, **0x20000000**, **0x40000000**und **0x80000000**|**0x01**, **0x20**, **0x2000**, **0x400000**, **0x800000**, **0x2000000**, **0x8000000**, **0x10000000**, **0x20000000**, **0x40000000**und **0x80000000**|  
|**view schema only**|**0x01**, **0x010**, **0x020**, **0x040**, **0x0100**, **0x2000**, **0x40000**, **0x100000**, **0x200000**, **0x400000**, **0x800000**, **0x2000000**, **0x8000000**, **0x40000000**und **0x80000000**|**0x01**, **0x010**, **0x020**, **0x040**, **0x0100**, **0x2000**, **0x40000**, **0x100000**, **0x200000**, **0x400000**, **0x800000**, **0x2000000**, **0x8000000**, **0x40000000**und **0x80000000**|  
|**func schema only**|**0x01**, **0x20**, **0x2000**, **0x400000**, **0x800000**, **0x2000000**, **0x8000000**, **0x10000000**, **0x20000000**, **0x40000000**und **0x80000000**|**0x01**, **0x20**, **0x2000**, **0x400000**, **0x800000**, **0x2000000**, **0x8000000**, **0x10000000**, **0x20000000**, **0x40000000**und **0x80000000**|  
|**indexed view schema only**|**0x01**, **0x010**, **0x020**, **0x040**, **0x0100**, **0x2000**, **0x40000**, **0x100000**, **0x200000**, **0x400000**, **0x800000**, **0x2000000**, **0x8000000**, **0x40000000**und **0x80000000**|**0x01**, **0x010**, **0x020**, **0x040**, **0x0100**, **0x2000**, **0x40000**, **0x100000**, **0x200000**, **0x400000**, **0x800000**, **0x2000000**, **0x8000000**, **0x40000000**und **0x80000000**|  
  
> [!NOTE]
>  Bei Veröffentlichungen mit verzögertem Update über eine Warteschlange muss der *schema_option* Wert **0x80** aktiviert werden. Die unterstützten *schema_option* Werte für nicht-- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Veröffentlichungen sind: **0x01**, **0x02**, **0x10**, **0x40**, **0x80**, **0x1000** und **0x4000**.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_changetranarticle](../../relational-databases/replication/codesnippet/tsql/sp-changearticle-transac_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_changearticle**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen und Ändern von Artikeleigenschaften](../../relational-databases/replication/publish/view-and-modify-article-properties.md)   
 [Ändern von Veröffentlichungs-und Artikeleigenschaften](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addarticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_articlecolumn &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sp_droparticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [sp_helparticlecolumns &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql.md)  
  
  
