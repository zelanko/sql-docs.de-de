---
title: Aggregationsverwendung überprüfen (Assistent für Verwendungsbasierte für Verwendungsbasierte Optimierung) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.storagedesignwizard.reviewaggregationusage.f1
ms.assetid: 49ce2094-c4dc-4e46-8cef-c17c5db084ca
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 21618aabe9c7e429c7d78a68c7fcfb9d61a0754c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060130"
---
# <a name="review-aggregation-usage-usage-based-optimiation-wizard"></a>Aggregationsverwendung überprüfen (Assistent für verwendungsbasierte Optimierung)
  Mithilfe der Seite **Aggregationsverwendung überprüfen** können Sie die Einstellungen für die Aggregationsverwendung konfigurieren.  
  
## <a name="options"></a>Tastatur  
 **Default**  
 Wählen Sie diese Option aus, um die Einstellung der Aggregationsverwendung für das Attribut auf den Standard festzulegen. Bei dieser Einstellung wendet der Designer eine Standardregel basierend auf dem Typ des Attributs und der Dimension an.  
  
 **Full**  
 Wählen Sie diese Option aus, um die vollständige Aggregationsverwendung für das Attribut festzulegen. Bei Verwendung dieser Einstellung muss jede Aggregation für den Cube dieses Attribut oder ein verknüpftes Attribut enthalten, das sich weiter unten in der Attributkette befindet. Die Einstellung für die vollständige Aggregationsverwendung sollte vermieden werden, wenn ein Attribut viele Elemente enthält. Falls diese Einstellung für mehrere Attribute oder für Attribute definiert ist, die über viele Elemente verfügen, kann hierdurch aufgrund einer Größenüberschreitung der Entwurf von Aggregationen verhindert werden.  
  
 **Keine**  
 Wählen Sie diese Option aus, um keine Aggregationsverwendung für das Attribut festzulegen. Wird diese Einstellung verwendet, kann keine Aggregation für den Cube dieses Attribut enthalten.  
  
 **Nicht eingeschränkt**  
 Wählen Sie diese Option aus, um eine uneingeschränkte Aggregationsverwendung für das Attribut festzulegen. Wird diese Einstellung verwendet, werden keine Einschränkungen auf den Aggregations-Designer angwendet. Das Attribut muss aber dennoch ausgewertet werden, um festzustellen, ob es sich um einen wertvollen Aggregationskandidaten handelt.  
  
 **Festlegen Sie alle als Standard**  
 Wählen Sie diese Option aus, um die Einstellungen der Aggregationsverwendung für alle Attribute auf den Standard festzulegen.  
  
## <a name="see-also"></a>Siehe auch  
 [Aggregationsentwurfs-Assistent F1 Hilfe](aggregation-design-wizard-f1-help.md)   
 [Analysis Services-Assistenten &#40;mehrdimensionale Daten&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  