---
title: Aggregations Verwendung überprüfen (Assistent für Verwendungs basierte Optimierung) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.storagedesignwizard.reviewaggregationusage.f1
ms.assetid: 49ce2094-c4dc-4e46-8cef-c17c5db084ca
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a58f7f8620924d4f707fe61c45ae87e19737471f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66070172"
---
# <a name="review-aggregation-usage-usage-based-optimiation-wizard"></a>Aggregationsverwendung überprüfen (Assistent für verwendungsbasierte Optimierung)
  Mithilfe der Seite **Aggregationsverwendung überprüfen** können Sie die Einstellungen für die Aggregationsverwendung konfigurieren.  
  
## <a name="options"></a>Optionen  
 **Standard**  
 Wählen Sie diese Option aus, um die Einstellung der Aggregationsverwendung für das Attribut auf den Standard festzulegen. Bei dieser Einstellung wendet der Designer eine Standardregel basierend auf dem Typ des Attributs und der Dimension an.  
  
 **Vollständig**  
 Wählen Sie diese Option aus, um die vollständige Aggregationsverwendung für das Attribut festzulegen. Bei Verwendung dieser Einstellung muss jede Aggregation für den Cube dieses Attribut oder ein verknüpftes Attribut enthalten, das sich weiter unten in der Attributkette befindet. Die Einstellung für die vollständige Aggregationsverwendung sollte vermieden werden, wenn ein Attribut viele Elemente enthält. Falls diese Einstellung für mehrere Attribute oder für Attribute definiert ist, die über viele Elemente verfügen, kann hierdurch aufgrund einer Größenüberschreitung der Entwurf von Aggregationen verhindert werden.  
  
 **None**  
 Wählen Sie diese Option aus, um keine Aggregationsverwendung für das Attribut festzulegen. Wird diese Einstellung verwendet, kann keine Aggregation für den Cube dieses Attribut enthalten.  
  
 **Unbegrenzt**  
 Wählen Sie diese Option aus, um eine uneingeschränkte Aggregationsverwendung für das Attribut festzulegen. Wird diese Einstellung verwendet, werden keine Einschränkungen auf den Aggregations-Designer angwendet. Das Attribut muss aber dennoch ausgewertet werden, um festzustellen, ob es sich um einen wertvollen Aggregationskandidaten handelt.  
  
 **Alle als Standard festlegen**  
 Wählen Sie diese Option aus, um die Einstellungen der Aggregationsverwendung für alle Attribute auf den Standard festzulegen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aggregations Entwurfs-Assistent F1-Hilfe](aggregation-design-wizard-f1-help.md)   
 [Analysis Services Assistenten &#40;Mehrdimensionale Daten&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  
