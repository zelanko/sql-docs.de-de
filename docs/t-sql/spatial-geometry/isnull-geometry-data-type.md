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
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 7cb1cccba4c880fd2e92d707e51c8c4e324fba9c
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86555658"
---
# <a name="isnull-geometry-data-type"></a>IsNull (geometry-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Der Typ einer **geometry**-Instanz ist NULL. Gibt 0 zurück, wenn die Instanz nicht NULL ist.
  
## <a name="syntax"></a>Syntax  
  
```  
.IsNull  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Rückgabetypen
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ: **bit**  
  
 CLR-Typ: **SqlBoolean**  
  
## <a name="remarks"></a>Bemerkungen  
 `IsNull` kann verwendet werden, um zu überprüfen, ob eine **geometry**-Instanz NULL ist. `IsNull` gibt 0 zurück, wenn die Instanz nicht NULL ist, gibt aber Null zurück, wenn die Instanz NULL ist.  
  
 Diese Methode wird in erster Linie von der SQL Server-Infrastruktur verwendet. Es wird nicht empfohlen, mit `IsNull` zu prüfen, ob eine Instanz NULL ist.  
  

## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

