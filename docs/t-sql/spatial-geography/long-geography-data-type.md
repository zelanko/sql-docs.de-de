---
title: Long (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Long_TSQL
- Long
dev_langs:
- TSQL
helpviewer_keywords:
- Long method
ms.assetid: bedbeced-70b8-4569-84f3-f86bfb04ce50
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: dd2424bff6322ad388ef6980c0055b098433cf40
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85731130"
---
# <a name="long-geography-data-type"></a>Long (geography-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Die Längengradeigenschaft der **geography** -Instanz.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.Long  
```  
  
## <a name="return-value"></a>Rückgabewert  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ: **float**  
  
 CLR-Typ: **SqlDouble**  
  
## <a name="remarks"></a>Bemerkungen  
 Im OpenGIS-Modell ist Long nur für **geography**-Instanzen definiert, die aus einem einzelnen Punkt bestehen. Diese Eigenschaft gibt NULL zurück, wenn **geography** -Instanzen mehr als nur einen Punkt enthalten. Diese Eigenschaft exakt und ist schreibgeschützt.  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel wird eine **Point** -Instanz erstellt und der Längengrad des Punkts abgerufen.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.Long;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Methoden für geography-Instanzen](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
