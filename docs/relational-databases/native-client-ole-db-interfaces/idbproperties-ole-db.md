---
title: IDBProperties-Schnittstelle (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 2e5a4fd8-5164-495a-9986-3477aef8d8a5
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 397c292e11291caa306100c15a07bf61b16060ab
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68051085"
---
# <a name="idbproperties-ole-db"></a>IDBProperties (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Dank der OLE DB-Standardspezifikation können Anbieter VT_EMPTY für **DBPROPINFO::vValues**angeben. Von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (OLE DB) wird jedoch immer VT_EMPTY zurückgegeben, wenn Sie **IDBProperties::GetPropertyInfo** zum Abrufen von Rowseteigenschaften zusammen mit **DBPROPSET_ROWSETALL** aufrufen.  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen &#40;OLE-DB&#41;](https://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)  
  
  
