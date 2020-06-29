---
title: Festlegen der Eigenschaften einer Rang folgen Einschränkung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Precedence Constraint Editor dialog box
- precedence constraints [Integration Services], properties
ms.assetid: d990f600-5c09-4cd5-8528-0a58d79dc9f2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 55e71b6615afc15c2963b4dbb9bfbf2790e90b3b
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85421548"
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
  
6.  `Value`Wählen Sie in der Dropdown Liste das Ausführungs Ergebnis der ausführbaren Datei der Rangfolge aus.  
  
7.  Wenn der Auswertungs Vorgang einen Ausdruck verwendet, `Expression` Geben Sie im Feld einen Ausdruck ein, und klicken Sie auf **Testen** , um den Ausdruck auszuwerten.  
  
    > [!NOTE]  
    >  Bei Variablennamen wird nach Groß-/Kleinschreibung unterschieden.  
  
8.  Wenn mehrere Tasks oder Container mit der eingeschränkten ausführbaren Datei verbunden sind, wählen Sie **logisch und** aus, um anzugeben, dass die Ausführungs Ergebnisse aller vorherigen ausführbaren Dateien als ausgewertet werden müssen `true` . Wählen Sie **logisches OR** aus, um anzugeben, dass nur ein Ausführungs Ergebnis als ausgewertet werden muss `true` .  
  
9. Klicken Sie auf **OK** , um das Dialogfeld **Rangfolgeneinschränkungs-Editor**zu schließen.  
  
10. Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
### <a name="to-set-the-properties-of-a-precedence-constraint-by-using-the-properties-window"></a>So legen Sie die Eigenschaften von Rangfolgeneinschränkungen mithilfe des Eigenschaftenfensters fest  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt mit dem Paket, das Sie ändern möchten.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Ablauf Steuerung** . Klicken Sie in der Entwurfs Oberfläche der Registerkarte **Ablauf Steuerung** mit der rechten Maustaste auf die Rang folgen Einschränkung, und klicken Sie dann auf **Eigenschaften**. Ändern Sie im Fenster Eigenschaften die Eigenschaftswerte.  
  
4.  Legen Sie im Fenster **Eigenschaften** die folgenden Lese-/Schreibeigenschaften der Rangfolgeneinschränkung fest:  
  
    |Lese/Schreibeigenschaft|Konfigurationsaktion|  
    |--------------------------|--------------------------|  
    |BESCHREIBUNG|Bereitstellen einer Beschreibung.|  
    |EvalOp|Auswählen eines Auswertungsvorgangs. Wenn die Vorgänge `Expression` , **ExpressionAndConstant**oder **ExpressionOrConstant** ausgewählt sind, können Sie einen Ausdruck angeben.|  
    |expression|Wenn der Auswertungsvorgang einen Ausdruck einschließt, wird ein Ausdruck bereitgestellt. Der Ausdruck muss zu einem booleschen Wert ausgewertet werden. Weitere Informationen zur Ausdruckssprache finden Sie unter [Integration Services-Ausdrücke &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md).|  
    |LogicalAnd|Legen `LogicalAnd` Sie fest, um anzugeben, ob die Rang folgen Einschränkung zusammen mit anderen Rang folgen Einschränkungen ausgewertet wird, wenn mehrere ausführbare Dateien vorausgehen und mit der eingeschränkten ausführbaren Datei verknüpft sind.|  
    |Name|Aktualisieren des Namens der Rangfolgeneinschränkung.|  
    |ShowAnnotation|Geben Sie den Typ der zu verwendenden Anmerkung ein. Wählen Sie **Never** aus, um Anmerkungen zu deaktivieren, **AsNeeded** , um Anmerkungen bei Bedarf zu aktivieren, **ConstraintName** , um automatisch den Wert mithilfe der Name-Eigenschaft anzumerken, **ConstraintDescription** , um automatisch den Wert mithilfe der Description-Eigenschaft anzumerken, und **ConstraintOptions** , um automatisch den Wert mithilfe der Eigenschaften Value und Expression anzumerken.|  
    |Wert|Wenn der Auswertungsvorgang in der EvalOP-Eigenschaft eine Einschränkung enthält, wählen Sie das Ausführungsergebnis der eingeschränkten ausführbaren Datei aus.|  
  
5.  Schließen Sie das Fenster Eigenschaften.  
  
6.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Rang folgen Einschränkungen](control-flow/precedence-constraints.md)   
 [Verbinden von Tasks und Containern mithilfe einer Standard Rang folgen Einschränkung](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)   
 [Festlegen des Werts einer Rang folgen Einschränkung mithilfe des Kontextmenüs](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md)   
 [Verwenden eines Ausdrucks in einer Rangfolgeneinschränkung](../../2014/integration-services/use-an-expression-in-a-precedence-constraint.md)  
  
  
