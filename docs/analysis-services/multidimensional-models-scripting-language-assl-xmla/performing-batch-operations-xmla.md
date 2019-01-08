---
title: Ausführen von Batchvorgängen (XMLA) | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6c451d13016915c9218efb2963429f8f5a7709e2
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52544233"
---
# <a name="performing-batch-operations-xmla"></a>Ausführen von Batchvorgängen (XMLA)
  Können Sie die [Batch](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) -Befehl in XML for Analysis (XMLA), führen Sie mehrere XMLA-Befehle, die mit einer einzigen XMLA- [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) Methode. Sie können mehrere Befehle, die in enthaltenen Ausführen der **Batch** Befehl entweder als einzelne Transaktion oder als individuelle Transaktionen für jeden Befehl, seriell oder parallel. Sie können auch angeben, Out-of-Line-Bindungen und andere Eigenschaften in der **Batch** Befehl für die Verarbeitung mehrerer [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Objekte.  
  
## <a name="running-transactional-and-nontransactional-batch-commands"></a>Ausführen von transaktionalen und nicht transaktionalen Batchbefehlen  
 Die **Batch** Befehl führt die Befehle in einer von zwei Arten:  
  
 **Transaktion**  
 Wenn die **Transaktion** Attribut der **Batch** Befehl festgelegt ist auf "true", die **Batch** Befehl führen Sie Befehle alle Befehle innerhalb der **Batch** Befehl in einer einzelnen Transaktion a *transaktionale* Batch.  
  
 Wenn ein Befehl in einem transaktionalen Batch fehlschlägt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Rollback für alle Befehle aus, der **Batch** -Befehl, der vor dem Befehl fehlgeschlagenen ausgeführt wurde, und die **Batch** -Befehl wird unmittelbar beendet. Alle Befehle in der **Batch** -Befehl, der noch nicht ausgeführt haben, werden nicht ausgeführt. Nach der **Batch** Befehl endet, die **Batch** -Befehl meldet alle Fehler, die für den fehlgeschlagenen Befehl aufgetreten sind.  
  
 **Nontransactional**  
 Wenn die **Transaktion** -Attribut auf "False" festgelegt ist die **Batch** Befehl führt jeden Befehl enthalten die **Batch** Befehl in einer separaten Transaktion a  *nicht transaktionale* Batch. Wenn ein Befehl in einem nicht transaktionalen Batch fehlschlägt der **Batch** Befehl zum Ausführen der Befehle nach dem Befehl der Fehler wird fortgesetzt. Nach der **Batch** Befehl versucht, alle Befehle auszuführen, die die **Batch** Befehl enthält, die **Batch** Befehl gibt alle aufgetretenen Fehler.  
  
 Alle Ergebnisse von Befehlen, die in enthaltenen eine **Batch** -Befehl zurückgegeben werden, in der gleichen Reihenfolge, in dem die Befehle enthalten sind, in, der **Batch** Befehl. Die Ergebnisse einer **Batch** Befehl variieren je nachdem, ob die **Batch** Befehl ist transaktional oder nicht transaktional.  
  
> [!NOTE]  
>  Wenn eine **Batch** -Befehl enthält einen Befehl, der keine Ausgabe, z. B. zurückgibt der [Sperre](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) Befehl, und dieser Befehl erfolgreich ausgeführt, die **Batch** Befehl gibt eine leere [Stamm](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/root-element-xmla) Element innerhalb des Elements der Ergebnisse. Die leere **Stamm** Element wird sichergestellt, dass jeder Befehl innerhalb einer **Batch** Befehl abgeglichen werden kann, mit dem entsprechenden **Stamm** -Element für die Ergebnisse des Befehls.  
  
### <a name="returning-results-from-transactional-batch-results"></a>Zurückgeben von Ergebnissen von transaktionalen Batchergebnissen  
 Ergebnisse von Befehlen in einem transaktionalen Batch ausgeführt werden nicht zurückgegeben, bis die gesamte **Batch** Befehl abgeschlossen ist. Die Ergebnisse werden nicht zurückgegeben werden, nach jedem Befehl ausgeführt wird, da es sich bei einem Befehl, mit dem ein Fehler auftritt, in einem transaktionalen Batch die gesamte würde **Batch** Befehl und alle darin enthaltenen Befehle ein Rollback ausgeführt werden. Wenn alle Befehle erfolgreich gestartet und ausgeführt, der [zurückgeben](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/return-element-xmla) Element der [ExecuteResponse](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects-executeresponse) von zurückgegebene Element der **Execute** -Methode für die **Batch**  -Befehl enthält eine [Ergebnisse](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/results-element-xmla) Element, das wiederum ein **Stamm** -Element für jeden erfolgreich ausgeführten Befehl innerhalb der **Batch** Befehl. Wenn ein Befehl die **Batch** Befehl kann nicht gestartet werden oder kann nicht abgeschlossen werden, die **Execute** Methode gibt einen SOAP-Fehler für die **Batch** Befehl, der den Fehler des der Befehl, der Fehler.  
  
### <a name="returning-results-from-nontransactional-batch-results"></a>Zurückgeben von Ergebnissen von nicht transaktionalen Batchergebnissen  
 Ergebnisse von Befehlen, die in einem nicht transaktionalen Batch ausgeführt werden zurückgegeben, in der Reihenfolge, in dem die Befehle, innerhalb enthalten sind, der **Batch** Befehl und wie sie von jedem Befehl zurückgegeben werden. Wenn keiner der in enthaltenen Befehle die **Batch** Befehl erfolgreich gestartet werden kann, die **Execute** Methode gibt einen SOAP-Fehler, die einen Fehler für enthält die **Batch** Befehl. Wenn mindestens ein Befehl wurde erfolgreich gestartet wurde, die **zurückgeben** Element der **ExecuteResponse** von zurückgegebene Element der **Execute** -Methode für die **Batch**  -Befehl enthält eine **Ergebnisse** Element, das wiederum ein **Stamm** -Element für jeden Befehl innerhalb der **Batch** Befehl . Wenn eine oder mehrere Befehle in einem nicht transaktionalen Batch kann nicht gestartet werden oder kann nicht abgeschlossen werden, die **Stamm** -Element für diesen fehlgeschlagenen Befehl enthält eine [Fehler](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/error-element-xmla) Element, das den Fehler beschreibt.  
  
> [!NOTE]  
>  Solange mindestens ein Befehl in einem nicht transaktionalen Batch gestartet werden kann, nicht transaktionalen Batch gilt erfolgreich ausgeführt haben, auch wenn alle in den nicht transaktionalen Batch enthaltene Befehl einen Fehler, in den Ergebnissen zurückgibt der **Batch**  Befehl.  
  
## <a name="using-serial-and-parallel-execution"></a>Verwenden von serieller und paralleler Ausführung  
 Sie können die **Batch** enthalten auszuführende Befehl Befehle seriell oder parallel. Wenn die Befehle seriell ausgeführt werden, enthalten der nächste Befehl der **Batch** Befehl kann nicht gestartet, bis der aktuell ausgeführten Befehl in der **Batch** Befehl abgeschlossen ist. Wenn die Befehle parallel ausgeführt werden, mehrere Befehle können ausgeführt werden gleichzeitig durch die **Batch** Befehl.  
  
 Damit Befehle parallel ausgeführt, Sie fügen die Befehle parallel ausgeführt werden hinzu, die [parallele](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/parallel-element-xmla) Eigenschaft der **Batch** Befehl. Derzeit [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] kann nur ausgeführt, zusammenhängender, sequenzieller [Prozess](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) Befehle parallel. Alle anderen XMLA-Befehl, z. B. [erstellen](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) oder [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla), enthalten in der **parallele** Eigenschaft seriell ausgeführt wird.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] versucht, alle auszuführen **Prozess** Befehle enthalten, die der **parallele** Eigenschaft gleichzeitig jedoch gewährleisten, dass alle enthaltenen kann nicht **Prozess** Befehle parallel ausgeführt werden können. Die Instanz analysiert jeden **Prozess** Befehl und, wenn die Instanz ermittelt, dass der Befehl nicht parallel ausgeführt werden darf nicht die **Prozess** seriell ausgeführt wird.  
  
> [!NOTE]  
>  Zum Ausführen von Befehlen gleichzeitig die **Transaktion** Attribut des der **Batch** Befehl muss festgelegt werden, auf true fest, da [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] unterstützt nur eine aktive Transaktion pro Verbindung und nicht transaktionalen Jeder Befehl Ausführen in einer separaten Transaktion. Wenn Sie enthalten die **parallele** -Eigenschaft in einem nicht transaktionalen Batch, ein Fehler auftritt.  
  
### <a name="limiting-parallel-execution"></a>Beschränken paralleler Ausführung  
 Ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instanz versucht, führen Sie so viele **Prozess** Befehle parallel wie möglich, bis zu den Grenzwerten des Computers, auf dem die Instanz ausgeführt wird. Sie können die Anzahl der gleichzeitig ausgeführten einschränken **Prozess** Befehle durch Festlegen der **MaxParallel** Attribut des der **parallele** Eigenschaft ein Wert, der die maximale Anzahl von **Prozess** Befehle, die parallel ausgeführt werden können.  
  
 Z. B. eine **parallele** Eigenschaft enthält die folgenden Befehle in der aufgeführten Reihenfolge:  
  
1.  **Erstellen**  
  
2.  **Verarbeiten**  
  
3.  **Alter**  
  
4.  **Verarbeiten**  
  
5.  **Verarbeiten**  
  
6.  **Verarbeiten**  
  
7.  **Delete**  
  
8.  **Verarbeiten**  
  
9. **Verarbeiten**  
  
 Die **MaxParalle**l-Attribut dieser **parallele** Eigenschaft auf 2 festgelegt ist. Daher führt die Instanz die vorherige Liste der Befehle wie in der folgenden Liste beschrieben aus:  
  
-   Befehl 1 wird seriell ausgeführt, da Befehl 1 ein **erstellen** -Befehl ist und nur **Prozess** Befehle parallel ausgeführt werden können.  
  
-   Befehl 2 wird seriell ausgeführt, nachdem Befehl 1 abgeschlossen wurde.  
  
-   Befehl 3 wird seriell ausgeführt, nachdem Befehl 2 abgeschlossen wurde.  
  
-   Befehle 4 und 5 werden parallel ausgeführt, nachdem Befehl 3 abgeschlossen wurde. Obwohl Befehl 6 auch ist eine **Prozess** Befehl Befehl 6 kann nicht parallel mit den Befehlen 4 und 5 ausgeführt, da die **MaxParallel** Eigenschaft auf 2 festgelegt ist.  
  
-   Befehl 6 wird seriell ausgeführt, nachdem die Befehle 4 und 5 abgeschlossen wurden.  
  
-   Befehl 7 wird seriell ausgeführt, nachdem Befehl 6 abgeschlossen wurde.  
  
-   Die Befehle 8 und 9 werden parallel ausgeführt, nachdem Befehl 7 abgeschlossen wurde.  
  
## <a name="using-the-batch-command-to-process-objects"></a>Verwenden des Batchbefehls für die Verarbeitung von Objekten  
 Die **Batch** -Befehl enthält mehrere optionale Eigenschaften und Attribute, die speziell eingebunden wurden zur Unterstützung von Verarbeitung mehrerer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Projekte:  
  
-   Die **ProcessAffectedObjects** Attribut der **Batch** Befehl gibt an, ob die Instanz ebenfalls Objekte, die erforderlich sind verarbeiten soll, eine erneute Verarbeitung aufgrund einer **Prozess** Befehl in der **Batch** -Befehl für die Verarbeitung eines angegebenen Objekts.  
  
-   Die [Bindungen](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla) Eigenschaft enthält eine Auflistung von Out-of-Line-Bindungen, die von allen verwendet die **Prozess** Befehle in der **Batch** Befehl.  
  
-   Die [DataSource](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasource-element-xmla) Eigenschaft enthält eine Out-of-Line-Bindung für eine Datenquelle, die von allen verwendet die **Prozess** Befehle in der **Batch** Befehl.  
  
-   Die [DataSourceView](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla) Eigenschaft enthält eine Out-of-Line-Bindung für eine Datenquellensicht, die von allen verwendet die **Prozess** Befehle in der **Batch** Befehl.  
  
-   Die [ErrorConfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla) Eigenschaft gibt an, wie in der die **Batch** Befehl behandelt Fehler, die von allen **Prozess** in die enthaltenenBefehle**Batch** Befehl.  
  
    > [!IMPORTANT]  
    >  Ein **Prozess** -Befehl kann nicht enthalten. die **Bindungen**, **DataSource**, **DataSourceView**, oder **ErrorConfiguration**  Eigenschaften, wenn die **Prozess** Befehl befindet sich einem **Batch** Befehl. Wenn Sie diese Eigenschaften angeben müssen eine **Prozess** Befehl, geben Sie die erforderlichen Informationen in den entsprechenden Eigenschaften der **Batch** Befehl, der die **Prozess** Befehl.  
  
## <a name="see-also"></a>Siehe auch  
 [Batch-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla)   
 [Element verarbeiten &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla)   
 [Verarbeiten eines mehrdimensionalen Modells &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)   
 [Entwickeln mit XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
