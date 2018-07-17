---
title: Long (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Long_TSQL
- Long
dev_langs:
- TSQL
helpviewer_keywords:
- Long method
ms.assetid: bedbeced-70b8-4569-84f3-f86bfb04ce50
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 88b07b5ea327b3d35946991e5a776d9d0fdea8ad
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36243422"
---
# <a name="long-geography-data-type"></a>Long (geography-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Die Längengradeigenschaft der **geography** -Instanz.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.Long  
```  
  
## <a name="return-value"></a>Rückgabewert  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ: **float**  
  
 CLR-Typ: **SqlDouble**  
  
## <a name="remarks"></a>Remarks  
 Im OpenGIS-Modell ist Long nur für **geography**-Instanzen definiert, die aus einem einzelnen Punkt bestehen. Diese Eigenschaft gibt NULL zurück, wenn **geography** -Instanzen mehr als nur einen Punkt enthalten. Diese Eigenschaft exakt und ist schreibgeschützt.  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel wird eine **Point** -Instanz erstellt und der Längengrad des Punkts abgerufen.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.Long;  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erweiterte Methoden für geography-Instanzen](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
