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
ms.openlocfilehash: 7eae60dc133734edb666737356a214af5bd9ea8c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444252"
---
# <a name="cursortype-property-ado"></a>CursorType-Eigenschaft (ADO)
Gibt den Typ des Cursors an, der in einem [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt verwendet wird.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen [Cursor typeenum](../../../ado/reference/ado-api/cursortypeenum.md) -Wert fest oder gibt ihn zurück. Der Standardwert ist ' **adOpenForwardOnly**'.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **CursorType** -Eigenschaft, um den Typ des Cursors anzugeben, der beim Öffnen des **Recordset** -Objekts verwendet werden soll.  
  
 Nur eine Einstellung von **adOpenStatic** wird unterstützt, wenn die [Cursor Location](../../../ado/reference/ado-api/cursorlocation-property-ado.md) -Eigenschaft auf **adUseClient**festgelegt ist. Wenn ein nicht unterstützter Wert festgelegt ist, wird kein Fehler ausgegeben. Stattdessen wird der nächste unterstützte **Cursor Type** verwendet.  
  
 Wenn ein Anbieter den angeforderten Cursortyp nicht unterstützt, kann er einen anderen Cursortyp zurückgeben. Die **CursorType** -Eigenschaft ändert sich entsprechend dem tatsächlich verwendeten Cursortyp, wenn das [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt geöffnet ist. Verwenden Sie die [unterstützte](../../../ado/reference/ado-api/supports-method.md) Methode, um bestimmte Funktionen des zurückgegebenen Cursors zu überprüfen. Nachdem Sie das **Recordset**geschlossen haben, wird die ursprüngliche Einstellung der **Cursor Type** -Eigenschaft wieder hergestellt.  
  
 Das folgende Diagramm zeigt die Anbieter Funktionalität (identifiziert durch **unterstützt** Methoden Konstanten), die für jeden Cursortyp erforderlich ist.  
  
|Für ein Recordset dieses Cursor Typs|Die unterstützte Methode muss für alle diese Konstanten true zurückgeben.|  
|----------------------------------------|---------------------------------------------------------------------|  
|**adOpenForwardOnly**|Keine|  
|**adOpenKeyset**|**adbookmark**, **adholdrecords**, **admuveprevious**, **adresync**|  
|**adOpenDynamic**|**admuveprevious**|  
|**adopkostatic**|**adbookmark**, **adholdrecords**, **admuveprevious**, **adresync**|  
  
> [!NOTE]
>  Obwohl **unterstützt**(**adUpdateBatch**) für dynamische und vorwärts gerichtete Cursor true ist, sollten Sie bei Batch Aktualisierungen entweder einen Keyset-oder einen static-Cursor verwenden. Legen Sie die [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) -Eigenschaft auf **adlockbatchoptimiund** die **CursorLocation** -Eigenschaft auf **adUseClient** fest, um den Cursor Dienst für die OLE DB zu aktivieren, die für Batch Aktualisierungen erforderlich ist.  
  
 Die **Cursor Type** -Eigenschaft ist Lese-/Schreibzugriff, wenn das **Recordset** geschlossen ist, und schreibgeschützt, wenn es geöffnet ist.  
  
> [!NOTE]
>  **Verwendung von Remote Datendiensten** Bei Verwendung auf einem Client seitigen **Recordset** -Objekt kann die Eigenschaft " **Cursor Type** " nur auf " **adOpenStatic**" festgelegt werden.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Cursor Type, LockType und EditMode Properties (VB)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vb.md)   
 [Beispiel für Cursor Type, LockType und EditMode Properties (VC + +)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vc.md)   
 [Supports-Methode](../../../ado/reference/ado-api/supports-method.md)
