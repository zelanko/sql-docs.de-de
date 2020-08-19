---
description: Sichtbarmachen einer Attributgruppe für Benutzer (Master Data Services)
title: Sichtbarmachen einer Attributgruppe für Benutzer
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b2f6cc27-dbc9-4f3f-961e-e81e76375248
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c966c12bb8245571dcbfac0984d0434282e82c57
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88495018"
---
# <a name="make-an-attribute-group-visible-to-users-master-data-services"></a>Sichtbarmachen einer Attributgruppe für Benutzer (Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Machen Sie in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]eine Attributgruppe für Benutzer oder Gruppen sichtbar, wenn Sie möchten, dass Benutzer im Funktionsbereich **Explorer** oberhalb des Rasters Registerkarten verwenden können.  
  
 Beim Erstellen einer Attributgruppe wird diese automatisch für alle Benutzer bis auf den Ersteller ausgeblendet.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **System Verwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Es muss mindestens eine Attributgruppe vorhanden sein. Weitere Informationen finden Sie unter [Erstellen einer Attributgruppe &#40;Master Data Services&#41;](../master-data-services/create-an-attribute-group-master-data-services.md).  
  
### <a name="to-make-an-attribute-group-visible-to-users"></a>So machen Sie eine Attributgruppe für Benutzer sichtbar  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Systemverwaltung**.  
  
2.  Wählen Sie auf der Seite **Modell verwalten** im Raster ein Modell aus, und klicken Sie dann auf **Entitäten**.  
  
3.  Wählen Sie auf der Seite **Entität verwalten** im Raster die Zeile der Entität aus, für die Sie die Attributgruppe bearbeiten möchten.  
  
4.  Klicken Sie auf **Attributgruppen**.  
  
5.  Wählen Sie auf der Seite **Attributgruppen verwalten** den Elementtyp in der Dropdownliste **Member Types** (Elementtypen) aus, um **Blatt**, **Konsolidiert** oder **Sammlung**abhängig vom Typ der Gruppe, die Sie sichtbar machen möchten, zu erweitern.  
  
6.  Wählen Sie im Raster die Attributgruppe aus, die Sie bearbeiten möchten, und klicken Sie anschließend auf **Bearbeiten**.  
  
7.  Klicken Sie im Feld **Verfügbar** auf einen Benutzer oder eine Gruppe, und klicken Sie auf den Pfeil für **Hinzufügen** . Klicken Sie auf den Pfeil für **Alle hinzufügen** , um alles hinzuzufügen.  
  
8.  Klicken Sie auf **Speichern**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Attribut Gruppen &#40;Master Data Services&#41;](../master-data-services/attribute-groups-master-data-services.md)   
 [Erstellen einer Attributgruppe &#40;Master Data Services&#41;](../master-data-services/create-an-attribute-group-master-data-services.md)  
  
  
