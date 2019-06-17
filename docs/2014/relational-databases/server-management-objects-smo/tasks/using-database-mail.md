---
title: Datenbank-e-Mails mit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- e-mail [SMO]
- Database Mail [SMO]
- mail [SMO]
ms.assetid: 7605390f-b485-48cc-8d97-e364a066067b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 232ea094ac81badfe7a6ec378371b55a0b08103b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62518744"
---
# <a name="using-database-mail"></a>Verwenden von Datenbank-E-Mail
  In SMO wird das Datenbank-E-Mail-Subsystem durch das <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail>-Objekt dargestellt, auf das durch die <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A>-Eigenschaft verwiesen wird. Durch die Verwendung des SMO-<xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail>-Objekts können Sie das Datenbank-E-Mail-Subsystem konfigurieren und Profile und E-Mail-Konten verwalten. Das SMO-<xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail>-Objekt gehört zum `Server`-Objekt, d. h., der Bereich der E-Mail-Konten befindet sich auf Serverebene.  
  
## <a name="examples"></a>Beispiele  
 Zum Verwenden eines angegebenen Codebeispiels müssen Sie die Programmierumgebung, Programmiervorlage und die zu verwendende Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [erstellen Sie eine Visual Basic-SMO-Projekts in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) oder [Erstellen eines Visual C&#35; SMO-Projekts in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
 Für Programme, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datenbank-e-Mails, müssen Sie enthalten die `Imports` Anweisung, um den e-Mail-Namespace zu qualifizieren. Fügen Sie die Anweisung nach den anderen `Imports`-Anweisungen und vor jeglichen Deklarationen in der Anwendung wie folgt ein:  
  
 `Imports Microsoft.SqlServer.Management.Smo`  
  
 `Imports Microsoft.SqlServer.Management.Common`  
  
 `Imports Microsoft.SqlServer.Management.Smo.Mail`  
  
## <a name="creating-a-database-mail-account-by-using-visual-basic"></a>Erstellen eines Datenbank-E-Mail-Kontos mit Visual Basic  
 In diesem Codebeispiel wird gezeigt, wie ein E-Mail-Konto in SMO erstellt wird. Datenbank-E-Mail wird durch das <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail>-Objekt dargestellt und durch die <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A>-Eigenschaft des <xref:Microsoft.SqlServer.Management.Smo.Server>-Objekts verwiesen. SMO kann verwendet werden, um programmgesteuert Datenbank-E-Mails zu konfigurieren. Das Senden von E-Mails und die Behandlung empfangener E-Mails sind allerdings hierüber nicht möglich.  
  
 VB.NET  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMail1](SMO How to#SMO_VBMail1)]  -->  
  
## <a name="creating-a-database-mail-account-by-using-visual-c"></a>Erstellen eines Datenbank-E-Mail-Kontos mit Visual C#  
 In diesem Codebeispiel wird gezeigt, wie ein E-Mail-Konto in SMO erstellt wird. Datenbank-E-Mail wird durch das <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail>-Objekt dargestellt und durch die <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A>-Eigenschaft des <xref:Microsoft.SqlServer.Management.Smo.Server>-Objekts verwiesen. SMO kann verwendet werden, um programmgesteuert Datenbank-E-Mails zu konfigurieren. Das Senden von E-Mails und die Behandlung empfangener E-Mails sind allerdings hierüber nicht möglich.  
  
```csharp  
{  
         //Connect to the local, default instance of SQL Server.  
         Server srv = default(Server);   
           srv = new Server();   
           //Define the Database Mail service with a SqlMail object variable   
           //and reference it using the Server Mail property.   
           SqlMail sm;   
           sm = srv.Mail;   
           //Define and create a mail account by supplying the Database Mail  
           //service, name, description, display name, and email address  
           //arguments in the constructor.   
           MailAccount a = default(MailAccount);   
           a = new MailAccount(sm, "AdventureWorks2012 Administrator", "AdventureWorks2012 Automated Mailer", "Mail account for administrative e-mail.", "dba@Adventure-Works.com");   
           a.Create();    
}  
```  
  
## <a name="creating-a-database-mail-account-by-using-powershell"></a>Erstellen eines Datenbank-E-Mail-Kontos mit PowerShell  
 In diesem Codebeispiel wird gezeigt, wie ein E-Mail-Konto in SMO erstellt wird. Datenbank-E-Mail wird durch das <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail>-Objekt dargestellt und durch die <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A>-Eigenschaft des <xref:Microsoft.SqlServer.Management.Smo.Server>-Objekts verwiesen. SMO kann verwendet werden, um programmgesteuert Datenbank-E-Mails zu konfigurieren. Das Senden von E-Mails und die Behandlung empfangener E-Mails sind allerdings hierüber nicht möglich.  
  
 PowerShell  
  
```powershell  
#Connect to the local, default instance of SQL Server.  
  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Define the Database Mail; reference it using the Server Mail property.  
$sm = $srv.Mail  
  
#Define and create a mail account by supplying the Database Mail service,  
#name, description, display name, and email address arguments in the constructor.  
$a = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Mail.MailAccount -argumentlist $sm, `  
"Adventure Works Administrator", "Adventure Works Automated Mailer",`  
 "Mail account for administrative e-mail.", "dba@Adventure-Works.com"  
$a.Create()  
```  
  
  
