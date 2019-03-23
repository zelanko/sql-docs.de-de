---
title: Runtime-Methoden einer Datenflusskomponente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- run-time [Integration Services]
- data flow components [Integration Services], run-time methods
ms.assetid: fd9e4317-18dd-43af-bbdc-79db32183ac4
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e107660073716019f48def8578a424ead92abf32
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58393501"
---
# <a name="run-time-methods-of-a-data-flow-component"></a>Laufzeitmethoden einer Datenflusskomponente
  Zur Laufzeit wird vom Datenflusstask die Reihenfolge von Komponenten überprüft, ein Ausführungsplan vorbereitet und ein Pool von Arbeitsthreads verwaltet, die den Arbeitsplan ausführen. Der Task lädt Datenzeilen aus Quellen, verarbeitet diese durch Transformationen und speichert sie dann in Zielen.  
  
## <a name="sequence-of-method-execution"></a>Reihenfolge der Methodenausführung  
 Während der Ausführung einer Datenflusskomponente, wird eine Untergruppe der Methoden in der <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>-Basisklasse aufgerufen. Die Methoden und die Reihenfolge, in der diese aufgerufen werden, sind immer gleich, mit Ausnahme der <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>-Methode und der <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>-Methode. Diese beiden Methoden werden basierend auf dem Vorhandensein und der Konfiguration des <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100>-Objekts und des <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100>-Objekts einer Komponente aufgerufen.  
  
 In der folgenden Liste sind die Methoden in der Reihenfolge veranschaulicht, in der sie während der Komponentenausführung aufgerufen werden. Beachten Sie, dass <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> im Falle eines Aufrufs immer vor <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> aufgerufen wird.  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrepareForExecute%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PostExecute%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Cleanup%2A>  
  
### <a name="primeoutput-method"></a>PrimeOutput-Methode  
 Die <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.PrimeOutput%2A>-Methode wird aufgerufen, wenn eine Komponente mindestens eine Ausgabe aufweist, die über ein <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100>-Objekt an eine Downstreamkomponente angefügt ist, und die <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A>-Eigenschaft der Ausgabe 0 (null) beträgt. Die <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.PrimeOutput%2A>-Methode wird für Quellkomponenten und Transformationen mit asynchronen Ausgaben aufgerufen. Im Gegensatz zu der weiter unten beschriebenen <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>-Methode wird die <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>-Methode nur einmal für jede Komponente aufgerufen, für die dies erforderlich ist.  
  
### <a name="processinput-method"></a>ProcessInput-Methode  
 Die <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.ProcessInput%2A>-Methode wird für Komponenten aufgerufen, die über mindestens eine Eingabe verfügen, die durch ein <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100>-Objekt an eine Upstreamkomponente angefügt ist. Die <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.ProcessInput%2A>-Methode wird für Zielkomponenten und Transformationen mit synchronen Ausgaben aufgerufen. <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> wird wiederholt aufgerufen, bis keine Zeilen von Upstreamkomponenten mehr vorhanden sind, die verarbeitet werden können.  
  
## <a name="working-with-inputs-and-outputs"></a>Arbeiten mit Eingaben und Ausgaben  
 Zur Laufzeit werden die folgenden Tasks von Datenflusskomponenten ausgeführt:  
  
-   Quellkomponenten fügen Zeilen hinzu.  
  
-   Transformationskomponenten mit synchronen Ausgaben empfangen von Quellkomponenten bereitgestellte Zeilen.  
  
-   Transformationskomponenten mit asynchronen Ausgaben empfangen Zeilen und fügen Zeilen hinzu.  
  
-   Zielkomponenten empfangen Zeilen und laden sie dann in ein Ziel.  
  
 Während der Ausführung ordnet der Datenflusstask <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer>-Objekte zu, die alle Spalten enthalten, die in der Ausgabespaltenauflistung einer Sequenz von Komponenten definiert sind. Wenn jede der vier Komponenten in einem Datenflusstask beispielsweise seiner Ausgabespaltenauflistung eine Ausgabespalte hinzufügt, enthält der Puffer, der jeder Komponente bereitgestellt wird, vier Spalten, eine für jede Ausgabespalte pro Komponente. Aufgrund dieses Verhaltens empfängt eine Komponente manchmal Puffer, die Spalten enthalten, die nicht verwendet werden.  
  
 Da die von der Komponente empfangenen Puffer Spalten enthalten können, die von der Komponente nicht verwendet werden, müssen Sie die Spalten, die Sie in den Eingabe- und Ausgabespaltenauflistungen der Komponente verwenden möchten, in dem Puffer suchen, der der Komponente von dem Datenflusstask bereitgestellt wird. Dazu steht Ihnen die <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A>-Methode der <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A>-Eigenschaft zur Verfügung. Aus Leistungsgründen wird dieser Task in der Regeln nur während der <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>-Methode ausgeführt und nicht in <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> oder <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>.  
  
 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> wird vor der <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>-Methode und der <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>-Methode aufgerufen. Dies ist auch die erste Gelegenheit für eine Komponente, diese Arbeit auszuführen, nachdem <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> für diese Komponente verfügbar wird. Während dieser Methode sollte die Komponente ihre Spalten in den Puffern suchen und diese Informationen intern speichern, sodass die Spalten in der <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>-Methode oder der <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>-Methode verwendet werden können.  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie eine Transformationskomponente mit synchroner Ausgabe ihre Eingabespalten während der <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>-Methode im Puffer sucht.  
  
```csharp  
private int []bufferColumnIndex;  
public override void PreExecute()  
{  
    IDTSInput100 input = ComponentMetaData.InputCollection[0];  
    bufferColumnIndex = new int[input.InputColumnCollection.Count];  
  
    for( int x=0; x < input.InputColumnCollection.Count; x++)  
    {  
        IDTSInputColumn100 column = input.InputColumnCollection[x];  
        bufferColumnIndex[x] = BufferManager.FindColumnByLineageID( input.Buffer, column.LineageID);  
    }  
}  
```  
  
```vb  
Dim bufferColumnIndex As Integer()  
  
    Public Overrides Sub PreExecute()  
  
        Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)  
  
        ReDim bufferColumnIndex(input.InputColumnCollection.Count)  
  
        For x As Integer = 0 To input.InputColumnCollection.Count  
  
            Dim column As IDTSInputColumn100 = input.InputColumnCollection(x)  
            bufferColumnIndex(x) = BufferManager.FindColumnByLineageID(input.Buffer, column.LineageID)  
  
        Next  
  
    End Sub  
```  
  
### <a name="adding-rows"></a>Hinzufügen von Zeilen  
 Komponenten liefern Zeilen für Downstreamkomponenten, indem <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer>-Objekten Zeilen hinzugefügt werden. Der Datenflusstask stellt ein Array von Ausgabepuffern – einen für jedes <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100>-Objekt, das mit einer Downstreamkomponente verbunden ist – als Parameter für die <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>-Methode bereit. Quellkomponenten und Transformationskomponenten mit asynchronen Ausgaben fügen den Puffern Zeilen hinzu und rufen die  <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetEndOfRowset%2A>-Methode auf, wenn das Hinzufügen der Zeilen abgeschlossen ist. Der Datenflusstask verwaltet die Ausgabepuffer, die er den Komponenten bereitstellt und verschiebt die Zeilen in dem Puffer automatisch zur nächsten Komponente, wenn der Puffer voll ist. Die <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>-Methode wird, im Gegensatz zur <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>-Methode, die wiederholt aufgerufen wird, einmal pro Komponente aufgerufen.  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie eine Komponente ihrem Ausgabepuffer Zeilen während der <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>-Methode hinzufügt und dann die <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetEndOfRowset%2A>-Methode aufruft.  
  
```csharp  
public override void PrimeOutput( int outputs, int []outputIDs,PipelineBuffer []buffers)  
{  
    for( int x=0; x < outputs; x++ )  
    {  
        IDTSOutput100 output = ComponentMetaData.OutputCollection.GetObjectByID( outputIDs[x]);  
        PipelineBuffer buffer = buffers[x];  
  
        // TODO: Add rows to the output buffer.  
    }  
    foreach( PipelineBuffer buffer in buffers )  
    {  
        /// Notify the data flow task that no more rows are coming.  
        buffer.SetEndOfRowset();  
    }  
}  
```  
  
```vb  
public overrides sub PrimeOutput( outputs as Integer , outputIDs() as Integer ,buffers() as PipelineBuffer buffers)  
  
    For x As Integer = 0 To outputs.MaxValue  
  
        Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection.GetObjectByID(outputIDs(x))  
        Dim buffer As PipelineBuffer = buffers(x)  
  
        ' TODO: Add rows to the output buffer.  
  
    Next  
  
    For Each buffer As PipelineBuffer In buffers  
  
        ' Notify the data flow task that no more rows are coming.  
        buffer.SetEndOfRowset()  
  
    Next  
  
End Sub  
```  
  
 Weitere Informationen finden Sie unter [Entwickeln einer benutzerdefinierten Quellkomponente](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md) und [Entwickeln einer benutzerdefinierten Transformationskomponente mit asynchronen Ausgaben](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md).  
  
### <a name="receiving-rows"></a>Empfangen von Zeilen  
 Komponenten empfangen Zeilen von Upstreamkomponenten in <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer>-Objekten. Der Datenflusstask stellt ein <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer>-Objekt, das die dem Datenfluss von Upstreamkomponenten hinzugefügten Zeilen enthält, einer <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>-Methode als Parameter bereit. Dieser Eingabepuffer kann verwendet werden, um die Zeilen und Spalten in dem Puffer zu überprüfen und zu ändern, er kann jedoch nicht verwendet werden, um Zeilen hinzuzufügen oder zu entfernen. Die <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>-Methode wird immer wieder aufgerufen, bis keine verfügbaren Puffer mehr vorhanden sind. Beim letzten Aufruf ist die <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A>-Eigenschaft `true`. Sie können eine Iteration durch die Auflistung von Zeilen in dem Puffer mithilfe der <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.NextRow%2A>-Methode durchführen, durch die der Puffer zur nächsten Zeile bewegt wird. Diese Methode gibt `false` zurück, wenn sich der Puffer in der letzten Zeile der Auflistung befindet. Sie müssen die <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A>-Eigenschaft nicht überprüfen, außer Sie müssen eine weitere Aktion ausführen, nachdem die letzte Datenzeile verarbeitet wurde.  
  
 Im folgenden Text wird das korrekte Muster für die Verwendung <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.NextRow%2A>-Methode und der <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A>-Eigenschaft veranschaulicht.  
  
 `while (buffer.NextRow())`  
  
 `{`  
  
 `// Do something with each row.`  
  
 `}`  
  
 `if (buffer.EndOfRowset)`  
  
 `{`  
  
 `// Optionally, do something after all rows have been processed.`  
  
 `}`  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie eine Komponente die Zeilen in Eingabepuffern während der <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>-Methode verarbeitet.  
  
```csharp  
public override void ProcessInput( int inputID, PipelineBuffer buffer )  
{  
    {  
        IDTSInput100 input = ComponentMetaData.InputCollection.GetObjectByID(inputID);  
        while( buffer.NextRow())  
        {  
            // TODO: Examine the columns in the current row.  
        }  
}  
```  
  
```vb  
Public Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer)  
  
        Dim input As IDTSInput100 = ComponentMetaData.InputCollection.GetObjectByID(inputID)  
        While buffer.NextRow() = True  
  
            ' TODO: Examine the columns in the current row.  
        End While  
  
End Sub  
```  
  
 Weitere Informationen zum Entwickeln von Komponenten, die Zeilen in Eingabepuffern empfangen, finden Sie unter [Entwickeln einer benutzerdefinierten Zielkomponente](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md) und [Entwickeln einer benutzerdefinierten Transformationskomponente mit synchronen Ausgaben](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md).  
  
![Integration Services (kleines Symbol)](../../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services**<br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwurfszeitmethoden einer Datenflusskomponente](design-time-methods-of-a-data-flow-component.md)  
  
  
