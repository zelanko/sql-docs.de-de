---
title: Automatisches Definieren eines neues Attributs | Microsoft-Dokumentation
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
- automatic attribute creation
- attributes [Analysis Services], creating
ms.assetid: 208a050a-5e2f-470c-b645-8d835e123db7
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 74b4e1950e6a31675994b7cae1562ff92a56de4a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299190"
---
# <a name="define-a-new-attribute-automatically"></a>Automatisches Definieren eines neuen Attributs
  Sie können ein neues Attribut in einer Dimension erstellen, indem Sie die Drag & Drop-Bearbeitung im Dimensions-Designer verwenden.  
  
### <a name="to-create-a-new-attribute-automatically"></a>So erstellen Sie automatisch ein neues Attribut  
  
1.  Öffnen Sie im Dimensions-Designer die Dimension, in der Sie das Attribut erstellen möchten.  
  
2.  Wählen Sie auf der Registerkarte **Dimensionsstruktur** im Bereich **Datenquellensicht** die Spalte aus der Tabelle aus, an die Sie das Attribut binden möchten, und ziehen Sie dann die Spalte in den Bereich **Attribute** .  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] erstellt das neue Attribut mit demselben Namen wie die Spalte, an die es gebunden ist. Wird die Spalte von mehreren Attributen verwendet, fügt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] eine Nummer an den Attributnamen an.  
  
## <a name="see-also"></a>Siehe auch  
 [Dimensionen in mehrdimensionalen Modellen](dimensions-in-multidimensional-models.md)   
 [Dimensionsattributeigenschaften-Verweis](dimension-attribute-properties-reference.md)  
  
  
