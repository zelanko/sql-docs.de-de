---
title: Erstellen eine währungstypdimension | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], currency
- currency [Analysis Services]
- converting currency
- currency dimensions [Analysis Services]
ms.assetid: b1f037d1-ce47-4e47-a1c2-5ec9e781cff6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dc9b89f4c1d3a1a44d5a568a47d16276639bb4cf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48140390"
---
# <a name="create-a-currency-type-dimension"></a>Erstellen einer Währungstypdimension
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]ist eine Dimension vom Typ "Währung" eine Dimension, deren Attribute eine Auflistung von Währungen für Finanzberichte darstellt.  
  
 Mit einer Währungsdimension können Sie einem Cube in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]Funktionen für die Währungsumrechnung hinzufügen. Wenn Sie einem Cube die Währungsumrechnung hinzufügen möchten, verwenden Sie den Business Intelligence-Assistenten zum Definieren eines Multidimensional Expressions-(MDX-)Skriptbefehls, der Währungsmeasures in Werte konvertiert, die für das Gebietsschema der Clientanwendung geeignet sind. Um dieses MDX-Skript erstellen zu können, benötigt der Business Intelligence-Assistent folgende Informationen:  
  
-   Eine Währungsdimension, die Quellwährungen darstellt. (Bei dieser Dimension handelt es sich um die Quellwährungsdimension.)  
  
-   Eine Measuregruppe, die die zu verwendenden Wechselkurse darstellt.  
  
 Anhand dieser Informationen entwirft der Business Intelligence-Assistent einen Währungsumrechnungsprozess, der die entsprechende Zielwährungsdimension (die Währungsdimension, die Zielwährungen darstellt) identifiziert. Abhängig von der Anzahl der Währungsumrechnungen, die für Ihre Business Intelligence-Lösung erforderlich sind, kann der Business Intelligence-Assistent mehrere Zielwährungsdimensionen definieren. Weitere Informationen zum Definieren von Währungsumrechnungen finden Sie unter [Währungsumrechnungen &#40;Analysis Services&#41;](../currency-conversions-analysis-services.md).  
  
 Um eine Dimension als Währungsdimension identifizieren möchten, legen die `Type` Eigenschaft der Dimension auf `Currency`.  
  
## <a name="dimension-structure"></a>Dimensionsstruktur  
 Eine Währungsdimension enthält zumindest ein Schlüsselattribut, das die einzelnen Währungen in der Dimensionstabelle für die Währungsdimension identifiziert. Der Wert des Schlüsselattributs ist in Quell- und Zielwährungsdimensionen unterschiedlich.  
  
-   Wenn Sie ein Attribut als Schlüsselattribut einer Quellwährungsdimension identifizieren möchten, legen Sie die `Type`-Eigenschaft des Attributs auf `CurrencySource` fest.  
  
-   Um ein Attribut als zielwährungsdimension identifizieren möchten, legen die `Type` -Eigenschaft des Attributs auf `CurrencyDestination`.  
  
 Für Berichtszwecke enthalten sowohl Quell- als auch Zielwährungsdimensionen optional folgende Attribute:  
  
-   Ein Attribut für den Namen der Währung.  
  
     Wenn Sie ein Attribut als Attribut für den Namen der Währung identifizieren möchten, legen Sie die `Type`-Eigenschaft des Attributs auf `CurrencyName` fest.  
  
-   Ein Attribut für die Quelle der Währung.  
  
     Wenn Sie ein Attribut als Attribut für die Quelle der Währung identifizieren möchten, legen Sie die `Type`-Eigenschaft des Attributs auf `CurrencySource` fest.  
  
-   Einen Währungscode gemäß der International Standards Organization (ISO).  
  
     Um ein Attribut als eine Währung ISO-Code-Attribut zu identifizieren, legen die `Type` -Eigenschaft des Attributs auf `CurrencyIsoCode`.  
  
 Weitere Informationen zu Attributtypen finden Sie unter [Konfigurieren von Attributtypen](attribute-properties-configure-attribute-types.md).  
  
## <a name="defining-account-intelligence-with-the-business-intelligence-wizard"></a>Definieren von Kontointelligenz mit dem Business Intelligence-Assistenten  
 Nachdem Sie eine Kontodimension definiert und diese Dimension einem Cube hinzugefügt haben, können Sie den Business Intelligence-Assistenten verwenden, um der Dimension die Kontointelligenzfunktionalität hinzuzufügen, beispielsweise das Identifizieren und Zuordnen von Kontotypen. Weitere Informationen finden Sie unter [Hinzufügen von Kontointelligenz zu einer Dimension](bi-wizard-add-account-intelligence-to-a-dimension.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Attribute und Attributhierarchien](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Business Intelligence-Assistent F1-Hilfe](../business-intelligence-wizard-f1-help.md)   
 [Dimensionstypen](../multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md)  
  
  
