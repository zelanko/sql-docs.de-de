---
description: M (geometry-Datentyp)
title: M (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- M (geometry Data Type)
- M_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- M (geometry Data Type)
ms.assetid: 443ae2ea-739b-41ef-96cc-ac5dfd65e10b
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 79a575b57bc3f41f48f9a00ed95784b09f84f5f6
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2020
ms.locfileid: "88497058"
---
# <a name="m-geometry-data-type"></a>M (geometry-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Der **M** (Measure)-Wert der **geometry** -Instanz. Die Semantik des Measurewerts ist benutzerdefiniert.  

## <a name="syntax"></a>Syntax  
  
```  
  
.M  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ: **float**  
  
 CLR-Typ: **SqlDouble**  
  
## <a name="remarks"></a>Bemerkungen  
 Der Wert dieser Eigenschaft ist NULL, wenn die **geometry** -Instanz kein **Point** ist. Sie ist außerdem NULL für jede **Point** -Instanz, für die sie nicht festgelegt ist.  
  
 Diese Eigenschaft ist schreibgeschützt.  
  
 **M** -Werte werden in Berechnungen der Bibliothek nicht verwendet und werden nicht in Bibliotheksberechnungen einbezogen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine `Point` -Instanz mit Z (Höhe)- und M (Measure)-Werten erstellt und `M` verwendet, um den M-Wert der Instanz abzurufen.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(1 2 3 4)', 0);  
SELECT @g.M;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)   
 [Z &#40;geometry-Datentyp&#41;](../../t-sql/spatial-geometry/z-geometry-data-type.md)   
 [AsTextZM &#40;geometry-Datentyp&#41;](../../t-sql/spatial-geometry/astextzm-geometry-data-type.md)  
  
  

