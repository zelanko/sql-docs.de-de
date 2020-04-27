---
title: For-Schleifencontainer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.forloopcontainerdetails.f1
helpviewer_keywords:
- repeating control flow
- containers [Integration Services], For Loop
- For Loop containers
ms.assetid: 44cf7355-992b-4bbf-a28c-bfb012de06f6
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 991223c373113b465c3182f552e5f5d157efef9f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62831604"
---
# <a name="for-loop-container"></a>For-Schleifencontainer
  Der For-Schleifencontainer definiert die Wiederholung einer Ablaufsteuerung in einem Paket. Die Schleifenimplementierung ist mit der **For** -Schleifenstruktur in Programmiersprachen zu vergleichen. Bei jeder Wiederholung der Schleife wertet der For-Schleifencontainer einen Ausdruck aus und wiederholt dessen Workflow, bis der Ausdruck zu `False` ausgewertet wird.  
  
 Der For-Schleifencontainer verwendet die folgenden Elemente zum Definieren der Schleife:  
  
-   Einen optionalen Initialisierungsausdruck, der den Schleifenzählern Werte zuweist.  
  
-   Einen Auswertungsausdruck, der den Ausdruck enthält, um zu testen, ob die Schleife beendet oder fortgesetzt werden soll.  
  
-   Einen optionalen Iterationsausdruck, der den Schleifenzähler inkrementiert oder reduziert.  
  
 Das folgende Diagramm zeigt einen For-Schleifencontainer mit einem Task Mail senden. Falls der Initialisierungsausdruck `@Counter = 0`ist, lautet der Auswertungsausdruck `@Counter < 4`. Falls der Iterationsausdruck `@Counter = @Counter + 1`ist, wird die Schleife viermal wiederholt, und es werden vier E-Mail-Nachrichten gesendet.  
  
 ![For-Schleifencontainer wiederholt einen Task viermal](../media/ssis-forloop.gif "For-Schleifencontainer wiederholt einen Task viermal")  
  
 Die Ausdrücke müssen für gültige [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Ausdrücke sein.  
  
 Zum Erstellen der Initialisierungs- und Zuweisungsausdrücke können Sie den Zuweisungsoperator (=) verwenden. Dieser Operator wird ansonsten nicht von der SQL Server Integration Services-Ausdrucksgrammatik unterstützt und kann nur von Initialisierungs- und Zuweisungsausdrücken im For-Schleifencontainer verwendet werden. Jeder Ausdruck, der den Zuweisungsoperator verwendet, erfordert die Syntax `@Var = <expression>`. Hierbei ist **Var** eine Laufzeitvariable, und \<expression> ist ein Ausdruck, der den Regeln der [!INCLUDE[ssIS](../../../includes/ssis-md.md)]-Ausdruckssyntax entspricht. Für diesen Ausdruck sind die Variablen, Literale sowie Operatoren und Funktionen zulässig, die von der SSIS-Ausdrucksgrammatik unterstützt werden. Der Ausdruck muss zu einem Datentyp ausgewertet werden, der in den Datentyp der Variablen umgewandelt werden kann.  
  
 Für einen For-Schleifencontainer ist nur ein Auswertungsausdruck zulässig. Dies bedeutet, dass der For-Schleifencontainer alle Ablaufsteuerungselemente mit der gleichen Häufigkeit ausführt. Der For-Schleifencontainer kann andere For-Schleifencontainer enthalten, sodass Sie geschachtelte Schleifen erstellen und komplexe Schleifen in Pakete implementieren können.  
  
 Sie können eine Transaktionseigenschaft für den For-Schleifencontainer festlegen, um eine Transaktion für eine Teilmenge der Paketablaufsteuerung zu definieren. Auf diese Weise können Sie Transaktionen mit feinerer Granularität verwalten. Angenommen, ein For-Schleifencontainer wiederholt eine Ablaufsteuerung, die Daten in einer Tabelle mehrmals aktualisiert. In diesem Fall können Sie für die For-Schleife und deren Ablaufsteuerung die Verwendung einer Transaktion konfigurieren, um sicherzustellen, dass entweder alle oder überhaupt keine Daten aktualisiert werden. Weitere Informationen finden Sie unter [Integration Services-Transaktionen](../integration-services-transactions.md).  
  
## <a name="configuration-of-the-for-loop-container"></a>Konfiguration des For-Schleifencontainers  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer festlegen können:  
  
-   [For-Schleifen-Editor](../for-loop-editor.md)  
  
-   [Seite Ausdrücke](../expressions/expressions-page.md)  
  
 Weitere Informationen zum programmgesteuerten Festlegen dieser Eigenschaften finden Sie in der Dokumentation zur **T:Microsoft.SqlServer.Dts.Runtime.ForLoop** -Klasse im Entwicklerhandbuch.  
  
## <a name="related-tasks"></a>Related Tasks  
 Informationen zum Konfigurieren eines For-Schleifencontainers finden Sie in den nachfolgenden Themen.  
  
-   [Konfigurieren eines For-Schleifencontainers](for-loop-container.md)  
  
-   [Festlegen der Eigenschaften eines Tasks oder Containers](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ablaufsteuerung](control-flow.md)   
 [Integration Services-Ausdrücke &#40;SSIS&#41;](../expressions/integration-services-ssis-expressions.md)  
  
  
