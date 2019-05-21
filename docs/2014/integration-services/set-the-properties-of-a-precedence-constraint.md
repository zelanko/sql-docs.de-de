---
title: Legen Sie die Eigenschaften von Rangfolgeneinschränkungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- Precedence Constraint Editor dialog box
- precedence constraints [Integration Services], properties
ms.assetid: d990f600-5c09-4cd5-8528-0a58d79dc9f2
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8b0c8d2eec40078e58b80170b37c4885b72ad2b8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62888873"
---
# <a name="set-the-properties-of-a-precedence-constraint"></a>Festlegen der Eigenschaften von Rangfolgeneinschränkungen
  Um Eigenschaften für Rangfolgeneinschränkungen festzulegen, verwenden Sie eines der folgenden Tools:  
  
-   Sie können das Dialogfeld **Rangfolgeneinschränkungs-Editor** verwenden.  
  
-   Sie können das Eigenschaftenfenster verwenden. Im Eigenschaftenfenster werden Eigenschaften zum Konfigurieren von Rangfolgeneinschränkungen aufgelistet, die nicht im Dialogfeld **Rangfolgeneinschränkungs-Editor** verfügbar sind. Im Eigenschaftenfenster können Sie eine Beschreibung und einen Namen der Rangfolgeneinschränkung bereitstellen und die Anmerkung konfigurieren, um die Rangfolgeneinschränkung auf der Entwurfsoberfläche anzuzeigen.  
  
 Im folgenden Verfahren wird das Festlegen der Eigenschaften von Rangfolgeneinschränkungen mithilfe der einzelnen Tools beschrieben.  
  
### <a name="to-set-the-properties-of-a-precedence-constraint-by-using-the-precedence-constraint-editor"></a>So legen Sie die Eigenschaften von Rangfolgeneinschränkungen mithilfe des Rangfolgeneinschränkungs-Editors fest  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Ablaufsteuerung** .  
  
4.  Doppelklicken Sie auf die Rangfolgeneinschränkung.  
  
     Das Dialogfeld **Rangfolgeneinschränkungs-Editor** wird geöffnet.  
  
5.  Wählen Sie in der Dropdownliste **Auswertungsvorgang** einen Auswertungsvorgang aus.  
  
6.  In der `Value` Dropdown-Liste, wählen Sie das Ausführungsergebnis der ausführbaren Datei der Rangfolge.  
  
7.  Wenn der Auswertungsvorgang einen Ausdruck verwendet die `Expression` Feld Geben Sie einen Ausdruck, und klicken Sie auf **Test** zum Auswerten des Ausdrucks.  
  
    > [!NOTE]  
    >  Bei Variablennamen wird nach Groß-/Kleinschreibung unterschieden.  
  
8.  Wenn mehrere Tasks oder Container mit der eingeschränkten ausführbaren Datei verbunden sind, wählen Sie **logische und** um anzugeben, dass die Ausführungsergebnisse aller vorherigen ausführbaren Dateien ergeben müssen `true`. Wählen Sie **logisches oder** um anzugeben, dass nur ein Ausführungsergebnis ergeben muss `true`.  
  
9. Klicken Sie auf **OK** , um das Dialogfeld **Rangfolgeneinschränkungs-Editor**zu schließen.  
  
10. Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
### <a name="to-set-the-properties-of-a-precedence-constraint-by-using-the-properties-window"></a>So legen Sie die Eigenschaften von Rangfolgeneinschränkungen mithilfe des Eigenschaftenfensters fest  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt mit dem Paket, das Sie ändern möchten.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Ablaufsteuerung** . Klicken Sie in der Entwurfsoberfläche der Registerkarte **Ablaufsteuerung** mit der rechten Maustaste auf Rangfolgeneinschränkung, und klicken Sie auf **Eigenschaften**. Ändern Sie im Fenster Eigenschaften die Eigenschaftswerte.  
  
4.  Legen Sie im Fenster **Eigenschaften** die folgenden Lese-/Schreibeigenschaften der Rangfolgeneinschränkung fest:  
  
    |Lese/Schreibeigenschaft|Konfigurationsaktion|  
    |--------------------------|--------------------------|  
    |Description|Bereitstellen einer Beschreibung.|  
    |EvalOp|Auswählen eines Auswertungsvorgangs. Wenn die `Expression`, **ExpressionAndConstant**, oder **ExpressionOrConstant** ausgewählt sind, können Sie einen Ausdruck angeben.|  
    |expression|Wenn der Auswertungsvorgang einen Ausdruck einschließt, wird ein Ausdruck bereitgestellt. Der Ausdruck muss zu einem booleschen Wert ausgewertet werden. Weitere Informationen zur Ausdruckssprache finden Sie unter [Integration Services-Ausdrücke &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md).|  
    |LogicalAnd|Legen Sie `LogicalAnd` angeben, ob die rangfolgeneinschränkung zusammen mit anderen rangfolgeneinschränkungen ausgewertet wird, wenn mehrere ausführbare Dateien vorausgehen und mit der eingeschränkten ausführbaren Datei verknüpft sind|  
    |Name|Aktualisieren des Namens der Rangfolgeneinschränkung.|  
    |ShowAnnotation|Geben Sie den Typ der zu verwendenden Anmerkung ein. Wählen Sie **Never** aus, um Anmerkungen zu deaktivieren, **AsNeeded** , um Anmerkungen bei Bedarf zu aktivieren, **ConstraintName** , um automatisch den Wert mithilfe der Name-Eigenschaft anzumerken, **ConstraintDescription** , um automatisch den Wert mithilfe der Description-Eigenschaft anzumerken, und **ConstraintOptions** , um automatisch den Wert mithilfe der Eigenschaften Value und Expression anzumerken.|  
    |Wert|Wenn der Auswertungsvorgang in der EvalOP-Eigenschaft eine Einschränkung enthält, wählen Sie das Ausführungsergebnis der eingeschränkten ausführbaren Datei aus.|  
  
5.  Schließen Sie das Fenster Eigenschaften.  
  
6.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Siehe auch  
 [Rangfolgeneinschränkungen](control-flow/precedence-constraints.md)   
 [Verbinden von Tasks und Containern mithilfe einer Standardrangfolgen-Einschränkung](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)   
 [Legen Sie den Wert einer rangfolgeneinschränkung mithilfe der Kontextmenüs](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md)   
 [Verwenden eines Ausdrucks in einer Rangfolgeneinschränkung](../../2014/integration-services/use-an-expression-in-a-precedence-constraint.md)  
  
  
