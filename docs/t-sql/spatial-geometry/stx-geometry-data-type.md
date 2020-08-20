---
description: STX (geometry-Datentyp)
title: STX (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/23/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STX (geometry Data Type)
- STX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STX (geometry Data Type)
ms.assetid: 2aef77e8-0460-43f9-bad6-2aae6d8c36f9
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 975126e2aa7c1628493894f433e82c9d5619f52e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88472415"
---
# <a name="stx-geometry-data-type"></a>STX (geometry-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Die Eigenschaft, die die X-Koordinate einer **Point** -Instanz angibt.
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STX  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Rückgabetypen
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ: **float**  
  
 CLR-Typ: **SqlDouble**  
  
## <a name="remarks"></a>Bemerkungen  
 Der Wert dieser Eigenschaft ist NULL, wenn die **geometry**-Instanz kein Punkt ist.  
  
 Diese Eigenschaft ist schreibgeschützt.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine `Point`-Instanz erstellt und `STX` verwendet, um die X-Koordinate der Instanz abzurufen.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(3 8)', 0);  
SELECT @g.STX;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [STY &#40;geometry-Datentyp&#41;](../../t-sql/spatial-geometry/sty-geometry-data-type.md)   
 [STSrid &#40;geometry-Datentyp&#41;](../../t-sql/spatial-geometry/stsrid-geometry-data-type.md)   
 [OGC-Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

