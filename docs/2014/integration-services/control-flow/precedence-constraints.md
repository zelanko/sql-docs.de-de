---
title: Rangfolgeneinschränkungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- tasks [Integration Services], precedence constraints
- control flow [Integration Services], precedence constraints
- precedence constraints [Integration Services]
- constraints [Integration Services]
- sequence execution options [Integration Services]
- containers [Integration Services], precedence constraints
ms.assetid: c5ce5435-fd89-4156-a11f-68470a69aa9f
caps.latest.revision: 50
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 52729044444db0668870cc9878ee3184f17b49b9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37163041"
---
# <a name="precedence-constraints"></a>Rangfolgeneinschränkungen
  Rangfolgeneinschränkungen verknüpfen ausführbare Dateien, Container und Tasks in Paketen in einer Ablaufsteuerung und geben Bedingungen an, die bestimmen, ob ausführbare Dateien ausgeführt werden. Bei einer ausführbaren Datei kann es sich um einen For-Schleifencontainer, einen Foreach-Schleifencontainer, einen Task oder einen Ereignishandler handeln. Ereignishandler verwenden Rangfolgeneinschränkungen zum Verlinken der ausführbaren Dateien zu einer Ablaufsteuerung.  
  
 Eine Rangfolgeneinschränkung verlinkt zwei ausführbare Dateien: die ausführbare Datei der Rangfolge und die eingeschränkte ausführbare Datei. Die ausführbare Datei der Rangfolge wird vor der eingeschränkten ausführbaren Datei ausgeführt, und das Ausführungsergebnis der ausführbaren Datei der Rangfolge kann bestimmen, ob die eingeschränkte ausführbare Datei ausgeführt wird. Im folgenden Diagramm werden zwei ausführbare Dateien dargestellt, die durch eine Rangfolgeneinschränkung verlinkt sind.  
  
 ![Ausführbare Dateien, die durch eine Rangfolgeneinschränkung verlinkt sind](../media/ssis-pcsimple.gif "Ausführbare Dateien, die durch eine Rangfolgeneinschränkung verlinkt sind")  
  
 Bei einer linearen Ablaufsteuerung, also einer Ablaufsteuerung ohne Verzweigungen, bestimmen Rangfolgeneinschränkungen alleine die Reihenfolge, in der Tasks ausgeführt werden. Falls sich eine Ablaufsteuerung verzweigt, bestimmt die [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]-Runtime-Engine die Ausführungsreihenfolge für die Tasks und Container, die unmittelbar auf die Verzweigung folgen. Die Runtime-Engine bestimmt außerdem die Ausführungsreihenfolge für nicht verbundene Workflows in einer Ablaufsteuerung.  
  
 Die geschachtelte Containerarchitektur von [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ermöglicht allen Containern (mit Ausnahme des Taskhostcontainers, der nur einen einzelnen Task kapselt), andere Container mit jeweils eigener Ablaufsteuerung einzuschließen. Der For-Schleifencontainer, der Foreach-Schleifencontainer und der Sequenzcontainer können mehrere Tasks und andere Container, die wiederum mehrere Tasks und Container enthalten können, einschließen. Angenommen, ein Paket mit einem Skripttask und einem Sequenzcontainer weist eine Rangfolgeneinschränkung auf, die den Skripttask und den Sequenzcontainer verlinkt. Der Sequenzcontainer schließt drei Skripttasks ein, und die Rangfolgeneinschränkungen verlinken die drei Skripttasks zu einer Ablaufsteuerung. Im folgenden Diagramm werden die Rangfolgeneinschränkungen in einem Paket mit zwei Schachtelungsebenen dargestellt.  
  
 ![Rangfolgeneinschränkungen in einem Paket](../media/mw-dts-12.gif "Rangfolgeneinschränkungen in einem Paket")  
  
 Das Paket befindet sich ganz oben in der [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Containerhierarchie. Deshalb können mehrere Pakete nicht durch Rangfolgeneinschränkungen verlinkt werden. Sie können jedoch einem Paket einen Task Paket ausführen hinzufügen und indirekt ein anderes Paket mit der Ablaufsteuerung verlinken.  
  
 Es gibt folgende Möglichkeiten, um Rangfolgeneinschränkungen zu konfigurieren:  
  
-   Geben Sie einen Auswertungsvorgang an. Die Rangfolgeneinschränkung verwendet einen Einschränkungswert und/oder einen Ausdruck, um zu bestimmen, ob die eingeschränkte ausführbare Datei ausgeführt wird.  
  
-   Falls die Rangfolgeneinschränkung ein Ausführungsergebnis verwendet, können Sie als Ausführungsergebnis Erfolg, Fehler oder Beendigung angeben.  
  
-   Falls die Rangfolgeneinschränkung ein Auswertungsergebnis verwendet, können Sie einen Ausdruck angeben, der zu einem booleschen Wert ausgewertet wird.  
  
-   Geben Sie an, ob die Rangfolgeneinschränkung einzeln oder zusammen mit anderen Einschränkungen, die auf die eingeschränkte ausführbare Datei zutreffen, ausgewertet wird.  
  
## <a name="evaluation-operations"></a>Auswertungsvorgänge  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] stellt die folgenden Auswertungsvorgänge bereit:  
  
-   Eine Einschränkung, die nur mithilfe des Ausführungsergebnisses der ausführbaren Datei der Rangfolge bestimmt, ob die eingeschränkte ausführbare Datei ausgeführt wird. Das Ausführungsergebnis der ausführbaren Datei der Rangfolge kann Beendigung, Erfolg oder Fehler sein. Dies ist der Standardvorgang.  
  
-   Einen Ausdruck, der ausgewertet wird, um zu bestimmen, ob die eingeschränkte ausführbare Datei ausgeführt wird. Falls der Ausdruck zu True ausgewertet wird, wird die eingeschränkte ausführbare Datei ausgeführt.  
  
-   Einen Ausdruck und eine Einschränkung, die die Anforderungen von Ausführungsergebnissen der ausführbaren Datei der Rangfolge mit den zurückgegebenen Ergebnisse aus der Auswertung des Ausdrucks kombiniert.  
  
-   Einen Ausdruck oder eine Einschränkung, der bzw. die die Ausführungsergebnisse der ausführbaren Datei der Rangfolge oder die zurückgegebenen Ergebnisse aus der Auswertung des Ausdrucks verwendet.  
  
 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer mithilfe einer farbcodierung den Typ der rangfolgeneinschränkung zu identifizieren. Die Success-Einschränkung ist grün, die Failure-Einschränkung ist rot und die Completion-Einschränkung ist blau. Zum Anzeigen von Beschriftungen im [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer, die den Typ der Einschränkung anzeigen, müssen Sie die Barrierefreiheitsfunktionen des [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designers konfigurieren.  
  
 Der Ausdruck muss ein gültiger [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Ausdruck sein, der Funktionen, Operatoren sowie Systemvariablen und benutzerdefinierte Variablen einschließen kann. Weitere Informationen finden Sie unter [Integration Services-Ausdrücke &#40;SSIS&#41;](../expressions/integration-services-ssis-expressions.md) und [Integration Services-Variablen &#40;SSIS&#41;](../integration-services-ssis-variables.md).  
  
## <a name="execution-results"></a>Ausführungsergebnisse  
 Die Rangfolgeneinschränkung kann die folgenden Ausführungsergebnisse separat oder in Kombination mit einem Ausdruck verwenden.  
  
-   Für die Beendigung muss die ausführbare Datei der Rangfolge ungeachtet des Ergebnisses abgeschlossen worden sein, damit die eingeschränkte ausführbare Datei ausgeführt wird.  
  
-   Für Erfolg muss die ausführbare Datei der Rangfolge erfolgreich abgeschlossen worden sein, damit die eingeschränkte ausführbare Datei ausgeführt wird.  
  
-   Für Fehler muss bei der ausführbaren Datei der Rangfolge ein Fehler auftreten, damit die eingeschränkte ausführbare Datei ausgeführt wird.  
  
> [!NOTE]  
>  Nur rangfolgeneinschränkungen, die Mitglieder der gleichen `Precedence Constraint` Auflistung in einer logischen AND-Bedingung gruppiert werden. Beispielsweise können Rangfolgeneinschränkungen aus zwei Foreach-Schleifencontainern nicht kombiniert werden.  
  
## <a name="configuration-of-the-precedence-constraint"></a>Konfiguration der Rangfolgeneinschränkung  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Weitere Informationen zu den Eigenschaften, die Sie im [!INCLUDE[ssIS](../../../includes/ssis-md.md)]-Designer festlegen können, finden Sie unter [Rangfolgeneinschränkungs-Editor](../precedence-constraint-editor.md).  
  
 Weitere Informationen zum programmgesteuerten Festlegen dieser Eigenschaften finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>.  
  
## <a name="related-tasks"></a>Related Tasks  
 Klicken Sie auf eines der folgenden Themen, um nähere Informationen zum Festlegen dieser Eigenschaften im [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer zu erhalten:  
  
-   [Festlegen der Eigenschaften von Rangfolgeneinschränkungen](../set-the-properties-of-a-precedence-constraint.md)  
  
-   [Festlegen des Werts einer Rangfolgeneinschränkung mithilfe des Kontextmenüs](../set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md)  
  
-   [Verbinden von Tasks und Containern mithilfe einer Standardrangfolgen-Einschränkung](../connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)  
  
     Dieses Thema enthält Informationen dazu, wie Sie das Standardverhalten für Rangfolgeneinschränkungen festlegen und ausführbare Dateien mithilfe der Standardrangfolgeneinschränkungen verbinden.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 Technischer Artikel, [SSIS Expression Examples](http://go.microsoft.com/fwlink/?LinkId=220761), auf social.technet.microsoft.com  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Ausdrücken zu Rangfolgeneinschränkungen](../add-expressions-to-precedence-constraints.md)   
 [Mehrere Rangfolgeneinschränkungen](../multiple-precedence-constraints.md)  
  
  
