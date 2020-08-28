---
description: PositionEnum
title: Positionumum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: a871f6d2f7b73e7430761318a5acee31f05df3c1
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990071"
---
# <a name="positionenum"></a>PositionEnum
Gibt die aktuelle Position des Daten Satz Zeigers innerhalb eines [Recordsets](./recordset-object-ado.md)an.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adposbof**|-2|Gibt an, dass sich der aktuelle Daten Satz Zeiger bei BOF befindet (d. h., die [BOF](./bof-eof-properties-ado.md) -Eigenschaft ist **true**).|  
|**adtargeof**|-3|Gibt an, dass der aktuelle Daten Satz Zeiger bei EOF ist (d. h., die [EOF](./bof-eof-properties-ado.md) -Eigenschaft ist **true**).|  
|**adPosUnknown**|-1|Gibt an, dass das **Recordset** leer ist, die aktuelle Position unbekannt ist oder der Anbieter die [AbsolutePage](./absolutepage-property-ado.md) -Eigenschaft oder die [AbsolutePosition](./absoluteposition-property-ado.md) -Eigenschaft nicht unterstützt.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstante|  
|--------------|  
|Adoumums. Position. BOF|  
|Adoumums. Position. EOF|  
|Adoumums. Position. Unknown|  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [AbsolutePage-Eigenschaft (ADO)](./absolutepage-property-ado.md)  
    :::column-end:::
    :::column:::
        [AbsolutePosition-Eigenschaft (ADO)](./absoluteposition-property-ado.md)  
    :::column-end:::
:::row-end:::