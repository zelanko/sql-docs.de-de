---
title: Konsolidierte Berechtigungen (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], consolidated member attribute permissions
- consolidated members [Master Data Services], attribute permissions
- permissions [Master Data Services], consolidated members
- members [Master Data Services], consolidated member permissions
ms.assetid: 084055a3-5fd3-43f3-b620-ac6afab42a3d
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6fbc636a4dcf67b6bdeaa17088405ffe079e50d9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48096960"
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
 [Blattberechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md)   
 [Berechtigungen für Modellobjekte &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Elemente &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md)   
 [Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
