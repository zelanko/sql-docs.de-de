---
description: 'Aufgaben und Berechtigungen: Aufgaben auf Systemebene'
title: Aufgaben auf Systemebene | Microsoft-Dokumentation
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- system-level tasks [Reporting Services]
ms.assetid: 7023b388-40b2-4590-b227-115cf380a1e7
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 817c695a88cd40e761e5da807856d03658e05022
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88497976"
---
# <a name="tasks-and-permissions---system-level-tasks"></a>Aufgaben und Berechtigungen: Aufgaben auf Systemebene
  Eine Aufgabe auf Systemebene ist eine Auflistung von Berechtigungen im Hinblick auf Vorgänge, die die Berichtsserversite insgesamt betreffen. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enthält auch Aufgaben auf Elementebene, die sich auf bestimmte Elemente beziehen. Weitere Informationen finden Sie unter [Aufgaben auf Elementebene](../../reporting-services/security/tasks-and-permissions-item-level-tasks.md). Weitere Informationen zu Aufgaben und Berechtigungen im Allgemeinen finden Sie unter [Tasks and Permissions](../../reporting-services/security/tasks-and-permissions.md).  
  
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
|Verwalten von Rollen|Erstellen von Rollen<br /><br /> Löschen von Rollen<br /><br /> Lesen von Rolleneigenschaften<br /><br /> Aktualisieren von Rolleneigenschaften|  
|Freigegebene Zeitpläne verwalten|Erstellen von Zeitplänen|  
|Berichtsserversicherheit verwalten|Lesen von Systemsicherheitsrichtlinien<br /><br /> Aktualisieren von Systemsicherheitsrichtlinien|  
|Berichtsservereigenschaften anzeigen|Lesen von Systemeigenschaften|  
|Freigegebene Zeitpläne anzeigen|Lesen von Zeitplänen|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Granting Permissions on a Native Mode Report Server (Erteilen von Berechtigungen für einen Berichtsserver im einheitlichen Modus)](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)  
  
  
