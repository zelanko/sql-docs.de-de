---
title: Parse (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- Parse (geometry Data Type)
ms.assetid: 6e080919-4b64-46cd-8dd2-254a9c232e53
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 631b079ca9e0e4ca23d807e84e337244e8f416d2
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36251172"
---
# <a name="parse-geometry-data-type"></a>Parse (geometry-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Gibt eine **geometry** -Instanz aus einer Open Geospatial-Konsortium (OGC) Well-Known Text (WKT)-Darstellung zurück. `Parse()` entspricht [STGeomFromText()](../../t-sql/spatial-geometry/parse-geometry-data-type.md), setzt aber eine SRID (Spatial Reference ID) mit dem Wert 0 als Parameter voraus. Die Eingabe kann optional Z- (Höhe) und M-Werte (Measure) tragen.
  
## <a name="syntax"></a>Syntax  
  
```  
  
Parse ( 'geometry_tagged_text' )  
```  
  
## <a name="arguments"></a>Argumente  
 *geometry_tagged_text*  
 Die WKT-Darstellung der Instanz von **geometry** , die zurückgegeben werden soll. *geometry_tagged_text* ist ein **nvarchar** -Ausdruck.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geometry**  
  
 CLR-Rückgabetyp: **SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 Der OGC-Typ der **geometry** -Instanz, die von `Parse()` zurückgegeben wird, wird auf die entsprechende WKT-Eingabe festgelegt.  
  
 Die Zeichenfolge 'Null' wird als eine NULL- **geometry** -Instanz interpretiert.  
  
 Diese Methode löst eine **FormatException** aus, wenn die Eingabe nicht korrekt formatiert ist.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird `Parse()` verwendet, um eine `geometry`-Instanz zu erstellen.  
  
```  
DECLARE @g geometry;   
SET @g = geometry::Parse('LINESTRING (100 100, 20 180, 180 180)');  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [STGeomFromText](../../t-sql/spatial-geometry/parse-geometry-data-type.md)   
 [Erweiterte statische geometry-Methoden](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  

