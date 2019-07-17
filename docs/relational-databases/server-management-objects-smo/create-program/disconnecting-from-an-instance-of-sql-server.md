---
title: Trennen von einer Instanz von SQLServer | Microsoft-Dokumentation
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
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 68b2dcc56e52ca35359e8af5f4c829a0be1ed6f0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68126733"
---
# <a name="disconnecting-from-an-instance-of-sql-server"></a>Trennen der Verbindung zu einer Instanz von SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Das manuelle Schließen und Trennen der Verbindung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) ist nicht erforderlich. Verbindungen werden bei Bedarf hergestellt und geschlossen.  
  
## <a name="connection-pooling"></a>Verbindungspooling  
 Wenn die [Connect](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionmanager.connect) -Methode aufgerufen wird, die Verbindung nicht automatisch freigegeben. Die [trennen](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionmanager.disconnect) -Methode muss explizit aufgerufen werden, um die Verbindung zum Verbindungspool freizugeben. Sie können auch eine nicht in einem Pool enthaltene Verbindung anfordern. Diesem Zweck legen die [NonPooledConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionsettings.nonpooledconnection) Eigenschaft der <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> -Eigenschaft, verweist der [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) Objekt.  
  
## <a name="disconnecting-from-an-instance-of-sql-server-for-rmo"></a>Trennen der Verbindung zu einer Instanz von SQL&#160;Server für RMO  
 Das Schließen von Serververbindungen beim Programmieren mit RMO funktioniert etwas anders als mit SMO.  
  
 Da die Serververbindung für ein RMO-Objekt, durch beibehalten wird die [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) Objekt ist, wird dieses Objekt wird auch verwendet werden, beim Trennen von einer Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] beim Programmieren mit RMO. Schließen Sie eine Verbindung mit der [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) Objekt, rufen Sie die [trennen](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionmanager.disconnect) -Methode des RMO-Objekts. Nachdem die Verbindung geschlossen wurde, können keine RMO-Objekte verwendet werden.  
  
## <a name="example"></a>Beispiel  
Zum Verwenden eines angegebenen Codebeispiels müssen Sie die Programmierumgebung, Programmiervorlage und die zu verwendende Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [Erstellen eines Visual C&#35; SMO-Projekts in Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
 
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-basic"></a>Schließen und Trennen der Verbindung eines SMO-Objekts in Visual Basic  
 Dieses Codebeispiel zeigt, wie Sie eine Verbindung ohne Pooling durch Festlegen von Anfordern der [NonPooledConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionsettings.nonpooledconnection) Eigenschaft der <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> Objekteigenschaft.  
  
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
 Dieses Codebeispiel zeigt, wie Sie eine Verbindung ohne Pooling durch Festlegen von Anfordern der [NonPooledConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionsettings.nonpooledconnection) Eigenschaft der <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> Objekteigenschaft.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.SqlServer.Management.Smo.Server>   
 [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx)  
  
  
