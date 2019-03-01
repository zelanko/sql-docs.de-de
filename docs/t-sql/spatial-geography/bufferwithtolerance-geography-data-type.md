---
title: BufferWithTolerance (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sqll
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- BufferWithTolerance_TSQL
- BufferWithTolerance
dev_langs:
- TSQL
helpviewer_keywords:
- BefferWithTolerance method
ms.assetid: f1783e6b-0f17-464f-b1c7-1c3f7d8aa042
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 01eccfab960c7ed6ac2d207c7768f2ea7ae24696
ms.sourcegitcommit: c61c7b598aa61faa34cd802697adf3a224aa7dc4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2019
ms.locfileid: "56154675"
---
# <a name="bufferwithtolerance-geography-data-type"></a>BufferWithTolerance (geography-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Gibt ein geometrisches Objekt zurück, das die Vereinigung aller Punktwerte darstellt, deren Abstand zu einer **geography**-Instanz kleiner oder gleich einem angegebenen Wert ist, wobei eine angegebene Toleranz gewährt wird.  
  
Diese geography-Datentypmethode unterstützt Instanzen von **FullGlobe** oder räumliche Instanzen, die größer als eine Hemisphäre sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.BufferWithTolerance ( distance, tolerance, relative )  
```  
  
## <a name="arguments"></a>Argumente  
_distance_  
Ein **float**-Ausdruck, der den Abstand zu der **geometry**-Instanz angibt, um die der Puffer berechnet werden soll.  
  
Der maximale Abstand des Puffers darf 0,999 \* _π_ * minorAxis \* minorAxis / majorAxis (~0,999 \* 1/2 Umfang der Erde) oder den vollständigen Umfang der Erde nicht überschreiten.  
  
_tolerance_  
Ein **float** -Ausdruck, der die Toleranz des Pufferabstands angibt.  
  
Die maximale Variation im idealen Pufferabstand für die zurückgegebene lineare Näherung ist der Wert _tolerance_.  
  
Beispielsweise kann der ideale Pufferabstand eines Punkts ein Kreis sein, dieser Abstand muss jedoch durch ein Polygon näherungsweise angegeben werden. Je kleiner die Toleranz, desto mehr Punkte wird das Polygon haben. Dieses Ergebnis erhöht die Komplexität des Ergebnisses, minimiert aber den Fehler.  
  
Die minimale Grenze ist 0,1 Prozent des Abstands, und geringere Toleranzen werden auf die minimale Grenze aufgerundet.  
  
_relative_  
Ein **bit** , das angibt, ob der _tolerance_ -Wert relativ oder absolut ist. Wenn der Wert „TRUE“ oder 1 ist, ist die Toleranz relativ. Dieser Wert ergibt sich aus dem _tolerance_-Parameter und (Winkelweite \* Äquatorradius) des Ellipsoids. Die Toleranz ist absolut, wenn der Wert „FALSE“ oder 0 ist. Dieser _tolerance_-Wert ist die absolute maximale Variation im idealen Pufferabstand für die zurückgegebene lineare Näherung.  
  
## <a name="return-types"></a>Rückgabetypen  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geography**  
  
CLR-Rückgabetyp: **SqlGeography**  
  
## <a name="remarks"></a>Remarks  
Diese Methode löst eine **ArgumentException** aus, wenn _distance_ keine Zahl (NAN) oder wenn _distance_ positiv oder negativ unendlich ist.  Diese Methode löst auch dann eine **ArgumentException** aus, wenn _tolerance_ Null (0), keine Zahl (NAN), negativ oder positiv oder negativ unendlich ist.  
  
`STBuffer()` gibt in bestimmten Fällen eine Instanz von **FullGlobe** zurück. Beispielsweise gibt `STBuffer()` eine **FullGlobe**-Instanz für zwei Pole zurück, wenn der Pufferabstand größer als der Abstand vom Äquator zu den Polen ist.  
  
Diese Methode löst eine **ArgumentException** in **FullGlobe**-Instanzen aus, bei denen der Abstand des Puffers die folgende Einschränkung überschreitet:  
  
0,999 \* _π_ * minorAxis \* minorAxis / majorAxis (~0.999 \* 1/2 Umfang der Erde)  
  
Die Abweichung zwischen dem theoretischen und dem berechneten Puffer beträgt max(tolerance, extents \* 1,E-7), wobei die Toleranz der Wert des Parameters _tolerance_ ist. Weitere Informationen zu Erweiterungen finden Sie unter [geography-Datentyp-Methodenverweis](https://msdn.microsoft.com/library/028e6137-7128-4c74-90a7-f7bdd2d79f5e).  
  
Diese Methode ist nicht exakt.  
  
## <a name="examples"></a>Beispiele  
Im folgenden Beispiel wird eine `Point` -Instanz erstellt und `BufferWithTolerance()` verwendet, um einen groben Puffer um die Instanz zu erhalten.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.BufferWithTolerance(1, .5, 0).ToString();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[STBuffer &#40;geography-Datentyp&#41;](../../t-sql/spatial-geography/stbuffer-geography-data-type.md)   
[Erweiterte Methoden für geography-Instanzen](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
