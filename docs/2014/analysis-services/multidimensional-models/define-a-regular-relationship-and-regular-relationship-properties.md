---
title: Definieren einer regulären Beziehung und reguläre Beziehungseigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- granularity attribute
- relationships [Analysis Services], regular relationships
ms.assetid: 840280d8-20c3-46c0-99ea-62479469c36b
caps.latest.revision: 9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dbf4b0f179c0c4ba0990b8fe61b2cd2a7584f058
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37211930"
---
# <a name="define-a-regular-relationship-and-regular-relationship-properties"></a>Definieren einer regulären Beziehung und von Eigenschaften einer regulären Beziehung
  Wenn Sie eine neue Cubedimension oder eine neue Measuregruppe definieren, versucht [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] zu erkennen, ob eine reguläre Beziehung vorhanden ist, und legt dann die Einstellung für die Dimensionsverwendung auf `Regular` fest. Sie können eine reguläre Dimensionsbeziehung im Cube-Designer auf der Registerkarte **Dimensionsverwendung** anzeigen oder bearbeiten.  
  
 Beim Definieren der Beziehung einer Cubedimension zu einer Measuregruppe geben Sie auch das Granularitätsattribut für die Beziehung an. Das Granularitätsattribut definiert die niedrigste Detailstufe, die im Cube für die entsprechende Dimension verfügbar ist. Im Allgemeinen ist dies das Schlüsselattribut für die Dimension. Mitunter kann es jedoch gewünscht sein, die Granularität einer bestimmten Cubedimension in einer bestimmten Measuregruppe auf eine andere Einheit festzulegen. So könnte es beispielsweise gewünscht sein, das Granularitätsattribut für die Time-Dimension auf das Month-Attribut anstatt auf das Day-Attribut festzulegen, wenn Sie eine Sales Quotas- oder Budget-Measuregruppe verwenden. Wenn Sie ein anderes als das Schlüsselattribut als Granularitätsattribut festlegen, müssen Sie sicherstellen, dass alle anderen Attribute in der Dimension über Attributbeziehungen direkt oder indirekt mit diesem anderen Attribut verknüpft sind. Andernfalls ist [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] nicht in der Lage, Daten ordnungsgemäß zu aggregieren.  
  
  
