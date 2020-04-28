---
title: sp_helparticle (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helparticle_TSQL
- sp_helparticle
helpviewer_keywords:
- sp_helparticle
ms.assetid: 9c4a1a88-56f1-45a0-890c-941b8e0f0799
author: stevestein
ms.author: sstein
ms.openlocfilehash: e1e71d3795b233ec335cf01848fa3b226a6ebde0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68771101"
---
# <a name="sp_helparticle-transact-sql"></a>sp_helparticle (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Zeigt Informationen zu einem Artikel an. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt. Für Oracle-Verleger wird diese gespeicherte Prozedur auf dem Verteiler auf jeder Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helparticle [ @publication = ] 'publication'   
    [ , [ @article = ] 'article' ]  
    [ , [ @returnfilter = ] returnfilter ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @found = ] found OUTPUT ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @article = ] 'article'`Der Name eines Artikels in der Veröffentlichung. der *Artikel* ist vom **%** **Datentyp vom Datentyp sysname**und hat den Standardwert. Wenn der *Artikel* nicht angegeben wird, werden Informationen zu allen Artikeln für die angegebene Veröffentlichung zurückgegeben.  
  
`[ @returnfilter = ] returnfilter`Gibt an, ob die Filter Klausel zurückgegeben werden soll. *returnfilter* ist vom Typ **Bit**. der Standardwert ist **1**, wodurch die Filter Klausel zurückgegeben wird.  
  
`[ @publisher = ] 'publisher'`Gibt einen nicht- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verleger an. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  der *Verleger* sollte nicht angegeben werden, wenn Informationen zu einem Artikel angefordert werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , der von einem Verleger veröffentlicht wurde.  
  
`[ @found = ] found OUTPUT`Nur interne Verwendung.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**Artikel-ID**|**int**|ID des Artikels.|  
|**article name**|**sysname**|Der Name des Artikels.|  
|**base object**|**nvarchar (257)**|Name der zugrunde liegenden Tabelle, dargestellt durch den Artikel oder die gespeicherte Prozedur.|  
|**destination-Objekt**|**sysname**|Name der Zieltabelle (Abonnement).|  
|**synchronization object**|**nvarchar (257)**|Name der Sicht, die den veröffentlichten Artikel definiert.|  
|**type**|**smallint**|Der Artikeltyp:<br /><br /> **1** = Protokoll basiert.<br /><br /> **3** = Protokoll basiert mit manuellem Filter.<br /><br /> **5** = Protokoll basiert mit manueller Sicht.<br /><br /> **7** = Protokoll basiert mit manuellem Filter und manueller Ansicht.<br /><br /> **8** = Ausführung gespeicherter Prozeduren.<br /><br /> **24** = serialisierbare Ausführung gespeicherter Prozeduren.<br /><br /> **32** = gespeicherte Prozedur (nur Schema).<br /><br /> **64** = Ansicht (nur Schema).<br /><br /> **96** = Aggregatfunktion (nur Schema).<br /><br /> **128** = Funktion (nur Schema).<br /><br /> **257** = Protokoll basierte indizierte Sicht.<br /><br /> **259** = Protokoll basierte indizierte Sicht mit manuellem Filter.<br /><br /> **261** = Protokoll basierte indizierte Sicht mit manueller Sicht.<br /><br /> **263** = Protokoll basierte indizierte Sicht mit manuellem Filter und manueller Sicht.<br /><br /> **320** = indizierte Sicht (nur Schema).<br /><br />|  
|**status**|**tinyint**|Kann das [& (Bitweises and)-](../../t-sql/language-elements/bitwise-and-transact-sql.md) Ergebnis einer oder mehrerer oder dieser Artikeleigenschaften sein:<br /><br /> **0x00** = [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> **0x01** = der Artikel ist aktiv.<br /><br /> **0x08** = schließt den Spaltennamen in INSERT-Anweisungen ein.<br /><br /> **0x16** = parametrisierte Anweisungen verwenden.<br /><br /> **0x32** = parametrisierte Anweisungen verwenden und den Spaltennamen in INSERT-Anweisungen einschließen.|  
|**filter**|**nvarchar (257)**|Die gespeicherte Prozedur, mit der die Tabelle horizontal gefiltert wird. Diese gespeicherte Prozedur muss mit der FOR REPLICATION-Klausel erstellt werden.|  
|**Beschreibung**|**nvarchar(255)**|Beschreibungseintrag für den Artikel.|  
|**insert_command**|**nvarchar(255)**|Der Replikationsbefehlstyp, der zur Replikation von Einfügungen bei Tabellenartikeln verwendet wird. Weitere Informationen finden Sie unter [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md).|  
|**update_command**|**nvarchar(255)**|Der Replikationsbefehlstyp, der zur Replikation von Updates bei Tabellenartikeln verwendet wird. Weitere Informationen finden Sie unter [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md).|  
|**delete_command**|**nvarchar(255)**|Der Replikationsbefehlstyp, der zur Replikation von Löschungen bei Tabellenartikeln verwendet wird. Weitere Informationen finden Sie unter [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md).|  
|**creation script path**|**nvarchar(255)**|Pfad und Name eines Artikelschemaskripts, mit dem Zieltabellen erstellt werden.|  
|**vertical partition**|**bit**|Gibt an, ob die vertikale Partitionierung für den Artikel aktiviert ist. der Wert **1** bedeutet, dass die vertikale Partitionierung aktiviert ist.|  
|**pre_creation_cmd**|**tinyint**|Der Vorabbefehl für die Anweisungen DROP TABLE, DELETE TABLE oder TRUNCATE TABLE.|  
|**filter_clause**|**ntext**|WHERE-Klausel für das horizontale Filtern.|  
|**schema_option**|**Binär (8)**|Bitmuster der Option zur Schemaerstellung für den angegebenen Artikel. Eine umfassende Liste der **schema_option** Werte finden Sie unter [sp_addarticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md).|  
|**dest_owner**|**sysname**|Name des Besitzers des Zielobjekts.|  
|**source_owner**|**sysname**|Besitzer des Quellobjekts.|  
|**unqua_source_object**|**sysname**|Name des Quellobjekts, ohne den Namen des Besitzers.|  
|**sync_object_owner**|**sysname**|Besitzer der Sicht, die den veröffentlichten Artikel definiert. .|  
|**unqualified_sync_object**|**sysname**|Name der Sicht, die den veröffentlichten Artikel definiert, ohne den Namen des Besitzers.|  
|**filter_owner**|**sysname**|Besitzer des Filters.|  
|**unqua_filter**|**sysname**|Name des Filters, ohne den Namen des Besitzers.|  
|**auto_identity_range**|**int**|Flag, das anzeigt, ob die automatische Behandlung von Identitätsbereichen für die Veröffentlichung bei ihrer Erstellung aktiviert wurde. **1** bedeutet, dass der automatische Identitäts Bereich aktiviert ist. der Wert **0** bedeutet, dass er deaktiviert ist.|  
|**publisher_identity_range**|**int**|Bereichs Größe des Identitäts Bereichs auf dem Verleger, wenn für den Artikel *identityrangemanagementoption* auf **Auto** oder **auto_identity_range** auf **true**festgelegt ist.|  
|**identity_range**|**bigint**|Bereichs Größe des Identitäts Bereichs auf dem Abonnenten, wenn für den Artikel *identityrangemanagementoption* auf **Auto** oder **auto_identity_range** auf **true**festgelegt ist.|  
|**Mindest**|**bigint**|Prozentwert, der anzeigt, wann der Verteilungs-Agent einen neuen Identitätsbereich zuweist.|  
|**identityrangemanagementoption**|**int**|Gibt die für den Artikel behandelte Identitätsbereichsverwaltung an.|  
|**fire_triggers_on_snapshot**|**bit**|Gibt an, ob replizierte Benutzertrigger beim Anwenden der Anfangsmomentaufnahme ausgeführt werden.<br /><br /> **1** = Benutzer Trigger werden ausgeführt.<br /><br /> **0** = Benutzer Trigger werden nicht ausgeführt.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_helparticle** wird bei der Momentaufnahme-und Transaktions Replikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** , der festen Daten Bank Rolle **db_owner** oder der Veröffentlichungs Zugriffsliste für die aktuelle Veröffentlichung können **sp_helparticle**ausführen.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_helptranarticle](../../relational-databases/replication/codesnippet/tsql/sp-helparticle-transact-_1.sql)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen und Ändern von Artikeleigenschaften](../../relational-databases/replication/publish/view-and-modify-article-properties.md)   
 [sp_addarticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_articlecolumn &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sp_changearticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
