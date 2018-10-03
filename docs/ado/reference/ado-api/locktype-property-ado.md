---
title: LockType-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::LockType
helpviewer_keywords:
- LockType property [ADO]
ms.assetid: 9920c14e-033a-4de1-8149-0ce9737a3246
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 05670439a8f14018a999557dd135912e0c2e0159
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47736018"
---
# <a name="locktype-property-ado"></a>LockType-Eigenschaft (ADO)
Gibt die Typen von Sperren, die auf Datensätze platziert werden, während der Bearbeitung an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen [LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md) Wert. Der Standardwert ist **AdLockReadOnly**.  
  
## <a name="remarks"></a>Hinweise  
 Legen Sie die **LockType** Eigenschaft vor dem Öffnen einer [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) angeben, welche Art von Sperre des Anbieters verwenden soll, beim Öffnen. Lesen die Eigenschaft, um den Typ der Sperre auf eine offene zurückzugeben **Recordset** Objekt.  
  
 Anbieter unterstützen möglicherweise nicht alle Typen von Sperren. Wenn ein Anbieter nicht die angeforderte unterstützt **LockType** festlegen, ersetzen sie einen anderen Typ von Sperren. Um zu bestimmen, die eigentliche Sperre Funktionalität, die in einem **Recordset** -Objekts die [unterstützt](../../../ado/reference/ado-api/supports-method.md) -Methode mit **AdUpdate** und **AdUpdateBatch**.  
  
 Die **AdLockPessimistic** Einstellung wird nicht unterstützt, wenn die [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) -Eigenschaftensatz auf **AdUseClient**. Wenn Sie ein nicht unterstützter Wert festgelegt ist, wird kein Fehler gemeldet. die nächstgelegene unterstützt **LockType** wird stattdessen verwendet.  
  
 Die **LockType** -Eigenschaft ist Lese-/Schreibzugriff bei der **Recordset** geschlossen ist, und schreibgeschützt, wenn es geöffnet ist.  
  
> [!NOTE]
>  **Remote Datendienstnutzung** bei Verwendung für eine clientseitige **Recordset** -Objekt, das **LockType** Eigenschaft kann nur festgelegt werden, um **AdLockBatchOptimistic**.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [CursorType, LockType und EditMode Eigenschaften – Beispiel (VB)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vb.md)   
 [CursorType, LockType und EditMode Eigenschaften – Beispiel (VC++)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vc.md)   
 [CancelBatch-Methode (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [UpdateBatch-Methode](../../../ado/reference/ado-api/updatebatch-method.md)
