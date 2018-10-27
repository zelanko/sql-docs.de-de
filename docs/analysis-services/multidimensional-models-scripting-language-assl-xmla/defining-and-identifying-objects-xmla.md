---
title: Definieren und Identifizieren von Objekten (XMLA) | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 48223f9718ae4eb87b0880c2f266c886ec7abbb0
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "50145266"
---
# <a name="defining-and-identifying-objects-xmla"></a>Definieren und Identifizieren von Objekten (XMLA)
  Objekte werden in XMLA-Befehlen (XML for Analysis) mithilfe von Objektbezeichnern und Objektverweisen identifiziert und mithilfe von ASSL-Elementen (Analysis Services Scripting Language) definiert.  
  
## <a name="object-identifiers"></a>Objekt-IDs  
 Ein Objekt wird mithilfe des eindeutigen Bezeichners des Objekts gemäß der in einer Instanz von identifiziert [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Objektbezeichner können entweder explizit angegeben oder durch die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz bestimmt werden, wenn [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] das Objekt erstellt. Können Sie die [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) Methode zum Abrufen der Objektbezeichner für nachfolgende **Discover** oder [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) Methodenaufrufe.  
  
## <a name="object-references"></a>Objektverweise  
 Zahlreiche XMLA-Befehle wie z. B. [löschen](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/delete-element-xmla) oder [Prozess](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla), verwenden Sie einen Objektverweis auf um eindeutige Weise auf ein Objekt zu verweisen. Ein Objektverweis enthält den Objektbezeichner des Objekts, für das ein Befehl ausgeführt wird, sowie die Objektbezeichner der Vorgänger dieses Objekts. Beispielsweise enthält der Objektverweis für eine Partition den Objektbezeichner der Partition sowie die Objektbezeichner der übergeordneten Measuregruppe, des übergeordneten Cubes und der übergeordneten Datenbank dieser Partition.  
  
## <a name="object-definitions"></a>Objektdefinitionen  
 Die [erstellen](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) und [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) Befehle in XMLA erstellen bzw. ändern, Objekte auf einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instanz. Die Definitionen für diese Objekte werden durch dargestellt eine [ObjectDefinition](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/objectdefinition-element-xmla) -Element, das Elemente aus ASSL enthält. Objektbezeichner können explizit für alle Haupt- und nebenobjekte angegeben werden, mithilfe der [ID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) Element. Wenn die **ID** Element nicht verwendet wird, die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instanz stellt einen eindeutigen Bezeichner, mit einer Namenskonvention, die von dem zu identifizierenden Objekt abhängt. Weitere Informationen zur Verwendung der **erstellen** und **Alter** Befehle zum Definieren von Objekten finden Sie unter [erstellen und Ändern von Objekten &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/creating-and-altering-objects-xmla.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Objekt-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)   
 [ParentObject-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)   
 [Source-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla)   
 [Target-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla)   
 [Entwickeln mit XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
