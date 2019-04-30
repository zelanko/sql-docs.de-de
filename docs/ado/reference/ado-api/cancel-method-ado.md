---
title: Cancel-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::Cancel
- _Record::Cancel
- _Connection::Cancel
- Command25::Cancel
- _Stream::Cancel
helpviewer_keywords:
- Cancel method [ADO]
ms.assetid: e0db4e15-6787-41e2-8f13-9e9b524d620a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9723b28ff56f4fe8eced52cecc43d58921d101e9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63239816"
---
# <a name="cancel-method-ado"></a>Cancel-Methode (ADO)
Bricht einen ausstehenden asynchronen Methodenaufruf Ausführung ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.Cancel  
```  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **Abbrechen** Methode, um die Ausführung eines asynchronen Methodenaufrufs beendet: d. h. eine Methode aufgerufen, mit der **AdAsyncConnect**, **AdAsyncExecute**, oder **AdAsyncFetch** Option.  
  
 Die folgende Tabelle zeigt, welcher Task beendet wird, bei der Verwendung der **Abbrechen** Methode für einen bestimmten Typ des Objekts.  
  
|Wenn *Objekt* ist ein|Der letzte asynchrone Aufruf dieser Methode wird beendet.|  
|----------------------|-------------------------------------------------------------|  
|[Befehl](../../../ado/reference/ado-api/command-object-ado.md)|[Ausführen](../../../ado/reference/ado-api/execute-method-ado-command.md)|  
|[Verbindung](../../../ado/reference/ado-api/connection-object-ado.md)|[Führen Sie](../../../ado/reference/ado-api/execute-method-ado-connection.md) oder [öffnen](../../../ado/reference/ado-api/open-method-ado-connection.md)|  
|[Record](../../../ado/reference/ado-api/record-object-ado.md)|[CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md), [DeleteRecord](../../../ado/reference/ado-api/deleterecord-method-ado.md), [MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md), oder [öffnen](../../../ado/reference/ado-api/open-method-ado-record.md)|  
|[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)|[Datei](../../../ado/reference/ado-api/open-method-ado-recordset.md)|  
|[Stream](../../../ado/reference/ado-api/stream-object-ado.md)|[Datei](../../../ado/reference/ado-api/open-method-ado-stream.md)|  
  
## <a name="applies-to"></a>Gilt für  
  
||||  
|-|-|-|  
|[Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Record-Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|  
|[Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)||  
  
## <a name="see-also"></a>Siehe auch  
 [Cancel – Methodenbeispiel (VB)](../../../ado/reference/ado-api/cancel-method-example-vb.md)   
 [Cancel – Methodenbeispiel (VBScript)](../../../ado/reference/rds-api/cancel-method-example-vbscript.md)   
 [Cancel – Methodenbeispiel (VC++)](../../../ado/reference/ado-api/cancel-method-example-vc.md)   
 [Cancel-Methode (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [CancelBatch-Methode (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [CancelUpdate-Methode (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [CancelUpdate-Methode (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Execute-Methode (ADO-Befehl)](../../../ado/reference/ado-api/execute-method-ado-command.md)   
 [Execute-Methode (ADO Connection)](../../../ado/reference/ado-api/execute-method-ado-connection.md)   
 [Open Sie-Methode (ADO Connection)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open-Methode (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)
