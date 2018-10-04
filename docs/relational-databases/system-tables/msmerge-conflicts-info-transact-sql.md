---
title: MSmerge_conflicts_info (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSmerge_conflicts_info_TSQL
- MSmerge_conflicts_info
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_conflicts_info system table
ms.assetid: 6b76ae96-737a-4000-a6b6-fcc8772c2af4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 34dd7496d514db14399134eb7ffe222af7251f95
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47737728"
---
# <a name="msmergeconflictsinfo-transact-sql"></a>MSmerge_conflicts_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSmerge_conflicts_info** -Tabelle verfolgt Konflikte, die beim Synchronisieren eines Abonnements für eine Mergeveröffentlichung auftreten. Die verlierenden Zeilendaten für Konflikte befindet sich in der [MSmerge_conflict_publication_article](../../relational-databases/system-tables/msmerge-conflict-publication-article-transact-sql.md) Tabelle für den Artikel, in dem der Konflikt aufgetreten ist. Diese Tabelle wird auf dem Verleger in der Veröffentlichungsdatenbank und auf dem Abonnenten in der Abonnementdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|Der Spitzname der veröffentlichten Tabelle.|  
|**rowguid**|**uniqueidentifier**|Der Bezeichner für die Konfliktzeile.|  
|**origin_datasource**|**nvarchar(255)**|Der Name der Datenbank, aus der die konfliktverursachende Änderung stammt.|  
|**conflict_type**|**int**|Der Typ des Konflikts, der aufgetreten ist. Die folgenden Werte sind möglich.<br /><br /> **1** = Update-Konflikt: der Konflikt wird erkannt, auf der Zeilenebene.<br /><br /> **2** = Spalte Update-Konflikt: der Konflikt auf Spaltenebene erkannt.<br /><br /> **3** = Update-Delete-WINS-Konflikt: der Löschvorgang gewinnt den Konflikt.<br /><br /> **4** = Update gewinnt Delete-Konflikt: der gelöschte Zeilen-GUID, die den Konflikt verliert, wird in dieser Tabelle aufgezeichnet.<br /><br /> **5** = Fehler beim Hochladen Anweisung einfügen: der Einfügevorgang des Abonnenten konnte nicht auf dem Verleger angewendet werden.<br /><br /> **6** = Fehler beim Einfügen herunterladen: der Einfügevorgang des Verlegers konnte nicht auf dem Abonnenten angewendet werden.<br /><br /> **7** = hochladen konnte nicht gelöscht: der Löschvorgang des Abonnenten konnte nicht an den Verleger hochgeladen werden.<br /><br /> **8** = Fehler beim Löschen von herunterladen: der Löschvorgang des Verlegers konnte nicht auf den Abonnenten heruntergeladen werden.<br /><br /> **9** = hochladen konnte nicht aktualisiert: der Updatevorgang des Abonnenten konnte nicht auf dem Verleger angewendet werden.<br /><br /> **10** = Fehler beim Aktualisieren herunterladen: der Updatevorgang des Verlegers konnte nicht auf den Abonnenten angewendet werden.<br /><br /> **11** = Lösung<br /><br /> **12** = logischer Datensatz Delete, Update gewinnt: der gelöschte logische Datensatz, der den Konflikt verliert, wird in dieser Tabelle aufgezeichnet.<br /><br /> **13** = logischer Datensatz Konflikt Insert/Update: Einfügung in einen logischen Datensatz steht in Konflikt mit einem Update.<br /><br /> **14** = logischer Datensatz löschen Wins-Update-Konflikt: der aktualisierte logische Datensatz, der den Konflikt verliert, wird in dieser Tabelle aufgezeichnet.|  
|**reason_code**|**int**|Der Fehlercode, der kontextbezogen sein kann. Bei Update / Update "und" Update / Delete-Konflikten, der Wert für diese Spalte entspricht der **Conflict_type**. Bei Konflikten, bei denen Fehler beim Ändern aufgetreten sind, wird als Ursachencode der bei der Änderung im Merge-Agent aufgetretene Fehler verwendet. Wenn der Merge-Agent eine Einfügung, auf dem Abonnenten aufgrund einer Verletzung eines Primärschlüssels anwenden können, z. B. protokolliert eine **Conflict_type** 6 ("Download Insert ist fehlgeschlagen") und ein **Reason_code** 2627, handelt es sich die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interne Fehlermeldung für eine primärschlüsselverletzung: "Verletzung der %ls-Einschränkung ' %. * ls'. Doppelten Schlüssel kann nicht eingefügt werden, in Objekt ' %. \*ls'. "|  
|**reason_text**|**nvarchar(720)**|Die Fehlerbeschreibung, die kontextbezogen sein kann.|  
|**pubid**|**uniqueidentifier**|Der Bezeichner für die Veröffentlichung.|  
|**MSrepl_create_time**|**datetime**|Die Uhrzeit, zu der der Konflikt aufgetreten ist.|  
|**origin_datasource_id**|**uniqueidentifier**|Der Bezeichner der Datenbank, aus der die konfliktverursachende Änderung stammt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
