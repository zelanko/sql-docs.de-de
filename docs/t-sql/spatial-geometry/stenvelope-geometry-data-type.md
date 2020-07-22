---
title: STEnvelope (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STEnvelope_TSQL
- STEnvelope (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STEnvelope (geometry Data Type)
ms.assetid: 781d22e9-38df-4c23-836f-6dd0bdef49c5
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 87146a39fda67da157c48abed2b06dab926e7194
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86554675"
---
# <a name="stenvelope-geometry-data-type"></a>STEnvelope (geometry-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Gibt das minimale, an den Achsen ausgerichtete umschließende Rechteck der Instanz zurück.
  
## <a name="syntax"></a>Syntax  
  
```  
  
STEnvelope ( )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Rückgabetypen
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geometry**  
  
 CLR-Rückgabetyp: **SqlGeometry**  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird mithilfe von `STGeomFromText()` eine `LineString`-Instanz aus (0,0) bis (2,3) erstellt und `STEnvelope()` verwendet, um das umschließende Rechteck der `LineString`-Instanz zurückzugeben.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 3)', 0);  
SELECT @g.STEnvelope().ToString();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [OGC-Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

