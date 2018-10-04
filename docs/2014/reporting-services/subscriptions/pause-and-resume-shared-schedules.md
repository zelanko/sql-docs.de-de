---
title: Anhalten und Fortsetzen von freigegebenen Zeitplänen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- pausing schedules
- report-specific schedules [Reporting Services]
- shared schedules [Reporting Services], resuming
- resuming schedules
- continuing schedules
- schedules [Reporting Services], resuming
- schedules [Reporting Services], pausing
ms.assetid: e416be75-5234-4aa6-a3de-77f60f25169a
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: a35e16107d926bc9815e2e6de2d43a35172bd2e8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48070280"
---
# <a name="pause-and-resume-shared-schedules"></a>Anhalten und Fortsetzen von freigegebenen Zeitplänen
  Es besteht die Möglichkeit, einen verwendeten freigegebenen Zeitplan anzuhalten und fortzusetzen. Durch das Anhalten eines freigegebenen Zeitplans kann ein Zeitplan vorübergehend eingefroren werden, mit dem die Berichtsverarbeitung und Abonnements ausgelöst werden. Nur freigegebene Zeitpläne können angehalten und fortgesetzt werden. Berichtsspezifische Zeitpläne können nicht angehalten werden.  
  
 Eine gerade ausgeführte Berichtsverarbeitung kann nicht angehalten und fortgesetzt werden. Es können nur die Zeitpläne angehalten und fortgesetzt werden, die sich in der Zeitplanwarteschlange des SQL Server-Agent-Dienstes befinden. Auf einen Auftrag, der verarbeitet wird, hat die Zeitplanungs-Engine keinen Einfluss. Weitere Informationen finden Sie unter [Verwalten eines ausgeführten Prozesses](manage-a-running-process.md)  
  
 Während ein freigegebener Zeitplan angehalten wird, werden alle Vorgänge, die stattgefunden hätten, versäumt. Nachdem Sie einen freigegebenen Zeitplan fortsetzen, findet die Berichts- und Abonnementverarbeitung zum nächsten geplanten Zeitpunkt statt, wobei die Ortszeit des Servers verwendet wird. Der Berichtsserver im einheitlichen Modus oder SharePoint-Dienstanwendungen holen keine geplanten Vorgänge nach, die stattgefunden hätten, wenn der Zeitplan nicht angehalten worden wäre.  
  
 In diesem Thema:  
  
-   [Anhalten und Fortsetzen von freigegebenen Zeitplänen (einheitlicher Modus)](#bkmk_native)  
  
-   [Anhalten und Fortsetzen von freigegebenen Zeitplänen (SharePoint-Modus)](#bkmk_sharepoint)  
  
##  <a name="bkmk_native"></a> Anhalten und Fortsetzen von freigegebenen Zeitplänen (einheitlicher Modus)  
 Verwenden Sie die Seite "Zeitpläne" im Berichts-Manager zum Anhalten und Fortsetzen eines freigegebenen Zeitplans. Sie können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]nicht verwenden, da hier keine Optionen zum Anhalten und Fortsetzen von Zeitplänen zur Verfügung stehen. Weitere Informationen finden Sie unter [erstellen, ändern und Löschen von Zeitplänen](create-modify-and-delete-schedules.md).  
  
#### <a name="to-pause-or-resume-a-shared-schedule"></a>So halten Sie einen freigegebenen Zeitplan an oder setzen ihn fort  
  
1.  Klicken Sie im Berichts-Manager auf **Siteeinstellungen**.  
  
2.  Klicken Sie auf **Zeitpläne**.  
  
3.  Wählen Sie den Zeitplan aus, und klicken Sie im Menüband auf **Anhalten** oder **Fortsetzen** . Wenn ein Zeitplan derzeit angehalten wird, wird **Angehalten** in der Spalte **Status**angezeigt.  
  
##  <a name="bkmk_sharepoint"></a> Anhalten und Fortsetzen von freigegebenen Zeitplänen (SharePoint-Modus)  
 Verwenden Sie die Seite "Siteeinstellungen" oder PowerShell, um einen freigegebenen Zeitplan anzuhalten und fortzusetzen. Zeitpläne werden pro SharePoint-Website verwaltet.  
  
#### <a name="to-pause-or-resume-a-shared-schedule"></a>So halten Sie einen freigegebenen Zeitplan an oder setzen ihn fort  
  
1.  Klicken Sie auf **Websiteaktionen**.  
  
2.  Klicken Sie auf **Siteeinstellungen**.  
  
3.  Klicken Sie im Abschnitt **Reporting Services**auf Freigegebene Zeitpläne verwalten.  
  
4.  Wählen Sie den Zeitplan aus, und klicken Sie auf **Ausgewählte Zeitpläne anhalten** oder **Ausgewählte Zeitpläne ausführen**. Wenn ein Zeitplan derzeit angehalten wird, wird **Angehalten** in der Spalte **Status**angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Zeitpläne](schedules.md)   
 [Erstellen, Ändern oder Löschen von Zeitplänen](create-modify-and-delete-schedules.md)   
 [Change Time Zones and Clock Settings on a Report Server (Ändern von Zeitzonen und Systemuhreinstellungen auf einem Berichtsserver)](change-time-zones-and-clock-settings-on-a-report-server.md)   
 [Verwalten eines ausgeführten Prozesses](manage-a-running-process.md)  
  
  
