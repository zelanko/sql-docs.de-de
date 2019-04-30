---
title: Aufgaben auf Systemebene | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- system-level tasks [Reporting Services]
ms.assetid: 7023b388-40b2-4590-b227-115cf380a1e7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b84e669f1a3621671bb476f8bc96fa68e36f7ae6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63306287"
---
# <a name="system-level-tasks"></a>Aufgaben auf Systemebene
  Eine Aufgabe auf Systemebene ist eine Auflistung von Berechtigungen im Hinblick auf Vorgänge, die die Berichtsserversite insgesamt betreffen. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enthält auch Aufgaben auf Elementebene, die sich auf bestimmte Elemente beziehen. Weitere Informationen finden Sie unter [Aufgaben auf Elementebene](tasks-and-permissions-item-level-tasks.md). Weitere Informationen zu Aufgaben und Berechtigungen im Allgemeinen finden Sie unter [Tasks and Permissions](tasks-and-permissions.md).  
  
> [!NOTE]  
>  Wenn Sie mit diesen Aufgaben programmgesteuert arbeiten, müssen Sie Methoden verwenden, die Aufgaben auf Systemebene unterstützen. Weitere Informationen finden Sie unter <xref:ReportService2010.ReportingService2010.ListTasks%2A> und <xref:ReportService2010.ReportingService2010.ListRoles%2A>.  
  
## <a name="permissions-in-system-level-tasks"></a>Berechtigungen für Aufgaben auf Systemebene  
 In der folgenden Tabelle sind die Berechtigungsarten für jede Systemaufgabe aufgeführt. Die Berechtigungsarten sind nur zu Informationszwecken aufgeführt, um eine genauere Beschreibung der über die verschiedenen Aufgaben verfügbaren Funktionalität bereitzustellen.  
  
|Aufgabe|Berechtigungen|  
|----------|-----------------|  
|Berichtsdefinitionen ausführen|Berichtsdefinitionen ausführen (Berechtigungs- und Aufgabenname sind identisch)|  
|Ereignisse generieren|Ereignisse generieren|  
|Aufträge verwalten|Lesen von Systemeigenschaften<br /><br /> Aktualisieren von Systemeigenschaften|  
|Berichtsservereigenschaften verwalten|Lesen von Systemeigenschaften<br /><br /> Aktualisieren von Systemeigenschaften|  
|Rollen verwalten|Erstellen von Rollen<br /><br /> Löschen von Rollen<br /><br /> Lesen von Rolleneigenschaften<br /><br /> Aktualisieren von Rolleneigenschaften|  
|Freigegebene Zeitpläne verwalten|Erstellen von Zeitplänen|  
|Berichtsserversicherheit verwalten|Lesen von Systemsicherheitsrichtlinien<br /><br /> Aktualisieren von Systemsicherheitsrichtlinien|  
|Berichtsservereigenschaften anzeigen|Lesen von Systemeigenschaften|  
|Freigegebene Zeitpläne anzeigen|Lesen von Zeitplänen|  
  
## <a name="see-also"></a>Siehe auch  
 [Granting Permissions on a Native Mode Report Server (Erteilen von Berechtigungen für einen Berichtsserver im einheitlichen Modus)](granting-permissions-on-a-native-mode-report-server.md)  
  
  
