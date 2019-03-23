---
title: Codieren eines benutzerdefinierten Foreach-Enumerators | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom foreach enumerators [Integration Services], coding
ms.assetid: 279cf6de-d06f-40e7-b8ca-569310449f36
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 84e1b606c9eedaf4ae1d4b8394b8bf8d2bdcb140
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58390188"
---
# <a name="coding-a-custom-foreach-enumerator"></a>Codieren eines benutzerdefinierten Foreach-Enumerators
  Nachdem Sie eine Klasse erstellt haben, die von der <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator>-Basisklasse erbt, und das <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>-Attribut auf die Klasse angewendet haben, müssen Sie die Implementierung der Eigenschaften und Methoden der Basisklasse überschreiben, um die benutzerdefinierte Funktionalität bereitzustellen.  
  
 Ein funktionierendes Beispiel eines benutzerdefinierten Enumerators finden Sie unter [Developing a User Interface for a Custom ForEach Enumerator](developing-a-user-interface-for-a-custom-foreach-enumerator.md) (Entwickeln einer Benutzeroberfläche für einen benutzerdefinierten ForEach-Enumerator).  
  
## <a name="initializing-the-enumerator"></a>Initialisieren des Enumerators  
 Sie können die <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.InitializeForEachEnumerator%2A>-Methode verwenden, um Verweise auf die im Paket definierten Verbindungs-Manager zwischenzuspeichern und um Verweise auf die Ereignisschnittstelle zwischenzuspeichern, die Sie verwenden können, um Fehler, Warnungen und Informationsmeldungen auszulösen.  
  
## <a name="validating-the-enumerator"></a>Überprüfen des Enumerators  
 Überschreiben Sie die <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.Validate%2A>-Methode, um zu überprüfen, ob der Enumerator ordnungsgemäß konfiguriert ist. Wenn die Methode `Failure` zurückgibt, werden der Enumerator und das Paket, das den Enumerator enthält, nicht ausgeführt. Die Implementierung dieser Methode ist für jeden Enumerator spezifisch. Wenn jedoch der Enumerator auf <xref:Microsoft.SqlServer.Dts.Runtime.Variable>- oder <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>-Objekten basiert, sollten Sie Code hinzufügen, um zu überprüfen, ob diese Objekte in den Auflistungen, die der Methode bereitgestellt werden, vorhanden sind.  
  
 Im folgenden Codebeispiel wird die Implementierung von <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.Validate%2A> gezeigt, die nach einer in einer Eigenschaft des Enumerators angegebenen Variablen sucht.  
  
```csharp  
private string variableNameValue;  
  
public string VariableName  
{  
    get{ return this.variableNameValue; }  
    set{ this.variableNameValue = value; }  
}  
  
public override DTSExecResult Validate(Connections connections, VariableDispenser variableDispenser, IDTSInfoEvents infoEvents, IDTSLogging log)  
{  
    if (!variableDispenser.Contains(this.variableNameValue))  
    {  
        infoEvents.FireError(0, "MyEnumerator", "The Variable " + this.variableNameValue + " does not exist in the collection.", "", 0);  
            return DTSExecResult.Failure;  
    }  
    return DTSExecResult.Success;  
}  
```  
  
```vb  
Private variableNameValue As String  
  
Public Property VariableName() As String  
    Get   
         Return Me.variableNameValue  
    End Get  
    Set (ByVal Value As String)   
         Me.variableNameValue = value  
    End Set  
End Property  
  
Public Overrides Function Validate(ByVal connections As Connections, ByVal variableDispenser As VariableDispenser, ByVal infoEvents As IDTSInfoEvents, ByVal log As IDTSLogging) As DTSExecResult  
    If Not variableDispenser.Contains(Me.variableNameValue) Then  
        infoEvents.FireError(0, "MyEnumerator", "The Variable " + Me.variableNameValue + " does not exist in the collection.", "", 0)  
            Return DTSExecResult.Failure  
    End If  
    Return DTSExecResult.Success  
End Function  
```  
  
## <a name="returning-the-collection"></a>Zurückgeben der Auflistung  
 Während der Ausführung ruft der <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop>-Container die <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A>-Methode des benutzerdefinierten Enumerators auf. In dieser Methode erstellt der Enumerator seine Auflistung von Elementen und füllt sie auf und gibt dann die Auflistung zurück. <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> führt dann eine Iteration für die Elemente in der Auflistung durch und führt die Ablaufsteuerung für jedes Element in der Auflistung durch.  
  
 Im folgenden Beispiel wird eine Implementierung von <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> gezeigt, wobei ein Array zufälliger ganzer Zahlen zurückgegeben wird.  
  
```csharp  
public override object GetEnumerator()  
{  
    ArrayList numbers = new ArrayList();  
  
    Random randomNumber = new Random(DateTime.Now);  
  
    for( int x=0; x < 100; x++ )  
        numbers.Add( randomNumber.Next());  
  
    return numbers;  
}  
```  
  
```vb  
Public Overrides Function GetEnumerator() As Object  
    Dim numbers As ArrayList =  New ArrayList()   
  
    Dim randomNumber As Random =  New Random(DateTime.Now)   
  
        Dim x As Integer  
        For  x = 0 To  100- 1  Step  x + 1  
        numbers.Add(randomNumber.Next())  
        Next  
  
    Return numbers  
End Function  
```  
  
![Integration Services (kleines Symbol)](../../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services**<br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines benutzerdefinierten Foreach-Enumerators](creating-a-custom-foreach-enumerator.md)   
 [Entwickeln einer Benutzeroberfläche für einen benutzerdefinierten ForEach-Enumerator](developing-a-user-interface-for-a-custom-foreach-enumerator.md)  
  
  
