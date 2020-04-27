---
title: Angeben von Auftragsantworten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], responses
- SQL Server Agent jobs, responses
- actions [SQL Server Agent jobs]
- responding to jobs
ms.assetid: 050242e1-9b79-4ade-91a9-580707b9d2d9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9fa238a639321e9464ca3de2cc074b516f7df1e1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63245996"
---
# <a name="specify-job-responses"></a>Angeben von Auftragsantworten
  Auftragsantworten geben Aktionen an, die der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst nach Abschluss eines Auftrags ausführt. Sie stellen sicher, dass Datenbankadministratoren wissen, wann Aufträge fertig gestellt sind und wie oft diese ausgeführt werden. Zu den typischen Auftragsantworten gehören folgende:  
  
-   Benachrichtigen des Operators per E-Mail, Pager oder **NET SEND** -Nachricht.  
  
     Verwenden Sie eine dieser Auftragsantworten vor allem dann, wenn der Operator weitere Schritte ausführen muss. Wenn beispielsweise ein Sicherungsauftrag erfolgreich ausgeführt wurde, muss der Operator darüber informiert werden, um das Sicherungsband entfernen zu können und an einem sicheren Standort aufbewahren zu lassen.  
  
-   Schreiben einer Ereignismeldung in das Windows-Anwendungsprotokoll.  
  
     Diese Art der Antwort können Sie nur bei fehlgeschlagenen Aufträgen verwenden.  
  
-   Automatisches Löschen des Auftrags.  
  
     Verwenden Sie diese Auftragsantwort, wenn Sie sicher sind, dass Sie diesen Auftrag nicht erneut ausführen müssen.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|||  
|-|-|  
|**Beschreibung**|**Sonder**|  
|Beschreibt, wie ein Operator über den Auftragsstatus benachrichtigt wird.|[Notify an Operator of Job Status](notify-an-operator-of-job-status.md)|  
|Beschreibt, wie der Auftragsstatus in das Windows-Anwendungsprotokoll ausgegeben wird.|[Write the Job Status to the Windows Application Log](../../reporting-services/report-server/windows-application-log.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen und Reagieren auf Ereignisse](monitor-and-respond-to-events.md)  
  
  
