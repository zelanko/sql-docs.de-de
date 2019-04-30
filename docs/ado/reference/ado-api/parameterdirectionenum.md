---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 01f423652f32b9afe801ef99e299f65a6a860a8a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63314831"
---
# <a name="parameterdirectionenum"></a>ParameterDirectionEnum
Gibt an, ob die [Parameter](../../../ado/reference/ado-api/parameter-object.md) stellt einen Eingabeparameter, Ausgabeparameter, sowohl einen Eingabe- und ein Output-Parameter oder den Rückgabewert einer gespeicherten Prozedur.  
  
|Konstante|Wert|Description|  
|--------------|-----------|-----------------|  
|**adParamInput**|1|Standard. Gibt an, dass der Parameter einen Eingabeparameter darstellt.|  
|**adParamInputOutput**|3|Gibt an, dass der Parameter einen Eingabe- und Parameter darstellt.|  
|**adParamOutput**|2|Gibt an, dass der Parameter einen Ausgabeparameter darstellt.|  
|**adParamReturnValue**|4|Gibt an, dass der Parameter einen Rückgabewert darstellt.|  
|**adParamUnknown**|0|Gibt an, dass die parameterrichtung unbekannt ist.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Package: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.ParameterDirection.INPUT|  
|AdoEnums.ParameterDirection.INPUTOUTPUT|  
|AdoEnums.ParameterDirection.OUTPUT|  
|AdoEnums.ParameterDirection.RETURNVALUE|  
|AdoEnums.ParameterDirection.UNKNOWN|  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[CreateParameter-Methode (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)|[Direction-Eigenschaft](../../../ado/reference/ado-api/direction-property.md)|
