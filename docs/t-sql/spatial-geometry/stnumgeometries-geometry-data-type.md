---
title: STNumGeometries (geometry-Datentyp) | Microsoft-Dokumentation
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
- STNumGeometries (geometry Data Type)
- STNumGeometries_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STNumGeometries (geometry Data Type)
ms.assetid: 9402b03d-3039-42ca-ac59-f96b7f1a48de
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7a34980aaad2ed7e78cb6b5058d792dd608d176f
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36252002"
---
# <a name="stnumgeometries-geometry-data-type"></a>STNumGeometries (geometry-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Gibt die Anzahl von Geometrien zurück, die eine **geometry**-Instanz enthalten.
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STNumGeometries ( )  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **int**  
  
 CLR-Rückgabetyp: **SqlInt32**  
  
## <a name="remarks"></a>Remarks  
 Diese Methode gibt 1 zurück, wenn die **geometry**-Instanz keine **MultiPoint**-, **MultiLineString**-, **MultiPolygon**- oder **GeometryCollection**-Instanz ist. Sie gibt 0 (null) zurück, wenn die **geometry**-Instanz leer ist.  
  
> [!NOTE]  
>  Wenn eine **GeometryCollection** geschachtelte leere Elemente enthält, gibt `STNumGeometries()` nicht 0 (null) zurück. Obwohl die Elemente in der **GeometryCollection**-Instanz leer sind, ist die Instanz selbst keine leere Menge.  
  
  

