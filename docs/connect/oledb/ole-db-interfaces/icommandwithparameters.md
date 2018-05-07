---
title: ICommandWithParameters | Microsoft Docs
description: ICommandWithParameters-Schnittstelle
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 52f14f27b313db701108f537b126fa9321fab971
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="icommandwithparameters"></a>ICommandWithParameters
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Verbesserungen am Anfang des Datenbank-Engine mit [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ICommandWithParameters:: GetParameterInfo genauere Beschreibungen der erwarteten Ergebnisse abrufen können. Diese genaueren Ergebnisse unterscheidet sich möglicherweise von der Rückgabewerte CommandWithParameters::GetParameterInfo in früheren Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter [Metadatenermittlung](../../oledb/features/metadata-discovery.md).  
  
 Ab [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], beim Aufrufen von ICommandWithParameters:: SetParameterInfo, der an übergebene Wert den *PwszName* Parameter muss ein gültiger Bezeichner sein. Weitere Informationen finden Sie unter [Datenbankbezeichner](../../../relational-databases/databases/database-identifiers.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen & #40; OLE DB & #41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md) 
  
  
