---
title: Auslösen und Definieren von Ereignissen in einem benutzerdefinierten Task | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SSIS events, custom
- status information [SQL Server], task events
- custom tasks [Integration Services], events
- SSIS custom tasks, events
- IDTSComponentEvents interface
- events [Integration Services], custom
- events [Integration Services], runtime
- custom events [Integration Services]
- SSIS events, runtime
- IDTSEvents interface
ms.assetid: e0898aa1-e90c-4c4e-99d4-708a76efddfd
caps.latest.revision: 52
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: a657c8d88f93355e50e69dbcffa1edda33fcfddf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36147726"
---
# <a name="raising-and-defining-events-in-a-custom-task"></a>Auslösen und Definieren von Ereignissen in einem benutzerdefinierten Task
  Die [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]-Runtime-Engine bietet eine Auflistung von Ereignissen, die Statusinformationen zu dem Fortschritt eines Tasks liefern, während der Task überprüft und ausgeführt wird. Diese Ereignisse werden durch die <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents>-Schnittstelle definiert. Sie wird Tasks als Parameter für die <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Validate%2A>-Methode und die <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Execute%2A>-Methode bereitgestellt.  
  
 Es gibt eine weitere Gruppe von Ereignissen, die in der <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents>-Schnittstelle definiert sind und von Seiten des Tasks von <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> ausgelöst werden. Der <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> löst Ereignisse aus, die vor und nach der Validierung und Ausführung auftreten, wohingegen der Task die Ereignisse auslöst, die während der Ausführung und Validierung auftreten.  
  
## <a name="creating-custom-events"></a>Erstellen von benutzerdefinierten Ereignissen  
 Entwickler von benutzerdefinierten Tasks können neue, benutzerdefinierte Ereignisse definieren, indem sie eine neue <xref:Microsoft.SqlServer.Dts.Runtime.EventInfo> in der überschriebenen Implementierung der <xref:Microsoft.SqlServer.Dts.Runtime.Task.InitializeTask%2A>-Methode erstellen. Nachdem die <xref:Microsoft.SqlServer.Dts.Runtime.EventInfo> erstellt wurde, wird sie der `EventInfos`-Auflistung mithilfe der <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos.Add%2A>-Methode hinzugefügt. Die Methodensignatur der <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos.Add%2A>-Methode lautet wie folgt:  
  
 `public void Add(string eventName, string description, bool allowEventHandlers, string[] parameterNames, TypeCode[] parameterTypes, string[] parameterDescriptions);`  
  
 Im folgenden Codebeispiel ist die `InitializeTask`-Methode eines benutzerdefinierten Tasks dargestellt. Es werden zwei benutzerdefinierte Ereignisse erstellt und ihre Eigenschaften festgelegt. Die neuen Ereignisse werden dann der <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos>-Auflistung hinzugefügt.  
  
 Das erste benutzerdefinierte Ereignis hat den Ereignisnamen (*eventName*) **OnBeforeIncrement** und die Beschreibung (*description* **Fires after the initial value is updated.** Der nächste Parameter, der `true`-Wert, gibt an, dass dieses Ereignis die Erstellung eines Ereignishandlercontainer zulässt, um das Ereignis zu verarbeiten. Bei dem Ereignishandler handelt es sich um einen Container für die Strukturen in Paketen und Dienste für Tasks, wie andere Container, z. B. Paketcontainer, Sequenzcontainer, For-Schleifencontainer und ForEach-Schleifencontainer. Wenn die *AllowEventHandlers* Parameter ist `true`, <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> Objekte für das Ereignis erstellt werden. Alle Parameter, die für das Ereignis definiert wurden, sind nun für den <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> in der Variablenauflistung des <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> verfügbar.  
  
```csharp  
public override void InitializeTask(Connections connections,  
   VariableDispenser variables, IDTSInfoEvents events,  
   IDTSLogging log, EventInfos eventInfos,  
   LogEntryInfos logEntryInfos, ObjectReferenceTracker refTracker)  
{  
    this.eventInfos = eventInfos;  
    string[] paramNames = new string[1];  
    TypeCode[] paramTypes = new TypeCode[1]{TypeCode.Int32};  
    string[] paramDescriptions = new string[1];  
  
    paramNames[0] = "InitialValue";  
    paramDescriptions[0] = "The value before it is incremented.";  
  
    this.eventInfos.Add("OnBeforeIncrement",   
      "Fires before the task increments the value.",  
      true,paramNames,paramTypes,paramDescriptions);  
    this.onBeforeIncrement = this.eventInfos["OnBeforeIncrement"];  
  
    paramDescriptions[0] = "The value after it has been incremented.";  
    this.eventInfos.Add("OnAfterIncrement",  
      "Fires after the initial value is updated.",  
      true,paramNames, paramTypes,paramDescriptions);  
    this.onAfterIncrement = this.eventInfos["OnAfterIncrement"];  
}  
```  
  
```vb  
Public Overrides Sub InitializeTask(ByVal connections As Connections, _  
ByVal variables As VariableDispenser, ByVal events As IDTSInfoEvents, _  
ByVal log As IDTSLogging, ByVal eventInfos As EventInfos, _  
ByVal logEntryInfos As LogEntryInfos, ByVal refTracker As ObjectReferenceTracker)   
  
    Dim paramNames(0) As String  
    Dim paramTypes(0) As TypeCode = {TypeCode.Int32}  
    Dim paramDescriptions(0) As String  
  
    Me.eventInfos = eventInfos  
  
    paramNames(0) = "InitialValue"  
    paramDescriptions(0) = "The value before it is incremented."  
  
    Me.eventInfos.Add("OnBeforeIncrement", _  
      "Fires before the task increments the value.", _  
      True, paramNames, paramTypes, paramDescriptions)  
    Me.onBeforeIncrement = Me.eventInfos("OnBeforeIncrement")  
  
    paramDescriptions(0) = "The value after it has been incremented."  
    Me.eventInfos.Add("OnAfterIncrement", _  
      "Fires after the initial value is updated.", True, _  
      paramNames, paramTypes, paramDescriptions)  
    Me.onAfterIncrement = Me.eventInfos("OnAfterIncrement")  
  
End Sub  
```  
  
## <a name="raising-custom-events"></a>Auslösen von benutzerdefinierten Ereignissen  
 Benutzerdefinierte Ereignisse werden erstellt, indem die <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireCustomEvent%2A>-Methode aufgerufen wird. Die folgende Codezeile löst ein benutzerdefiniertes Ereignis aus.  
  
```csharp  
componentEvents.FireCustomEvent(this.onBeforeIncrement.Name,  
   this.onBeforeIncrement.Description, ref arguments,  
   null, ref bFireOnBeforeIncrement);  
```  
  
```vb  
componentEvents.FireCustomEvent(Me.onBeforeIncrement.Name, _  
Me.onBeforeIncrement.Description, arguments, _  
Nothing,  bFireOnBeforeIncrement)  
```  
  
## <a name="sample"></a>Beispiel  
 Im folgenden Beispiel ist ein Task dargestellt, der ein benutzerdefiniertes Ereignis in der `InitializeTask`-Methode definiert, das benutzerdefinierte Ereignis der <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos>-Auflistung hinzufügt und dann das benutzerdefinierte Ereignis während der `Execute`-Methode durch Aufrufen der <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireCustomEvent%2A>-Methode auslöst.  
  
```csharp  
[DtsTask(DisplayName = "CustomEventTask")]  
    public class CustomEventTask : Task  
    {  
        public override DTSExecResult Execute(Connections connections,   
          VariableDispenser variableDispenser, IDTSComponentEvents componentEvents,  
           IDTSLogging log, object transaction)  
        {  
            bool fireAgain;  
            object[] args = new object[1] { "The value of the parameter." };  
            componentEvents.FireCustomEvent( "MyCustomEvent",   
              "Firing the custom event.", ref args,  
              "CustomEventTask" , ref fireAgain );  
            return DTSExecResult.Success;  
        }  
  
        public override void InitializeTask(Connections connections,  
          VariableDispenser variableDispenser, IDTSInfoEvents events,  
          IDTSLogging log, EventInfos eventInfos,  
          LogEntryInfos logEntryInfos, ObjectReferenceTracker refTracker)  
        {  
            string[] names = new string[1] {"Parameter1"};  
            TypeCode[] types = new TypeCode[1] {TypeCode.String};  
            string[] descriptions = new string[1] {"Parameter description." };  
  
            eventInfos.Add("MyCustomEvent",  
             "Fires when my interesting event happens.",  
             true, names, types, descriptions);  
  
        }  
   }  
```  
  
```vb  
<DtsTask(DisplayName = "CustomEventTask")> _   
    Public Class CustomEventTask  
     Inherits Task  
        Public Overrides Function Execute(ByVal connections As Connections, _  
          ByVal variableDispenser As VariableDispenser, _  
          ByVal componentEvents As IDTSComponentEvents, _  
          ByVal log As IDTSLogging, ByVal transaction As Object) _  
          As DTSExecResult  
  
            Dim fireAgain As Boolean  
            Dim args() As Object =  New Object(1) {"The value of the parameter."}  
  
            componentEvents.FireCustomEvent("MyCustomEvent", _  
              "Firing the custom event.", args, _  
              "CustomEventTask" ,  fireAgain)  
            Return DTSExecResult.Success  
        End Function  
  
        Public Overrides  Sub InitializeTask(ByVal connections As Connections, _  
          ByVal variableDispenser As VariableDispenser,  
          ByVal events As IDTSInfoEvents,  
          ByVal log As IDTSLogging, ByVal eventInfos As EventInfos, ByVal logEnTryInfos As LogEnTryInfos, ByVal refTracker As ObjectReferenceTracker)  
  
            Dim names() As String =  New String(1) {"Parameter1"}  
            Dim types() As TypeCode =  New TypeCode(1) {TypeCode.String}  
            Dim descriptions() As String =  New String(1) {"Parameter description."}  
  
            eventInfos.Add("MyCustomEvent", _  
              "Fires when my interesting event happens.", _  
              True, names, types, descriptions)  
  
        End Sub  
  
    End Class  
```  
  
![Integration Services (kleines Symbol)](../../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben Sie mit Integration Services** <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Integration Services-Ereignishandler &#40;SSIS&#41;](../../integration-services-ssis-event-handlers.md)   
 [Hinzufügen eines Ereignishandlers zu einem Paket](../../add-an-event-handler-to-a-package.md)  
  
  