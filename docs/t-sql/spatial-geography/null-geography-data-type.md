---
title: NULL (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Null (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- Null (geography Data Type)
- Null method
ms.assetid: bb464b06-86e0-4b8b-ad78-04bd33b6069c
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4972ec118bf7d9abc146271c97072a7184d726af
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47720168"
---
# <a name="null-geography-data-type"></a>NULL (geography-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Eine schreibgeschützte Eigenschaft, die eine NULL-Instanz des **geography** -Typs bereitstellt.
  
## <a name="syntax"></a>Syntax  
  
```  
  
Null  
```  
  
## <a name="arguments"></a>Argumente  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ: **geography**  
  
 CLR-Typ: **SqlGeography**  
  
## <a name="remarks"></a>Remarks  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine NULL- `geography` -Instanz abgerufen.  
  
```  
DECLARE @g geography;   
SET @g = geography::[Null];  
SELECT @g  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erweiterte statische geography-Methoden](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
