---
title: STY (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STY_TSQL
- STY (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STY (geometry Data Type)
ms.assetid: f72e0eaa-7d1d-4052-88fd-a172d8cb0d71
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cab1e15d6ea1757042c0d310e60b7ff757a84a3d
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36257562"
---
# <a name="sty-geometry-data-type"></a>STY (geometry-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Die Eigenschaft, die die Y-Koordinate einer **Point** -Instanz angibt.
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STY  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ: **float**  
  
 CLR-Typ: **SqlDouble**  
  
## <a name="remarks"></a>Remarks  
 Der Wert dieser Eigenschaft ist NULL, wenn die **geometry** -Instanz ein Punkt ist. Diese Eigenschaft ist schreibgeschützt.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine `Point` -Instanz erstellt und `STY` verwendet, um die Y-Koordinate der Instanz abzurufen.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(3 8)', 0);  
SELECT @g.STY;  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [STX &#40;geometry-Datentyp&#41;](../../t-sql/spatial-geometry/stx-geometry-data-type.md)   
 [STSrid &#40;geometry-Datentyp&#41;](../../t-sql/spatial-geometry/stsrid-geometry-data-type.md)   
 [OGC-Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

