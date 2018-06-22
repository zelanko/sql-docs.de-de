---
title: Trennen von einer Instanz von SQLServer | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, disconnecting
- SMO [SQL Server], disconnecting
- instances of SQL Server, disconnecting
- disconnecting [SMO]
ms.assetid: 4ca7f7eb-6b3f-4c73-ac63-88afa8570b61
caps.latest.revision: 43
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1f2ce4ae7ce42df42be9b6bc68c3d13acf949dba
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149575"
---
# <a name="disconnecting-from-an-instance-of-sql-server"></a>Trennen der Verbindung zu einer Instanz von SQL Server
  Manuelle Schließen und Trennen der Verbindung [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) ist nicht erforderlich. Verbindungen werden bei Bedarf hergestellt und geschlossen.  
  
## <a name="connection-pooling"></a>Verbindungspooling  
 Wenn die <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> -Methode aufgerufen wird, die Verbindung nicht automatisch freigegeben. Die <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A>-Methode muss explizit aufgerufen werden, um die Verbindung zum Verbindungspool freizugeben. Sie können auch eine nicht in einem Pool enthaltene Verbindung anfordern. Hierfür wird die <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A>-Eigenschaft der <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A>-Eigenschaft, die auf das <xref:Microsoft.SqlServer.Management.Common.ServerConnection>-Objekt verweist, festgelegt.  
  
## <a name="disconnecting-from-an-instance-of-sql-server-for-rmo"></a>Trennen der Verbindung zu einer Instanz von SQL&#160;Server für RMO  
 Das Schließen von Serververbindungen beim Programmieren mit RMO funktioniert etwas anders als mit SMO.  
  
 Da durch die Serververbindung für ein RMO-Objekt beibehalten wird die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Objekt, dieses Objekt wird auch verwendet, wenn Trennen von einer Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] beim Programmieren mit RMO erfolgt. Schließen Sie eine Verbindung mit der <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Objekt, rufen Sie die <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> -Methode des RMO-Objekts. Nachdem die Verbindung geschlossen wurde, können keine RMO-Objekte verwendet werden.  
  
## <a name="example"></a>Beispiel  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-basic"></a>Schließen und Trennen der Verbindung eines SMO-Objekts in Visual Basic  
 Dieses Codebeispiel zeigt, wie eine Pool-Verbindung angefordert wird durch Festlegen der <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> Eigenschaft von der <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> -Objekteigenschaft.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VB4](SMO How to#SMO_VB4)]  -->  
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-c"></a>Schließen und Trennen der Verbindung eines SMO-Objekts in Visual C#  
 Dieses Codebeispiel zeigt, wie eine Pool-Verbindung angefordert wird durch Festlegen der <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> Eigenschaft von der <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> -Objekteigenschaft.  
  
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
  
  