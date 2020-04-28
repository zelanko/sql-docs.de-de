---
title: sysmergepartitioninfoview (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysmergepartitioninfoview
- sysmergepartitioninfoview_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmergepartitioninfoview view
ms.assetid: 714e2935-1bc7-4901-aea2-64b1bbda03d6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 40b1ebc5319c13b5aa84a28e1a5c5546dd62bd03
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68094832"
---
# <a name="sysmergepartitioninfoview-transact-sql"></a>sysmergepartitioninfoview (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **sysmergepartitioninfoview** -Sicht macht Partitionierungs Informationen für Tabellen Artikel verfügbar. Diese Sicht wird in der Veröffentlichungsdatenbank auf dem Verleger und in der Abonnementdatenbank auf dem Abonnenten gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Der Name des Artikels.|  
|**type**|**tinyint**|Gibt den Artikeltyp an, der einen der folgenden Werte aufweisen kann:<br /><br /> **0x0A** = Tabelle.<br /><br /> **0x20** = nur Prozedur Schema.<br /><br /> **0x40** = nur Schema anzeigen oder indiziertes Sicht Schema.<br /><br /> **0x80** = nur Funktions Schema.|  
|**objid**|**int**|Der Bezeichner für das veröffentlichte Objekt.|  
|**sync_objid**|**int**|Die Objekt-ID der Sicht, die das synchronisierte Dataset darstellt.|  
|**view_type**|**tinyint**|Der Typ der Sicht:<br /><br /> **0** = keine Ansicht; Verwenden Sie das gesamte Basisobjekt.<br /><br /> **1** = permanente Ansicht.<br /><br /> **2** = temporäre Ansicht.|  
|**artid**|**uniqueidentifier**|Die eindeutige ID des angegebenen Artikels.|  
|**Beschreibung**|**nvarchar(255)**|Eine kurze Beschreibung des Artikels.|  
|**pre_creation_command**|**tinyint**|Die Standardaktion, die durchgeführt wird, wenn der Artikel in der Abonnementdatenbank erstellt wird:<br /><br /> **0** = None: Wenn die Tabelle bereits auf dem Abonnenten vorhanden ist, wird keine Aktion ausgeführt.<br /><br /> **1** = Drop-löscht die Tabelle, bevor Sie neu erstellt wird.<br /><br /> **2** = DELETE: gibt einen Löschvorgang basierend auf der WHERE-Klausel im Teilmengen Filter aus.<br /><br /> **3** = Abschneiden-identisch mit 2, löscht jedoch Seiten anstelle von Zeilen. Eine WHERE-Klausel wird jedoch nicht verwendet.|  
|**pubid**|**uniqueidentifier**|Die ID der Veröffentlichung, zu der der aktuelle Artikel gehört.|  
|**Namen**|**int**|Die Spitznamenzuordnung zur Identifikation des Artikels.|  
|**column_tracking**|**int**|Gibt an, ob die Spaltennachverfolgung für den Artikel implementiert wurde.|  
|**status**|**tinyint**|Zeigt den Status des Artikels an. Die folgenden Werte sind möglich:<br /><br /> **1** = nicht synchronisiert: das Anfangs Verarbeitungs Skript zum Veröffentlichen der Tabelle wird bei der nächsten Ausführung des Momentaufnahmen-Agent ausgeführt.<br /><br /> **2** = aktiv: das Anfangs Verarbeitungs Skript zum Veröffentlichen der Tabelle wurde ausgeführt.|  
|**conflict_table**|**sysname**|Der Name der lokalen Tabelle, die die Konflikt verursachenden Datensätze für den aktuellen Artikel enthält. Diese Tabelle dient nur zu Informationszwecken; ihr Inhalt kann mit benutzerdefinierten Konfliktlösungsroutinen oder direkt vom Administrator geändert oder gelöscht werden.|  
|**creation_script**|**nvarchar(255)**|Das Erstellungsskript für diesen Artikel.|  
|**conflict_script**|**nvarchar(255)**|Das Konfliktskript für diesen Artikel.|  
|**article_resolver**|**nvarchar(255)**|Der Konfliktlöser für diesen Artikel.|  
|**ins_conflict_proc**|**sysname**|Die Prozedur, die zum Schreiben von Konfliktinformationen in die Konflikttabelle verwendet wird.|  
|**insert_proc**|**sysname**|Die Prozedur, die zum Einfügen von Zeilen während der Synchronisierung verwendet wird.|  
|**update_proc**|**sysname**|Die Prozedur, die zum Aktualisieren von Zeilen während der Synchronisierung verwendet wird.|  
|**select_proc**|**sysname**|Der Name einer automatisch generierten gespeicherten Prozedur, die der Merge-Agent verwendet, um Sperren einzurichten, und zum Suchen von Spalten und Zeilen für einen Artikel.|  
|**metadata_select_proc**|**sysname**|Der Name einer automatisch generierten gespeicherten Prozedur, mit der auf Metadaten in den Systemtabellen für die Mergereplikation zugegriffen wird.|  
|**delete_proc**|**sysname**|Die Prozedur, die zum Löschen von Zeilen während der Synchronisierung verwendet wird.|  
|**schema_option**|**Binär (8)**|Das Bitmuster der Option zur Schemagenerierung für den angegebenen Artikel. Weitere Informationen zu unterstützten *schema_option* Werten finden Sie unter [sp_addmergearticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md).|  
|**destination_object**|**sysname**|Der Name der auf dem Abonnenten erstellten Tabelle.|  
|**destination_owner**|**sysname**|Der Name des Besitzers des Zielobjekts.|  
|**resolver_clsid**|**nvarchar(50)**|Die ID des benutzerdefinierten Konfliktlösers. Für einen Geschäftslogikhandler ist dieser Wert NULL.|  
|**subset_filterclause**|**nvarchar (1000)**|Die Filterklausel für diesen Artikel.|  
|**missing_col_count**|**int**|Die Anzahl veröffentlichter Spalten, die im Artikel fehlen.|  
|**missing_cols**|**varbinary(128)**|Das Bitmuster, das die Spalten beschreibt, die im Artikel fehlen.|  
|**excluded_cols**|**varbinary(128)**|Das Bitmuster der Spalten, die vom Artikel ausgeschlossen sind.|  
|**excluded_col_count**|**int**|Die Anzahl von Spalten, die aus dem Artikel ausgeschlossen sind.|  
|**Spalten**|**varbinary(128)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**deleted_cols**|**varbinary(128)**|Das Bitmuster, das die Spalten beschreibt, die im Artikel gelöscht wurden.|  
|**resolver_info**|**nvarchar(255)**|Der Speicherplatz für zusätzliche vom benutzerdefinierten Konfliktlöser benötigte Informationen.|  
|**view_sel_proc**|**nvarchar (290)**|Der Name einer gespeicherten Prozedur, die der Merge-Agent zum ersten Auffüllen eines Artikels in einer dynamisch gefilterten Veröffentlichung und zum Aufzählen von geänderten Zeilen in einer beliebigen gefilterten Veröffentlichung verwendet.|  
|**gen_cur**|**bigint**|Generiert eine Nummer für lokale Änderungen an der Basistabelle eines Artikels.|  
|**vertical_partition**|**int**|Gibt an, ob die Spaltenfilterung für einen Tabellenartikel aktiviert ist. **0** gibt an, dass keine vertikale Filterung vorhanden ist und alle Spalten veröffentlicht werden.|  
|**identity_support**|**int**|Gibt an, ob die automatische Verarbeitung der Identitätsbereiche aktiviert ist. **1** bedeutet, dass die Identitäts Bereichs Behandlung aktiviert ist, und **0** bedeutet, dass keine Identitäts Bereichs Unterstützung vorhanden ist.|  
|**before_image_objid**|**int**|Die Objekt-ID der Nachverfolgungstabelle. Die Nachverfolgungstabelle enthält bestimmte Schlüsselspaltenwerte, wenn Partitionsänderungsoptimierungen für die Veröffentlichung aktiviert wurden.|  
|**before_view_objid**|**int**|Die Objekt-ID einer Sichttabelle. Die Sicht ist für eine Tabelle festgelegt, die überwacht, ob eine Zeile zu einem bestimmten Abonnenten gehört hat, bevor sie gelöscht oder aktualisiert wurde. Dies trifft nur zu, wenn Partitionsänderungsoptimierungen für die Veröffentlichung aktiviert wurden.|  
|**verify_resolver_signature**|**int**|Gibt an, ob eine digitale Signatur überprüft wird, bevor ein Konfliktlöser in einer Mergereplikation verwendet wird:<br /><br /> **0** = Signatur wird nicht überprüft.<br /><br /> **1** = Signatur wird überprüft, um festzustellen, ob Sie von einer vertrauenswürdigen Quelle ist.|  
|**allow_interactive_resolver**|**bit**|Gibt an, ob die Verwendung des interaktiven Konfliktlösers für einen Artikel aktiviert ist. **1** bedeutet, dass der interaktive Konflikt Löser für den Artikel verwendet werden kann.|  
|**fast_multicol_updateproc**|**bit**|Gibt an, ob der Merge-Agent aktiviert wurde, um in einer UPDATE-Anweisung Änderungen auf mehrere Spalten in derselben Zeile anzuwenden.<br /><br /> **0** = gibt ein separates Update für jede geänderte Spalte aus.<br /><br /> **1** = wird bei der Update-Anweisung ausgegeben, wodurch Aktualisierungen in mehreren Spalten in einer Anweisung auftreten.|  
|**check_permissions**|**int**|Die Bitmap der Berechtigungen auf Tabellenebene, die überprüft werden, wenn der Merge-Agent Änderungen auf den Verleger anwendet. *check_permissions* kann einen der folgenden Werte aufweisen:<br /><br /> **0x00** = Berechtigungen werden nicht geprüft.<br /><br /> **0x10** = überprüft Berechtigungen auf dem Verleger, bevor Einfügungen auf einem Abonnenten hochgeladen werden können.<br /><br /> **0x20** = überprüft Berechtigungen auf dem Verleger, bevor auf einem Abonnenten vorgenommene Aktualisierungen hochgeladen werden können.<br /><br /> **0x40** = überprüft Berechtigungen auf dem Verleger, bevor auf einem Abonnenten ausgeführte Löschvorgänge hochgeladen werden können.|  
|**maxversion_at_cleanup**|**int**|Die maximale Generierung, für die bei der nächsten Ausführung des Merge-Agents ein Cleanup ausgeführt wird.|  
|**processing_order**|**int**|Gibt die Verarbeitungsreihenfolge von Artikeln in einer Mergeveröffentlichung an. der Wert **0** gibt an, dass der Artikel nicht sortiert ist, und die Artikel werden in der Reihenfolge vom niedrigsten zum höchsten Wert verarbeitet. Wenn zwei Artikel denselben Wert haben, werden sie gleichzeitig verarbeitet. Weitere Informationen finden Sie unter [Specify Merge Replication properties (Angeben von Mergereplikationseigenschaften)](../../relational-databases/replication/merge/specify-merge-replication-properties.md).|  
|**upload_options**|**tinyint**|Definiert, ob Änderungen auf dem Abonnenten vorgenommen oder von diesem hochgeladen werden können. Die folgenden Werte sind möglich.<br /><br /> **0** = es gibt keine Einschränkungen für Updates, die auf dem Abonnenten vorgenommen wurden. Alle Änderungen werden auf den Verleger hochgeladen.<br /><br /> **1** = Änderungen sind auf dem Abonnenten zulässig, werden jedoch nicht auf den Verleger hochgeladen.<br /><br /> **2** = Änderungen sind auf dem Abonnenten nicht zulässig.|  
|**published_in_tran_pub**|**bit**|Gibt an, dass ein Artikel in einer Mergeveröffentlichung auch in einer Transaktionsveröffentlichung veröffentlicht wird.<br /><br /> **0** = der Artikel wird nicht in einem transaktionalen Artikel veröffentlicht.<br /><br /> **1** = der Artikel wird auch in einem transaktionalen Artikel veröffentlicht.|  
|**Gewicht**|**bit**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**procname_postfix**|**NCHAR (32)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**well_partitioned_lightweight**|**bit**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**before_upd_view_objid**|**int**|Die ID der Tabellensicht vor Updates.|  
|**delete_tracking**|**bit**|Zeigt an, ob Löschvorgänge repliziert werden.<br /><br /> **0** = Löschvorgänge werden nicht repliziert.<br /><br /> **1** = Löschvorgänge werden repliziert. Dies ist das Standardverhalten für die Mergereplikation.<br /><br /> Wenn der Wert von *delete_tracking* **0**ist, müssen auf dem Abonnenten gelöschte Zeilen manuell auf dem Verleger entfernt werden, und auf dem Verleger gelöschte Zeilen müssen manuell auf dem Abonnenten entfernt werden.<br /><br /> Hinweis: der Wert **0** führt zu einer nicht Konvergenz.|  
|**compensate_for_errors**|**bit**|Zeigt an, ob kompensierende Aktionen ausgeführt werden, wenn während der Synchronisierung Fehler auftreten.<br /><br /> **0** = kompensierende Aktionen sind deaktiviert.<br /><br /> **1** = Änderungen, die nicht auf einem Abonnenten oder Verleger angewendet werden können, führen immer zu kompensierenden Aktionen, um diese Änderungen rückgängig zu machen. Dies ist das Standardverhalten der Mergereplikation.<br /><br /> Hinweis: der Wert **0** führt zu einer nicht Konvergenz.|  
|**pub_range**|**bigint**|Die Größe des Identitätsbereichs für den Verleger.|  
|**range**|**bigint**|Die Bereichsgröße der aufeinander folgenden Identitätswerte, die Abonnenten bei einer Anpassung zugewiesen würden.|  
|**Mindest**|**int**|Als Prozentsatz angegebener Schwellenwert für den Identitätsbereich.|  
|**stream_blob_columns**|**bit**|Gibt an, ob die Datenstromoptimierung für BLOB-Spalten (Binary Large Object) verwendet wird. der Wert **1** bedeutet, dass die Optimierung versucht wird.|  
|**preserve_rowguidcol**|**bit**|Zeigt an, ob die Replikation eine vorhandene rowguid-Spalte verwendet. Der Wert **1** bedeutet, dass eine vorhandene ROWGUIDCOL-Spalte verwendet wird. **0** bedeutet, dass die Replikation die ROWGUIDCOL-Spalte hinzugefügt hat.|  
|**partition_view_id**|**int**|Identifiziert die Sicht, die eine Abonnentenpartition definiert.|  
|**repl_view_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**partition_deleted_view_rule**|**sysname**|Die Anweisung, mit der in einem Mergereplikationstrigger die Partitions-ID für jede gelöschte oder aktualisierte Zeile basierend auf den alten Spaltenwerten abgerufen wird.|  
|**partition_inserted_view_rule**|**Vom Datentyp sysname**|Die Anweisung, mit der in einem Mergereplikationstrigger die Partitions-ID für jede eingefügte oder aktualisierte Zeile basierend auf den neuen Spaltenwerten abgerufen wird.|  
|**membership_eval_proc_name**|**sysname**|Der Name der Prozedur, die die aktuellen Partitions-IDs von Zeilen in [MSmerge_contents &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/msmerge-contents-transact-sql.md)auswertet.|  
|**column_list**|**sysname**|Eine durch Trennzeichen getrennte Liste mit in einem Artikel veröffentlichten Spalten.|  
|**column_list_blob**|**sysname**|Eine durch Trennzeichen getrennte Liste mit in einem Artikel veröffentlichten Spalten, einschließlich BLOB-Spalten (Binary Large Object).|  
|**expand_proc**|**sysname**|Der Name der Prozedur, die Partitions-IDs für alle untergeordneten Zeilen einer neu eingefügten übergeordneten Zeile und für übergeordnete Zeilen, die einer Partitions Änderung unterzogen wurden oder gelöscht wurden, neu bewertet.|  
|**logical_record_parent_nickname**|**int**|Der Spitzname des übergeordneten Elements der obersten Ebene eines Artikels in einem logischen Datensatz.|  
|**logical_record_view**|**int**|Eine Sicht, die den rowguid-Wert des übergeordneten Artikels der obersten Ebene ausgibt, der jedem untergeordneten rowguid-Wert entspricht.|  
|**logical_record_deleted_view_rule**|**sysname**|Vergleichbar mit **logical_record_view**, mit dem Unterschied, dass in Update-und DELETE-Triggern untergeordnete Zeilen in der Tabelle "Deleted" angezeigt werden.|  
|**logical_record_level_conflict_detection**|**bit**|Gibt an, ob Konflikte auf der logischen Datensatzebene oder auf der Zeilen- oder Spaltenebene erkannt werden sollen.<br /><br /> **0** = Konflikterkennung auf Zeilen-oder Spaltenebene wird verwendet.<br /><br /> **1** = die Konflikterkennung logischer Datensätze wird verwendet, wobei eine Änderung in einer Zeile auf dem Verleger und eine Änderung in einer separaten Zeile denselben logischen Datensatz auf dem Abonnenten als Konflikt behandelt.<br /><br /> Mit dem Wert 1 kann nur die Konfliktauflösung auf der logischen Datensatzebene verwendet werden.|  
|**logical_record_level_conflict_resolution**|**bit**|Gibt an, ob Konflikte auf der logischen Datensatzebene oder auf Zeilen-oder Spaltenebene aufgelöst werden sollen.<br /><br /> **0** = Auflösung auf Zeilen-oder Spaltenebene wird verwendet.<br /><br /> **1** = bei einem Konflikt überschreibt der gesamte logische Datensatz aus dem Gewinner den gesamten logischen Datensatz auf der Verliererseite.<br /><br /> Der Wert 1 kann für die Erkennung auf der logischen Datensatzebene und für die Erkennung auf Zeilen- oder Spaltenebene verwendet werden.|  
|**partition_options**|**tinyint**|Definiert die Art und Weise, wie Daten im Artikel partitioniert werden. Dies ermöglicht Leistungsoptimierungen, wenn alle Zeilen nur zu einer einzigen Partition oder zu einem einzigen Abonnement gehören. Der *partition_options* kann einen der folgenden Werte aufweisen.<br /><br /> **0** = das Filtern für den Artikel ist entweder statisch oder ergibt keine eindeutige Teilmenge von Daten für jede Partition, d. h. eine "überlappende" Partition.<br /><br /> **1** = die Partitionen überlappen sich, und auf dem Abonnenten vorgenommene DML-Updates können nicht die Partition ändern, zu der eine Zeile gehört.<br /><br /> **2** = das Filtern für den Artikel ergibt nicht überlappende Partitionen, mehrere Abonnenten können jedoch die gleiche Partition erhalten.<br /><br /> **3** = das Filtern für den Artikel ergibt nicht überlappende Partitionen, die für jedes Abonnement eindeutig sind.|  
|**name**|**sysname**|Der Name einer Partition.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Partitionen für eine Mergeveröffentlichung mit parametrisierten Filtern](../../relational-databases/replication/publish/manage-partitions-for-a-merge-publication-with-parameterized-filters.md)   
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikations Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_addmergepartition &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql.md)   
 [sp_helpmergepartition &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepartition-transact-sql.md)  
  
  
