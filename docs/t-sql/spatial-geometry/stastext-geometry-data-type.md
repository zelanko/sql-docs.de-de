---
title: STAsText (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STAsText_TSQL
- STAsText (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STAsText (geometry Data Type)
ms.assetid: e0decf5e-2858-4c56-b61a-6123f47fb51c
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: b2c16ad7d74d69f743708bbf95fdaf0d23f43e14
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86554320"
---
# <a name="stastext-geometry-data-type"></a>STAsText (geometry-Datentyp)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

Gibt die Open Geospatial Consortium (OGC) Well-Known Text (WKT)-Darstellung einer **geometry** -Instanz zurück. Dieser Text enthält keine Z (Höhe)- oder M (Measure)-Werte, die von der Instanz getragen werden.
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STAsText ( )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Rückgabetypen
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **nvarchar(max)**  
  
 CLR-Rückgabetyp: **SqlChars**  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine `LineString` -geometry-Instanz von (0,0) bis (2,3) aus Text erstellt. `STAsText()` gibt das Ergebnis als Text zurück.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 3)', 0);  
SELECT @g.STAsText();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [OGC-Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

