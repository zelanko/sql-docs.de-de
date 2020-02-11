---
title: Systemrolleneigenschaften (Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.systemroleproperties.f1
ms.assetid: 0210fc2a-74fb-41dd-8e39-4830047ec417
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d64c8e0fc4281a5e2f8767a303b1ee1009ee76b8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66099459"
---
# <a name="system-role-properties-management-studio"></a>Systemrolleneigenschaften (Management Studio)
  Mithilfe der Seite Systemrollen können Sie die Systemrollendefinitionen anzeigen, die aktuell für den Berichtsserver definiert sind. Eine Systemrollendefinition enthält eine benannte Auflistung von Aufgaben, die in Bezug auf die gesamte Site statt nur für ein einzelnes Element ausgeführt werden. Rollendefinitionen werden Benutzern oder Gruppen zugewiesen, um eine Rollenzuweisung zu erstellen. Die Aufgaben in der Rollendefinition geben die Aktionen an, die der Benutzer oder die Gruppe ausführen kann.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]verfügt über zwei vordefinierte System Rollen Definitionen: **System Administrator** und **Systembenutzer**. Sie können die Rollendefinitionen ändern, indem Sie ihre Aufgabenlisten ändern. Oder Sie erstellen eine neue Systemrolle, die eine andere Kombination von Aufgaben unterstützt. Die Bearbeitung einer Rollendefinition wirkt sich auf alle Rollenzuweisungen aus, die diese Rollendefinition enthalten.  
  
> [!NOTE]  
>  Systemrollenzuweisungen werden nur auf einem Berichtsserver verwendet, der im einheitlichen Modus ausgeführt wird. Ist der Berichtsserver für den integrierten SharePoint-Modus konfiguriert, ist diese Seite nicht verfügbar.  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Gibt den Namen der Systemrollendefinition an.  
  
 **Beschreibung**  
 Zeigt eine Beschreibung der Systemrollendefinition. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]wird diese Beschreibung nur auf dieser Seite angezeigt. Benutzer, die dieses Element über den Berichts-Manager anzeigen, sehen diese Beschreibung möglicherweise, wenn Sie die Ordnerhierarchie durchsuchen.  
  
 **Aufgabe**  
 Listet alle Tasks auf Systemebene auf, die für diese Rollendefinition ausgewählt werden können. Sie können in der vordefinierten Aufgabenliste Elemente hinzufügen oder löschen, um zu definieren, wie Benutzer über die Rolle auf ein bestimmtes Element zugreifen können. Sie können keine neuen Tasks erstellen oder vorhandene Tasks ändern.  
  
 **Beschreibung**  
 Bietet Informationen zu den einzelnen Tasks. Taskbeschreibungen können Sie nicht ändern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichtsserver im Management Studio (F1-Hilfe)](report-server-in-management-studio-f1-help.md)   
 [Aufgaben auf System Ebene](../security/tasks-and-permissions-system-level-tasks.md)   
 [Aufgaben und Berechtigungen](../security/tasks-and-permissions.md)   
 [Vordefinierte Rollen](../security/role-definitions-predefined-roles.md)  
  
  
