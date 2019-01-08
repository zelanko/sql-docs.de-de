---
title: Ausführen von Batchvorgängen (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- multiple projects
- XML for Analysis, batches
- parallel batch execution [XMLA]
- transactional batches
- serial batch execution [XMLA]
- XMLA, batches
- batches [XML for Analysis]
- nontransactional batches
ms.assetid: 731c70e5-ed51-46de-bb69-cbf5aea18dda
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bca0c74ab978b6f47e68221987777f1818a95b7b
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52542585"
---
# <a name="performing-batch-operations-xmla"></a>Ausführen von Batchvorgängen (XMLA)
  Können Sie die [Batch](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) -Befehl in XML for Analysis (XMLA), führen Sie mehrere XMLA-Befehle, die mit einer einzigen XMLA- [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) Methode. Sie können mehrere im `Batch`-Befehl enthaltene Befehle entweder als Einzeltransaktion oder als individuelle Transaktionen für jeden Befehl in Serie oder parallel ausführen. Sie können auch angeben, Out-of-Line-Bindungen und andere Eigenschaften in der `Batch` Befehl für die Verarbeitung mehrerer [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Objekte.  
  
## <a name="running-transactional-and-nontransactional-batch-commands"></a>Ausführen von transaktionalen und nicht transaktionalen Batchbefehlen  
 Der Befehl `Batch` führt Befehle in einer von zwei Methoden aus:  
  
 **Transaktion**  
 Wenn die `Transaction` Attribut der `Batch` Befehl festgelegt ist auf "true", die `Batch` Befehl führen Sie Befehle alle Befehle innerhalb der `Batch` Befehl in einer einzelnen Transaktion eine *transaktionale* Batch.  
  
 Wenn ein Befehl in einem transaktionalen Batch fehlschlägt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Rollback für alle Befehle aus, der `Batch` -Befehl, der vor dem Befehl fehlgeschlagenen ausgeführt wurde, und die `Batch` -Befehl wird unmittelbar beendet. Jegliche noch nicht ausgeführten Befehle im Befehl `Batch` werden nicht ausgeführt. Nachdem der Befehl `Batch` beendet wurde, meldet der Befehl `Batch` alle Fehler, die für den fehlgeschlagenen Befehl aufgetreten sind.  
  
 **Nontransactional**  
 Wenn die `Transaction` -Attribut auf "False" festgelegt ist die `Batch` Befehl führt jeden Befehl enthalten die `Batch` Befehl in einer separaten Transaktion a *nicht transaktionalen* Batch. Wenn ein beliebiger Befehl in einem nicht transaktionalen Batch fehlschlägt, führt der `Batch`-Befehl weiterhin alle Befehle nach dem fehlgeschlagenen Befehl aus. Nachdem der `Batch`-Befehl versucht hat, alle im `Batch`-Befehl enthaltenen Befehle auszuführen, meldet der `Batch`-Befehl alle aufgetretenen Fehler.  
  
 Alle Ergebnisse, die von Befehlen zurückgegeben werden, die im `Batch`-Befehl enthalten sind, werden in der gleichen Reihenfolge zurückgegeben, in der die Befehle im `Batch`-Befehl enthalten sind. Die von einem `Batch`-Befehl zurückgegebenen Ergebnisse fallen unterschiedlich aus, je nachdem, ob der `Batch`-Befehl transaktional oder nicht transaktional ist.  
  
> [!NOTE]  
>  Wenn eine `Batch` -Befehl enthält einen Befehl, der keine Ausgabe, z. B. zurückgibt der [Sperre](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) Befehl, und dieser Befehl erfolgreich ausgeführt, die `Batch` Befehl gibt eine leere [Stamm](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/root-element-xmla) Element innerhalb des Elements der Ergebnisse. Das leere `root`-Element stellt sicher, dass jeder in einem `Batch`-Befehl enthaltene Befehl dem für die Ergebnisse des Befehls geeigneten `root`-Element zugeordnet werden kann.  
  
### <a name="returning-results-from-transactional-batch-results"></a>Zurückgeben von Ergebnissen von transaktionalen Batchergebnissen  
 Ergebnisse von Befehlen, die in einem transaktionalen Batch ausgeführt werden, werden nicht zurückgegeben, solange der `Batch`-Befehl noch nicht vollständig ausgeführt ist. Die Ergebnisse werden nicht nach Ausführung eines jeden Befehls zurückgegeben, da jeder fehlgeschlagene Befehl in einem transaktionalen Batch dazu führt, dass ein Rollback für den gesamten `Batch`-Befehl und alle darin enthaltenen Befehle durchgeführt wird. Wenn alle Befehle erfolgreich gestartet und ausgeführt, die [zurückgeben](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/return-element-xmla) Element der [ExecuteResponse](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects-executeresponse) von zurückgegebene Element der `Execute` -Methode für die `Batch` -Befehl enthält eine [Ergebnisse](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/results-element-xmla) Element, das wiederum ein `root` -Element für jeden erfolgreich ausgeführten Befehl innerhalb der `Batch` Befehl. Wenn ein Befehl im `Batch`-Befehl nicht gestartet werden kann oder fehlschlägt, gibt die `Execute`-Methode einen SOAP-Fehler für den `Batch`-Befehl aus, der den Fehler des fehlgeschlagenen Befehls enthält.  
  
### <a name="returning-results-from-nontransactional-batch-results"></a>Zurückgeben von Ergebnissen von nicht transaktionalen Batchergebnissen  
 Ergebnisse von Befehlen, die in einem nicht transaktionalen Batch ausgeführt werden, werden in der Reihenfolge zurückgegeben, in der sie im `Batch`-Befehl enthalten sind und wie sie von jedem Befehl zurückgegeben werden. Wenn keiner der Befehle, die im `Batch`-Befehl enthalten sind, erfolgreich gestartet werden kann, gibt die `Execute`-Methode einen SOAP-Fehler zurück, der einen Fehler für den `Batch`-Befehl enthält. Wenn mindestens ein Befehl erfolgreich gestartet werden kann, enthält das `return`-Element des `ExecuteResponse`-Elements, das von der `Execute`-Methode für den `Batch`-Befehl ausgegeben wird, ein `results`-Element, das wiederum ein `root`-Element für jeden im `Batch`-Befehl enthaltenen Befehl enthält. Wenn eine oder mehrere Befehle in einem nicht transaktionalen Batch kann nicht gestartet werden oder kann nicht abgeschlossen werden, die `root` -Element für diesen fehlgeschlagenen Befehl enthält eine [Fehler](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/error-element-xmla) Element, das den Fehler beschreibt.  
  
> [!NOTE]  
>  Solange mindestens ein Befehl in einem nicht transaktionalen Batch gestartet werden kann, wird der nicht transaktionale Batch als erfolgreich ausgeführt angesehen, auch wenn jeder im nicht transaktionalen Batch enthaltene Befehl einen Fehler in den Ergebnissen des `Batch`-Befehls zurückgibt.  
  
## <a name="using-serial-and-parallel-execution"></a>Verwenden von serieller und paralleler Ausführung  
 Sie können den `Batch`-Befehl verwenden, um eingeschlossene Befehle seriell oder parallel auszuführen. Wenn die Befehle seriell ausgeführt werden, kann der nächste im `Batch`-Befehl enthaltene Befehl nicht gestartet werden, solange nicht der `Batch`-Befehl, der aktuell ausgeführt wird, abgeschlossen ist. Wenn die Befehle parallel ausgeführt werden, können mehrere Befehle gleichzeitig vom `Batch`-Befehl ausgeführt werden.  
  
 Damit Befehle parallel ausgeführt, Sie fügen die Befehle parallel ausgeführt werden hinzu, die [parallele](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/parallel-element-xmla) Eigenschaft der `Batch` Befehl. Derzeit [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] kann nur ausgeführt, zusammenhängender, sequenzieller [Prozess](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) Befehle parallel. Alle anderen XMLA-Befehl, z. B. [erstellen](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) oder [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla), enthalten in der `Parallel` Eigenschaft seriell ausgeführt wird.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] versucht, alle `Process`-Befehle, die in die `Parallel`-Eigenschaft eingebunden werden, parallel auszuführen. Es gibt allerdings keine Garantie dafür, dass alle enthaltenen `Process`-Befehle parallel ausgeführt werden. Die Instanz analysiert jeden `Process`-Befehl, und wenn die Instanz ermittelt, dass der Befehl nicht parallel ausgeführt werden kann, wird der `Process`-Befehl seriell ausgeführt.  
  
> [!NOTE]  
>  Damit Befehle parallel ausgeführt werden können, muss das `Transaction`-Attribut des `Batch`-Befehls auf True gesetzt sein, da [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] nur eine aktive Transaktion pro Verbindung unterstützt und nicht transaktionale Batches jeden Befehl in einer separaten Transaktion ausführen. Wenn Sie die `Parallel`-Eigenschaft in einen nicht transaktionalen Batch einbinden, tritt ein Fehler auf.  
  
### <a name="limiting-parallel-execution"></a>Beschränken paralleler Ausführung  
 Eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz versucht, so viele `Process`-Befehle wie möglich parallel auszuführen. Die Anzahl ist durch den Computer beschränkt, auf dem die Instanz ausgeführt wird. Sie können die Anzahl gleichzeitig auszuführender `Process`-Befehle beschränken, indem Sie das `maxParallel`-Attribut der `Parallel`-Eigenschaft auf einen Wert setzen, der die maximale Anzahl an `Process`-Befehlen angibt, die parallel ausgeführt werden können.  
  
 Beispielsweise enthält eine `Parallel`-Eigenschaft die folgenden Befehle in der aufgelisteten Reihenfolge:  
  
1.  `Create`  
  
2.  `Process`  
  
3.  `Alter`  
  
4.  `Process`  
  
5.  `Process`  
  
6.  `Process`  
  
7.  `Delete`  
  
8.  `Process`  
  
9. `Process`  
  
 Das Attribut `maxParalle`l dieser `Parallel`-Eigenschaft ist auf 2 gesetzt. Daher führt die Instanz die vorherige Liste der Befehle wie in der folgenden Liste beschrieben aus:  
  
-   Befehl 1 wird seriell ausgeführt, da Befehl 1 ein `Create`-Befehl ist und nur `Process`-Befehle parallel ausgeführt werden können.  
  
-   Befehl 2 wird seriell ausgeführt, nachdem Befehl 1 abgeschlossen wurde.  
  
-   Befehl 3 wird seriell ausgeführt, nachdem Befehl 2 abgeschlossen wurde.  
  
-   Befehle 4 und 5 werden parallel ausgeführt, nachdem Befehl 3 abgeschlossen wurde. Obwohl Befehl 6 auch ein `Process`-Befehl ist, kann Befehl 6 nicht parallel mit den Befehlen 4 und 5 ausgeführt werden, da die `maxParallel`-Eigenschaft auf 2 gesetzt ist.  
  
-   Befehl 6 wird seriell ausgeführt, nachdem die Befehle 4 und 5 abgeschlossen wurden.  
  
-   Befehl 7 wird seriell ausgeführt, nachdem Befehl 6 abgeschlossen wurde.  
  
-   Die Befehle 8 und 9 werden parallel ausgeführt, nachdem Befehl 7 abgeschlossen wurde.  
  
## <a name="using-the-batch-command-to-process-objects"></a>Verwenden des Batchbefehls für die Verarbeitung von Objekten  
 Der Befehl `Batch` enthält mehrere optionale Eigenschaften und Attribute, die speziell eingebunden wurden, um die Verarbeitung mehrerer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Projekte zu unterstützen:  
  
-   Das `ProcessAffectedObjects`-Attribut des `Batch`-Befehls gibt an, ob die Instanz ebenfalls Objekte verarbeiten soll, die als Ergebnis eines `Process`-Befehls, der im `Batch`-Befehl für die Verarbeitung eines bestimmten Objekts enthalten ist, eine erneute Verarbeitung erfordern.  
  
-   Die [Bindungen](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla) Eigenschaft enthält eine Auflistung von Out-of-Line-Bindungen, die von allen verwendet die `Process` Befehle in der `Batch` Befehl.  
  
-   Die [DataSource](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla) Eigenschaft enthält eine Out-of-Line-Bindung für eine Datenquelle, die von allen verwendet die `Process` Befehle in der `Batch` Befehl.  
  
-   Die [DataSourceView](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla) Eigenschaft enthält eine Out-of-Line-Bindung für eine Datenquellensicht, die von allen verwendet die `Process` Befehle in der `Batch` Befehl.  
  
-   Die [ErrorConfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla) Eigenschaft gibt an, wie in der die `Batch` Befehl behandelt Fehler, die von allen `Process` in enthaltenen Befehle die `Batch` Befehl.  
  
    > [!IMPORTANT]  
    >  Ein `Process`-Befehl kann nicht die Eigenschaften `Bindings`, `DataSource`, `DataSourceView` oder `ErrorConfiguration` enthalten, wenn der `Process`-Befehl in einem `Batch`-Befehl enthalten ist. Wenn Sie diese Eigenschaften für einen `Process`-Befehl festlegen müssen, geben Sie die notwendigen Informationen in den entsprechenden Eigenschaften des `Batch`-Befehls an, der im `Process`-Befehl enthalten ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Batch-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla)   
 [Element verarbeiten &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla)   
 [Verarbeitung von mehrdimensionalen Modellobjekten](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md)   
 [Entwickeln mit XMLA in Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
