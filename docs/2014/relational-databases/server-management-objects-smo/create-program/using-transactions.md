---
title: Verwenden von Transaktionen | Microsoft Docs
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
- SQL Server Management Objects, transactions
- transactions [SMO]
- SMO [SQL Server], transactions
ms.assetid: 399aded8-bee3-4cfb-a671-1877c7d0de9f
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2c132ac199fb6af9e0349c463d5b30954acbf8bd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151080"
---
# <a name="using-transactions"></a>Verwenden von Transaktionen
  In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) wird die Transaktionsverarbeitung durch die Verbindung zur Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mit dem <xref:Microsoft.SqlServer.Management.Common.ServerConnection>-Objekt erreicht. Die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> Objekt verweist auf die <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> Eigenschaft von der <xref:Microsoft.SqlServer.Management.Smo.Server> Objekt, wenn die Verbindung hergestellt wird. Methoden wie <xref:Microsoft.SqlServer.Management.Common.DataTransferProgressEventType.StartTransaction>, <xref:Microsoft.SqlServer.Management.Common.ServerConnection.RollBackTransaction%2A> und <xref:Microsoft.SqlServer.Management.Common.ServerConnection.CommitTransaction%2A> gehören zur <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A>-Objekteigenschaft.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von SMO-Programmen](creating-smo-programs.md)  
  
  