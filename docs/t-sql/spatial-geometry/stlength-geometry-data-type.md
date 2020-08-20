---
description: STLength (geometry-Datentyp)
title: STLength (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STLength_TSQL
- STLength (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STLength (geometry Data Type)
ms.assetid: e34dc620-2a65-4248-b099-fff91830ab98
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 713e423d0ef388ea63089bc2b4a203b8affa0fad
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88488110"
---
# <a name="stlength-geometry-data-type"></a>STLength (geometry-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Gibt die Gesamtlänge der Elemente in einer **geometry**-Instanz zurück.
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STLength ( )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Rückgabetypen
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **float**  
  
 CLR-Rückgabetyp: **SqlDouble**  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn eine **geometry**-Instanz geschlossen ist, wird ihre Länge als Gesamtlänge um die Instanz herum berechnet. Die Länge eines Polygons entspricht seinem Umfang, und die Länge eines Punkts ist 0. Die Länge eines beliebigen **geometrycollection**-Typs ist die Summe der Längen der in ihm enthaltenen **geometry**-Instanzen.  
  
 STLength() funktioniert sowohl für gültige als auch für ungültige LineStrings. In der Regel ist ein LineString aufgrund überlappender Segmente ungültig, die möglicherweise durch Anomalien wie ungenaue GPS-Ablaufverfolgungen verursacht werden. STLength() entfernt keine überlappenden oder ungültigen Segmente. Sie schließt überlappende und ungültige Segmente in den zurückgegebenen Längenwert ein. Die MakeValid()-Methode kann überlappende Segmente aus einem LineString entfernen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine `LineString` -Instanz erstellt und `STLength()` verwendet, um die Länge der Instanz zu bestimmen.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STLength();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [OGC-Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

