---
title: Verwenden von Nachrichten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- messages [SMO]
ms.assetid: 4037a866-4826-4c1f-890c-e7e3658adf13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 43ff94bf10dee2bda0a61b573b87621fa5d3256b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "72781800"
---
# <a name="using-messages"></a>Verwenden von Meldungen
  In SMO werden Systemmeldungen durch das <xref:Microsoft.SqlServer.Management.Smo.SystemMessageCollection>-Objekt dargestellt, das zum `Server`-Objekt gehört. Da die Systemmeldungen nicht geändert werden können, sind `SystemMessage`-Objekteigenschaften schreibgeschützt.  
  
 Benutzerdefinierte Meldungen werden programmgesteuert vom <xref:Microsoft.SqlServer.Management.Smo.UserDefinedMessageCollection>-Objekt in SMO dargestellt. Vorhandene benutzerdefinierte Meldungen können ermittelt werden, indem man die Auflistung durchläuft. Neue benutzerdefinierte Meldungen können durch Instanziierung eines neuen `UserDefinedMessage`-Objekts und Festlegung der entsprechenden Eigenschaften erstellt werden.  
  
## <a name="examples"></a>Beispiele  
 Für die folgenden Codebeispiele müssen Sie die Programmierungsumgebung, die Programmiervorlage und die Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [Erstellen eines Visual Basic SMO-Projekts in Visual Studio .net](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) und [Erstellen eines Visual C&#35; SMO-Projekts in Visual Studio .net](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="finding-a-particular-system-message-in-visual-basic"></a>Suchen einer bestimmten Systemmeldung in Visual Basic  
 Das Codebeispiel zeigt, wie eine Systemmeldung über die ID-Nummer identifiziert und die Meldung angezeigt wird.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMessages1](SMO How to#SMO_VBMessages1)]  -->  
  
## <a name="finding-a-particular-system-message-in-visual-c"></a>Suchen einer bestimmten Systemmeldung in Visual C#  
 Das Codebeispiel zeigt, wie eine Systemmeldung über die ID-Nummer identifiziert und die Meldung angezeigt wird.  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
            //Reference an existing system message using the   
            //ItemByIdAndLanguage method.   
            SystemMessage msg = default(SystemMessage);  
            msg = srv.SystemMessages.ItemByIdAndLanguage(14126, "us_english");  
            //Display the message ID and text.   
            Console.WriteLine(msg.ID.ToString() + " " + msg.Text);  
        }  
```  
  
## <a name="finding-a-particular-system-message-in-powershell"></a>Suchen einer bestimmten Systemmeldung in PowerShell  
 Das Codebeispiel zeigt, wie eine Systemmeldung über die ID-Nummer identifiziert und die Meldung angezeigt wird.  
  
```powershell
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = Get-Item default  
  
#Get the message 14126 in US English and display it  
$msg = $srv.SystemMessages.ItemByIdAndLanguage(14126, "us_english")  
$msg.ID.ToString() + " "+ $msg.Text  
```  
  
## <a name="adding-a-new-user-defined-message-in-visual-basic"></a>Hinzufügen einer neuen benutzerdefinierten Meldung in Visual Basic  
 Das Codebeispiel zeigt, wie eine benutzerdefinierte Meldung mit einer ID größer als 50.000 erstellt wird.  
  
```vb
Dim mysrv As Server  
mysrv = New Server  
Dim udm As UserDefinedMessage  
udm = New UserDefinedMessage(mysrv, 50003, "us_english", 16, "Test message")  
udm.Create()  
```  
  
## <a name="adding-a-new-user-defined-message-in-visual-c"></a>Hinzufügen einer neuen benutzerdefinierten Meldung in Visual C#  
 Das Codebeispiel zeigt, wie eine benutzerdefinierte Meldung mit einer ID größer als 50.000 erstellt wird.  
  
```csharp
{
            Server mysrv = new Server();  
  
            UserDefinedMessage udm = new UserDefinedMessage(mysrv, 50030, "us_english",16, "Test message");  
            udm.Create();  
             UserDefinedMessage  msg = mysrv.UserDefinedMessages.ItemByIdAndLanguage(50030, "us_english");  
            //Display the message ID and text.   
            Console.WriteLine(msg.ID.ToString() + " " + msg.Text);  
  
        }  
```  
  
## <a name="adding-a-new-user-defined-message-in-powershell"></a>Hinzufügen einer neuen benutzerdefinierten Meldung in Visual C#
 Das Codebeispiel zeigt, wie eine benutzerdefinierte Meldung mit einer ID größer als 50.000 erstellt wird.  
  
```powershell
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Create a new message
$udm = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedMessage -ArgumentList `  
$srv, 50030, "us_english", 16, "Test message"  
$udm.Create()  
$msg = $srv.UserDefinedMessages.ItemByIdAndLanguage(50030, "us_english");  
$msg  
```  
