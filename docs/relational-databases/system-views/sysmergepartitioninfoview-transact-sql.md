---
title: Sysmergepartitioninfoview (Transact-SQL) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68094832"
---
# <a name="sysmergepartitioninfoview-transact-sql"></a>sysmergepartitioninfoview (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **Sysmergepartitioninfoview** -Sicht macht Partitionierungsinformationen für Tabellenartikel verfügbar. Diese Sicht wird in der Veröffentlichungsdatenbank auf dem Verleger und in der Abonnementdatenbank auf dem Abonnenten gespeichert.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Der Name des Artikels.|  
|**type**|**tinyint**|Gibt den Artikeltyp an, der einen der folgenden Werte aufweisen kann:<br /><br /> **0x0A** = Tabelle.<br /><br /> **0 x 20** = nur prozedurschema.<br /><br /> **0 x 40** = nur sichtschema oder nur indizierte sichtschema.<br /><br /> **0 x 80** = nur funktionsschema.|  
|**objid**|**int**|Der Bezeichner für das veröffentlichte Objekt.|  
|**sync_objid**|**int**|Die Objekt-ID der Sicht, die das synchronisierte Dataset darstellt.|  
|**view_type**|**tinyint**|Der Typ der Sicht:<br /><br /> **0** = keine Sicht; Verwendung des gesamten des Basisobjekts.<br /><br /> **1** = permanente Sicht.<br /><br /> **2** = temporäre Sicht.|  
|**artid**|**uniqueidentifier**|Die eindeutige ID des angegebenen Artikels.|  
|**description**|**nvarchar(255)**|Eine kurze Beschreibung des Artikels.|  
|**pre_creation_command**|**tinyint**|Die Standardaktion, die durchgeführt wird, wenn der Artikel in der Abonnementdatenbank erstellt wird:<br /><br /> **0** = keine - Wenn die Tabelle bereits auf dem Abonnenten vorhanden ist, wird keine Aktion ausgeführt.<br /><br /> **1** = Drop - die Tabelle vor dem Neuerstellen gelöscht.<br /><br /> **2** = löschen: ein Löschvorgang wird auf der WHERE-Klausel im Teilmengenfilter ausgegeben basierend.<br /><br /> **3** = Abschneiden - identisch mit 2, jedoch Seiten statt Zeilen gelöscht. Eine WHERE-Klausel wird jedoch nicht verwendet.|  
|**pubid**|**uniqueidentifier**|Die ID der Veröffentlichung, zu der der aktuelle Artikel gehört.|  
|**der Spitzname**|**int**|Die Spitznamenzuordnung zur Identifikation des Artikels.|  
|**column_tracking**|**int**|Gibt an, ob die Spaltennachverfolgung für den Artikel implementiert wurde.|  
|**status**|**tinyint**|Zeigt den Status des Artikels an. Die folgenden Werte sind möglich:<br /><br /> **1** = unsynchronisiert - das Anfangsverarbeitungsskript zum Veröffentlichen der Tabelle wird der nächsten Ausführung der Momentaufnahme-Agent ausgeführt wird.<br /><br /> **2** = aktiv - das Anfangsverarbeitungsskript zum Veröffentlichen der Tabelle ausgeführt wurde.|  
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
|**schema_option**|**binary(8)**|Das Bitmuster der Option zur Schemagenerierung für den angegebenen Artikel. Informationen zu unterstützten *Schema_option* Werte finden Sie unter [Sp_addmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md).|  
|**destination_object**|**sysname**|Der Name der auf dem Abonnenten erstellten Tabelle.|  
|**destination_owner**|**sysname**|Der Name des Besitzers des Zielobjekts.|  
|**resolver_clsid**|**nvarchar(50)**|Die ID des benutzerdefinierten Konfliktlösers. Für einen Geschäftslogikhandler ist dieser Wert NULL.|  
|**subset_filterclause**|**nvarchar(1000)**|Die Filterklausel für diesen Artikel.|  
|**missing_col_count**|**int**|Die Anzahl veröffentlichter Spalten, die im Artikel fehlen.|  
|**missing_cols**|**varbinary(128)**|Das Bitmuster, das die Spalten beschreibt, die im Artikel fehlen.|  
|**excluded_cols**|**varbinary(128)**|Das Bitmuster der Spalten, die vom Artikel ausgeschlossen sind.|  
|**excluded_col_count**|**int**|Die Anzahl von Spalten, die aus dem Artikel ausgeschlossen sind.|  
|**columns**|**varbinary(128)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**deleted_cols**|**varbinary(128)**|Das Bitmuster, das die Spalten beschreibt, die im Artikel gelöscht wurden.|  
|**resolver_info**|**nvarchar(255)**|Der Speicherplatz für zusätzliche vom benutzerdefinierten Konfliktlöser benötigte Informationen.|  
|**view_sel_proc**|**nvarchar(290)**|Der Name einer gespeicherten Prozedur, die der Merge-Agent zum ersten Auffüllen eines Artikels in einer dynamisch gefilterten Veröffentlichung und zum Aufzählen von geänderten Zeilen in einer beliebigen gefilterten Veröffentlichung verwendet.|  
|**gen_cur**|**bigint**|Generiert eine Nummer für lokale Änderungen an der Basistabelle eines Artikels.|  
|**vertical_partition**|**int**|Gibt an, ob die Spaltenfilterung für einen Tabellenartikel aktiviert ist. **0** zeigt an, dass keine vertikale Filterung und alle Spalten veröffentlicht.|  
|**identity_support**|**int**|Gibt an, ob die automatische Verarbeitung der Identitätsbereiche aktiviert ist. **1** bedeutet, dass die Behandlung der Identitätsbereiche aktiviert ist, und **0** bedeutet, dass keine identitätsbereichsunterstützung vorhanden ist.|  
|**before_image_objid**|**int**|Die Objekt-ID der Nachverfolgungstabelle. Die Nachverfolgungstabelle enthält bestimmte Schlüsselspaltenwerte, wenn Partitionsänderungsoptimierungen für die Veröffentlichung aktiviert wurden.|  
|**before_view_objid**|**int**|Die Objekt-ID einer Sichttabelle. Die Sicht ist für eine Tabelle festgelegt, die überwacht, ob eine Zeile zu einem bestimmten Abonnenten gehört hat, bevor sie gelöscht oder aktualisiert wurde. Dies trifft nur zu, wenn Partitionsänderungsoptimierungen für die Veröffentlichung aktiviert wurden.|  
|**verify_resolver_signature**|**int**|Gibt an, ob eine digitale Signatur überprüft wird, bevor ein Konfliktlöser in einer Mergereplikation verwendet wird:<br /><br /> **0** = Signatur wird nicht überprüft.<br /><br /> **1** = Signatur wird überprüft, um festzustellen, ob sie von einer vertrauenswürdigen Quelle stammt.|  
|**allow_interactive_resolver**|**bit**|Gibt an, ob die Verwendung des interaktiven Konfliktlösers für einen Artikel aktiviert ist. **1** bedeutet, dass der interaktive Konfliktlöser für den Artikel verwendet werden kann.|  
|**fast_multicol_updateproc**|**bit**|Gibt an, ob der Merge-Agent aktiviert wurde, um in einer UPDATE-Anweisung Änderungen auf mehrere Spalten in derselben Zeile anzuwenden.<br /><br /> **0** = Probleme, die für jede Spalte ein getrenntes UPDATE geändert.<br /><br /> **1** = gibt eine UPDATE-Anweisung, die bewirkt, Updates dass für mehrere Spalten in einer Anweisung auftreten.|  
|**check_permissions**|**int**|Die Bitmap der Berechtigungen auf Tabellenebene, die überprüft werden, wenn der Merge-Agent Änderungen auf den Verleger anwendet. *Check_permissions* kann einen der folgenden Werte aufweisen:<br /><br /> **0 x 00** = Berechtigungen werden nicht überprüft.<br /><br /> **0 x 10** = überprüft Berechtigungen auf dem Verleger, bevor Einfügungen, auf dem Abonnenten vorgenommen werden hochgeladen werden können.<br /><br /> **0 x 20** = Berechtigungen werden auf dem Verleger überprüft, bevor UPDATEs, die auf einem Abonnenten hochgeladen werden können.<br /><br /> **0 x 40** = Berechtigungen werden auf dem Verleger überprüft, bevor auf einem Abonnenten ausgeführte Löschvorgänge hochgeladen werden können.|  
|**maxversion_at_cleanup**|**int**|Die maximale Generierung, für die bei der nächsten Ausführung des Merge-Agents ein Cleanup ausgeführt wird.|  
|**processing_order**|**int**|Gibt die Verarbeitungsreihenfolge von Artikeln in einer Mergeveröffentlichung an. ein Wert von **0** gibt an, dass der Artikel ungeordnet ist, und die Artikel in der Reihenfolge vom niedrigsten zum höchsten Wert verarbeitet werden. Wenn zwei Artikel denselben Wert haben, werden sie gleichzeitig verarbeitet. Weitere Informationen finden Sie unter [Specify Merge Replication properties (Angeben von Mergereplikationseigenschaften)](../../relational-databases/replication/merge/specify-merge-replication-properties.md).|  
|**upload_options**|**tinyint**|Definiert, ob Änderungen auf dem Abonnenten vorgenommen oder von diesem hochgeladen werden können. Die folgenden Werte sind möglich.<br /><br /> **0** = es gibt keine Einschränkungen für Updates, die auf dem Abonnenten vorgenommen; alle Änderungen an den Verleger hochgeladen werden.<br /><br /> **1** = Änderungen sind auf dem Abonnenten zulässig, aber nicht an den Verleger hochgeladen.<br /><br /> **2** = Änderungen sind auf dem Abonnenten nicht zulässig.|  
|**published_in_tran_pub**|**bit**|Gibt an, dass ein Artikel in einer Mergeveröffentlichung auch in einer Transaktionsveröffentlichung veröffentlicht wird.<br /><br /> **0** = der Artikel ist nicht in einem Transaktionsartikel veröffentlicht.<br /><br /> **1** = der Artikel ist auch in einem Transaktionsartikel veröffentlicht.|  
|**lightweight**|**bit**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**procname_postfix**|**NCHAR(32)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**well_partitioned_lightweight**|**bit**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**before_upd_view_objid**|**int**|Die ID der Tabellensicht vor Updates.|  
|**delete_tracking**|**bit**|Zeigt an, ob Löschvorgänge repliziert werden.<br /><br /> **0** = Löschvorgänge werden nicht repliziert.<br /><br /> **1** = löschungen werden repliziert, dies ist das Standardverhalten für die Mergereplikation.<br /><br /> Wenn der Wert des *Delete_tracking* ist **0**, auf dem Abonnenten gelöschte Zeilen müssen manuell entfernt werden, auf dem Verleger und auf dem Verleger gelöschte Zeilen müssen auf dem Abonnenten manuell entfernt werden.<br /><br /> Hinweis: Der Wert **0** führt zu einer Nichtkonvergenz.|  
|**compensate_for_errors**|**bit**|Zeigt an, ob kompensierende Aktionen ausgeführt werden, wenn während der Synchronisierung Fehler auftreten.<br /><br /> **0** = kompensierende Aktionen sind deaktiviert.<br /><br /> **1** = Änderungen, die auf einem Abonnenten oder Verleger führen immer zu kompensierenden Aktionen, um diese Änderungen rückgängig machen, dies ist das Standardverhalten für die Mergereplikation angewendet werden können.<br /><br /> Hinweis: Der Wert **0** führt zu einer Nichtkonvergenz.|  
|**pub_range**|**bigint**|Die Größe des Identitätsbereichs für den Verleger.|  
|**range**|**bigint**|Die Bereichsgröße der aufeinander folgenden Identitätswerte, die Abonnenten bei einer Anpassung zugewiesen würden.|  
|**threshold**|**int**|Als Prozentsatz angegebener Schwellenwert für den Identitätsbereich.|  
|**stream_blob_columns**|**bit**|Gibt an, ob die Datenstromoptimierung für BLOB-Spalten (Binary Large Object) verwendet wird. **1** bedeutet, dass die Optimierung versucht wird.|  
|**preserve_rowguidcol**|**bit**|Zeigt an, ob die Replikation eine vorhandene rowguid-Spalte verwendet. Der Wert **1** bedeutet, dass eine vorhandene ROWGUIDCOL-Spalte verwendet wird. **0** bedeutet, dass die Replikation die ROWGUIDCOL-Spalte hinzugefügt wurde.|  
|**partition_view_id**|**int**|Identifiziert die Sicht, die eine Abonnentenpartition definiert.|  
|**repl_view_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**partition_deleted_view_rule**|**sysname**|Die Anweisung, mit der in einem Mergereplikationstrigger die Partitions-ID für jede gelöschte oder aktualisierte Zeile basierend auf den alten Spaltenwerten abgerufen wird.|  
|**partition_inserted_view_rule**|**sysname**|Die Anweisung, mit der in einem Mergereplikationstrigger die Partitions-ID für jede eingefügte oder aktualisierte Zeile basierend auf den neuen Spaltenwerten abgerufen wird.|  
|**membership_eval_proc_name**|**sysname**|Der Name der Prozedur, die die aktuellen Partitions-IDs von Zeilen in ergibt [MSmerge_contents &#40;Transact-SQL&#41;](../../relational-databases/system-tables/msmerge-contents-transact-sql.md).|  
|**column_list**|**sysname**|Eine durch Trennzeichen getrennte Liste mit in einem Artikel veröffentlichten Spalten.|  
|**column_list_blob**|**sysname**|Eine durch Trennzeichen getrennte Liste mit in einem Artikel veröffentlichten Spalten, einschließlich BLOB-Spalten (Binary Large Object).|  
|**expand_proc**|**sysname**|Der Name der Prozedur, die bewertet Partitions-IDs für alle untergeordneten Zeilen einer neu eingefügten übergeordneten Zeile sowie für übergeordnete Zeilen, die eine partitionsänderung unterzogen oder gelöscht wurden.|  
|**logical_record_parent_nickname**|**int**|Der Spitzname des übergeordneten Elements der obersten Ebene eines Artikels in einem logischen Datensatz.|  
|**logical_record_view**|**int**|Eine Sicht, die den rowguid-Wert des übergeordneten Artikels der obersten Ebene ausgibt, der jedem untergeordneten rowguid-Wert entspricht.|  
|**logical_record_deleted_view_rule**|**sysname**|Ähnlich wie **Logical_record_view**, außer dass die untergeordneten Zeilen in der "gelöschten" Tabelle in Update- und delete-Trigger werden.|  
|**logical_record_level_conflict_detection**|**bit**|Gibt an, ob Konflikte auf der logischen Datensatzebene oder auf der Zeilen- oder Spaltenebene erkannt werden sollen.<br /><br /> **0** = die konflikterkennung verwendet wird, mit Zeilen- oder Spaltenebene.<br /><br /> **1** = logischer Datensatz konflikterkennung verwendet wird, wenn eine Änderung in einer Zeile auf dem Verleger und die Änderung in einer separaten Zeile desselben logischen Datensatzes auf dem Abonnenten als Konflikt behandelt.<br /><br /> Mit dem Wert 1 kann nur die Konfliktauflösung auf der logischen Datensatzebene verwendet werden.|  
|**logical_record_level_conflict_resolution**|**bit**|Gibt an, ob Konflikte auf der logischen Datensatzebene oder auf die Zeile oder Spaltenebene aufgelöst werden soll.<br /><br /> **0** = Auflösung verwendet mit Zeilen- oder Spaltenebene.<br /><br /> **1** = bei einem Konflikt der gesamte logische Datensatz des Gewinners den gesamten logischen Datensatz des verlierers überschreibt.<br /><br /> Der Wert 1 kann für die Erkennung auf der logischen Datensatzebene und für die Erkennung auf Zeilen- oder Spaltenebene verwendet werden.|  
|**partition_options**|**tinyint**|Definiert die Art und Weise, wie Daten im Artikel partitioniert werden. Dies ermöglicht Leistungsoptimierungen, wenn alle Zeilen nur zu einer einzigen Partition oder zu einem einzigen Abonnement gehören. Die *Partition_options* kann einer der folgenden Werte sein.<br /><br /> **0** = das Filtern für den Artikel, die entweder statisch oder ergibt keine eindeutige Teilmenge von Daten für jede Partition, d. h. einer "überlappenden" Partitions.<br /><br /> **1** = die Partitionen überlappen, und auf dem Abonnenten vorgenommene DML-Updates können nicht die Partition ändern, der eine Zeile gehört.<br /><br /> **2** = das Filtern für den Artikel nicht überlappende Partitionen ergibt, aber mehrere Abonnenten können die gleiche Partition erhalten.<br /><br /> **3** = das Filtern für den Artikel nicht überlappende Partitionen ergibt, die für jedes Abonnement eindeutig sind.|  
|**name**|**sysname**|Der Name einer Partition.|  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Partitionen für eine Mergeveröffentlichung mit parametrisierten Filtern](../../relational-databases/replication/publish/manage-partitions-for-a-merge-publication-with-parameterized-filters.md)   
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_addmergepartition &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql.md)   
 [sp_helpmergepartition &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepartition-transact-sql.md)  
  
  
