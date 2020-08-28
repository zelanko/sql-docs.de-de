---
description: CursorLocation-Eigenschaft (ADO)
title: Cursor Location-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::CursorLocation
- Recordset15::CursorLocation
helpviewer_keywords:
- CursorLocation property [ADO]
ms.assetid: 39c8d86e-7ee9-4182-be5e-aad5ce952f84
author: rothja
ms.author: jroth
ms.openlocfilehash: 121aeef137946152a82808c8a439f2e5d03a2c94
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88974461"
---
# <a name="cursorlocation-property-ado"></a>CursorLocation-Eigenschaft (ADO)
Gibt den Speicherort des Cursor Dienstanbieter an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Long** -Wert fest, der auf einen der [Cursor](./cursorlocationenum.md) -Werte festgelegt werden kann, oder gibt ihn zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Eigenschaft ermöglicht Ihnen die Auswahl zwischen verschiedenen Cursor Bibliotheken, auf die der Anbieter zugreifen kann. Normalerweise können Sie zwischen der Verwendung einer Client seitigen Cursor Bibliothek oder einer Client seitigen Cursor Bibliothek wählen, die sich auf dem Server befindet.  
  
 Diese Eigenschafts Einstellung wirkt sich auf Verbindungen aus, die erst nach dem Festlegen der Eigenschaft hergestellt wurden. Das Ändern der **Cursor Location** -Eigenschaft hat keine Auswirkungen auf vorhandene Verbindungen.  
  
 Von der [Execute](./execute-method-ado-connection.md) -Methode zurückgegebene Cursor erben diese Einstellung. **Recordset** -Objekte erben diese Einstellung automatisch von ihren zugeordneten Verbindungen.  
  
 Diese Eigenschaft ist für eine [Verbindung](./connection-object-ado.md) oder ein geschlossenes [Recordset](./recordset-object-ado.md)mit Lese-/Schreibzugriff versehen und ist für ein offenes **Recordset**schreibgeschützt.  
  
> [!NOTE]
>  **Verwendung von Remote Datendiensten** Bei Verwendung in einem Client seitigen **Recordset** oder **Verbindungs** Objekt kann die **Cursor Location** -Eigenschaft nur auf **adUseClient**festgelegt werden.  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Connection-Objekt (ADO)](./connection-object-ado.md)  
    :::column-end:::
    :::column:::
        [Recordset-Objekt (ADO)](./recordset-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen  
 [Anhang A: Anbieter](../../guide/appendixes/appendix-a-providers.md)