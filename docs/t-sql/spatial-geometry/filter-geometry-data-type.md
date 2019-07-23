---
title: Filter (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Filter
- Filter_TSQL
- Filter (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- Filter method
ms.assetid: 3d629a39-157e-4159-a3ca-a3c2e0ed4160
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 701110865f4cda286c647ef887dba2e29cc5fb42
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68081158"
---
# <a name="filter-geometry-data-type"></a>Filter (geometry-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Eine Methode, die eine schnelle, nur indexbezogene Schnittmethode bietet, um zu ermitteln, ob eine **geometry** -Instanz eine andere **geometry** -Instanz überschneidet, vorausgesetzt, dass ein Index verfügbar ist.
  
Gibt 1 zurück, wenn eine **geometry** -Instanz möglicherweise eine andere **geometry** -Instanz überschneidet. Diese Methode erzeugt eventuell eine falsche positive Rückgabe, und das genaue Ergebnis ist unter Umständen planabhängig. Gibt einen genauen Wert 0 (wahr negative Rückgabe) zurück, wenn keine Überschneidung von **geometry** -Instanzen gefunden wird.
  
Wenn kein Index verfügbar ist oder verwendet wird, gibt die Methode dieselben Werte zurück wie **STIntersects()** , wenn diese Methode mit denselben Parametern aufgerufen wird.
  
## <a name="syntax"></a>Syntax  
  
```  
  
.Filter ( other_geometry )  
```  
  
## <a name="arguments"></a>Argumente  
 *other_geometry*  
 Eine andere **geometry**-Instanz zum Vergleich mit der Instanz, in der Filter() aufgerufen wird.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **bit**  
  
 CLR-Rückgabetyp: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 Diese Methode ist weder deterministisch noch präzise.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird `Filter()` verwendet, um festzustellen, wo sich zwei `geometry` -Instanzen schneiden.  
  
```  
CREATE TABLE sample (id int primary key, g geometry);  
GO  
INSERT INTO sample VALUES  
   (0, geometry::Point(0, 0, 0)),  
   (1, geometry::Point(0, 1, 0)),  
   (2, geometry::Point(0, 2, 0)),  
   (3, geometry::Point(0, 3, 0)),  
   (4, geometry::Point(0, 4, 0));  
  
CREATE SPATIAL INDEX sample_idx ON sample(g)  
WITH (bounding_box = (-8000, -8000, 8000, 8000));  
GO  
SELECT id  
FROM sample   
WHERE g.Filter(geometry::Parse('POLYGON((-1 -1, 1 -1, 1 1, -1 1, -1 -1))')) = 1;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)   
 [STIntersects &#40;geometry-Datentyp&#41;](../../t-sql/spatial-geometry/stintersects-geometry-data-type.md)  
  
  

