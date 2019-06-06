---
title: RecordStatusEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RecordStatusEnum
helpviewer_keywords:
- RecordStatusEnum enumeration [ADO]
ms.assetid: 506fdd70-4452-4e83-95d5-c94311988dfa
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 7c57878b73c3c6a20f8dc0a8abd422c12a0446a2
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66711728"
---
# <a name="recordstatusenum"></a>RecordStatusEnum
Gibt an, die [Status](../../../ado/reference/ado-api/status-property-ado-recordset.md) eines Datensatzes in Bezug auf Batch-Updates und andere Massenvorgänge.  
  
|Konstante|Wert|Description|  
|--------------|-----------|-----------------|  
|**adRecCanceled**|0x100|Gibt an, dass der Datensatz wurde nicht gespeichert werden, da der Vorgang abgebrochen wurde.|  
|**adRecCantRelease**|0x400|Gibt an, dass der neue Datensatz nicht gespeichert wurde, da der vorhandene Eintrag gesperrt wurde.|  
|**adRecConcurrencyViolation**|0x800|Gibt an, dass der Datensatz nicht gespeichert werden, wurde da vollständige Parallelität verwendet wurde.|  
|**adRecDBDeleted**|0x40000|Gibt an, dass der Datensatz bereits aus der Datenquelle gelöscht wurde.|  
|**adRecDeleted**|0x4|Gibt an, dass der Datensatz gelöscht wurde.|  
|**adRecIntegrityViolation**|0x1000|Gibt an, dass der Datensatz nicht gespeichert wurde, da der Benutzer die Einschränkungen für die Integrität verletzt wird.|  
|**adRecInvalid**|0x10|Gibt an, dass der Datensatz nicht gespeichert wurde, weil die Lesezeichen ungültig ist.|  
|**adRecMaxChangesExceeded**|0x2000|Gibt an, dass der Datensatz nicht gespeichert wurde, da es zu viele ausstehende Änderungen wurden.|  
|**adRecModified**|0x2|Gibt an, dass der Datensatz geändert wurde.|  
|**adRecMultipleChanges**|0x40|Gibt an, dass der Datensatz wurde nicht gespeichert werden, da es mehrere Datensätze auswirken würde.|  
|**adRecNew**|0x1|Gibt an, dass der Datensatz neu ist.|  
|**adRecObjectOpen**|0x4000|Gibt an, dass der Datensatz nicht aufgrund eines Konflikts mit einem geöffnetes Speicherobjekt gespeichert wurde.|  
|**adRecOK**|0|Gibt an, dass der Datensatz wurde erfolgreich aktualisiert wurde.|  
|**adRecOutOfMemory**|0x8000|Gibt an, dass der Datensatz wurde nicht gespeichert werden, weil nicht genügend Arbeitsspeicher auf dem Computer ausgeführt wurde.|  
|**adRecPendingChanges**|0x80|Gibt an, dass der Datensatz nicht gespeichert werden, wurde weil er auf eine ausstehende Einfügung verweist.|  
|**adRecPermissionDenied**|0x10000|Gibt an, dass der Datensatz nicht gespeichert werden, wurde da der Benutzer nicht über ausreichende Berechtigungen verfügt.|  
|**adRecSchemaViolation**|0x20000|Gibt an, dass der Datensatz nicht gespeichert wurde, weil es die Struktur der zugrunde liegenden Datenbank verletzt.|  
|**adRecUnmodified**|0x8|Gibt an, dass der Datensatz nicht geändert wurde.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 AdoEnums.RecordStatus.  
  
 Package: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.RecordStatus.CANCELED|  
|AdoEnums.RecordStatus.CANTRELEASE|  
|AdoEnums.RecordStatus.CONCURRENCYVIOLATION|  
|AdoEnums.RecordStatus.DBDELETED|  
|AdoEnums.RecordStatus.DELETED|  
|AdoEnums.RecordStatus.INTEGRITYVIOLATION|  
|AdoEnums.RecordStatus.INVALID|  
|AdoEnums.RecordStatus.MAXCHANGESEXCEEDED|  
|AdoEnums.RecordStatus.MODIFIED|  
|AdoEnums.RecordStatus.MULTIPLECHANGES|  
|AdoEnums.RecordStatus.NEW|  
|AdoEnums.RecordStatus.OBJECTOPEN|  
|AdoEnums.RecordStatus.OK|  
|AdoEnums.RecordStatus.OUTOFMEMORY|  
|AdoEnums.RecordStatus.PENDINGCHANGES|  
|AdoEnums.RecordStatus.PERMISSIONDENIED|  
|AdoEnums.RecordStatus.SCHEMAVIOLATION|  
|AdoEnums.RecordStatus.UNMODIFIED|  
  
## <a name="applies-to"></a>Gilt für  
 [Status-Eigenschaft (ADO Recordset)](../../../ado/reference/ado-api/status-property-ado-recordset.md)
