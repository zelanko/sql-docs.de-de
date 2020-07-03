---
title: Verwenden von Nachrichten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- messages [SMO]
ms.assetid: 4037a866-4826-4c1f-890c-e7e3658adf13
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e62b90ee9d5d3eaa15747435395510629e2e5feb
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85892424"
---
# <a name="using-messages"></a>Verwenden von Meldungen
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../../includes/applies-to-version/sql-asdb-asdbmi-asdw.md)]

  In SMO werden Systemmeldungen durch das-Objekt dargestellt, <xref:Microsoft.SqlServer.Management.Smo.SystemMessageCollection> das zum **Server** Objekt gehört. Da die Systemmeldungen nicht geändert werden können, sind **SystemMessage** -Objekteigenschaften schreibgeschützt.  
  
 Benutzerdefinierte Meldungen werden programmgesteuert vom <xref:Microsoft.SqlServer.Management.Smo.UserDefinedMessageCollection>-Objekt in SMO dargestellt. Vorhandene benutzerdefinierte Meldungen können ermittelt werden, indem man die Auflistung durchläuft. Neue benutzerdefinierte Meldungen können durch Instanziierung eines neuen **UserDefinedMessage** -Objekts und Festlegung der entsprechenden Eigenschaften erstellt werden.  
  
## <a name="examples"></a>Beispiele  
 Für die folgenden Codebeispiele müssen Sie die Programmierungsumgebung, die Programmiervorlage und die Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [Erstellen eines Visual C-&#35; SMO-Projekts in Visual Studio .net](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="finding-a-particular-system-message-in-visual-basic"></a>Suchen einer bestimmten Systemmeldung in Visual Basic  
 Das Codebeispiel zeigt, wie eine Systemmeldung über die ID-Nummer identifiziert und die Meldung angezeigt wird.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Reference an existing system message using the ItemByIdAndLanguage method.
Dim msg As SystemMessage
msg = srv.SystemMessages.ItemByIdAndLanguage(14126, "us_english")
'Display the message ID and  text.
Console.WriteLine(msg.ID.ToString + " " + msg.Text)
```
  
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
$srv = get-item default  
  
#Get the message 14126 in US English and display it  
$msg = $srv.SystemMessages.ItemByIdAndLanguage(14126, "us_english")  
$msg.ID.ToString() + " "+ $msg.Text  
```  
  
## <a name="adding-a-new-user-defined-message-in-visual-basic"></a>Hinzufügen einer neuen benutzerdefinierten Meldung in Visual Basic  
 Das Codebeispiel zeigt, wie eine benutzerdefinierte Meldung mit einer ID größer als 50.000 erstellt wird.  
  
```VBNET  
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
  
$udm = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedMessage -argumentlist `  
$srv, 50030, "us_english", 16, "Test message"  
$udm.Create()  
$msg = $srv.UserDefinedMessages.ItemByIdAndLanguage(50030, "us_english");  
$msg  
```  
  
  
