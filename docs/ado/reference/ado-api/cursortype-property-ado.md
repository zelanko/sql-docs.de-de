---
title: CursorType-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::CursorType
helpviewer_keywords:
- CursorType property [ADO]
ms.assetid: b62c66ca-58d5-430e-9257-eb38c65e48c2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4dc881b96a1e2641d4946340c9462455197f2043
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67919255"
---
# <a name="cursortype-property-ado"></a>CursorType-Eigenschaft (ADO)
Gibt den Typ des Cursors verwendet eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen [CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md) Wert. Der Standardwert ist **AdOpenForwardOnly**.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **CursorType** Eigenschaft, um den Typ des Cursors anzugeben, die verwendet werden soll, beim Öffnen der **Recordset** Objekt.  
  
 Nur die Einstellung **"adOpenStatic"** wird unterstützt, wenn die [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) -Eigenschaftensatz auf **AdUseClient**. Wenn Sie ein nicht unterstützter Wert festgelegt ist, wird kein Fehler gemeldet. die nächstgelegene unterstützt **CursorType** wird stattdessen verwendet.  
  
 Wenn ein Anbieter den angeforderten Cursortyp nicht unterstützt, wird möglicherweise ein anderer Cursortyp zurückgegeben. Die **CursorType** Eigenschaft ändert sich entsprechend des eigentlichen Cursortyps verwendet bei der [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekts geöffnet ist. Um bestimmte Funktionen des zurückgegebenen Cursors zu überprüfen, verwenden die [unterstützt](../../../ado/reference/ado-api/supports-method.md) Methode. Nach dem Schließen der **Recordset**, **CursorType** Eigenschaft auf die ursprüngliche Einstellung zurückgesetzt.  
  
 Das folgende Diagramm zeigt die Anbieterfunktionalität (identifizierte **unterstützt** Methode Konstanten) für jeden Cursortyp erforderlich sind.  
  
|Für ein Recordset mit diesem CursorType|Unterstützt die Methode muss für alle der folgenden Konstanten "true" zurückgeben.|  
|----------------------------------------|---------------------------------------------------------------------|  
|**adOpenForwardOnly**|none|  
|**adOpenKeyset**|**adBookmark**, **adHoldRecords**, **adMovePrevious**, **adResync**|  
|**adOpenDynamic**|**adMovePrevious**|  
|**adOpenStatic**|**adBookmark**, **adHoldRecords**, **adMovePrevious**, **adResync**|  
  
> [!NOTE]
>  Obwohl **unterstützt**(**AdUpdateBatch**) gilt möglicherweise für dynamische und Vorwärts-Cursorn für Batch-updates sollten entweder ein Keyset oder static-Cursor verwenden. Festlegen der [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) Eigenschaft **AdLockBatchOptimistic** und die **CursorLocation** Eigenschaft **AdUseClient** So aktivieren Sie den Cursor Dienst für OLE DB, die für Batch-Updates erforderlich ist.  
  
 Die **CursorType** -Eigenschaft ist Lese-/Schreibzugriff bei der **Recordset** geschlossen ist, und schreibgeschützt, wenn es geöffnet ist.  
  
> [!NOTE]
>  **Remote Datendienstnutzung** bei Verwendung für eine clientseitige **Recordset** -Objekt, das **CursorType** Eigenschaft kann nur festgelegt werden **"adOpenStatic"** .  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [CursorType, LockType und EditMode Eigenschaften – Beispiel (VB)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vb.md)   
 [CursorType, LockType und EditMode Eigenschaften – Beispiel (VC++)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vc.md)   
 [Supports-Methode](../../../ado/reference/ado-api/supports-method.md)
