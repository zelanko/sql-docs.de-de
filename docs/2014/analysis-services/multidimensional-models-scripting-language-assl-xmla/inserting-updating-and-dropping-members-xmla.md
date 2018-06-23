---
title: Einfügen, aktualisieren und Löschen von Elementen (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- inserting dimension members
- XML for Analysis, members
- removing dimension members
- dropping dimension members
- write-enabled dimensions [Analysis Services]
- XMLA, members
- deleting dimension members
- dimensions [Analysis Services], XML for Analysis
ms.assetid: bba922b5-8b88-4051-9506-ff055248182a
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 4b283d0eec203422b97b9e7981783ac81999dc18
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060169"
---
# <a name="inserting-updating-and-dropping-members-xmla"></a>Einfügen, Aktualisieren und Löschen von Elementen (XMLA)
  Können Sie die [einfügen](../xmla/xml-elements-commands/insert-element-xmla.md), [aktualisieren](../xmla/xml-elements-commands/update-element-xmla.md), und [löschen](../xmla/xml-elements-commands/drop-element-xmla.md) -Befehle in XML for Analysis (XMLA) bzw. einfügen, aktualisieren oder Löschen von Elementen aus einer Dimension mit aktiviertem Schreibzugriff. Weitere Informationen zu Dimensionen mit aktiviertem Schreibzugriff finden Sie unter [Dimensionen mit aktiviertem Schreibzugriff](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md).  
  
## <a name="inserting-new-members"></a>Einfügen von neuen Elementen  
 Der `Insert`-Befehl fügt festgelegten Attributen in einer Dimension mit aktiviertem Schreibzugriff neue Elemente hinzu.  
  
 Vor der Erstellung des `Insert`-Befehls sollten Sie für die einzufügenden neuen Mitglieder über folgende Informationen verfügen:  
  
-   Die Dimension, in die die neuen Elemente eingefügt werden sollen.  
  
-   Das Dimensionsattribut, in die die neuen Elemente eingefügt werden sollen.  
  
-   Die Namen der neuen Elemente, einschließlich alle entsprechenden Übersetzungen für den Namen.  
  
-   Die Schlüssel der neuen Elemente. Wenn ein Attribut einen zusammengesetzten Schlüssel verwendet, erfordert der Schlüssel möglicherweise mehrere Werte.  
  
-   Werte für alle entsprechenden Attributeigenschaften, die nicht als andere Attribute innerhalb der Dimension implementiert wurden. Derartige Attributeigenschaften umfassen unäre Operationen, Übersetzungen, benutzerdefinierte Rollups, benutzerdefinierte Rollupeigenschaften und übersprungene Ebenen.  
  
 Der `Insert`-Befehl unterstützt nur zwei Eigenschaften:  
  
-   Die [Objekt](../xmla/xml-elements-properties/object-element-xmla.md) -Eigenschaft, die einen Objektverweis für die Dimension enthält, in dem die Elemente eingefügt werden. Der Objektverweis enthält den Datenbankbezeichner, den Cubebezeichner sowie den Dimensionsbezeichner für die Dimension.  
  
-   Die [Attribute](../xmla/xml-elements-properties/attributes-element-xmla.md) -Eigenschaft, die einer mehreren oder [Attribut](../xmla/xml-elements-properties/attribute-element-xmla.md) Elemente die Attribute zu identifizieren, in dem Elemente eingefügt werden. Jedes `Attribute`-Element identifiziert ein Attribut und stellt den Namen, den Wert, Übersetzungen, den unären Operator, benutzerdefinierte Rollups, benutzerdefinierte Rollupeigenschaften und übersprungene Ebenen für ein einzelnes Element bereit, das dem identifizierten Attribut hinzugefügt werden soll.  
  
    > [!NOTE]  
    >  Alle Eigenschaften für das `Attribute`-Element müssen eingefügt werden. Andernfalls tritt möglicherweise ein Fehler auf.  
  
## <a name="updating-existing-members"></a>Aktualisieren von vorhandenen Elementen  
 Der `Update`-Befehl aktualisiert auf der Grundlage der Beziehungen zu anderen Elementen in anderen Attributen in einer Dimension mit aktiviertem Schreibzugriff vorhandene Elemente in festgelegten Attributen. Der `Update`-Befehl kann Elemente auf andere Ebenen in Hierarchien innerhalb der Dimension verschieben. Zudem kann er verwendet werden, um von übergeordneten Attributen definierte Über-/Unterordnungshierarchien neu zu strukturieren.  
  
 Vor der Erstellung des `Update`-Befehls sollten Sie für die zu aktualisierenden Mitglieder über folgende Informationen verfügen:  
  
-   Die Dimension, in der die vorhandenen Elemente aktualisiert werden sollen.  
  
-   Die Dimensionsattribute, in denen die vorhandenen Elemente aktualisiert werden sollen.  
  
-   Die Schlüssel der vorhandenen Elemente. Wenn ein Attribut einen zusammengesetzten Schlüssel verwendet, erfordert der Schlüssel möglicherweise mehrere Werte.  
  
-   Werte für alle entsprechenden Attributeigenschaften, die nicht als andere Attribute innerhalb der Dimension implementiert wurden. Derartige Attributeigenschaften umfassen unäre Operationen, Übersetzungen, benutzerdefinierte Rollups, benutzerdefinierte Rollupeigenschaften und übersprungene Ebenen.  
  
 Der `Update`-Befehl unterstützt nur drei erforderliche Eigenschaften:  
  
-   Die `Object`-Eigenschaft, die einen Objektverweis für die Dimension enthält, in der die Elemente aktualisiert werden sollen. Der Objektverweis enthält den Datenbankbezeichner, den Cubebezeichner sowie den Dimensionsbezeichner für die Dimension.  
  
-   Die `Attributes`-Eigenschaft, die mindestens ein `Attribute`-Element enthält, um die Attribute zu identifizieren, in denen Elemente aktualisiert werden sollen. Das `Attribute`-Element identifiziert ein Attribut und stellt den Namen, den Wert, Übersetzungen, den unären Operator, benutzerdefinierte Rollups, benutzerdefinierte Rollupeigenschaften und übersprungene Ebenen für ein einzelnes Element bereit, das für das identifizierte Attribut aktualisiert werden soll.  
  
    > [!NOTE]  
    >  Alle Eigenschaften für das `Attribute`-Element müssen eingefügt werden. Andernfalls tritt möglicherweise ein Fehler auf.  
  
-   Die [, in denen](../xmla/xml-elements-properties/where-element-xmla.md) -Eigenschaft, die einer mehreren oder `Attribute` Elemente, die die Attribute zu beschränken, in denen Elemente aktualisiert werden. Die `Where` Eigenschaft ist wichtig für die Beschränkung ein `Update` -Befehls auf bestimmte Instanzen eines Elements. Wenn die `Where` Eigenschaft nicht angegeben ist, werden alle Instanzen eines bestimmten Elements aktualisiert. Angenommen, Sie möchten den Stadtnamen für drei Kunden von Redmond zu Bellevue ändern. Um den Stadtnamen zu ändern, müssen Sie eine `Where`-Eigenschaft bereitstellen, die die drei Elemente im Customer-Attribut identifiziert, für die die Elemente im City-Attribut geändert werden sollen. Wenn Sie diese `Where`-Eigenschaft nicht bereitstellen, würde für jeden Kunden, dessen Stadtname zurzeit Redmond lautet, der Stadtname nach der Ausführung des `Update`-Befehls Bellevue lauten.  
  
    > [!NOTE]  
    >  Mit der Ausnahme von neuen Elementen kann der `Update`-Befehl nur Attributschlüsselwerte für Attribute aktualisieren, die nicht in der `Where`-Klausel enthalten sind. Der Stadtname kann beispielsweise nicht aktualisiert werden, wenn ein Kunde aktualisiert wird, andernfalls wird der Stadtname für alle Kunden geändert.  
  
### <a name="updating-members-in-parent-attributes"></a>Aktualisieren von Elementen in übergeordneten Attributen  
 Zur Unterstützung von übergeordneten Attributen, die `Update` -Befehl die optionalen [MoveWithDescendants](../xmla/xml-elements-properties/movewithdescendants-element-xmla.md)sollte Eigenschaften. Wenn die `MoveWithDescendants`-Eigenschaft auf „True“ festgelegt wird, wird angegeben, dass die Nachfolger des übergeordneten Elements zusammen mit dem übergeordneten Element verschoben werden sollen, wenn sich der Bezeichner dieses übergeordneten Elements ändert. Wenn dieser Wert auf „False“ festgelegt wird, werden die unmittelbaren Nachfolger eines übergeordneten Elements zu der Ebene höhergestuft, auf der sich das übergeordnete Element zuvor befand, wenn dieses übergeordnete Element verschoben wird.  
  
 Wenn Elemente in einem übergeordneten Attribut aktualisiert werden, kann der `Update`-Befehl keine Elemente in anderen Attributen aktualisieren.  
  
## <a name="dropping-existing-members"></a>Löschen von vorhandenen Elementen  
 Vor der Erstellung des `Drop`-Befehls sollten Sie für die zu löschenden Mitglieder über folgende Informationen verfügen:  
  
-   Die Dimension, in der die vorhandenen Elemente gelöscht werden sollen.  
  
-   Die Dimensionsattribute, in denen die vorhandenen Elemente gelöscht werden sollen.  
  
-   Die Schlüssel der zu löschenden vorhandenen Elemente. Wenn ein Attribut einen zusammengesetzten Schlüssel verwendet, erfordert der Schlüssel möglicherweise mehrere Werte.  
  
 Der `Drop`-Befehl unterstützt nur zwei erforderliche Eigenschaften:  
  
-   Die `Object`-Eigenschaft, die einen Objektverweis für die Dimension enthält, in der die Elemente gelöscht werden sollen. Der Objektverweis enthält den Datenbankbezeichner, den Cubebezeichner sowie den Dimensionsbezeichner für die Dimension.  
  
-   Die `Where`-Eigenschaft,  die mindestens ein `Attribute`-Element enthält, um die Attribute zu beschränken, in denen Elemente gelöscht werden sollen. Die `Where`-Eigenschaft ist wichtig für die Beschränkung eines `Drop`-Befehls auf bestimmte Instanzen eines Elements. Wenn der `Where`-Befehl nicht festgelegt wird, werden alle Instanzen eines bestimmten Elements gelöscht. Angenommen, Sie möchten in Redmond drei Kunden löschen. Um diese Kunden zu löschen, müssen Sie eine `Where`-Eigenschaft angeben, die die drei zu entfernenden Elemente im Customer-Attribut identifiziert, sowie das Element „Redmond“ des City-Attributs, aus dem die drei Kunden entfernt werden sollen. Wenn die `Where`-Eigenschaft nur das Element „Redmond“ des City-Attributs angibt, wird jeder Kunde von dem `Drop`-Befehl gelöscht, der „Redmond“ zugeordnet ist. Wenn die `Where`-Eigenschaft nur die drei Elemente im Customer-Attribut festlegt, werden die drei Kunden von dem `Drop`-Befehl vollständig gelöscht.  
  
    > [!NOTE]  
    >  Die in einem `Attribute`-Befehl enthaltenen `Drop`-Elemente dürfen nur die `AttributeName`- und die `Keys`-Eigenschaft enthalten. Andernfalls tritt möglicherweise ein Fehler auf.  
  
### <a name="dropping-members-in-parent-attributes"></a>Löschen von Elementen in übergeordneten Attributen  
 Festlegen der [DeleteWithDescendants](../xmla/xml-elements-properties/deletewithdescendants-element-xmla.md) Eigenschaft gibt an, dass die Nachfolger eines übergeordneten Elements mit dem übergeordneten Element ebenfalls gelöscht werden soll. Wenn dieser Wert auf „False“ festgelegt wird, werden die unmittelbaren Nachfolger eines übergeordneten Elements zu der Ebene höhergestuft, auf der sich das übergeordnete Element zuvor befand.  
  
> [!IMPORTANT]  
>  Ein Benutzer muss lediglich über Löschberechtigungen für das übergeordnete Element verfügen, um sowohl das übergeordnete Element als auch die Nachfolger zu löschen. Ein Benutzer benötigt keine Löschberechtigungen für die Nachfolger.  
  
## <a name="see-also"></a>Siehe auch  
 [Drop-Element &#40;XMLA&#41;](../xmla/xml-elements-commands/drop-element-xmla.md)   
 [INSERT-Element &#40;XMLA&#41;](../xmla/xml-elements-commands/insert-element-xmla.md)   
 [Update-Element &#40;XMLA&#41;](../xmla/xml-elements-commands/update-element-xmla.md)   
 [Definieren und Identifizieren von Objekten &#40;XMLA&#41;](../xmla/xml-elements-objects.md)   
 [Entwickeln mit XMLA in Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  