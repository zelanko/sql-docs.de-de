---
title: Verschieben von Elementen innerhalb einer Hierarchie (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Master Data Services], moving members
- explicit hierarchies, moving members
- derived hierarchies, moving members
- members [Master Data Services], moving
ms.assetid: 049c9a15-89c1-478c-8438-028fffc9e187
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 58b39d2dc660fd51d1ba21308ff056874a239731
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66054093"
---
# <a name="move-members-within-a-hierarchy-master-data-services"></a>Verschieben von Elementen innerhalb einer Hierarchie (Master Data Services)
  Sie können in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Elemente innerhalb einer Hierarchie verschieben, um deren Position oder die Zuweisung des übergeordneten Elements zu ändern.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung für den Zugriff auf den Funktionsbereich **Explorer** verfügen.  
  
-   Bei expliziten Hierarchien müssen Sie mindestens über die Berechtigung **Aktualisieren** für die Entität verfügen.  
  
-   Bei abgeleiteten Hierarchien benötigen Sie mindestens ein **Update** für das Modell und alle domänenbasierten Attribute, die in der Hierarchie verwendet werden.  
  
### <a name="to-move-members-within-a-hierarchy"></a>So verschieben Sie Elemente innerhalb einer Hierarchie  
  
1.  Wählen Sie auf der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Startseite aus der Liste **Modell** ein Modell aus.  
  
2.  Wählen Sie aus der Liste **Version** eine Version aus.  
  
3.  Klicken Sie auf **Explorer**.  
  
4.  Zeigen Sie auf der Menüleiste auf **Hierarchien** , und klicken Sie auf *Hierarchy_Name*.  
  
5.  Klicken Sie im Bereich **Hierarchie** , in dem die Hierarchie in einer Baumstruktur angezeigt wird, auf das Kontrollkästchen für jedes Element, das Sie verschieben möchten.  
  
6.  Klicken Sie oben im Bereich **Hierarchie** auf **Ausschneiden**.  
  
7.  Aktivieren Sie im Bereich **Hierarchie** das Kontrollkästchen für den Member, in den die Elemente verschoben werden sollen.  
  
8.  Klicken Sie auf **Einfügen**.  
  
    > [!NOTE]  
    >  In abgeleiteten Hierarchien können Sie Elemente nur in Elemente auf gleicher Ebene verschieben. Auch die Sortierreihenfolge der Elemente kann nicht geändert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verschieben Sie explizite Hierarchie Elemente mithilfe des Stagingprozesses &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md)   
 [Abgeleitete Hierarchien &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md)   
 [Explizite Hierarchien &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
  
