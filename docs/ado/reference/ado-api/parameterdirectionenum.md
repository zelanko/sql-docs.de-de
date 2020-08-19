---
description: ParameterDirectionEnum
title: ParameterDirectionEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
ms.openlocfilehash: 8c586b4e7ce2e18411d147e8aafb4eb144e01e6f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442782"
---
# <a name="parameterdirectionenum"></a>ParameterDirectionEnum
Gibt an, ob der [Parameter](../../../ado/reference/ado-api/parameter-object.md) einen Eingabeparameter, einen Ausgabeparameter, einen Eingabe-und einen Output-Parameter oder den Rückgabewert einer gespeicherten Prozedur darstellt.  
  
|Konstant|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adParamInput**|1|Standard. Gibt an, dass der Parameter einen Eingabeparameter darstellt.|  
|**adparser-putoutput**|3|Gibt an, dass der Parameter sowohl einen Eingabe-als auch einen Output-Parameter darstellt.|  
|**adparamoutput**|2|Gibt an, dass der Parameter einen Output-Parameter darstellt.|  
|**adparamreturnvalue**|4|Gibt an, dass der Parameter einen Rückgabewert darstellt.|  
|**adparamunknown**|0|Gibt an, dass die Parameter Richtung unbekannt ist.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstant|  
|--------------|  
|Adoumums. ParameterDirection. Input|  
|Adoerums. ParameterDirection. InputOutput|  
|Adoerums. ParameterDirection. Output|  
|Adoenumerations. ParameterDirection. ReturnValue|  
|Adoumums. ParameterDirection. Unknown|  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [CreateParameter-Methode (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)  
    :::column-end:::
    :::column:::
        [Direction-Eigenschaft](../../../ado/reference/ado-api/direction-property.md)  
    :::column-end:::
:::row-end:::
