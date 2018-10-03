---
title: Verwenden von Transaktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, transactions
- transactions [SMO]
- SMO [SQL Server], transactions
ms.assetid: 399aded8-bee3-4cfb-a671-1877c7d0de9f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d9f7984be9f48a3651d5dc804faabbc0cd9625f3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48086160"
---
# <a name="using-transactions"></a>Verwenden von Transaktionen
  In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) wird die Transaktionsverarbeitung durch die Verbindung zur Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mit dem <xref:Microsoft.SqlServer.Management.Common.ServerConnection>-Objekt erreicht. Die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> Objekt verweist auf die <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> Eigenschaft der <xref:Microsoft.SqlServer.Management.Smo.Server> Objekt, wenn die Verbindung hergestellt wird. Methoden wie <xref:Microsoft.SqlServer.Management.Common.DataTransferProgressEventType.StartTransaction>, <xref:Microsoft.SqlServer.Management.Common.ServerConnection.RollBackTransaction%2A> und <xref:Microsoft.SqlServer.Management.Common.ServerConnection.CommitTransaction%2A> gehören zur <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A>-Objekteigenschaft.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von SMO-Programmen](creating-smo-programs.md)  
  
  
