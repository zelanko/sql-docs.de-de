---
title: Attributgruppen
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attribute groups [Master Data Services]
- attribute groups [Master Data Services], about attribute groups
ms.assetid: 648b3d0b-e15a-45f9-8292-3a54a072e62c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2b5cefb3548886cc26e55a9f408ac68e2bd30620
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73729769"
---
# <a name="attribute-groups-master-data-services"></a>Attributgruppen (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]können Attribute in einer Entität mithilfe von Attributgruppen organisiert werden. Wenn eine Entität über viele Attribute verfügt, kann die Entität mit Attributgruppen besser in der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendung angezeigt werden.  
  
## <a name="how-attribute-groups-change-the-display"></a>Ändern der Anzeige mithilfe von Attributgruppen  
 Attributgruppen werden als Registerkarten oberhalb des Rasters im Funktionsbereich **Explorer** von [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]angezeigt.  
  
 Wenn eine Entität über eine große Anzahl von Attributen verfügt und Sie diese Entität in einem Raster in **Explorer**anzeigen, müssen Sie zum Anzeigen aller Attribute einen Bildlauf nach rechts durchführen. Um dies zu vermeiden, können Sie Attributgruppen erstellen.  
  
-   Attributgruppen schließen immer das Name-Attribut und das Code-Attribut ein.  
  
-   Jedes Attribut für eine Entität kann einer oder mehreren Attributgruppen angehören.  
  
-   Alle Attribute sind automatisch im **Explorer** auf der Registerkarte **Alle Attribute**enthalten.  
  
-   Es gibt keine Möglichkeit, die Registerkarte **Alle Attribute** auszublenden.  
  
 Attributgruppen werden im Funktionsbereich **Systemverwaltung** von [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]verwaltet.  
  
## <a name="show-or-hide-attribute-groups"></a>Anzeigen oder Ausblenden von Attributgruppen  
 Beim Erstellen einer Attributgruppe wird diese automatisch für alle Benutzer bis auf den Ersteller ausgeblendet. Weitere Informationen zum Sichtbarmachen der Gruppe finden Sie unter [Sichtbarmachen einer Attributgruppe für Benutzer &#40;Master Data Services&#41;](../master-data-services/make-an-attribute-group-visible-to-users-master-data-services.md)angezeigt.  
  
 Wenn Sie ein bestimmtes Attribut innerhalb einer Gruppe ausblenden möchten, können Sie dem Attribut die Berechtigung **Verweigern** zuweisen. Weitere Informationen finden Sie unter [Blattberechtigungen &#40;Master Data Services&#41;](../master-data-services/leaf-permissions-master-data-services.md).  
  
## <a name="related-tasks"></a>Verwandte Aufgaben  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Erstellen Sie eine neue Attributgruppe, und fügen Sie ihr Attribute hinzu.|[Erstellen einer Attributgruppe &#40;Master Data Services&#41;](../master-data-services/create-an-attribute-group-master-data-services.md)|  
|Machen Sie eine Attributgruppe für Benutzer sichtbar.|[Sichtbarmachen einer Attributgruppe für Benutzer &#40;Master Data Services&#41;](../master-data-services/make-an-attribute-group-visible-to-users-master-data-services.md)|  
|Ändern Sie den Namen einer vorhandenen Attributgruppe.|[Ändern des Namens einer Attributgruppe &#40;Master Data Services&#41;](../master-data-services/change-an-attribute-group-name-master-data-services.md)|  
|Löschen Sie eine vorhandeme Attributgruppe.|[Löschen einer Attributgruppe &#40;Master Data Services&#41;](../master-data-services/delete-an-attribute-group-master-data-services.md)|  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   [Attribute &#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md)  
  
  
