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
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: eaa6406e04eddbba012cfb61d6ae82a73b7f30bb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "70148671"
---
# <a name="using-transactions"></a>Verwenden von Transaktionen
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) wird die Transaktionsverarbeitung durch die Verbindung zur Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mit dem <xref:Microsoft.SqlServer.Management.Common.ServerConnection>-Objekt erreicht. Auf <xref:Microsoft.SqlServer.Management.Common.ServerConnection> das-Objekt wird von <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> der-Eigenschaft <xref:Microsoft.SqlServer.Management.Smo.Server> des-Objekts verwiesen, wenn die Verbindung hergestellt wird. Methoden wie <xref:Microsoft.SqlServer.Management.Common.DataTransferProgressEventType.StartTransaction>, <xref:Microsoft.SqlServer.Management.Common.ServerConnection.RollBackTransaction%2A> und <xref:Microsoft.SqlServer.Management.Common.ServerConnection.CommitTransaction%2A> gehören zur <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A>-Objekteigenschaft.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von SMO-Programmen](../../../relational-databases/server-management-objects-smo/create-program/creating-smo-programs.md)  
  
  
