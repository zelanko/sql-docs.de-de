---
title: Dimension Attribute Properties Reference | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- properties [Analysis Services], attributes
- attributes [Analysis Services], properties
ms.assetid: 7f83d1cb-4732-424f-adc5-2449c1dd1008
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: cc66df28276802d7d397e498ceb1a22abdedb80e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046993"
---
# <a name="dimension-attribute-properties-reference"></a>Dimensionsattributeigenschaftenverweis
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]wird anhand von zahlreichen Eigenschaften die Funktionsweise von Dimensionen und Dimensionsattributen festgelegt. In der folgenden Tabelle werden die einzelnen Attributeigenschaften aufgelistet und beschrieben.  
  
|Eigenschaft|Description|  
|--------------|-----------------|  
|`AttributeHierarchyDisplayFolder`|Gibt den Ordner an, in dem Endbenutzern die verknüpfte Attributhierarchie angezeigt wird.|  
|`AttributeHierarchyEnabled`|Bestimmt, ob [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] eine Attributhierarchie für das Attribut generiert. Wird die Attributhierarchie nicht aktiviert, kann weder das Attribut in einer benutzerdefinierten Hierarchie verwendet werden, noch kann in MDX (Multidimensional Expressions)-Anweisungen auf die Attributhierarchie verwiesen werden.|  
|`AttributeHierarchyOptimizedState`|Bestimmt die Optimierungsebene, die auf die Attributhierarchie angewendet wird. Standardmäßig ist eine Attributhierarchie `FullyOptimized`, d. h. durch [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] werden Indizes zum Verbessern der Abfrageleistung für die Attributhierarchie erstellt. Die andere Option, `NotOptimized`, bedeutet, dass keine Indizes für die Attributhierarchie erstellt werden. Die Verwendung von `NotOptimized` ist dann hilfreich, wenn die Attributhierarchie für andere Zwecke als Abfragen verwendet wird, da keine zusätzlichen Indizes für das Attribut erstellt werden. Eine andere Verwendungen für eine Attributhierarchie könnte sein, ein anderes Attribut zu ordnen.|  
|`AttributeHierarchyOrdered`|Legt fest, ob die verknüpfte Attributhierarchie geordnet wird. Der Standardwert lautet `True`. Jedoch, wenn eine Attributhierarchie gilt nicht für Abfragen verwendet werden, können Sie einsparen Verarbeitungszeit durch Ändern des Werts dieser Eigenschaft auf `False`.|  
|`AttributeHierarchyVisible`|Bestimmt, ob die Attributhierarchie für Clientanwendungen sichtbar ist. Der Standardwert lautet `True`. Jedoch, wenn eine Attributhierarchie gilt nicht für Abfragen verwendet werden, können Sie einsparen Verarbeitungszeit durch Ändern des Werts dieser Eigenschaft auf `False`.|  
|`CustomRollupColumn`|Gibt die Spalte an, die eine benutzerdefinierte Rollupformel definiert.|  
|`CustomRollupPropertiesColumn`|Gibt die Spalte an, die die Eigenschaften einer benutzerdefinierten Rollupformel enthält.|  
|`DefaultMember`|Enthält einen mehrdimensionalen Ausdruck (Multidimensional Expression, MDX), der das Standardmeasure für das Attribut definiert.|  
|`Description`|Enthält die Beschreibung des Attributs.|  
|`DiscretizationBucketCount`|Enthält die Anzahl der Buckets, in denen diskretisiert werden soll.|  
|`DiscretizationMethod`|Definiert die zur Diskretisierung zu verwendende Methode.|  
|`EstimatedCount`|Gibt die Anzahl der geschätzten Elemente im Attribut an. Der Standardwert ist so lange Null, bis Sie den Aggregationsentwurfs-Assistenten ausführen. Sie können die Anzahl der Datensätze durch den Assistenten zählen lassen oder einen geschätzten Wert eingeben. Geben Sie den Wert manuell ein, wenn Sie die Anzahl der Elemente kennen und die Zeit sparen möchten, die das Abfragen der Datenbank erfordert. Wenn Sie mit einer Testteilmenge der Produktionsdaten arbeiten, können Sie die Anzahl der Produktionsdaten verwenden, damit der Aggregationsentwurf für die Produktionsdaten und nicht für die Testdaten optimiert wird.|  
|`GroupingBehavior`|Ein benutzerdefinierter Wert, der Clientanwendungen einen Hinweis darauf gibt, wie Attribute gruppiert werden.|  
|`ID`|Enthält den eindeutigen Bezeichner (ID) der Dimension.|  
|`InstanceSelection`|Stellt einen Hinweis für Clientanwendungen bezüglich der Anzeige einer Liste von Elementen bereit, die auf der erwarteten Anzahl von Elementen in der Liste basiert. Die folgenden Optionen sind verfügbar:<br /><br /> **None** Gibt keinen Hinweis an die Clientanwendung. Dies ist der Standardwert.<br /><br /> **DropDown** : Die Anzahl der Elemente ist klein genug für die Anzeige in einer Dropdownliste.<br /><br /> **List** : Die Anzahl der Elemente ist zu groß für eine **Dropdownliste**, erfordert aber keine Filter.<br /><br /> **FilteredList** Die Anzahl der Elemente ist groß genug, dass das Anwenden von Filtern für ihre Anzeige sinnvoll ist.<br /><br /> **MandatoryFilter** Die Anzahl der Elemente ist so groß, dass die Anzeige immer gefiltert werden muss.|  
|`IsAggregatable`|Legt fest, ob die Werte der Attributelemente aggregiert werden können. Der Standardwert ist `True`, was bedeutet, dass die Attributhierarchie eine (All)-Ebene enthält. Ist der Wert für diese Eigenschaft auf `False` festgelegt, enthält die Attributhierarchie keine (All)-Ebene.|  
|`KeyColumns`|Enthält die Spalte bzw. Spalten, die den Schlüssel für das Attribut darstellen, also die Spalte in der zugrunde liegenden relationalen Tabelle in der Datenquellensicht, an die das Attribut gebunden ist. Benutzern wird der Wert dieser Spalte für die einzelnen Elemente angezeigt, bis ein Wert für die `NameColumn`-Eigenschaft festgelegt wird.|  
|`MemberNamesUnique`|Bestimmt, ob Elementnamen in der Attributhierarchie eindeutig sein müssen.|  
|`MembersWithData`|Wird von übergeordneten Attributen verwendet, um zu bestimmen, ob Nichtblatt-Datenelemente im übergeordneten Attribut angezeigt werden. Dieser Eigenschaftswert wird nur verwendet, wenn der Wert der `Usage` -Eigenschaft auf Parent festgelegt ist. Dies bedeutet, dass eine Über-/Unterordnungshierarchie definiert wurde. Die folgenden Optionen sind verfügbar:<br /><br /> **NonLeafDataHidden** : Nichtblattdaten werden ausgeblendet.<br /><br /> **NonLeafDataVisible** : Nichtblattdaten sind sichtbar.|  
|`MembersWithDataCaption`|Stellt eine Vorlagenzeichenfolge bereit, die von übergeordneten Attributen zum Erstellen von Beschriftungen für die vom System generierten Datenelemente im übergeordneten Attribut verwendet wird. Dieser Eigenschaftswert wird nur verwendet, wenn der Wert der `Usage` -Eigenschaft auf Parent festgelegt ist. Dies bedeutet, dass eine Über-/Unterordnungshierarchie definiert wurde.|  
|`Name`|Enthält den benutzerfreundlichen Namen des Attributs.|  
|`NameColumn`|Identifiziert die Spalte, die den Namen des Attributs bereitstellt, das Benutzern angezeigt wird, und nicht den Wert in der Schlüsselspalte für das Attribut. Diese Spalte wird verwendet, wenn der Schlüsselspaltenwert für ein Attributelement kryptisch ist bzw. dem Benutzer nicht weiterhilft oder wenn die Schlüsselspalte auf einem zusammengesetzten Schlüssel basiert. Die `NameColumn`-Eigenschaft wird in Über-/Unterordnungshierarchien nicht verwendet. Die `NameColumn`-Eigenschaft für untergeordnete Elemente wird hingegen für Elementnamen in einer Über-/Unterordnungshierarchie verwendet.|  
|`NamingTemplate`|Definiert, wie Ebenen in einer Über-/Unterordnungshierarchie, die vom übergeordneten Attribut erstellt wurde, benannt werden. Dieser Eigenschaftswert wird nur verwendet, wenn der Wert der `Usage` -Eigenschaft auf Parent festgelegt ist. Dies bedeutet, dass eine Über-/Unterordnungshierarchie definiert wurde.|  
|`OrderBy`|Beschreibt das Anordnen der in der Attributhierarchie enthaltenen Elemente. Der Standardwert ist Name, wodurch der gibt an, dass die Sortierung der Attributelemente basiert auf dem Wert der `NameColumn` Eigenschaft, falls vorhanden. Andernfalls werden Elemente nach dem Wert der Schlüsselspalte sortiert. Die folgenden Optionen sind verfügbar:<br /><br /> `NameColumn` Sortieren nach dem Wert, der die `NameColumn` Eigenschaft.<br /><br /> **Key** Anordnung nach dem Wert der Schlüsselspalte des Attributelements.<br /><br /> **AttributeKey** Anordnung nach dem Wert des Elementschlüssels eines festgelegten Attributs, der über eine Attributbeziehung mit dem Attribut verfügen muss.<br /><br /> **AttributeName** Anordnung nach dem Wert des Elementnamens eines festgelegten Attributs, der über eine Attributbeziehung mit dem Attribut verfügen muss.|  
|`OrderByAttribute`|Identifiziert das Attribut, nach dem die in der Attributhierarchie enthaltenen Elemente angeordnet werden sollen.|  
|`RootMemberIf`|Bestimmt, wie der Stamm oder die obersten Elemente einer Über-/Unterordnungshierarchie identifiziert werden. Dieser Eigenschaftswert wird nur verwendet, wenn der Wert der `Usage` -Eigenschaft auf Parent festgelegt ist. Dies bedeutet, dass eine Über-/Unterordnungshierarchie definiert wurde. Der Standardwert ist auf `ParentIsBlankSelfOrMissing` festgelegt, das heißt, nur Elemente, die mindestens eine der für `ParentIsBlank`, `ParentIsSelf` oder `ParentIsMissing` geltenden Bedingungen erfüllen, werden als Stammelemente behandelt. Die folgenden Werte sind ebenfalls verfügbar:<br /><br /> `ParentIsBlank` Nur Elemente mit einer Null, eine 0 (null) oder eine leere Zeichenfolge in die bzw. den Schlüsselspalten werden als Stammelemente behandelt.<br /><br /> `ParentIsSelf` Nur Elemente mit sich selbst als übergeordnetes Element festgelegt werden als Stammelemente behandelt.<br /><br /> `ParentIsMissing` Nur Elemente mit übergeordneten Elementen, die nicht gefunden werden können, werden als Stammelemente behandelt.|  
|`Type`|Enthält den Typ des Attributs. Weitere Informationen finden Sie unter [Konfigurieren von Attributtypen](attribute-properties-configure-attribute-types.md).|  
|`UnaryOperatorColumn`|Gibt die Spalte an, die unäre Operatoren bereitstellt. Es ist eine Bindung vom DataItem-Typ, die die Details einer Spalte, die einen unären Operator bereitstellt, definiert.|  
|`Usage`|Beschreibt die Verwendung eines Attributs.<br /><br /> Die folgenden Optionen sind verfügbar:<br /><br /> `Regular` Das Attribut ist ein reguläres Attribut. Dies ist der Standardwert.<br /><br /> **Schlüssel** Das Attribut ist ein Schlüsselattribut.<br /><br /> **Parent** Das Attribut ist ein übergeordnetes Attribut.|  
|`ValueColumn`|Identifiziert die Spalte, die den Wert des Attributs bereitstellt. Wenn die `NameColumn` Element des Attributs angegeben wird, die gleiche `DataItem` Werte dienen als Standardwerte für die `ValueColumn` Element. Ist das `NameColumn`-Attributelement nicht festgelegt und enthält die `KeyColumns`-Attributauflistung ein einzelnes `KeyColumn`-Element, das eine Schlüsselspalte mit einem Zeichenfolgen-Datentyp darstellt, werden die `DataItem`-Werte auch für das `ValueColumn`-Element als Standardwerte verwendet.|  
  
> [!NOTE]  
>  Weitere Informationen zum Festlegen von Werten für die `KeyColumn` Eigenschaft bei der Arbeit mit null-Werte und anderen Problemen mit der Datenintegrität finden Sie unter [Handling Data Integrity Issues in Analysis Services 2005](http://go.microsoft.com/fwlink/?LinkId=81891).  
  
> [!NOTE]  
>  Das Standardelement eines Attributs wird zum Auswerten von Ausdrücken verwendet, wenn ein Element der Hierarchie nicht explizit in einer Abfrage enthalten ist. Das Standardelement eines Attributs wird angegeben, indem die `DefaultMember` -Eigenschaft des Attributs. Wenn eine Hierarchie aus einer Dimension in einer Abfrage enthalten ist, werden alle Standardelemente von Attributen ignoriert, die Ebenen in der Hierarchie entsprechen. Ist keine Hierarchie aus einer Dimension in einer Abfrage enthalten, werden für alle Attribute in der Dimension Standardelemente verwendet. Weitere Informationen zu Standardelementen finden Sie unter [Definieren eines Standardelements](attribute-properties-define-a-default-member.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Attribute und Attributhierarchien](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)  
  
  