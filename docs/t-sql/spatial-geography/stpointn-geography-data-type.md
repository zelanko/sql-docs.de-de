---
title: STPointN (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STPointN_TSQL
- STPointN (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STPointN method
ms.assetid: 47670feb-b9e0-4b4b-af83-b9bba7da66ac
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 12ae393f99510df743b5a5ec0bf777f7b982d570
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "68120820"
---
# <a name="stpointn-geography-data-type"></a>STPointN (geography-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt den angegebenen Punkt in einer **geography** -Instanz zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STPointN ( expression )  
```  
  
## <a name="arguments"></a>Argumente  
 *expression*  
 Ein **int** -Ausdruck zwischen 1 und der Anzahl der Punkte in der **geography** -Instanz.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geography**  
  
 CLR-Rückgabetyp: **SqlGeography**  
  
 Open Geospatial Consortium (OGC)-Typ: **Point**  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn eine **geography**-Instanz von einem Benutzer erstellt wurde, gibt STPointN() den von *expression* festgelegten Punkt zurück, indem die Punkte in der Reihenfolge sortiert werden, in der sie ursprünglich eingegeben wurden.  
  
 Wenn eine **geography**-Instanz systemseitig erstellt wurde, gibt STPointN() den von *expression* angegebenen Punkt zurück, indem alle Punkte in der Reihenfolge sortiert werden, in der sie ausgegeben werden: erst nach der **geography**-Instanz, dann nach dem Ring innerhalb der Instanz (falls zutreffend) und schließlich nach dem Punkt innerhalb des Rings. Diese Reihenfolge ist deterministisch.  
  
 Wenn diese Methode mit einem geringeren Wert als 1 aufgerufen wird, löst sie eine **ArgumentOutOfRangeException**aus.  
  
 Wenn diese Methode mit einem Wert aufgerufen wird, der die Anzahl der Punkte in der Instanz übersteigt, gibt sie NULL zurück.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine `LineString` -Instanz erstellt und `STPointN()` verwendet, um den zweiten Punkt in der Beschreibung der Instanz abzurufen.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STPointN(2).ToString();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [OGC-Methoden für geography-Instanzen](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
