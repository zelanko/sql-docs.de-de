---
title: Modellberechtigungen (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: 733827ecace64ef86b54831f63fd8c2889203919
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65478965"
---
# <a name="model-permissions-master-data-services"></a>Modellberechtigungen (Master Data Services)
  Modellberechtigungen gelten für alle Entitäten, Attribute, abgeleiteten Hierarchien, expliziten Hierarchien und Auflistungen innerhalb des Modells. Dem Modell zugewiesene Berechtigungen können für beliebige einzelne Objekte überschrieben werden.  
  
> [!NOTE]  
>  Wenn ein Benutzer ein Modelladministrator ist, wird das Modell in allen Funktionsbereichen der Benutzeroberfläche angezeigt. Andernfalls wird das Modell nur im Funktionsbereich **Explorer** angezeigt. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
|Berechtigung|BESCHREIBUNG|  
|----------------|-----------------|  
|**Schreibgeschützt**|Im **Explorer**wird das Modell angezeigt, aber der Benutzer kann keine Elemente hinzufügen oder entfernen, und es können keine Attributwerte, Hierarchie Mitgliedschaften oder Sammlungs Mitgliedschaften aktualisiert werden.|  
|**Alisierungs**|Im **Explorer**wird das Modell angezeigt, und der Benutzer kann Elemente hinzufügen und entfernen, Attributwerte, Hierarchie Mitgliedschaften und Sammlungs Mitgliedschaften aktualisieren.|  
|**Deny**|Das Modell wird nicht angezeigt.|  
  
 Wenn Sie einem Modell eine Berechtigung zuweisen, erhält der Benutzer Zugriff auf alle Versionen des Modells. Sie können keine Berechtigung für eine einzelne Version zuweisen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zuweisen von Berechtigungen für Modell Objekte &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Modell Objekt Berechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Entitäts Berechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/entity-permissions-master-data-services.md)   
 [Sammlungs Berechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/collection-permissions-master-data-services.md)  
  
  
