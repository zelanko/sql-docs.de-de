---
title: Löschen eines Elements oder einer Auflistung (Master Data Services) | Microsoft-Dokumentation
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
- collections [Master Data Services], deleting
- leaf members [Master Data Services], deleting
- deleting members [Master Data Services]
- members [Master Data Services], deleting
- consolidated members [Master Data Services], deleting
ms.assetid: 519130a7-4226-4d71-9124-d2ee0ce7e5bd
caps.latest.revision: 6
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: cbfc5554d70a460d137b0938319f3025e581218c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37172931"
---
# <a name="delete-a-member-or-collection-master-data-services"></a>Löschen eines Elements oder einer Auflistung (Master Data Services)
  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]können Sie ein Element oder eine Auflistung löschen, das bzw. die Sie nicht mehr benötigen. Wenn Sie Elemente in einer Massenoperation löschen möchten, verwenden Sie stattdessen den Stagingprozess. Weitere Informationen finden Sie unter [deaktivieren oder Löschen von Elementen mithilfe des Stagingprozesses &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md).  
  
> [!NOTE]  
>  Sie können kein Element löschen, das als domänenbasierter Attributwert für ein anderes Element verwendet wird.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung für den Zugriff auf den Funktionsbereich **Explorer** verfügen.  
  
-   Für Mitglieder, benötigen Sie mindestens **Update** Berechtigung für das blattmodellobjekt, löschen Sie ein Element aus.  
  
-   Bei Auflistungen müssen Sie für das zu löschende Blattauflistungsobjekt mindestens über die Berechtigung **Aktualisieren** verfügen.  
  
### <a name="to-delete-a-member-or-collection"></a>So löschen Sie ein Element oder eine Auflistung  
  
1.  Wählen Sie auf der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Startseite aus der Liste **Modell** ein Modell aus.  
  
2.  Wählen Sie aus der Liste **Version** eine Version aus.  
  
3.  Klicken Sie auf **Explorer**.  
  
4.  Zum Löschen  
  
    -   eines Elements zeigen Sie auf der Menüleiste auf **Entitäten** und klicken auf den Namen der Entität, in der das Element enthalten ist.  
  
    -   eines konsolidierten Elements zeigen Sie auf der Menüleiste auf **Hierarchien** und klicken auf den Namen der Hierarchie, in der das Element enthalten ist. Klicken Sie dann auf den Knoten in der Hierarchie, die das Element enthält.  
  
    -   einer Sammlung zeigen Sie auf der Menüleiste auf **Sammlungen** und klicken auf den Namen der Entität, in der die Sammlung enthalten ist.  
  
5.  Klicken Sie im Raster auf die Zeile mit dem Element oder der Sammlung, das bzw. die Sie löschen möchten.  
  
6.  Klicken Sie auf **Element löschen**, **Löschen**oder **Sammlung löschen**.  
  
7.  Klicken Sie im Bestätigungsdialogfeld auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Reaktivieren eines Elements oder einer Auflistung &#40;Master Data Services&#41;](../../2014/master-data-services/reactivate-a-member-or-collection-master-data-services.md)   
 [Elemente &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md)   
 [Sammlungen &#40;Master Data Services&#41;](../../2014/master-data-services/collections-master-data-services.md)  
  
  
