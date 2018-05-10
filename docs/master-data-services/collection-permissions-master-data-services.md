---
title: Auflistungsberechtigungen (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services], permissions
- permissions [Master Data Services], collections
ms.assetid: 703e1bf5-4b4b-4830-8a5b-f979b09f677d
caps.latest.revision: 6
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: bd95459436787b679fd68b9a98a0df40d9e3bb50
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
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
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Zuweisen von Berechtigungen für Modellobjekte &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Sammlungen &#40;Master Data Services&#41;](../master-data-services/collections-master-data-services.md)   
 [Berechtigungen für Modellobjekte &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)  
  
  
