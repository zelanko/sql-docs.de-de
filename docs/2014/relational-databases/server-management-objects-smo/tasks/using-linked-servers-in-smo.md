---
title: Verwenden von Verbindungsservern in SMO | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- linked servers [SQL Server], SMO
ms.assetid: 0ea8837b-2596-4df1-b065-3bb717c9f22c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8cdbbe3b44b2e3e6754f1f6c4dd084bec0032051
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48213980"
---
# <a name="using-linked-servers-in-smo"></a>Verwenden von Verbindungsservern in SMO
  Ein Verbindungsserver stellt eine OLE DB-Datenquelle auf einem Remoteserver dar. Remote-OLE DB-Datenquellen sind verknüpft, mit der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mithilfe der <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> Objekt.  
  
 Remote-Datenbankserver können verknüpft werden, um die aktuelle Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mithilfe eines OLE DB-Anbieters. In SMO werden Verbindungsserver durch dargestellt die <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> Objekt. Die <xref:Microsoft.SqlServer.Management.Smo.LinkedServer.LinkedServerLogins%2A> -Eigenschaft verweist auf eine Auflistung von <xref:Microsoft.SqlServer.Management.Smo.LinkedServerLogin> Objekte. Diese speichern die Anmeldeinformationen, die erforderlich sind, um eine Verbindung mit dem Verbindungsserver herzustellen.  
  
## <a name="ole-db-providers"></a>OLE DB-Anbieter  
 In SMO werden installierte OLE-DB-Anbieter durch eine Auflistung von <xref:Microsoft.SqlServer.Management.Smo.OleDbProviderSettings>-Objekten dargestellt.  
  
## <a name="example"></a>Beispiel  
 Für das folgende Codebeispiel müssen Sie die Programmierungsumgebung, die Programmiervorlage und die Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [erstellen Sie eine Visual Basic-SMO-Projekts in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) und [Erstellen eines Visual C&#35; SMO-Projekts in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-visual-basic"></a>Erstellen eines Links zu einem OLE DB-Anbieterserver in Visual Basic  
 Im Codebeispiel wird veranschaulicht, wie Sie eine Verknüpfung zum Erstellen einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB, heterogene Datenquelle mithilfe der <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> Objekt. Durch Angabe [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Daten erfolgt als der Name des Produkts, auf dem Verbindungsserver mithilfe der [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client OLE DB-Anbieter die ist der offizielle OLE DB-Anbieter für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBLinkedServers1](SMO How to#SMO_VBLinkedServers1)]  -->  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-visual-c"></a>Erstellen eines Links zu einem OLE DB-Anbieterserver in Visual C#  
 Im Codebeispiel wird veranschaulicht, wie Sie eine Verknüpfung zum Erstellen einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB, heterogene Datenquelle mithilfe der <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> Objekt. Durch Angabe [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Daten erfolgt als der Name des Produkts, auf dem Verbindungsserver mithilfe der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client OLE DB-Anbieter die ist der offizielle OLE DB-Anbieter für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```  
//Connect to the local, default instance of SQL Server.   
{   
   Server srv = new Server();   
   //Create a linked server.   
   LinkedServer lsrv = default(LinkedServer);   
   lsrv = new LinkedServer(srv, "OLEDBSRV");   
   //When the product name is SQL Server the remaining properties are   
   //not required to be set.   
   lsrv.ProductName = "SQL Server";   
   lsrv.Create();   
}   
```  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-powershell"></a>Erstellen eines Links zu einem OLE DB-Anbieterserver in PowerShell  
 Im Codebeispiel wird veranschaulicht, wie Sie eine Verknüpfung zum Erstellen einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB, heterogene Datenquelle mithilfe der <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> Objekt. Durch Angabe [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Daten erfolgt als der Name des Produkts, auf dem Verbindungsserver mithilfe der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client OLE DB-Anbieter die ist der offizielle OLE DB-Anbieter für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```  
#Get a server object which corresponds to the default instance  
$svr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Create a linked server object which corresponds to an OLEDB type of SQL server product  
$lsvr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.LinkedServer -argumentlist $svr,"OLEDBSRV"  
  
#When the product name is SQL Server the remaining properties are not required to be set.   
$lsvr.ProductName = "SQL Server"  
  
#Create the Database Object  
$lsvr.Create()   
```  
  
  
