---
title: ICommandWithParameters | Microsoft-Dokumentation
description: Schnittstelle „ICommandWithParameters“
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: a998292f4d1c03485dc75eee02cefa437dc1fe36
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47600048"
---
# <a name="icommandwithparameters"></a>ICommandWithParameters
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Verbesserungen in der Datenbank-Engine ab mit [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ICommandWithParameters:: GetParameterInfo, genauere Beschreibungen der erwarteten Ergebnisse abrufen können. Diese genaueren Ergebnisse unterscheiden sich möglicherweise aus den Werten, die vom CommandWithParameters::GetParameterInfo in früheren Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter [Metadatenermittlung](../../oledb/features/metadata-discovery.md).  
  
 Ab [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] muss beim Aufrufen von ICommandWithParameters::SetParameterInfo der an den Parameter *pwszName* übergebene Wert ein gültiger Bezeichner sein. Weitere Informationen finden Sie unter [Datenbankbezeichner](../../../relational-databases/databases/database-identifiers.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Schnittstellen &#40;OLE-DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md) 
  
  
