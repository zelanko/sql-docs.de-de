---
title: Erstellen eines Finanzkontos des über-und untergeordneten Typs Dimension | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a9db268d931d46f6254501e95d68739c3e71db3b
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52517233"
---
# <a name="database-dimensions---finance-account-of-parent-child-type"></a>Datenbankdimensionen Sie – Finanzkontos des über-und untergeordneten Typs
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]ist eine Dimension vom Typ "Konto" eine Dimension, deren Attribute ein Kontodiagramm für Finanzberichte darstellen.  
  
 Mit einer Kontodimension können Sie selektiv das Aggregationsverhalten für Konten im Lauf der Zeit verwalten. Eine Kontodimension ermöglicht auch das Verwenden eines Standardmechanismus, mit dem die meisten der vom Standard abweichenden Aggregationsprobleme behoben werden können, die in Business Intelligence-Projektmappen für den Umgang mit Finanzdaten typischerweise auftreten. Wenn Sie bisher nicht über einen solchen Standardmechanismus verfügt haben, waren zum Beheben dieser vom Standard abweichenden Aggregationsprobleme benutzerdefinierte Rollupformeln, berechnete Elemente oder MDX-Skripts (Multidimensional Expressions) erforderlich.  
  
 Um eine Dimension als eine Kontodimension zu identifizieren, legen Sie die **Type** -Eigenschaft der Dimension auf **Accounts**fest.  
  
## <a name="dimension-structure"></a>Dimensionsstruktur  
 Eine Kontodimension enthält mindestens zwei Attribute:  
  
-   Ein Attribut ein Schlüsselattribut, das individuelle Konten in der Dimensionstabelle für die Kontodimension identifiziert.  
  
-   Ein Konto-Attribut eine übergeordnete Attribut, das beschreibt, wie Konten in der Kontodimension hierarchisch angeordnet sind.  
  
     Um ein Attribut als Kontoattribut zu identifizieren, legen Sie die **Type** -Eigenschaft des Attributs auf **Account** und die **Usage** -Eigenschaft auf **Parent**fest.  
  
 Kontodimensionen können optional die folgenden Attribute enthalten:  
  
-   Geben Sie ein Konto-Attribut ein Attribut, das den Kontotyp für jedes Konto in der Dimension definiert. Die Elementnamen des Kontotypattributs sind in den Kontotypen zugeordnet, die für die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank oder das Projekt definiert sind, und geben die Aggregatfunktion an, die von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] für diese Konten verwendet wird. Sie können auch unäre Operatoren oder benutzerdefinierte Rollupformeln verwenden, um das Aggregationsverhalten für Kontoattribute zu bestimmen, aber mit Kontotypen können Sie problemlos ein einheitliches Verhalten für ein Kontodiagramm durchsetzen, ohne dass dazu Änderungen an der zugrunde liegenden relationalen Datenbank erforderlich sind.  
  
     Um ein Kontotypattribut zu identifizieren, legen Sie die **Type** -Eigenschaft des Attributs auf **AccountType**fest.  
  
-   Ein Attribut ein Kontonamenattribut, die für die berichterstellung verwendet wird. Um ein Kontonamenattribut zu identifizieren, legen Sie die **Type** -Eigenschaft des Attributs auf **AccountName**fest.  
  
-   Ein Konto number-Attribut ein Attribut, das für die berichterstellung verwendet wird. Um ein Kontonummernattribut zu identifizieren, legen Sie die **Type** -Eigenschaft des Attributs auf **AccountNumber**fest.  
  
 Weitere Informationen zu Attributtypen finden Sie unter [Konfigurieren von Attributtypen](../../analysis-services/multidimensional-models/attribute-properties-configure-attribute-types.md).  
  
## <a name="adding-account-intelligence-with-the-business-intelligence-wizard"></a>Hinzufügen von Kontointelligenz mit dem Business Intelligence-Assistenten  
 Nachdem Sie eine Kontodimension definiert und diese Dimension zu einem Cube hinzugefügt haben, können Sie den Business Intelligence-Assistenten verwenden, um der Dimension Kontointelligenzfunktionalität hinzuzufügen, z. B. zum Identifizieren und Zuordnen von Kontotypen. Weitere Informationen finden Sie unter [Hinzufügen von Kontointelligenz zu einer Dimension](../../analysis-services/multidimensional-models/bi-wizard-add-account-intelligence-to-a-dimension.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Attribute und Attributhierarchien](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Business Intelligence-Assistent (F1-Hilfe)](http://msdn.microsoft.com/library/155ac80c-63ae-47aa-9e86-9396e3d920eb)   
 [Dimensionstypen](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md)  
  
  
