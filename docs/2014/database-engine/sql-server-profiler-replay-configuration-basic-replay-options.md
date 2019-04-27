---
title: SQL Server Profiler - Wiedergabekonfiguration (grundlegende Wiedergabeoptionen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.replay.generaloptions.f1
helpviewer_keywords:
- Replay Configuration dialog box
ms.assetid: 85a1dec6-9bbc-477a-86c5-b463db9ebb31
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 379cb1ab2ed12ad8d5d835068bb68008fd6ca9af
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62773822"
---
# <a name="sql-server-profiler---replay-configuration-basic-replay-options"></a>SQL Server Profiler-Wiedergabekonfiguration (Grundlegende Wiedergabeoptionen)
  Mithilfe der Seite **Grundlegende Wiedergabeoptionen** des Dialogfelds **Wiedergabekonfiguration** können Sie angeben, auf welche Weise eine Ablaufverfolgungsdatei oder -tabelle wiedergegeben werden soll.  
  
 Zum Anzeigen dieses Fensters öffnen Sie mithilfe von [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] eine Ablaufverfolgungsdatei oder -tabelle, die die zur Wiedergabe vorgesehenen Ereignisse enthält. Weitere Informationen finden Sie unter [Replay Requirements](../tools/sql-server-profiler/replay-requirements.md). Wenn die Ablaufverfolgungsdatei oder -tabelle geöffnet ist, klicken Sie im Menü **Wiedergeben** auf **Start**, und stellen Sie dann eine Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] her, auf der die Ablaufverfolgung wiedergegeben werden soll.  
  
## <a name="options"></a>Optionen  
 **Wiedergabeserver**  
 Zeigt die Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] an, mit der eine Verbindung für die Wiedergabe hergestellt wird.  
  
 **Ändern...**  
 Öffnet das Dialogfeld **Verbindung mit Server herstellen** , um eine Verbindung mit einem anderen Server herzustellen.  
  
 **In Datei speichern**  
 Speichert die Wiedergabeergebnisse in einer Datei. [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] zeigt das Standarddialogfeld zum Speichern von Dateien an, in dem Sie einen Speicherort für die Datei angeben können.  
  
 **In Tabelle speichern**  
 Speichert die Wiedergabeergebnisse in einer Tabelle. [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] wird ein Dialogfeld zum Auswählen der Tabelle angezeigt, in dem Sie einen Speicherort für die Tabelle angeben können.  
  
 **Anzahl von Wiedergabethreads**  
 Gibt die Anzahl der Threads an, die gleichzeitig verwendet werden können. Bei einer höheren Anzahl werden zwar mehr Ressourcen beansprucht, dafür erfolgt die Wiedergabe schneller und in höherem Maße gleichzeitig.  
  
 **Ereignisse in der Reihenfolge wiedergeben, in der ihr Ablauf verfolgt wurde**  
 Gibt Ereignisse sequenziell wieder. Verwenden Sie diese Option, wenn Sie eine Ablaufverfolgung zum Debuggen wiedergeben.  
  
 **Ereignisse mithilfe mehrerer Threads wiedergeben**  
 Gibt die Ereignisse gleichzeitig wieder. Diese Option ist zwar schneller als die sequenzielle Wiedergabe von Ereignissen, dafür ist kein Debugging verfügbar. Die Ereignisse werden je nach dazugehöriger Systemprozess-ID (SPID) geordnet.  
  
 **Wiedergabeergebnisse anzeigen**  
 Zeigt die Wiedergabeergebnisse in [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]an.  
  
## <a name="see-also"></a>Siehe auch  
 [Wiedergeben einer Ablaufverfolgungstabelle &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md)   
 [Wiedergeben einer Ablaufverfolgungsdatei &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md)   
 [Wiedergeben von Ablaufverfolgungen](../tools/sql-server-profiler/replay-traces.md)  
  
  
