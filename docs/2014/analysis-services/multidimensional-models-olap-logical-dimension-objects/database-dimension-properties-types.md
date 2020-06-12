---
title: Dimensions Typen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
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
ms.openlocfilehash: 5e0c16a57081aa1d9ed3cc6964d1f17fa7135986
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545185"
---
# <a name="dimension-types"></a>Dimensionstypen
  In der Einstellung der `Type`-Eigenschaft werden Informationen zum Inhalt einer Dimension für Server- und Clientanwendungen bereitgestellt. In einigen Fällen wird in der `Type`-Einstellung nur ein Hinweis für Clientanwendungen bereitgestellt, sie ist dann optional. In anderen Fällen, z. B. für die `Accounts`- oder `Time`-Dimension, wird durch die Einstellungen der `Type`-Eigenschaft für die Dimension und ihre Attribute ein spezifisches serverbasiertes Verhalten festgelegt. Die Einstellungen können dann erforderlich sein, um ein bestimmtes Verhalten im Cube zu implementieren. So kann z. B. die `Type`-Eigenschaft einer Dimension auf `Accounts` festgelegt werden, um den Clientanwendungen mitzuteilen, dass die Standarddimension Kontoattribute enthält. Weitere Informationen zu Zeit-, Konto-und Währungs Dimensionen finden Sie unter [Create a Date Type Dimension](../multidimensional-models/database-dimensions-create-a-date-type-dimension.md), [Create a Finance Account of Parent-Child Type Dimension](../multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md)und [Create a Currency Type Dimension](../multidimensional-models/database-dimensions-create-a-currency-type-dimension.md).  
  
 Die Standardeinstellung für den Dimensionstyp ist `Regular`, sie bietet keine Informationen zum Inhalt der Dimension. Das ist die Standardeinstellung für alle Dimensionen beim ersten Definieren einer Dimension, es sei denn, Sie haben beim Definieren der Dimension mithilfe des Dimensions-Assistenten `Time` angegeben. Sie sollten auch die Einstellung `Regular` für den Dimensionstyp beibehalten, wenn im Dimensions-Assistent kein geeigneter Typ aufgelistet wird.  
  
## <a name="available-dimension-types"></a>Verfügbare Dimensionstypen  
 In der folgenden Tabelle werden die in verfügbaren Dimensions Typen beschrieben [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
|Dimensionstyp|Beschreibung|  
|--------------------|-----------------|  
|Regular|Eine Dimension, für die kein spezieller Dimensionstyp festgelegt wurde|  
|Time|Eine Dimension, deren Attribute Zeiträume darstellen, z. B. Jahre, Semester, Quartale, Monate und Tage|  
|Organization|Eine Dimension, deren Attribute organisatorische Informationen darstellen, z. B. Angestellte oder Tochterunternehmen|  
|Gebiet|Eine Dimension, deren Attribute geografische Informationen darstellen, z. B. Städte oder Postleitzahlen|  
|BillOfMaterials|Eine Dimension, deren Attribute Informationen zu Inventar oder Produktion darstellen, z. B. Stücklisten für Produkte|  
|Konten|Eine Dimension, deren Attribute ein Kontodiagramm für Finanzberichte darstellen|  
|Kunden|Eine Dimension, deren Attribute Kunden- oder Kontaktinformationen darstellen|  
|Produkte|Eine Dimension, deren Attribute Produktinformationen darstellen|  
|Szenario|Eine Dimension, deren Attribute Informationen für Planung oder strategische Analyse darstellen|  
|Quantitative|Eine Dimension, deren Attribute quantitative Informationen darstellen|  
|Hilfsprogramm|Eine Dimension, deren Attribute verschiedene Informationen darstellen|  
|Währung|Dieser Dimensionstyp enthält Währungsdaten und Metadaten|  
|Rates|Eine Dimension, deren Attribute Währungskursinformationen darstellen|  
|Channel|Eine Dimension, deren Attribute verschiedene Kanalinformationen darstellen|  
|Promotion|Eine Dimension, deren Attribute verschiedene Marketinghöherstufungsinformationen darstellen|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer Dimension mithilfe einer vorhandenen Tabelle](../multidimensional-models/create-a-dimension-by-using-an-existing-table.md)   
 [Dimensionen &#40;Analysis Services – mehrdimensionale Daten&#41;](dimensions-analysis-services-multidimensional-data.md)  
  
  
