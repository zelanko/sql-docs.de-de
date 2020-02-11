---
title: Verwenden von Verbindungs Servern in SMO | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- linked servers [SQL Server], SMO
ms.assetid: 0ea8837b-2596-4df1-b065-3bb717c9f22c
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c55ef4914c02aca954a15930e754194e5b3419cc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "70148390"
---
# <a name="using-linked-servers-in-smo"></a>Verwenden von Verbindungsservern in SMO
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Ein Verbindungsserver stellt eine OLE DB-Datenquelle auf einem Remoteserver dar. Remote-OLE DB-Datenquellen werden mit dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Objekt mithilfe der Instanz von <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> verknüpft.  
  
 Remote-Datenbankserver können mithilfe eines OLE DB Anbieters mit [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] der aktuellen Instanz von verknüpft werden. In SMO werden Verbindungsserver durch das <xref:Microsoft.SqlServer.Management.Smo.LinkedServer>-Objekt dargestellt. Die <xref:Microsoft.SqlServer.Management.Smo.LinkedServer.LinkedServerLogins%2A>-Eigenschaft verweist auf eine Auflistung von <xref:Microsoft.SqlServer.Management.Smo.LinkedServerLogin>-Objekten. Diese speichern die Anmeldeinformationen, die erforderlich sind, um eine Verbindung mit dem Verbindungsserver herzustellen.  
  
## <a name="ole-db-providers"></a>OLE DB-Anbieter  
 In SMO werden installierte OLE-DB-Anbieter durch eine Auflistung von <xref:Microsoft.SqlServer.Management.Smo.OleDbProviderSettings>-Objekten dargestellt.  
  
## <a name="example"></a>Beispiel  
 Für die folgenden Codebeispiele müssen Sie die Programmierungsumgebung, die Programmiervorlage und die Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [Erstellen eines Visual C-&#35; SMO-Projekts in Visual Studio .net](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
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
$lsvr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.LinkedServer -argumentlist $svr,"OLEDBSRV"  
  
#When the product name is SQL Server the remaining properties are not required to be set.   
$lsvr.ProductName = "SQL Server"  
  
#Create the Database Object  
$lsvr.Create()   
```  
  
  
