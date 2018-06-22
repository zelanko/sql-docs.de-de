---
title: Konsolidierte Berechtigungen (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [Master Data Services], consolidated member attribute permissions
- consolidated members [Master Data Services], attribute permissions
- permissions [Master Data Services], consolidated members
- members [Master Data Services], consolidated member permissions
ms.assetid: 084055a3-5fd3-43f3-b620-ac6afab42a3d
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: a0436df9a9aa4f21d9a581172e2874ca2dad6aa6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148152"
---
# <a name="consolidated-permissions-master-data-services"></a>Konsolidierte Berechtigungen (Master Data Services)
  Konsolidierte Berechtigungen beziehen sich auf die Attributwerte für alle konsolidierten Elemente einer Entität.  
  
 Konsolidierte Berechtigungen gelten nur für Entitäten, die für explizite Hierarchien und Auflistungen aktiviert sind.  
  
 **Hinweise:**  
  
-   Blattberechtigungen gelten nur für den Funktionsbereich **Explorer** der Benutzeroberfläche.  
  
-   Den Attributen **Name** und **Code** zugewiesene Berechtigungen werden nicht erzwungen.  
  
|Berechtigung|Description|  
|----------------|-----------------|  
|**Schreibgeschützt**|Konsolidierte Elemente werden zwar angezeigt, Benutzer können jedoch keine Elemente hinzufügen, entfernen oder ändern.|  
|**Update**|Konsolidierte Elemente werden angezeigt und können vom Benutzer hinzugefügt, entfernt und geändert werden.|  
|**Verweigern**|Konsolidierte Elemente für die Entität werden nicht angezeigt.|  
  
## <a name="attribute-permissions"></a>Attributberechtigungen  
 Attributberechtigungen gelten für die Attributwerte der jeweiligen Entität. Benutzer, die nur über Attributberechtigungen verfügen, können keine Elemente hinzufügen oder entfernen.  
  
|Berechtigung|Description|  
|----------------|-----------------|  
|**Schreibgeschützt**|Das Attribut wird zwar angezeigt, aber der Benutzer kann keine Attributwerte ändern.|  
|**Update**|Das Attribut wird angezeigt, und der Benutzer kann Attributwerte ändern.|  
|**Verweigern**|Das Attribut wird nicht angezeigt.<br /><br /> Hinweis: Der Zugriff auf die Attribute Name und Code kann nicht explizit verweigert werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Zuweisen von Berechtigungen für Modellobjekte &#40;Master Data Services&#41;](assign-model-object-permissions-master-data-services.md)   
 [Blattelemente Berechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md)   
 [Modellobjektberechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Elemente &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md)   
 [Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)  
  
  