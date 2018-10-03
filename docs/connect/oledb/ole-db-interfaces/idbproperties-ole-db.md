---
title: IDBProperties-Schnittstelle (OLE DB) | Microsoft-Dokumentation
description: IDBProperties-Schnittstelle (OLE DB)
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
ms.openlocfilehash: 8965d6f15798ec1bbae29e00116ecbd06717af1b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47704388"
---
# <a name="idbproperties-ole-db"></a>IDBProperties (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Dank der OLE DB-Standardspezifikation können Anbieter VT_EMPTY für **DBPROPINFO::vValues**angeben. Vom OLE DB-Treiber für SQL Server wird jedoch immer VT_EMPTY zurückgegeben, wenn Sie **IDBProperties::GetPropertyInfo** zum Abrufen von Rowseteigenschaften zusammen mit **DBPROPSET_ROWSETALL** aufrufen.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Schnittstellen &#40;OLE-DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md) 
  
  
