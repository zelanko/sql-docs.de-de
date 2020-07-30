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
author: rothja
ms.author: jroth
ms.openlocfilehash: 25b6de609d286847fe7458353203dd7f4b9c7b4b
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242426"
---
# <a name="cancel-method-ado"></a>Cancel-Methode (ADO)
Bricht die Ausführung eines ausstehenden asynchronen Methoden Aufrufes ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.Cancel  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **Cancel** -Methode, um die Ausführung eines asynchronen Methoden Aufrufs zu beenden, d. h. eine Methode, die mit der Option **adasyncconnect**, **adAsyncExecute**oder **adasyncfetch** aufgerufen wird.  
  
 In der folgenden Tabelle wird gezeigt, welche Aufgabe beendet wird, wenn Sie die **Cancel** -Methode für einen bestimmten Objekttyp verwenden.  
  
|Wenn das *Objekt* ein|Der letzte asynchrone Aufrufe dieser Methode wird beendet.|  
|----------------------|-------------------------------------------------------------|  
|[Befehl](../../../ado/reference/ado-api/command-object-ado.md)|[Auszuführen](../../../ado/reference/ado-api/execute-method-ado-command.md)|  
|[Connection](../../../ado/reference/ado-api/connection-object-ado.md)|[Ausführen](../../../ado/reference/ado-api/execute-method-ado-connection.md) oder [Öffnen](../../../ado/reference/ado-api/open-method-ado-connection.md)|  
|[Datensatz](../../../ado/reference/ado-api/record-object-ado.md)|[CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md), [DeleteRecord](../../../ado/reference/ado-api/deleterecord-method-ado.md), [muverecord](../../../ado/reference/ado-api/moverecord-method-ado.md)oder [Open](../../../ado/reference/ado-api/open-method-ado-record.md)|  
|[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)|[Öffnen](../../../ado/reference/ado-api/open-method-ado-recordset.md)|  
|[Stream](../../../ado/reference/ado-api/stream-object-ado.md)|[Öffnen](../../../ado/reference/ado-api/open-method-ado-stream.md)|  
  
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
 [Cancel-Methode (Beispiel) (VB)](../../../ado/reference/ado-api/cancel-method-example-vb.md)   
 [Cancel-Methode (Beispiel) (VBScript)](../../../ado/reference/rds-api/cancel-method-example-vbscript.md)   
 [Beispiel für eine Abbruch Methode (VC + +)](../../../ado/reference/ado-api/cancel-method-example-vc.md)   
 [Cancel-Methode (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [CancelBatch-Methode (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [CancelUpdate-Methode (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [CancelUpdate-Methode (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Execute-Methode (ADO-Befehl)](../../../ado/reference/ado-api/execute-method-ado-command.md)   
 [Execute-Methode (ADO-Verbindung)](../../../ado/reference/ado-api/execute-method-ado-connection.md)   
 [Open-Methode (ADO-Verbindung)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open-Methode (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)
