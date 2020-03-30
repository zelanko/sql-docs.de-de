---
title: AsTextZM (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- AsTextZM (geography Data Type)
- AsTextZM_TSQL
- AsTextZM
- AsTextZM_(geography_Data_Type)_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- AsTextZM method
ms.assetid: e9dc27f6-e945-4457-8498-7644db34008e
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: a711e81c796293f9c9ac8694b1dc32e0e60f6938
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68066605"
---
# <a name="astextzm-geography-data-type"></a>AsTextZM (geography-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt die Open Geospatial Consortium (OGC) Well-Known Text (WKT)-Darstellung einer **geography** -Instanz zurück, die um alle von der Instanz getragenen **Z** (Höhe)- und **M** (Measure)-Werte erweitert ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.AsTextZM ()  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **nvarchar(max)**  
  
 CLR-Rückgabetyp: **SqlChars**  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine `Point` -Instanz mit dem Wert **Z** (Höhe)- und **M** (Measure) erstellt. `STAsText()` wählt die WKT-Werte (-122.34900 47.65100) aus; `AsTextZM()` wählt identische WKT-Werte aus und gibt die Werte für **Z** und **M** zurück; dies ergibt (-122.34900 47.65100 10.3 12).  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100 10.3 12)', 4326);  
SELECT @g.STAsText();  
SELECT @g.AsTextZM();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Methoden für geography-Instanzen](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [M &#40;geography-Datentyp&#41;](../../t-sql/spatial-geography/m-geography-data-type.md)   
 [Z &#40;geography-Datentyp&#41;](../../t-sql/spatial-geography/z-geography-data-type.md)  
  
  
