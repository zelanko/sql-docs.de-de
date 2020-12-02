---
description: STEndpoint (geometry-Datentyp)
title: STEndpoint (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STEndpoint (geometry Data Type)
- STEndpoint_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STEndpoint (geometry Data Type)
ms.assetid: 61773c45-b568-4e0c-94da-1310c42de7f5
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 1ec856db5c9f528135393bdb968ac35de4e94f2e
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2020
ms.locfileid: "88497023"
---
# <a name="stendpoint-geometry-data-type"></a>STEndpoint (geometry-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Gibt den Endpunkt einer **geometry** -Instanz zurück.
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STEndPoint ( )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Rückgabetypen
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geometry**  
  
 CLR-Rückgabetyp: **SqlGeometry**  
  
 Open Geospatial Consortium (OGC)-Typ: **Point**  
  
## <a name="remarks"></a>Bemerkungen  
 `STEndPoint()` entspricht [STPointN](../../t-sql/spatial-geometry/stpointn-geometry-data-type.md) (x.NumPoints()).  
  
 Diese Methode gibt NULL zurück, wenn Sie für eine leere **geometry** -Instanz aufgerufen wird.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird mit `LineString` eine `STGeomFromText()` -Instanz erstellt und `STEndpoint()` verwendet, um den Endpunkt in der Beschreibung der `LineString`-Instanz abzurufen.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STEndPoint().ToString();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [OGC-Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

