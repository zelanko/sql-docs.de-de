---
description: ParameterDirectionEnum
title: ParameterDirectionEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ParameterDirectionEnum
helpviewer_keywords:
- ParameterDirectionEnum enumeration [ADO]
ms.assetid: c66aa6e6-d4f0-4f0f-9640-e08ae6cfdef3
author: rothja
ms.author: jroth
ms.openlocfilehash: b7422bf0037adc8d756c20c82404a7f3b06ae9e3
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990131"
---
# <a name="parameterdirectionenum"></a>ParameterDirectionEnum
Gibt an, ob der [Parameter](./parameter-object.md) einen Eingabeparameter, einen Ausgabeparameter, einen Eingabe-und einen Output-Parameter oder den Rückgabewert einer gespeicherten Prozedur darstellt.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adParamInput**|1|Standard. Gibt an, dass der Parameter einen Eingabeparameter darstellt.|  
|**adparser-putoutput**|3|Gibt an, dass der Parameter sowohl einen Eingabe-als auch einen Output-Parameter darstellt.|  
|**adparamoutput**|2|Gibt an, dass der Parameter einen Output-Parameter darstellt.|  
|**adparamreturnvalue**|4|Gibt an, dass der Parameter einen Rückgabewert darstellt.|  
|**adparamunknown**|0|Gibt an, dass die Parameter Richtung unbekannt ist.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstante|  
|--------------|  
|Adoumums. ParameterDirection. Input|  
|Adoerums. ParameterDirection. InputOutput|  
|Adoerums. ParameterDirection. Output|  
|Adoenumerations. ParameterDirection. ReturnValue|  
|Adoumums. ParameterDirection. Unknown|  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [CreateParameter-Methode (ADO)](./createparameter-method-ado.md)  
    :::column-end:::
    :::column:::
        [Direction-Eigenschaft](./direction-property.md)  
    :::column-end:::
:::row-end:::