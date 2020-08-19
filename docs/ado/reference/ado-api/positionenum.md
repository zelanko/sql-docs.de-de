---
description: PositionEnum
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 326fc4f1b9b77c8a4470fedc7d55f2d379aff6f3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442712"
---
# <a name="positionenum"></a>PositionEnum
Gibt die aktuelle Position des Daten Satz Zeigers innerhalb eines [Recordsets](../../../ado/reference/ado-api/recordset-object-ado.md)an.  
  
|Konstant|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adposbof**|-2|Gibt an, dass sich der aktuelle Daten Satz Zeiger bei BOF befindet (d. h., die [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) -Eigenschaft ist **true**).|  
|**adtargeof**|-3|Gibt an, dass der aktuelle Daten Satz Zeiger bei EOF ist (d. h., die [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) -Eigenschaft ist **true**).|  
|**adPosUnknown**|-1|Gibt an, dass das **Recordset** leer ist, die aktuelle Position unbekannt ist oder der Anbieter die [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) -Eigenschaft oder die [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) -Eigenschaft nicht unterstützt.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstant|  
|--------------|  
|Adoumums. Position. BOF|  
|Adoumums. Position. EOF|  
|Adoumums. Position. Unknown|  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [AbsolutePage-Eigenschaft (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)  
    :::column-end:::
    :::column:::
        [AbsolutePosition-Eigenschaft (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)  
    :::column-end:::
:::row-end:::
