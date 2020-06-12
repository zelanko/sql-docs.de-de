---
title: Definieren und Identifizieren von Objekten (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [XML for Analysis]
- identifying objects [XML for Analysis]
- XML for Analysis, objects
- object references [XML for Analysis]
- object identifiers [XML for Analysis]
- object definitions [XML for Analysis]
- XMLA, objects
ms.assetid: 43b65f6d-0123-4556-81f0-c7a0b84361e5
author: minewiskan
ms.author: owend
ms.openlocfilehash: d2fd3263a2f8050c36747a81ab3473f5b405ef21
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545026"
---
# <a name="defining-and-identifying-objects-xmla"></a>Definieren und Identifizieren von Objekten (XMLA)
  Objekte werden in XMLA-Befehlen (XML for Analysis) mithilfe von Objektbezeichnern und Objektverweisen identifiziert und mithilfe von ASSL-Elementen (Analysis Services Scripting Language) definiert.  
  
## <a name="object-identifiers"></a>Objektbezeichner  
 Ein-Objekt wird mit dem eindeutigen Bezeichner des-Objekts identifiziert, das in einer Instanz von definiert ist [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Objektbezeichner können entweder explizit angegeben oder durch die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz bestimmt werden, wenn [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] das Objekt erstellt. Mit der [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) -Methode können Sie Objekt Bezeichner für nachfolgende `Discover` oder [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) -Methodenaufrufe abrufen.  
  
## <a name="object-references"></a>Objektverweise  
 Mehrere XMLA-Befehle, z. b. " [Delete](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/delete-element-xmla) " oder " [Process](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla)", verwenden einen Objekt Verweis, um auf eindeutige Weise auf ein Objekt zu verweisen. Ein Objektverweis enthält den Objektbezeichner des Objekts, für das ein Befehl ausgeführt wird, sowie die Objektbezeichner der Vorgänger dieses Objekts. Beispielsweise enthält der Objektverweis für eine Partition den Objektbezeichner der Partition sowie die Objektbezeichner der übergeordneten Measuregruppe, des übergeordneten Cubes und der übergeordneten Datenbank dieser Partition.  
  
## <a name="object-definitions"></a>Objektdefinitionen  
 Die Befehle [Create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) und [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) in XMLA erstellen bzw. ändern Objekte einer- [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instanz. Die Definitionen für diese Objekte werden durch ein [ObjectDefinition](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/objectdefinition-element-xmla) -Element dargestellt, das Elemente aus ASSL enthält. Objekt Bezeichner können mit dem [ID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) -Element für alle Haupt-und viele neben Objekte explizit angegeben werden. Wenn das `ID`-Element nicht verwendet wird, stellt die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz einen eindeutigen Bezeichner mit einer Benennungskonvention bereit, die von dem zu identifizierenden Objekt abhängt. Weitere Informationen zur Verwendung der `Create` `Alter` Befehle und zum Definieren von Objekten finden Sie unter [Erstellen und Ändern von Objekten &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Object-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)   
 [Element Object-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)   
 [Quell Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla)   
 [Target-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla)   
 [Entwickeln mit XMLA in Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
