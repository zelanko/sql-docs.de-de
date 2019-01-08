---
title: 'Vorgehensweise: Festlegen von Berechtigungen (Master Data Services) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Master Data Services], determining permissions
ms.assetid: 1dc0b43a-d023-4e7d-b027-8b1459fd058c
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 7b138dd1cf07ccfccefb9e1556c743f3c0a45abd
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52747412"
---
# <a name="how-permissions-are-determined-master-data-services"></a>Vorgehensweise: Festlegen von Berechtigungen (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]ist die einfachste Methode zum Konfigurieren der Sicherheit, Modellobjektberechtigungen einer Gruppe zuzuweisen, deren Mitglied der Benutzer ist.  
  
 Die Sicherheit wird komplexer, wenn:  
  
-   Modellobjekt- und Hierarchieelementberechtigungen zugewiesen werden.  
  
-   Der Benutzer Gruppen angehört und die Berechtigung dem Benutzer und Gruppen zugewiesen wird.  
  
-   Der Benutzer Gruppen angehört und die Berechtigung mehreren Gruppen zugewiesen wird.  
  
## <a name="permissions-assigned-to-a-single-group-or-user"></a>Einer einzelnen Gruppe oder einem Benutzer zugewiesene Berechtigungen  
 Wenn Sie Berechtigungen einer einzelnen Gruppe oder einem Benutzer zuweisen, werden Berechtigungen gemäß dem folgenden Workflow festgelegt.  
  
 ![mds_conc_security_no_overlap](../../2014/master-data-services/media/mds-conc-security-no-overlap.gif "mds_conc_security_no_overlap")  
  
### <a name="step-1-effective-attribute-permissions-are-determined"></a>Schritt 1: Effektive Attributberechtigungen werden festgelegt.  
 Die folgende Liste beschreibt, wie effektive Attributberechtigungen festgelegt werden:  
  
-   Modellobjekten zugewiesene Berechtigungen legen fest, auf welche Attribute ein Benutzer zugreifen kann.  
  
-   Von allen Modellobjekten wird die Berechtigung automatisch vom nächst gelegenen Objekt auf einer höheren Ebene in der Modellstruktur geerbt.  
  
-   Objekte auf derselben Ebene wie die Entität werden implizit verweigert.  
  
-   Objekten auf einer höheren Ebene wird Navigationszugriff gewährt. Weitere Informationen zum Navigationszugriff finden Sie unter [Navigationszugriff &#40;Master Data Services&#41;](navigational-access-master-data-services.md).  
  
 In diesem Beispiel **schreibgeschützte** Berechtigung zu einer Entität zugewiesen wird, und diese Berechtigung wird von dessen Attribut, das auf einer niedrigeren Ebene in der Modellstruktur geerbt. Das Modell bietet Navigationszugriff auf diese Entität und ihr Attribut. Der anderen Entität im Modell wurde keine explizite Berechtigung zugewiesen, und von ihr werden keine Berechtigungen geerbt. Sie wird daher implizit verweigert.  
  
 ![mds_conc_inheritance_model](../../2014/master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")  
  
### <a name="step-2-if-hierarchy-member-permissions-are-assigned-effective-member-permissions-are-determined"></a>Schritt 2: Wenn Berechtigungen für Hierarchieelemente zugewiesen sind, werden effektive Elementberechtigungen festgelegt.  
 Die folgende Liste beschreibt, wie effektive Hierarchieelementberechtigungen festgelegt werden:  
  
-   Hierarchieknoten zugewiesene Berechtigungen legen fest, auf welche Elemente ein Benutzer zugreifen kann.  
  
-   Von allen Knoten in einer Hierarchie wird die Berechtigung automatisch vom nächst gelegenen Objekt auf einer höheren Ebene in der Hierarchiestruktur geerbt.  
  
-   Alle Knoten auf derselben Ebene werden implizit verweigert.  
  
-   Alle Knoten auf höheren Ebenen, denen keine Berechtigungen zugewiesen wurden, werden implizit verweigert.  
  
 In diesem Beispiel **schreibgeschützte** Berechtigung einem Knoten der Hierarchie zugewiesen wird, und diese Berechtigung wird von einem Knoten auf einer niedrigeren Ebene in der Hierarchiestruktur geerbt. Dem Stamm wurde keine Berechtigung zugewiesen, er wird daher implizit verweigert. Dem anderen Knoten in der Hierarchiestruktur wurde keine explizite Berechtigung zugewiesen, und von ihm werden keine Berechtigungen geerbt. Er wird daher implizit verweigert.  
  
 ![mds_conc_inheritance_hierarchy](../../2014/master-data-services/media/mds-conc-inheritance-hierarchy.gif "mds_conc_inheritance_hierarchy")  
  
### <a name="step-3-the-intersection-of-attribute-and-member-permissions-is-determined"></a>Schritt 3: Die Schnittmenge von Attribut-und Elementberechtigungen wird bestimmt.  
 Wenn sich die effektiven Attributberechtigungen von den effektiven Elementberechtigungen unterscheiden, müssen Berechtigungen für jeden einzelnen Attributwert festgelegt werden. Weitere Informationen finden Sie unter [Überlappende Benutzer- und Gruppenberechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md).  
  
## <a name="permissions-assigned-to-multiple-groups"></a>Mehreren Gruppen zugewiesene Berechtigungen  
 Wenn ein Benutzer einer oder mehreren Gruppen angehört und Berechtigungen dem Benutzer und den Gruppen zugewiesen werden, wird der Workflow komplexer.  
  
 ![mds_conc_security_group_overlap](../../2014/master-data-services/media/mds-conc-security-group-overlap.gif "mds_conc_security_group_overlap")  
  
 In diesem Fall müssen überlappende Benutzer- und Gruppenberechtigungen aufgelöst werden, bevor Modellobjekt- und Hierarchieelementberechtigungen verglichen werden können. Weitere Informationen finden Sie unter [Überlappende Benutzer- und Gruppenberechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Überlappende Benutzer- und Gruppenberechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md)   
 [Überlappende Modell- und Elementberechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md)  
  
  
