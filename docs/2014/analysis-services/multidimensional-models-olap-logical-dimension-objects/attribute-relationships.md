---
title: Attribut Beziehungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- member properties [Analysis Services], attribute relationships
- security [Analysis Services], properties
- PROPERTIES keyword
- storage [Analysis Services], attribute relationships
- natural hierarchies [Analysis Services]
- dimensions [Analysis Services], member properties
- queries [MDX], attribute relationships
- user-defined hierarchies [Analysis Services]
- attributes [Analysis Services], relationships
- member properties [Analysis Services]
- members [Analysis Services], attribute relationships
- storing data [Analysis Services], attribute relationships
- relationships [Analysis Services], attributes
ms.assetid: 2491422a-4cf5-4b23-b6ab-289222b22ce8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 81d51c8778cfbc6e3891dfb3b6783db48f0c65a2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62728516"
---
# <a name="attribute-relationships"></a>Attributbeziehungen
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]sind Attribute innerhalb einer Dimension immer entweder direkt oder indirekt mit dem Schlüssel Attribut verknüpft. Wenn Sie eine Dimension auf Basis eines Sternschemas definieren, in dem sämtliche Dimensionsattribute aus derselben relationalen Tabelle abgeleitet werden, wird automatisch eine Attributbeziehung zwischen dem Schlüsselattribut und den einzelnen Nichtschlüsselattributen definiert. Wenn Sie eine Dimension auf Basis eines Schneeflockenschemas definieren, in dem Dimensionsattribute aus mehreren verknüpften Tabellen abgeleitet werden, wird eine Attributbeziehung automatisch wie folgt definiert:  
  
-   Zwischen dem Schlüsselattribut und den einzelnen Nichtschlüsselattributen, die an die Spalten in der Dimensionshaupttabelle gebunden sind  
  
-   Zwischen dem Schlüsselattribut und dem Attribut, das an den Fremdschlüssel in der sekundären Tabelle gebunden ist, die die zugrunde liegenden Dimensionstabellen verknüpft  
  
-   Zwischen dem Attribut, das an den Fremdschlüssel in der sekundären Tabelle gebunden ist, und den einzelnen Nichtschlüsselattributen, die an Spalten aus der sekundären Tabelle gebunden sind  
  
 Es kann jedoch Gründe dafür geben, die Standardattributbeziehungen zu ändern. Ein möglicher Grund wäre, dass Sie eine natürliche Hierarchie, eine benutzerdefinierte Sortierreihenfolge oder Dimensionsgranularität auf Basis eines Nichtschlüsselattributs definieren möchten. Weitere Informationen finden Sie unter [Dimensions Attribut Eigenschaften Reference](../multidimensional-models/dimension-attribute-properties-reference.md).  
  
> [!NOTE]  
>  Attributbeziehungen sind in MDX (Multidimensional Expressions) als Elementeigenschaften bekannt.  
  
## <a name="natural-hierarchy-relationships"></a>Beziehungen mit natürlicher Hierarchie  
 Eine Hierarchie wird als natürlich bezeichnet, wenn die in der benutzerdefinierten Hierarchie enthaltenen Attribute 1:n-Beziehungen mit dem jeweils direkt darunter liegenden Attribut haben. Ein Beispiel ist eine Customer-Dimension, die auf einer relationalen Quelltabelle mit acht Spalten basiert:  
  
-   CustomerKey  
  
-   CustomerName  
  
-   Age  
  
-   Geschlecht  
  
-   E-Mail  
  
-   City  
  
-   Country  
  
-   Region  
  
 Die entsprechende Analysis Services-Dimension verfügt über sieben Attribute:  
  
-   Customer (basierend auf CustomerKey, wobei CustomerName Elementnamen angibt)  
  
-   Age, Gender, Email, City, Region, Country  
  
 Beziehungen, die natürliche Hierarchien darstellen, werden dadurch erzwungen, dass eine Attributbeziehung zwischen dem Attribut einer Ebene und dem Attribut der darunter liegenden Ebene erstellt wird. Für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] gibt dies eine natürliche Beziehung und potenzielle Aggregation an. In der Customer-Dimension besteht für die Attribute Country, Region, City und Customer eine natürliche Hierarchie. Die natürliche Hierarchie für `{Country, Region, City, Customer}` wird durch Hinzufügen der folgenden Attributbeziehungen beschrieben:  
  
-   Das Country-Attribut als Attributbeziehung zum Region-Attribut.  
  
-   Das Region-Attribut als Attributbeziehung zum City-Attribut.  
  
-   Das City-Attribut als Attributbeziehung zum Customer-Attribut.  
  
 Zum Navigieren von Daten im Cube können Sie auch eine benutzerdefinierte Hierarchie erstellen, die keine natürliche Hierarchie in den Daten darstellt (Dies wird als *Ad-hoc-* oder *Berichterstattungs* Hierarchie bezeichnet). Sie könnten z. B. eine benutzerdefinierte Hierarchie auf der Basis von `{Age, Gender}` erstellen. Benutzer sehen keinen Unterschied in der Art und Weise, wie sich die beiden Hierarchien Verhalten. die natürliche Hierarchie profitiert von Aggregations-und Indizierungs Strukturen, die für die natürlichen Beziehungen in den Quelldaten ausgeblendet sind.  
  
 Durch die `SourceAttribute`-Eigenschaft einer Ebene ist festgelegt, mit welchem Attribut die Ebene beschrieben wird. Die `KeyColumns`-Eigenschaft des Attributs gibt an, welche Spalte in der Datenquellensicht die Elemente bereitstellt. Mit der `NameColumn`-Eigenschaft des Attributs kann eine andere Namensspalte für die Elemente festgelegt werden.  
  
 Zum Definieren einer Ebene in einer benutzerdefinierten Hierarchie mithilfe [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]von können Sie mit dem **Dimensions-Designer** ein Dimensions Attribut, eine Spalte in einer Dimensions Tabelle oder eine Spalte aus einer verknüpften Tabelle auswählen, die in der Datenquellen Sicht für den Cube enthalten ist. Weitere Informationen zum Erstellen von benutzerdefinierten Hierarchien finden Sie unter [Erstellen von benutzerdefinierten Hierarchien](../multidimensional-models/user-defined-hierarchies-create.md).  
  
 In Analysis Services erfolgt in der Regel eine Annahme zum Inhalt von Elementen. Blattelemente haben keine nachfolgenden Werte und enthalten von zugrunde liegenden Datenquellen abgeleitete Daten. Nicht-Blattelemente haben nachfolgende Werte und enthalten von Aggregationen abgeleitete Daten, die für untergeordnete Elemente ausgeführt wurden. Auf aggregierten Ebenen basieren Elemente auf Aggregationen der untergeordneten Ebenen. Wenn also die `IsAggregatable`-Eigenschaft für das Quellattribut einer Ebene auf `False` festgelegt ist, sollten keine aggregierbaren Attribute als nächst höhere Ebenen hinzugefügt werden.  
  
## <a name="defining-an-attribute-relationship"></a>Definieren einer Attributbeziehung  
 Die wesentliche Einschränkung beim Erstellen einer Attributbeziehung liegt darin, sicherzustellen, dass das Attribut, auf das durch die Attributbeziehung verwiesen wird, maximal einen Wert für jeweils ein Element in dem Attribut aufweist, zu dem die Attributbeziehung gehört. Wenn Sie beispielsweise eine Beziehung zwischen einem City-Attribut und einem State-Attribut definieren, kann sich jede Stadt nur auf ein Bundesland beziehen.  
  
## <a name="attribute-relationship-queries"></a>Abfragen von Attributbeziehungen  
 Sie können MDX-Abfragen verwenden, um Daten aus Attributbeziehungen abzurufen, und zwar in Form von Elementeigenschaften, mit dem `PROPERTIES`-Schlüsselwort der `SELECT`-MDX-Anweisung. Weitere Informationen zum Verwenden von MDX zum Abrufen von Element Eigenschaften finden Sie unter [using Member Properties &#40;MDX&#41;](../multidimensional-models/mdx/mdx-member-properties.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Attribute und Attribut Hierarchien](attributes-and-attribute-hierarchies.md)   
 [Dimensions Attribut-Eigenschaften Referenz](../multidimensional-models/dimension-attribute-properties-reference.md)   
 [Benutzer Hierarchien](user-hierarchies.md)   
 [Eigenschaften der Benutzerhierarchie](user-hierarchies-properties.md)  
  
  
