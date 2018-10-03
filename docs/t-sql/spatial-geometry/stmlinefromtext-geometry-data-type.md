---
title: STMLineFromText (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STMLineFromText (geometry Data Type)
- STMLineFromText_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STMLineFromText (geometry Data Type)
ms.assetid: 39fe8559-c4c2-4d61-8508-86eb0a103807
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: da888409c10249e6ef110af1762fb69a3350b630
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47800469"
---
# <a name="stmlinefromtext-geometry-data-type"></a>STMLineFromText (geometry-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Gibt eine **geometry** -Instanz aus einer Darstellung des Typs Open Geospatial Consortium (OGC) Well-Known Text (WKT) zurück, die um alle von der Instanz getragenen Z (Höhe)- und M (Measure)-Werte erweitert wurde.
  
## <a name="syntax"></a>Syntax  
  
```  
  
STMLineFromText ( 'multilinestring_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>Argumente  
 *multilinestring_tagged_text*  
 Die WKT-Darstellung der **geometryMultiLineString**-Instanz, die zurückgegeben werden soll. *multilinestring_tagged_text* ist ein **nvarchar(max)**-Ausdruck.  
  
 *SRID*  
 Ein **int**-Ausdruck, der die SRID (Spatial Reference ID) der **geometryMultiLineString**-Instanz darstellt, die Sie zurückgeben möchten.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geometry**  
  
 CLR-Rückgabetyp: **SqlGeometry**  
  
 OGC-Typ: **MultiLineString**  
  
## <a name="remarks"></a>Remarks  
 Diese Methode löst eine **FormatException** aus, wenn die Eingabe nicht korrekt formatiert ist.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird `STMLineFromText()` verwendet, um eine `geometry`-Instanz zu erstellen.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STMLineFromText('MULTILINESTRING ((100 100, 200 200), (3 4, 7 8, 10 10))', 0);  
```  
  
 `SELECT @g.ToString();`  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Statische geometry-Methoden des OGC](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  

