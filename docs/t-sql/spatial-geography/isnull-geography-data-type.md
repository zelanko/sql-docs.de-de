---
description: IsNull (geography-Datentyp)
title: IsNull (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- IsNull (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- IsNull method
ms.assetid: c031074f-bfda-4584-a3bf-4e7c324f237f
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: cd161c4d14241a6596e2a54ae79cd919fb776c59
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2020
ms.locfileid: "88422374"
---
# <a name="isnull-geography-data-type"></a>IsNull (geography-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Eigenschaft, die angibt, ob die **geography**-Instanz NULL ist. Gibt TRUE zurück, wenn die Instanz NULL ist, und gibt 0 zurück, wenn die Instanz nicht NULL ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.IsNull  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Rückgabetypen
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ: **bit**  
  
 CLR-Typ: **SqlBoolean**  
  
## <a name="remarks"></a>Hinweise  
 `IsNull` kann verwendet werden, um zu überprüfen, ob eine **geography**-Instanz NULL ist. Dies kann zu möglicherweise verwirrenden Ergebnissen führen, da 0 zurückgegeben wird, wenn die Instanz nicht NULL ist, aber NULL zurückgegeben wird, wenn die Instanz NULL ist.  
  
 Diese Methode wird in erster Linie von der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Infrastruktur verwendet. Es wird empfohlen, mit dem T-SQL-Prädikat IS NULL zu prüfen, ob eine **geography**-Instanz NULL ist. Weitere Informationen zum T-SQL-Prädikat IS NULL finden Sie unter [IS NULL &#40;Transact-SQL&#41;](../../t-sql/queries/is-null-transact-sql.md).  
  
## <a name="examples"></a>Beispiele  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Methoden für geography-Instanzen](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
