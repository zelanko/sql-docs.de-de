---
title: sp_addarticle (Transact-SQL) | Microsoft-Dokumentation
description: Erstellt einen Artikel und fügt ihn zu einer Veröffentlichung hinzu. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.
ms.custom: ''
ms.date: 10/28/2015
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addarticle
- sp_addarticle_TSQL
helpviewer_keywords:
- sp_addarticle
ms.assetid: 0483a157-e403-4fdb-b943-23c1b487bef0
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 35aa02236cf3e8a11d03539042ccdaf9049dd8f9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85731707"
---
# <a name="sp_addarticle-transact-sql"></a>sp_addarticle (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Erstellt einen Artikel und fügt ihn zu einer Veröffentlichung hinzu. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addarticle [ @publication = ] 'publication'   
        , [ @article = ] 'article'   
    [ , [ @source_table = ] 'source_table' ]  
    [ , [ @destination_table = ] 'destination_table' ]   
    [ , [ @vertical_partition = ] 'vertical_partition' ]   
    [ , [ @type = ] 'type' ]   
    [ , [ @filter = ] 'filter' ]   
    [ , [ @sync_object= ] 'sync_object' ]   
        [ , [ @ins_cmd = ] 'ins_cmd' ]   
    [ , [ @del_cmd = ] 'del_cmd' ]   
        [ , [ @upd_cmd = ] 'upd_cmd' ]   
    [ , [ @creation_script = ] 'creation_script' ]   
    [ , [ @description = ] 'description' ]   
    [ , [ @pre_creation_cmd = ] 'pre_creation_cmd' ]   
    [ , [ @filter_clause = ] 'filter_clause' ]   
    [ , [ @schema_option = ] schema_option ]   
    [ , [ @destination_owner = ] 'destination_owner' ]   
    [ , [ @status = ] status ]   
    [ , [ @source_owner = ] 'source_owner' ]   
    [ , [ @sync_object_owner = ] 'sync_object_owner' ]   
    [ , [ @filter_owner = ] 'filter_owner' ]   
    [ , [ @source_object = ] 'source_object' ]   
    [ , [ @artid = ] article_ID  OUTPUT ]   
    [ , [ @auto_identity_range = ] 'auto_identity_range' ]   
    [ , [ @pub_identity_range = ] pub_identity_range ]   
    [ , [ @identity_range = ] identity_range ]   
    [ , [ @threshold = ] threshold ]   
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @use_default_datatypes = ] use_default_datatypes  
    [ , [ @identityrangemanagementoption = ] identityrangemanagementoption ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @fire_triggers_on_snapshot = ] 'fire_triggers_on_snapshot' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung, die den Artikel enthält. Der Name muss in der Datenbank eindeutig sein. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @article = ] 'article'`Der Name des Artikels. Der Name muss innerhalb der Veröffentlichung eindeutig sein. der *Artikel* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @source_table = ] 'source_table'`Dieser Parameter wurde als veraltet markiert. Verwenden Sie stattdessen *source_object* .  
  
 *Der Parameter wird von Oracle-Verlegern nicht unterstützt.*  
  
`[ @destination_table = ] 'destination_table'`Der Name der Ziel Tabelle (Abonnement Tabelle), wenn Sie von *source_table*oder der gespeicherten Prozedur abweicht. *destination_table* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Dies bedeutet, dass *source_table* *destination_table * * entspricht.*  
  
`[ @vertical_partition = ] 'vertical_partition'`Aktiviert und deaktiviert die Spalten Filterung für einen Tabellen Artikel. *vertical_partition* ist vom Typ **NCHAR (5)** und hat den Standardwert false.  
  
 **false** gibt an, dass keine vertikale Filterung vorhanden ist und alle Spalten veröffentlicht werden.  
  
 **true** löscht alle Spalten außer dem deklarierten Primärschlüssel, NULL-Werte, die keine Standard Spalten sind, und eindeutige Schlüssel Spalten. Spalten werden mit [sp_articlecolumn](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)hinzugefügt.  
  
`[ @type = ] 'type'`Der Typ des Artikels. *Type ist vom Datentyp* **vom Datentyp sysname**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**aggregate schema only**|Aggregatfunktion vom Typ schema only.|  
|**func schema only**|Funktion vom Typ schema only.|  
|**indexed view logbased**|Artikel für protokollbasierte indizierte Sicht. Diese Option wird für Oracle-Verleger nicht unterstützt. Für diesen Artikeltyp muss die Basistabelle nicht separat veröffentlicht werden.|  
|**indexed view logbased manualboth**|Artikel für protokollbasierte indizierte Sicht mit manuell erstelltem Filter und manuell erstellter Sicht. Diese Option erfordert, dass Sie sowohl *sync_object* als auch *Filter* Parameter angeben. Für diesen Artikeltyp muss die Basistabelle nicht separat veröffentlicht werden. Diese Option wird für Oracle-Verleger nicht unterstützt.|  
|**indexed view logbased manualfilter **|Artikel für protokollbasierte indizierte Sicht mit manuell erstelltem Filter. Diese Option erfordert, dass Sie sowohl *sync_object* als auch *Filter* Parameter angeben. Für diesen Artikeltyp muss die Basistabelle nicht separat veröffentlicht werden. Diese Option wird für Oracle-Verleger nicht unterstützt.|  
|**indexed view logbased manualview**|Artikel für protokollbasierte indizierte Sicht mit manuell erstellter Sicht. Diese Option erfordert, dass Sie den *sync_object* -Parameter angeben. Für diesen Artikeltyp muss die Basistabelle nicht separat veröffentlicht werden. Diese Option wird für Oracle-Verleger nicht unterstützt.|  
|**indexed view schema only**|Indizierte Sicht vom Typ schema only. Für diesen Artikeltyp muss die Basistabelle ebenfalls veröffentlicht werden.|  
|**logbased** (Standard)|Protokollbasierter Artikel.|  
|**logbased manualboth**|Protokollbasierter Artikel mit manuell erstelltem Filter und manuell erstellter Sicht. Diese Option erfordert, dass Sie sowohl *sync_object* als auch *Filter* Parameter angeben. Diese Option wird für Oracle-Verleger nicht unterstützt.|  
|**logbased manualfilter**|Protokollbasierter Artikel mit manuell erstelltem Filter. Diese Option erfordert, dass Sie sowohl *sync_object* als auch *Filter* Parameter angeben. Diese Option wird für Oracle-Verleger nicht unterstützt.|  
|**logbased manualview**|Protokollbasierter Artikel mit manuell erstellter Sicht. Diese Option erfordert, dass Sie den *sync_object* -Parameter angeben. Diese Option wird für Oracle-Verleger nicht unterstützt.|  
|**proc exec**|Repliziert die Ausführung der gespeicherten Prozedur auf alle Abonnenten des Artikels. Diese Option wird für Oracle-Verleger nicht unterstützt. Es wird empfohlen, anstelle von **proc exec**die Option **serialisierbares proc exec** zu verwenden. Weitere Informationen finden Sie im Abschnitt "Typen von Artikeln zur Ausführung gespeicherter Prozeduren" unter [Veröffentlichen der Ausführung gespeicherter Prozeduren in der Transaktions Replikation](../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md). Nicht verfügbar, wenn Change Data Capture aktiviert ist.|  
|**proc schema only**|Prozedur vom Typ schema only. Diese Option wird für Oracle-Verleger nicht unterstützt.|  
|**serializable proc exec**|Repliziert die Ausführung der gespeicherten Prozedur nur, wenn die Prozedur im Kontext einer serialisierbaren Transaktion ausgeführt wird. Diese Option wird für Oracle-Verleger nicht unterstützt.<br /><br /> Der Vorgang muss auch innerhalb einer expliziten Transaktion ausgeführt werden, damit die Ausführung repliziert werden kann.|  
|**view schema only**|Sicht vom Typ schema only. Diese Option wird für Oracle-Verleger nicht unterstützt. Wenn diese Option verwendet wird, müssen Sie auch die Basistabelle veröffentlichen.|  
  
`[ @filter = ] 'filter'`Ist die gespeicherte Prozedur (erstellt mit for Replication), mit der die Tabelle horizontal gefiltert wird. der *Filter* ist vom Datentyp **nvarchar (386)** und hat den Standardwert NULL. [sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) und [sp_articlefilter](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md) müssen manuell ausgeführt werden, um die gespeicherte Prozedur "View" und "Filter" zu erstellen. Bei einem Wert ungleich NULL wird die Filterprozedur nicht erstellt (es wird angenommen, dass die gespeicherte Prozedur manuell erstellt wird).  
  
`[ @sync_object = ] 'sync_object'`Der Name der Tabelle oder Sicht, die zum Erstellen der Datendatei verwendet wird, mit der die Momentaufnahme für diesen Artikel dargestellt wird. *sync_object* ist vom Datentyp **nvarchar (386)** und hat den Standardwert NULL. Wenn der Wert NULL ist, wird [sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) aufgerufen, um automatisch die Ansicht zum Generieren der Ausgabedatei zu erstellen. Dies tritt auf, nachdem alle Spalten mit [sp_articlecolumn](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)hinzugefügt wurden. Bei einem Wert ungleich NULL wird keine Sicht erstellt (es wird angenommen, dass die Sicht manuell erstellt wird).  
  
`[ @ins_cmd = ] 'ins_cmd'`Der beim Replizieren von Einfügungen für diesen Artikel verwendete Replikations Befehlstyp. *ins_cmd* ist vom Datentyp **nvarchar (255)** und kann einen der folgenden Werte aufweisen.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**NONE**|Es wird keine Aktion ausgeführt.|  
|**CALL sp_MSins_**<br /> **_Tabelle_** (Standard)<br /><br /> - oder -<br /><br /> **CALL custom_stored_procedure_name**|Eine gespeicherte Prozedur wird aufgerufen, die auf dem Abonnenten ausgeführt werden soll. Wenn Sie diese Methode der Replikation verwenden möchten, verwenden Sie *schema_option* , um die automatische Erstellung der gespeicherten Prozedur anzugeben, oder erstellen Sie die angegebene gespeicherte Prozedur in der Zieldatenbank jedes Abonnenten des Artikels. *custom_stored_procedure* ist der Name einer vom Benutzer erstellten gespeicherten Prozedur. <strong>sp_Msins_*Tabelle* </strong> enthält den Namen der Ziel Tabelle anstelle des *_table* Teils des Parameters. Wenn *destination_owner* angegeben wird, wird es dem Ziel Tabellennamen vorangestellt. Beispielsweise wäre der-Parameter für die **ProductCategory** -Tabelle, deren Besitzer das **Produktions** Schema auf dem Abonnenten ist, `CALL sp_MSins_ProductionProductCategory` . Bei einem Artikel in einer Peer-zu-Peer-Replikations Topologie wird *_table* mit einem GUID-Wert angefügt. Das Angeben von *custom_stored_procedure* wird für Update Abonnenten nicht unterstützt.|  
|**SQL** oder NULL|Repliziert eine INSERT-Anweisung. Für die INSERT-Anweisung werden Werte für alle in dem Artikel veröffentlichten Spalten bereitgestellt. Der folgende Befehl wird bei Einfügungen repliziert:<br /><br /> `INSERT INTO <table name> VALUES (c1value, c2value, c3value, ..., cnvalue)`|  
  
 Weitere Informationen finden Sie unter [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
`[ @del_cmd = ] 'del_cmd'`Der Replikations Befehlstyp, der beim Replizieren von Löschungen für diesen Artikel verwendet wird. *del_cmd* ist vom Datentyp **nvarchar (255)** und kann einen der folgenden Werte aufweisen.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**NONE**|Es wird keine Aktion ausgeführt.|  
|**CALLsp_MSdel_**<br /> **_Tabelle_** (Standard)<br /><br /> - oder -<br /><br /> **CALL custom_stored_procedure_name**|Eine gespeicherte Prozedur wird aufgerufen, die auf dem Abonnenten ausgeführt werden soll. Wenn Sie diese Methode der Replikation verwenden möchten, verwenden Sie *schema_option* , um die automatische Erstellung der gespeicherten Prozedur anzugeben, oder erstellen Sie die angegebene gespeicherte Prozedur in der Zieldatenbank jedes Abonnenten des Artikels. *custom_stored_procedure* ist der Name einer vom Benutzer erstellten gespeicherten Prozedur. <strong>sp_MSdel_*Tabelle* </strong> enthält den Namen der Ziel Tabelle anstelle des *_table* Teils des Parameters. Wenn *destination_owner* angegeben wird, wird es dem Ziel Tabellennamen vorangestellt. Beispielsweise wäre der-Parameter für die **ProductCategory** -Tabelle, deren Besitzer das **Produktions** Schema auf dem Abonnenten ist, `CALL sp_MSdel_ProductionProductCategory` . Bei einem Artikel in einer Peer-zu-Peer-Replikations Topologie wird *_table* mit einem GUID-Wert angefügt. Das Angeben von *custom_stored_procedure* wird für Update Abonnenten nicht unterstützt.|  
|**XCALL sp_MSdel_**<br /> **_glaub_**<br /><br /> - oder -<br /><br /> **XCALL custom_stored_procedure_name**|Ruft eine gespeicherte Prozedur auf, die XCALL-Parameter akzeptiert. Wenn Sie diese Methode der Replikation verwenden möchten, verwenden Sie *schema_option* , um die automatische Erstellung der gespeicherten Prozedur anzugeben, oder erstellen Sie die angegebene gespeicherte Prozedur in der Zieldatenbank jedes Abonnenten des Artikels. Die Angabe einer benutzerdefinierten gespeicherten Prozedur ist für Updateabonnenten nicht zulässig.|  
|**SQL** oder NULL|Repliziert eine DELETE-Anweisung. Für die DELETE-Anweisung werden alle Spaltenwerte der Primärschlüssel bereitgestellt. Der folgende Befehl wird bei Löschungen repliziert:<br /><br /> `DELETE FROM <table name> WHERE pkc1 = pkc1value AND pkc2 = pkc2value AND pkcn = pkcnvalue`|  
  
 Weitere Informationen finden Sie unter [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
`[ @upd_cmd = ] 'upd_cmd'`Der Replikations Befehlstyp, der beim Replizieren von Updates für diesen Artikel verwendet wird. *upd_cmd* ist vom Datentyp **nvarchar (255)** und kann einen der folgenden Werte aufweisen.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**NONE**|Es wird keine Aktion ausgeführt.|  
|**CALL sp_MSupd_**<br /> **_glaub_**<br /><br /> - oder -<br /><br /> **CALL custom_stored_procedure_name**|Eine gespeicherte Prozedur wird aufgerufen, die auf dem Abonnenten ausgeführt werden soll. Wenn Sie diese Methode der Replikation verwenden möchten, verwenden Sie *schema_option* , um die automatische Erstellung der gespeicherten Prozedur anzugeben, oder erstellen Sie die angegebene gespeicherte Prozedur in der Zieldatenbank jedes Abonnenten des Artikels.|  
|**MCALL sp_MSupd_**<br /> **_glaub_**<br /><br /> - oder -<br /><br /> **MCALL custom_stored_procedure_name**|Ruft eine gespeicherte Prozedur auf, die MCALL-Parameter akzeptiert. Wenn Sie diese Methode der Replikation verwenden möchten, verwenden Sie *schema_option* , um die automatische Erstellung der gespeicherten Prozedur anzugeben, oder erstellen Sie die angegebene gespeicherte Prozedur in der Zieldatenbank jedes Abonnenten des Artikels. *custom_stored_procedure* ist der Name einer vom Benutzer erstellten gespeicherten Prozedur. <strong>sp_Msupd_*Tabelle* </strong> enthält den Namen der Ziel Tabelle anstelle des *_table* Teils des Parameters. Wenn *destination_owner* angegeben wird, wird es dem Ziel Tabellennamen vorangestellt. Beispielsweise wäre der-Parameter für die **ProductCategory** -Tabelle, deren Besitzer das **Produktions** Schema auf dem Abonnenten ist, `MCALL sp_MSupd_ProductionProductCategory` . Bei einem Artikel in einer Peer-zu-Peer-Replikations Topologie wird *_table* mit einem GUID-Wert angefügt. Die Angabe einer benutzerdefinierten gespeicherten Prozedur ist für Updateabonnenten nicht zulässig.|  
|**SCALL sp_MSupd_**<br /> **_Tabelle_** (Standard)<br /><br /> - oder -<br /><br /> **SCALL custom_stored_procedure_name**|Ruft eine gespeicherte Prozedur auf, die SCALL-Parameter akzeptiert. Wenn Sie diese Methode der Replikation verwenden möchten, verwenden Sie *schema_option* , um die automatische Erstellung der gespeicherten Prozedur anzugeben, oder erstellen Sie die angegebene gespeicherte Prozedur in der Zieldatenbank jedes Abonnenten des Artikels. *custom_stored_procedure* ist der Name einer vom Benutzer erstellten gespeicherten Prozedur. <strong>sp_Msupd_*Tabelle* </strong> enthält den Namen der Ziel Tabelle anstelle des *_table* Teils des Parameters. Wenn *destination_owner* angegeben wird, wird es dem Ziel Tabellennamen vorangestellt. Beispielsweise wäre der-Parameter für die **ProductCategory** -Tabelle, deren Besitzer das **Produktions** Schema auf dem Abonnenten ist, `SCALL sp_MSupd_ProductionProductCategory` . Bei einem Artikel in einer Peer-zu-Peer-Replikations Topologie wird *_table* mit einem GUID-Wert angefügt. Die Angabe einer benutzerdefinierten gespeicherten Prozedur ist für Updateabonnenten nicht zulässig.|  
|**XCALL sp_MSupd_**<br /> **_glaub_**<br /><br /> - oder -<br /><br /> **XCALL custom_stored_procedure_name**|Ruft eine gespeicherte Prozedur auf, die XCALL-Parameter akzeptiert. Wenn Sie diese Methode der Replikation verwenden möchten, verwenden Sie *schema_option* , um die automatische Erstellung der gespeicherten Prozedur anzugeben, oder erstellen Sie die angegebene gespeicherte Prozedur in der Zieldatenbank jedes Abonnenten des Artikels. Die Angabe einer benutzerdefinierten gespeicherten Prozedur ist für Updateabonnenten nicht zulässig.|  
|**SQL** oder NULL|Repliziert eine UPDATE-Anweisung. Die UPDATE-Anweisung wird für alle Spaltenwerte und für die Spaltenwerte der Primärschlüssel bereitgestellt. Der folgende Befehl wird bei Updates repliziert:<br /><br /> `UPDATE <table name> SET c1 = c1value, SET c2 = c2value, SET cn = cnvalue WHERE pkc1 = pkc1value AND pkc2 = pkc2value AND pkcn = pkcnvalue`|  
  
> [!NOTE]  
>  Die CALL-, MCALL-, SCALL- und XCALL-Syntax variiert den Umfang der Daten, die an den Abonnenten weitergegeben werden. Die CALL-Syntax übergibt alle Werte für alle eingefügten und gelöschten Spalten. Die SCALL-Syntax übergibt nur die Werte für betroffene Spalten. Die XCALL-Syntax übergibt die Werte für alle Spalten, unabhängig davon, ob diese geändert wurden, einschließlich des vorherigen Werts der Spalte. Weitere Informationen finden Sie unter [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
`[ @creation_script = ] 'creation_script'`Der Pfad und der Name eines optionalen Artikel Schema Skripts, mit dem der Artikel in der Abonnement Datenbank erstellt wird. *creation_script* ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL.  
  
`[ @description = ] 'description'`Ist ein beschreibender Eintrag für den Artikel. die *Beschreibung* ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL.  
  
`[ @pre_creation_cmd = ] 'pre_creation_cmd'`Gibt an, was das System tun soll, wenn beim Anwenden der Momentaufnahme für diesen Artikel ein vorhandenes Objekt mit demselben Namen auf dem Abonnenten erkannt wird. *pre_creation_cmd* ist vom Datentyp **nvarchar (10)**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**keine**|Verwendet keinen Befehl.|  
|**delete**|Löscht Daten aus der Zieltabelle vor dem Anwenden der Momentaufnahme. Wird der Artikel horizontal gefiltert, werden nur Daten in Spalten gelöscht, die von der Filterklausel angegeben werden. Wird von Oracle-Verlegern nicht unterstützt, wenn ein horizontaler Filter definiert wurde.|  
|**Drop** (Standard)|Entfernt die Zieltabelle.|  
|**TRUNCATE**|Schneidet die Zieltabelle ab. Gilt nicht für ODBC- oder OLE DB-Abonnenten.|  
  
`[ @filter_clause = ] 'filter_clause'`Eine Einschränkungs Klausel (WHERE), die einen horizontalen Filter definiert. Wenn Sie die Einschränkungs Klausel eingeben, lassen Sie das Schlüsselwort aus. *filter_clause* ist vom Typ **ntext**und hat den Standardwert NULL. Weitere Informationen finden Sie unter [Filtern von veröffentlichten Daten](../../relational-databases/replication/publish/filter-published-data.md).  
  
`[ @schema_option = ] schema_option`Ist eine Bitmaske der Schema Generierungs Option für den angegebenen Artikel. *schema_option* ist **Binär (8)** und kann das [| (Bitweises OR)](../../t-sql/language-elements/bitwise-or-transact-sql.md) Produkt mindestens eines der folgenden Werte:  
  
> [!NOTE]  
>  Ist dieser Wert NULL, generiert das System automatisch eine gültige Schemaoption für den Artikel, abhängig von anderen Artikeleigenschaften. Die in den Hinweisen angegebene **Standard Schema Optionen** -Tabelle zeigt den Wert, der basierend auf der Kombination des Artikel Typs und des Replikations Typs ausgewählt wird.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**0x00**|Deaktiviert die Skripterstellung durch den Momentaufnahmen-Agent und verwendet *creation_script*.|  
|**0x01**|Generiert das Objekterstellungsskript (CREATE TABLE, CREATE PROCEDURE usw.). Dies ist der Standardwert für alle Artikel mit gespeicherten Prozeduren.|  
|**0x02**|Generiert die gespeicherten Prozeduren, die Änderungen für den Artikel weitergeben (falls definiert).|  
|**0x04**|Die Skripterstellung für Identitätsspalten erfolgt mithilfe der IDENTITY-Eigenschaft.|  
|**0x08**|Replizieren von **Zeitstempel** -Spalten. Wenn nicht festgelegt, werden **Zeitstempel** -Spalten als **Binärdateien**repliziert.|  
|**0x10**|Generiert einen entsprechenden gruppierten Index. Auch wenn diese Option nicht festgelegt ist, werden Indizes im Zusammenhang mit primär Schlüsseln und UNIQUE-Einschränkungen generiert, wenn Sie bereits für eine veröffentlichte Tabelle definiert sind.|  
|**0x20**|Konvertiert benutzerdefinierte Datentypen (UDT) auf dem Abonnenten in Basisdatentypen. Diese Option kann nicht verwendet werden, wenn eine CHECK- oder DEFAULT-Einschränkung für eine UDT-Spalte vorhanden ist, wenn eine UDT-Spalte Teil des Primärschlüssels ist oder wenn eine berechnete Spalte auf eine UDT-Spalte verweist. *Wird für Oracle-Verleger nicht unterstützt*.|  
|**0x40**|Generiert entsprechende nicht gruppierte Indizes. Auch wenn diese Option nicht festgelegt ist, werden Indizes im Zusammenhang mit primär Schlüsseln und UNIQUE-Einschränkungen generiert, wenn Sie bereits für eine veröffentlichte Tabelle definiert sind.|  
|**0x80**|Repliziert Primärschlüsseleinschränkungen. Alle Indizes im Zusammenhang mit der Einschränkung werden ebenfalls repliziert, auch wenn die Optionen **0x10** und **0x40** nicht aktiviert sind.|  
|**0x100**|Repliziert Benutzertrigger für einen Tabellenartikel, wenn definiert. *Wird für Oracle-Verleger nicht unterstützt*.|  
|**0x200**|Repliziert Fremdschlüsseleinschränkungen. Wenn die Tabelle, auf die verwiesen wird, nicht Teil einer Veröffentlichung ist, werden keine Fremdschlüsseleinschränkungen für eine veröffentlichte Tabelle repliziert. *Wird für Oracle-Verleger nicht unterstützt*.|  
|**0x400**|Repliziert CHECK-Einschränkungen. *Wird für Oracle-Verleger nicht unterstützt*.|  
|**0x800**|Repliziert Standards. *Wird für Oracle-Verleger nicht unterstützt*.|  
|**0x1000**|Repliziert die Sortierung auf Spaltenebene.<br /><br /> **Hinweis:** Diese Option sollte für Oracle-Verleger festgelegt werden, um Vergleiche zwischen Groß-und Kleinschreibung zu ermöglichen.|  
|**0x2000**|Repliziert erweiterte Eigenschaften, die dem Quellobjekt des veröffentlichten Artikels zugeordnet sind. *Wird für Oracle-Verleger nicht unterstützt*.|  
|**0x4000**|Repliziert UNIQUE-Einschränkungen. Alle Indizes im Zusammenhang mit der Einschränkung werden ebenfalls repliziert, auch wenn die Optionen **0x10** und **0x40** nicht aktiviert sind.|  
|**0x8000**|Diese Option ist für [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]-Verleger nicht gültig.|  
|**0x10000**|Repliziert CHECK-Einschränkungen als NOT FOR REPLICATION, sodass die Einschränkungen während der Synchronisierung nicht erzwungen werden.|  
|**0x20000**|Repliziert FOREIGN KEY-Einschränkungen als NOT FOR REPLICATION, sodass diese Einschränkungen bei der Synchronisierung nicht erzwungen werden.|  
|**0x40000**|Repliziert Dateigruppen, die mit einer partitionierten Tabelle oder einem Index verbunden sind.|  
|**0x80000**|Repliziert das Partitionsschema für eine partitionierte Tabelle.|  
|**0x100000**|Repliziert das Partitionsschema für einen partitionierten Index.|  
|**0x200000**|Repliziert Tabellenstatistiken.|  
|**0x400000**|Standard Bindungen|  
|**0x800000**|Regelbindungen|  
|**0x1000000**|Volltextindex|  
|**0x2000000**|An **XML** -Spalten gebundene XML-Schema Auflistungen werden nicht repliziert.|  
|**0x4000000**|Repliziert Indizes für **XML** -Spalten.|  
|**0x8000000**|Legt Schemas an, die auf dem Abonnent noch nicht vorhanden sind.|  
|**0x10000000**|Konvertiert **XML** -Spalten in **ntext** auf dem Abonnenten.|  
|**0x20000000**|Konvertiert große Objekt Datentypen (**nvarchar (max)**, **varchar (max)** und **varbinary (max)**), die in eingeführt wurden, in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Datentypen, die in unterstützt werden [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] .|  
|**0x40000000**|Berechtigungen für die Replikation.|  
|**0x80000000**|Der Versuch, Abhängigkeiten für Objekte zu löschen, die nicht Teil der Veröffentlichung sind.|  
|**0x100000000**|Verwenden Sie diese Option, um das FILESTREAM-Attribut zu replizieren, wenn es für **varbinary (max)** -Spalten angegeben wird. Geben Sie diese Option nicht an, wenn Sie Tabellen auf [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]-Abonnenten replizieren. Das Replizieren von Tabellen mit FILESTREAM-Spalten auf [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Abonnenten wird unabhängig davon, wie diese Schema Option festgelegt ist, nicht unterstützt.<br /><br /> Siehe Verwandte Option **0x800000000**.|  
|**0x200000000**|Konvertiert Datums-und Uhrzeit Datentypen (**Date**, **time**, **DateTimeOffset**und **datetime2**), die in eingeführt wurden [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] , in Datentypen, die in früheren Versionen von unterstützt werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|**0x400000000**|Repliziert die Komprimierungsoption für Daten und Indizes. Weitere Informationen finden Sie unter [Data Compression](../../relational-databases/data-compression/data-compression.md).|  
|**0x800000000**|Legen Sie diese Option fest, um FILESTREAM-Daten in einer eigenen Dateigruppe auf dem Abonnenten zu speichern. Wenn diese Option nicht festgelegt wird, werden FILESTREAM-Daten in der Standarddateigruppe gespeichert. Bei der Replikation werden keine Dateigruppen erstellt. Daher müssen Sie beim Festlegen dieser Option die Dateigruppe erstellen, bevor Sie die Momentaufnahme auf dem Abonnenten anwenden. Weitere Informationen zum Erstellen von Objekten vor dem Anwenden der Momentaufnahme finden Sie unter [Ausführen von Skripts vor und nach dem Anwenden der](../../relational-databases/replication/snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied)Momentaufnahme.<br /><br /> Siehe Verwandte Option **0x100000000**.|  
|**0x1000000000**|Konvertiert Common Language Runtime (CLR)-benutzerdefinierten Typen (UDTs), die größer als 8000 Bytes sind, in **varbinary (max)** , sodass Spalten vom Typ UDT auf Abonnenten repliziert werden können, auf denen ausgeführt wird [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .|  
|**0x2000000000**|Konvertiert den **hierarchyid** -Datentyp in **varbinary (max)** , sodass Spalten vom Typ **hierarchyid** auf Abonnenten repliziert werden können, auf denen ausgeführt wird [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] . Weitere Informationen zur Verwendung von **hierarchyid** -Spalten in replizierten Tabellen finden Sie unter [hierarchyid &#40;Transact-SQL-&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md).|  
|**0x4000000000**|Repliziert die gefilterten Indizes in der Tabelle. Weitere Informationen zu gefilterten Indizes finden Sie unter [Erstellen von gefilterten Indizes](../../relational-databases/indexes/create-filtered-indexes.md).|  
|**0x8000000000**|Konvertiert den **geography** -Datentyp und den **Geometry** -Datentyp in **varbinary (max)** , sodass Spalten dieser Typen auf Abonnenten repliziert werden können, auf denen ausgeführt wird [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .|  
|**0x10000000000**|Repliziert Indizes für Spalten vom Typ **geography** und **Geometry**.|  
|**0x20000000000**|Repliziert das SPARSE-Attribut für Spalten. Weitere Informationen zu diesem Attribut finden Sie unter [Verwenden von sparsespalten](../../relational-databases/tables/use-sparse-columns.md).|  
|**0x40000000000**|Aktivieren Sie die Skripterstellung durch den Momentaufnahme-Agent, um eine Speicher optimierte Tabelle auf dem Abonnenten zu erstellen.|  
|**0x80000000000**|Konvertiert den gruppierten Index für Speicher optimierte Artikel in einen nicht gruppierten Index.|  
|**0x400000000000**|Repliziert Alle nicht gruppierten columnstore--Indizes für die Tabelle (n).|  
|**0x800000000000**|Repliziert Alle geclusterten nicht gruppierten columnstore--Indizes für die Tabelle (n).|  
|NULL|Bei der Replikation wird automatisch *schema_option* auf einen Standardwert festgelegt, dessen Wert von anderen Artikeleigenschaften abhängt. Die in den Hinweisen enthaltene Tabelle "Default Schema Options" zeigt die Standardschemaoptionen auf der Grundlage des Artikeltyps und des Replikationstyps an.<br /><br /> Der Standardwert für nicht-- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Veröffentlichungen ist **0x050D3**.|  
  
 Nicht alle *schema_option* Werte sind für jeden Replikationstyp und Artikeltyp gültig. Die Tabelle **gültige Schema Optionen** im Abschnitt "Hinweise" zeigt die gültigen Schema Optionen an, die basierend auf der Kombination des Artikel Typs und des Replikations Typs ausgewählt werden können.  
  
`[ @destination_owner = ] 'destination_owner'`Der Name des Besitzers des Zielobjekts. *destination_owner* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Wenn *destination_owner* nicht angegeben ist, wird der Besitzer automatisch anhand der folgenden Regeln angegeben:  
  
|Bedingung|Zielobjektbesitzer|  
|---------------|------------------------------|  
|Die Veröffentlichung generiert die Anfangsmomentaufnahme, die nur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Abonnenten unterstützt, über das Massenkopieren im einheitlichen Modus.|Der Standardwert ist *source_owner*.|  
|Veröffentlicht von einem Nicht-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verleger.|Standardmäßig wird der Besitzer der Zieldatenbank verwendet.|  
|Die Veröffentlichung generiert die Anfangsmomentaufnahme, die Nicht-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Abonnenten unterstützt, über das Massenkopieren im Zeichenmodus.|Nicht zugewiesen.|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *Destination_owner* muss NULL sein, um nicht--Abonnenten zu unterstützen.  
  
`[ @status = ] status`Gibt an, ob der Artikel aktiv ist, und gibt zusätzliche Optionen für die Weitergabe von Änderungen an. der *Status* ist " **tinyint**" und kann "|" lauten. [ (Bitweises OR)](../../t-sql/language-elements/bitwise-or-transact-sql.md) Produkt mindestens eines der folgenden Werte.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|Der Artikel ist aktiv.|  
|**8**|Bezieht den Spaltennamen in INSERT-Anweisungen mit ein.|  
|**16** (Standard)|Verwendet parametrisierte Anweisungen.|  
|**24**|Bezieht den Spaltennamen in INSERT-Anweisungen mit ein und verwendet parametrisierte Anweisungen.|  
|**64**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
 Ein aktiver Artikel, der parametrisierte Anweisungen verwendet, würde in dieser Spalte beispielsweise den Wert 17 anzeigen. Der Wert **0** bedeutet, dass der Artikel inaktiv ist und keine zusätzlichen Eigenschaften definiert sind.  
  
`[ @source_owner = ] 'source_owner'`Der Besitzer des Quell Objekts. *source_owner* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. *source_owner* muss für Oracle-Verleger angegeben werden.  
  
`[ @sync_object_owner = ] 'sync_object_owner'`Der Besitzer der Sicht, die den veröffentlichten Artikel definiert. *sync_object_owner* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @filter_owner = ] 'filter_owner'`Der Besitzer des Filters. *filter_owner* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @source_object = ] 'source_object'`Das Datenbankobjekt, das veröffentlicht werden soll. *source_object* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Wenn *source_table* NULL ist, kann *source_object* nicht NULL sein. *source_object* sollte anstelle *source_table*verwendet werden. Weitere Informationen zu den Objekttypen, die mithilfe der Momentaufnahme-oder Transaktions Replikation veröffentlicht werden können, finden Sie unter [Veröffentlichen von Daten und Datenbankobjekten](../../relational-databases/replication/publish/publish-data-and-database-objects.md).  
  
`[ @artid = ] _article_ID_ OUTPUT`Ist die Artikel-ID des neuen Artikels. *article_id* ist vom Datentyp **int** und hat den Standardwert NULL, und es handelt sich um einen Output-Parameter.  
  
`[ @auto_identity_range = ] 'auto_identity_range'`Aktiviert und deaktiviert die automatische Behandlung von Identitäts Bereichen für eine Veröffentlichung zu dem Zeitpunkt, zu dem Sie erstellt wird. *auto_identity_range* ist vom Datentyp **nvarchar (5)**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**true**|Aktiviert die automatische Behandlung von Identitätsbereichen|  
|**false**|Deaktiviert die automatische Behandlung von Identitätsbereichen|  
|NULL (Standard)|Die Identitäts Bereichs Behandlung wird von *identityrangemanagementoption*festgelegt.|  
  
> [!NOTE]  
>  *auto_identity_range* wurde als veraltet markiert und wird nur aus Gründen der Abwärtskompatibilität bereitgestellt. Sie sollten die *identityrangemanagementoption* zum Angeben der Optionen für die Identitäts Bereichs Verwaltung verwenden. Weitere Informationen finden Sie unter [Replizieren von Identitätsspalten](../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
`[ @pub_identity_range = ] pub_identity_range`Steuert die Bereichs Größe auf dem Verleger, wenn für den Artikel *identityrangemanagementoption* auf **Auto** oder *auto_identity_range* auf **true**festgelegt ist. *pub_identity_range* ist vom Datentyp **bigint**und hat den Standardwert NULL. *Wird für Oracle-Verleger nicht unterstützt*.  
  
`[ @identity_range = ] identity_range`Steuert die Bereichs Größe auf dem Abonnenten, wenn für den Artikel *identityrangemanagementoption* auf **Auto** oder *auto_identity_range* auf **true**festgelegt ist. *identity_range* ist vom Datentyp **bigint**und hat den Standardwert NULL. Wird verwendet, wenn *auto_identity_range* auf **true**festgelegt ist. *Wird für Oracle-Verleger nicht unterstützt*.  
  
`[ @threshold = ] threshold`Der Prozentwert, der steuert, wann der Verteilungs-Agent einen neuen Identitäts Bereich zuweist. Wenn der in *Schwellenwert* angegebene Prozentsatz der Werte verwendet wird, erstellt der Verteilungs-Agent einen neuen Identitäts Bereich. der *Schwellenwert* ist **bigint**, der Standardwert ist NULL. Wird verwendet, wenn " *identityrangemanagementoption* " auf " **Auto** " oder " *auto_identity_range* auf" **true**"festgelegt ist. *Wird für Oracle-Verleger nicht unterstützt*.  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot`Bestätigt, dass die von dieser gespeicherten Prozedur ausgeführte Aktion eine vorhandene Momentaufnahme für ungültig erklären kann. *force_invalidate_snapshot* ist ein **Bit**, der Standardwert ist 0.  
  
 **0** gibt an, dass das Hinzufügen eines Artikels nicht dazu führt, dass die Momentaufnahme ungültig wird. Wenn die gespeicherte Prozedur erkennt, dass die Änderungen eine neue Momentaufnahme erfordern, tritt ein Fehler auf, und es werden keine Änderungen durchgeführt.  
  
 der Wert **1** gibt an, dass das Hinzufügen eines Artikels dazu führen kann, dass die Momentaufnahme ungültig wird. wenn Abonnements vorhanden sind, die eine neue Momentaufnahme erfordern, wird die Berechtigung erteilt, die vorhandene Momentaufnahme als veraltet zu markieren und eine neue Momentaufnahme zu generieren.  
  
`[ @use_default_datatypes = ] use_default_datatypes`Gibt an, ob die standardmäßigen Spaltendatentyp Zuordnungen verwendet werden, wenn ein Artikel von einem Oracle-Verleger veröffentlicht wird. *use_default_datatypes* ist vom Typ Bit und hat den Standardwert 1.  
  
 **1** = die standardmäßigen Artikel Spalten Zuordnungen werden verwendet. Die standardmäßigen Datentyp Zuordnungen können angezeigt werden, indem [sp_getdefaultdatatypemapping](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md)ausgeführt wird.  
  
 **0** = benutzerdefinierte Artikel Spalten Zuordnungen werden definiert, weshalb [sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) nicht von **sp_addarticle**aufgerufen wird.  
  
 Wenn *use_default_datatypes* auf **0**festgelegt ist, müssen Sie für jede Spalten Zuordnung, die von der Standardeinstellung geändert wird, [sp_changearticlecolumndatatype](../../relational-databases/system-stored-procedures/sp-changearticlecolumndatatype-transact-sql.md) einmal ausführen. Nachdem alle benutzerdefinierten Spalten Zuordnungen definiert wurden, müssen Sie [sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)ausführen.  
  
> [!NOTE]  
>  Dieser Parameter sollte nur für Oracle-Verleger verwendet werden. Wenn *use_default_datatypes* für einen Verleger auf **0** festgelegt wird, wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ein Fehler generiert.  
  
`[ @identityrangemanagementoption = ] identityrangemanagementoption`Gibt an, wie die Identitäts Bereichs Verwaltung für den Artikel behandelt wird. die *identityrangemanagementoption* ist vom Datentyp **nvarchar (10)**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**keine**|Die Replikation führt keine explizite Identitätsbereichsverwaltung aus. Diese Option wird nur aus Gründen der Abwärtskompatibilität mit früheren Versionen von SQL Server verwendet. Ist für die Peer-Replikation nicht zulässig.|  
|**Manuell**|Markiert die Identitätsspalte mithilfe von NOT FOR REPLICATION, um die manuelle Identitätsbereichsverwaltung zu ermöglichen.|  
|**auto**|Gibt die automatisierte Verwaltung von Identitätsbereichen an.|  
|NULL (Standard)|Der Standardwert ist **None** , wenn der Wert von *auto_identity_range* nicht **true**ist. Der Standardwert ist **manuell** in einem Peer-zu-Peer-topologiestandard (*auto_identity_range* wird ignoriert).|  
  
 Aus Gründen der Abwärtskompatibilität, wenn der Wert von *identityrangemanagementoption* NULL ist, wird der Wert *auto_identity_range* geprüft. Wenn der Wert von *identityrangemanagementoption* jedoch nicht NULL ist, wird der Wert *auto_identity_range* ignoriert.  
  
 Weitere Informationen finden Sie unter [Replizieren von Identitätsspalten](../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
`[ @publisher = ] 'publisher'`Gibt einen nicht-- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger an. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  der *Verleger* sollte nicht verwendet werden, wenn einem Verleger ein Artikel hinzugefügt wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
`[ @fire_triggers_on_snapshot = ] 'fire_triggers_on_snapshot'`Gibt an, ob replizierte Benutzer Trigger ausgeführt werden, wenn die Anfangs Momentaufnahme angewendet wird. *fire_triggers_on_snapshot* ist vom Datentyp **nvarchar (5)** und hat den Standardwert false. " **true** " bedeutet, dass Benutzer Trigger für eine replizierte Tabelle ausgeführt werden, wenn die Momentaufnahme angewendet wird. Damit Trigger repliziert werden können, muss der Bitmasken Wert *schema_option* den Wert **0x100**enthalten.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_addarticle** wird bei der Momentaufnahme-oder Transaktions Replikation verwendet.  
  
 Standardmäßig werden bei der Replikation keine Spalten in der Quelltabelle veröffentlicht, wenn der Spaltendatentyp nicht von der Replikation unterstützt wird. Wenn Sie eine solche Spalte veröffentlichen müssen, müssen Sie [sp_articlecolumn](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) ausführen, um die Spalte hinzuzufügen.  
  
 Wird einer Veröffentlichung, die die Peer-zu-Peer-Transaktionsreplikation unterstützt, ein Artikel hinzugefügt, gelten die folgenden Einschränkungen:  
  
-   Parametrisierte Anweisungen müssen für alle logbased-Artikel angegeben werden. Sie müssen **16** in den *Status* Wert einschließen.  
  
-   Name und Besitzer der Ziel- und der Quelltabelle müssen übereinstimmen.  
  
-   Der Artikel kann nicht horizontal oder vertikal gefiltert werden.  
  
-   Die automatische Identitätsbereichsverwaltung wird nicht unterstützt. Sie müssen den Wert manuell für *identityrangemanagementoption*angeben.  
  
-   Wenn eine **Zeitstempel** -Spalte in der Tabelle vorhanden ist, müssen Sie 0x08 in *schema_option* einschließen, um die Spalte als **Zeitstempel**zu replizieren.  
  
-   Der Wert **SQL** kann für *ins_cmd*, *upd_cmd*und *del_cmd*nicht angegeben werden.  
  
 Weitere Informationen finden Sie unter [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 Wenn Sie Objekte veröffentlichen, werden ihre Definitionen auf Abonnenten kopiert. Wenn Sie ein Datenbankobjekt veröffentlichen, das von mindestens einem anderen Objekt abhängig ist, müssen Sie alle Objekte veröffentlichen, auf die verwiesen wird. Wenn Sie beispielsweise eine Sicht veröffentlichen, die von einer Tabelle abhängt, muss auch die Tabelle veröffentlicht werden.  
  
 Wenn *vertical_partition* auf **true**festgelegt ist, wird die Erstellung der Sicht von **sp_addarticle** so lange festgelegt, bis [sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) aufgerufen wird (nachdem die letzte [sp_articlecolumn](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) hinzugefügt wurde).  
  
 Wenn die Veröffentlichung das Aktualisieren von Abonnements zulässt und die veröffentlichte Tabelle keine **uniqueidentifier** -Spalte enthält, fügt **sp_addarticle** der Tabelle automatisch eine **uniqueidentifier** -Spalte hinzu.  
  
 Bei der Replikation auf einen Abonnenten, der keine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (heterogene Replikation) ist, werden nur- [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisungen für **Insert**-, **Update**-und **Delete** -Befehle unterstützt.  
  
 Wenn der Protokollleser-Agent ausgeführt wird, kann das Hinzufügen eines Artikel zu einer Peer-zu-Peer-Veröffentlichung einen Deadlock zwischen dem Protokolllese-Agent und dem Prozess verursachen,der den Artikel hinzufügt. Damit Sie dieses Problem vermeiden, bevor Sie einer Peer-zu-Peer-Veröffentlichung einen Artikel hinzufügen, verwenden Sie den Replikationsmonitor, um den Protokolllese-Agent auf dem Knoten zu beenden, auf dem Sie den Artikel hinzufügen möchten. Starten Sie den Protokolllese-Agent neu, nachdem Sie den Artikel hinzugefügt haben.  
  
 Beim Festlegen `@del_cmd = 'NONE'` `@ins_cmd = 'NONE'` von oder wird die Weitergabe von **Update** Befehlen möglicherweise auch dadurch beeinträchtigt, dass diese Befehle beim Auftreten eines begrenzten Updates nicht gesendet werden. (Ein begrenztes Update ist eine Art von UPDATE-Anweisung vom Verleger, die als DELETE/INSERT-Paar auf dem Abonnenten repliziert wird).  
  
## <a name="default-schema-options"></a>Default Schema Options  
 In dieser Tabelle wird der Standardwert beschrieben, der von der Replikation festgelegt wird, wenn *schema_options* nicht vom Benutzer angegeben wird, wobei dieser Wert vom Replikationstyp (oben angezeigt) und vom Artikeltyp abhängig ist (in der ersten Spalte angezeigt).  
  
|Artikeltyp|Replikationstyp||  
|------------------|----------------------|------|  
||Transaktionsreplikation|Snapshot|  
|**aggregate schema only**|**0x01**|**0x01**|  
|**func schema only**|**0x01**|**0x01**|  
|**indexed view schema only**|**0x01**|**0x01**|  
|**indexed view logbased**|**0x30F3**|**0x3071**|  
|**indexed view logbase manualboth**|**0x30F3**|**0x3071**|  
|**indexed view logbased manualfilter **|**0x30F3**|**0x3071**|  
|**indexed view logbased manualview**|**0x30F3**|**0x3071**|  
|**logbased**|**0x30F3**|**0x3071**|  
|**logbased manualfilter**|**0x30F3**|**0x3071**|  
|**logbased manualview**|**0x30F3**|**0x3071**|  
|**proc exec**|**0x01**|**0x01**|  
|**proc schema only**|**0x01**|**0x01**|  
|**serializable proc exec**|**0x01**|**0x01**|  
|**view schema only**|**0x01**|**0x01**|  
  
> [!NOTE]
>  Wenn eine Veröffentlichung für das verzögerte Update über eine Warteschlange aktiviert ist, wird dem Standardwert, der in der Tabelle angezeigt wird, ein *schema_option* Wert von **0x80** hinzugefügt. Der Standard *schema_option* für eine nicht-- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Veröffentlichung ist **0x050D3**.  
  
## <a name="valid-schema-options"></a>Valid Schema Options  
 In dieser Tabelle werden die zulässigen Werte *schema_option* basierend auf dem Replikationstyp (oben dargestellt) und dem Artikeltyp beschrieben (in der ersten Spalte angezeigt).  
  
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
>  Bei Veröffentlichungen mit verzögertem Update über eine Warteschlange müssen die *schema_option* Werte **0X8000** und **0x80** aktiviert werden. Die unterstützten *schema_option* Werte für nicht-- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Veröffentlichungen sind: **0x01**, **0x02**, **0x10**, **0x40**, **0x80**, **0x1000**, **0x4000** und **0X8000**.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_AddTranArticle](../../relational-databases/replication/codesnippet/tsql/sp-addarticle-transact-sql_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_addarticle**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Definieren eines Artikels](../../relational-databases/replication/publish/define-an-article.md)   
 [sp_articlecolumn &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sp_articlefilter &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md)   
 [sp_articleview &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)   
 [sp_changearticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [sp_helparticlecolumns &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql.md)   
 [Gespeicherte Replikations Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [Veröffentlichen von Daten und Datenbankobjekten](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
