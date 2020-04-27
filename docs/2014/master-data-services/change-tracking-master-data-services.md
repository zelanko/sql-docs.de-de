---
title: Änderungsnachverfolgung (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- change tracking [SQL Server]
ms.assetid: 5e879c65-0d38-454f-9a20-62a6e72c89f7
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 7b4b7d9d9d153456ca471196c6480465d057e412
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "65483522"
---
# <a name="change-tracking-master-data-services"></a>Änderungsnachverfolgung (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]können Sie Änderungsnachverfolgungsgruppen verwenden, um Aktionen durchzuführen, wenn sich ein Attributwert ändert. Verwenden Sie die Änderungsnachverfolgung, wenn Sie nicht wissen, was der neue Wert ist, aber wissen möchten, ob eine Änderung aufgetreten ist.  
  
## <a name="configuring-change-tracking"></a>Konfigurieren der Änderungsnachverfolgung  
 Um die Änderungsnachverfolgung zu konfigurieren, fügen Sie einer Änderungsnachverfolgungsgruppe ein Attribut hinzu. Die Gruppe kann ein oder viele Attribute enthalten. Erstellen Sie dann eine Geschäftsregel, um die Aktion zu definieren, die ausgeführt wird, wenn sich eines der Attribute in der Gruppe ändert.  
  
> [!NOTE]  
>  Änderungsnachverfolgungs-Geschäftsregeln stufen bereitgestellte (importierte) Daten als geändert ein.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Hinzufügen von Attributen zu einer Änderungsnachverfolgungsgruppe.|[Hinzufügen von Attributen zu einer Änderungsnachverfolgungsgruppe &#40;Master Data Services&#41;](add-attributes-to-a-change-tracking-group-master-data-services.md)|  
|Erstellen einer Geschäftsregel, die Aktionen auf der Grundlage von Änderungen an Attributwerten initiiert.|[Initiieren von Aktionen auf der Grundlage von Attributwertänderungen &#40;Master Data Services&#41;](../../2014/master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   [Überprüfung &#40;Master Data Services&#41;](../../2014/master-data-services/validation-master-data-services.md)  
  
-   [Geschäftsregeln &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)  
  
-   [Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
