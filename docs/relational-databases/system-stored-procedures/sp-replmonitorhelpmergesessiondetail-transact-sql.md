---
title: Sp_replmonitorhelpmergesessiondetail (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorhelpmergesessiondetail
- sp_replmonitorhelpmergesessiondetail_TSQL
helpviewer_keywords:
- sp_replmonitorhelpmergesessiondetail
ms.assetid: 805c92fc-3169-410c-984d-f37e063b791d
author: stevestein
ms.author: sstein
ms.openlocfilehash: c9f883b7eafc59a3d9d93541e07fe4c4db08b9c9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67950596"
---
# <a name="spreplmonitorhelpmergesessiondetail-transact-sql"></a>sp_replmonitorhelpmergesessiondetail (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt detaillierte Artikelinformationen zu einer bestimmten Replikationsmerge-Agent-Sitzung zurück, mit der die Mergereplikation überwacht wird. Das Resultset enthält eine detaillierte Zeile für jeden Artikel, der während der Sitzung synchronisiert wurde. Es enthält außerdem eine Zeile, die die Sitzungsinitialisierung darstellt, und Zeilen mit Zusammenfassungen der Upload- und Downloadphasen der Sitzung. Diese gespeicherte Prozedur wird auf dem Verteiler für die Verteilungsdatenbank oder auf dem Abonnenten für die Abonnementdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_replmonitorhelpmergesessiondetail [ @session_id = ] session_id  
```  
  
## <a name="arguments"></a>Argumente  
`[ @session_id = ] session_id` Gibt eine agentsitzung an. *Sitzungs-ID* ist **Int** hat keinen Standardwert.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**PhaseID**|**int**|Die Phase der Synchronisierungssitzung. Die folgenden Werte sind möglich:<br /><br /> **0** = Initialisierungs- oder Zusammenfassungszeile<br /><br /> **1** = Upload<br /><br /> **2** = herunterladen|  
|**ArticleName**|**sysname**|Der Name des Artikels, der synchronisiert wird. **ArticleName** enthält auch Zusammenfassungsinformationen für Zeilen im Resultset, die keine Artikeldetails darstellen.|  
|**PercentComplete**|**decimal**|Gibt die prozentualen Änderungen an, die insgesamt in einer Artikeldetailzeile für aktuell ausgeführte oder fehlerhafte Sitzungen angewendet wurden.|  
|**RelativeCost**|**decimal**|Gibt den Zeitaufwand zum Synchronisieren des Artikels als Prozentsatz der Gesamtsynchronisierungszeit für die Sitzung an.|  
|**Dauer**|**int**|Dauer der Agentsitzung|  
|**Inserts**|**int**|Anzahl von Einfügungen in einer Sitzung|  
|**Updates**|**int**|Anzahl von Updates in einer Sitzung|  
|**Löschvorgang**|**int**|Anzahl von Löschvorgängen in einer Sitzung|  
|**Konflikte**|**int**|Anzahl der in einer Sitzung aufgetretenen Konflikte|  
|**ErrorID**|**int**|ID eines Sitzungsfehlers|  
|**SeqNo**|**int**|Reihenfolge von Sitzungen im Resultset|  
|**RowType**|**int**|Gibt an, welchen Informationstyp jede Zeile im Resultset repräsentiert.<br /><br /> **0** = Initialisierung<br /><br /> **1** = uploadzusammenfassung<br /><br /> **2** = artikeluploaddetail<br /><br /> **3** = downloadzusammenfassung<br /><br /> **4** = artikeldownloaddetail|  
|**SchemaChanges**|**int**|Anzahl von Schemaänderungen in einer Sitzung|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_replmonitorhelpmergesessiondetail** wird zum Überwachen der Mergereplikation verwendet.  
  
 Bei der Ausführung auf dem Abonnenten **Sp_replmonitorhelpmergesessiondetail** nur Gibt ausführliche Informationen zu den letzten 5 Merge-agentsitzungen zurück.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Db_owner** oder **Replmonitor** festen Datenbankrolle, die für die Verteilungsdatenbank auf dem Verteiler oder für die Abonnementdatenbank auf dem Abonnenten ausführen kann **Sp_ Replmonitorhelpmergesessiondetail**.  
  
## <a name="see-also"></a>Siehe auch  
 [Programmgesteuertes Überwachen der Replikation](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
