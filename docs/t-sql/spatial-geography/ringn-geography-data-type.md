---
title: RingN (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- RingN
- RingN_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- RingN method
ms.assetid: 30f47275-2727-4d22-bbec-c0c54bcb3ac2
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 8de2f7c47572e8f25fdc38ce6bb537dadfc38d7d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68042661"
---
# <a name="ringn-geography-data-type"></a>RingN (geography-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt den angegebenen Ring der **geography** -Instanz zurück: `1 ≤ n ≤ NumRings()`.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.RingN (expression )  
```  
  
## <a name="arguments"></a>Argumente  
 *expression*  
 Ein **int** -Ausdruck zwischen 1 und der Anzahl der Ringe in einer **polygon** -Instanz.  
  
## <a name="return-value"></a>Rückgabewert  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geography**  
  
 CLR-Rückgabetyp: **SqlGeography**  
  
## <a name="remarks"></a>Bemerkungen  
 Ist der Wert des Ringindex **n** kleiner 1, löst diese Methode eine **ArgumentOutOfRangeException.** aus. Der Wert des Ringindex muss größer oder gleich 1 sein und sollte kleiner oder gleich dem Wert sein, der von `NumRings()`.  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel wird eine `Polygon` -Instanz mit zwei Ringen erstellt. Dann wird der zweite Ring zurückgegeben.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653), (-122.357 47.654, -122.357 47.657, -122.349 47.657, -122.349 47.650, -122.357 47.654))', 4326);  
SELECT @g.RingN(2).ToString();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Methoden für geography-Instanzen](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [NumRings &#40;geography-Datentyp&#41;](../../t-sql/spatial-geography/numrings-geography-data-type.md)  
  
  
