---
title: Hinzufügen von Ausdrücken zu Rangfolgeneinschränkungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- precedence executables [Integration Services]
- precedence constraints [Integration Services], adding expressions
- adding expressions
- constrained executables [Integration Services]
- combining constraints
- expressions [Integration Services], constraints
ms.assetid: 5574d89a-a68e-4b84-80ea-da93305e5ca1
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 68455f23f5d05895af8f0cfb4d7b1e12e3d65b16
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66061895"
---
# <a name="add-expressions-to-precedence-constraints"></a>Hinzufügen von Ausdrücken zu Rangfolgeneinschränkungen
  Eine Rangfolgeneinschränkung kann mithilfe eines Ausdrucks die Einschränkung zwischen zwei ausführbaren Dateien definieren, nämlich der ausführbaren Datei der Rangfolge und der eingeschränkten ausführbaren Datei. Bei den ausführbaren Dateien kann es sich um Tasks oder Container handeln. Der Ausdruck kann separat oder in Kombination mit dem Ausführungsergebnis der ausführbaren Datei der Rangfolge verwendet werden. Das Ausführungsergebnis einer ausführbaren Datei ist Erfolg oder Fehler. Wenn Sie das Ausführungsergebnis einer Rangfolgeneinschränkung konfigurieren, können Sie das Ausführungsergebnis auf `Success`, `Failure` oder `Completion` festlegen. Für `Success` muss die ausführbare Datei der Rangfolge erfolgreich ausgeführt werden, für `Failure` muss die ausführbare Datei der Rangfolge mit einem Fehler ausgeführt werden. `Completion` zeigt an, dass die eingeschränkte ausführbare Datei unabhängig von einer erfolgreichen Ausführung des Rangfolgentasks ausgeführt werden sollte. Weitere Informationen finden Sie unter [Rangfolgeneinschränkungen](control-flow/precedence-constraints.md).  
  
 Der Ausdruck muss zu  `True` oder `False` ausgewertet werden, und er muss ein gültiger [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Ausdruck sein. Für diesen Ausdruck sind Literale, Systemvariablen und benutzerdefinierte Variablen sowie die Funktionen und Operatoren zulässig, die von der [!INCLUDE[ssIS](../includes/ssis-md.md)] -Ausdrucksgrammatik bereitgestellt werden. Beispielsweise verwendet der Ausdruck `@Count == SQRT(144) + 10` die `Count`-Variable, die SQRT-Funktion und die Operatoren Gleich (==) und Hinzufügen (+) . Weitere Informationen finden Sie unter [Integration Services-Ausdrücke &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md)ausgewertet wird.  
  
 In der folgenden Abbildung sind Task A und Task B durch eine Rangfolgeneinschränkung miteinander verlinkt, die ein Ausführungsergebnis und einen Ausdruck verwendet. Der Einschränkungswert ist auf `Success` festgelegt, und der Ausdruck lautet `@X >== @Z`. Task B, der eingeschränkte Task, wird nur ausgeführt, wenn Task A erfolgreich abgeschlossen wird und der Wert der `X`-Variablen größer oder gleich dem Wert der `Z`-Variablen ist.  
  
 ![Rangfolgeneinschränkung zwischen zwei Tasks](media/mw-dts-03.gif "Rangfolgeneinschränkung zwischen zwei Tasks")  
  
 Ausführbare Dateien können auch mithilfe mehrerer Rangfolgeneinschränkungen miteinander verlinkt werden, die unterschiedliche Ausdrücke enthalten. Beispielsweise sind in der folgenden Abbildung Task B und Task C mit Task A durch Rangfolgeneinschränkungen verlinkt, die Ausführungsergebnisse und Ausdrücke verwenden. Beide Einschränkungswerte sind auf `Success.` festgelegt. Eine Rangfolgeneinschränkung enthält den Ausdruck `@X >== @Z`, und die andere Rangfolgeneinschränkung den Ausdruck `@X < @Z`. In Abhängigkeit von den Werten der `X`-Variablen und der `Z`-Variablen wird Task C oder Task B ausgeführt.  
  
 ![Ausdrücke für Rangfolgeneinschränkungen](media/mw-dts-04.gif "Ausdrücke für Rangfolgeneinschränkungen")  
  
 Mit dem **Rangfolgeneinschränkungs-Editor** im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer und im Eigenschaftenfenster von [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] können Sie einen Ausdruck hinzufügen oder ändern. Das Eigenschaftenfenster ermöglicht jedoch keine Überprüfung der Ausdruckssyntax.  
  
 Wenn eine Rangfolgeneinschränkung einen Ausdruck einschließt, wird auf der Entwurfsoberfläche der Registerkarte **Ablaufsteuerung** neben der Rangfolgeneinschränkung ein Symbol angezeigt, und die QuickInfo auf dem Symbol zeigt den Ausdruck an.  
  
## <a name="combining-execution-values-and-expressions"></a>Kombinieren von Ausführungswerten und Ausdrücken  
 In der folgenden Tabelle werden die Auswirkung durch das Kombinieren einer Ausführungswerteinschränkung und eines Ausdrucks in einer Rangfolgeneinschränkung beschrieben.  
  
|Auswertungsvorgang|Einschränkung wird ausgewertet zu|Ausdruck wird ausgewertet zu|Eingeschränkte ausführbare Datei wird ausgeführt|  
|--------------------------|-----------------------------|-----------------------------|---------------------------------|  
|Einschränkung|Wahr|Nicht zutreffend|Wahr|  
|Einschränkung|False|–|False|  
|expression|Nicht zutreffend|Wahr|Wahr|  
|expression|Nicht zutreffend|False|False|  
|Einschränkung und Ausdruck|Wahr|Wahr|Wahr|  
|Einschränkung und Ausdruck|Wahr|False|False|  
|Einschränkung und Ausdruck|False|Wahr|False|  
|Einschränkung und Ausdruck|False|False|False|  
|Einschränkung oder Ausdruck|Wahr|Wahr|Wahr|  
|Einschränkung oder Ausdruck|Wahr|False|Wahr|  
|Einschränkung oder Ausdruck|False|Wahr|Wahr|  
|Einschränkung oder Ausdruck|False|False|False|  
  
### <a name="to-add-an-expression-to-a-precedence-constraint"></a>So fügen Sie einer Rangfolgeneinschränkung einen Ausdruck hinzu  
  
-   [Verwenden eines Ausdrucks in einer Rangfolgeneinschränkung](../../2014/integration-services/use-an-expression-in-a-precedence-constraint.md)  
  
-   [Festlegen der Eigenschaften von Rangfolgeneinschränkungen](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md)  
  
## <a name="external-resources"></a>Externe Ressourcen  
 Technischer Artikel, [SSIS Expression Examples](https://go.microsoft.com/fwlink/?LinkId=220761), auf social.technet.microsoft.com  
  
## <a name="see-also"></a>Siehe auch  
 [Mehrere Rangfolgeneinschränkungen](../../2014/integration-services/multiple-precedence-constraints.md)   
 [Rangfolgeneinschränkungen](control-flow/precedence-constraints.md)  
  
  
