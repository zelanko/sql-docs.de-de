---
title: Sp_addarticle (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 6f24f7ca51f4836c8b1e446283eabb858eb8d387
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493892"
---
# <a name="spaddarticle-transact-sql"></a>sp_addarticle (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Erstellt einen Artikel und fügt ihn zu einer Veröffentlichung hinzu. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung, die der Artikel enthält. Der Name muss in der Datenbank eindeutig sein. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
`[ @article = ] 'article'` Ist der Name des Artikels. Der Name muss innerhalb der Veröffentlichung eindeutig sein. *Artikel* ist **Sysname**, hat keinen Standardwert.  
  
`[ @source_table = ] 'source_table'` Dieser Parameter wurde als veraltet markiert; Verwenden Sie *Source_object* stattdessen.  
  
 *Dieser Parameter wird nicht für Oracle-Verleger unterstützt.*  
  
`[ @destination_table = ] 'destination_table'` Ist der Name der Zieltabelle (Abonnement), wenn sich von *Source_table*oder der gespeicherten Prozedur. *Destination_table* ist **Sysname**, hat den Standardwert NULL, was bedeutet, dass *Source_table* gleich *Destination_table **.*  
  
`[ @vertical_partition = ] 'vertical_partition'` Aktiviert und deaktiviert die spaltenfilterung für einen Tabellenartikel. *Vertical_partition* ist **nchar(5)**, hat den Standardwert "false".  
  
 **"false"** zeigt an, dass keine vertikale Filterung und alle Spalten veröffentlicht.  
  
 **"true"** löscht alle Spalten außer dem deklarierten Primärschlüssel, auf NULL festlegbare Spalten hat keinen Standardwert und Spalten für eindeutige Schlüssel. Spalten werden mit hinzugefügt [Sp_articlecolumn](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md).  
  
`[ @type = ] 'type'` Ist der Typ des Artikels. *Typ* ist **Sysname**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**nur Aggregatschemas**|Aggregatfunktion vom Typ schema only.|  
|**nur Func schema**|Funktion vom Typ schema only.|  
|**indizierte Sicht logbased**|Artikel für protokollbasierte indizierte Sicht. Diese Option wird für Oracle-Verleger nicht unterstützt. Für diesen Artikeltyp muss die Basistabelle nicht separat veröffentlicht werden.|  
|**indizierte Sicht Logbased manualboth**|Artikel für protokollbasierte indizierte Sicht mit manuell erstelltem Filter und manuell erstellter Sicht. Diese Option erfordert, dass Sie beide angeben *Sync_object* und *Filter* Parameter. Für diesen Artikeltyp muss die Basistabelle nicht separat veröffentlicht werden. Diese Option wird für Oracle-Verleger nicht unterstützt.|  
|**indizierte Sicht Logbased manualfilter**|Artikel für protokollbasierte indizierte Sicht mit manuell erstelltem Filter. Diese Option erfordert, dass Sie beide angeben *Sync_object* und *Filter* Parameter. Für diesen Artikeltyp muss die Basistabelle nicht separat veröffentlicht werden. Diese Option wird für Oracle-Verleger nicht unterstützt.|  
|**indizierte Sicht Logbased manualview**|Artikel für protokollbasierte indizierte Sicht mit manuell erstellter Sicht. Diese Option erfordert die Angabe der *Sync_object* Parameter. Für diesen Artikeltyp muss die Basistabelle nicht separat veröffentlicht werden. Diese Option wird für Oracle-Verleger nicht unterstützt.|  
|**Nur indizierte sichtschema**|Indizierte Sicht vom Typ schema only. Für diesen Artikeltyp muss die Basistabelle ebenfalls veröffentlicht werden.|  
|**Logbased** (Standard)|Protokollbasierter Artikel.|  
|**Logbased manualboth**|Protokollbasierter Artikel mit manuell erstelltem Filter und manuell erstellter Sicht. Diese Option erfordert, dass Sie beide angeben *Sync_object* und *Filter* Parameter. Diese Option wird für Oracle-Verleger nicht unterstützt.|  
|**Logbased manualfilter**|Protokollbasierter Artikel mit manuell erstelltem Filter. Diese Option erfordert, dass Sie beide angeben *Sync_object* und *Filter* Parameter. Diese Option wird für Oracle-Verleger nicht unterstützt.|  
|**Logbased manualview**|Protokollbasierter Artikel mit manuell erstellter Sicht. Diese Option erfordert die Angabe der *Sync_object* Parameter. Diese Option wird für Oracle-Verleger nicht unterstützt.|  
|**Proc exec**|Repliziert die Ausführung der gespeicherten Prozedur auf alle Abonnenten des Artikels. Diese Option wird für Oracle-Verleger nicht unterstützt. Es wird empfohlen, dass die Verwendung der Option **serializable Proc Exec** anstelle von **Proc Exec**. Weitere Informationen finden Sie im Abschnitt "Typen der gespeicherten Prozedur Artikeln für die Ausführung" in [Publishing Stored Procedure Execution in Transactional Replication](../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md). Nicht verfügbar, wenn Change Data Capture aktiviert ist.|  
|**Proc Schema nur**|Prozedur vom Typ schema only. Diese Option wird für Oracle-Verleger nicht unterstützt.|  
|**Serializable Proc exec**|Repliziert die Ausführung der gespeicherten Prozedur nur, wenn die Prozedur im Kontext einer serialisierbaren Transaktion ausgeführt wird. Diese Option wird für Oracle-Verleger nicht unterstützt.<br /><br /> Die Prozedur muss innerhalb einer expliziten Transaktion für die Ausführung der Prozedur repliziert wird, werden auch ausgeführt werden.|  
|**nur Schema anzeigen**|Sicht vom Typ schema only. Diese Option wird für Oracle-Verleger nicht unterstützt. Wenn diese Option verwendet wird, müssen Sie auch die Basistabelle veröffentlichen.|  
  
`[ @filter = ] 'filter'` Um die Tabelle horizontal gefiltert wird die gespeicherte Prozedur (erstellt mit FOR REPLICATION) verwendet werden. *Filter* ist **nvarchar(386)**, hat den Standardwert NULL. [Sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) und [Sp_articlefilter](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md) müssen manuell zum Erstellen der Ansicht, und Filtern die gespeicherte Prozedur ausgeführt werden. Bei einem Wert ungleich NULL wird die Filterprozedur nicht erstellt (es wird angenommen, dass die gespeicherte Prozedur manuell erstellt wird).  
  
`[ @sync_object = ] 'sync_object'` Ist der Name der Tabelle oder Sicht, die zum Erzeugen der Datendatei verwendet, um die Momentaufnahme für diesen Artikel darzustellen. *Sync_object* ist **nvarchar(386)**, hat den Standardwert NULL. Wenn der Wert NULL, [Sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) wird aufgerufen, um automatisch die Ansicht verwendet, um die Generierung der Ausgabedatei zu erstellen. Dieser Schritt erfolgt nach jedem Hinzufügen von Spalten mit [Sp_articlecolumn](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md). Bei einem Wert ungleich NULL wird keine Sicht erstellt (es wird angenommen, dass die Sicht manuell erstellt wird).  
  
`[ @ins_cmd = ] 'ins_cmd'` Der Befehlstyp für die Replikation ist verwendet werden, bei der Replikation für diesen Artikel eingefügt. *Ins_cmd* ist **nvarchar(255)**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**NONE**|Es wird keine Aktion ausgeführt.|  
|**CALL sp_MSins_**<br /> **_Tabelle_**  (Standard)<br /><br /> -oder-<br /><br /> **Rufen Sie custom_stored_procedure_name**|Eine gespeicherte Prozedur wird aufgerufen, die auf dem Abonnenten ausgeführt werden soll. Verwenden Sie zum Verwenden dieser Methode der Replikation *Schema_option* , geben die automatische Erstellung der gespeicherten Prozedur, oder erstellen die angegebene gespeicherte Prozedur in der Zieldatenbank jedes Abonnenten des Artikels. *custom_stored_procedure_name* ist der Name einer vom Benutzer erstellten gespeicherten Prozedur. <strong>Sp_MSins_*Tabelle*</strong>  enthält den Namen der Zieltabelle anstelle des dem *_tabulky* -Teils des Parameters. Wenn *Destination_owner* angegeben ist, wird er dem Namen der Zieltabelle vorangestellt wird. Z. B. für die **"ProductCategory"** -Tabelle im Besitz der **Produktion** Schema auf dem Abonnenten, der-Parameter wäre `CALL sp_MSins_ProductionProductCategory`. Für einen Artikel in einer Peer-zu-Peer-Replikationstopologie *_tabulky* mit einem GUID-Wert angefügt. Angeben von *custom_stored_procedure_name* wird für Updateabonnenten nicht unterstützt.|  
|**SQL** oder NULL|Repliziert eine INSERT-Anweisung. Für die INSERT-Anweisung werden Werte für alle in dem Artikel veröffentlichten Spalten bereitgestellt. Der folgende Befehl wird bei Einfügungen repliziert:<br /><br /> `INSERT INTO <table name> VALUES (c1value, c2value, c3value, ..., cnvalue)`|  
  
 Weitere Informationen finden Sie unter [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md)  
  
`[ @del_cmd = ] 'del_cmd'` Der Befehlstyp für die Replikation wird verwendet werden, wenn replizieren, die in diesem Artikel werden gelöscht. *Del_cmd* ist **nvarchar(255)**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**NONE**|Es wird keine Aktion ausgeführt.|  
|**CALLsp_MSdel_**<br /> **_Tabelle_**  (Standard)<br /><br /> -oder-<br /><br /> **Rufen Sie custom_stored_procedure_name**|Eine gespeicherte Prozedur wird aufgerufen, die auf dem Abonnenten ausgeführt werden soll. Verwenden Sie zum Verwenden dieser Methode der Replikation *Schema_option* , geben die automatische Erstellung der gespeicherten Prozedur, oder erstellen die angegebene gespeicherte Prozedur in der Zieldatenbank jedes Abonnenten des Artikels. *custom_stored_procedure_name* ist der Name einer vom Benutzer erstellten gespeicherten Prozedur. <strong>Sp_MSdel_*Tabelle*</strong>  enthält den Namen der Zieltabelle anstelle des dem *_tabulky* -Teils des Parameters. Wenn *Destination_owner* angegeben ist, wird er dem Namen der Zieltabelle vorangestellt wird. Z. B. für die **"ProductCategory"** -Tabelle im Besitz der **Produktion** Schema auf dem Abonnenten, der-Parameter wäre `CALL sp_MSdel_ProductionProductCategory`. Für einen Artikel in einer Peer-zu-Peer-Replikationstopologie *_tabulky* mit einem GUID-Wert angefügt. Angeben von *custom_stored_procedure_name* wird für Updateabonnenten nicht unterstützt.|  
|**XCALL sp_MSdel_**<br /> **_Tabelle_**<br /><br /> -oder-<br /><br /> **XCALL custom_stored_procedure_name**|Ruft eine gespeicherte Prozedur auf, die XCALL-Parameter akzeptiert. Verwenden Sie zum Verwenden dieser Methode der Replikation *Schema_option* , geben die automatische Erstellung der gespeicherten Prozedur, oder erstellen die angegebene gespeicherte Prozedur in der Zieldatenbank jedes Abonnenten des Artikels. Die Angabe einer benutzerdefinierten gespeicherten Prozedur ist für Updateabonnenten nicht zulässig.|  
|**SQL** oder NULL|Repliziert eine DELETE-Anweisung. Für die DELETE-Anweisung werden alle Spaltenwerte der Primärschlüssel bereitgestellt. Der folgende Befehl wird bei Löschungen repliziert:<br /><br /> `DELETE FROM <table name> WHERE pkc1 = pkc1value AND pkc2 = pkc2value AND pkcn = pkcnvalue`|  
  
 Weitere Informationen finden Sie unter [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md)  
  
`[ @upd_cmd = ] 'upd_cmd'` Der Befehlstyp für die Replikation wird verwendet werden, wenn updates für diesen Artikel repliziert. *Upd_cmd* ist **nvarchar(255)**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**NONE**|Es wird keine Aktion ausgeführt.|  
|**CALL sp_MSupd_**<br /> **_Tabelle_**<br /><br /> -oder-<br /><br /> **Rufen Sie custom_stored_procedure_name**|Eine gespeicherte Prozedur wird aufgerufen, die auf dem Abonnenten ausgeführt werden soll. Verwenden Sie zum Verwenden dieser Methode der Replikation *Schema_option* , geben die automatische Erstellung der gespeicherten Prozedur, oder erstellen die angegebene gespeicherte Prozedur in der Zieldatenbank jedes Abonnenten des Artikels.|  
|**MCALL sp_MSupd_**<br /> **_Tabelle_**<br /><br /> -oder-<br /><br /> **MCALL custom_stored_procedure_name**|Ruft eine gespeicherte Prozedur auf, die MCALL-Parameter akzeptiert. Verwenden Sie zum Verwenden dieser Methode der Replikation *Schema_option* , geben die automatische Erstellung der gespeicherten Prozedur, oder erstellen die angegebene gespeicherte Prozedur in der Zieldatenbank jedes Abonnenten des Artikels. *custom_stored_procedure_name* ist der Name einer vom Benutzer erstellten gespeicherten Prozedur. <strong>Sp_MSupd_*Tabelle*</strong>  enthält den Namen der Zieltabelle anstelle des dem *_tabulky* -Teils des Parameters. Wenn *Destination_owner* angegeben ist, wird er dem Namen der Zieltabelle vorangestellt wird. Z. B. für die **"ProductCategory"** -Tabelle im Besitz der **Produktion** Schema auf dem Abonnenten, der-Parameter wäre `MCALL sp_MSupd_ProductionProductCategory`. Für einen Artikel in einer Peer-zu-Peer-Replikationstopologie *_tabulky* mit einem GUID-Wert angefügt. Die Angabe einer benutzerdefinierten gespeicherten Prozedur ist für Updateabonnenten nicht zulässig.|  
|**SCALL sp_MSupd_**<br /> **_Tabelle_**  (Standard)<br /><br /> -oder-<br /><br /> **SCALL custom_stored_procedure_name**|Ruft eine gespeicherte Prozedur auf, die SCALL-Parameter akzeptiert. Verwenden Sie zum Verwenden dieser Methode der Replikation *Schema_option* , geben die automatische Erstellung der gespeicherten Prozedur, oder erstellen die angegebene gespeicherte Prozedur in der Zieldatenbank jedes Abonnenten des Artikels. *custom_stored_procedure_name* ist der Name einer vom Benutzer erstellten gespeicherten Prozedur. <strong>Sp_MSupd_*Tabelle*</strong>  enthält den Namen der Zieltabelle anstelle des dem *_tabulky* -Teils des Parameters. Wenn *Destination_owner* angegeben ist, wird er dem Namen der Zieltabelle vorangestellt wird. Z. B. für die **"ProductCategory"** -Tabelle im Besitz der **Produktion** Schema auf dem Abonnenten, der-Parameter wäre `SCALL sp_MSupd_ProductionProductCategory`. Für einen Artikel in einer Peer-zu-Peer-Replikationstopologie *_tabulky* mit einem GUID-Wert angefügt. Die Angabe einer benutzerdefinierten gespeicherten Prozedur ist für Updateabonnenten nicht zulässig.|  
|**XCALL sp_MSupd_**<br /> **_Tabelle_**<br /><br /> -oder-<br /><br /> **XCALL custom_stored_procedure_name**|Ruft eine gespeicherte Prozedur auf, die XCALL-Parameter akzeptiert. Verwenden Sie zum Verwenden dieser Methode der Replikation *Schema_option* , geben die automatische Erstellung der gespeicherten Prozedur, oder erstellen die angegebene gespeicherte Prozedur in der Zieldatenbank jedes Abonnenten des Artikels. Die Angabe einer benutzerdefinierten gespeicherten Prozedur ist für Updateabonnenten nicht zulässig.|  
|**SQL** oder NULL|Repliziert eine UPDATE-Anweisung. Die UPDATE-Anweisung wird für alle Spaltenwerte und für die Spaltenwerte der Primärschlüssel bereitgestellt. Der folgende Befehl wird bei Updates repliziert:<br /><br /> `UPDATE <table name> SET c1 = c1value, SET c2 = c2value, SET cn = cnvalue WHERE pkc1 = pkc1value AND pkc2 = pkc2value AND pkcn = pkcnvalue`|  
  
> [!NOTE]  
>  Die CALL-, MCALL-, SCALL- und XCALL-Syntax variiert den Umfang der Daten, die an den Abonnenten weitergegeben werden. Die CALL-Syntax übergibt alle Werte für alle eingefügten und gelöschten Spalten. Die SCALL-Syntax übergibt nur die Werte für betroffene Spalten. Die XCALL-Syntax übergibt die Werte für alle Spalten, unabhängig davon, ob diese geändert wurden, einschließlich des vorherigen Werts der Spalte. Weitere Informationen finden Sie unter [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md)  
  
`[ @creation_script = ] 'creation_script'` Ist der Pfad und Name von einem optionalen Artikelschemaskripts, das verwendet wird, um den Artikel in der Abonnementdatenbank zu erstellen. *Creation_script* ist **nvarchar(255)**, hat den Standardwert NULL.  
  
`[ @description = ] 'description'` Ist ein beschreibender Eintrag für den Artikel. *Beschreibung* ist **nvarchar(255)**, hat den Standardwert NULL.  
  
`[ @pre_creation_cmd = ] 'pre_creation_cmd'` Gibt an, was das System tun sollte, wenn beim Anwenden der Momentaufnahme für diesen Artikel ein vorhandenes Objekt mit dem gleichen Namen auf dem Abonnenten erkannt. *Pre_creation_cmd* ist **nvarchar(10)**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**Keine**|Verwendet keinen Befehl.|  
|**delete**|Löscht Daten aus der Zieltabelle vor dem Anwenden der Momentaufnahme. Wird der Artikel horizontal gefiltert, werden nur Daten in Spalten gelöscht, die von der Filterklausel angegeben werden. Wird von Oracle-Verlegern nicht unterstützt, wenn ein horizontaler Filter definiert wurde.|  
|**Drop** (Standard)|Entfernt die Zieltabelle.|  
|**truncate**|Schneidet die Zieltabelle ab. Gilt nicht für ODBC- oder OLE DB-Abonnenten.|  
  
`[ @filter_clause = ] 'filter_clause'` Ist eine Einschränkung (WHERE)-Klausel, die einen horizontalen Filter definiert. Wenn Sie die Einschränkungsklausel eingeben, lassen Sie das Schlüsselwort, in dem. *Filter_clause* ist **Ntext**, hat den Standardwert NULL. Weitere Informationen finden Sie unter [Filtern von veröffentlichten Daten](../../relational-databases/replication/publish/filter-published-data.md).  
  
`[ @schema_option = ] schema_option` Ist eine Bitmaske der schemagenerierungsoption für den angegebenen Artikel. *Schema_option* ist **binary(8)**, und kann die [| (Bitweises OR) ](../../t-sql/language-elements/bitwise-or-transact-sql.md) Produkt eine oder mehrere der folgenden Werte:  
  
> [!NOTE]  
>  Ist dieser Wert NULL, generiert das System automatisch eine gültige Schemaoption für den Artikel, abhängig von anderen Artikeleigenschaften. Die **Default Schema Options** Tabelle, die in den Hinweisen angegebene wird der Wert, der ausgewählt wird, auf der Grundlage der Kombination des Artikeltyps und des Replikationstyps.  
  
|Wert|Description|  
|-----------|-----------------|  
|**0x00**|Deaktiviert die Skripterstellung durch den Momentaufnahme-Agent und verwendet *Creation_script*.|  
|**0x01**|Generiert das Objekterstellungsskript (CREATE TABLE, CREATE PROCEDURE usw.). Dies ist der Standardwert für alle Artikel mit gespeicherten Prozeduren.|  
|**0x02**|Generiert die gespeicherten Prozeduren, die Änderungen für den Artikel weitergeben (falls definiert).|  
|**0x04**|Die Skripterstellung für Identitätsspalten erfolgt mithilfe der IDENTITY-Eigenschaft.|  
|**0x08**|Replizieren von **Zeitstempel** Spalten. Wenn nicht festgelegt, **Zeitstempel** Spalten repliziert werden, als **binäre**.|  
|**0x10**|Generiert einen entsprechenden gruppierten Index. Auch wenn diese Option nicht festgelegt ist, Indizes bezüglich der Primärschlüssel und unique-Einschränkungen werden generiert, wenn sie bereits in einer veröffentlichten Tabelle definiert sind.|  
|**0x20**|Konvertiert benutzerdefinierte Datentypen (UDT) auf dem Abonnenten in Basisdatentypen. Diese Option kann nicht verwendet werden, wenn eine CHECK- oder DEFAULT-Einschränkung für eine UDT-Spalte vorhanden ist, wenn eine UDT-Spalte Teil des Primärschlüssels ist oder wenn eine berechnete Spalte auf eine UDT-Spalte verweist. *Nicht für Oracle-Verleger unterstützt*.|  
|**0x40**|Generiert entsprechende nicht gruppierte Indizes. Auch wenn diese Option nicht festgelegt ist, Indizes bezüglich der Primärschlüssel und unique-Einschränkungen werden generiert, wenn sie bereits in einer veröffentlichten Tabelle definiert sind.|  
|**0x80**|Repliziert Primärschlüsseleinschränkungen. Alle Indizes bezüglich der Einschränkung werden ebenfalls repliziert, auch wenn Optionen **0 x 10** und **0 x 40** sind nicht aktiviert.|  
|**0x100**|Repliziert Benutzertrigger für einen Tabellenartikel, wenn definiert. *Nicht für Oracle-Verleger unterstützt*.|  
|**0x200**|Repliziert Fremdschlüsseleinschränkungen. Wenn die Tabelle, auf die verwiesen wird, nicht Teil einer Veröffentlichung ist, werden keine Fremdschlüsseleinschränkungen für eine veröffentlichte Tabelle repliziert. *Nicht für Oracle-Verleger unterstützt*.|  
|**0x400**|Repliziert CHECK-Einschränkungen. *Nicht für Oracle-Verleger unterstützt*.|  
|**0x800**|Repliziert Standards. *Nicht für Oracle-Verleger unterstützt*.|  
|**0x1000**|Repliziert die Sortierung auf Spaltenebene.<br /><br /> **Hinweis**: Dieser Option sollte für Oracle-Verleger eingerichtet werden, um Vergleiche zu ermöglichen, die nach Groß-/Kleinschreibung unterscheiden.|  
|**0x2000**|Repliziert erweiterte Eigenschaften, die dem Quellobjekt des veröffentlichten Artikels zugeordnet sind. *Nicht für Oracle-Verleger unterstützt*.|  
|**0x4000**|Repliziert UNIQUE-Einschränkungen. Alle Indizes bezüglich der Einschränkung werden ebenfalls repliziert, auch wenn Optionen **0 x 10** und **0 x 40** sind nicht aktiviert.|  
|**0x8000**|Diese Option ist für [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]-Verleger nicht gültig.|  
|**0x10000**|Repliziert CHECK-Einschränkungen als NOT FOR REPLICATION, sodass die Einschränkungen während der Synchronisierung nicht erzwungen werden.|  
|**0x20000**|Repliziert FOREIGN KEY-Einschränkungen als NOT FOR REPLICATION, sodass diese Einschränkungen bei der Synchronisierung nicht erzwungen werden.|  
|**0x40000**|Repliziert Dateigruppen, die mit einer partitionierten Tabelle oder einem Index verbunden sind.|  
|**0x80000**|Repliziert das Partitionsschema für eine partitionierte Tabelle.|  
|**0x100000**|Repliziert das Partitionsschema für einen partitionierten Index.|  
|**0x200000**|Repliziert Tabellenstatistiken.|  
|**0x400000**|Standardbindungen|  
|**0x800000**|Regelbindungen|  
|**0x1000000**|Volltextindex|  
|**0x2000000**|XML-schemaauflistungen gebunden **Xml** Spalten werden nicht repliziert.|  
|**0x4000000**|Repliziert Indizes für **Xml** Spalten.|  
|**0x8000000**|Legt Schemas an, die auf dem Abonnent noch nicht vorhanden sind.|  
|**0x10000000**|Konvertiert **Xml** Spalten **Ntext** auf dem Abonnenten.|  
|**0x20000000**|Konvertiert, die große Objekttypen Daten (**nvarchar(max)**, **varchar(max)**, und **'varbinary(max)'**) in eingeführte [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Datentypen, die auf unterstütztwerden[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].|  
|**0x40000000**|Berechtigungen für die Replikation.|  
|**0x80000000**|Der Versuch, Abhängigkeiten für Objekte zu löschen, die nicht Teil der Veröffentlichung sind.|  
|**0x100000000**|Mit dieser Option können Sie das FILESTREAM-Attribut replizieren, wenn es für angegeben wird **'varbinary(max)'** Spalten. Geben Sie diese Option nicht an, wenn Sie Tabellen auf [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]-Abonnenten replizieren. Replizieren von Tabellen mit FILESTREAM-Spalten auf [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] -Abonnenten wird unabhängig von der Festlegung dieser Schemaoption nicht unterstützt.<br /><br /> Siehe die verwandte Option **0 x 800000000**.|  
|**0x200000000**|Konvertiert Datentypen für Datum und Uhrzeit (**Datum**, **Zeit**, **Datetimeoffset**, und **datetime2**) in eingeführte [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] auf Daten Typen, die in früheren Versionen von unterstützt werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**0x400000000**|Repliziert die Komprimierungsoption für Daten und Indizes. Weitere Informationen finden Sie unter [Data Compression](../../relational-databases/data-compression/data-compression.md).|  
|**0x800000000**|Legen Sie diese Option fest, um FILESTREAM-Daten in einer eigenen Dateigruppe auf dem Abonnenten zu speichern. Wenn diese Option nicht festgelegt wird, werden FILESTREAM-Daten in der Standarddateigruppe gespeichert. Bei der Replikation werden keine Dateigruppen erstellt. Daher müssen Sie beim Festlegen dieser Option die Dateigruppe erstellen, bevor Sie die Momentaufnahme auf dem Abonnenten anwenden. Weitere Informationen zum Erstellen von Objekten vor dem Anwenden der Momentaufnahme, finden Sie unter [Ausführen von Skripts vor und nach dem Anwenden der Momentaufnahme](../../relational-databases/replication/snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied).<br /><br /> Siehe die verwandte Option **0 x 100000000**.|  
|**0x1000000000**|Konvertiert die common Language Runtime (CLR) eine benutzerdefinierte Typen (UDTs, die größer als 8000 Bytes in) **'varbinary(max)'** , sodass Spalten vom Typ UDT auf Abonnenten repliziert werden können, die ausgeführt werden [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
|**0x2000000000**|Konvertiert die **Hierarchyid** Datentyp, **'varbinary(max)'** so, dass Spalten vom Typ **Hierarchyid** können repliziert werden, auf Abonnenten, die ausgeführt werden [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Weitere Informationen zur Verwendung von **Hierarchyid** Spalten in replizierten Tabellen finden Sie unter [Hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md).|  
|**0x4000000000**|Repliziert die gefilterten Indizes in der Tabelle. Weitere Informationen zu gefilterten Indizes finden Sie unter [erstellen gefilterter Indizes](../../relational-databases/indexes/create-filtered-indexes.md).|  
|**0x8000000000**|Konvertiert die **Geography** und **Geometrie** -Datentypen in **'varbinary(max)'** , sodass Spalten dieser Typen auf Abonnenten repliziert werden können, auf denen [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
|**0x10000000000**|Repliziert Indizes für Spalten vom Typ **Geography** und **Geometrie**.|  
|**0x20000000000**|Repliziert das SPARSE-Attribut für Spalten. Weitere Informationen zu diesem Attribut finden Sie unter [Verwenden von Sparsespalten](../../relational-databases/tables/use-sparse-columns.md).|  
|**0x40000000000**|Aktivieren Sie die Skripterstellung durch den Momentaufnahme-Agent zum Erstellen einer speicheroptimierten Tabelle auf dem Abonnenten.|  
|**0x80000000000**|Konvertiert gruppierten Index, die nicht gruppierten Index für Speicheroptimierte Artikel.|  
|**0x400000000000**|Alle nicht gruppierten columnstore-Indizes für die Tabellen repliziert|  
|**0x800000000000**|Repliziert alle Flitered nicht gruppierten columnstore-Indizes für die Tabellen an.|  
|NULL|Die Replikation automatisch aktiviert *Schema_option* auf einen Standardwert, hängt der Wert der von anderen Artikeleigenschaften. Die in den Hinweisen enthaltene Tabelle "Default Schema Options" zeigt die Standardschemaoptionen auf der Grundlage des Artikeltyps und des Replikationstyps an.<br /><br /> Der Standard für nicht-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Veröffentlichungen ist **0x050D3**.|  
  
 Nicht alle *Schema_option* Werte sind für alle Replikations- oder Artikeltyp gültig. Die **Valid Schema Options** Tabelle im Abschnitt "Hinweise" zeigt die gültigen Schemaoptionen an, die ausgewählt werden können, auf der Grundlage der Kombination des Artikeltyps und des Replikationstyps.  
  
`[ @destination_owner = ] 'destination_owner'` Ist der Name des Besitzers des Zielobjekts. *Destination_owner* ist **Sysname**, hat den Standardwert NULL. Wenn *Destination_owner* nicht angegeben ist, wird der Besitzer angegeben ist, automatisch basierend auf den folgenden Regeln:  
  
|Bedingung|Zielobjektbesitzer|  
|---------------|------------------------------|  
|Die Veröffentlichung generiert die Anfangsmomentaufnahme, die nur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Abonnenten unterstützt, über das Massenkopieren im einheitlichen Modus.|Standardmäßig auf den Wert der *der Standardwert*.|  
|Veröffentlicht von einem Nicht-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verleger.|Standardmäßig wird der Besitzer der Zieldatenbank verwendet.|  
|Die Veröffentlichung generiert die Anfangsmomentaufnahme, die Nicht-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Abonnenten unterstützt, über das Massenkopieren im Zeichenmodus.|Nicht zugewiesen.|  
  
 Unterstützung von nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnenten *Destination_owner* muss NULL sein.  
  
`[ @status = ] status` Gibt an, wenn der Artikel ist aktiv und zusätzliche Optionen für die wie Änderungen weitergegeben werden. *Status* ist **Tinyint**, und kann die [| (Bitweises OR) ](../../t-sql/language-elements/bitwise-or-transact-sql.md) Produkt eine oder mehrere der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Der Artikel ist aktiv.|  
|**8**|Bezieht den Spaltennamen in INSERT-Anweisungen mit ein.|  
|**16** (Standard)|Verwendet parametrisierte Anweisungen.|  
|**24**|Bezieht den Spaltennamen in INSERT-Anweisungen mit ein und verwendet parametrisierte Anweisungen.|  
|**64**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
 Ein aktiver Artikel, der parametrisierte Anweisungen verwendet, würde in dieser Spalte beispielsweise den Wert 17 anzeigen. Der Wert **0** bedeutet, dass der Artikel inaktiv ist und keine zusätzlichen Eigenschaften definiert wurden.  
  
`[ @source_owner = ] 'source_owner'` Ist der Besitzer des Quellobjekts. *Der Standardwert* ist **Sysname**, hat den Standardwert NULL. *Der Standardwert* für Oracle-Verleger muss angegeben werden.  
  
`[ @sync_object_owner = ] 'sync_object_owner'` Ist der Besitzer der Sicht, die den veröffentlichten Artikel definiert. *Der Standardwert* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @filter_owner = ] 'filter_owner'` Ist der Besitzer des Filters. *Der Standardwert* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @source_object = ] 'source_object'` Ist das Datenbankobjekt, das veröffentlicht werden. *Source_object* ist **Sysname**, hat den Standardwert NULL. Wenn *Source_table* NULL ist, *Source_object* darf nicht NULL sein. *Source_object* sollte verwendet werden, anstelle von *Source_table*. Weitere Informationen zu den Typen von Objekten, die mit der Momentaufnahme- oder Transaktionsreplikation veröffentlicht werden können, finden Sie unter [Veröffentlichen von Daten und Datenbankobjekte](../../relational-databases/replication/publish/publish-data-and-database-objects.md).  
  
`[ @artid = ] _article_ID_ OUTPUT` Ist die Artikel-ID des neuen Artikels. *Article_id* ist **Int** hat den Standardwert NULL, und es ist ein OUTPUT-Parameter.  
  
`[ @auto_identity_range = ] 'auto_identity_range'` Aktiviert und deaktiviert die automatische Behandlung von Identitätsbereichen für eine Veröffentlichung, zu dem Zeitpunkt, die sie erstellt wird. *Auto_identity_range* ist **nvarchar(5)**, und kann einen der folgenden Werte:  
  
|Wert|Description|  
|-----------|-----------------|  
|**true**|Aktiviert die automatische Behandlung von Identitätsbereichen|  
|**false**|Deaktiviert die automatische Behandlung von Identitätsbereichen|  
|Null(Default)|Von Identitätsbereichen wird festgelegt, indem *Identityrangemanagementoption*.|  
  
> [!NOTE]  
>  *Auto_identity_range* ist veraltet und wird nur zur Abwärtskompatibilität bereitgestellt. Verwenden Sie *Identityrangemanagementoption* zum Verwaltungsoptionen für Identitätsbereiche angeben. Weitere Informationen finden Sie unter [Replizieren von Identitätsspalten](../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
`[ @pub_identity_range = ] pub_identity_range` Steuert die Bereichsgröße auf dem Verleger aus, wenn der Artikel hat *Identityrangemanagementoption* festgelegt **automatisch** oder *Auto_identity_range* festgelegt **"true"** . *Pub_identity_range* ist **Bigint**, hat den Standardwert NULL. *Nicht für Oracle-Verleger unterstützt*.  
  
`[ @identity_range = ] identity_range` Steuert die Bereichsgröße auf dem Abonnenten, wenn der Artikel hat *Identityrangemanagementoption* festgelegt **automatisch** oder *Auto_identity_range* festgelegt **"true"** . *Identity_range* ist **Bigint**, hat den Standardwert NULL. Wird verwendet, wenn *Auto_identity_range* nastaven NA hodnotu **"true"**. *Nicht für Oracle-Verleger unterstützt*.  
  
`[ @threshold = ] threshold` Ist der Prozentsatz-Wert, der steuert, wann der Verteilungs-Agent einen neuen Identitätsbereich zuweist. Wenn der Prozentsatz der Werte in angegebenen *Schwellenwert* wird verwendet, erstellt der Verteilungs-Agent einen neuen Identitätsbereich. *Schwellenwert für* ist **Bigint**, hat den Standardwert NULL. Wird verwendet, wenn *Identityrangemanagementoption* nastaven NA hodnotu **automatisch** oder *Auto_identity_range* nastaven NA hodnotu **"true"**. *Nicht für Oracle-Verleger unterstützt*.  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot` Bestätigt, dass die von dieser gespeicherten Prozedur ausgeführte Aktion eine vorhandene Momentaufnahme für ungültig erklären kann. *Force_invalidate_snapshot* ist eine **Bit**, hat den Standardwert 0.  
  
 **0** gibt an, dass das Hinzufügen eines Artikels nicht die Momentaufnahme ungültig werden kann. Wenn die gespeicherte Prozedur erkennt, dass die Änderungen eine neue Momentaufnahme erfordern, tritt ein Fehler auf, und es werden keine Änderungen durchgeführt.  
  
 **1** gibt an, dass das Hinzufügen ein Artikels kann dazu führen, dass die Momentaufnahme ungültig wird, und wenn Abonnements vorhanden sind, würde, eine neue Momentaufnahme erfordern über die Berechtigung für die vorhandene Momentaufnahme als veraltet zu markieren und eine neue Momentaufnahme generiert werden kann.  
  
`[ @use_default_datatypes = ] use_default_datatypes` Ist, gibt an, ob die standardmäßigen datentypzuordnungen Spalte beim Veröffentlichen eines Artikels von einem Oracle-Verleger verwendet werden. *Use_default_datatypes* bit und hat den Standardwert 1.  
  
 **1** = Standard Artikelspalte Zuordnungen verwendet werden. Die Standard-datentypzuordnungen können angezeigt werden, indem Sie Ausführung [Sp_getdefaultdatatypemapping](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md).  
  
 **0** = benutzerdefinierte artikelspaltenzuordnungen definiert wurden; daher [Sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) wird nicht aufgerufen werden, indem **Sp_addarticle**.  
  
 Wenn *Use_default_datatypes* nastaven NA hodnotu **0**, müssen Sie ausführen, [Sp_changearticlecolumndatatype](../../relational-databases/system-stored-procedures/sp-changearticlecolumndatatype-transact-sql.md) einmal für jede spaltenzuordnung, die von der Standardeinstellung geändert wird. Nach dem aller benutzerdefinierten spaltenzuordnungen definiert wurden, müssen Sie ausführen, [Sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md).  
  
> [!NOTE]  
>  Dieser Parameter sollte nur für Oracle-Verleger verwendet werden. Festlegen von *Use_default_datatypes* zu **0** für eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger wird ein Fehler generiert.  
  
`[ @identityrangemanagementoption = ] identityrangemanagementoption` Gibt an, wie die Verwaltung des Identitätsbereichs für den Artikel behandelt wird. *Identityrangemanagementoption* ist **nvarchar(10)**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**Keine**|Die Replikation führt keine explizite Identitätsbereichsverwaltung aus. Diese Option wird nur aus Gründen der Abwärtskompatibilität mit früheren Versionen von SQL Server verwendet. Ist für die Peer-Replikation nicht zulässig.|  
|**manual**|Markiert die Identitätsspalte mithilfe von NOT FOR REPLICATION, um die manuelle Identitätsbereichsverwaltung zu ermöglichen.|  
|**auto**|Gibt die automatisierte Verwaltung von Identitätsbereichen an.|  
|Null(Default)|Standardmäßig **keine** Wenn der Wert des *Auto_identity_range* nicht **"true"**. Standardmäßig **manuelle** in einer Peer-zu-Peer-Topologie-Default (*Auto_identity_range* wird ignoriert).|  
  
 Für die Abwärtskompatibilität bei der der Wert des *Identityrangemanagementoption* NULL ist, den Wert der *Auto_identity_range* aktiviert ist. Jedoch, wenn der Wert des *Identityrangemanagementoption* ist nicht NULL, und klicken Sie dann auf den Wert der *Auto_identity_range* wird ignoriert.  
  
 Weitere Informationen finden Sie unter [Replizieren von Identitätsspalten](../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
`[ @publisher = ] 'publisher'` Gibt einen nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger. *Publisher* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  *Publisher* sollte nicht verwendet werden, wenn ein Artikel hinzugefügt eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger.  
  
`[ @fire_triggers_on_snapshot = ] 'fire_triggers_on_snapshot'` Ist repliziert Benutzertrigger ausgeführt werden, wenn die anfangsmomentaufnahme angewendet wird. *Fire_triggers_on_snapshot* ist **nvarchar(5)**, hat den Standardwert "false". **"true"** bedeutet, dass Benutzertrigger für eine replizierte Tabelle ausgeführt werden, wenn die Momentaufnahme angewendet wird. In der Reihenfolge, damit Trigger repliziert werden der Bitmaskenwert von *Schema_option* muss den Wert enthalten **0 x 100**.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_addarticle** wird bei Momentaufnahme- oder Transaktionsreplikation verwendet.  
  
 Standardmäßig werden bei der Replikation keine Spalten in der Quelltabelle veröffentlicht, wenn der Spaltendatentyp nicht von der Replikation unterstützt wird. Wenn Sie eine solche Spalte veröffentlichen möchten, müssen Sie ausführen [Sp_articlecolumn](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) um die Spalte hinzuzufügen.  
  
 Wird einer Veröffentlichung, die die Peer-zu-Peer-Transaktionsreplikation unterstützt, ein Artikel hinzugefügt, gelten die folgenden Einschränkungen:  
  
-   Parametrisierte Anweisungen müssen für alle logbased-Artikel angegeben werden. Sie müssen einschließen **16** in die *Status* Wert.  
  
-   Name und Besitzer der Ziel- und der Quelltabelle müssen übereinstimmen.  
  
-   Der Artikel kann nicht horizontal oder vertikal gefiltert werden.  
  
-   Die automatische Identitätsbereichsverwaltung wird nicht unterstützt. Geben Sie einen Wert manuell für *Identityrangemanagementoption*.  
  
-   Wenn eine **Zeitstempel** Spalte, die in der Tabelle vorhanden ist, müssen Sie 0 x 08 in einschließen *Schema_option* zum Replizieren der Spalte als **Zeitstempel**.  
  
-   Der Wert **SQL** kann nicht angegeben werden, für die *Ins_cmd*, *Upd_cmd*, und *Del_cmd*.  
  
 Weitere Informationen finden Sie unter [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 Wenn Sie Objekte veröffentlichen, werden ihre Definitionen auf Abonnenten kopiert. Wenn Sie ein Datenbankobjekt veröffentlichen, das von mindestens einem anderen Objekt abhängig ist, müssen Sie alle Objekte veröffentlichen, auf die verwiesen wird. Wenn Sie beispielsweise eine Sicht veröffentlichen, die von einer Tabelle abhängt, muss auch die Tabelle veröffentlicht werden.  
  
 Wenn *Vertical_partition* nastaven NA hodnotu **"true"**, **Sp_addarticle** verzögert die Erstellung der Sicht, bis [Sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) heißt (nach die letzte [Sp_articlecolumn](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) hinzugefügt wird).  
  
 Wenn die Veröffentlichung updateabonnements zulässt und die veröffentlichte Tabelle keine **Uniqueidentifier** Spalte **Sp_addarticle** Fügt eine **Uniqueidentifier** Spalte in der Tabelle automatisch.  
  
 Wenn auf einen Abonnenten repliziert werden, die keine Instanz des ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (heterogene Replikation), nur [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen unterstützt **einfügen**, **UPDATE**, und **Löschen** Befehle.  
  
 Wenn der Protokollleser-Agent ausgeführt wird, kann das Hinzufügen eines Artikel zu einer Peer-zu-Peer-Veröffentlichung einen Deadlock zwischen dem Protokolllese-Agent und dem Prozess verursachen,der den Artikel hinzufügt. Damit Sie dieses Problem vermeiden, bevor Sie einer Peer-zu-Peer-Veröffentlichung einen Artikel hinzufügen, verwenden Sie den Replikationsmonitor, um den Protokolllese-Agent auf dem Knoten zu beenden, auf dem Sie den Artikel hinzufügen möchten. Starten Sie den Protokolllese-Agent neu, nachdem Sie den Artikel hinzugefügt haben.  
  
 Beim Festlegen `@del_cmd = 'NONE'` oder `@ins_cmd = 'NONE'`, die Weitergabe von **aktualisieren** Befehle können auch von nicht diese Befehle senden, wenn es sich bei einem begrenzten Update beeinflusst werden. (Ein begrenztes Update ist eine Art von UPDATE-Anweisung vom Verleger, die als DELETE/INSERT-Paar auf dem Abonnenten repliziert wird).  
  
## <a name="default-schema-options"></a>Default Schema Options  
 Diese Tabelle wird beschrieben, den Standardwert von der Replikation festgelegt werden, wenn *Schema_options* ist nicht vom Benutzer, in denen dieser Wert hängt von der Replikationstyp (oben) und den Artikeltyp (in der ersten Spalte) angegeben.  
  
|Artikeltyp|Replikationstyp||  
|------------------|----------------------|------|  
||Transaktion|Momentaufnahme|  
|**nur Aggregatschemas**|**0x01**|**0x01**|  
|**nur Func schema**|**0x01**|**0x01**|  
|**Nur indizierte sichtschema**|**0x01**|**0x01**|  
|**indizierte Sicht logbased**|**0x30F3**|**0x3071**|  
|**die logarithmische Basis Manualboth indizierte Sicht**|**0x30F3**|**0x3071**|  
|**indizierte Sicht Logbased manualfilter**|**0x30F3**|**0x3071**|  
|**indizierte Sicht Logbased manualview**|**0x30F3**|**0x3071**|  
|**logbased**|**0x30F3**|**0x3071**|  
|**Logbased manualfilter**|**0x30F3**|**0x3071**|  
|**Logbased manualview**|**0x30F3**|**0x3071**|  
|**Proc exec**|**0x01**|**0x01**|  
|**Proc Schema nur**|**0x01**|**0x01**|  
|**Serializable Proc exec**|**0x01**|**0x01**|  
|**nur Schema anzeigen**|**0x01**|**0x01**|  
  
> [!NOTE]
>  Wenn eine Veröffentlichung aktiviert ist, für das verzögerte Update eine *Schema_option* Wert **0 x 80** hinzugefügt wird, auf den Standardwert, der in der Tabelle dargestellt. Der Standardwert *Schema_option* für einen nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Veröffentlichung **0x050D3**.  
  
## <a name="valid-schema-options"></a>Valid Schema Options  
 Diese Tabelle beschreibt die zulässigen Werte von *Schema_option* basierend auf dem Replikationstyp (oben dargestellt) und den Artikeltyp (in der ersten Spalte angezeigt).  
  
|Artikeltyp|Replikationstyp||  
|------------------|----------------------|------|  
||Transaktion|Momentaufnahme|  
|**logbased**|Alle Optionen|Alle Optionen, aber **0 x 02**|  
|**Logbased manualfilter**|Alle Optionen|Alle Optionen, aber **0 x 02**|  
|**Logbased manualview**|Alle Optionen|Alle Optionen, aber **0 x 02**|  
|**indizierte Sicht logbased**|Alle Optionen|Alle Optionen, aber **0 x 02**|  
|**indizierte Sicht Logbased manualfilter**|Alle Optionen|Alle Optionen, aber **0 x 02**|  
|**indizierte Sicht Logbased manualview**|Alle Optionen|Alle Optionen, aber **0 x 02**|  
|**die logarithmische Basis Manualboth indizierte Sicht**|Alle Optionen|Alle Optionen, aber **0 x 02**|  
|**Proc exec**|**0 x 01**, **0 x 20**, **0 x 2000**, **0 x 400000**, **0 x 800000**, **0x2000000**, **0x8000000**, **0 x 10000000**, **0 x 20000000**, **0 x 40000000**, und **0 x 80000000**|**0 x 01**, **0 x 20**, **0 x 2000**, **0 x 400000**, **0 x 800000**, **0x2000000**, **0x8000000**, **0 x 10000000**, **0 x 20000000**, **0 x 40000000**, und **0 x 80000000**|  
|**Serializable Proc exec**|**0 x 01**, **0 x 20**, **0 x 2000**, **0 x 400000**, **0 x 800000**, **0x2000000**, **0x8000000**, **0 x 10000000**, **0 x 20000000**, **0 x 40000000**, und **0 x 80000000**|**0 x 01**, **0 x 20**, **0 x 2000**, **0 x 400000**, **0 x 800000**, **0x2000000**, **0x8000000**, **0 x 10000000**, **0 x 20000000**, **0 x 40000000**, und **0 x 80000000**|  
|**Proc Schema nur**|**0 x 01**, **0 x 20**, **0 x 2000**, **0 x 400000**, **0 x 800000**, **0x2000000**, **0x8000000**, **0 x 10000000**, **0 x 20000000**, **0 x 40000000**, und **0 x 80000000**|**0 x 01**, **0 x 20**, **0 x 2000**, **0 x 400000**, **0 x 800000**, **0x2000000**, **0x8000000**, **0 x 10000000**, **0 x 20000000**, **0 x 40000000**, und **0 x 80000000**|  
|**nur Schema anzeigen**|**0 x 01**, **0x010**, **0 x 020**, **0 x 040**, **0 x 0100**, **0 x 2000**, **0 x 40000**, **0 x 100000**, **0x200000**, **0 x 400000**, **0 x 800000**,  **0x2000000**, **0x8000000**, **0 x 40000000**, und **0 x 80000000**|**0 x 01**, **0x010**, **0 x 020**, **0 x 040**, **0 x 0100**, **0 x 2000**, **0 x 40000**, **0 x 100000**, **0x200000**, **0 x 400000**, **0 x 800000**,  **0x2000000**, **0x8000000**, **0 x 40000000**, und **0 x 80000000**|  
|**nur Func schema**|**0 x 01**, **0 x 20**, **0 x 2000**, **0 x 400000**, **0 x 800000**, **0x2000000**, **0x8000000**, **0 x 10000000**, **0 x 20000000**, **0 x 40000000**, und **0 x 80000000**|**0 x 01**, **0 x 20**, **0 x 2000**, **0 x 400000**, **0 x 800000**, **0x2000000**, **0x8000000**, **0 x 10000000**, **0 x 20000000**, **0 x 40000000**, und **0 x 80000000**|  
|**Nur indizierte sichtschema**|**0 x 01**, **0x010**, **0 x 020**, **0 x 040**, **0 x 0100**, **0 x 2000**, **0 x 40000**, **0 x 100000**, **0x200000**, **0 x 400000**, **0 x 800000**,  **0x2000000**, **0x8000000**, **0 x 40000000**, und **0 x 80000000**|**0 x 01**, **0x010**, **0 x 020**, **0 x 040**, **0 x 0100**, **0 x 2000**, **0 x 40000**, **0 x 100000**, **0x200000**, **0 x 400000**, **0 x 800000**,  **0x2000000**, **0x8000000**, **0 x 40000000**, und **0 x 80000000**|  
  
> [!NOTE]
>  Für Veröffentlichungen mit in der Warteschlange die *Schema_option* Werte **0 x 8000** und **0 x 80** muss aktiviert sein. Die unterstützten *Schema_option* -Werte für nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Veröffentlichungen werden: **0 x 01**, **0 x 02**, **0 x 10**, **0 x 40**, **0 x 80**, **0 x 1000**,  **0 x 4000** und **0 x 8000**.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_AddTranArticle](../../relational-databases/replication/codesnippet/tsql/sp-addarticle-transact-sql_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_addarticle**.  
  
## <a name="see-also"></a>Siehe auch  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [sp_articlecolumn &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sp_articlefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md)   
 [sp_articleview &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)   
 [sp_changearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [sp_helparticlecolumns &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql.md)   
 [Gespeicherte Replikationsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [Veröffentlichen von Daten und Datenbankobjekten](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
