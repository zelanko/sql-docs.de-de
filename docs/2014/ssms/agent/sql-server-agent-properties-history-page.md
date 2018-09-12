---
title: SQL Server-Agent-Eigenschaften (Seite Verlauf)|Microsoft-Dokumente
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.history.f1
ms.assetid: dc73734c-b3c3-407f-bbd1-8714b4fa47b0
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 46a62984a55b5141f66fb459b42274fe3ca94c1d
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43818186"
---
# <a name="sql-server-agent-properties-history-page"></a>SQL Server-Agent-Eigenschaften (Seite Verlauf)
  Auf dieser Seite können Sie die Einstellungen für die Verwaltung des Verlaufsprotokolls für den [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst anzeigen und bearbeiten.  
  
## <a name="options"></a>Tastatur  
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
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Agent-Fehlerprotokoll](sql-server-agent-error-log.md)  
  
  
