---
title: Entitäten-Synchronisierungspartnerschaft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: bd627a2d-dc64-47e9-9a71-2d0ad04b4962
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fde11c6b106a9e559d74504b77d975d096c1f3d0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "73729271"
---
# <a name="entity-sync-relationship-master-data-services"></a>Entitäten-Synchronisierungspartnerschaft (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Entitäten-Synchronisierung ist eine unidirektionale und wiederholbare Synchronisierung zwischen Entitätsversionen. Sie ermöglicht Ihnen, Entitätsdaten zwischen verschiedenen Modellen freizugeben. Sie können eine Single Source of Truth in einem Modell beibehalten und diese Masterdaten in anderen Modellen wiederverwenden. Sie können beispielsweise in einer Modellentität Daten zu US-Staaten speichern und diese Daten in anderen Modellen wiederverwenden.  
  
 Durch die Entitäten-Synchronisierung können Sie auch eine einmalige Kopie der Daten vornehmen.  
  
 Alle Blattelemente mit Freiform- und Dateiattributen in der Quellentität werden während der Ausführung der Synchronisierung mit der Zielentität synchronisiert. Dadurch werden Entitätsschema und -elemente erstellt, gelöscht und geändert.  
  
 Nachdem eine Synchronisierungspartnerschaft eingerichtet wurde, kann die Zielentität nur durch den Synchronisierungsprozess geändert werden. Eine Synchronisierungspartnerschaft kann jederzeit entfernt werden, um die Zielentität bearbeitbar zu machen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen und Ausführen einer Entitäten-Synchronisierungs Partnerschaft &#40;Master Data Services&#41;](../master-data-services/create-and-execute-an-entity-sync-relationship-master-data-services.md)   
 [Bearbeiten und Löschen einer Entitäten-Synchronisierungspartnerschaft &#40;Master Data Services&#41;](../master-data-services/edit-and-delete-an-entity-sync-relationship-master-data-services.md)  
  
  
