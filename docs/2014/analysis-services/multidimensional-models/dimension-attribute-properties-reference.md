---
title: Verweis auf Dimensions Attribut Eigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- properties [Analysis Services], attributes
- attributes [Analysis Services], properties
ms.assetid: 7f83d1cb-4732-424f-adc5-2449c1dd1008
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: db132a4a4cf6e8c2b73067220a5ed91a5316afef
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66075184"
---
# <a name="dimension-attribute-properties-reference"></a>Dimensionsattributeigenschaftenverweis
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]gibt es viele Eigenschaften, die bestimmen, wie Dimensionen und Dimensions Attribute funktionieren. In der folgenden Tabelle werden die einzelnen Attributeigenschaften aufgelistet und beschrieben.  
  
|Eigenschaft|BESCHREIBUNG|  
|--------------|-----------------|  
|`AttributeHierarchyDisplayFolder`|Gibt den Ordner an, in dem Endbenutzern die verknüpfte Attributhierarchie angezeigt wird.|  
|`AttributeHierarchyEnabled`|Bestimmt, ob [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] eine Attributhierarchie für das Attribut generiert. Wird die Attributhierarchie nicht aktiviert, kann weder das Attribut in einer benutzerdefinierten Hierarchie verwendet werden, noch kann in MDX (Multidimensional Expressions)-Anweisungen auf die Attributhierarchie verwiesen werden.|  
|`AttributeHierarchyOptimizedState`|Bestimmt die Optimierungsebene, die auf die Attributhierarchie angewendet wird. Standardmäßig ist eine Attributhierarchie `FullyOptimized`, d. h. durch [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] werden Indizes zum Verbessern der Abfrageleistung für die Attributhierarchie erstellt. Die andere Option, `NotOptimized`, bedeutet, dass keine Indizes für die Attributhierarchie erstellt werden. Die Verwendung von `NotOptimized` ist dann hilfreich, wenn die Attributhierarchie für andere Zwecke als Abfragen verwendet wird, da keine zusätzlichen Indizes für das Attribut erstellt werden. Eine andere Verwendungen für eine Attributhierarchie könnte sein, ein anderes Attribut zu ordnen.|  
|`AttributeHierarchyOrdered`|Legt fest, ob die verknüpfte Attributhierarchie geordnet wird. Standardwert: `True`. Wird die Attributhierarchie jedoch nicht für Abfragen verwendet, können Sie Verarbeitungszeit einsparen, indem Sie den Wert dieser Eigenschaft auf `False` festlegen.|  
|`AttributeHierarchyVisible`|Bestimmt, ob die Attributhierarchie für Clientanwendungen sichtbar ist. Standardwert: `True`. Wird die Attributhierarchie jedoch nicht für Abfragen verwendet, können Sie Verarbeitungszeit einsparen, indem Sie den Wert dieser Eigenschaft auf `False` festlegen.|  
|`CustomRollupColumn`|Gibt die Spalte an, die eine benutzerdefinierte Rollupformel definiert.|  
|`CustomRollupPropertiesColumn`|Gibt die Spalte an, die die Eigenschaften einer benutzerdefinierten Rollupformel enthält.|  
|`DefaultMember`|Enthält einen mehrdimensionalen Ausdruck (Multidimensional Expression, MDX), der das Standardmeasure für das Attribut definiert.|  
|`Description`|Enthält die Beschreibung des Attributs.|  
|`DiscretizationBucketCount`|Enthält die Anzahl der Buckets, in denen diskretisiert werden soll.|  
|`DiscretizationMethod`|Definiert die zur Diskretisierung zu verwendende Methode.|  
|`EstimatedCount`|Gibt die Anzahl der geschätzten Elemente im Attribut an. Der Standardwert ist so lange Null, bis Sie den Aggregationsentwurfs-Assistenten ausführen. Sie können die Anzahl der Datensätze durch den Assistenten zählen lassen oder einen geschätzten Wert eingeben. Geben Sie den Wert manuell ein, wenn Sie die Anzahl der Elemente kennen und die Zeit sparen möchten, die das Abfragen der Datenbank erfordert. Wenn Sie mit einer Testteilmenge der Produktionsdaten arbeiten, können Sie die Anzahl der Produktionsdaten verwenden, damit der Aggregationsentwurf für die Produktionsdaten und nicht für die Testdaten optimiert wird.|  
|`GroupingBehavior`|Ein benutzerdefinierter Wert, der Clientanwendungen einen Hinweis darauf gibt, wie Attribute gruppiert werden.|  
|`ID`|Enthält den eindeutigen Bezeichner (ID) der Dimension.|  
|`InstanceSelection`|Stellt einen Hinweis für Clientanwendungen bezüglich der Anzeige einer Liste von Elementen bereit, die auf der erwarteten Anzahl von Elementen in der Liste basiert. Die folgenden Optionen sind verfügbar:<br /><br /> **Keine** Für die Client Anwendung wird kein Hinweis bereitgestellt. Dies ist der Standardwert.<br /><br /> **Dropdown** Die Anzahl der Elemente ist klein genug, um in einer Dropdown Liste angezeigt zu werden.<br /><br /> **Liste** Die Anzahl der Elemente ist zu groß für eine Dropdown **Liste**, erfordert aber keine Filterung.<br /><br /> **FilteredList** Die Anzahl der Elemente ist groß genug, damit Benutzer die anzuzeigenden Elemente filtern müssen.<br /><br /> **MandatoryFilter** Die Anzahl der Elemente ist so groß, dass die Anzeige immer gefiltert werden muss.|  
|`IsAggregatable`|Legt fest, ob die Werte der Attributelemente aggregiert werden können. Der Standardwert ist auf `True` festgelegt, was bedeutet, dass die Attributhierarchie eine (All)-Ebene enthält. Ist der Wert für diese Eigenschaft auf `False` festgelegt, enthält die Attributhierarchie keine (All)-Ebene.|  
|`KeyColumns`|Enthält die Spalte bzw. Spalten, die den Schlüssel für das Attribut darstellen, also die Spalte in der zugrunde liegenden relationalen Tabelle in der Datenquellensicht, an die das Attribut gebunden ist. Der Wert dieser Spalte für jedes Element wird Benutzern angezeigt, es sei denn, für die `NameColumn` Eigenschaft wird ein Wert angegeben.|  
|`MemberNamesUnique`|Bestimmt, ob Elementnamen in der Attributhierarchie eindeutig sein müssen.|  
|`MembersWithData`|Wird von übergeordneten Attributen verwendet, um zu bestimmen, ob Nichtblatt-Datenelemente im übergeordneten Attribut angezeigt werden. Dieser Eigenschaftswert wird nur verwendet, wenn der Wert der `Usage`-Eigenschaft auf Parent festgelegt ist. Dies bedeutet, dass eine Über-/Unterordnungshierarchie definiert wurde. Die folgenden Optionen sind verfügbar:<br /><br /> **NonLeafDataHidden** Nicht Blatt Daten werden ausgeblendet.<br /><br /> **NonLeafDataVisible** Nicht Blatt Daten sind sichtbar.|  
|`MembersWithDataCaption`|Stellt eine Vorlagenzeichenfolge bereit, die von übergeordneten Attributen zum Erstellen von Beschriftungen für die vom System generierten Datenelemente im übergeordneten Attribut verwendet wird. Dieser Eigenschaftswert wird nur verwendet, wenn der Wert der `Usage`-Eigenschaft auf Parent festgelegt ist. Dies bedeutet, dass eine Über-/Unterordnungshierarchie definiert wurde.|  
|`Name`|Enthält den benutzerfreundlichen Namen des Attributs.|  
|`NameColumn`|Identifiziert die Spalte, die den Namen des Attributs bereitstellt, das Benutzern angezeigt wird, und nicht den Wert in der Schlüsselspalte für das Attribut. Diese Spalte wird verwendet, wenn der Schlüsselspaltenwert für ein Attributelement kryptisch ist bzw. dem Benutzer nicht weiterhilft oder wenn die Schlüsselspalte auf einem zusammengesetzten Schlüssel basiert. Die `NameColumn`-Eigenschaft wird in Über-/Unterordnungshierarchien nicht verwendet. Die `NameColumn`-Eigenschaft für untergeordnete Elemente wird hingegen für Elementnamen in einer Über-/Unterordnungshierarchie verwendet.|  
|`NamingTemplate`|Definiert, wie Ebenen in einer Über-/Unterordnungshierarchie, die vom übergeordneten Attribut erstellt wurde, benannt werden. Dieser Eigenschaftswert wird nur verwendet, wenn der Wert der `Usage`-Eigenschaft auf Parent festgelegt ist. Dies bedeutet, dass eine Über-/Unterordnungshierarchie definiert wurde.|  
|`OrderBy`|Beschreibt das Anordnen der in der Attributhierarchie enthaltenen Elemente. Der Standardwert ist Name, wodurch festgelegt wird, dass die Sortierung der Attributelemente auf dem Wert der `NameColumn`-Eigenschaft basiert, sofern ein solcher vorhanden ist. Andernfalls werden Elemente nach dem Wert der Schlüsselspalte sortiert. Die folgenden Optionen sind verfügbar:<br /><br /> `NameColumn`Sortieren Sie nach dem Wert der `NameColumn` -Eigenschaft.<br /><br /> **Schlüssel** Sortiert nach dem Wert der Schlüssel Spalte des Attribut Elements.<br /><br /> **AttributeKey** Sortiert nach dem Wert des Element Schlüssels eines angegebenen Attributs, das über eine Attribut Beziehung mit dem Attribut verfügen muss.<br /><br /> **AttributeName** Sortiert nach dem Wert des Element namens eines angegebenen Attributs, das über eine Attribut Beziehung mit dem Attribut verfügen muss.|  
|`OrderByAttribute`|Identifiziert das Attribut, nach dem die in der Attributhierarchie enthaltenen Elemente angeordnet werden sollen.|  
|`RootMemberIf`|Bestimmt, wie der Stamm oder die obersten Elemente einer Über-/Unterordnungshierarchie identifiziert werden. Dieser Eigenschaftswert wird nur verwendet, wenn der Wert der `Usage`-Eigenschaft auf Parent festgelegt ist. Dies bedeutet, dass eine Über-/Unterordnungshierarchie definiert wurde. Der Standardwert ist auf `ParentIsBlankSelfOrMissing` festgelegt, das heißt, nur Elemente, die mindestens eine der für `ParentIsBlank`, `ParentIsSelf` oder `ParentIsMissing` geltenden Bedingungen erfüllen, werden als Stammelemente behandelt. Die folgenden Werte sind ebenfalls verfügbar:<br /><br /> `ParentIsBlank`Nur Elemente mit einer NULL-, 0-oder leeren Zeichenfolge in der Schlüssel Spalte oder den Spalten werden als Stamm Elemente behandelt.<br /><br /> `ParentIsSelf`Nur Member mit sich selbst als übergeordnete Elemente werden als Stamm Elemente behandelt.<br /><br /> `ParentIsMissing`Nur Member mit übergeordneten Elementen, die nicht gefunden werden können, werden als Stamm Elemente behandelt.|  
|`Type`|Enthält den Typ des Attributs. Weitere Informationen finden Sie unter [Konfigurieren von Attributtypen](attribute-properties-configure-attribute-types.md).|  
|`UnaryOperatorColumn`|Gibt die Spalte an, die unäre Operatoren bereitstellt. Es ist eine Bindung vom DataItem-Typ, die die Details einer Spalte, die einen unären Operator bereitstellt, definiert.|  
|`Usage`|Beschreibt die Verwendung eines Attributs.<br /><br /> Die folgenden Optionen sind verfügbar:<br /><br /> `Regular`Das Attribut ist ein reguläres Attribut. Dies ist der Standardwert.<br /><br /> **Schlüssel** Das-Attribut ist ein Schlüssel Attribut.<br /><br /> Über **geordnetes** Element Das Attribut ist ein übergeordnetes Attribut.|  
|`ValueColumn`|Identifiziert die Spalte, die den Wert des Attributs bereitstellt. Ist das `NameColumn`-Element des Attributs festgelegt, werden die `DataItem`-Werte auch als Standardwerte für das `ValueColumn`-Element verwendet. Ist das `NameColumn`-Attributelement nicht festgelegt und enthält die `KeyColumns`-Attributauflistung ein einzelnes `KeyColumn`-Element, das eine Schlüsselspalte mit einem Zeichenfolgen-Datentyp darstellt, werden die `DataItem`-Werte auch für das `ValueColumn`-Element als Standardwerte verwendet.|  
  
> [!NOTE]  
>  Weitere Informationen zum Festlegen von Werten für die `KeyColumn` -Eigenschaft beim Arbeiten mit NULL-Werten und anderen Problemen mit der Datenintegrität finden Sie unter [Handling Data Integrity Issues in Analysis Services 2005](https://go.microsoft.com/fwlink/?LinkId=81891).  
  
> [!NOTE]  
>  Das Standardelement eines Attributs wird zum Auswerten von Ausdrücken verwendet, wenn ein Element der Hierarchie nicht explizit in einer Abfrage enthalten ist. Das Standardelement eines Attributs wird durch die `DefaultMember`-Eigenschaft des Attributs angegeben. Wenn eine Hierarchie aus einer Dimension in einer Abfrage enthalten ist, werden alle Standardelemente von Attributen ignoriert, die Ebenen in der Hierarchie entsprechen. Ist keine Hierarchie aus einer Dimension in einer Abfrage enthalten, werden für alle Attribute in der Dimension Standardelemente verwendet. Weitere Informationen zu Standardelementen finden Sie unter [Definieren eines Standardelements](attribute-properties-define-a-default-member.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Attribute und Attributhierarchien](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)  
  
  
