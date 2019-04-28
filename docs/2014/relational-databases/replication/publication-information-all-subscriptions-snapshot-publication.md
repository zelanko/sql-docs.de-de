---
title: Veröffentlichungsinformationen, Alle Abonnements (Momentaufnahmeveröffentlichung) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.allsubscriptions.snapshot.f1
ms.assetid: 7ce656c2-6e60-4625-8955-1daff641070c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3665647e89c03b75230acf58d2f5193fceefe878
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63021828"
---
# <a name="publication-information-all-subscriptions-snapshot-publication"></a>Veröffentlichungsinformationen, Alle Abonnements (Momentaufnahmeveröffentlichung)
  Auf der Registerkarte **Alle Abonnements** werden Informationen zu allen Abonnements der ausgewählten Momentaufnahmeveröffentlichung angezeigt.  
  
## <a name="options"></a>Optionen  
 Ausführliche Informationen und eine Liste der Aufträge für ein Abonnement können Sie anzeigen, indem Sie mit der rechten Maustaste in die Zeile des jeweiligen Abonnements klicken und eine Option im Kontextmenü auswählen. Wenn Sie die Anzeige der Daten im Raster ändern möchten, klicken Sie mit der rechten Maustaste auf das Raster, und klicken Sie anschließend auf eine der folgenden Optionen:  
  
-   **Sortieren:** Sortieren Sie nach einer oder mehreren Spalten im Dialogfeld **Spalten sortieren**.  
  
-   **Anzuzeigende Spalten auswählen:** Wählen Sie die anzuzeigenden Spalten sowie die Reihenfolge aus, in der diese im Dialogfeld **Spalten auswählen** angezeigt werden sollen.  
  
-   **Filtern:** Filtern Sie Zeilen im Raster auf Grundlage der Spaltenwerte im Dialogfeld **Filtereinstellungen**.  
  
-   **Filter löschen:** Löschen Sie alle Filtereinstellungen für das Raster.  
  
 Filtereinstellungen sind rasterspezifisch. Die Spaltenauswahl und -sortierung wird auf alle Raster desselben Typs angewendet, z. B. das Veröffentlichungsraster für jeden Verleger.  
  
 **Anzeigen**  
 Nur in[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höheren Versionen. Wählen Sie die Abonnementstatus aus, die für Abonnements des ausgewählten Typs angezeigt werden sollen. Sie können z. B. auswählen, dass nur die Abonnements angezeigt werden, die einen Fehler aufweisen.  
  
 **Status**  
 Der Status jedes Abonnements, der vom Status des Momentaufnahme-Agents oder des Verteilungs-Agents bestimmt wird (der Status mit der höheren Priorität wird angezeigt).  
  
 Standardmäßig wird das Raster mit den Abonnementinformationen nach der **Status** -Spalte sortiert. In der folgenden Liste werden die möglichen Statuswerte und ihre Sortierreihenfolge aufgeführt (Fehler werden z. B. immer oben im Raster angezeigt).  
  
-   Fehler  
  
-   Läuft demnächst ab/Abgelaufen (nur in[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höheren Versionen)  
  
-   Nicht initialisiertes Abonnement (nur in[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höheren Versionen)  
  
-   fehlerhafter Befehl wird wiederholt  
  
-   Wird synchronisiert  
  
-   Synchronisierung wird nicht ausgeführt  
  
 Die Sortierreihenfolge bestimmt auch, welcher Wert angezeigt wird, wenn ein Abonnement mehr als einen Statuswert aufweist. Wenn ein Abonnement z. B. einen Fehler aufweist und bald abläuft, dann wird in der **Status** -Spalte der Eintrag **Fehler**angezeigt.  
  
 Die Statuswerte **Läuft demnächst ab/Abgelaufen** und **Nicht initialisiertes Abonnement** stellen Warnungen dar. Wenn eine Warnung angezeigt wird, wird unter **Status** auch angezeigt, ob ein Agent ausgeführt wird. Der Status kann beispielsweise **Wird ausgeführt, Läuft demnächst ab/Abgelaufen**lauten.  
  
 Der Statuswert **Läuft demnächst ab/Abgelaufen** wird nur angezeigt, wenn ein Schwellenwert festgelegt wird. Informationen zum Festlegen von Schwellenwerten finden Sie unter [Festlegen von Schwellenwerten und Warnungen im Replikationsmonitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
 **Abonnement**  
 Der Name des Abonnements im Format: *Abonnentenname: Name_der_Abonnentendatenbank*.  
  
 **Letzte Synchronisierung**  
 Der Zeitpunkt der letzten Ausführung des Verteilungs-Agents. Wenn eine Synchronisierung ausgeführt wird, wird **Vorgang wird ausgeführt** angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Starten des Replikationsmonitors](monitor/start-the-replication-monitor.md)   
 [View information and perform tasks using Replication Monitor (Anzeigen von Informationen und Ausführen von Aufgaben mit dem Replikationsmonitor)](monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Überwachen der Replikation](monitoring-replication.md)  
  
  
