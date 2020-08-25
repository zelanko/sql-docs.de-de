---
description: CursorType-Eigenschaft (ADO)
title: Cursor Type-Eigenschaft (ADO) | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: a85bb0f624c5f5a3100bfba5d33d63a574fa9d0e
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88775499"
---
# <a name="cursortype-property-ado"></a>CursorType-Eigenschaft (ADO)
Gibt den Typ des Cursors an, der in einem [Recordset](./recordset-object-ado.md) -Objekt verwendet wird.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen [Cursor typeenum](./cursortypeenum.md) -Wert fest oder gibt ihn zurück. Der Standardwert ist ' **adOpenForwardOnly**'.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **CursorType** -Eigenschaft, um den Typ des Cursors anzugeben, der beim Öffnen des **Recordset** -Objekts verwendet werden soll.  
  
 Nur eine Einstellung von **adOpenStatic** wird unterstützt, wenn die [Cursor Location](./cursorlocation-property-ado.md) -Eigenschaft auf **adUseClient**festgelegt ist. Wenn ein nicht unterstützter Wert festgelegt ist, wird kein Fehler ausgegeben. Stattdessen wird der nächste unterstützte **Cursor Type** verwendet.  
  
 Wenn ein Anbieter den angeforderten Cursortyp nicht unterstützt, kann er einen anderen Cursortyp zurückgeben. Die **CursorType** -Eigenschaft ändert sich entsprechend dem tatsächlich verwendeten Cursortyp, wenn das [Recordset](./recordset-object-ado.md) -Objekt geöffnet ist. Verwenden Sie die [unterstützte](./supports-method.md) Methode, um bestimmte Funktionen des zurückgegebenen Cursors zu überprüfen. Nachdem Sie das **Recordset**geschlossen haben, wird die ursprüngliche Einstellung der **Cursor Type** -Eigenschaft wieder hergestellt.  
  
 Das folgende Diagramm zeigt die Anbieter Funktionalität (identifiziert durch **unterstützt** Methoden Konstanten), die für jeden Cursortyp erforderlich ist.  
  
|Für ein Recordset dieses Cursor Typs|Die unterstützte Methode muss für alle diese Konstanten true zurückgeben.|  
|----------------------------------------|---------------------------------------------------------------------|  
|**adOpenForwardOnly**|none|  
|**adOpenKeyset**|**adbookmark**, **adholdrecords**, **admuveprevious**, **adresync**|  
|**adOpenDynamic**|**admuveprevious**|  
|**adopkostatic**|**adbookmark**, **adholdrecords**, **admuveprevious**, **adresync**|  
  
> [!NOTE]
>  Obwohl **unterstützt**(**adUpdateBatch**) für dynamische und vorwärts gerichtete Cursor true ist, sollten Sie bei Batch Aktualisierungen entweder einen Keyset-oder einen static-Cursor verwenden. Legen Sie die [LockType](./locktype-property-ado.md) -Eigenschaft auf **adlockbatchoptimiund** die **CursorLocation** -Eigenschaft auf **adUseClient** fest, um den Cursor Dienst für die OLE DB zu aktivieren, die für Batch Aktualisierungen erforderlich ist.  
  
 Die **Cursor Type** -Eigenschaft ist Lese-/Schreibzugriff, wenn das **Recordset** geschlossen ist, und schreibgeschützt, wenn es geöffnet ist.  
  
> [!NOTE]
>  **Verwendung von Remote Datendiensten** Bei Verwendung auf einem Client seitigen **Recordset** -Objekt kann die Eigenschaft " **Cursor Type** " nur auf " **adOpenStatic**" festgelegt werden.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Cursor Type, LockType und EditMode Properties (VB)](./cursortype-locktype-and-editmode-properties-example-vb.md)   
 [Beispiel für Cursor Type, LockType und EditMode Properties (VC + +)](./cursortype-locktype-and-editmode-properties-example-vc.md)   
 [Supports-Methode](./supports-method.md)