---
description: State-Eigenschaft (ADO)
title: State-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command25::State
helpviewer_keywords:
- State property [ADO]
ms.assetid: 0b993bac-2653-40b1-bcbb-5b57b6aae2bf
author: rothja
ms.author: jroth
ms.openlocfilehash: ca8a2421f15e5999347b0b7879f3faf707598ba2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441982"
---
# <a name="state-property-ado"></a>State-Eigenschaft (ADO)
Gibt für alle anwendbaren Objekte an, ob der Status des Objekts geöffnet oder geschlossen ist. Wenn das-Objekt eine asynchrone Methode ausführt, gibt an, ob der aktuelle Zustand des Objekts eine Verbindung herstellt, wird ausgeführt oder abgerufen wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen **Long** -Wert zurück, der ein [objectstateenum](../../../ado/reference/ado-api/objectstateenum.md) -Wert sein kann. Der Standardwert ist " **adStatus eclosed**".  
  
## <a name="remarks"></a>Bemerkungen  
 Sie können die **State** -Eigenschaft verwenden, um den aktuellen Status eines bestimmten Objekts zu einem beliebigen Zeitpunkt zu bestimmen.  
  
 Die **State** -Eigenschaft des Objekts kann eine Kombination von Werten aufweisen. Wenn z. b. eine-Anweisung ausgeführt wird, hat diese Eigenschaft den kombinierten Wert **adstateopen** und **adstateausführungs**.  
  
 Die **State** -Eigenschaft ist schreibgeschützt.  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
        [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
    :::column-end:::
    :::column:::
        [Record-Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
        [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
    :::column-end:::
    :::column:::
        [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für ConnectionString, ConnectionTimeout und State Properties (VB)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [Beispiel für ConnectionString, ConnectionTimeout und State Properties (VC + +)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
