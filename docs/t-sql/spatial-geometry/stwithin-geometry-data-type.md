---
title: STWithin (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STWithin_TSQL
- STWithin (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STWithin (geometry Data Type)
ms.assetid: f845d28c-8029-4e2b-bcf0-71c52a592501
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 579f2fd2e4e662bf5f8a060c93f7370af4edb7e7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65935643"
---
# <a name="stwithin-geometry-data-type"></a>STWithin (geometry-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Gibt 1 zurück, wenn eine **geometry** -Instanz sich vollständig innerhalb einer anderen **geometry** -Instanz befindet. Andernfalls wird 0 zurückgegeben. Für den Befehl `STWithin` muss die Groß-/Kleinschreibung beachtet werden.
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STWithin ( other_geometry )  
```  
  
## <a name="arguments"></a>Argumente  
 *other_geometry*  
 Eine andere **geometry** -Instanz zum Vergleich mit der Instanz, in der `STWithin()` aufgerufen wird.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **bit**  
  
 CLR-Rückgabetyp: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 Diese Methode gibt immer NULL zurück, wenn die SRIDs (Spatial Reference IDs) der **geometry** -Instanzen nicht übereinstimmen.
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird `STWithin()` verwendet, um zwei `geometry` -Instanzen daraufhin zu überprüfen, ob die erste Instanz sich vollständig innerhalb der zweiten Instanz befindet.  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 2 0, 2 2, 0 2, 0 0))', 0);  
SET @h = geometry::STGeomFromText('POLYGON((1 1, 3 1, 3 3, 1 3, 1 1))', 0);  
SELECT @g.STWithin(@h);  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über räumliche Indizes](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [OGC-Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

