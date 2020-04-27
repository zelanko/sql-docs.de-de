---
title: Hinzufügen einer Iterationen zu einer Ablauf Steuerung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- repeating workflows
- adding iterations
- control flow [Integration Services], iterations
- expressions [Integration Services], control flow
- iterations [Integration Services]
- For Loop containers
ms.assetid: eb3a7494-88ae-4165-9d0f-58715eb1734a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b96f5f900e8c1a3adf136c7bdaf1b89f297e4921
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66061983"
---
# <a name="add-iteration-to-a-control-flow"></a>Hinzufügen einer Iteration zu einer Ablaufsteuerung
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] schließt den For-Schleifencontainer ein. Dabei handelt es sich um ein Ablaufsteuerungselement, mit dem Sie auf einfache Weise Schleifen einschließen können, mit denen eine Ablaufsteuerung in einem Paket wiederholt wird. Weitere Informationen finden Sie unter [For-Schleifencontainer](control-flow/for-loop-container.md)ausgewertet wird.  
  
 Der For-Schleifencontainer wertet eine Bedingung für jede Iteration der Schleife aus und wird beendet, wenn die Bedingung zu False ausgewertet wird. Der For-Schleifencontainer enthält Ausdrücke zum Initialisieren der Schleife, zum Angeben der Auswertungsbedingung, mit der die Wiederholung der Ablaufsteuerung beendet wird, und zum Zuweisen eines Wertes zu einem Ausdruck, mit dem die Auswertungsbedingung verglichen wird. Sie müssen eine Auswertungsbedingung angeben, Initialisierungs- und Zuweisungsausdrücke sind dagegen optional.  
  
 Der For-Schleifencontainer stellt keine Funktionalität bereit. Er stellt lediglich die Struktur bereit, in der Sie die wiederholbare Ablaufsteuerung erstellen. Sie müssen mindestens einen Task in den For-Schleifencontainer einschließen, um Containerfunktionalität bereitzustellen. Weitere Informationen finden Sie unter [Integration Services-Tasks](control-flow/integration-services-tasks.md).  
  
 Der For-Schleifencontainer kann eine Ablaufsteuerung mit mehreren Tasks und anderen Containern enthalten. Das Hinzufügen von Tasks und Containern zu einem For-Schleifencontainer ist mit dem Hinzufügen von Tasks und Containern zu einem Paket vergleichbar, außer dass Sie die Tasks und Container nicht in das Paket, sondern in den For-Schleifencontainer ziehen. Falls der For-Schleifencontainer mehrere Tasks oder Container einschließt, können Sie diese wie bei einem Paket mithilfe von Rangfolgeneinschränkungen verbinden. Weitere Informationen finden Sie unter [Rangfolgeneinschränkungen](control-flow/precedence-constraints.md).  
  
## <a name="using-expressions-in-for-loop-configuration"></a>Verwenden von Ausdrücken bei der For-Schleifenkonfiguration  
 Wenn Sie den For-Schleifencontainer konfigurieren, indem Sie eine Auswertungsbedingung, einen Initialisierungswert oder einen Zuweisungswert angeben, können Sie Literale oder Ausdrücke verwenden.  
  
 Die Ausdrücke können Variablen einschließen. Die Verwendung von Variablen bietet den Vorteil, dass sie zur Laufzeit aktualisiert werden können, wodurch die Pakete flexibler und einfacher zu verwalten sind. Die maximale Länge eines Ausdrucks beträgt 4000 Zeichen.  
  
 Wenn Sie eine Variable in einem Ausdruck angeben, müssen Sie dem Variablennamen ein @-Zeichen voranstellen. Geben Sie @Counter z. b. für `Counter`eine Variable mit dem Namen in den Ausdruck ein, den der for-Schleifen Container verwendet. Falls Sie die Namespaceeigenschaft für die Variable angeben, müssen Sie die Variable und den Namespace in eckige Klammern einschließen. Geben Sie z. b `Counter` . für eine `MyNamespace` Variable im-Namespace@MyNamespace::Counter[] ein.  
  
 Die Variablen, die der For-Schleifencontainer verwendet, müssen im Bereich des For-Schleifencontainers oder im Bereich eines beliebigen Containers, der in der Paketcontainerhierarchie höher angeordnet ist, definiert sein. Beispielsweise kann ein For-Schleifencontainer Variablen verwenden, die in seinem Bereich definiert sind, sowie Variablen, die im Paketbereich definiert sind. Weitere Informationen finden Sie unter [Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md) und [Verwenden von Variablen in Paketen](../../2014/integration-services/use-variables-in-packages.md).  
  
 Die Ausdrucksgrammatik von [!INCLUDE[ssIS](../includes/ssis-md.md)] stellt umfangreiche Operatoren und Funktionen zum Implementieren komplexer Ausdrücke bereit, die zum Auswerten, Initialisieren oder Zuweisen verwendet werden. Weitere Informationen finden Sie unter [Integration Services-Ausdrücke &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md)ausgewertet wird.  
  
### <a name="to-implement-a-for-loop-container-in-a-control-flow"></a>So implementieren Sie einen For-Schleifencontainer in einer Ablaufsteuerung  
  
1.  Fügen Sie dem Paket den For-Schleifencontainer hinzu. Weitere Informationen finden Sie unter [Hinzufügen oder Löschen eines Tasks oder Containers in einer Ablauf Steuerung](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md) .  
  .  
  
2.  Fügen Sie dem For-Schleifencontainer Tasks und Container hinzu. Weitere Informationen finden Sie unter [Hinzufügen oder Löschen eines Tasks oder Containers in einer Ablauf Steuerung](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md) .  
  .  
  
3.  Verbinden Sie Tasks und Container im For-Schleifencontainer mithilfe von Rangfolgeneinschränkungen. Weitere Informationen finden Sie unter [Verbinden von Tasks und Containern mithilfe einer Standardrangfolgeneinschränkung](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md).  
  
4.  Konfigurieren Sie den For-Schleifencontainer. Weitere Informationen finden Sie unter [Konfigurieren eines For-Schleifencontainers](../../2014/integration-services/configure-a-for-loop-container.md)ausgewertet wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen oder Löschen eines Tasks oder Containers in einer Ablauf Steuerung](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)   
 [Gruppieren oder Deaktivieren von Komponenten](group-or-ungroup-components.md)   
 [Verbinden von Tasks und Containern mithilfe einer Standard Rang folgen Einschränkung](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)   
 [Hinzufügen einer Enumeration zu einer Ablauf Steuerung](../../2014/integration-services/add-enumeration-to-a-control-flow.md)   
 [Ablaufsteuerung](control-flow/control-flow.md)  
  
  
