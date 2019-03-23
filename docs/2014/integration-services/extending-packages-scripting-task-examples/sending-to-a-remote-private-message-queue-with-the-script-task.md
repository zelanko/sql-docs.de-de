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
manager: craigg
ms.openlocfilehash: e4791e826adccb925241b02312900ea524f228e0
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58374511"
---
# <a name="sending-to-a-remote-private-message-queue-with-the-script-task"></a>Senden mit dem Skripttask an eine private Remotemeldungswarteschlange
  Message Queuing (auch als MSMQ bezeichnet) bietet Entwicklern eine einfache Möglichkeit, durch das Senden und Empfangen von Meldungen schnell und zuverlässig mit Anwendungshilfsprogrammen zu kommunizieren. Meldungswarteschlangen können sich auf einem lokalen oder einem Remotecomputer befinden und öffentlich oder privat sein. In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] unterstützen der MSMQ-Verbindungs-Manager und der Task Nachrichtenwarteschlange das Senden an eine private Warteschlange auf einem Remotecomputer nicht. Mit dem Skripttask können Meldungen jedoch ganz einfach an eine private Remotewarteschlange gesendet werden.  
  
> [!NOTE]  
>  Wenn Sie einen Task erstellen möchten, den Sie einfacher in mehreren Paketen wiederverwenden können, empfiehlt es sich, den Code in diesem Skripttaskbeispiel als Ausgangspunkt für einen benutzerdefinierten Task zu verwenden. Weitere Informationen finden Sie unter [Entwickeln eines benutzerdefinierten Tasks](../extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="description"></a>Description  
 Im folgenden Beispiel werden ein vorhandener MSMQ-Verbindungs-Manager sowie Objekte und Methoden des System.Messaging-Namespace verwendet, um in einer Paketvariablen enthaltenen Text an eine private Remotemeldungswarteschlange zu senden. Der Aufruf der m:Microsoft.SqlServer.DTS.managedconnections.msmqconn.AcquireConnection(System.Object)-Methode des MSMQ-Verbindungs-Managers gibt ein **MessageQueue** Objekt, dessen `Send` Methode erreicht wird dies Aufgabe.  
  
#### <a name="to-configure-this-script-task-example"></a>So konfigurieren Sie dieses Skripttaskbeispiel  
  
1.  Erstellen Sie einen MSMQ-Verbindungs-Manager mit dem Standardnamen. Geben Sie den Pfad einer gültigen privaten Remotewarteschlange im folgenden Format an:  
  
    ```  
    FORMATNAME:DIRECT=OS:<computername>\private$\<queuename>  
    ```  
  
2.  Erstellen Sie eine [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Variable mit dem Namen **MessageText** des Typs `String` auf den Meldungstext an das Skript übergeben. Geben Sie eine Standardmeldung als Wert der Variablen ein.  
  
3.  Fügen Sie der Entwurfsoberfläche einen Skripttask hinzu, und bearbeiten Sie ihn. Um die Variable im Skript verfügbar zu machen, fügen Sie die `MessageText`-Variable im **Scripttask-Editor** auf der Registerkarte **Skript** der **ReadOnlyVariables**-Eigenschaft hinzu.  
  
4.  Klicken Sie auf **Skript bearbeiten**, um den [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications-Skript-Editor (VSTA) zu öffnen.  
  
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
  
![Integration Services (kleines Symbol)](../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services**<br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Nachrichtenwarteschlange (Task)](../control-flow/message-queue-task.md)  
  
  
