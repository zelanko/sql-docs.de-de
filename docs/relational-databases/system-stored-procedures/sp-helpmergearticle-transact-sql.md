---
description: sp_helpmergearticle (Transact-SQL)
title: sp_helpmergearticle (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergearticle
- sp_helpmergearticle_TSQL
helpviewer_keywords:
- sp_helpmergearticle
ms.assetid: 0fb9986a-3c33-46ef-87bb-297396ea5a6a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ec07e77bcc2dbf3c0503e348b509848880705424
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88485963"
---
# <a name="sp_helpmergearticle-transact-sql"></a>sp_helpmergearticle (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt Informationen zu einem Artikel zurück. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank oder auf dem Wiederveröffentlichungsabonnenten für die Abonnementdatenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpmergearticle [ [ @publication = ] 'publication' ]  
    [ , [ @article= ] 'article' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Der Name der Veröffentlichung, für die Informationen abgerufen werden sollen. *Publication*ist vom **Datentyp vom Datentyp sysname**und **%** hat den Standardwert, der Informationen zu allen Mergeartikeln zurückgibt, die in allen Veröffentlichungen in der aktuellen Datenbank enthalten sind.  
  
`[ @article = ] 'article'` Der Name des Artikels, für den Informationen zurückgegeben werden sollen. der *Artikel*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert **%** , mit dem Informationen zu allen Mergeartikeln in der angegebenen Veröffentlichung zurückgegeben werden.  
  
## <a name="result-set"></a>Resultset  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Artikelbezeichner|  
|**name**|**sysname**|Der Name des Artikels.|  
|**source_owner**|**sysname**|Name des Besitzers des Quellobjekts|  
|**source_object**|**sysname**|Name des Quellobjekts, aus dem der Artikel hinzugefügt werden soll|  
|**sync_object_owner**|**sysname**|Name des Besitzers der Sicht, die den veröffentlichten Artikel definiert|  
|**sync_object**|**sysname**|Name des benutzerdefinierten Objekts, mit dem die Anfangsdaten für die Partition eingerichtet werden|  
|**Beschreibung**|**nvarchar(255)**|Beschreibung des Artikels|  
|**status**|**tinyint**|Status des Artikels. Die folgenden Werte sind möglich:<br /><br /> **1** = inaktiv<br /><br /> **2** = aktiv<br /><br /> **5** = DDL-Vorgang (Data Definition Language) steht aus.<br /><br /> **6** = DDL-Vorgang mit einer neu generierten Momentaufnahme<br /><br /> Hinweis: Wenn ein Artikel erneut initialisiert wird, werden die Werte **5** und **6** in **2**geändert.|  
|**creation_script**|**nvarchar(255)**|Pfad und Name eines optionalen Artikelschemaskripts, mit dem der Artikel in der Abonnementdatenbank erstellt wurde|  
|**conflict_table**|**nvarchar (270)**|Name der Tabelle, in der die Einfüge- oder Updatekonflikte gespeichert werden.|  
|**article_resolver**|**nvarchar(255)**|Benutzerdefinierter Konfliktlöser für den Artikel|  
|**subset_filterclause**|**nvarchar (1000)**|WHERE-Klausel für das horizontale Filtern.|  
|**pre_creation_command**|**tinyint**|Methode zur Voraberstellung. Die folgenden Werte sind möglich:<br /><br /> **0** = keine<br /><br /> **1** = löschen<br /><br /> **2** = löschen<br /><br /> **3** = Abschneiden|  
|**schema_option**|**Binär (8)**|Bitmuster der Option zur Schemaerstellung für den Artikel. Weitere Informationen zu dieser Bitmap-Option finden Sie unter [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) oder [sp_changemergearticle](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md).|  
|**type**|**smallint**|Artikeltyp. Die folgenden Werte sind möglich:<br /><br /> **10** = Tabelle<br /><br /> **32** = gespeicherte Prozedur<br /><br /> **64** = Sicht oder indizierte Sicht<br /><br /> **128** = benutzerdefinierte Funktion<br /><br /> **160** = nur Synonym Schema|  
|**column_tracking**|**int**|Einstellung für die Nachverfolgung auf Spaltenebene; Dabei bedeutet **1** , dass die Nachverfolgung auf Spaltenebene auf ON fest steht, und **0** bedeutet, dass die Nachverfolgung auf Spaltenebene deaktiviert ist.|  
|**resolver_info**|**nvarchar(255)**|Name des Artikelkonfliktlösers|  
|**vertical_partition**|**bit**|, Wenn der Artikel vertikal partitioniert ist. wobei **1** bedeutet, dass der Artikel vertikal partitioniert ist, und **0** bedeutet, dass dies nicht der Fall ist.|  
|**destination_owner**|**sysname**|Besitzer des Zielobjekts. Nur anwendbar beim Zusammenführen von gespeicherten Prozeduren, Sichten und Schemaartikeln benutzerdefinierter Funktionen (UDF, User-Defined Function).|  
|**identity_support**|**int**|, Wenn die automatische Handhabung von Identitäts Bereichen aktiviert ist. Dabei ist **1** aktiviert, und **0** ist deaktiviert.|  
|**pub_identity_range**|**bigint**|Die beim Zuweisen neuer Identitätswerte zu verwendende Bereichsgröße. Weitere Informationen finden Sie im Abschnitt "Mergereplikation" unter [Replizieren von Identitäts Spalten](../../relational-databases/replication/publish/replicate-identity-columns.md).|  
|**identity_range**|**bigint**|Die beim Zuweisen neuer Identitätswerte zu verwendende Bereichsgröße. Weitere Informationen finden Sie im Abschnitt "Mergereplikation" unter [Replizieren von Identitäts Spalten](../../relational-databases/replication/publish/replicate-identity-columns.md).|  
|**threshold**|**int**|Prozentwert, der für Abonnenten verwendet wird, die [!INCLUDE[ssEW](../../includes/ssew-md.md)] oder frühere Versionen von ausführen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . **Schwellenwert** steuert, wenn der Merge-Agent einen neuen Identitäts Bereich zuweist. Wenn der im Schwellenwert angegebene Prozentsatz verwendet wird, erstellt der Merge-Agent einen neuen Identitätsbereich. Weitere Informationen finden Sie im Abschnitt "Mergereplikation" unter [Replizieren von Identitäts Spalten](../../relational-databases/replication/publish/replicate-identity-columns.md).|  
|**verify_resolver_signature**|**int**|Wenn eine digitale Signatur überprüft wird, bevor ein Konflikt Löser bei der Mergereplikation verwendet wird. Dabei bedeutet **0** , dass die Signatur nicht überprüft wird, und **1** bedeutet, dass die Signatur überprüft wird, um festzustellen, ob Sie aus einer vertrauenswürdigen Quelle ist.|  
|**destination_object**|**sysname**|Name des Zielobjekts. Nur anwendbar beim Zusammenführen gespeicherter Prozeduren, Sichten und UDF-Schemaartikel.|  
|**allow_interactive_resolver**|**int**|, Wenn der interaktive Konflikt Löser für einen Artikel verwendet wird. Dabei bedeutet **1** , dass dieser Konflikt Löser verwendet wird, und **0** bedeutet, dass er nicht verwendet wird.|  
|**fast_multicol_updateproc**|**int**|Aktiviert oder deaktiviert die Merge-Agent, um Änderungen auf mehrere Spalten in derselben Zeile in einer Update-Anweisung anzuwenden. wobei **1** bedeutet, dass mehrere Spalten in einer Anweisung aktualisiert werden, und **0** bedeutet, dass separate UPDATE-Anweisungen für jede aktualisierte Spalte Probleme sind.|  
|**check_permissions**|**int**|Ein Wert für eine ganze Zahl, der das Bitmuster der überprüften Berechtigungen auf Tabellenebene darstellt. Eine Liste möglicher Werte finden Sie unter [sp_addmergearticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md).|  
|**processing_order**|**int**|Die Reihenfolge, in der Datenänderungen auf Artikel in einer Veröffentlichung angewendet werden.|  
|**upload_options**|**tinyint**|Definiert Einschränkungen für Updates, die auf einem Abonnenten mit Clientabonnement vorgenommen wurden. Dabei sind folgende Werte möglich.<br /><br /> **0** = es gibt keine Einschränkungen für Updates, die auf einem Abonnenten mit einem Client Abonnement vorgenommen wurden. Alle Änderungen werden auf den Verleger hochgeladen.<br /><br /> **1** = Änderungen sind auf einem Abonnenten mit einem Client Abonnement zulässig, werden jedoch nicht auf den Verleger hochgeladen.<br /><br /> **2** = Änderungen sind auf einem Abonnenten mit einem Client Abonnement nicht zulässig.<br /><br /> Weitere Informationen finden Sie unter [Optimieren der Leistung der Mergereplikation durch nur herunterladbare Artikel](../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md).|  
|**identityrangemanagementoption**|**int**|, Wenn die automatische Handhabung von Identitäts Bereichen aktiviert ist. Dabei ist **1** aktiviert, und **0** ist deaktiviert.|  
|**delete_tracking**|**bit**|, Wenn Löschungen repliziert werden. Dabei bedeutet **1** , dass Löschvorgänge repliziert werden, und **0** bedeutet, dass Sie nicht gelöscht werden.|  
|**compensate_for_errors**|**bit**|Gibt an, ob kompensierende Aktionen ausgeführt werden, wenn während der Synchronisierung Fehler auftreten. Dabei gibt **1** an, dass kompensierende Aktionen ausgeführt werden, und **0** bedeutet, dass keine kompensierenden Aktionen durchgeführt werden.|  
|**partition_options**|**tinyint**|Definiert die Art und Weise, wie Daten im Artikel partitioniert werden. Dies ermöglicht Leistungsoptimierungen, wenn alle Zeilen nur zu einer einzigen Partition oder zu einem einzigen Abonnement gehören. *partition_options* kann einen der folgenden Werte aufweisen.<br /><br /> **0** = das Filtern für den Artikel ist entweder statisch oder ergibt keine eindeutige Teilmenge von Daten für jede Partition. Das heißt, es handelt sich um eine "überlappende" Partition.<br /><br /> **1** = die Partitionen überlappen sich, und die auf dem Abonnenten vorgenommenen Updates der Daten Bearbeitungs Sprache (Data Manipulation Language, DML) können nicht die Partition ändern, zu der eine Zeile gehört.<br /><br /> **2** = das Filtern für den Artikel ergibt nicht überlappende Partitionen, mehrere Abonnenten können jedoch die gleiche Partition erhalten.<br /><br /> **3** = das Filtern für den Artikel ergibt nicht überlappende Partitionen, die für jedes Abonnement eindeutig sind.|  
|**artid**|**uniqueidentifier**|Ein Bezeichner, der den Artikel eindeutig identifiziert|  
|**pubid**|**uniqueidentifier**|Ein Bezeichner, der die Veröffentlichung, in der der Artikel veröffentlicht wird, eindeutig identifiziert|  
|**stream_blob_columns**|**bit**|Gibt an, ob die Datenstromoptimierung beim Replizieren von BLOB-Spalten (Binary Large Object) verwendet wird. **1** bedeutet, dass die Optimierung verwendet wird, und **0** bedeutet, dass die Optimierung nicht verwendet wird.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_helpmergearticle** wird bei der Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Daten Bank Rolle **db_owner** in der Veröffentlichungs Datenbank, der **replmonitor** -Rolle in der Verteilungs Datenbank oder der Veröffentlichungs Zugriffsliste für eine Veröffentlichung können **sp_helpmergearticle**ausführen.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_helpmergearticle](../../relational-databases/replication/codesnippet/tsql/sp-helpmergearticle-tran_1.sql)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen und Ändern von Artikeleigenschaften](../../relational-databases/replication/publish/view-and-modify-article-properties.md)   
 [sp_addmergearticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)   
 [sp_changemergearticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)   
 [sp_dropmergearticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
