---
title: Blattberechtigungen (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attribute groups [Master Data Services], permissions
- members [Master Data Services], leaf member permissions
- permissions [Master Data Services], leaf members
- leaf members [Master Data Services], attribute permissions
- attributes [Master Data Services], leaf member attribute permissions
ms.assetid: bde16e8c-bcd4-4041-8130-55c5450e5f72
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bf091886adb0a7fe484b2b62f44eb51b6c58d8bc
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971270"
---
# <a name="leaf-permissions-master-data-services"></a>Blattberechtigungen (Master Data Services)
  Blattberechtigungen gelten für die Attributwerte aller Blattelemente einer Entität.  
  
 Bei Entitäten, für die keine expliziten Hierarchien aktiviert wurden, erfolgen die Zuweisung einer Berechtigung zu einem **Blatt** und die Zuweisung einer Berechtigung zur Entität auf die gleiche Weise.  
  
 **Hinweise:**  
  
-   Blattberechtigungen gelten nur für den Funktionsbereich **Explorer** der Benutzeroberfläche.  
  
-   Den Attributen **Name** und **Code** zugewiesene Berechtigungen werden nicht erzwungen.  
  
|Berechtigung|BESCHREIBUNG|  
|----------------|-----------------|  
|**Schreibgeschützt**|Blattelemente werden zwar angezeigt, können vom Benutzer jedoch nicht hinzufügt, entfernt oder geändert werden.<br /><br /> Wenn konsolidierte Elemente vorhanden sind, werden die Namen und Codes zwar angezeigt, können vom Benutzer jedoch nicht hinzufügt, entfernt oder geändert werden.|  
|**Update**|Blattelemente werden angezeigt und können vom Benutzer hinzugefügt, entfernt und geändert werden.<br /><br /> Wenn konsolidierte Elemente vorhanden sind, werden die Namen und Codes zwar angezeigt, können vom Benutzer jedoch nicht hinzufügt, entfernt oder geändert werden.|  
|**Deny**|Blattelemente für die Entität werden nicht angezeigt.|  
  
## <a name="attribute-permissions"></a>Attributberechtigungen  
 Attributberechtigungen gelten für die Attributwerte der jeweiligen Entität. Benutzer mit Attributberechtigungen wird lediglich verweigert, Elemente hinzuzufügen oder zu entfernen.  
  
|Berechtigung|BESCHREIBUNG|  
|----------------|-----------------|  
|**Schreibgeschützt**|Das Attribut wird zwar angezeigt, aber der Benutzer kann keine Attributwerte ändern.|  
|**Update**|Das Attribut wird angezeigt, und der Benutzer kann Attributwerte ändern.|  
|**Deny**|Das Attribut wird nicht angezeigt.<br /><br /> Hinweis: Der Zugriff auf die Attribute Name und Code kann nicht explizit verweigert werden.|  
  
### <a name="example"></a>Beispiel  
 Weisen Sie dem Attribut „Subcategory“ der Entität „Product“ die Berechtigung **Aktualisieren** zu. Verweigern Sie die Berechtigung für alle anderen Attribute.  
  
|Name|Code|Subcategory (Aktualisiert)|  
|----------|----------|----------------------------|  
|Mountain-100|BK-M101|{5}Mountain Bikes|  
|Mountain-100|BK-M201|{5}Mountain Bikes|  
  
 Sie können im **Explorer**jeden Attributwert in der Spalte „Subcategory“ aktualisieren. Wenn Sie keine Berechtigung für ein Attribut haben, wird das Attribut nicht angezeigt.  
  
> [!NOTE]  
>  In diesem Beispiel ist Subcategory ein domänenbasiertes Attribut, das auf der SubcategoryList-Entität basiert. Sie können eine andere Unterkategorie für Mountain-100 auswählen, der SubcategoryList-Entität jedoch keine Elemente hinzufügen bzw. Elemente aus dieser Entität löschen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zuweisen von Berechtigungen für Modell Objekte &#40;Master Data Services&#41;](assign-model-object-permissions-master-data-services.md)   
 [Konsolidierte Berechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-permissions-master-data-services.md)   
 [Modell Objekt Berechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Mitglieder &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md)   
 [Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
