---
title: Erstellen einer expliziten Hierarchie (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating explicit hierarchies [Master Data Services]
- explicit hierarchies, creating
ms.assetid: ba768393-6990-4eda-8cb0-d58cb3cfc2e2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b9cd0874c77a6e179772ac532af3402a8fe4b6c0
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971711"
---
# <a name="create-an-explicit-hierarchy-master-data-services"></a>Erstellen einer expliziten Hierarchie (Master Data Services)
  Erstellen Sie in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]eine explizite Hierarchie, wenn Sie eine unregelmäßige Hierarchie benötigen, in der Elemente auf jeder Ebene vorhanden sein können. Explizite Hierarchien enthalten Elemente aus einer einzelnen Entität.  
  
 Wenn Sie eine explizite Hierarchie erstellt haben, können Sie dieser im Funktionsbereich **Explorer** Elemente hinzufügen.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **System Verwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Die Entität muss für explizite Hierarchien und Auflistungen aktiviert werden. Weitere Informationen finden Sie unter [Aktivieren einer Entität für explizite Hierarchien und Auflistungen &#40;Master Data Services&#41;](../../2014/master-data-services/enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md).  
  
### <a name="to-create-an-explicit-hierarchy"></a>So erstellen Sie eine explizite Hierarchie  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Systemverwaltung**.  
  
2.  Zeigen Sie auf der Seite **Modellansicht** auf der Menüleiste auf **Verwalten** , und klicken Sie auf **Entitäten**.  
  
3.  Wählen Sie auf der Seite **Entitätsverwaltung** aus der Liste **Modell** ein Modell aus.  
  
4.  Wählen Sie die Zeile für die Entität aus, für die Sie eine explizite Hierarchie erstellen möchten.  
  
5.  Klicken Sie auf **Ausgewählte Entität bearbeiten**.  
  
6.  Klicken Sie auf der Seite **Entität bearbeiten** im Bereich **explizite Hierarchien** auf **explizite Hierarchie hinzufügen**.  
  
7.  Geben Sie auf der Seite **explizite Hierarchie hinzufügen** im Feld **Name der expliziten Hierarchie** einen Namen für die Hierarchie ein.  
  
8.  Optional können Sie das Kontrollkästchen für **Obligatorische Hierarchie** deaktivieren, um die Hierarchie als nicht obligatorische Hierarchie zu erstellen. Weitere Informationen zu Hierarchietypen finden Sie unter [Explizite Hierarchien &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md).  
  
9. Klicken Sie auf **Hierarchie speichern**.  
  
10. Klicken Sie auf der Seite **Entität bearbeiten** auf **Entität speichern**.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
-   [Erstellen eines konsolidierten Elements &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-consolidated-member-master-data-services.md)  
  
-   [Verschieben von Elementen innerhalb einer Hierarchie &#40;Master Data Services&#41;](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Explizite Hierarchien &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)   
 [Abgeleitete Hierarchien mit expliziten Caps &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)   
 [Ändern des Namens einer expliziten Hierarchie &#40;Master Data Services&#41;](../../2014/master-data-services/change-an-explicit-hierarchy-name-master-data-services.md)  
  
  
