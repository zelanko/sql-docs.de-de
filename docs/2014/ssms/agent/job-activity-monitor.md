---
title: Auftragsaktivitätsmonitor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.ACTIVITYMON.F1
- sql12.ag.jobactivitymonitor.alljobs.f1
ms.assetid: 11f2182c-5f71-46f8-8d2b-74f0fc48f2d6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 58f04e83541f218a4cdcfbd99d6b3de12bf38b2f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85064981"
---
# <a name="job-activity-monitor"></a>Auftragsaktivitätsmonitor
  Mithilfe dieser Seite können Sie die aktuelle Aktivität von Aufträgen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents anzeigen. Klicken Sie auf **Filter** , um die Anzahl der angezeigten Aufträge zu beschränken. Das Raster **Agentauftragsaktivität** ist schreibgeschützt. Klicken Sie auf die Spaltenheader, um das Raster zu sortieren. Sie können einen Auftrag ändern, indem Sie auf den betreffenden Auftrag doppelklicken und das Dialogfeld **Auftragseigenschaften** öffnen. Klicken Sie mit der rechten Maustaste auf einen Auftrag im Raster, um die Ausführung aller Auftragsschritte zu starten, einen speziellen Auftragsschritt zu starten, den Auftrag zu aktivieren oder zu deaktivieren, den Auftrag zu aktualisieren, den Auftrag zu löschen, den Verlauf des Auftrags anzuzeigen oder die Auftragseigenschaften anzuzeigen. Klicken Sie auf **Aktualisieren** , um das Raster mit den aktuellen Informationen zu aktualisieren.  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Der Name des Auftrags.  
  
 **Aktiviert**  
 Zeigt an, ob der Auftrag aktiviert (**Ja**) oder nicht aktiviert (**Nein**) ist.  
  
 **Status** <sup>1</sup>  
 Aktueller Status des Auftrags  
  
 **Ergebnis der letzten Ausführung**  
 Auftragsstatus bei der letzten Ausführung  
  
 **Zuletzt ausgeführt**  
 Datum und Uhrzeit, an dem bzw. zu der der Auftrag zuletzt ausgeführt wurde (ausgehend vom lokalen Datum und der lokalen Uhrzeit des Servers).  
  
 **Nächste ausführen** <sup>1</sup>  
 Datum und Uhrzeit des Zeitpunkts, an dem die nächste Ausführung des Auftrags geplant ist (ausgehend vom lokalen Datum und der lokalen Uhrzeit des Servers).  
  
 **Kategorie**  
 Die dem Auftrag zugewiesene Auftragskategorie.  
  
 **Ausführbar**  
 **Ja** , wenn der Auftrag ausgeführt werden kann; **Nein** , wenn der Auftrag nicht ausgeführt werden kann. Ein Auftrag kann nicht ausgeführt werden, wenn er keine Schritte oder keinen Zielserver aufweist.  
  
 **Scheduled**  
 **Ja** , wenn der Auftrag einem Auftragszeitplan zugewiesen ist; **Nein** , wenn für den Auftrag kein Zeitplan vorhanden ist.  
  
 <sup>1</sup> Nur Mitglieder der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] festen Server Rolle sysadmin und der Server Administrator Gruppe können Werte in dieser Spalte sehen. Mitglieder der SQLAgentOperatorRole-Rolle können keine Werte in dieser Spalte sehen.  
  
#### <a name="to-open-the-job-activity-monitor"></a>So öffnen Sie den Auftragsaktivitätsmonitor  
  
-   Erweitern Sie in **Objekt-Explorer**den verwendeten Server und anschließend **SQL Server-Agent**. Klicken Sie mit der rechten Maustaste auf **Auftragsaktivitätsmonitor**, und klicken Sie dann auf **Auftragsaktivitäten anzeigen**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der Auftragsaktivität](monitor-job-activity.md)  
  
  
