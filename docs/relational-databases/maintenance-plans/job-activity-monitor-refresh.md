---
description: Aktualisieren des Auftragsaktivitätsmonitors
title: Aktualisieren des Auftragsaktivitätsmonitors | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql13.swb.jobactivitymon.refresh.f1
ms.assetid: 413a368e-fd2b-4e1f-b370-002cdbc85bab
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 78141d10b6244308f075e420f1d1ea3501830286
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424042"
---
# <a name="job-activity-monitor-refresh"></a>Aktualisieren des Auftragsaktivitätsmonitors
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Mithilfe des Dialogfelds **Aktualisierungseinstellungen** können Sie konfigurieren, wie oft durch den Auftragsaktivitätsmonitor neue Informationen zur Serveraktivität abgerufen werden. Der Auftragsaktivitätsmonitor muss Abfragen an die überwachten Server ausführen, um Informationen für das Raster des Auftragsaktivitätsmonitors zu erhalten. Wenn für das Intervall für die automatische Aktualisierung weniger als 30 Sekunden festgelegt ist, kann die für die Ausführung der Abfragen benötigte Zeit die Serverleistung beeinträchtigen.  
  
 Zum Öffnen dieses Dialogfelds klicken Sie im Abschnitt **Status**des Auftragsaktivitätsmonitors auf **Aktualisierungseinstellungen anzeigen** .  
  
## <a name="options"></a>Tastatur  
 **Automatische Aktualisierung alle**  
 Wählen Sie diese Option, um die automatische Aktualisierung der Aktivitätsmonitorinformationen zu aktivieren. Standardmäßig ist die automatische Aktualisierung ausgeschaltet.  
  
 **Sekunden**  
 Anzahl der Sekunden zwischen den automatischen Aktualisierungsversuchen. Der Standardwert ist 60 Sekunden. Wenn der Wert auf 5 oder weniger festgelegt ist, erfolgt die Aktualisierung alle 5 Sekunden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der Auftragsaktivität](../../ssms/agent/monitor-job-activity.md)  
  
  
