---
title: MSmerge_conflicts_info (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
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
ms.openlocfilehash: 7629bff37fb33080f8057fc1799437fff182882f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68044805"
---
# <a name="msmergeconflictsinfo-transact-sql"></a>MSmerge_conflicts_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSmerge_conflicts_info** -Tabelle verfolgt Konflikte, die beim Synchronisieren eines Abonnements für eine Mergeveröffentlichung auftreten. Die verlierenden Zeilendaten für Konflikte befindet sich in der [MSmerge_conflict_publication_article](../../relational-databases/system-tables/msmerge-conflict-publication-article-transact-sql.md) Tabelle für den Artikel, in dem der Konflikt aufgetreten ist. Diese Tabelle wird auf dem Verleger in der Veröffentlichungsdatenbank und auf dem Abonnenten in der Abonnementdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|Der Spitzname der veröffentlichten Tabelle.|  
|**rowguid**|**uniqueidentifier**|Der Bezeichner für die Konfliktzeile.|  
|**origin_datasource**|**nvarchar(255)**|Der Name der Datenbank, aus der die konfliktverursachende Änderung stammt.|  
|**conflict_type**|**int**|Der Typ des Konflikts, der aufgetreten ist. Die folgenden Werte sind möglich.<br /><br /> **1** = Update-Konflikt: Der Konflikt wurde auf Zeilenebene erkannt.<br /><br /> **2** = Spalte Update-Konflikt: Der Konflikt auf Spaltenebene erkannt.<br /><br /> **3** = Update, Delete gewinnt-Konflikt: Der Löschvorgang gewinnt den Konflikt.<br /><br /> **4** = Update gewinnt Delete-Konflikt: Der gelöschte Zeilen-GUID, die den Konflikt verliert, wird in dieser Tabelle aufgezeichnet.<br /><br /> **5** = Fehler beim Hochladen einer Insert: Der Einfügevorgang des Abonnenten konnte nicht auf dem Verleger angewendet werden.<br /><br /> **6** = Fehler beim Herunterladen einer Insert: Der Einfügevorgang des Verlegers konnte nicht auf dem Abonnenten angewendet werden.<br /><br /> **7** = Fehler beim Löschen der hochladen: Der Löschvorgang des Abonnenten konnte nicht an den Verleger hochgeladen werden.<br /><br /> **8** = Fehler beim Löschen der Download: Der Löschvorgang des Verlegers konnte nicht auf den Abonnenten heruntergeladen werden.<br /><br /> **9** = Fehler beim Aktualisieren der hochladen: Der Updatevorgang des Abonnenten konnte nicht auf dem Verleger angewendet werden.<br /><br /> **10** = Fehler beim Download aktualisieren: Der Updatevorgang des Verlegers konnte nicht auf dem Abonnenten angewendet werden.<br /><br /> **11** = Lösung<br /><br /> **12** = logischer Datensatz Update gewinnt löschen: Der gelöschte logische Datensatz, der den Konflikt verliert, wird in dieser Tabelle aufgezeichnet.<br /><br /> **13** = logischer Datensatz Konflikt Insert aktualisieren: Fügen Sie einen logischen Datensatz verursacht einen Konflikt mit einem Update.<br /><br /> **14** = logischer Datensatz löschen, WINS-Update-Konflikt: Der aktualisierte logische Datensatz, der den Konflikt verliert, wird in dieser Tabelle aufgezeichnet.|  
|**reason_code**|**int**|Der Fehlercode, der kontextbezogen sein kann. Bei Update / Update "und" Update / Delete-Konflikten, der Wert für diese Spalte entspricht der **Conflict_type**. Bei Konflikten, bei denen Fehler beim Ändern aufgetreten sind, wird als Ursachencode der bei der Änderung im Merge-Agent aufgetretene Fehler verwendet. Wenn der Merge-Agent eine Einfügung, auf dem Abonnenten aufgrund einer Verletzung eines Primärschlüssels anwenden können, z. B. protokolliert eine **Conflict_type** 6 ("Download Insert ist fehlgeschlagen") und ein **Reason_code** 2627, handelt es sich die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interne Fehlermeldung für eine primärschlüsselverletzung: "Verletzung der %ls-Einschränkung ' %. * ls'. Doppelten Schlüssel kann nicht eingefügt werden, in Objekt ' %. \*ls'. "|  
|**reason_text**|**nvarchar(720)**|Die Fehlerbeschreibung, die kontextbezogen sein kann.|  
|**pubid**|**uniqueidentifier**|Der Bezeichner für die Veröffentlichung.|  
|**MSrepl_create_time**|**datetime**|Die Uhrzeit, zu der der Konflikt aufgetreten ist.|  
|**origin_datasource_id**|**uniqueidentifier**|Der Bezeichner der Datenbank, aus der die konfliktverursachende Änderung stammt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
