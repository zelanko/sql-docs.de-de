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
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 34d9b73b050d40e6ae83637f69f2f7aa2ec6f7b4
ms.sourcegitcommit: 57c3b07cba5855fc7b4195a0586b42f8b45c08c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2019
ms.locfileid: "65937599"
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte statische geography-Methoden](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
