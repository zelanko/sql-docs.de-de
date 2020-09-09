---
title: sp_replmonitorhelpmergesessiondetail (T-SQL)
description: Beschreibt die gespeicherte Prozedur sp_replmonitorhelpmergesessiondetail, mit der ausführliche Informationen zu einer bestimmten Replikations Merge-Agent Sitzung zurückgegeben werden.
ms.custom: seo-lt-2019
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 8c09007256e5c336ecfa2ad62c45623fe2c0e5ff
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89543203"
---
# <a name="sp_replmonitorhelpmergesessiondetail-transact-sql"></a>sp_replmonitorhelpmergesessiondetail (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Gibt detaillierte Artikelinformationen zu einer bestimmten Replikationsmerge-Agent-Sitzung zurück, mit der die Mergereplikation überwacht wird. Das Resultset enthält eine detaillierte Zeile für jeden Artikel, der während der Sitzung synchronisiert wurde. Es enthält außerdem eine Zeile, die die Sitzungsinitialisierung darstellt, und Zeilen mit Zusammenfassungen der Upload- und Downloadphasen der Sitzung. Diese gespeicherte Prozedur wird auf dem Verteiler für die Verteilungsdatenbank oder auf dem Abonnenten für die Abonnementdatenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_replmonitorhelpmergesessiondetail [ @session_id = ] session_id  
```  
  
## <a name="arguments"></a>Argumente  
`[ @session_id = ] session_id` Gibt eine Agentsitzung an. *session_id* ist vom Datentyp **int** und hat keinen Standardwert.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
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
|**SeqNo**|**int**|Reihenfolge von Sitzungen im Resultset|  
|**RowType**|**int**|Gibt an, welchen Informationstyp jede Zeile im Resultset repräsentiert.<br /><br /> **0** = Initialisierung<br /><br /> **1** = Uploadzusammenfassung<br /><br /> **2** = Details zum Hochladen von Artikeln<br /><br /> **3** = Download Zusammenfassung<br /><br /> **4** = Details zum Download von Artikeln|  
|**SchemaChanges**|**int**|Anzahl von Schemaänderungen in einer Sitzung|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_replmonitorhelpmergesessiondetail** wird zum Überwachen der Mergereplikation verwendet.  
  
 Wenn **sp_replmonitorhelpmergesessiondetail** auf dem Abonnenten ausgeführt wird, werden nur ausführliche Informationen zu den letzten 5 Merge-Agent Sitzungen zurückgegeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Daten Bank Rolle **db_owner** oder **replmonitor** in der Verteilungs Datenbank auf dem Verteiler oder der Abonnement Datenbank auf dem Abonnenten können **sp_replmonitorhelpmergesessiondetail**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Programmgesteuertes Überwachen der Replikation](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
