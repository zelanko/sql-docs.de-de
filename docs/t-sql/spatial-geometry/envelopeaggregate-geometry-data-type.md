---
title: EnvelopeAggregate (geometry-Datentyp) | Microsoft-Dokumentation
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
- EnvelopeAggregate method (geometry)
ms.assetid: c4c15abe-0fe9-441d-9d42-6572e264869c
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 5c82d456f6c51b60f095178608e976303f0f6c48
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85700277"
---
# <a name="envelopeaggregate-geometry-data-type"></a>EnvelopeAggregate (geometry-Datentyp)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

Gibt für einen angegebenen Satz von **geometry** -Objekten einen Begrenzungsrahmen zurück.
  
## <a name="syntax"></a>Syntax  
  
```  
  
EnvelopeAggregate ( geometry_operand )  
```  
  
## <a name="arguments"></a>Argumente  
 *geometry_operand*  
 Eine Tabellenspalte vom Typ **geometry** , die den Satz von **geometry** -Objekten darstellt.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geometry**  
  
## <a name="exceptions"></a>Ausnahmen  
 Löst eine `FormatException` aus, wenn ungültige Eingabewerte vorhanden sind. Weitere Informationen finden Sie unter [STIsValid &#40;geometry-Datentyp&#41;](../../t-sql/spatial-geometry/stisvalid-geometry-data-type.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode gibt **null** zurück, wenn die Eingabe leer ist oder andere SRIDs aufweist. Weitere Informationen finden Sie unter [SRIDs &#40;Spatial Reference Identifiers&#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
 Diese Methode ignoriert **null** -Eingaben.  
  
> [!NOTE]  
>  Diese Methode gibt **null** zurück, wenn alle eingegebenen Werte **null**sind.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird ein Begrenzungsrahmen für einen Satz von Objekten in der Variablenspalte einer Tabelle zurückgegeben.  
  
 ```
 -- Setup table variable for EnvelopeAggregate example 
DECLARE @Geom TABLE 
( 
shape geometry, 
shapeType nvarchar(50) 
) 
INSERT INTO @Geom(shape,shapeType) VALUES('CURVEPOLYGON(CIRCULARSTRING(2 3, 4 1, 6 3, 4 5, 2 3))', 'Circle'), 
('POLYGON((1 1, 4 1, 4 5, 1 5, 1 1))', 'Rectangle'); 
-- Perform EnvelopeAggregate on @Geom.shape column 
SELECT geometry::EnvelopeAggregate(shape).ToString() 
FROM @Geom;
 ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte statische geometry-Methoden](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  

