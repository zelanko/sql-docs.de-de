---
title: ToString (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ToString (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- ToString (geometry Data Type)
ms.assetid: 2e55fa98-aa22-4baa-a516-7c233a33e212
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 62d8f5a0348dd6104983daaf2592feda80514a4f
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86554900"
---
# <a name="tostring-geometry-data-type"></a>ToString (geometry-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Gibt die Open Geospatial Consortium (OGC) Well-Known Text (WKT)-Darstellung einer geometry-Instanz zurück, die um alle von der Instanz getragenen Z (Höhe)- und M (Measure)-Werte erweitert ist.
  
## <a name="syntax"></a>Syntax  
  
```  
  
.ToString ()  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Rückgabetypen
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **nvarchar(max)**  
  
 CLR-Rückgabetyp: **SqlString**  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode gibt die Zeichenfolge "NULL" zurück, wenn sie für NULL-Instanzen aufgerufen wird.  
  
 Bei Instanzen, die nicht NULL sind, entspricht diese Methode der Verwendung von `AsTextZM().`.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine `LineString` -Instanz erstellt und mithilfe von `ToString()` eine Textbeschreibung der Instanz abgerufen.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 0 1, 1 0)', 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [STAsText &#40;geometry-Datentyp&#41;](../../t-sql/spatial-geometry/stastext-geometry-data-type.md)   
 [Erweiterte Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

