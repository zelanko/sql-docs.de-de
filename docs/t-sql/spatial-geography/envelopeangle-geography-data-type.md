---
title: EnvelopeAngle (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- EnvelopeAngle
- EnvelopeAngle_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- EnvelopeAngle method
ms.assetid: 14a7ba15-168c-4b08-ba3d-951d73092ac7
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 9406d8a5913c850d492c588b49d6cff8c6cec5e4
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85736146"
---
# <a name="envelopeangle-geography-data-type"></a>EnvelopeAngle (geography-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Gibt den maximalen Winkel zwischen dem durch `EnvelopeCenter()` zurückgegebenen Punkt und einem Punkt in der **geography** -Instanz in Grad zurück.  
  
 Diese **geography** -Datentypmethode unterstützt Instanzen von **FullGlobe** oder räumliche Instanzen, die größer als eine Hemisphäre sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
EnvelopeAngle( )  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **float**  
  
 CLR-Rückgabetyp: **SqlDouble**  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode gibt einen Punkt in der **geography** -Instanz in Grad zurück. Bei Verwendung mit EnvelopeCenter () gibt `EnvelopeAngle()` einen umschließenden Kreis einer **geography**-Instanz zurück.  
  
 In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] wurde diese Methode auf **FullGlobe**-Instanzen erweitert.  
  
 Die in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] für `EnvelopeAngle()` verwendete Hemisphäreneinschränkung wurde entfernt. Bei Instanzen, deren Winkel 90 Grad übersteigt, wird jedoch 180 Grad zurückgegeben. `EnvelopeAngle()` ist bei Instanzen von **geography**, die mehr als eine Hemisphäre umfassen, nicht exakt.  
  
## <a name="examples"></a>Beispiele  
  
```  
DECLARE @g geography = 'LINESTRING(-120 45, -120 0, -90 0)';   
SELECT @g.EnvelopeAngle();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Methoden für geography-Instanzen](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [EnvelopeCenter &#40;geography-Datentyp&#41;](../../t-sql/spatial-geography/envelopecenter-geography-data-type.md)  
  
  
