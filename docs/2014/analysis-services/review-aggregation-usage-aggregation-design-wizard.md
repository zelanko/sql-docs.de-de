---
title: Aggregations Verwendung überprüfen (Aggregations Entwurfs-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.aggregationdesignwizard.reviewusage.f1
ms.assetid: 107ee872-3df2-4931-b56c-af11e38f6745
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0a248721ee64ff815c1b5b73a81d3b29fc5d2b84
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547402"
---
# <a name="review-aggregation-usage-aggregation-design-wizard"></a>Aggregationsverwendung überprüfen (Aggregationsentwurfs-Assistent)
  Mithilfe der Seite **Aggregationsverwendung überprüfen** können Sie die Einstellungen für die Aggregationsverwendung konfigurieren.  
  
## <a name="options"></a>Optionen  
 **Standard**  
 Wählen Sie diese Option aus, um die Einstellung der Aggregationsverwendung für das Attribut auf den Standard festzulegen. Bei dieser Einstellung wendet der Designer eine Standardregel basierend auf dem Typ des Attributs und der Dimension an.  
  
 `Full`  
 Wählen Sie diese Option aus, um die Aggregationsverwendung für das Attribut auf `Full` festzulegen. Bei Verwendung dieser Einstellung muss jede Aggregation für den Cube dieses Attribut oder ein verknüpftes Attribut enthalten, das sich weiter unten in der Attributkette befindet. Die Einstellung `Full` für die Aggregationsverwendung sollte vermieden werden, wenn ein Attribut viele Elemente enthält. Falls diese Einstellung für mehrere Attribute oder für Attribute definiert ist, die über viele Elemente verfügen, kann hierdurch aufgrund einer Größenüberschreitung der Entwurf von Aggregationen verhindert werden.  
  
 **None**  
 Wählen Sie diese Option aus, um keine Aggregationsverwendung für das Attribut festzulegen. Wird diese Einstellung verwendet, kann keine Aggregation für den Cube dieses Attribut enthalten.  
  
 `Unrestricted`  
 Wählen Sie diese Option aus, um die Aggregationsverwendung für das Attribut auf `Unrestricted` festzulegen. Bei Verwendung dieser Einstellung werden keine Einschränkungen auf den Aggregations-Designer angewendet, das Attribut muss aber dennoch ausgewertet werden, um festzustellen, ob es sich um einen wertvollen Aggregationskandidaten handelt.  
  
 **Alle als Standard festlegen**  
 Wählen Sie diese Option aus, um die Einstellungen der Aggregationsverwendung für alle Attribute auf den Standard festzulegen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aggregations Entwurfs-Assistent F1-Hilfe](aggregation-design-wizard-f1-help.md)   
 [Analysis Services Assistenten &#40;Mehrdimensionale Daten&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  
