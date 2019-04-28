---
title: Typen von Dimensionsattributen | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 663c26ac169c11e5ab2d9b90285419cf4145368c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63025769"
---
# <a name="database-dimension-properties---types"></a>Eigenschaften von Datenbankdimensionen – Typen
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Die **Typ** Einstellung der Eigenschaft enthält Informationen über den Inhalt einer Dimension für Server- und Clientanwendungen bereit. In einigen Fällen die **Typ** Einstellung nur Anleitungen für Clientanwendungen bereit und ist optional. In anderen Fällen z. B. **Konten** oder **Zeit** Dimensionen, die **Typ** eigenschafteneinstellungen für die Dimension und ihre Attribute bestimmen bestimmte serverbasiertes Verhalten und möglicherweise erforderlich, um bestimmte Verhalten im Cube zu implementieren. Z. B. die **Typ** -Eigenschaft einer Dimension kann festgelegt werden, um **Konten** Clientanwendungen an, dass die Standarddimension Kontoattribute enthält. Weitere Informationen über die Zeit, Konto und währungsdimensionen finden Sie unter [Erstellen eines datumstyps Dimension](../../analysis-services/multidimensional-models/database-dimensions-create-a-date-type-dimension.md), [Erstellen eines Finanzkontos des über-und untergeordneten Typs Dimension](../../analysis-services/multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md), und [erstellen Sie eine Währung Geben Sie die Dimension](../../analysis-services/multidimensional-models/database-dimensions-create-a-currency-type-dimension.md).  
  
 Die Standardeinstellung für den Dimensionstyp ist **regulären**, womit keine Annahmen zum Inhalt der Dimension. Dies ist die Standardeinstellung für alle Dimensionen, wenn Sie zunächst eine Dimension definieren, es sei denn, Sie geben **Zeit** beim Definieren der Dimensions mithilfe des Dimensions-Assistenten. Sie sollten auch eine verlassen **regulären** den Dimensionstyp aus, wenn der Dimensions-Assistent einen geeigneten Typ für die Zeitdimension ein Dimensionstyp nicht aufgelistet wird.  
  
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
 [Erstellen einer Dimension anhand einer vorhandenen Tabelle](../../analysis-services/multidimensional-models/create-a-dimension-by-using-an-existing-table.md)   
 [Dimensionen &#40;Analysis Services – mehrdimensionale Daten&#41;](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  
