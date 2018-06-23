---
title: Blattberechtigungen (Master Data Services) | Microsoft-Dokumentation
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
- attribute groups [Master Data Services], permissions
- members [Master Data Services], leaf member permissions
- permissions [Master Data Services], leaf members
- leaf members [Master Data Services], attribute permissions
- attributes [Master Data Services], leaf member attribute permissions
ms.assetid: bde16e8c-bcd4-4041-8130-55c5450e5f72
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: e6487c15c05fa157afdb8e644ead2f692e35f6ee
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151379"
---
# <a name="leaf-permissions-master-data-services"></a>Blattberechtigungen (Master Data Services)
  Blattberechtigungen gelten für die Attributwerte aller Blattelemente einer Entität.  
  
 Bei Entitäten, für die keine expliziten Hierarchien aktiviert wurden, erfolgen die Zuweisung einer Berechtigung zu einem **Blatt** und die Zuweisung einer Berechtigung zur Entität auf die gleiche Weise.  
  
 **Hinweise:**  
  
-   Blattberechtigungen gelten nur für den Funktionsbereich **Explorer** der Benutzeroberfläche.  
  
-   Den Attributen **Name** und **Code** zugewiesene Berechtigungen werden nicht erzwungen.  
  
|Berechtigung|Description|  
|----------------|-----------------|  
|**Schreibgeschützt**|Blattelemente werden zwar angezeigt, können vom Benutzer jedoch nicht hinzufügt, entfernt oder geändert werden.<br /><br /> Wenn konsolidierte Elemente vorhanden sind, werden die Namen und Codes zwar angezeigt, können vom Benutzer jedoch nicht hinzufügt, entfernt oder geändert werden.|  
|**Update**|Blattelemente werden angezeigt und können vom Benutzer hinzugefügt, entfernt und geändert werden.<br /><br /> Wenn konsolidierte Elemente vorhanden sind, werden die Namen und Codes zwar angezeigt, können vom Benutzer jedoch nicht hinzufügt, entfernt oder geändert werden.|  
|**Verweigern**|Blattelemente für die Entität werden nicht angezeigt.|  
  
## <a name="attribute-permissions"></a>Attributberechtigungen  
 Attributberechtigungen gelten für die Attributwerte der jeweiligen Entität. Benutzer mit Attributberechtigungen wird lediglich verweigert, Elemente hinzuzufügen oder zu entfernen.  
  
|Berechtigung|Description|  
|----------------|-----------------|  
|**Schreibgeschützt**|Das Attribut wird zwar angezeigt, aber der Benutzer kann keine Attributwerte ändern.|  
|**Update**|Das Attribut wird angezeigt, und der Benutzer kann Attributwerte ändern.|  
|**Verweigern**|Das Attribut wird nicht angezeigt.<br /><br /> Hinweis: Der Zugriff auf die Attribute Name und Code kann nicht explizit verweigert werden.|  
  
### <a name="example"></a>Beispiel  
 Weisen Sie dem Attribut „Subcategory“ der Entität „Product“ die Berechtigung **Aktualisieren** zu. Verweigern Sie die Berechtigung für alle anderen Attribute.  
  
|Name|Code|Subcategory (Aktualisiert)|  
|----------|----------|----------------------------|  
|Mountain-100|BK-M101|{5} Mountain Bikes|  
|Mountain-100|BK-M201|{5} Mountain Bikes|  
  
 Sie können im **Explorer**jeden Attributwert in der Spalte „Subcategory“ aktualisieren. Wenn Sie keine Berechtigung für ein Attribut haben, wird das Attribut nicht angezeigt.  
  
> [!NOTE]  
>  In diesem Beispiel ist Subcategory ein domänenbasiertes Attribut, das auf der SubcategoryList-Entität basiert. Sie können eine andere Unterkategorie für Mountain-100 auswählen, der SubcategoryList-Entität jedoch keine Elemente hinzufügen bzw. Elemente aus dieser Entität löschen.  
  
## <a name="see-also"></a>Siehe auch  
 [Zuweisen von Berechtigungen für Modellobjekte &#40;Master Data Services&#41;](assign-model-object-permissions-master-data-services.md)   
 [Konsolidierte Berechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-permissions-master-data-services.md)   
 [Modellobjektberechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Elemente &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md)   
 [Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)  
  
  