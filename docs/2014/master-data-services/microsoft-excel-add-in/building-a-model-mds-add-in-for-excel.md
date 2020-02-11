---
title: Erstellen eines Modells (MDS-Add-In für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 8ae26ec3-c5d5-4c4f-a810-2951a7454439
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: ee3473ba16ad3a03a95065aea94888654db53187
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65479347"
---
# <a name="building-a-model-mds-add-in-for-excel"></a>Erstellen eines Modells (MDS-Add-In für Excel)
  In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]können Administratoren eine Teilmenge der Administratorfunktionen ausführen, die in der [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung verfügbar sind.  
  
 Administratoren können in [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] die folgenden Modellerstellungstasks ausführen:  
  
-   Erstellen von Entitäten Weitere Informationen zu Entitäten finden Sie unter [Entitäten &#40;Master Data Services&#41;](../entities-master-data-services.md).  
  
-   Erstellen von Attributen aller Typen, einschließlich domänenbasierter Attribute Weitere Informationen zu Attributen finden Sie unter [Attribute &#40;Master Data Services&#41;](../attributes-master-data-services.md) und [Domänenbasierte Attribute &#40;Master Data Services&#41;](../domain-based-attributes-master-data-services.md).  
  
 Als Administrator müssen Sie das Modell mit der [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung oder dem Webdienst erstellen. Sie können Entitäten und Attribute innerhalb des Modells dann mithilfe von [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] erstellen. Weitere Informationen zu Modellobjekten finden Sie unter [Modelle &#40;Master Data Services&#41;](../models-master-data-services.md).  
  
## <a name="related-tasks"></a>Related Tasks  
 Die meisten Administratortasks müssen weiterhin in der [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung oder mithilfe des Webdiensts ausgeführt werden. In der folgenden Tabelle ist aufgeführt, welche Tools Administratoren verwenden können, um Tasks unter MDS auszuführen.  
  
|Taskbeschreibung|Tool|Thema|  
|----------------------|----------|-----------|  
|Erstellen von Modellen|
  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung oder Webdienst|[Erstellen Sie ein Modell &#40;Master Data Services&#41;](../create-a-model-master-data-services.md)|  
|Erstellen einer Entität|
  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung, Webdienst oder [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]|[Erstellen Sie eine Entität &#40;MDS-Add-in für Excel&#41;](create-an-entity-mds-add-in-for-excel.md)|  
|Erstellen eines domänenbasierten Attributs|
  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung, Webdienst oder [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]|[Erstellen eines domänenbasierten Attributs &#40;MDS-Add-in für Excel&#41;](create-a-domain-based-attribute-mds-add-in-for-excel.md)|  
|Erstellen von Attributgruppen|
  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung oder Webdienst|[Erstellen Sie eine Attribut Gruppe &#40;Master Data Services&#41;](../create-an-attribute-group-master-data-services.md)|  
|Erstellen von Geschäftsregeln|
  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung oder Webdienst|[Erstellen und Veröffentlichen einer Geschäftsregel &#40;Master Data Services&#41;](../create-and-publish-a-business-rule-master-data-services.md)|  
|Erstellen von Abonnementsichten|
  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung oder Webdienst|[Erstellen Sie eine Abonnement Sicht &#40;Master Data Services&#41;](../create-a-subscription-view-to-export-data-master-data-services.md)|  
|Erstellen von Hierarchien|
  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung oder Webdienst|[Erstellen Sie eine abgeleitete Hierarchie &#40;Master Data Services&#41;](../create-a-derived-hierarchy-master-data-services.md)<br /><br /> [Erstellen einer expliziten Hierarchie &#40;Master Data Services&#41;](../create-an-explicit-hierarchy-master-data-services.md)|  
|Erstellen von Auflistungen|
  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung oder Webdienst|[Erstellen Sie eine Sammlung &#40;Master Data Services&#41;](../create-a-collection-master-data-services.md)|  
|Erstellen von Versionen von Daten|
  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung oder Webdienst|[Eine Version &#40;Master Data Services Sperren&#41;](../lock-a-version-master-data-services.md)|  
|Bereitstellen von Modellen|
  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung, Webdienst oder MDSModelDeploy-Tool|[Erstellen eines Modellbereitstellungspakets mit MDSModelDeploy](../create-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   [Modelle &#40;Master Data Services&#41;](../models-master-data-services.md)  
  
-   [Entitäten &#40;Master Data Services&#41;](../entities-master-data-services.md)  
  
-   [Attribute &#40;Master Data Services&#41;](../attributes-master-data-services.md)  
  
-   [Domänen basierte Attribute &#40;Master Data Services&#41;](../domain-based-attributes-master-data-services.md)  
  
-   [Attribut Gruppen &#40;Master Data Services&#41;](../attribute-groups-master-data-services.md)  
  
-   [Master Data Services von Geschäftsregeln &#40;&#41;](../business-rules-master-data-services.md)  
  
-   [Daten &#40;Master Data Services werden exportiert&#41;](../overview-exporting-data-master-data-services.md)  
  
-   [Hierarchien &#40;Master Data Services&#41;](../hierarchies-master-data-services.md)  
  
-   [Sammlungen &#40;Master Data Services&#41;](../collections-master-data-services.md)  
  
-   [Versionen &#40;Master Data Services&#41;](../versions-master-data-services.md)  
  
-   [Sicherheits &#40;Master Data Services&#41;](../security-master-data-services.md)  
  
-   [Bereitstellen von Modellen &#40;Master Data Services&#41;](../deploying-models-master-data-services.md)  
  
  
