---
title: Modellberechtigungen (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], permissions
- permissions [Master Data Services], models
ms.assetid: 210f440b-2cc1-4c49-94b1-3a97e2af7bc3
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 1f42513c7f8fa52fddfa9d3f77f537d81a34c0bc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65484082"
---
# <a name="model-permissions-master-data-services"></a>Modellberechtigungen (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Modellberechtigungen gelten für alle Entitäten, Attribute, abgeleiteten Hierarchien, expliziten Hierarchien und Auflistungen innerhalb des Modells. Dem Modell zugewiesene Berechtigungen können für beliebige einzelne Objekte überschrieben werden.  
  
> [!NOTE]  
>  Wenn ein Benutzer ein Modelladministrator ist, wird das Modell in allen Funktionsbereichen der Benutzeroberfläche angezeigt. Andernfalls wird das Modell nur im Funktionsbereich **Explorer** angezeigt. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)zuzugreifen.  
  
|Berechtigung|Description|  
|----------------|-----------------|  
|**Lesen**|Der Benutzer kann Elemente, Attribute, Hierarchiemitgliedschaften oder Sammlungszugehörigkeiten anzeigen.|  
|**Erstellen**|Der Benutzer kann Elemente erstellen und während der Erstellung Attributwerte zuweisen.|  
|**Update**|Der Benutzer kann Elemente, Attribute, Hierarchiemitgliedschaften oder Sammlungszugehörigkeiten aktualisieren.|  
|**Löschen**|Der Benutzer kann Elemente löschen.|  
|**Verweigern**|Der Zugriff auf das Modell wird vollständig verweigert.|  
|**Admin**|Administratorberechtigung für das Modell. Die Administratorberechtigung ist nur auf Modellebene verfügbar.|  
  
 Die Berechtigungen zum Lesen, Erstellen, Aktualisieren und Löschen können miteinander kombiniert werden. Wenn Berechtigungen zum Erstellen, Aktualisieren und Löschen zugewiesen werden, wird die Leseberechtigung automatisch zugewiesen.  
  
## <a name="see-also"></a>Siehe auch  
 [Zuweisen von Berechtigungen für Modellobjekte &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Berechtigungen für Modellobjekte &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [Entitätsberechtigungen &#40;Master Data Services&#41;](../master-data-services/entity-permissions-master-data-services.md)   
 [Sammlungsberechtigungen &#40;Master Data Services&#41;](../master-data-services/collection-permissions-master-data-services.md)  
  
  
