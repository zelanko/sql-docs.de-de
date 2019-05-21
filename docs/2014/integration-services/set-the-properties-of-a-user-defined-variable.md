---
title: Legen Sie die Eigenschaften einer benutzerdefinierten Variablen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- modifying variables
- variables [Integration Services], properties
ms.assetid: f98ddbec-f668-4dba-a768-44ac3ae0536f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 4aaac5f66e8c01364419d8d2d9d5e853bf929ef7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62878203"
---
# <a name="set-the-properties-of-a-user-defined-variable"></a>Festlegen der Eigenschaften von benutzerdefinierten Variablen
  Sie können eine der folgenden Funktionen verwenden, um die Eigenschaften einer benutzerdefinierten Variable in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] festzulegen:  
  
-   Fenster "Variablen".  
  
-   Eigenschaftenfenster. Im Fenster **Eigenschaften** werden Eigenschaften zum Konfigurieren von Variablen aufgelistet, die im Fenster **Variablen** nicht verfügbar sind: Description, EvaluateAsExpression, Expression, ReadOnly, ValueType und IncludeInDebugDump.  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] stellt außerdem eine Gruppe von Systemvariablen bereit, deren Eigenschaften, mit Ausnahme der RaiseChangedEvent-Eigenschaft, nicht aktualisiert werden können.  
  
 **Festlegen von Ausdrücken für Variablen**  
  
 Wenn Sie das Fenster **Eigenschaften** verwenden, um Ausdrücke für eine benutzerdefinierte Variable festzulegen:  
  
-   Der Wert dieser Variablen kann durch die Value-Eigenschaft oder die Expression-Eigenschaft festgelegt werden. Standardmäßig ist die EvaluateAsExpression-Eigenschaft auf festgelegt `False` und der Wert der Variablen wird durch die Value-Eigenschaft festgelegt. Um einen Ausdruck verwenden, um den Wert festzulegen, müssen Sie zuerst EvaluateAsExpression auf festlegen `True`, und geben Sie einen Ausdruck in der Expression-Eigenschaft. Die Value-Eigenschaft wird automatisch auf das Auswertungsergebnis des Ausdrucks festgelegt.  
  
-   Die ValueType-Eigenschaft enthält den Datentyp des Werts in der Value-Eigenschaft. Wenn Value durch einen Ausdruck festgelegt wird, dann wird ValueType automatisch auf einen Datentyp aktualisiert, der mit dem Auswertungsergebnis des Ausdrucks kompatibel ist. Wenn der Wert 0 und ValueType-Eigenschaft enthält z. B. enthält **Int32** und Sie legen Sie Expression auf GETDATE() Wert enthält, das aktuelle Datum und die Uhrzeit und ValueType nastaven NA hodnotu `DateTime`.  
  
-   Das  **Eigenschaftenfenster** für die Variable stellt den Zugriff auf das Dialogfeld **Ausdrucks-Generator** bereit. Sie können dieses Tool zum Erstellen, Überprüfen und Auswerten von Ausdrücken verwenden. Weitere Informationen finden Sie unter [Ausdrucks-Generator](expressions/expression-builder.md) und [Integration Services-Ausdrücke &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md).  
  
 Wenn Sie das Fenster **Variablen** verwenden, um Ausdrücke für eine benutzerdefinierte Variable festzulegen:  
  
-   Um einen Ausdruck zum Festlegen des Variablenwerts verwenden, bestätigen, dass der Datentyp der Variablen mit dem Auswertungsergebnis des Ausdrucks kompatibel ist, und geben Sie einen Ausdruck in der `Expression` Spalte die **Variablen** Fenster. Die EvaluateAsExpression-Eigenschaft in der **Eigenschaften** Fenster wird automatisch festgelegt, um `True`.  
  
-   Wenn Sie einer Variablen einen Ausdruck zuweisen, wird ein spezieller Symbolmarker neben der Variablen angezeigt. Dieser spezielle Symbolmarker wird auch neben Verbindungs-Managern und Tasks angezeigt, für die Ausdrücke festgelegt wurden.  
  
-   Das Fenster **Variablen** für die Variable stellt den Zugriff auf das Dialogfeld **Ausdrucks-Generator** bereit. Sie können dieses Tool zum Erstellen, Überprüfen und Auswerten von Ausdrücken verwenden. Weitere Informationen finden Sie unter [Ausdrucks-Generator](expressions/expression-builder.md) und [Integration Services-Ausdrücke &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md).  
  
 Sowohl die **Variablen** und **Eigenschaften** -Fenster, wenn Sie die Variable einen Ausdruck zuweisen und `EvaluateAsExpression` nastaven NA hodnotu `True`, Sie können den Datentyp der Variablen nicht ändern.  
  
 **Festlegen des Namespace und der Namenseigenschaften**  
  
 Die Werte der Eigenschaften `Name` und `Namespace` müssen mit einem Buchstaben beginnen, wie in Unicode-Standard 2.0 definiert ist, oder mit einem Unterstrich (_). Bei den nachfolgenden Zeichen kann es sich um Buchstaben oder Zahlen gemäß Unicode-Standard 2.0 oder um einem Unterstrich (\_) handeln.  
  
## <a name="using-the-variables-window-to-set-properties"></a>Verwenden des Variablenfensters zum Festlegen von Eigenschaften  
  
#### <a name="to-set-the-properties-of-a-variable-by-using-the-variables-window"></a>So legen Sie die Eigenschaften einer Variablen mithilfe des Variablenfensters fest  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Projekt mit dem gewünschten Paket.  
  
2.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie im Menü **SSIS** auf **Variablen**.  
  
     Sie können das Fenster **Variablen** auch anzeigen, indem Sie im Dialogfeld **Optionen** auf der Seite **Tastatur** den Befehl View.Variables einer beliebigen Tastenkombination zuordnen.  
  
4.  Klicken Sie optional im Fenster **Variablen** auf **Rasteroptionen**, und wählen Sie die Spalten aus, die im Fenster **Variablen** angezeigt werden sollen. Wählen Sie dann die Filter aus, die auf die Liste der Variablen angewendet werden sollen.  
  
5.  Wählen Sie die Variable in der Liste aus, und aktualisieren Sie dann die Werte in der `Name`, **Datentyp**, `Value`, `Namespace`, **Änderungsereignis**, **Beschreibung,** und `Expression` Spalten.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md)   
 [Verwenden von Variablen in Paketen](../../2014/integration-services/use-variables-in-packages.md)   
 [Hinzufügen, Löschen, Ändern des Bereichs von benutzerdefinierten Variablen in einem Paket](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)  
  
  
