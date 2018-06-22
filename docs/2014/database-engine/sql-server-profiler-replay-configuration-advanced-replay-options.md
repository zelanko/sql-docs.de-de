---
title: SQL Server Profiler - Wiedergabekonfiguration (Erweiterte Wiedergabeoptionen) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.pro.replay.generaloptions.advanced.f1
helpviewer_keywords:
- Replay Configuration dialog box
ms.assetid: b4eb34f7-3af6-4a44-ba7e-2b8430ec3cd7
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4147fa559e52373afab9352aabaaa46a79d8a266
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048794"
---
# <a name="sql-server-profiler---replay-configuration-advanced-replay-options"></a>SQL Server Profiler - Wiedergabekonfiguration (Erweiterte Wiedergabeoptionen)
  Mithilfe der Registerkarte **Erweiterte Wiedergabeoptionen** des Dialogfelds **Wiedergabekonfiguration** können Sie angeben, auf welche Weise eine Ablaufverfolgungsdatei wiedergegeben werden soll.  
  
 Zum Anzeigen dieses Fensters öffnen Sie mithilfe von [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] eine Ablaufverfolgungsdatei oder -tabelle, die die zur Wiedergabe vorgesehenen Ereignisse enthält. Weitere Informationen finden Sie unter [Replay Requirements](../tools/sql-server-profiler/replay-requirements.md). Wenn die Ablaufverfolgungsdatei oder -tabelle geöffnet ist, klicken Sie im Menü **Wiedergeben** auf **Start**, und stellen Sie dann eine Verbindung mit der Instanz von SQL Server her, auf der die Ablaufverfolgung wiedergegeben werden soll. Klicken Sie anschließend auf die Registerkarte **Erweiterte Wiedergabeoptionen** .  
  
## <a name="options"></a>Tastatur  
 **System-SPIDs wiedergeben**  
 Gibt an, ob [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] die Systemprozess-IDs (SPIDs) wiedergibt.  
  
 **Nur eine SPID wiedergeben**  
 Gibt nur die Aktivität in der Ablaufverfolgungs-Quelldatei wieder, die mit der ausgewählten SPID in Beziehung steht.  
  
 **SPID für Wiedergabe**  
 Gibt an, welche SPID wiedergegeben werden soll.  
  
 **Wiedergabe nach Datum und Zeit beschränken**  
 Durch Aktivieren dieses Kontrollkästchens kann festgelegt werden, dass nur ein Teil der Ablaufverfolgungs-Quelldatei wiedergegeben wird.  
  
 **Startzeit**  
 Datum und Uhrzeit in der Ablaufverfolgungs-Quelldatei, zu der die Wiedergabe beginnen soll.  
  
 **Beendigungszeit**  
 Datum und Uhrzeit in der Ablaufverfolgungs-Quelldatei, zu der die Wiedergabe enden soll.  
  
 **Wartezeit für Systemüberwachung (Sek.)**  
 Gibt die Wartezeit für die Wiedergabe in Sekunden an. Der Standardwert ist 3600 Sekunden (1 Stunde). Die Einstellung bestimmt den Zeitraum, in dem ein Prozess ausgeführt werden kann, bevor er von der Systemüberwachung beendet wird.  
  
 **Abrufintervall für Systemüberwachung (Sek.)**  
 Gibt das Abrufinterval für die Systemüberwachung während der Wiedergabe in Sekunden an. Der Standardwert ist 60 Sekunden. Mit diesem Wert kann der Benutzer konfigurieren, wie oft die Systemüberwachung Informationen zu potenziell zu beendenden Vorgängen abruft.  
  
 **Überwachung blockierter SQL Server-Prozesse aktivieren**  
 Aktiviert einen Prozess, mit dem nach blockierten oder blockierenden Prozessen gesucht wird.  
  
 **Wartezeit für die Überwachung blockierter Prozesse (Sek.)**  
 Konfiguriert die Häufigkeit, mit der mithilfe der Überwachung für blockierte Prozesse nach blockierten oder blockierenden Prozessen gesucht wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Wiedergeben einer Ablaufverfolgungstabelle &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md)   
 [Wiedergeben einer Ablaufverfolgungsdatei &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md)   
 [Wiedergeben von Ablaufverfolgungen](../tools/sql-server-profiler/replay-traces.md)  
  
  