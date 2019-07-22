---
title: ICommandWithParameters | Microsoft-Dokumentation
description: Schnittstelle „ICommandWithParameters“
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 205a93fe5ce57a8b4c10fffb8648a1ef4c7b6506
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015463"
---
# <a name="icommandwithparameters"></a>ICommandWithParameters
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Verbesserungen in der Datenbank- [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Engine, beginnend mit "ICommandWithParameters:: GetParameterInfo", um genauere Beschreibungen der erwarteten Ergebnisse zu erhalten. Diese präziseren Ergebnisse können sich von den Werten unterscheiden, die von commandwithparameters:: GetParameterInfo in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]früheren Versionen von zurückgegeben wurden. Weitere Informationen finden Sie unter [metadatenermittlung](../../oledb/features/metadata-discovery.md).  
  
 Ab [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] muss beim Aufrufen von ICommandWithParameters::SetParameterInfo der an den Parameter *pwszName* übergebene Wert ein gültiger Bezeichner sein. Weitere Informationen finden Sie unter [Datenbankbezeichner](../../../relational-databases/databases/database-identifiers.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schnitt &#40;stellen OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md) 
  
  
