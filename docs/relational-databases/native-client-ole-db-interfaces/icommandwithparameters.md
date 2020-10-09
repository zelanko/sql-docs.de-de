---
description: ICommandWithParameters (Native Client OLE DB-Anbieter)
title: ICommandWithParameters (Native Client OLE DB-Anbieter) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 66644c70-def7-46d8-8c47-b883292a0288
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0ecf207fa32d103042fd5888f3f416cffd4563bd
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91868313"
---
# <a name="icommandwithparameters-native-client-ole-db-provider"></a>ICommandWithParameters (Native Client OLE DB-Anbieter)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Verbesserungen an der Datenbank-Engine ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ermöglichen das Abrufen genauerer Beschreibungen der erwarteten Ergebnisse durch ICommandWithParameters::GetParameterInfo. Diese genaueren Ergebnisse unterscheiden sich möglicherweise von den Werten, die von CommandWithParameters::GetParameterInfo in früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zurückgegeben wurden. Weitere Informationen finden Sie unter [Metadatenermittlung](../../relational-databases/native-client/features/metadata-discovery.md).  
  
 Ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] muss beim Aufrufen von ICommandWithParameters::SetParameterInfo der an den Parameter *pwszName* übergebene Wert ein gültiger Bezeichner sein. Weitere Informationen finden Sie unter [Datenbankbezeichner](../../relational-databases/databases/database-identifiers.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schnittstellen &#40;OLE DB&#41;](./sql-server-native-client-ole-db-interfaces.md)  
  
