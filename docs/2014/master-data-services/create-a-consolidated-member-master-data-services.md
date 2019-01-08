---
title: Erstellen eines konsolidierten Elements (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating consolidated members [Master Data Services]
- members [Master Data Services], creating consolidated members
- consolidated members [Master Data Services], creating
ms.assetid: 431ab2d2-5517-4372-9980-142b05427c08
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 8bef17d900fe9a823439a88b8e94eb78810e6627
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52766942"
---
# <a name="create-a-consolidated-member-master-data-services"></a>Create a Consolidated Member (Master Data Services)
  Erstellen Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]ein konsolidiertes Element, wenn Sie einen übergeordneten Knoten für eine explizite Hierarchie wollen. Konsolidierte Elemente können eigene Attribute aufweisen. Sie werden zum Gruppieren verwendet. Wie im folgenden Beispiel gezeigt, können konsolidierte Elemente zum Gruppieren von Konten verwendet werden, die Konten unter sich haben.  
  
 ![MDS konsolidierte Elemente](../../2014/master-data-services/media/mds-consolidated-members.png "MDS konsolidierten Elementen")  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung für den Zugriff auf den Funktionsbereich **Explorer** verfügen.  
  
-   Sie müssen mindestens die Berechtigung **Aktualisieren** für das konsolidierte Modellobjekt für die Entität besitzen, der Sie ein Element hinzufügen.  
  
### <a name="to-create-a-consolidated-member"></a>So erstellen Sie ein konsolidiertes Element  
  
1.  Wählen Sie auf der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Startseite aus der Liste **Modell** ein Modell aus.  
  
2.  Wählen Sie aus der Liste **Version** eine Version aus.  
  
3.  Klicken Sie auf **Explorer**.  
  
4.  Zeigen Sie auf der Menüleiste auf **Hierarchien** , und klicken Sie auf den Namen der Hierarchie, der Sie ein konsolidiertes Element hinzufügen möchten.  
  
5.  Aktivieren Sie über dem Raster die Option **Konsolidierte Elemente** oder **Alle konsolidierten Elemente in der Hierarchie** .  
  
6.  Klicken Sie auf **Hinzufügen**.  
  
7.  Vervollständigen Sie im Bereich rechts die Felder.  
  
8.  Dies ist optional. Geben Sie im Feld **Anmerkungen** einen Kommentar dazu ein, warum das Element hinzugefügt wurde. Alle Benutzer, die Zugriff auf das Element haben, können die Anmerkung anzeigen.  
  
9. Klicken Sie auf **OK**.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
-   [Verschieben von Elementen innerhalb einer Hierarchie &#40;Master Data Services&#41;](move-members-within-a-hierarchy-master-data-services.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer expliziten Hierarchie &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)   
 [Erstellen eines Blattelements &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-leaf-member-master-data-services.md)   
 [Laden oder Aktualisieren von Elementen in Master Data Services mithilfe des Stagingprozesses](/sql/2014/master-data-services/add-update-and-delete-data-master-data-services)   
 [Elemente &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md)   
 [Explizite Hierarchien &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
  
