---
title: Aktualisieren des Auftragsaktivitätsmonitors | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.jobactivitymon.refresh.f1
ms.assetid: 413a368e-fd2b-4e1f-b370-002cdbc85bab
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 44490a19763f69a4ed88d15aacdfba853db8c040
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62856478"
---
# <a name="job-activity-monitor-refresh"></a>Aktualisieren des Auftragsaktivitätsmonitors
  Mithilfe des Dialogfelds **Aktualisierungseinstellungen** können Sie konfigurieren, wie oft durch den Auftragsaktivitätsmonitor neue Informationen zur Serveraktivität abgerufen werden. Der Auftragsaktivitätsmonitor muss Abfragen an die überwachten Server ausführen, um Informationen für das Raster des Auftragsaktivitätsmonitors zu erhalten. Wenn für das Intervall für die automatische Aktualisierung weniger als 30 Sekunden festgelegt ist, kann die für die Ausführung der Abfragen benötigte Zeit die Serverleistung beeinträchtigen.  
  
 Zum Öffnen dieses Dialogfelds klicken Sie im Abschnitt **Status**des Auftragsaktivitätsmonitors auf **Aktualisierungseinstellungen anzeigen** .  
  
## <a name="options"></a>Optionen  
 **Automatische Aktualisierung alle**  
 Wählen Sie diese Option, um die automatische Aktualisierung der Aktivitätsmonitorinformationen zu aktivieren. Standardmäßig ist die automatische Aktualisierung ausgeschaltet.  
  
 **Sekunden**  
 Anzahl der Sekunden zwischen den automatischen Aktualisierungsversuchen. Der Standardwert ist 60 Sekunden. Wenn der Wert auf 5 oder weniger festgelegt ist, erfolgt die Aktualisierung alle 5 Sekunden.  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen der Auftragsaktivität](../../ssms/agent/monitor-job-activity.md)  
  
  
