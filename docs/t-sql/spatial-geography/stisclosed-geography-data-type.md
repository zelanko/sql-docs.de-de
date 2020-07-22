---
title: STIsClosed (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STIsClosed (geography Data Type)
- STIsClosed_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STIsClosed method
ms.assetid: eba1643f-07c4-4500-8643-b7e90f908147
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 06190fa6cc6a0377e49f423c50369a7ceb4b51d7
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86555771"
---
# <a name="stisclosed-geography-data-type"></a>STIsClosed (geography-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Gibt 1 zurück, wenn Ausgangs- und Endpunkte der angegebenen **geography** -Instanz gleich sind. Gibt 1 für **geography** -Auflistungstypen zurück, wenn alle enthaltenen Instanzen von **geography** geschlossen sind. Gibt 0 zurück, wenn die Instanz nicht geschlossen ist.  
  
 Diese **geography** -Datentypmethode unterstützt Instanzen von **FullGlobe** oder räumliche Instanzen, die größer als eine Hemisphäre sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STIsClosed ( )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Rückgabetypen
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **bit**  
  
 CLR-Rückgabetyp: **SqlBoolean**  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode gibt 0 zurück, wenn eine beliebige Abbildung einer **geography** -Instanz ein Punkt ist oder wenn die Instanz leer ist.  
  
 Diese Methode gibt true zurück, wenn eine **FullGlobe** -Instanz ein **Polygon** oder anderer Typ der Instanz ist.  
  
 Alle **Polygon** -Instanzen werden als geschlossen betrachtet.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine `Polygon` -Instanz erstellt und `STIsClosed()` verwendet, um zu überprüfen, ob die `Polygon` -Instanz geschlossen ist.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SELECT @g.STIsClosed();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [OGC-Methoden für geography-Instanzen](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
