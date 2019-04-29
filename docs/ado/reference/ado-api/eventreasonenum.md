---
title: EventReasonEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EventReasonEnum
helpviewer_keywords:
- EventReasonEnum enumeration [ADO]
ms.assetid: 7d4a5496-ec2d-4936-b36a-7049a82be4b4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 743e36e379760cb2c148c5484bb7b49b08d1d27e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63070854"
---
# <a name="eventreasonenum"></a>EventReasonEnum
Gibt den Grund für der Eintreten ein Ereignisses verursacht hat.  
  
|Konstante|Wert|Description|  
|--------------|-----------|-----------------|  
|**adRsnAddNew**|1|Ein Vorgang hinzugefügt, einen neuen Datensatz.|  
|**adRsnClose**|9|Ein Vorgang geschlossen der **Recordset**.|  
|**adRsnDelete**|2|Ein Vorgang wird einen Datensatz gelöscht.|  
|**adRsnFirstChange**|11|Ein Vorgang versucht die erste Änderung, einen Datensatz an.|  
|**adRsnMove**|10|Ein Vorgang verschoben, die Zeiger für den Datensatz in die **Recordset**.|  
|**adRsnMoveFirst**|12|Ein Vorgang verschoben Zeiger für den Datensatz auf den ersten Eintrag in der **Recordset**.|  
|**adRsnMoveLast**|15|Ein Vorgang verschoben den Datensatzzeiger der letzte Datensatz in die **Recordset**.|  
|**adRsnMoveNext**|13|Ein Vorgang verschoben Zeiger für den Datensatz auf den nächsten Datensatz in die **Recordset**.|  
|**adRsnMovePrevious**|14|Ein Vorgang verliert den Datensatzzeiger zum vorherigen Datensatz in die **Recordset**.|  
|**adRsnRequery**|7|Ein Vorgang erneut abgefragt der [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).|  
|**adRsnResynch**|8|Ein Vorgang synchronisiert die **Recordset** mit der Datenbank.|  
|**adRsnUndoAddNew**|5|Ein Vorgang rückgängig gemacht, das Hinzufügen eines neuen Datensatzes.|  
|**adRsnUndoDelete**|6|Ein Vorgang rückgängig gemacht, das Löschen eines Datensatzes.|  
|**adRsnUndoUpdate**|4|Ein Vorgang rückgängig gemacht, die Aktualisierung eines Datensatzes.|  
|**adRsnUpdate**|3|Ein Vorgang aktualisiert einen vorhandenen Datensatz.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Package: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.EventReason.ADDNEW|  
|AdoEnums.EventReason.CLOSE|  
|AdoEnums.EventReason.DELETE|  
|AdoEnums.EventReason.FIRSTCHANGE|  
|AdoEnums.EventReason.MOVE|  
|AdoEnums.EventReason.MOVEFIRST|  
|AdoEnums.EventReason.MOVELAST|  
|AdoEnums.EventReason.MOVENEXT|  
|AdoEnums.EventReason.MOVEPREVIOUS|  
|AdoEnums.EventReason.REQUERY|  
|AdoEnums.EventReason.RESYNCH|  
|AdoEnums.EventReason.UNDOADDNEW|  
|AdoEnums.EventReason.UNDODELETE|  
|AdoEnums.EventReason.UNDOUPDATE|  
|AdoEnums.EventReason.UPDATE|  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[WillChangeRecord- und RecordChangeComplete-Ereignis (ADO)](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|[WillChangeRecordset- und RecordsetChangeComplete-Ereignis (ADO)](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|  
|[WillMove- und MoveComplete-Ereignis (ADO)](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)||
