---
title: sys. dm_repl_articles (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_repl_articles_TSQL
- dm_repl_articles
- dm_repl_articles_TSQL
- sys.dm_repl_articles
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_repl_articles dynamic management function
ms.assetid: 794d514e-bacd-432e-a8ec-3a063a97a37b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 07dc611371cbff373fb60036c8c16da6656a8de1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68088594"
---
# <a name="sysdm_repl_articles-transact-sql"></a>sys.dm_repl_articles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen zu Datenbankobjekten zurück, die als Artikel in einer Replikationstopologie veröffentlicht sind.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**artcache_db_address**|**varbinary(8)**|Speicherinterne Adresse der zwischengespeicherten Datenbankstruktur für die Veröffentlichungsdatenbank.|  
|**artcache_table_address**|**varbinary(8)**|Speicherinterne Adresse der zwischengespeicherten Tabellenstruktur für den veröffentlichten Tabellenartikel.|  
|**artcache_schema_address**|**varbinary(8)**|Speicherinterne Adresse der zwischengespeicherten Artikelschemastruktur für den veröffentlichten Tabellenartikel.|  
|**artcache_article_address**|**varbinary(8)**|Speicherinterne Adresse der zwischengespeicherten Artikelstruktur für den veröffentlichten Tabellenartikel.|  
|**artid**|**BIGINT**|Identifiziert jeden Eintrag in dieser Tabelle eindeutig.|  
|**artfilter**|**BIGINT**|Die ID der zum horizontalen Filtern des Artikels verwendeten gespeicherten Prozedur.|  
|**artobjid**|**BIGINT**|ID des veröffentlichten Objekts.|  
|**artpubid**|**BIGINT**|ID der Veröffentlichung, zu der der Artikel gehört.|  
|**artstatus**|**tinyint**|Die Bitmaske der Artikeloptionen und der Status, der das Ergebnis der bitweisen logischen OR-Operation von mindestens einem der folgenden Werte sein kann:<br /><br /> **1** = Artikel ist aktiv.<br /><br /> **8** = schließen Sie den Spaltennamen in INSERT-Anweisungen ein.<br /><br /> **16** = parametrisierte Anweisungen verwenden.<br /><br /> **24** = beide enthalten den Spaltennamen in INSERT-Anweisungen und verwenden parametrisierte Anweisungen.<br /><br /> Ein aktiver Artikel, der parametrisierte Anweisungen verwendet, würde in dieser Spalte beispielsweise den Wert 17 anzeigen. Der Wert 0 gibt an, dass der Artikel inaktiv ist und keine zusätzlichen Eigenschaften definiert wurden.|  
|**arttype**|**tinyint**|Artikeltyp:<br /><br /> **1** = Protokoll basierter Artikel.<br /><br /> **3** = Protokoll basierter Artikel mit manuellem Filter.<br /><br /> **5** = Protokoll basierter Artikel mit manueller Sicht.<br /><br /> **7** = Protokoll basierter Artikel mit manuellem Filter und manueller Ansicht.<br /><br /> **8** = Ausführung gespeicherter Prozeduren.<br /><br /> **24** = serialisierbare Ausführung gespeicherter Prozeduren.<br /><br /> **32** = gespeicherte Prozedur (nur Schema).<br /><br /> **64** = Ansicht (nur Schema).<br /><br /> **128** = Funktion (nur Schema).|  
|**wszArtdesttable**|**nvarchar (514)**|Name des veröffentlichten Objekts am Ziel.|  
|**wszArtdesttableowner**|**nvarchar (514)**|Besitzer des veröffentlichten Objekts am Ziel.|  
|**wszArtinscmd**|**nvarchar (510)**|Befehl oder gespeicherte Prozedur, der bzw. die für Einfügungen verwendet wird.|  
|**cmdTypeIns**|**int**|Aufrufsyntax für die gespeicherte Prozedur zur Einfügung. Folgende Werte sind möglich.<br /><br /> **1** = aufzurufen<br /><br /> **2** = SQL<br /><br /> **3** = keine<br /><br /> **7** = unbekannt|  
|**wszArtdelcmd**|**nvarchar (510)**|Befehl oder gespeicherte Prozedur, der bzw. die für Löschungen verwendet wird.|  
|**cmdTypeDel**|**int**|Aufrufsyntax für die gespeicherte Prozedur zur Löschung. Folgende Werte sind möglich.<br /><br /> **0** = XCALL<br /><br /> **1** = aufzurufen<br /><br /> **2** = SQL<br /><br /> **3** = keine<br /><br /> **7** = unbekannt|  
|**wszArtupdcmd**|**nvarchar (510)**|Befehl oder gespeicherte Prozedur, der bzw. die für Updates verwendet wird.|  
|**cmdTypeUpd**|**int**|Aufrufsyntax für die gespeicherte Updateprozedur. Folgende Werte sind möglich.<br /><br /> **0** = XCALL<br /><br /> **1** = aufzurufen<br /><br /> **2** = SQL<br /><br /> **3** = keine<br /><br /> **4** = mcallcenter<br /><br /> **5** = VCALL<br /><br /> **6** = SCALL<br /><br /> **7** = unbekannt|  
|**wszArtpartialupdcmd**|**nvarchar (510)**|Befehl oder gespeicherte Prozedur, der bzw. die für Teilupdates verwendet wird.|  
|**cmdTypePartialUpd**|**int**|Aufrufsyntax für die gespeicherte Teilupdateprozedur. Folgende Werte sind möglich.<br /><br /> **2** = SQL|  
|**numcol**|**int**|Anzahl von Spalten in der Partition für einen vertikal gefilterten Artikel.|  
|**artcmdtype**|**tinyint**|Typ von Befehl, der zurzeit repliziert wird. Folgende Werte sind möglich.<br /><br /> **1** = einfügen<br /><br /> **2** = löschen<br /><br /> **3** = Update<br /><br /> **4** = UPDATETEXT<br /><br /> **5** = keine<br /><br /> **6** = nur interner Gebrauch<br /><br /> **7** = nur interne Verwendung<br /><br /> **8** = partielles Update|  
|**artgeninscmd**|**nvarchar (510)**|INSERT-Befehlsvorlage basierend auf den im Artikel enthaltenen Spalten.|  
|**artgendelcmd**|**nvarchar (510)**|DELETE-Befehlsvorlage, die abhängig von der verwendeten Aufrufsyntax den Primärschlüssel oder die im Artikel enthaltenen Spalten enthalten kann.|  
|**artgenupdcmd**|**nvarchar (510)**|UPDATE-Befehlsvorlage, die abhängig von der verwendeten Aufrufsyntax den Primärschlüssel, aktualisierte Spalten oder eine vollständige Spaltenliste enthalten kann.|  
|**artpartialupdcmd**|**nvarchar (510)**|Befehlsvorlage für ein Teilupdate, die den Primärschlüssel und aktualisierte Spalten enthält.|  
|**artupdtxtcmd**|**nvarchar (510)**|UPDATETEXT-Befehlsvorlage, die den Primärschlüssel und aktualisierte Spalten enthält.|  
|**artgenins2cmd**|**nvarchar (510)**|INSERT-Befehlsvorlage, die beim Abgleichen eines Artikels während der gleichzeitigen Momentaufnahmeverarbeitung verwendet wird.|  
|**artgendel2cmd**|**nvarchar (510)**|DELETE-Befehlsvorlage, die beim Abgleichen eines Artikels während der gleichzeitigen Momentaufnahmeverarbeitung verwendet wird.|  
|**fInReconcile**|**tinyint**|Gibt an, ob ein Artikel zurzeit während der gleichzeitigen Momentaufnahmeverarbeitung abgeglichen wird.|  
|**fPubAllowUpdate**|**tinyint**|Zeigt an, ob die Veröffentlichung Updates des Abonnements zulässt.|  
|**intPublicationOptions**|**BIGINT**|Bitmuster, mit dem zusätzliche Veröffentlichungsoptionen angegeben werden, mit den folgenden bitweisen Optionswerten:<br /><br /> **0x1** : für die Peer-zu-Peer-Replikation aktiviert.<br /><br /> **0x2** -nur lokale Änderungen veröffentlichen.<br /><br /> **0x4** -aktiviert für nicht-SQL Server-Abonnenten.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW DATABASE STATE-Berechtigung für die Veröffentlichungs Datenbank, um **dm_repl_articles**aufzurufen.  
  
## <a name="remarks"></a>Bemerkungen  
 Informationen werden nur für replizierte Datenbankobjekte zurückgegeben, die zurzeit in den Replikationsartikelcache geladen sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungs Sichten im Zusammenhang mit der Replikation &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/replication-related-dynamic-management-views-transact-sql.md)  
  
  

