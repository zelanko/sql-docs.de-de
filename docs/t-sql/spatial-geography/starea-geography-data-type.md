---
title: STArea (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STArea (geography Data Type)
- STArea_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STArea method
ms.assetid: cfc0b0e0-7fde-431a-863f-d13f3b1b1bef
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 299ccb67b03a654a348492f81ea62f086229efab
ms.sourcegitcommit: 01e17c5f1710e7058bad8227c8011985a9888d36
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265277"
---
# <a name="starea-geography-data-type"></a>STArea (geography-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Gibt die gesamte Oberfläche einer **geography**-Instanz zurück. Die Ergebnisse für STArea() sind die quadratische Maßeinheit, die von der räumlichen Referenz-ID der Instanz **geography** verwendet wird. Wenn beispielsweise die SRID der Instanz 4326 ist, gibt STArea() die Ergebnisse in Quadratmetern zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STArea ( )  
```  
  
## <a name="return-types"></a>Rückgabetypen  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **float**  
  
CLR-Rückgabetyp: **SqlDouble**  
  
## <a name="remarks"></a>Remarks  
STArea() gibt 0 zurück, wenn eine **geography**-Instanz nur null- und eindimensionale Abbildungen enthält oder leer ist.  
  
> [!NOTE]  
>  Methoden für den **geography**-Datentyp, die einen metrischen Rückgabewert erzeugen, liefern unterschiedliche Ergebnisse, abhängig vom SRID der in der jeweiligen Methode verwendeten Instanz. Weitere Informationen über SRIDs finden Sie unter [SRIDs &#40;Spatial Reference Identifiers&#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
## <a name="examples"></a>Beispiele  
Im folgenden Beispiel wird mithilfe von `STArea()` eine `Polygon geography`-Instanz erstellt und dann der Bereich des Polygons berechnet.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SELECT @g.STArea();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[OGC-Methoden für geography-Instanzen](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
