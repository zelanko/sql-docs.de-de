---
title: Automatisches Definieren eines neues Attributs | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e6191af998108de112a81ab3a5b4edbaa7a49d18
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="attribute-properties---define-a-new-attribute-automatically"></a>Attributeigenschaften – Automatisches Definieren eines neuen Attributs
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Sie können ein neues Attribut in einer Dimension erstellen, indem Sie die Drag & Drop-Bearbeitung im Dimensions-Designer verwenden.  
  
### <a name="to-create-a-new-attribute-automatically"></a>So erstellen Sie automatisch ein neues Attribut  
  
1.  Öffnen Sie im Dimensions-Designer die Dimension, in der Sie das Attribut erstellen möchten.  
  
2.  Wählen Sie auf der Registerkarte **Dimensionsstruktur** im Bereich **Datenquellensicht** die Spalte aus der Tabelle aus, an die Sie das Attribut binden möchten, und ziehen Sie dann die Spalte in den Bereich **Attribute** .  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] erstellt das neue Attribut mit demselben Namen wie die Spalte, an die es gebunden ist. Wird die Spalte von mehreren Attributen verwendet, fügt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] eine Nummer an den Attributnamen an.  
  
## <a name="see-also"></a>Siehe auch  
 [Dimensionen in mehrdimensionalen Modellen](../../analysis-services/multidimensional-models/dimensions-in-multidimensional-models.md)   
 [Dimensionsattributeigenschaftenverweis](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
