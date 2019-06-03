---
title: Z (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Z (geometry Data Type)
- Z_(geometry_Data_Type)_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Z (geometry Data Type)
ms.assetid: a62ed736-44df-4591-9109-ce90e1df9bd3
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 3354d243b7a49e7fc34041e7912e8ac337476917
ms.sourcegitcommit: 57c3b07cba5855fc7b4195a0586b42f8b45c08c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2019
ms.locfileid: "65935406"
---
# <a name="z-geometry-data-type"></a>Z (geometry-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Der Z-Wert (Höhe) der Instanz. Die Semantik des Höhenwerts ist benutzerdefiniert.
  
## <a name="syntax"></a>Syntax  
  
```  
  
.Z  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ: **float**  
  
 CLR-Typ: **SqlDouble**  
  
## <a name="remarks"></a>Remarks  
 Der Wert dieser Eigenschaft ist NULL, wenn die geometry-Instanz kein Punkt ist. Sie ist außerdem NULL für jede **Point** -Instanz, für die sie nicht festgelegt ist.  
  
 Diese Eigenschaft ist schreibgeschützt.  
  
 Z-Koordinaten werden in Berechnungen der Bibliothek nicht verwendet und werden nicht in Bibliotheksberechnungen einbezogen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine `Point` -Instanz mit Z (Höhe)- und M (Measure)-Werten erstellt und `Z` verwendet, um den Z-Wert der Instanz abzurufen.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(1 2 3 4)', 0);  
SELECT @g.Z;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [M &#40;geometry-Datentyp&#41;](../../t-sql/spatial-geometry/m-geometry-data-type.md)   
 [AsTextZM &#40;geometry-Datentyp&#41;](../../t-sql/spatial-geometry/astextzm-geometry-data-type.md)   
 [Erweiterte Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

