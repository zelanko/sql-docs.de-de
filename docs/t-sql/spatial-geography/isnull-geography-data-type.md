---
title: IsNull (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- IsNull (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- IsNull method
ms.assetid: c031074f-bfda-4584-a3bf-4e7c324f237f
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 438b51547823e190d568681a904c2fbfcc1e8a74
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "33058327"
---
# <a name="isnull-geography-data-type"></a>IsNull (geography-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Eigenschaft, die angibt, ob die **geography**-Instanz NULL ist. Gibt TRUE zurück, wenn die Instanz NULL ist, und gibt 0 zurück, wenn die Instanz nicht NULL ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.IsNull  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ: **bit**  
  
 CLR-Typ: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 `IsNull` kann verwendet werden, um zu überprüfen, ob eine **geography**-Instanz NULL ist. Dies kann zu möglicherweise verwirrenden Ergebnissen führen, da 0 zurückgegeben wird, wenn die Instanz nicht NULL ist, aber NULL zurückgegeben wird, wenn die Instanz NULL ist.  
  
 Diese Methode wird in erster Linie von der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Infrastruktur verwendet. Es wird empfohlen, mit dem T-SQL-Prädikat IS NULL zu prüfen, ob eine **geography**-Instanz NULL ist. Weitere Informationen zum T-SQL-Prädikat IS NULL finden Sie unter [IS NULL &#40;Transact-SQL&#41;](../../t-sql/queries/is-null-transact-sql.md).  
  
## <a name="examples"></a>Beispiele  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erweiterte Methoden für geography-Instanzen](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
