---
title: Erstellen eines Finance-Kontos der Dimension "Parent-Child Type" | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], account
- account dimensions [Analysis Services]
- adding account intelligence
- account intelligence [Analysis Services]
ms.assetid: 2ba74e81-5b4b-407e-acdf-deb2f6accf0a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 28a7cf6b3a712144daead54d521fb3cc6936c99e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66075922"
---
# <a name="create-a-finance-account-of-parent-child-type-dimension"></a>Erstellen eines Finanzkontos des über- und untergeordneten Typs Dimension
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]handelt es sich bei einer Kontotyp Dimension um eine Dimension, deren Attribute ein Diagramm der Konten für Finanz Berichterstattungs Zwecke darstellen.  
  
 Mit einer Kontodimension können Sie selektiv das Aggregationsverhalten für Konten im Lauf der Zeit verwalten. Eine Kontodimension ermöglicht auch das Verwenden eines Standardmechanismus, mit dem die meisten der vom Standard abweichenden Aggregationsprobleme behoben werden können, die in Business Intelligence-Projektmappen für den Umgang mit Finanzdaten typischerweise auftreten. Wenn Sie bisher nicht über einen solchen Standardmechanismus verfügt haben, waren zum Beheben dieser vom Standard abweichenden Aggregationsprobleme benutzerdefinierte Rollupformeln, berechnete Elemente oder MDX-Skripts (Multidimensional Expressions) erforderlich.  
  
 Um eine Dimension als eine Kontodimension zu identifizieren, legen Sie die `Type`-Eigenschaft der Dimension auf `Accounts` fest.  
  
## <a name="dimension-structure"></a>Dimensionsstruktur  
 Eine Kontodimension enthält mindestens zwei Attribute:  
  
-   Ein Schlüssel Attribut: ein Attribut, das einzelne Konten in der Dimensions Tabelle für die Konto Dimension identifiziert.  
  
-   Ein Konto Attribut: ein übergeordnetes Attribut, das beschreibt, wie Konten hierarchisch in der Konto Dimension angeordnet werden.  
  
     Um ein Attribut als Kontoattribut zu identifizieren, legen Sie die `Type`-Eigenschaft des Attributs auf `Account` und die `Usage`-Eigenschaft auf `Parent` fest.  
  
 Kontodimensionen können optional die folgenden Attribute enthalten:  
  
-   Ein Kontotyp Attribut: ein Attribut, das den Kontotyp für jedes Konto in der Dimension definiert. Die Elementnamen des Kontotypattributs sind in den Kontotypen zugeordnet, die für die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank oder das Projekt definiert sind, und geben die Aggregatfunktion an, die von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] für diese Konten verwendet wird. Sie können auch unäre Operatoren oder benutzerdefinierte Rollupformeln verwenden, um das Aggregationsverhalten für Kontoattribute zu bestimmen, aber mit Kontotypen können Sie problemlos ein einheitliches Verhalten für ein Kontodiagramm durchsetzen, ohne dass dazu Änderungen an der zugrunde liegenden relationalen Datenbank erforderlich sind.  
  
     Um ein Kontotypattribut zu identifizieren, legen Sie die `Type`-Eigenschaft des Attributs auf `AccountType` fest.  
  
-   Ein Konto Namensattribut-ein Attribut, das zu Berichtszwecken verwendet wird. Um ein Kontonamenattribut zu identifizieren, legen Sie die `Type`-Eigenschaft des Attributs auf `AccountName` fest.  
  
-   Ein Kontonummern Attribut: ein Attribut, das zu Berichtszwecken verwendet wird. Um ein Kontonummernattribut zu identifizieren, legen Sie die `Type`-Eigenschaft des Attributs auf `AccountNumber` fest.  
  
 Weitere Informationen zu Attributtypen finden Sie unter [Konfigurieren von Attributtypen](attribute-properties-configure-attribute-types.md).  
  
## <a name="adding-account-intelligence-with-the-business-intelligence-wizard"></a>Hinzufügen von Kontointelligenz mit dem Business Intelligence-Assistenten  
 Nachdem Sie eine Kontodimension definiert und diese Dimension zu einem Cube hinzugefügt haben, können Sie den Business Intelligence-Assistenten verwenden, um der Dimension Kontointelligenzfunktionalität hinzuzufügen, z. B. zum Identifizieren und Zuordnen von Kontotypen. Weitere Informationen finden Sie unter [Hinzufügen von Kontointelligenz zu einer Dimension](bi-wizard-add-account-intelligence-to-a-dimension.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Attribute und Attribut Hierarchien](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Business Intelligence Wizard (F1-Hilfe)](../business-intelligence-wizard-f1-help.md)   
 [Dimensionstypen](../multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md)  
  
  
