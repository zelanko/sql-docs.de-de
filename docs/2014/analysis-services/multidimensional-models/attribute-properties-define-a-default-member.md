---
title: Definieren eines Standardmembers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- default members
- attributes [Analysis Services], default members
- members [Analysis Services], default
- DefaultMember property
ms.assetid: db487856-ee21-49c3-aa08-d9136e193374
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 959645223eacec6c000ddbfa23615b7949d10d5a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66077420"
---
# <a name="define-a-default-member"></a>Definieren eines Standardelements
  Das Standardelement einer Attributhierarchie wird zum Auswerten von Ausdrücken verwendet, wenn eine Attributhierarchie nicht in einer Abfrage enthalten ist. Das Standardelement wird ignoriert, wenn eine Abfrage eine Attributhierarchie oder eine benutzerdefinierte Hierarchie einschließt, die das Quellattribut der Attributhierarchie enthält. Der Grund dafür ist, dass hier das in der Abfrage angegebene Element verwendet wird.  
  
 Das Standardelement einer Attributhierarchie wird festgelegt, indem ein Attributelement als `DefaultMember`-Eigenschaftswert der Attributhierarchie angegeben wird. Diese Eigenschaft legen Sie auf der Registerkarte Dimensionsstruktur des Dimensions-Designers oder im Kalkulationsskript auf der Registerkarte Berechnung des Cube-Designers in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]fest. Sie können die `DefaultMember`-Eigenschaft auch für eine Sicherheitsrolle angeben (und damit das für die Dimension festgelegte Standardelement überschreiben). Öffnen Sie dazu während der Definition der Dimensionssicherheit die Registerkarte Dimensionsdaten. Wenn Sie Namensauflösungsprobleme in folgenden Situationen vermeiden möchten, definieren Sie das Standardelement im MDX-Skript des Cubes: wenn der Cube mehr als einmal auf eine Datenbankdimension verweist; wenn die Dimension im Cube einen anderen Namen aufweist als die Dimension in der Datenbank; wenn Sie in verschiedenen Cubes verschiedene Standardelemente verwenden möchten.  
  
 Das Standardelement eines Attributs wird zum Auswerten von Ausdrücken verwendet, wenn ein Attribut nicht in einer Abfrage enthalten ist. Das Standardelement eines Attributs wird durch die `DefaultMember`-Eigenschaft des Attributs angegeben. Wenn eine Hierarchie aus einer Dimension in einer Abfrage enthalten ist, werden alle Standardelemente von Attributen ignoriert, die Ebenen in der Hierarchie entsprechen. Ist keine Hierarchie aus einer Dimension in einer Abfrage enthalten, werden für alle Attribute in der Dimension Standardelemente verwendet.  
  
## <a name="resolving-the-default-member-when-no-default-member-is-specified"></a>Auflösen des Standardelements, wenn kein Standardelement angegeben ist  
 Wird für eine Attributhierarchie kein Standardelement angegeben, und kann die Attributhierarchie aggregiert werden (die `IsAggregatable`-Eigenschaft des Attributs ist auf `True` festgelegt), ist das (Alle)-Element das Standardelement. Wird kein Standardelement angegeben, und kann die Attributhierarchie nicht aggregiert werden (die `IsAggregatable`-Eigenschaft des Attributs ist auf `False` festgelegt), wird ein Standardelement aus der obersten Ebene der Attributhierarchie ausgewählt.  
  
## <a name="specifying-the-default-member"></a>Festlegen des Standardelements  
 Jedes Attribut in einer Dimension in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] verfügt über ein Standardmember, das Sie mithilfe der `DefaultMember` -Eigenschaft für ein Attribut angeben können. Diese Einstellung wird zum Auswerten von Ausdrücken verwendet, wenn ein Attribut nicht in einer Abfrage enthalten ist. Legt eine Abfrage eine Hierarchie in einer Dimension fest, werden die Standardelemente für die Attribute in der Hierarchie ignoriert. Wenn eine Abfrage keine Hierarchie in einer Dimension angibt, treten die `DefaultMember` Einstellungen für Dimensions Attribute in Kraft.  
  
 Wenn die `DefaultMember` Einstellung für ein Attribut leer ist und die `IsAggregatable` -Eigenschaft auf `True`festgelegt ist, ist das Standardelement das alle-Element. Wenn die `IsAggregatable` -Eigenschaft auf `False`festgelegt ist, ist das Standardelement das erste Element der ersten sichtbaren Ebene.  
  
 Die `DefaultMember` -Einstellung für ein Attribut gilt für jede Hierarchie, an der das Attribut beteiligt ist. Sie können für verschiedene Hierarchien in einer Dimension keine unterschiedlichen Einstellungen verwenden. Wenn beispielsweise das Element [1998] das Standardelement für ein [Year]-Attribut ist, gilt diese Einstellung für jede Hierarchie in der Dimension. Die `DefaultMember` Einstellung in diesem Fall darf nicht [1998] in einer Hierarchie und [1997] in einer anderen Hierarchie sein.  
  
 Wenn Sie ein Standardelement für eine bestimmte Ebene in einer Hierarchie definieren, das nicht auf natürliche Weise aggregiert, müssen Sie in allen Ebenen über dieser Ebene in der Hierarchie Standardelemente definieren. Beispielsweise können Sie in der Hierarchie "All-Länder-Climate" kein Standardelement für "Klima" definieren, es sei denn, Sie definieren ein Standardelement für Länder. Tun Sie dies nicht, führt dies zu Abfragezeitfehlern.  
  
 Wenn Ebenen in einer Hierarchie natürlich aggregieren, können Sie ein Standardelement für ein beliebiges Attribut in der Hierarchie definieren, ohne andere Attribute in der Hierarchie berücksichtigen zu müssen. In der Hierarchie Country-Province-City können Sie z. b. ein Standardelement für City wie [City] definieren. [Montreal], ohne das Standardelement für State oder für Country zu definieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren der Ebene &#40;Alle&#41; für Attributhierarchien](database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  
