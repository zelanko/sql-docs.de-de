---
title: Konfigurieren der alle-Ebene für Attributhierarchien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- All members
- IsAggregatable property
- topmost levels [Analysis Services]
- (All) levels
- AttributeAllMemberName property
- levels [Analysis Services]
- members [Analysis Services], All
- AllMemberName property
ms.assetid: 0cb35e6f-b10f-483d-b893-78f6ca3979fd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 96e7e0cd5377e180630f10bdae6c32e33fcd119b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48171620"
---
# <a name="configure-the-all-level-for-attribute-hierarchies"></a>Konfigurieren der Ebene (aller Ebenen) für Attributhierarchien
  Die Alle-Ebene in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ist eine optionale, vom System generierte Ebene. Sie enthält nur ein Element, dessen Wert die Aggregation der Werte aller Elemente in der direkt untergeordneten Ebene ist. Dieses Element wird als Alle-Element bezeichnet. Das vom System erzeugte Element ist nicht in der Dimensionstabelle enthalten. Da sich das Element in der Gesamtergebnisebene an oberster Stelle in der Hierarchie befindet, ist der Wert des Elements die konsolidierte Aggregation der Werte aller Elemente in der Hierarchie. Das Alle-Element dient häufig als Standardelement einer Hierarchie.  
  
 Das Vorhandensein einer alle-Ebene in einer Attributhierarchie hängt von der `IsAggregatable` Einstellung der Eigenschaft für das Attribut und das Vorhandensein einer alle-Ebene in einer benutzerdefinierten Hierarchie hängt von der `IsAggregatable` -Eigenschaft des Attributs auf der obersten Ebene der eine benutzerdefinierte Hierarchie. Wenn die `IsAggregatable`-Eigenschaft auf `True` festgelegt ist, ist eine Alle-Ebene vorhanden. In einer Hierarchie ist keine Alle-Ebene vorhanden, wenn die `IsAggregatable`-Eigenschaft auf `False` festgelegt ist.  
  
## <a name="establishing-the-topmost-level"></a>Einrichten der obersten Ebene  
 Wenn die `IsAggregatable`-Eigenschaft für das Quellattribut einer Ebene in einer Hierarchie auf `False` festgelegt ist, kann in der Hierarchie über dieser Ebene keine Aggregatebene vorkommen. Eine Nichtaggregatebene muss die oberste Ebene jeder Hierarchie sein, oder die `IsAggregatable`-Eigenschaft der Quellattribute für alle Ebenen darüber müssen ebenfalls auf `False` festgelegt sein.  
  
## <a name="all-member-and-all-level"></a>Alle-Element und Alle-Ebene  
 Das einzige Element der Alle-Ebene wird als Alle-Element bezeichnet. Die `AttributeAllMemberName`-Eigenschaft einer Dimension gibt den Namen des alle-Elements für Attribute in einer Dimension. Die `AllMemberName`-Eigenschaft in einer Hierarchie gibt den Namen des Alle-Elements für die Hierarchie an.  
  
## <a name="see-also"></a>Siehe auch  
 [Definieren eines Standardelements](attribute-properties-define-a-default-member.md)  
  
  
