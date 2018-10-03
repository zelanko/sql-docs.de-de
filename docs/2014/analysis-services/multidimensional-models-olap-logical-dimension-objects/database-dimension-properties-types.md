---
title: Typen von Dimensionsattributen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- time dimensions [Analysis Services]
- quantitative dimensions [Analysis Services]
- BillOfMaterials dimension [Analysis Services]
- geography dimensions
- utility dimensions [Analysis Services]
- channel dimensions
- dimensions [Analysis Services], types
- products dimensions [Analysis Services]
- account dimensions [Analysis Services]
- organization dimensions
- currency dimensions [Analysis Services]
- rates dimensions
- promotion dimensions
- scenario dimensions [Analysis Services]
- customers dimensions [Analysis Services]
- Type property
ms.assetid: bd3195da-e762-4c98-b643-34c76e842343
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 61792f88c028ce1c011b91fb9a5ecbec97b50396
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48212510"
---
# <a name="dimension-types"></a>Dimensionstypen
  In der Einstellung der `Type`-Eigenschaft werden Informationen zum Inhalt einer Dimension für Server- und Clientanwendungen bereitgestellt. In einigen Fällen wird in der `Type`-Einstellung nur ein Hinweis für Clientanwendungen bereitgestellt, sie ist dann optional. In anderen Fällen, z. B. für die `Accounts`- oder `Time`-Dimension, wird durch die Einstellungen der `Type`-Eigenschaft für die Dimension und ihre Attribute ein spezifisches serverbasiertes Verhalten festgelegt. Die Einstellungen können dann erforderlich sein, um ein bestimmtes Verhalten im Cube zu implementieren. So kann z. B. die `Type`-Eigenschaft einer Dimension auf `Accounts` festgelegt werden, um den Clientanwendungen mitzuteilen, dass die Standarddimension Kontoattribute enthält. Weitere Informationen über die Zeit, Konto und währungsdimensionen finden Sie unter [Erstellen eines datumstyps Dimension](../multidimensional-models/database-dimensions-create-a-date-type-dimension.md), [Erstellen eines Finanzkontos des über-und untergeordneten Typs Dimension](../multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md), und [erstellen Sie eine Währung Geben Sie die Dimension](../multidimensional-models/database-dimensions-create-a-currency-type-dimension.md).  
  
 Die Standardeinstellung für den Dimensionstyp ist `Regular`, sie bietet keine Informationen zum Inhalt der Dimension. Das ist die Standardeinstellung für alle Dimensionen beim ersten Definieren einer Dimension, es sei denn, Sie haben beim Definieren der Dimension mithilfe des Dimensions-Assistenten `Time` angegeben. Sie sollten auch die Einstellung `Regular` für den Dimensionstyp beibehalten, wenn im Dimensions-Assistent kein geeigneter Typ aufgelistet wird.  
  
## <a name="available-dimension-types"></a>Verfügbare Dimensionstypen  
 Die folgende Tabelle beschreibt die in verfügbaren Dimensionstypen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
|Dimensionstyp|Description|  
|--------------------|-----------------|  
|Regulär|Eine Dimension, für die kein spezieller Dimensionstyp festgelegt wurde|  
|Uhrzeit|Eine Dimension, deren Attribute Zeiträume darstellen, z. B. Jahre, Semester, Quartale, Monate und Tage|  
|Organization|Eine Dimension, deren Attribute organisatorische Informationen darstellen, z. B. Angestellte oder Tochterunternehmen|  
|Geography|Eine Dimension, deren Attribute geografische Informationen darstellen, z. B. Städte oder Postleitzahlen|  
|BillOfMaterials|Eine Dimension, deren Attribute Informationen zu Inventar oder Produktion darstellen, z. B. Stücklisten für Produkte|  
|Konten|Eine Dimension, deren Attribute ein Kontodiagramm für Finanzberichte darstellen|  
|Customers|Eine Dimension, deren Attribute Kunden- oder Kontaktinformationen darstellen|  
|Products|Eine Dimension, deren Attribute Produktinformationen darstellen|  
|Szenario|Eine Dimension, deren Attribute Informationen für Planung oder strategische Analyse darstellen|  
|Quantitative|Eine Dimension, deren Attribute quantitative Informationen darstellen|  
|Hilfsprogramm|Eine Dimension, deren Attribute verschiedene Informationen darstellen|  
|Währung|Dieser Dimensionstyp enthält Währungsdaten und Metadaten|  
|Rates|Eine Dimension, deren Attribute Währungskursinformationen darstellen|  
|Channel|Eine Dimension, deren Attribute verschiedene Kanalinformationen darstellen|  
|Promotion|Eine Dimension, deren Attribute verschiedene Marketinghöherstufungsinformationen darstellen|  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer Dimension anhand einer vorhandenen Tabelle](../multidimensional-models/create-a-dimension-by-using-an-existing-table.md)   
 [Dimensionen &#40;Analysis Services – mehrdimensionale Daten&#41;](dimensions-analysis-services-multidimensional-data.md)  
  
  
