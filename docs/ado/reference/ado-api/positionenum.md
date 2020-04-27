---
title: Positionumum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- PositionEnum
helpviewer_keywords:
- PositionEnum enumeration
ms.assetid: e69af0a5-3405-4b72-9c6e-6b188ff746fd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d5f7ca47177a953313ff983bb25f9178b73b4930
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67917603"
---
# <a name="positionenum"></a>PositionEnum
Gibt die aktuelle Position des Daten Satz Zeigers innerhalb eines [Recordsets](../../../ado/reference/ado-api/recordset-object-ado.md)an.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adposbof**|-2|Gibt an, dass sich der aktuelle Daten Satz Zeiger bei BOF befindet (d. h., die [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) -Eigenschaft ist **true**).|  
|**adtargeof**|-3|Gibt an, dass der aktuelle Daten Satz Zeiger bei EOF ist (d. h., die [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) -Eigenschaft ist **true**).|  
|**adPosUnknown**|-1|Gibt an, dass das **Recordset** leer ist, die aktuelle Position unbekannt ist oder der Anbieter die [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) -Eigenschaft oder die [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) -Eigenschaft nicht unterstützt.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstante|  
|--------------|  
|Adoumums. Position. BOF|  
|Adoumums. Position. EOF|  
|Adoumums. Position. Unknown|  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[AbsolutePage-Eigenschaft (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)|[AbsolutePosition-Eigenschaft (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|
