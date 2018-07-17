---
title: STInteriorRingN (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STInteriorRingN_TSQL
- STInteriorRingN (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STInteriorRingN (geometry Data Type)
ms.assetid: 47310f9f-2cdb-41e0-a6da-7c3cfbf139ac
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 07df50a6de97ea992935b536c19ffab8eb9d0fd9
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36250332"
---
# <a name="stinteriorringn-geometry-data-type"></a>STInteriorRingN (geometry-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Gibt den angegebenen inneren Ring einer **Polygongeometry**-Instanz zurück.
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STInteriorRingN ( expression )  
```  
  
## <a name="arguments"></a>Argumente  
 *expression*  
 Ein **int**-Ausdruck zwischen 1 und der Anzahl der inneren Ringe in der **geometry**-Instanz.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geometry**  
  
 CLR-Rückgabetyp: **SqlGeometry**  
  
 Open Geospatial Consortium (OGC)-Typ: **LineString**  
  
## <a name="remarks"></a>Remarks  
 Diese Methode gibt **null** zurück, wenn die **geometry** -Instanz kein Polygon ist. Diese Methode löst außerdem eine **ArgumentOutOfRangeException** aus, wenn der Ausdruck größer als die Anzahl der Ringe ist. Die Anzahl der Ringe kann mithilfe von `STNumInteriorRing``()` zurückgegeben werden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine `Polygon`-Instanz erstellt und dann mithilfe von `STInteriorRingN()` der innere Ring des Polygons als **LineString** zurückgegeben.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0),(2 2, 2 1, 1 1, 1 2, 2 2))', 0);  
SELECT @g.STInteriorRingN(1).ToString();  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [OGC-Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

