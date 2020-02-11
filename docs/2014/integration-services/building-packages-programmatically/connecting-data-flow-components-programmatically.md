---
title: Programmgesteuertes Verbinden von Datenflusskomponenten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow task [Integration Services], components
- paths [Integration Services], components
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: 404ecab7-7698-447b-93d6-dd256beb11ff
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2d3b785785e9f3481b8dfb5f661b4b78f1923629
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62836339"
---
# <a name="connecting-data-flow-components-programmatically"></a>Programmgesteuertes Verbinden von Datenflusskomponenten
  Nachdem Sie dem Datenflusstask Komponenten hinzugefügt haben, verbinden Sie diese, um eine Ausführungsstruktur zu erstellen. Diese spiegelt den Datenfluss von den Quellen über Transformationen bis hin zu den Zielen wider. Sie verwenden <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100>-Objekte, um die Komponenten im Datenfluss zu verbinden.  
  
## <a name="creating-a-path"></a>Erstellen eines Pfads  
 Rufen Sie die neue Methode der <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.PathCollection%2A>-Eigenschaft der <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipe>-Schnittstelle auf, um einen neuen Pfad zu erstellen, und fügen Sie diesen der Pfadauflistung im Datenflusstask hinzu. Diese Methode gibt ein neues, getrenntes <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100>-Objekt zurück. Sie verwenden dieses anschließend, um zwei Komponenten zu verbinden.  
  
 Rufen Sie die <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100.AttachPathAndPropagateNotifications%2A>-Methode auf, um den Pfad zu verbinden und die Komponenten im Pfad über die Verbindung in Kenntnis zu setzen. Diese Methode akzeptiert eine <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> der Upstreamkomponente sowie eine <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100> der Downstreamkomponente als Parameter. Standardmäßig wird durch den Aufruf der <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A>-Methode der Komponente eine einzelne Eingabe für Komponenten, die über Eingaben verfügen, und eine einzelne Ausgabe für Komponenten, die über Ausgaben verfügen, erstellt. Im folgenden Beispiel wird diese Standardeinstellung für die Ausgabe der Quelle und die Eingabe des Ziels verwendet.  
  
## <a name="next-step"></a>Nächster Schritt  
 Nachdem Sie einen Pfad zwischen zwei Komponenten eingerichtet haben, ist der nächste Schritt, Eingabespalten in der Downstreamkomponente zuzuordnen. Dieser Vorgang wird im nächsten Thema – [Programmgesteuertes Auswählen von Eingabespalten](../building-packages-programmatically/selecting-input-columns-programmatically.md) – erläutert.  
  
## <a name="sample"></a>Beispiel  
 Im folgenden Codebeispiel wird die Einrichtung eines Pfads zwischen zwei Komponenten veranschaulicht.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package package = new Package();  
      Executable e = package.Executables.Add("STOCK:PipelineTask");  
      TaskHost thMainPipe = e as TaskHost;  
      MainPipe dataFlowTask = thMainPipe.InnerObject as MainPipe;  
  
      // Create the source component.    
      IDTSComponentMetaData100 source =  
        dataFlowTask.ComponentMetaDataCollection.New();  
      source.ComponentClassID = "DTSAdapter.OleDbSource";  
      CManagedComponentWrapper srcDesignTime = source.Instantiate();  
      srcDesignTime.ProvideComponentProperties();  
  
      // Create the destination component.  
      IDTSComponentMetaData100 destination =  
        dataFlowTask.ComponentMetaDataCollection.New();  
      destination.ComponentClassID = "DTSAdapter.OleDbDestination";  
      CManagedComponentWrapper destDesignTime = destination.Instantiate();  
      destDesignTime.ProvideComponentProperties();  
  
      // Create the path.  
      IDTSPath100 path = dataFlowTask.PathCollection.New();  
      path.AttachPathAndPropagateNotifications(source.OutputCollection[0],  
        destination.InputCollection[0]);  
    }  
  }  
```  
  
 }  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
Module Module1  
  
  Sub Main()  
  
    Dim package As Microsoft.SqlServer.Dts.Runtime.Package = _  
      New Microsoft.SqlServer.Dts.Runtime.Package()  
    Dim e As Executable = package.Executables.Add("STOCK:PipelineTask")  
    Dim thMainPipe As Microsoft.SqlServer.Dts.Runtime.TaskHost = _  
      CType(e, Microsoft.SqlServer.Dts.Runtime.TaskHost)  
    Dim dataFlowTask As MainPipe = CType(thMainPipe.InnerObject, MainPipe)  
  
    ' Create the source component.    
    Dim source As IDTSComponentMetaData100 = _  
      dataFlowTask.ComponentMetaDataCollection.New()  
    source.ComponentClassID = "DTSAdapter.OleDbSource"  
    Dim srcDesignTime As CManagedComponentWrapper = source.Instantiate()  
    srcDesignTime.ProvideComponentProperties()  
  
    ' Create the destination component.  
    Dim destination As IDTSComponentMetaData100 = _  
      dataFlowTask.ComponentMetaDataCollection.New()  
    destination.ComponentClassID = "DTSAdapter.OleDbDestination"  
    Dim destDesignTime As CManagedComponentWrapper = destination.Instantiate()  
    destDesignTime.ProvideComponentProperties()  
  
    ' Create the path.  
    Dim path As IDTSPath100 = dataFlowTask.PathCollection.New()  
    path.AttachPathAndPropagateNotifications(source.OutputCollection(0), _  
      destination.InputCollection(0))  
  
  End Sub  
  
End Module  
```  
  
![Integration Services Symbol (klein)](../media/dts-16.gif "Integration Services (kleines Symbol)")immer auf**dem neuesten Stand bleiben mit Integration Services**  <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Programmgesteuertes Auswählen von Eingabespalten](../building-packages-programmatically/selecting-input-columns-programmatically.md)  
  
  
