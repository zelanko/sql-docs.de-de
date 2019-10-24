---
title: Verwenden von Verbindungs Servern in SMO | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- linked servers [SQL Server], SMO
ms.assetid: 0ea8837b-2596-4df1-b065-3bb717c9f22c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0f62efaa1550ea0b9e68ce4914e4852612d53f48
ms.sourcegitcommit: a165052c789a327a3a7202872669ce039bd9e495
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72781997"
---
# <a name="using-linked-servers-in-smo"></a>Verwenden von Verbindungsservern in SMO
  Ein Verbindungsserver stellt eine OLE DB-Datenquelle auf einem Remoteserver dar. Remote-OLE DB-Datenquellen werden mit dem <xref:Microsoft.SqlServer.Management.Smo.LinkedServer>-Objekt mithilfe der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verknüpft.  
  
 Remote-Datenbankserver können über einen OLE DB-Anbieter mit der aktuellen Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verknüpft werden. In SMO werden Verbindungsserver durch das <xref:Microsoft.SqlServer.Management.Smo.LinkedServer>-Objekt dargestellt. Die <xref:Microsoft.SqlServer.Management.Smo.LinkedServer.LinkedServerLogins%2A>-Eigenschaft verweist auf eine Auflistung von <xref:Microsoft.SqlServer.Management.Smo.LinkedServerLogin>-Objekten. Diese speichern die Anmeldeinformationen, die erforderlich sind, um eine Verbindung mit dem Verbindungsserver herzustellen.  
  
## <a name="ole-db-providers"></a>OLE DB-Anbieter  
 In SMO werden installierte OLE-DB-Anbieter durch eine Auflistung von <xref:Microsoft.SqlServer.Management.Smo.OleDbProviderSettings>-Objekten dargestellt.  
  
## <a name="example"></a>Beispiel  
 Für das folgende Codebeispiel müssen Sie die Programmierungsumgebung, die Programmiervorlage und die Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [Erstellen eines Visual Basic SMO-Projekts in Visual Studio .net](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) und [Erstellen eines Visual&#35; C SMO-Projekts in Visual Studio .net](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-visual-basic"></a>Erstellen eines Links zu einem OLE DB-Anbieterserver in Visual Basic  
 Im folgenden Codebeispiel wird veranschaulicht, wie ein Link zu einer heterogenen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB-Datenquelle mithilfe des <xref:Microsoft.SqlServer.Management.Smo.LinkedServer>-Objekts erstellt wird. Durch die Angabe von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] als Produktname wird über den [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client OLE DB-Anbieter auf die Daten auf einem Verbindungsserver zugegriffen. Dies ist der offizielle OLE DB-Anbieter für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBLinkedServers1](SMO How to#SMO_VBLinkedServers1)]  -->  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-visual-c"></a>Erstellen eines Links zu einem OLE DB-Anbieterserver in Visual C#  
 Im folgenden Codebeispiel wird veranschaulicht, wie ein Link zu einer heterogenen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB-Datenquelle mithilfe des <xref:Microsoft.SqlServer.Management.Smo.LinkedServer>-Objekts erstellt wird. Durch die Angabe von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] als Produktname wird über den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client OLE DB-Anbieter auf die Daten auf einem Verbindungsserver zugegriffen. Dies ist der offizielle OLE DB-Anbieter für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```csharp
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
 Im folgenden Codebeispiel wird veranschaulicht, wie ein Link zu einer heterogenen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB-Datenquelle mithilfe des <xref:Microsoft.SqlServer.Management.Smo.LinkedServer>-Objekts erstellt wird. Durch die Angabe von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] als Produktname wird über den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client OLE DB-Anbieter auf die Daten auf einem Verbindungsserver zugegriffen. Dies ist der offizielle OLE DB-Anbieter für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```powershell
#Get a server object which corresponds to the default instance  
$svr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Create a linked server object which corresponds to an OLEDB type of SQL server product  
$lsvr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.LinkedServer -ArgumentList $svr,"OLEDBSRV"  
  
#When the product name is SQL Server the remaining properties are not required to be set.
$lsvr.ProductName = "SQL Server"
  
#Create the Database Object  
$lsvr.Create()
```  
