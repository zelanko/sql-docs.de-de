---
title: SQL Server-Agent-Eigenschaften (Seite Verlauf)|Microsoft-Dokumente
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.history.f1
ms.assetid: dc73734c-b3c3-407f-bbd1-8714b4fa47b0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4008df15ded37398ef8565bac759364699561fad
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85058689"
---
# <a name="sql-server-agent-properties-history-page"></a>SQL Server-Agent-Eigenschaften (Seite Verlauf)
  Mithilfe dieser Seite können Sie Einstellungen für die Verwaltung des Verlaufs Protokolls für den-Agent-Dienst anzeigen und ändern [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="options"></a>Optionen  
 **Größe des Auftragsverlaufsprotokolls beschränken**  
 Legt die Grenzen für die Menge der Auftragsverlaufsinformationen fest, die im Protokoll des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents verbleiben.  
  
 **Maximale Länge des Auftragsverlaufsprotokolls (in Zeilen)**  
 Legt die maximale Anzahl der Zeilen fest, die der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent beibehält. Wenn das Protokoll diese Anzahl von Zeilen überschreitet, werden die ältesten Zeilen vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent entfernt, sobald neue Zeilen eingetragen werden.  
  
 **Maximale Zeilenanzahl pro Auftrag in Auftragsverlauf**  
 Legt die maximale Anzahl von Zeilen fest, die der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent pro Auftrag beibehält. Wenn der Verlauf eines bestimmten Auftrags diese Anzahl von Zeilen überschreitet, werden die ältesten Zeilen vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent entfernt, sobald neue Zeilen eingetragen werden.  
  
 **Agentverlauf entfernen**  
 Gibt an, dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent Einträge entfernt, die länger als eine bestimmte Zeitspanne im Protokoll vorhanden sind. Dies ist eine einmalige Ausführung zum Löschen des Verlaufs. Wenn ein erneut auftretender Auftrag benötigt wird, erstellen und planen Sie einen Wartungsplan mit einem Cleanupauftrag.  
  
 **Älter als**  
 Legt die Zeitspanne fest, für die der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent die Einträge beibehält.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Agent-Fehlerprotokoll](sql-server-agent-error-log.md)  
  
  
