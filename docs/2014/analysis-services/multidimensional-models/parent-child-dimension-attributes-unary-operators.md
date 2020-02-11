---
title: Unäre Operatoren in über-und untergeordneten Dimensionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- UnaryOperatorColumn property
- attributes [Analysis Services], unary operators
- unary operators
ms.assetid: b8ef549c-5458-458a-bf1a-fd743a1417fd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 25c1acf7a1fadbc79b7781488143ce57881c81fc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66073444"
---
# <a name="unary-operators-in-parent-child-dimensions"></a>Unäre Operatoren in über- und untergeordneten Dimensionen
  In einer Dimension, die eine Beziehung zwischen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]über-und untergeordneten Elementen enthält, geben Sie eine unäre Operator Spalte (oder eine benutzerdefinierte Rollup-Operator Spalte) an, die den benutzerdefinierten Rollup für alle nicht berechneten Elemente des übergeordneten Attributs bestimmt. Der unäre Operator wird immer dann auf die Elemente angewendet, wenn die Werte des übergeordneten Elements ausgewertet werden. Die **UnaryOperatorColumn** -Eigenschaft für ein übergeordnetes Attribut (**Usage**=Parent) gibt die Spalte einer Tabelle in der Datenquellensicht an, die unäre Operatoren enthält. Werte für die benutzerdefinierten Rollup-Operatoren, die in dieser Spalte gespeichert sind, werden auf die einzelnen Elemente des Attributs angewendet.  
  
 Sie können eine benannte Berechnung für eine Dimensionstabelle in der Datenquellensicht als unäre Operatorspalte erstellen und angeben. Der einfachste Ausdruck, z. B. '+', gibt denselben Operator für alle Elemente zurück. Aber Sie können jeden beliebigen Ausdruck verwenden, solange er einen Operator für jedes Element zurückgibt.  
  
 Sie können die Einstellung der **UnaryOperatorColumn** -Eigenschaft für ein übergeordnetes Attribut manuell ändern oder die Erweiterung zum Definieren einer benutzerdefinierten Aggregation des Business Intelligence-Assistenten verwenden, um die Standardaggregation zu ersetzen, die mit Elementen einer Dimension verknüpft ist. Weitere Informationen zum Ausführen dieser Konfiguration mithilfe des Business Intelligence-Assistenten finden Sie unter [Hinzufügen einer benutzerdefinierten Aggregation zu einer Dimension](bi-wizard-add-a-custom-aggregation-to-a-dimension.md).  
  
 Die Standardeinstellung für die **UnaryOperatorColumn** -Eigenschaft für ein übergeordnetes Attribut ist (keine), wodurch die benutzerdefinierten Rollup-Operatoren deaktiviert werden. In der folgenden Tabelle werden die unären Operatoren aufgelistet. Außerdem wird das Verhalten dieser Operatoren beschrieben, wenn sie auf eine Ebene angewendet werden.  
  
|Unärer Operator|BESCHREIBUNG|  
|--------------------|-----------------|  
|+ (Pluszeichen)|Der Wert des Elements wird dem Aggregatwert der gleichgeordneten Elemente hinzugefügt, die vor dem Element auftreten. Bei diesem Operator handelt es sich um den Standardoperator, wenn für ein Attribut keine unäre Operatorspalte definiert ist.|  
|-(Minuszeichen)|Der Wert des Elements wird vom Aggregatwert der gleichgeordneten Elemente subtrahiert, die vor dem Element auftreten.|  
|* (Sternchen)|Der Wert des Elements wird mit dem Aggregatwert der gleichgeordneten Elemente multipliziert, die vor dem Element auftreten.|  
|/ (Schrägstrich)|Der Wert des Elements wird durch den Aggregatwert der gleichgeordneten Elemente dividiert, die vor dem Element auftreten.|  
|~ (Tilde)|Der Wert des Elements wird nicht berücksichtigt.|  
  
 Leere Werte und alle anderen Werte, die nicht in der Tabelle aufgeführt sind, werden wie der unäre Operator + (Pluszeichen) behandelt. Es ist keine Operatorrangfolge vorhanden. Die Reihenfolge der Auswertung wird somit durch die Reihenfolge bestimmt, mit der Elemente in der Spalte des unären Operators gespeichert sind. Sie müssen zum Ändern der Auswertungsreihenfolge ein neues Attribut erstellen, für die zugehörige **Typ** -Eigenschaft den Wert **Sequenz**festlegen und dann Sequenznummern in der zugehörigen **Quellspalte** -Eigenschaft zuweisen, die der Reihenfolge der Auswertung entsprechen. Sie müssen auch die Reihenfolge der Elemente des Attributs gemäß diesem Attribut festlegen. Weitere Informationen zum Festlegen der Reihenfolge von Elementen eines Attributs mithilfe des Business Intelligence-Assistenten finden Sie unter [Definieren der Reihenfolge für eine Dimension](bi-wizard-define-the-ordering-for-a-dimension.md).  
  
 Sie können mithilfe der **UnaryOperatorColumn** -Eigenschaft eine benannte Berechnung angeben, die für alle Elemente des Attributs einen unären Operator als Literalzeichen zurückgibt. Geben Sie dazu einfach ein Literalzeichen, z. B. `'*'` , in die benannte Berechnung ein. Dadurch wird der Standardoperator, das Pluszeichen (+), für alle Elemente des Attributs durch den Multiplikationsoperator, das Sternchen (*), ersetzt. Weitere Informationen finden Sie unter [Definieren von benannten Berechnungen in einer Datenquellen Sicht &#40;Analysis Services&#41;](define-named-calculations-in-a-data-source-view-analysis-services.md).  
  
 Auf der Registerkarte **Browser** des Dimensions-Designers können Sie die unären Operatoren neben den einzelnen Elementen in einer Hierarchie anzeigen. Außerdem können Sie die unären Operatoren ändern, wenn Sie mit einer Dimension mit aktiviertem Schreibzugriff arbeiten. Wenn der Schreibzugriff für die Dimension nicht aktiviert ist, müssen Sie die Datenquelle mithilfe eines Tools direkt ändern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dimensions Attribut-Eigenschaften Referenz](dimension-attribute-properties-reference.md)   
 [Benutzerdefinierte Rollup-Operatoren in über-und untergeordneten Dimensionen](parent-child-dimension-attributes-custom-rollup-operators.md)   
 [Starten des Business Intelligence-Assistenten im Dimensions-Designer](database-dimensions-bi-wizard-in-dimension-designer.md)  
  
  
