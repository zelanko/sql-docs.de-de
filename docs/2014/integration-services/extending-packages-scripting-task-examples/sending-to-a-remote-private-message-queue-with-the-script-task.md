---
title: Senden mit dem Skripttask an eine private Remotemeldungswarteschlange | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], remote private message queues
- Message Queue task [Integration Services]
- Script task [Integration Services], examples
ms.assetid: 636314fd-d099-45cd-8bb4-f730d0a06739
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 39ccf68bcd7a16c95fd5247c7b7a9fa7b5e63fce
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84966460"
---
# <a name="sending-to-a-remote-private-message-queue-with-the-script-task"></a>Senden mit dem Skripttask an eine private Remotemeldungswarteschlange
  Message Queuing (auch als MSMQ bezeichnet) bietet Entwicklern eine einfache Möglichkeit, durch das Senden und Empfangen von Meldungen schnell und zuverlässig mit Anwendungshilfsprogrammen zu kommunizieren. Meldungswarteschlangen können sich auf einem lokalen oder einem Remotecomputer befinden und öffentlich oder privat sein. In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] unterstützen der MSMQ-Verbindungs-Manager und der Task Nachrichtenwarteschlange das Senden an eine private Warteschlange auf einem Remotecomputer nicht. Mit dem Skripttask können Meldungen jedoch ganz einfach an eine private Remotewarteschlange gesendet werden.  
  
> [!NOTE]  
>  Wenn Sie einen Task erstellen möchten, den Sie einfacher in mehreren Paketen wiederverwenden können, empfiehlt es sich, den Code in diesem Skripttaskbeispiel als Ausgangspunkt für einen benutzerdefinierten Task zu verwenden. Weitere Informationen finden Sie unter [Entwickeln eines benutzerdefinierten Tasks](../extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="description"></a>BESCHREIBUNG  
 Im folgenden Beispiel werden ein vorhandener MSMQ-Verbindungs-Manager sowie Objekte und Methoden des System.Messaging-Namespace verwendet, um in einer Paketvariablen enthaltenen Text an eine private Remotemeldungswarteschlange zu senden. Der Aufrufe der M:Microsoft.SqlServer.DTS.ManagedConnections.MSMQConn.AcquireConnection (System. Object)-Methode des MSMQ-Verbindungs-Managers gibt ein **MessageQueue** -Objekt zurück, dessen- `Send` Methode diese Aufgabe erfüllt.  
  
#### <a name="to-configure-this-script-task-example"></a>So konfigurieren Sie dieses Skripttaskbeispiel  
  
1.  Erstellen Sie einen MSMQ-Verbindungs-Manager mit dem Standardnamen. Geben Sie den Pfad einer gültigen privaten Remotewarteschlange im folgenden Format an:  
  
    ```  
    FORMATNAME:DIRECT=OS:<computername>\private$\<queuename>  
    ```  
  
2.  Erstellen [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Sie eine Variable namens **MessageText** des Typs `String` , um den Meldungs Text an das Skript zu übergeben. Geben Sie eine Standardmeldung als Wert der Variablen ein.  
  
3.  Fügen Sie der Entwurfsoberfläche einen Skripttask hinzu, und bearbeiten Sie ihn. Um die Variable im Skript verfügbar zu machen, fügen Sie die `MessageText`-Variable im **Scripttask-Editor** auf der Registerkarte **Skript** der **ReadOnlyVariables**-Eigenschaft hinzu.  
  
4.  Klicken Sie auf **Skript bearbeiten**, um den [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Tools für Anwendungen-Skript-Editor (VSTA) zu öffnen.  
  
5.  Fügen Sie zum `System.Messaging`-Namespace einen Verweis im Skriptprojekt hinzu.  
  
6.  Ersetzen Sie den Inhalt des Skriptfensters durch den Code im folgenden Abschnitt.  
  
## <a name="code"></a>Code  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports System.Messaging  
  
Public Class ScriptMain  
  
    Public Sub Main()  
  
        Dim remotePrivateQueue As MessageQueue  
        Dim messageText As String  
  
        remotePrivateQueue = _  
            DirectCast(Dts.Connections("Message Queue Connection Manager").AcquireConnection(Dts.Transaction), _  
            MessageQueue)  
        messageText = DirectCast(Dts.Variables("MessageText").Value, String)  
        remotePrivateQueue.Send(messageText)  
  
        Dts.TaskResult = ScriptResults.Success  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Messaging;  
  
public class ScriptMain  
{  
  
    public void Main()  
        {  
  
            MessageQueue remotePrivateQueue = new MessageQueue();  
            string messageText;  
  
            remotePrivateQueue = (MessageQueue)(Dts.Connections["Message Queue Connection Manager"].AcquireConnection(Dts.Transaction) as MessageQueue);  
            messageText = (string)(Dts.Variables["MessageText"].Value);  
            remotePrivateQueue.Send(messageText);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
}  
```  
  
![Integration Services Symbol (klein)](../media/dts-16.gif "Integration Services (kleines Symbol)")immer auf**dem neuesten Stand bleiben mit Integration Services**  <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Nachrichtenwarteschlange (Task)](../control-flow/message-queue-task.md)  
  
  
