---
description: AsBinaryZM (geometry-Datentyp)
title: AsBinaryZM (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- AsBinaryZM geometry
ms.assetid: 5eae2872-adca-4b8f-8b04-4ee91ced98f1
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 83f6f173213f81f9633d9593f73d115851789cce
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88445119"
---
# <a name="asbinaryzm-geometry-datatype"></a>AsBinaryZM (geometry-Datentyp)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

Gibt die Open Geospatial Consortium (OGC) WKB-Darstellung (Well-Known Binary) einer **geometry**-Instanz zurück, die um alle von der Instanz getragenen **Z**- (Höhe) und **M**-Werte (Measure) erweitert wurde.
  
## <a name="syntax"></a>Syntax  
  
```  
  
.AsBinaryZM()  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Rückgabetypen
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **varbinary(max)**  
  
 CLR-Rückgabetyp: **SqlBytes**  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="examples"></a>Beispiele  
  
```sql  
DECLARE @g1 GEOMETRY = 'Point(1 1 2 3)';  
  
SELECT @g1.STAsBinary();  
-- Returns: 0x0101000000000000000000F03F000000000000F03F  
  
SELECT @g1.AsBinaryZM();  
--Returns: 0x01B90B0000000000000000F03F000000000000F03F00000000000000400000000000000840  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)   
 [M &#40;geometry-Datentyp&#41;](../../t-sql/spatial-geometry/m-geometry-data-type.md)   
 [Z &#40;geometry Data Type&#41; (Z (geometry-Datentyp))](../../t-sql/spatial-geometry/z-geometry-data-type.md)  
  
  

