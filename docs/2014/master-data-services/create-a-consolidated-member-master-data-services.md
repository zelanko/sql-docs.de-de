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
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 588295d0705ec9c556c85eb5bef1d96d8128b580
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "78176069"
---
# <a name="create-a-consolidated-member-master-data-services"></a>Create a Consolidated Member (Master Data Services)
  Erstellen Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]ein konsolidiertes Element, wenn Sie einen übergeordneten Knoten für eine explizite Hierarchie wollen. Konsolidierte Elemente können eigene Attribute aufweisen. Sie werden zum Gruppieren verwendet. Wie im folgenden Beispiel gezeigt, können konsolidierte Elemente zum Gruppieren von Konten verwendet werden, die Konten unter sich haben.

 ![Konsolidierte MDS-Elemente](../../2014/master-data-services/media/mds-consolidated-members.png "Konsolidierte MDS-Elemente")

## <a name="prerequisites"></a>Voraussetzungen
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

8.  (Optional) Geben Sie im Feld **Anmerkungen** einen Kommentar dazu ein, warum das Element hinzugefügt wurde. Alle Benutzer, die Zugriff auf das Element haben, können die Anmerkung anzeigen.

9. Klicken Sie auf **OK**.

## <a name="next-steps"></a>Nächste Schritte

-   [Verschieben von Elementen innerhalb einer Hierarchie &#40;Master Data Services&#41;](move-members-within-a-hierarchy-master-data-services.md)

## <a name="see-also"></a>Weitere Informationen
 [Erstellen einer expliziten Hierarchie &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md) [ein Blatt Element &#40;Master Data Services](../../2014/master-data-services/create-a-leaf-member-master-data-services.md)&#41;[Laden oder Aktualisieren von Elementen in Master Data Services mithilfe der stagingprozessmember](add-update-and-delete-data-master-data-services.md) [&#40;](../../2014/master-data-services/members-master-data-services.md) Master Data Services&#41;[expliziten Hierarchien](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) &#40;Master Data Services&#41;


