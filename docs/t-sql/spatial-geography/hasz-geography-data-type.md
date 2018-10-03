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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 54d74f96eee99b7c05ab9d26bf9733d4b457bbc5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47625108"
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
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erweiterte Methoden für geography-Instanzen](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [Z &#40;geography-Datentyp&#41;](../../t-sql/spatial-geography/z-geography-data-type.md)  
  
  
