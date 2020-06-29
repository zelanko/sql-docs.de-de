---
title: Vergleich zwischen Skripttask und Skriptkomponente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], comparing to Script component
- Script component [Integration Services], comparing to Script task
ms.assetid: 4b73753a-4239-491b-b7a6-abc63ba83d2d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 134cce74fc88cc9a7358c8aa4ba8de3fb7e58c5e
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85426407"
---
# <a name="comparing-the-script-task-and-the-script-component"></a>Vergleich zwischen Skripttask und Skriptkomponente
  Der Skripttask, der im Fenster „Ablaufsteuerung“ des [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Designers zur Verfügung steht, und die Skriptkomponente im Fenster „Datenfluss“ dienen in einem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Paket völlig unterschiedlichen Zwecken. Der Task stellt ein allgemeines Ablaufsteuerungstool dar, während die Komponente als Quelle, Transformation oder Ziel im Datenfluss dient. Trotz ihres unterschiedlichen Zwecks verfügen der Skripttask und die Skriptkomponente jedoch über Gemeinsamkeiten hinsichtlich der verwendeten Codierungstools sowie der Objekte im Paket, die sie dem Entwickler bereitstellen. Die Unterschiede und Gemeinsamkeiten zu kennen, kann Ihnen dabei helfen, Task und Komponente effektiver einzusetzen.  
  
## <a name="similarities-between-the-script-task-and-the-script-component"></a>Gemeinsamkeiten zwischen Skripttask und Skriptkomponente  
 Skripttask und Skriptkomponente verfügen über folgende gemeinsame Funktionen:  
  
|Funktion|BESCHREIBUNG|  
|-------------|-----------------|  
|Zwei Entwurfszeitmodi|Bei Task und Komponente legen Sie zunächst im Editor Eigenschaften fest und wechseln anschließend in die Entwicklungsumgebung, um Code zu schreiben.|  
|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA)|Task und Komponente verwenden dieselbe VSTA IDE und unterstützen in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# geschriebenen Code.|  
|Vorkompilierte Skripts|Ab [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] werden alle Skripts vorkompiliert. In früheren Versionen konnten Sie festlegen, ob Skripts vorkompiliert werden sollten.<br /><br /> Das Skript wird in binärem Code vorkompiliert. Dies ermöglicht eine schnellere Ausführung, vergrößert jedoch das Paket.|  
|Debuggen|Beim Debuggen in der Entwurfsumgebung unterstützen der Task und die Komponente Breakpoints und die schrittweise Ausführung von Code. Weitere Informationen finden Sie unter [Codieren und Debuggen des Skript](../control-flow/script-task.md) Tasks und [codieren und Debuggen der Skript Komponente] (.. /extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md.|  
  
## <a name="differences-between-the-script-task-and-the-script-component"></a>Unterschiede zwischen Skripttask und Skriptkomponente  
 Skripttask und Skriptkomponente weisen folgende wichtige Unterschiede auf:  
  
|Funktion|Skripttask|Skriptkomponente|  
|-------------|-----------------|----------------------|  
|Ablaufsteuerung/Datenfluss|Der Skripttask wird auf der Registerkarte Ablaufsteuerung des Designers konfiguriert und außerhalb des Paketdatenflusses ausgeführt.|Die Skriptkomponente wird auf der Seite Datenfluss des Designers konfiguriert und stellt eine Quelle, Transformation oder ein Ziel im Datenflusstask dar.|  
|Zweck|Ein Skripttask kann fast jede allgemeine Aufgabe ausführen.|Sie müssen festlegen, ob Sie mit der Skriptkomponente eine Quelle, Transformation oder ein Ziel erstellen möchten.|  
|Ausführung|Ein Skripttask führt benutzerdefinierten Code an einem bestimmten Punkt im Paketworkflow aus. Er wird nur einmal ausgeführt, sofern Sie ihn nicht in einem Schleifencontainer oder Ereignishandler platzieren.|Auch eine Skriptkomponente wird einmal ausgeführt. Sie führt aber ihre Verarbeitungsroutine meist für jede Datenzeile im Datenfluss aus.|  
|Editor|Der **Skripttask-Editor** weist drei Seiten auf: **Allgemein**, **Skript** und **Ausdrücke**. Nur die `ReadOnlyVariables` Eigenschaften und und die `ReadWriteVariables` **ScriptLanguage** -Eigenschaft wirken sich direkt auf den Code aus, den Sie schreiben können.|Der **Transformations-Editor für Skripterstellung** verfügt über maximal vier Seiten: **Eingabespalten**, **Eingaben und Ausgaben**, **Skript** sowie **Verbindungs-Manager**. Die Metadaten und Eigenschaften, die Sie auf diesen Seiten konfigurieren, legen die Member der Basisklassen fest, die für Sie bei der Codierung automatisch generiert werden.|  
|Interaktion mit dem Paket|Im Code für ein Skripttask verwenden Sie die `Dts`-Eigenschaft, um auf andere Funktionen des Pakets zuzugreifen. Die `Dts`-Eigenschaft ist ein Member der `ScriptMain`-Klasse.|Im Skriptkomponentencode verwenden Sie typisierte Accessoreigenschaften für den Zugriff auf bestimmte Paketfunktionen wie Variablen und Verbindungs-Manager.<br /><br /> Die `PreExecute`-Methode kann nur auf schreibgeschützte Variablen zugreifen. Die `PostExecute`-Methode kann sowohl auf schreibgeschützte als auch auf Lese-/Schreibvariablen zugreifen.<br /><br /> Weitere Informationen zu diesen Methoden finden Sie unter [codieren und Debuggen der Skript Komponente] (.). /extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md.|  
|Verwenden von Variablen|Der Skript Task verwendet die <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> -Eigenschaft des `Dts` -Objekts, um auf Variablen zuzugreifen, die über die-und-Eigenschaften der Aufgabe verfügbar sind <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadOnlyVariables%2A> <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadWriteVariables%2A> . Beispiel:<br /><br /> **Auftraten**<br /><br /> `Dim myVar as String myVar = Dts.Variables("MyStringVariable").Value.ToString`<br /><br /> <br /><br /> **C#**<br /><br /> `string myVar; myVar = Dts.Variables["MyStringVariable"].Value.ToString();`|Die Skriptkomponente verwendet typisierte Accessoreigenschaften der automatisch generierten Basisklasse, die aus den Eigenschaften <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReadOnlyVariables%2A> und <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReadWriteVariables%2A> der Komponente erstellt werden. Beispiel:<br /><br /> **Auftraten**<br /><br /> `Dim myVar as String myVar = Me.Variables.MyStringVariable`<br /><br /> <br /><br /> **C#**<br /><br /> `string myVar; myVar = this.Variables.MyStringVariable;`|  
|Verwenden von Verbindungen|Der Skripttask nutzt die <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A>-Eigenschaft des `Dts`-Objekts, um auf im Paket definierte Verbindungs-Manager zuzugreifen. Beispiel:<br /><br /> **Auftraten**<br /><br /> `Dim myFlatFileConnection As String myFlatFileConnection = _     DirectCast(Dts.Connections("Test Flat File Connection").AcquireConnection(Dts.Transaction), _     String)`<br /><br /> <br /><br /> **C#**<br /><br /> `string myFlatFileConnection; myFlatFileConnection = (Dts.Connections["Test Flat File Connection"].AcquireConnection(Dts.Transaction) as String);`|Die Skriptkomponente verwendet typisierte Accessoreigenschaften der automatisch generierten Basisklasse, die aus der Liste von Verbindungs-Managern erstellt werden, die vom Benutzer auf der Seite Verbindungs-Manager des Editors eingegeben wurden. Beispiel:<br /><br /> **Auftraten**<br /><br /> `Dim connMgr As IDTSConnectionManager100 connMgr = Me.Connections.MyADONETConnection`<br /><br /> <br /><br /> **C#**<br /><br /> `IDTSConnectionManager100 connMgr; connMgr = this.Connections.MyADONETConnection;`|  
|Auslösen von Ereignissen|Der Skripttask verwendet die <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A>-Eigenschaft des `Dts`-Objekts, um Ereignisse auszulösen. Beispiel:<br /><br /> **Auftraten**<br /><br /> `Dts.Events.FireError(0, "Event Snippet", _     ex.Message & ControlChars.CrLf & ex.StackTrace, _     "", 0)`<br /><br /> <br /><br /> **C#**<br /><br /> `Dts.Events.FireError(0, "Event Snippet", ex.Message + "\r" + ex.StackTrace, "", 0);`|Die Skriptkomponente löst Fehler, Warnungen und Informationsmeldungen mithilfe der Methoden der <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>-Schnittstelle, die von der <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A>-Eigenschaft zurückgegeben werden, aus. Beispiel:<br /><br /> **Auftraten**<br /><br /> `Dim myMetadata as IDTSComponentMetaData100 myMetaData = Me.ComponentMetaData myMetaData.FireError(...)`|  
|Protokollierung|Der Skript Task verwendet die- <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> Methode des- `Dts` Objekts, um Informationen an aktivierte Protokoll Anbieter zu protokollieren. Beispiel:<br /><br /> **Auftraten**<br /><br /> `Dim bt(0) As Byte Dts.Log("Test Log Event", _     0, _     bt)`<br /><br /> <br /><br /> **C#**<br /><br /> `byte[] bt = new byte[0]; Dts.Log("Test Log Event", 0, bt);`|Die Skriptkomponente verwendet die <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A>-Methode der automatisch generierten Basisklasse, um Informationen bei aktivierten Protokollanbietern zu protokollieren. Beispiel:<br /><br /> **Auftraten**<br /><br /> `Dim bt(0) As Byte`<br /><br /> `Me.Log("Test Log Event", _`<br /><br /> `0, _`<br /><br /> `bt)`<br /><br /> <br /><br /> **C#**<br /><br /> `byte[] bt = new byte[0]; this.Log("Test Log Event", 0, bt);`|  
|Zurückgeben von Ergebnissen|Der Skript Task verwendet die <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> -Eigenschaft und die optionale- <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> Eigenschaft des- `Dts` Objekts, um die Laufzeit über die Ergebnisse zu benachrichtigen.|Die Skriptkomponente wird als Teil des Datenflusstasks ausgeführt und erstellt keine Ergebnisberichte mit einer dieser Eigenschaften.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweitern von Paketen mithilfe des Skripttasks](task/extending-the-package-with-the-script-task.md)   
 [Erweitern des Datenflusses mit der Skript Komponente](data-flow-script-component/extending-the-data-flow-with-the-script-component.md)   
 [Verwenden eines Skript Tasks in SQL Server Integration Services SSIS zum Herstellen einer Verbindung mit einem Webdienst](https://www.mssqltips.com/sqlservertip/4288/using-a-script-task-in-sql-server-integration-services-ssis-to-connect-to-a-web-service/)  
  
  
