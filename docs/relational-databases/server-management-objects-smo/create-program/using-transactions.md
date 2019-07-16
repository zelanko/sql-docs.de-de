---
title: Verwenden von Transaktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, transactions
- transactions [SMO]
- SMO [SQL Server], transactions
ms.assetid: 399aded8-bee3-4cfb-a671-1877c7d0de9f
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 53f5813aac141c82f87f3bec5164e5d617af6cce
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68098200"
---
# <a name="using-transactions"></a>Verwenden von Transaktionen
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) wird die Transaktionsverarbeitung durch die Verbindung zur Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mit dem <xref:Microsoft.SqlServer.Management.Common.ServerConnection>-Objekt erreicht. Die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> Objekt verweist auf die <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> Eigenschaft der <xref:Microsoft.SqlServer.Management.Smo.Server> Objekt, wenn die Verbindung hergestellt wird. Methoden wie <xref:Microsoft.SqlServer.Management.Common.DataTransferProgressEventType.StartTransaction>, <xref:Microsoft.SqlServer.Management.Common.ServerConnection.RollBackTransaction%2A> und <xref:Microsoft.SqlServer.Management.Common.ServerConnection.CommitTransaction%2A> gehören zur <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A>-Objekteigenschaft.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von SMO-Programmen](../../../relational-databases/server-management-objects-smo/create-program/creating-smo-programs.md)  
  
  
