---
title: ReorientObject (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ReorientObject
- ReorientObject_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ReorientObject method (geography)
ms.assetid: e2a1a4f1-211b-4e82-abed-03fc7140a83c
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: e2945b08eaf0a22c6c83bd412e97c729bedfdfea
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65936352"
---
# <a name="reorientobject-geography-data-type"></a>ReorientObject (geography-Datentyp)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Gibt eine **geography** -Instanz mit ausgetauschtem inneren und äußeren Bereich zurück.  
  
Diese **geography** -Datentypmethode unterstützt Instanzen von **FullGlobe** oder räumliche Instanzen, die größer als eine Hemisphäre sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.ReorientObject (geography)  
```  
  
## <a name="arguments"></a>Argumente  
_geography_  
Eine andere Instanz von **geography** , für die `ReorientObject()` aufgerufen wird.  
  
## <a name="return-value"></a>Rückgabewert  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geography**  
  
CLR-Rückgabetyp: **SqlGeography**  
  
## <a name="remarks"></a>Remarks  
Mit dieser Methode wird die Ringausrichtung aller **Polygons** in eine **GeometryCollection** geändert, ohne **Points** oder **LineStrings** in der angegebenen Sammlung zu ändern.  
  
Wenn Sie eine **GeometryCollection** an die Methode übergeben, werden alle Instanzen in der Sammlung neu ausgerichtet, die Sammlung als Ganzes wird jedoch nicht neu ausgerichtet.  
  
## <a name="examples"></a>Beispiele  
  
```  
DECLARE @R GEOGRAPHY = GEOGRAPHY::Parse('Polygon((-10 -10, -10 10, 10 10, 10 -10, -10 -10))');  
SELECT @R.ReorientObject().STAsText();  
--Result: POLYGON ((10 10, -10 10, -10 -10, 10 -10, 10 10))  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[Erweiterte Methoden für geography-Instanzen](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
