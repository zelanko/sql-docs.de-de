---
title: Erstellen eines benutzerdefinierten Tasks | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- custom tasks [Integration Services], creating
ms.assetid: 42965c09-1782-4cdb-9ce1-216af4c23e0a
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 06ff2d20ee28c67fa95db4f4ef5f8f1f65862e04
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37227760"
---
# <a name="creating-a-custom-task"></a>Erstellen eines benutzerdefinierten Tasks
  Die Schritte zum Erstellen eines benutzerdefinierten Tasks ähneln denen jedes anderen benutzerdefinierten Objekts für [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]:  
  
-   Erstellen Sie eine neue Klasse, die von der Basisklasse erbt. Für einen Task ist die Basisklasse <xref:Microsoft.SqlServer.Dts.Runtime.Task>.  
  
-   Weisen Sie das Attribut zu, das den Typ des Objekts für die Klasse identifiziert. Für einen Task ist das Attribut <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute>.  
  
-   Überschreiben Sie die Implementierung der Methoden und Eigenschaften der Basisklasse. Für einen Task sind dies die Methoden <xref:Microsoft.SqlServer.Dts.Runtime.Task.Validate%2A> und <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A>.  
  
-   Entwickeln Sie optional eine individuelle Benutzeroberfläche. Für einen Task ist dazu eine Klasse erforderlich, die die <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI>-Schnittstelle implementiert.  
  
## <a name="getting-started-with-a-custom-task"></a>Erste Schritte mit einem benutzerdefinierten Task  
  
### <a name="creating-projects-and-classes"></a>Erstellen von Projekten und Klassen  
 Da alle verwalteten Tasks von der <xref:Microsoft.SqlServer.Dts.Runtime.Task>-Basisklasse abgeleitet sind, besteht der erste Schritt beim Erstellen eines benutzerdefinierten Tasks darin, in Ihrer bevorzugten verwalteten Programmiersprache ein Klassenbibliotheksprojekt anzulegen und eine Klasse zu generieren, die von der Basisklasse erbt. In dieser abgeleiteten Klasse überschreiben Sie die Methoden und Eigenschaften der Basisklasse, um die benutzerdefinierten Funktionen zu implementieren.  
  
 Erstellen Sie in der gleichen Lösung ein zweites Klassenbibliotheksprojekt für die individuelle Benutzeroberfläche. Für eine einfache Bereitstellung sollten Sie eine eigene Assembly für die Benutzeroberfläche verwenden, da Sie so den Verbindungs-Manager oder seine Benutzeroberfläche unabhängig aktualisieren und erneut bereitstellen können.  
  
 Konfigurieren Sie beide Projekte für das Signieren der Assemblys, die bei der Erstellung erzeugt werden, mit einer Schlüsseldatei mit starkem Namen.  
  
### <a name="applying-the-dtstask-attribute"></a>Zuweisen des 'DtsTask'-Attributs  
 Weisen Sie das <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute>-Attribut der Klasse zu, die Sie erstellt haben, um sie als Task zu kennzeichnen. Dieses Attribut stellt Entwurfszeitinformationen, z. B. Name, Beschreibung und Tasktyp des Tasks, bereit.  
  
 Verwenden Sie die <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.UITypeName%2A>-Eigenschaft, um den Task mit der individuellen Benutzeroberfläche zu verknüpfen. Um das für diese Eigenschaft erforderliche öffentliche Schlüsseltoken zu erhalten, können Sie **sn.exe -t** verwenden. Damit zeigen Sie das öffentliche Schlüsseltoken aus der Schlüsselpaardatei (.snk) an, die Sie für das Signieren der Benutzeroberflächenassembly verwenden möchten.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
namespace Microsoft.SSIS.Samples  
{  
  [DtsTask  
  (  
   DisplayName = "MyTask",  
   IconResource = "MyTask.MyTaskIcon.ico",  
   UITypeName = "My Custom Task," +  
   "Version=1.0.0.0," +  
   "Culture = Neutral," +  
   "PublicKeyToken = 12345abc6789de01",  
   TaskType = "PackageMaintenance",  
   TaskContact = "MyTask; company name; any other information",  
   RequiredProductLevel = DTSProductLevel.None  
   )]  
  public class MyTask : Task  
  {  
    // Your code here.  
  }  
}  
```  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
  
<DtsTask(DisplayName:="MyTask", _  
 IconResource:="MyTask.MyTaskIcon.ico", _  
 UITypeName:="My Custom Task," & _  
 "Version=1.0.0.0,Culture=Neutral," & _  
 "PublicKeyToken=12345abc6789de01", _  
 TaskType:="PackageMaintenance", _  
 TaskContact:="MyTask; company name; any other information", _  
 RequiredProductLevel:=DTSProductLevel.None)> _  
Public Class MyTask  
  Inherits Task  
  
  ' Your code here.  
  
End Class 'MyTask  
```  
  
## <a name="building-deploying-and-debugging-a-custom-task"></a>Erstellen, Bereitstellen und Debuggen eines benutzerdefinierten Tasks  
 Die Schritte zum Erstellen, Bereitstellen und Debuggen eines benutzerdefinierten Tasks in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ähneln denen für andere Typen benutzerdefinierter Objekte. Weitere Informationen finden Sie unter [Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md) (Erstellen, Bereitstellen und Debuggen von benutzerdefinierten Objekten).  
  
![Integration Services (kleines Symbol)](../../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services** <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines benutzerdefinierten Tasks](creating-a-custom-task.md)   
 [Codieren eines benutzerdefinierten Tasks](coding-a-custom-task.md)   
 [Entwickeln einer Benutzeroberfläche für einen benutzerdefinierten Task](developing-a-user-interface-for-a-custom-task.md)  
  
  
