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
author: rothja
ms.author: jroth
ms.openlocfilehash: 88754f7dbd0064c765314d88b0fcc0d06f05bbb2
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763401"
---
# <a name="parameterdirectionenum"></a>ParameterDirectionEnum
Gibt an, ob der [Parameter](../../../ado/reference/ado-api/parameter-object.md) einen Eingabeparameter, einen Ausgabeparameter, einen Eingabe-und einen Output-Parameter oder den Rückgabewert einer gespeicherten Prozedur darstellt.  
  
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
  
|||  
|-|-|  
|[CreateParameter-Methode (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)|[Direction-Eigenschaft](../../../ado/reference/ado-api/direction-property.md)|
