---
title: STNumGeometries (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STNumGeometries (geometry Data Type)
- STNumGeometries_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STNumGeometries (geometry Data Type)
ms.assetid: 9402b03d-3039-42ca-ac59-f96b7f1a48de
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 3bd050fc07c39dc33781a2c9c1ec09128540f216
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85762283"
---
# <a name="stnumgeometries-geometry-data-type"></a>STNumGeometries (geometry-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Gibt die Anzahl von Geometrien zurück, die eine **geometry**-Instanz enthalten.
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STNumGeometries ( )  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **int**  
  
 CLR-Rückgabetyp: **SqlInt32**  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode gibt 1 zurück, wenn die **geometry**-Instanz keine **MultiPoint**-, **MultiLineString**-, **MultiPolygon**- oder **GeometryCollection**-Instanz ist. Sie gibt 0 (null) zurück, wenn die **geometry**-Instanz leer ist.  
  
> [!NOTE]  
>  Wenn eine **GeometryCollection** geschachtelte leere Elemente enthält, gibt `STNumGeometries()` nicht 0 (null) zurück. Obwohl die Elemente in der **GeometryCollection**-Instanz leer sind, ist die Instanz selbst keine leere Menge.  
  
  

