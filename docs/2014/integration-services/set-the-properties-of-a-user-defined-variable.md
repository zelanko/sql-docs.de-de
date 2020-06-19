---
title: Festlegen der Eigenschaften einer benutzerdefinierten Variablen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- modifying variables
- variables [Integration Services], properties
ms.assetid: f98ddbec-f668-4dba-a768-44ac3ae0536f
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 53eeb46b5ce23a8976c9de1aaace7959bc708a84
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84963080"
---
# <a name="set-the-properties-of-a-user-defined-variable"></a>Festlegen der Eigenschaften von benutzerdefinierten Variablen
  Sie können eine der folgenden Funktionen verwenden, um die Eigenschaften einer benutzerdefinierten Variable in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]festzulegen:  
  
-   Fenster "Variablen".  
  
-   Eigenschaftenfenster. Im Fenster **Eigenschaften** werden die Eigenschaften zum Konfigurieren von Variablen aufgelistet, die im Fenster **Variablen** nicht zur Verfügung stehen: Description, EvaluateAsExpression, Expression, ReadOnly, ValueType und IncludeInDebugDump.  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] stellt außerdem eine Gruppe von Systemvariablen bereit, deren Eigenschaften, mit Ausnahme der RaiseChangedEvent-Eigenschaft, nicht aktualisiert werden können.  
  
 **Festlegen von Ausdrücken für Variablen**  
  
 Wenn Sie das Fenster **Eigenschaften** verwenden, um Ausdrücke für eine benutzerdefinierte Variable festzulegen:  
  
-   Der Wert dieser Variablen kann durch die Value-Eigenschaft oder die Expression-Eigenschaft festgelegt werden. Standardmäßig ist die EvaluateAsExpression-Eigenschaft auf festgelegt, `False` und der Wert der Variablen wird durch die Value-Eigenschaft festgelegt. Wenn Sie einen Ausdruck verwenden möchten, um den Wert festzulegen, müssen Sie zuerst EvaluateAsExpression auf festlegen `True` und dann einen Ausdruck in der Expression-Eigenschaft angeben. Die Value-Eigenschaft wird automatisch auf das Auswertungsergebnis des Ausdrucks festgelegt.  
  
-   Die ValueType-Eigenschaft enthält den Datentyp des Werts in der Value-Eigenschaft. Wenn Value durch einen Ausdruck festgelegt wird, dann wird ValueType automatisch auf einen Datentyp aktualisiert, der mit dem Auswertungsergebnis des Ausdrucks kompatibel ist. Wenn der Wert z. b. 0 und die ValueType-Eigenschaft **Int32** enthält und Sie dann Expression auf GETDATE () festlegen, enthält Value das aktuelle Datum und die aktuelle Uhrzeit, und ValueType ist auf festgelegt `DateTime` .  
  
-   Das ** Eigenschaftenfenster** für die Variable stellt den Zugriff auf das Dialogfeld **Ausdrucks-Generator** bereit. Sie können dieses Tool zum Erstellen, Überprüfen und Auswerten von Ausdrücken verwenden. Weitere Informationen finden Sie unter [Ausdrucks-Generator](expressions/expression-builder.md) und [Integration Services-Ausdrücke &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md).  
  
 Wenn Sie das Fenster **Variablen** verwenden, um Ausdrücke für eine benutzerdefinierte Variable festzulegen:  
  
-   Um einen Ausdruck zum Festlegen des Variablen Werts zu verwenden, vergewissern Sie sich zunächst, dass der Datentyp der Variablen mit dem Auswertungs Ergebnis des Ausdrucks kompatibel ist, und stellen Sie dann einen Ausdruck in der- `Expression` Spalte des **Variablen** Fensters bereit. Die EvaluateAsExpression-Eigenschaft im **Eigenschaften** Fenster wird automatisch auf festgelegt `True` .  
  
-   Wenn Sie einer Variablen einen Ausdruck zuweisen, wird ein spezieller Symbolmarker neben der Variablen angezeigt. Dieser spezielle Symbolmarker wird auch neben Verbindungs-Managern und Tasks angezeigt, für die Ausdrücke festgelegt wurden.  
  
-   Das Fenster **Variablen** für die Variable stellt den Zugriff auf das Dialogfeld **Ausdrucks-Generator** bereit. Sie können dieses Tool zum Erstellen, Überprüfen und Auswerten von Ausdrücken verwenden. Weitere Informationen finden Sie unter [Ausdrucks-Generator](expressions/expression-builder.md) und [Integration Services-Ausdrücke &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md).  
  
 Wenn Sie der Variablen im Fenster **Variablen** und **Eigenschaften** einen Ausdruck zuweisen und `EvaluateAsExpression` auf festgelegt ist `True` , können Sie den Datentyp der Variablen nicht ändern.  
  
 **Festlegen des Namespaces und der Namenseigenschaften**  
  
 Die Werte der Eigenschaften `Name` und `Namespace` müssen mit einem Buchstaben beginnen, wie in Unicode-Standard 2.0 definiert ist, oder mit einem Unterstrich (_). Bei den nachfolgenden Zeichen kann es sich um Buchstaben oder Zahlen gemäß Unicode-Standard 2.0 oder um einem Unterstrich (\_) handeln.  
  
## <a name="using-the-variables-window-to-set-properties"></a>Verwenden des Variablenfensters zum Festlegen von Eigenschaften  
  
#### <a name="to-set-the-properties-of-a-variable-by-using-the-variables-window"></a>So legen Sie die Eigenschaften einer Variablen mithilfe des Variablenfensters fest  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Projekt mit dem gewünschten Paket.  
  
2.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie im Menü **SSIS** auf **Variablen**.  
  
     Sie können das Fenster **Variablen** auch anzeigen, indem Sie im Dialogfeld **Optionen** auf der Seite **Tastatur** den Befehl View.Variables einer beliebigen Tastenkombination zuordnen.  
  
4.  Klicken Sie optional im Fenster **Variablen** auf **Rasteroptionen**, und wählen Sie die Spalten aus, die im Fenster **Variablen** angezeigt werden sollen. Wählen Sie dann die Filter aus, die auf die Liste der Variablen angewendet werden sollen.  
  
5.  Wählen Sie die Variable in der Liste aus, und aktualisieren Sie dann die Werte in den `Name` **Datentypen**,,, und ändern Sie das `Value` `Namespace` **Änderungs Ereignis**, die **Beschreibung** und die `Expression` Spalten.  
  
6.  Wählen Sie die Variable in der Liste aus, und klicken Sie dann auf **Variable verschieben** , um den Bereich zu ändern.  
  
7.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern**, um das aktualisierte Paket zu speichern.  
  
## <a name="using-the-properties-window-to-set-properties"></a>Verwenden des Eigenschaftenfensters zum Festlegen von Eigenschaften  
  
#### <a name="to-set-the-properties-of-a-variable-by-using-the-properties-window"></a>So legen Sie die Eigenschaften einer Variablen mithilfe des Eigenschaftenfensters fest  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Projekt mit dem gewünschten Paket.  
  
2.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**.  
  
4.  Klicken Sie in [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer auf die Registerkarte **Paket-Explorer** , und erweitern Sie den Paketknoten.  
  
5.  Um Variablen mit Paketbereich zu ändern, erweitern Sie den Variablenknoten. Erweitern Sie anderenfalls den Ereignishandlerknoten oder den Knoten für Ausführbare Dateien, bis Sie den Variablenknoten finden, der die zu ändernde Variable enthält.  
  
6.  Klicken Sie auf die Variable, deren Eigenschaften Sie ändern möchten.  
  
7.  Aktualisieren Sie im Fenster **Eigenschaften** die Variableneigenschaften für den Lese-/Schreibzugriff. Einige Eigenschaften sind für benutzerdefinierte Variablen auf Nur Lesen festgelegt.  
  
     Weitere Informationen zu den Eigenschaften finden Sie unter [Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md).  
  
8.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern**, um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services &#40;SSIS-&#41; Variablen](integration-services-ssis-variables.md)   
 [Verwenden von Variablen in Paketen](../../2014/integration-services/use-variables-in-packages.md)   
 [Hinzufügen, Löschen, Ändern des Bereichs von benutzerdefinierten Variablen in einem Paket](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)  
  
  
