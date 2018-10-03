---
title: IsNull (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- IsNull (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- IsNull (geometry Data Type)
ms.assetid: f95813a5-26c0-48aa-bfb8-56d2a0980788
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 89bbf3581f8a62750338d1d7ea360fc46ea36479
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47682028"
---
# <a name="isnull-geometry-data-type"></a>IsNull (geometry-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Der Typ einer **geometry**-Instanz ist NULL. Gibt 0 zurück, wenn die Instanz nicht NULL ist.
  
## <a name="syntax"></a>Syntax  
  
```  
.IsNull  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ: **bit**  
  
 CLR-Typ: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 `IsNull` kann verwendet werden, um zu überprüfen, ob eine **geometry**-Instanz NULL ist. Dies kann zu möglicherweise verwirrenden Ergebnissen führen, da 0 zurückgegeben wird, wenn die Instanz nicht NULL ist, aber NULL zurückgegeben wird, wenn die Instanz NULL ist.  
  
 Diese Methode wird in erster Linie von der .SQL Server-Infrastruktur verwendet. Es wird nicht empfohlen, mit `IsNull` zu prüfen, ob eine Instanz NULL ist.  
  

## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erweiterte Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

