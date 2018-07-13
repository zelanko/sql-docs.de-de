---
title: Verschieben von Elementen innerhalb einer Hierarchie (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Master Data Services], moving members
- explicit hierarchies, moving members
- derived hierarchies, moving members
- members [Master Data Services], moving
ms.assetid: 049c9a15-89c1-478c-8438-028fffc9e187
caps.latest.revision: 8
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8048fce8af968f0a1188f8330993977bedcac7d3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37252308"
---
# <a name="move-members-within-a-hierarchy-master-data-services"></a>Verschieben von Elementen innerhalb einer Hierarchie (Master Data Services)
  Sie können in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Elemente innerhalb einer Hierarchie verschieben, um deren Position oder die Zuweisung des übergeordneten Elements zu ändern.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung für den Zugriff auf den Funktionsbereich **Explorer** verfügen.  
  
-   Für explizite Hierarchien, benötigen Sie mindestens **Update** Berechtigung für die Entität.  
  
-   Abgeleitete Hierarchien, benötigen Sie mindestens **Update** für das Modell und alle domänenbasierten Attributen, die in der Hierarchie verwendet.  
  
### <a name="to-move-members-within-a-hierarchy"></a>So verschieben Sie Elemente innerhalb einer Hierarchie  
  
1.  Wählen Sie auf der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Startseite aus der Liste **Modell** ein Modell aus.  
  
2.  Wählen Sie aus der Liste **Version** eine Version aus.  
  
3.  Klicken Sie auf **Explorer**.  
  
4.  Zeigen Sie auf der Menüleiste **Hierarchien** , und klicken Sie auf *Hierarchiename*.  
  
5.  In der **Hierarchie** Bereich, in denen die Hierarchie in einer Baumstruktur angezeigt wird, klicken Sie auf das Kontrollkästchen für jedes Element, das Sie verschieben möchten.  
  
6.  Am oberen Rand der **Hierarchie** Bereich, klicken Sie auf **Ausschneiden**.  
  
7.  In der **Hierarchie** Bereich, klicken Sie auf das Kontrollkästchen für das Element, das die Elemente verschoben werden sollen.  
  
8.  Klicken Sie auf **einfügen**.  
  
    > [!NOTE]  
    >  In abgeleiteten Hierarchien können Sie Elemente nur in Elemente auf gleicher Ebene verschieben. Auch die Sortierreihenfolge der Elemente kann nicht geändert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Verschieben von expliziten Hierarchieelementen mithilfe des Stagingprozesses &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md)   
 [Abgeleitete Hierarchien &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md)   
 [Explizite Hierarchien &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
  
