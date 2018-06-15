---
title: IDBProperties (OLE DB) | Microsoft Docs
description: IDBProperties-Schnittstelle (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 870a331b7ae15c84c2dc9cfb4abaa14ed57d5a42
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35304779"
---
# <a name="idbproperties-ole-db"></a>IDBProperties (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Dank der OLE DB-Standardspezifikation können Anbieter VT_EMPTY für **DBPROPINFO::vValues**angeben. Allerdings OLE DB-Treiber für SQL Server-OLE DB immer VT_EMPTY zurückgegeben beim Aufrufen von **GetPropertyInfo** mit **DBPROPSET_ROWSETALL** Rowseteigenschaften abgerufen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md) 
  
  
