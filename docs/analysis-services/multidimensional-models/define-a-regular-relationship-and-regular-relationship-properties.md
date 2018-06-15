---
title: Definieren einer regulären Beziehung und reguläre Beziehungseigenschaften | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9ee79742f919d7f47ae73968666d96622e3429bc
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34022277"
---
# <a name="define-a-regular-relationship-and-regular-relationship-properties"></a>Definieren einer regulären Beziehung und von Eigenschaften einer regulären Beziehung
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Wenn Sie eine neue Cubedimension oder eine neue Measuregruppe definieren, versucht [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] zu erkennen, ob eine reguläre Beziehung vorhanden ist, und legt dann die Einstellung für die Dimensionsverwendung auf **Regulär**fest. Sie können eine reguläre Dimensionsbeziehung im Cube-Designer auf der Registerkarte **Dimensionsverwendung** anzeigen oder bearbeiten.  
  
 Beim Definieren der Beziehung einer Cubedimension zu einer Measuregruppe geben Sie auch das Granularitätsattribut für die Beziehung an. Das Granularitätsattribut definiert die niedrigste Detailstufe, die im Cube für die entsprechende Dimension verfügbar ist. Im Allgemeinen ist dies das Schlüsselattribut für die Dimension. Mitunter kann es jedoch gewünscht sein, die Granularität einer bestimmten Cubedimension in einer bestimmten Measuregruppe auf eine andere Einheit festzulegen. So könnte es beispielsweise gewünscht sein, das Granularitätsattribut für die Time-Dimension auf das Month-Attribut anstatt auf das Day-Attribut festzulegen, wenn Sie eine Sales Quotas- oder Budget-Measuregruppe verwenden. Wenn Sie ein anderes als das Schlüsselattribut als Granularitätsattribut festlegen, müssen Sie sicherstellen, dass alle anderen Attribute in der Dimension über Attributbeziehungen direkt oder indirekt mit diesem anderen Attribut verknüpft sind. Andernfalls ist [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] nicht in der Lage, Daten ordnungsgemäß zu aggregieren.  
  
  
