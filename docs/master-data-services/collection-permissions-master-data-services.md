---
title: Auflistungsberechtigungen (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services], permissions
- permissions [Master Data Services], collections
ms.assetid: 703e1bf5-4b4b-4830-8a5b-f979b09f677d
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 81b56aa57aeb6dd1cb2b2063c41c2dc9ccd6fb19
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65484241"
---
# <a name="collection-permissions-master-data-services"></a>Auflistungsberechtigungen (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Auflistungsberechtigungen gelten für alle Auflistungen in einer Entität. Es kann keine Berechtigung für eine bestimmte Auflistung erteilt werden; Berechtigungen gelten für alle Auflistungen.  
  
> [!NOTE]  
>  Diese Berechtigungen gelten nur für den Funktionsbereich **Explorer** der Benutzeroberfläche.  
  
|Berechtigung|Description|  
|----------------|-----------------|  
|**Lesen**|Der Benutzer kann Elemente der Auflistung und die Elementattribute lesen.|  
|**Erstellen**|Der Benutzer kann Auflistungselemente erstellen und Attributwerte zuweisen.|  
|**Update**|Der Benutzer kann Auflistungselemente, Attribute und Beziehungen aktualisieren.|  
|**Delete**|Der Benutzer kann Elemente der Auflistung löschen.|  
|**Verweigern**|Jeglicher Zugriff auf die Elemente der Auflistung wird verweigert.|  
  
 Die Berechtigungen Lesen, Erstellen, Aktualisieren und Löschen können kombiniert werden. Wenn Erstellen, Aktualisieren und Löschen zugewiesen werden, wird die Leseberechtigung automatisch zugewiesen.  
  
## <a name="see-also"></a>Siehe auch  
 [Zuweisen von Berechtigungen für Modellobjekte &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Sammlungen &#40;Master Data Services&#41;](../master-data-services/collections-master-data-services.md)   
 [Berechtigungen für Modellobjekte &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)  
  
  
