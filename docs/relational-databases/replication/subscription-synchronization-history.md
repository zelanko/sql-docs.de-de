---
description: Abonnement, Synchronisierungsverlauf
title: Abonnement, Synchronisierungsverlauf | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.subscription.synchhistory.f1
- sql13.rep.monitor.subscription.downlevelsynchhistory.f1
ms.assetid: 85f666f6-14ee-4f19-b385-e5cc508aabe4
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: db40c8e3848ee5dac3d770e77629555ea87814b3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88326018"
---
# <a name="subscription-synchronization-history"></a>Abonnement, Synchronisierungsverlauf
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
   Die Registerkarte **Synchronisierungsverlauf** zeigt detaillierte Informationen zum Merge-Agent an, u. a. Status, Verlauf, Informationsmeldungen und alle Fehlermeldungen.  
  
## <a name="options"></a>Optionen  
 Wählen Sie im Menü **Sicht** aus, welche Sitzungen des Merge-Agents angezeigt werden, und wählen Sie dann eine bestimmte Sitzung aus dem Raster mit der Bezeichnung **Sitzungen des Merge-Agents**aus. Detaillierte Informationen zu dieser Sitzung werden im Raster mit der Bezeichnung **In der ausgewählten Sitzung verarbeitete Artikel**angezeigt.  
  
 **Ansicht**  
 Wählen Sie aus, welche Sitzungen des Merge-Agents angezeigt werden.  
  
 **Status**  
 Der Status des Merge-Agents am Ende der Sitzung. In der folgenden Liste sind die möglichen Statuswerte aufgeführt:  
  
-   Fehler  
  
-   Abgeschlossen  
  
-   Wird wiederholt  
  
-   Wird ausgeführt  
  
 **Startzeit**  
 Startzeit der Sitzung.  
  
 **Endzeit**  
 Beendigungszeit der Sitzung. Wenn der Agent noch nicht beendet wurde, ist dieses Feld leer.  
  
 **Duration**  
 Die Zeitspanne, für die der Merge-Agent in einer Sitzung ausgeführt wurde. Dieser Wert gibt entweder die verstrichene Zeit eines zurzeit ausgeführten Agents oder die Gesamtzeit des zuvor ausgeführten Agents an.  
  
 **Hochgeladene Befehle**  
 Die Anzahl der während der Merge-Agentsitzung hochgeladenen Zeilen.  
  
 **Heruntergeladene Befehle**  
 Die Anzahl der während der Merge-Agentsitzung heruntergeladenen Zeilen.  
  
 **Fehlermeldung**  
 Wenn eine Sitzung mit einem Fehler beendet wurde, wird in diesem Feld die Fehlermeldung angezeigt, die vom Merge-Agent zuletzt protokolliert wurde. Wurde die Sitzung nicht mit einem Fehler beendet, ist dieses Feld leer.  
  
 **Artikel**  
 Die Namen der einzelnen Artikel der Veröffentlichung und die folgenden Verarbeitungsphasen für die gesamte Veröffentlichung:  
  
-   **Initialisierung**. Bezieht sich auf den Start des Merge-Agents und ist damit nicht gleichbedeutend mit der Initialisierung eines Abonnements, bei der auch eine Momentaufnahme angewendet wird.  
  
-   **Schemaänderungen und Masseneinfügungen**.  
  
-   **Änderungen auf den Verleger hochladen**.  
  
-   **Änderungen auf den Abonnenten herunterladen**.  
  
 Die Phasen werden eingeschlossen, damit im Raster die Werte für die Zeitdauer und der prozentuale Anteil an der Gesamtzeit angezeigt werden können, die in der ausgewählten Sitzung von den einzelnen Phasen beansprucht wird.  
  
 **% von Gesamt**  
 Der prozentuale Anteil, den die einzelnen Phasen in der ausgewählten Sitzung von der Gesamtverarbeitungszeit beanspruchen.  
  
 **Duration**  
 Die Zeitdauer, die für die einzelnen Verarbeitungsphasen beansprucht wird. Dieser Wert gibt entweder die verstrichene Zeit eines zurzeit ausgeführten Merge-Agents oder die Gesamtzeit des zuvor ausgeführten Merge-Agents an.  
  
 **Inserts**  
 Die Anzahl der in dieser Phase der ausgewählten Sitzung eingefügten Zeilen.  
  
 **Updates**  
 Die Anzahl der in dieser Phase der ausgewählten Sitzung aktualisierten Zeilen.  
  
 **Löschvorgang**  
 Die Anzahl der in dieser Phase der ausgewählten Sitzung gelöschten Zeilen.  
  
 **Konflikte**  
 Die Anzahl der Konflikte in der ausgewählten Sitzung.  
  
 **Schemaänderungen**  
 Die Anzahl der Schemaänderungen in der ausgewählten Sitzung. Schemaänderungen können auf von der Veröffentlichungsdatenbank replizierte Schemaänderungen, das Hinzufügen oder Löschen von Artikeln oder Änderungen an Artikel- oder Veröffentlichungseigenschaften zurückzuführen sein.  
  
 **Letzte Meldung der ausgewählten Sitzung**  
 In diesem Textbereich wird die letzte Meldung in der ausgewählten Sitzung angezeigt. Wenn ein Fehler aufgetreten ist, werden detaillierte Informationen zu dem Fehler und der Befehl angezeigt, der zum Fehlerzeitpunkt auszuführen versucht wurde. Er enthält außerdem Links zu weiteren Informationen, die sich auf den Fehler beziehen.  
  
## <a name="see-also"></a>Siehe auch  
 [Starten des Replikationsmonitors](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [View information and perform tasks using Replication Monitor (Anzeigen von Informationen und Ausführen von Aufgaben mit dem Replikationsmonitor)](../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Überwachen der Replikation](../../relational-databases/replication/monitor/monitoring-replication.md)   
 [Übersicht über Replikations-Agents](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  
