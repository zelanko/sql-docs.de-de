---
title: Objectstateaufumum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ObjectStateEnum
helpviewer_keywords:
- ObjectStateEnum enumeration [ADO]
ms.assetid: 32746558-097b-4749-989e-519aadf7e3f4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 708d146aaa40d873e0a519c860a047d4b1f93161
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67931927"
---
# <a name="objectstateenum"></a>ObjectStateEnum
Gibt an, ob ein Objekt geöffnet oder geschlossen ist, ob eine Verbindung mit einer Datenquelle hergestellt wird, ob ein Befehl ausgeführt oder Daten abgerufen werden.  
  
|Dauerhaft|value|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adStatus**|0|Gibt an, dass das-Objekt geschlossen ist.|  
|**adstateopen**|1|Gibt an, dass das-Objekt geöffnet ist.|  
|**adstatueconnecting**|2|Gibt an, dass das Objekt eine Verbindung herstellt.|  
|**adstate-Ausführung**|4|Gibt an, dass das Objekt einen Befehl ausführt.|  
|**adstatefeabruf**|8|Gibt an, dass die Zeilen des-Objekts abgerufen werden.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Dauerhaft|  
|--------------|  
|AdoEnums. ObjectState. Closed|  
|Adoerums. ObjectState. Open|  
|Adoerums. ObjectState. Connecting|  
|Adoerums. ObjectState. wird ausgeführt|  
|Adoerums. ObjectState. fetchen|  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[State-Eigenschaft (ADO MD)](../../../ado/reference/ado-md-api/state-property-ado-md.md)|[State-Eigenschaft (ADO)](../../../ado/reference/ado-api/state-property-ado.md)|
