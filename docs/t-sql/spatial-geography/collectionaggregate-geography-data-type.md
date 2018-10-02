---
title: CollectionAggregate (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- CollectionAggregate method (geography)
ms.assetid: e49a644a-dbf2-46c3-98f5-4b3ec197e2ad
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3f081e7c3bb990ae28bcd035008719b90e7b7ae6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47600088"
---
# <a name="collectionaggregate-geography-data-type"></a>CollectionAggregate (geography-Datentyp)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Erstellt eine **GeometryCollection** -Instanz aus einem Satz von **geography** -Objekten.
  
## <a name="syntax"></a>Syntax  
  
```  
  
ConvexHullAggregate ( geography_operand )  
```  
  
## <a name="arguments"></a>Argumente  
 *geography_operand*  
 Eine Tabellenspalte vom Typ **geography** , die einen Satz von **geography** -Objekten darstellt, die in der **GeometryCollection** -Instanz aufgelistet werden sollen.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geography**  
  
## <a name="exception"></a>Exception  
 Löst eine `FormatException` aus, wenn ungültige Eingabewerte vorhanden sind. Weitere Informationen finden Sie unter [STIsValid &#40;geography-Datentyp&#41;](../../t-sql/spatial-geography/stisvalid-geography-data-type.md).  
  
## <a name="remarks"></a>Remarks  
 Diese Methode gibt **null** zurück, wenn die Eingabe leer ist oder andere SRIDs aufweist. Weitere Informationen finden Sie unter [SRIDs &#40;Spatial Reference Identifiers&#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
 Diese Methode ignoriert **null** -Eingaben.  
  
> [!NOTE]  
>  Diese Methode gibt **null** zurück, wenn alle eingegebenen Werte **null**sind.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine `GeometryCollection` -Instanz zurückgegeben, die einen Satz von **geography** -Objekten.  
  
 ```
 USE AdventureWorks2012  
 GO  
 SELECT geography::CollectionAggregate(SpatialLocation).ToString() AS SpatialLocation  
 FROM Person.Address  
 WHERE City LIKE ('Bothell')
 ```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erweiterte statische geography-Methoden](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
