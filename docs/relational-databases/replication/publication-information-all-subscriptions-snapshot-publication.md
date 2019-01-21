---
title: Veröffentlichungsinformationen, Alle Abonnements (Momentaufnahmeveröffentlichung) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.publicationinfo.allsubscriptions.snapshot.f1
ms.assetid: 7ce656c2-6e60-4625-8955-1daff641070c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 761fc300a7e7b8a47bed6830713ba87b6d755f1b
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54127830"
---
# <a name="publication-information-all-subscriptions-snapshot-publication"></a>Veröffentlichungsinformationen, Alle Abonnements (Momentaufnahmeveröffentlichung)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Auf der Registerkarte **Alle Abonnements** werden Informationen zu allen Abonnements der ausgewählten Momentaufnahmeveröffentlichung angezeigt.  
  
## <a name="options"></a>enthalten  
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
  
 Der Statuswert **Läuft demnächst ab/Abgelaufen** wird nur angezeigt, wenn ein Schwellenwert festgelegt wird. Informationen zum Festlegen von Schwellenwerten finden Sie unter [Festlegen von Schwellenwerten und Warnungen im Replikationsmonitor](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
 **Abonnement**  
 Der Name des Abonnements im Format: *Abonnentenname: Name_der_Abonnentendatenbank*.  
  
 **Letzte Synchronisierung**  
 Der Zeitpunkt der letzten Ausführung des Verteilungs-Agents. Wenn eine Synchronisierung ausgeführt wird, wird **Vorgang wird ausgeführt** angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten des Replikationsmonitors](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [View information and perform tasks using Replication Monitor (Anzeigen von Informationen und Ausführen von Aufgaben mit dem Replikationsmonitor)](../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Überwachen der Replikation](../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
