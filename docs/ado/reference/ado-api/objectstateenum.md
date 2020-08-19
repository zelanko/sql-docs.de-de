---
description: ObjectStateEnum
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 0c387240e36225f03c8ba1287618ab59a98fb63c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443022"
---
# <a name="objectstateenum"></a>ObjectStateEnum
Gibt an, ob ein Objekt geöffnet oder geschlossen ist, ob eine Verbindung mit einer Datenquelle hergestellt wird, ob ein Befehl ausgeführt oder Daten abgerufen werden.  
  
|Konstant|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adStatus**|0|Gibt an, dass das-Objekt geschlossen ist.|  
|**adstateopen**|1|Gibt an, dass das-Objekt geöffnet ist.|  
|**adstatueconnecting**|2|Gibt an, dass das Objekt eine Verbindung herstellt.|  
|**adstate-Ausführung**|4|Gibt an, dass das Objekt einen Befehl ausführt.|  
|**adstatefeabruf**|8|Gibt an, dass die Zeilen des-Objekts abgerufen werden.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstant|  
|--------------|  
|AdoEnums. ObjectState. Closed|  
|Adoerums. ObjectState. Open|  
|Adoerums. ObjectState. Connecting|  
|AdoEnums.ObjectState.EXE-Kürzung|  
|Adoerums. ObjectState. fetchen|  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [State-Eigenschaft (ADO)](../../../ado/reference/ado-api/state-property-ado.md)  
    :::column-end:::
    :::column:::
        [State-Eigenschaft (ADO MD)](../../../ado/reference/ado-md-api/state-property-ado-md.md)  
    :::column-end:::
:::row-end:::
