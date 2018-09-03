---
title: Systemrolleneigenschaften (Management Studio) | Microsoft-Dokumentation
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: tools
ms.suite: pro-bi
ms.topic: conceptual
f1_keywords:
- sql13.swb.reportserver.systemroleproperties.f1
ms.assetid: 0210fc2a-74fb-41dd-8e39-4830047ec417
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 0d1fd1a96d3e472c01eb899c12976e0980fa2dff
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43276532"
---
# <a name="system-role-properties-management-studio"></a>Systemrolleneigenschaften (Management Studio)
  Mithilfe der Seite Systemrollen können Sie die Systemrollendefinitionen anzeigen, die aktuell für den Berichtsserver definiert sind. Eine Systemrollendefinition enthält eine benannte Auflistung von Aufgaben, die in Bezug auf die gesamte Site statt nur für ein einzelnes Element ausgeführt werden. Rollendefinitionen werden Benutzern oder Gruppen zugewiesen, um eine Rollenzuweisung zu erstellen. Die Aufgaben in der Rollendefinition geben die Aktionen an, die der Benutzer oder die Gruppe ausführen kann.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] besitzt zwei vordefinierte Systemrollendefinitionen: **Systemadministrator** und **Systembenutzer**. Sie können die Rollendefinitionen ändern, indem Sie ihre Aufgabenlisten ändern. Oder Sie erstellen eine neue Systemrolle, die eine andere Kombination von Aufgaben unterstützt. Die Bearbeitung einer Rollendefinition wirkt sich auf alle Rollenzuweisungen aus, die diese Rollendefinition enthalten.  
  
> [!NOTE]  
>  Systemrollenzuweisungen werden nur auf einem Berichtsserver verwendet, der im einheitlichen Modus ausgeführt wird. Ist der Berichtsserver für den integrierten SharePoint-Modus konfiguriert, ist diese Seite nicht verfügbar.  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Gibt den Namen der Systemrollendefinition an.  
  
 **Beschreibung**  
 Zeigt eine Beschreibung der Systemrollendefinition. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]wird diese Beschreibung nur auf dieser Seite angezeigt. Benutzer, die dieses Element über den Berichts-Manager anzeigen, sehen diese Beschreibung möglicherweise, wenn Sie die Ordnerhierarchie durchsuchen.  
  
 **Task**  
 Listet alle Tasks auf Systemebene auf, die für diese Rollendefinition ausgewählt werden können. Sie können in der vordefinierten Aufgabenliste Elemente hinzufügen oder löschen, um zu definieren, wie Benutzer über die Rolle auf ein bestimmtes Element zugreifen können. Sie können keine neuen Tasks erstellen oder vorhandene Tasks ändern.  
  
 **Beschreibung**  
 Bietet Informationen zu den einzelnen Tasks. Taskbeschreibungen können Sie nicht ändern.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Berichtsserver im Management Studio (F1-Hilfe)](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [Aufgaben auf Systemebene](../../reporting-services/security/tasks-and-permissions-system-level-tasks.md)   
 [Aufgaben und Berechtigungen](../../reporting-services/security/tasks-and-permissions.md)   
 [Vordefinierte Rollen](../../reporting-services/security/role-definitions-predefined-roles.md)  
  
  
