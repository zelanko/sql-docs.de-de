---
title: Erstellen eines Modells (MDS-Add-In für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
ms.assetid: 8ae26ec3-c5d5-4c4f-a810-2951a7454439
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 297441a73dcf2ff6f6e0e1808f863c7641edfa30
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48190570"
---
# <a name="building-a-model-mds-add-in-for-excel"></a>Erstellen eines Modells (MDS-Add-In für Excel)
  In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]können Administratoren eine Teilmenge der Administratorfunktionen ausführen, die in der [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung verfügbar sind.  
  
 Administratoren können in [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] die folgenden Modellerstellungstasks ausführen:  
  
-   Erstellen von Entitäten Weitere Informationen zu Entitäten finden Sie unter [Entities &#40;Master Data Services&#41;](../entities-master-data-services.md).  
  
-   Erstellen von Attributen aller Typen, einschließlich domänenbasierter Attribute Weitere Informationen zu Attributen finden Sie unter [Attributes &#40;Master Data Services&#41;](../attributes-master-data-services.md) und [Domain-Based Attributes &#40;Master Data Services&#41;](../domain-based-attributes-master-data-services.md).  
  
 Als Administrator müssen Sie das Modell mit der [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung oder dem Webdienst erstellen. Sie können Entitäten und Attribute innerhalb des Modells dann mithilfe von [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] erstellen. Weitere Informationen zu Modellobjekten finden Sie unter [Models &#40;Master Data Services&#41;](../models-master-data-services.md).  
  
## <a name="related-tasks"></a>Related Tasks  
 Die meisten Administratortasks müssen weiterhin in der [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung oder mithilfe des Webdiensts ausgeführt werden. In der folgenden Tabelle ist aufgeführt, welche Tools Administratoren verwenden können, um Tasks unter MDS auszuführen.  
  
|Taskbeschreibung|Tool|Thema|  
|----------------------|----------|-----------|  
|Erstellen von Modellen|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung oder Webdienst|[Erstellen eines Modells &#40;Master Data Services&#41;](../create-a-model-master-data-services.md)|  
|Erstellen einer Entität|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung, Webdienst oder [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]|[Erstellen einer Entität &#40;MDS-Add-In für Excel&#41;](create-an-entity-mds-add-in-for-excel.md)|  
|Erstellen eines domänenbasierten Attributs|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung, Webdienst oder [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]|[Erstellen eines domänenbasierten Attributs &#40;MDS-Add-In für Excel&#41;](create-a-domain-based-attribute-mds-add-in-for-excel.md)|  
|Erstellen von Attributgruppen|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung oder Webdienst|[Erstellen einer Attributgruppe &#40;Master Data Services&#41;](../create-an-attribute-group-master-data-services.md)|  
|Erstellen von Geschäftsregeln|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung oder Webdienst|[Erstellen und Veröffentlichen einer Geschäftsregel &#40;Master Data Services&#41;](../create-and-publish-a-business-rule-master-data-services.md)|  
|Erstellen von Abonnementsichten|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung oder Webdienst|[Erstellen einer Abonnementsicht &#40;Master Data Services&#41;](../create-a-subscription-view-to-export-data-master-data-services.md)|  
|Erstellen von Hierarchien|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung oder Webdienst|[Erstellen einer abgeleiteten Hierarchie &#40;Master Data Services&#41;](../create-a-derived-hierarchy-master-data-services.md)<br /><br /> [Erstellen einer expliziten Hierarchie &#40;Master Data Services&#41;](../create-an-explicit-hierarchy-master-data-services.md)|  
|Erstellen von Auflistungen|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung oder Webdienst|[Erstellen Sie eine Sammlung &#40;Master Data Services&#41;](../create-a-collection-master-data-services.md)|  
|Erstellen von Versionen von Daten|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung oder Webdienst|[Sperren einer Version &#40;Master Data Services&#41;](../lock-a-version-master-data-services.md)|  
|Bereitstellen von Modellen|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung, Webdienst oder MDSModelDeploy-Tool|[Erstellen eines Modellbereitstellungspakets mit MDSModelDeploy](../create-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   [Modelle &#40;Master Data Services&#41;](../models-master-data-services.md)  
  
-   [Entitäten &#40;Master Data Services&#41;](../entities-master-data-services.md)  
  
-   [Attribute &#40;Master Data Services&#41;](../attributes-master-data-services.md)  
  
-   [Domänenbasierte Attribute &#40;Master Data Services&#41;](../domain-based-attributes-master-data-services.md)  
  
-   [Attributgruppen &#40;Master Data Services&#41;](../attribute-groups-master-data-services.md)  
  
-   [Geschäftsregeln &#40;Master Data Services&#41;](../business-rules-master-data-services.md)  
  
-   [Exportieren von Daten &#40;Master Data Services&#41;](../overview-exporting-data-master-data-services.md)  
  
-   [Hierarchien &#40;Master Data Services&#41;](../hierarchies-master-data-services.md)  
  
-   [Sammlungen &#40;Master Data Services&#41;](../collections-master-data-services.md)  
  
-   [Versionen &#40;Master Data Services&#41;](../versions-master-data-services.md)  
  
-   [Sicherheit &#40;Master Data Services&#41;](../security-master-data-services.md)  
  
-   [Bereitstellen von Modellen &#40;Master Data Services&#41;](../deploying-models-master-data-services.md)  
  
  
