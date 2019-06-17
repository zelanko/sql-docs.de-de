---
title: Erstellen eines Modelladministrators (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], creating
ms.assetid: dae17afc-3b39-490e-b51f-2d8da26d429e
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 44bede292cb49ddcfd791b3e7d65605e1aa2399c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65487491"
---
# <a name="create-a-model-administrator-master-data-services"></a>Erstellen eines Modelladministrators (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Erstellen Sie in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]einen Modelladministrator, wenn Sie möchten, dass eine Gruppe oder ein Benutzer die Berechtigung für alle Objekte in einem oder mehreren Modellen hat.  
  
> [!TIP]  
>  Erstellen Sie zum Vereinfachen der Verwaltung eine Windows-Gruppe oder lokale Gruppe und konfigurieren Sie diese als Modelladministrator. Sie können anschließend der Gruppe Benutzer hinzufügen und diese daraus entfernen, ohne auf [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]zuzugreifen.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Benutzer- und Gruppenberechtigungen** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)zuzugreifen.  
  
### <a name="to-create-a-model-administrator"></a>So erstellen Sie einen Modelladministrator  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Benutzer- und Gruppenberechtigungen**.  
  
2.  Wählen Sie auf der Seite **Benutzer** oder **Gruppen** die Zeile für den Benutzer oder die Gruppe aus, den bzw. die Sie bearbeiten möchten.  
  
3.  Klicken Sie auf **Ausgewähltem Benutzer bearbeiten**.  
  
4.  Klicken Sie auf die Registerkarte **Modelle** .  
  
5.  Wählen Sie optional ein Modell aus der Liste **Modell** aus.  
  
6.  Klicken Sie auf **Bearbeiten**.  
  
7.  Klicken Sie auf das Modell, dem Sie die Berechtigung zuweisen möchten.  
  
8.  Wählen Sie im Menü **Administrator**aus.  
  
9. Führen Sie die Schritte 7 und 8 für jedes Modell aus, für das Sie die Gruppe bzw. den Benutzer als Administrator definieren möchten.  
  
10. Klicken Sie auf **Speichern**.  
  
## <a name="see-also"></a>Siehe auch  
 [Administratoren &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)   
 [Zuweisen von Berechtigungen für Modellobjekte &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Zuweisen von Hierarchieelementberechtigungen &#40;Master Data Services&#41;](../master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [Berechtigungen für Modellobjekte &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [Berechtigungen für Hierarchieelemente &#40;Master Data Services&#41;](../master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
