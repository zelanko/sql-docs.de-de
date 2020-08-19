---
description: STIsClosed (geometry-Datentyp)
title: STIsClosed (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STIsClosed_TSQL
- STIsClosed (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STIsClosed (geometry Data Type)
ms.assetid: 14edbb22-df7b-4b8a-b16c-ac477a5d32c1
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: c92d311ba67c71f77fef8052bcfe8e5938d1f1b5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88445037"
---
# <a name="stisclosed-geometry-data-type"></a>STIsClosed (geometry-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Gibt 1 zurück, wenn die Ausgangs- und Endpunkte der angegebenen **geometry**-Instanz gleich sind. Gibt 1 für **geometrycollection**-Typen zurück, wenn alle enthaltenen Instanzen von **geometry** geschlossen sind. Gibt 0 zurück, wenn die Instanz nicht geschlossen ist.
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STIsClosed ( )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Rückgabetypen
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **bit**  
  
 CLR-Rückgabetyp: **SqlBoolean**  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt 0 zurück, wenn eine beliebige Abbildung einer **geometry**-Instanz ein Punkt ist oder wenn die Instanz leer ist.  
  
 Alle **Polygon** -Instanzen werden als geschlossen betrachtet.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine `LineString` -Instanz erstellt und `STIsClosed()` verwendet, um zu überprüfen, ob die `LineString` -Instanz geschlossen ist.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STIsClosed();  
```  
  
## <a name="see-also"></a>Siehe auch  
 [OGC-Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

