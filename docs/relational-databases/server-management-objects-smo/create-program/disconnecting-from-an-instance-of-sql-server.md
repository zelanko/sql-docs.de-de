---
title: Trennen der Verbindung zu einer Instanz von SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, disconnecting
- SMO [SQL Server], disconnecting
- instances of SQL Server, disconnecting
- disconnecting [SMO]
ms.assetid: 4ca7f7eb-6b3f-4c73-ac63-88afa8570b61
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: de53acd4ef3d9feb6ed1a5026d8890f83e88d557
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "70148736"
---
# <a name="disconnecting-from-an-instance-of-sql-server"></a>Trennen der Verbindung zu einer Instanz von SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Das manuelle Schließen und Trennen der Verbindung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) ist nicht erforderlich. Verbindungen werden bei Bedarf hergestellt und geschlossen.  
  
## <a name="connection-pooling"></a>Verbindungspooling  
 Wenn die [Connect](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionmanager.connect) -Methode aufgerufen wird, wird die Verbindung nicht automatisch freigegeben. Die [Disconnect](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionmanager.disconnect) -Methode muss explizit aufgerufen werden, um die Verbindung zum Verbindungspool freizugeben. Sie können auch eine nicht in einem Pool enthaltene Verbindung anfordern. Hierzu legen Sie die [NonPooledConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionsettings.nonpooledconnection) -Eigenschaft der- <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> Eigenschaft fest, die auf das [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) -Objekt verweist.  
  
## <a name="disconnecting-from-an-instance-of-sql-server-for-rmo"></a>Trennen der Verbindung zu einer Instanz von SQL&#160;Server für RMO  
 Das Schließen von Serververbindungen beim Programmieren mit RMO funktioniert etwas anders als mit SMO.  
  
 Da die Server Verbindung für ein RMO-Objekt durch das [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) -Objekt verwaltet wird, wird dieses Objekt auch verwendet, wenn eine Verbindung mit [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] einer Instanz von hergestellt wird, wenn Sie mithilfe von RMO programmieren. Um eine Verbindung mit dem [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) -Objekt zu schließen, müssen Sie die [Disconnect](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionmanager.disconnect) -Methode des RMO-Objekts aufzurufen. Nachdem die Verbindung geschlossen wurde, können keine RMO-Objekte verwendet werden.  
  
## <a name="example"></a>Beispiel  
Zum Verwenden eines angegebenen Codebeispiels müssen Sie die Programmierumgebung, Programmiervorlage und die zu verwendende Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [Erstellen eines Visual C-&#35; SMO-Projekts in Visual Studio .net](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
 
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-basic"></a>Schließen und Trennen der Verbindung eines SMO-Objekts in Visual Basic  
 In diesem Codebeispiel wird veranschaulicht, wie Sie eine nicht in einem Pool zusammengefasste Verbindung anfordern, indem Sie die <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> [NonPooledConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionsettings.nonpooledconnection) -Eigenschaft der-Objekt Eigenschaft festlegen.  
  
```VBNET
Dim srv As Server
srv = New Server
'Disable automatic disconnection.
srv.ConnectionContext.AutoDisconnectMode = AutoDisconnectMode.NoAutoDisconnect
'Connect to the local, default instance of SQL Server.
srv.ConnectionContext.Connect()
'The actual connection is made when a property is retrieved.
Console.WriteLine(srv.Information.Version)
'Disconnect explicitly.
srv.ConnectionContext.Disconnect()
```
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-c"></a>Schließen und Trennen der Verbindung eines SMO-Objekts in Visual C#  
 In diesem Codebeispiel wird veranschaulicht, wie Sie eine nicht in einem Pool zusammengefasste Verbindung anfordern, indem Sie die <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> [NonPooledConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionsettings.nonpooledconnection) -Eigenschaft der-Objekt Eigenschaft festlegen.  
  
```csharp  
{   
Server srv;   
srv = new Server();   
//Disable automatic disconnection.   
srv.ConnectionContext.AutoDisconnectMode = AutoDisconnectMode.NoAutoDisconnect;   
//Connect to the local, default instance of SQL Server.   
srv.ConnectionContext.Connect();   
//The actual connection is made when a property is retrieved.   
Console.WriteLine(srv.Information.Version);   
//Disconnect explicitly.   
srv.ConnectionContext.Disconnect();  
}  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.SqlServer.Management.Smo.Server>   
 [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx)  
  
  
