---
title: Trennen von einer Instanz von SQLServer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 7783fa93912c305403cc34ad6e52668123d164ed
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52781452"
---
# <a name="disconnecting-from-an-instance-of-sql-server"></a>Trennen der Verbindung zu einer Instanz von SQL Server
  Das manuelle Schließen und Trennen der Verbindung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) ist nicht erforderlich. Verbindungen werden bei Bedarf hergestellt und geschlossen.  
  
## <a name="connection-pooling"></a>Verbindungspooling  
 Wenn die <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A>-Methode aufgerufen wird, wird die Verbindung nicht automatisch freigegeben. Die <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A>-Methode muss explizit aufgerufen werden, um die Verbindung zum Verbindungspool freizugeben. Sie können auch eine nicht in einem Pool enthaltene Verbindung anfordern. Hierfür wird die <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A>-Eigenschaft der <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A>-Eigenschaft, die auf das <xref:Microsoft.SqlServer.Management.Common.ServerConnection>-Objekt verweist, festgelegt.  
  
## <a name="disconnecting-from-an-instance-of-sql-server-for-rmo"></a>Trennen der Verbindung zu einer Instanz von SQL&#160;Server für RMO  
 Das Schließen von Serververbindungen beim Programmieren mit RMO funktioniert etwas anders als mit SMO.  
  
 Da die Serververbindung für ein RMO-Objekt, durch beibehalten wird die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> Objekt ist, wird dieses Objekt wird auch verwendet werden, beim Trennen von einer Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] beim Programmieren mit RMO. Um mit dem <xref:Microsoft.SqlServer.Management.Common.ServerConnection>-Objekt eine Verbindung zu schließen, rufen Sie die <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A>-Methode des RMO-Objekts auf. Nachdem die Verbindung geschlossen wurde, können keine RMO-Objekte verwendet werden.  
  
## <a name="example"></a>Beispiel  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-basic"></a>Schließen und Trennen der Verbindung eines SMO-Objekts in Visual Basic  
 Dieses Codebeispiel zeigt, wie Sie eine nicht in einem Pool enthaltene Verbindung anfordern, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A>-Eigenschaft der <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A>-Objekteigenschaft festlegen.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VB4](SMO How to#SMO_VB4)]  -->  
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-c"></a>Schließen und Trennen der Verbindung eines SMO-Objekts in Visual C#  
 Dieses Codebeispiel zeigt, wie Sie eine nicht in einem Pool enthaltene Verbindung anfordern, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A>-Eigenschaft der <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A>-Objekteigenschaft festlegen.  
  
```  
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
 <xref:Microsoft.SqlServer.Management.Common.ServerConnection>  
  
  
