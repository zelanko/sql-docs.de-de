---
title: Veröffentlichungsinformationen, Agents (Transaktionsveröffentlichung) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.downlevelagents.tran.f1
ms.assetid: 38ef2f54-53bb-4053-876d-86f8f06a4519
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7a4542370eff5ad631701f0bf988929ad56e8799
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54125820"
---
# <a name="publication-information-agents-transactional-publication"></a>Veröffentlichungsinformationen, Agents (Transaktionsveröffentlichung)
  Auf der Registerkarte **Agents** werden Zusammenfassungsinformationen zu den Agents für die ausgewählte Veröffentlichung angezeigt. Die Informationen auf dem Momentaufnahme-Agent und dem Protokolllese-Agent werden für alle Transaktionsveröffentlichungen angezeigt. Die Informationen auf dem Warteschlangenlese-Agent werden für solche Transaktionsveröffentlichungen, die für Abonnements mit verzögertem Update über eine Warteschlange verfügbar sind.  
  
## <a name="options"></a>Optionen  
 Ausführliche Informationen und eine Liste der Aufträge für einen Agent können Sie anzeigen, indem Sie mit der rechten Maustaste in die Zeile des jeweiligen Agents klicken und ein Kontextmenü auswählen. Wenn Sie die Anzeige der Daten im Raster ändern möchten, klicken Sie mit der rechten Maustaste auf das Raster, und klicken Sie anschließend auf eine der folgenden Optionen:  
  
-   **Sortierung**: Sortieren Sie nach einer oder mehreren Spalten in der **Sortierspalten** Dialogfeld.  
  
-   **Anzuzeigende Spalten auswählen**: Wählen Sie die anzuzeigenden Spalten sowie die Reihenfolge, in der anzeigen in der **Spalten auswählen** Dialogfeld.  
  
-   **Filter**: Filtern Sie Zeilen im Raster auf Grundlage der Spaltenwerte in die **Filtereinstellungen** Dialogfeld.  
  
-   **Filter löschen**: Deaktivieren Sie alle filtereinstellungen für das Raster an.  
  
 Filtereinstellungen sind rasterspezifisch. Die Spaltenauswahl und -sortierung wird auf alle Raster desselben Typs angewendet, z. B. das Veröffentlichungsraster für jeden Verleger.  
  
 **Status**  
 Die Status der einzelnen Replikations-Agents, die der Veröffentlichung zugeordnet sind. In der folgenden Liste sind die möglichen Statuswerte aufgeführt:  
  
-   Fehler  
  
-   Fehlgeschlagener Befehl wird wiederholt  
  
-   Wird nicht ausgeführt  
  
-   Wird ausgeführt  
  
-   Abgeschlossen  
  
 **Agent**  
 Die Namen der einzelnen Replikations-Agents, die der Veröffentlichung zugeordnet sind. Der Verteilungs-Agent ist den Abonnements dieser Veröffentlichung zugeordnet. Weitere Informationen finden Sie unter [Anzeigen von Informationen und Ausführen von Aufgaben mithilfe des Replikationsmonitors](monitor/view-information-and-perform-tasks-replication-monitor.md).  
  
 **Letzte Startzeit**  
 Zeitpunkt, zu dem der Agent zuletzt gestartet wurde.  
  
 **Dauer**  
 Zeitdauer, für die der Agent ausgeführt wurde. Dieser Wert gibt entweder die verstrichene Zeit eines zurzeit ausgeführten Agents oder die Gesamtzeit des zuvor ausgeführten Agents an.  
  
 **Letzte Aktion**  
 Die letzte Aktion, die bei der letzten Ausführung des Agents ausgeführt wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [Starten des Replikationsmonitors](monitor/start-the-replication-monitor.md)   
 [Anzeigen von Informationen und Ausführen von Aufgaben mithilfe des Replikationsmonitors](monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Überwachen der Replikation](monitoring-replication.md)  
  
  
