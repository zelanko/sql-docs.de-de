---
description: ObjectStateEnum
title: Objectstateaufumum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: f89b433ae7e44b3b90c3a7ef1f8eca4bcd62f5ec
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990381"
---
# <a name="objectstateenum"></a>ObjectStateEnum
Gibt an, ob ein Objekt geöffnet oder geschlossen ist, ob eine Verbindung mit einer Datenquelle hergestellt wird, ob ein Befehl ausgeführt oder Daten abgerufen werden.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adStatus**|0|Gibt an, dass das-Objekt geschlossen ist.|  
|**adstateopen**|1|Gibt an, dass das-Objekt geöffnet ist.|  
|**adstatueconnecting**|2|Gibt an, dass das Objekt eine Verbindung herstellt.|  
|**adstate-Ausführung**|4|Gibt an, dass das Objekt einen Befehl ausführt.|  
|**adstatefeabruf**|8|Gibt an, dass die Zeilen des-Objekts abgerufen werden.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstante|  
|--------------|  
|AdoEnums. ObjectState. Closed|  
|Adoerums. ObjectState. Open|  
|Adoerums. ObjectState. Connecting|  
|AdoEnums.ObjectState.EXE-Kürzung|  
|Adoerums. ObjectState. fetchen|  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [State-Eigenschaft (ADO)](./state-property-ado.md)  
    :::column-end:::
    :::column:::
        [State-Eigenschaft (ADO MD)](../ado-md-api/state-property-ado-md.md)  
    :::column-end:::
:::row-end:::