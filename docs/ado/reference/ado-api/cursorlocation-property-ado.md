---
title: CursorLocation-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3860434236f5a0751ddb857c6b8bce1cf54d19ac
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63308690"
---
# <a name="cursorlocation-property-ado"></a>CursorLocation-Eigenschaft (ADO)
Gibt die Position des Cursordiensts.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **lange** -Wert, der auf eine der festgelegt werden kann die [CursorLocationEnum](../../../ado/reference/ado-api/cursorlocationenum.md) Werte.  
  
## <a name="remarks"></a>Hinweise  
 Diese Eigenschaft können Sie zwischen verschiedenen Cursorbibliotheken, die an den Anbieter zugegriffen werden kann. Sie können in der Regel zwischen der Verwendung einer clientseitigen Cursor-Bibliothek oder eine, die sich befindet, auf dem Server.  
  
 Die Einstellung dieser Eigenschaft wirkt sich auf Verbindungen nur, nachdem Sie die Eigenschaft festgelegt wurde. Ändern der **CursorLocation** Eigenschaft hat keine Auswirkungen auf vorhandene Verbindungen.  
  
 Cursor, die zurückgegeben werden, indem die [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) Methode erben diese Einstellung. **Recordset** Objekte erben diese Einstellung automatisch aus ihren zugeordneten Verbindungen.  
  
 Diese Eigenschaft ist Lese-/Schreibzugriff auf eine [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) oder ein geschlossenes [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), und auf einem geöffneten schreibgeschützt **Recordset**.  
  
> [!NOTE]
>  **Remote Datendienstnutzung** bei Verwendung für eine clientseitige **Recordset** oder **Verbindung** -Objekt, das **CursorLocation** Eigenschaft kann nur festgelegt werden, um **AdUseClient**.  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Anhang A: Anbieter](../../../ado/guide/appendixes/appendix-a-providers.md)
