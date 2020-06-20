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
ms.openlocfilehash: 2846918b515bba16d12d48cd7058cf25863bf569
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971180"
---
# <a name="model-permissions-master-data-services"></a>Modellberechtigungen (Master Data Services)
  Modellberechtigungen gelten für alle Entitäten, Attribute, abgeleiteten Hierarchien, expliziten Hierarchien und Auflistungen innerhalb des Modells. Dem Modell zugewiesene Berechtigungen können für beliebige einzelne Objekte überschrieben werden.  
  
> [!NOTE]  
>  Wenn ein Benutzer ein Modelladministrator ist, wird das Modell in allen Funktionsbereichen der Benutzeroberfläche angezeigt. Andernfalls wird das Modell nur im Funktionsbereich **Explorer** angezeigt. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
|Berechtigung|BESCHREIBUNG|  
|----------------|-----------------|  
|**Schreibgeschützt**|Im **Explorer**wird das Modell angezeigt, aber der Benutzer kann keine Elemente hinzufügen oder entfernen, und es können keine Attributwerte, Hierarchie Mitgliedschaften oder Sammlungs Mitgliedschaften aktualisiert werden.|  
|**Update**|Im **Explorer**wird das Modell angezeigt, und der Benutzer kann Elemente hinzufügen und entfernen, Attributwerte, Hierarchie Mitgliedschaften und Sammlungs Mitgliedschaften aktualisieren.|  
|**Deny**|Das Modell wird nicht angezeigt.|  
  
 Wenn Sie einem Modell eine Berechtigung zuweisen, erhält der Benutzer Zugriff auf alle Versionen des Modells. Sie können keine Berechtigung für eine einzelne Version zuweisen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zuweisen von Berechtigungen für Modell Objekte &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Modell Objekt Berechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Entitäts Berechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/entity-permissions-master-data-services.md)   
 [Sammlungsberechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/collection-permissions-master-data-services.md)  
  
  
