---
title: sp_replmonitorhelpmergesessiondetail (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: b1aaa8afdb6ad67f906140c0714f115b64c08bc1
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2019
ms.locfileid: "68764429"
---
# <a name="spreplmonitorhelpmergesessiondetail-transact-sql"></a>sp_replmonitorhelpmergesessiondetail (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Gibt detaillierte Artikelinformationen zu einer bestimmten Replikationsmerge-Agent-Sitzung zurück, mit der die Mergereplikation überwacht wird. Das Resultset enthält eine detaillierte Zeile für jeden Artikel, der während der Sitzung synchronisiert wurde. Es enthält außerdem eine Zeile, die die Sitzungsinitialisierung darstellt, und Zeilen mit Zusammenfassungen der Upload- und Downloadphasen der Sitzung. Diese gespeicherte Prozedur wird auf dem Verteiler für die Verteilungsdatenbank oder auf dem Abonnenten für die Abonnementdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_replmonitorhelpmergesessiondetail [ @session_id = ] session_id  
```  
  
## <a name="arguments"></a>Argumente  
`[ @session_id = ] session_id`Gibt eine Agentsitzung an. *session_id* ist vom Datentyp **int** und hat keinen Standardwert.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**PhaseID**|**int**|Die Phase der Synchronisierungssitzung. Die folgenden Werte sind möglich:<br /><br /> **0** = Initialisierungs-oder Zusammenfassungs Zeile<br /><br /> **1** = hochladen<br /><br /> **2** = herunterladen|  
|**ArticleName**|**sysname**|Der Name des Artikels, der synchronisiert wird. **ArticleName** enthält auch Zusammenfassungs Informationen für Zeilen im Resultset, die keine Artikeldetails darstellen.|  
|**PercentComplete**|**decimal**|Gibt die prozentualen Änderungen an, die insgesamt in einer Artikeldetailzeile für aktuell ausgeführte oder fehlerhafte Sitzungen angewendet wurden.|  
|**RelativeCost**|**decimal**|Gibt den Zeitaufwand zum Synchronisieren des Artikels als Prozentsatz der Gesamtsynchronisierungszeit für die Sitzung an.|  
|**Dauer**|**int**|Dauer der Agentsitzung|  
|**Inserts**|**int**|Anzahl von Einfügungen in einer Sitzung|  
|**Updates**|**int**|Anzahl von Updates in einer Sitzung|  
|**Löschvorgang**|**int**|Anzahl von Löschvorgängen in einer Sitzung|  
|**Konflikte**|**int**|Anzahl der in einer Sitzung aufgetretenen Konflikte|  
|**ErrorID**|**int**|ID eines Sitzungsfehlers|  
|**Des Seqno**|**int**|Reihenfolge von Sitzungen im Resultset|  
|**RowType**|**int**|Gibt an, welchen Informationstyp jede Zeile im Resultset repräsentiert.<br /><br /> **0** = Initialisierung<br /><br /> **1** = Uploadzusammenfassung<br /><br /> **2** = Details zum Hochladen von Artikeln<br /><br /> **3** = Download Zusammenfassung<br /><br /> **4** = Details zum Download von Artikeln|  
|**Schemachanges**|**int**|Anzahl von Schemaänderungen in einer Sitzung|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_replmonitorhelpmergesessiondetail** wird zum Überwachen der Mergereplikation verwendet.  
  
 Bei der Ausführung auf dem Abonnenten gibt **sp_replmonitorhelpmergesessiondetail** nur ausführliche Informationen zu den letzten fünf Merge-Agent Sitzungen zurück.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Daten Bank Rolle **db_owner** oder **replmonitor** in der Verteilungs Datenbank auf dem Verteiler oder in der Abonnement Datenbank auf dem Abonnenten können **sp_replmonitorhelpmergesessiondetail**ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Programmgesteuertes Überwachen der Replikation](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
