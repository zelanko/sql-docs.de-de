---
title: HasZ (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- HasZ
- HasZ_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- HasZ geography
ms.assetid: 4c5e1669-a987-4dda-9ebf-f573ce615c34
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 8d4a1365424adcf8601fdccb6cd59dc5d94b7f2f
ms.sourcegitcommit: 57c3b07cba5855fc7b4195a0586b42f8b45c08c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2019
ms.locfileid: "65937732"
---
# <a name="hasz-geography-data-type"></a>HasZ (geography-Datentyp)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Gibt 1 (true) zurück, wenn ein räumliches Objekt mindestens einen Z-Wert enthält. Andernfalls wird 0 (false) zurückgegeben.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.HasZ  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **bit**  
  
 CLR-Rückgabetyp: **Boolean**  
  
## <a name="remarks"></a>Remarks  
  
## <a name="examples"></a>Beispiele  
  
```sql  
DECLARE @p GEOGRAPHY = 'Point(1 1 1 1)'  
SELECT @p.HasZ   
--Returns: 1 (true)  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Methoden für geography-Instanzen](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [Z &#40;geography-Datentyp&#41;](../../t-sql/spatial-geography/z-geography-data-type.md)  
  
  
