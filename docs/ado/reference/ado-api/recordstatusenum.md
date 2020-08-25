---
description: RecordStatusEnum
title: RecordStatus usenum | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 57edf327f2ba4661ba47f43cf8b2f128b9fe92ab
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88772129"
---
# <a name="recordstatusenum"></a>RecordStatusEnum
Gibt den [Status](./status-property-ado-recordset.md) eines Datensatzes in Bezug auf Batch Updates und andere Massen Vorgänge an.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adRecCanceled**|0x100|Gibt an, dass der Datensatz nicht gespeichert wurde, weil der Vorgang abgebrochen wurde.|  
|**adRecCantRelease**|0x400|Gibt an, dass der neue Datensatz nicht gespeichert wurde, weil der vorhandene Datensatz gesperrt war.|  
|**adRecConcurrencyViolation**|0x800|Gibt an, dass der Datensatz nicht gespeichert wurde, weil die optimistische Parallelität verwendet wurde.|  
|**adRecDBDeleted**|0x40000|Gibt an, dass der Datensatz bereits aus der Datenquelle gelöscht wurde.|  
|**adRecDeleted**|0x4|Gibt an, dass der Datensatz gelöscht wurde.|  
|**adRecIntegrityViolation**|0x1000|Gibt an, dass der Datensatz nicht gespeichert wurde, weil der Benutzer die Integritäts Einschränkungen verletzt hat.|  
|**adRecInvalid**|0x10|Gibt an, dass der Datensatz nicht gespeichert wurde, weil sein Lesezeichen ungültig ist.|  
|**adRecMaxChangesExceeded**|0x2000|Gibt an, dass der Datensatz nicht gespeichert wurde, weil zu viele ausstehende Änderungen vorhanden sind.|  
|**adRecModified**|0x2|Gibt an, dass der Datensatz geändert wurde.|  
|**adRecMultipleChanges**|0x40|Gibt an, dass der Datensatz nicht gespeichert wurde, da er sich auf mehrere Datensätze ausgewirkt hätte.|  
|**adRecNew**|0x1|Gibt an, dass der Datensatz neu ist.|  
|**adRecObjectOpen**|0x4000|Gibt an, dass der Datensatz aufgrund eines Konflikts mit einem geöffneten Speicher Objekt nicht gespeichert wurde.|  
|**adRecOK**|0|Gibt an, dass der Datensatz erfolgreich aktualisiert wurde.|  
|**adRecOutOfMemory**|0x8000|Gibt an, dass der Datensatz nicht gespeichert wurde, weil der Computer nicht über genügend Arbeitsspeicher verfügt.|  
|**adRecPendingChanges**|0x80|Gibt an, dass der Datensatz nicht gespeichert wurde, weil er auf einen ausstehenden Einfügevorgang verweist.|  
|**adRecPermissionDenied**|0x10000|Gibt an, dass der Datensatz nicht gespeichert wurde, da der Benutzer nicht über ausreichende Berechtigungen verfügt.|  
|**adRecSchemaViolation**|0x20000|Gibt an, dass der Datensatz nicht gespeichert wurde, weil er gegen die Struktur der zugrunde liegenden Datenbank verstößt.|  
|**adRecUnmodified**|0x8|Gibt an, dass der Datensatz nicht geändert wurde.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 AdoEnums.RecordStatus.  
  
 Paket: **com. ms. wfc. Data**  
  
|Konstante|  
|--------------|  
|AdoEnums.RecordStatus.CANCELED|  
|AdoEnums.RecordStatus.CANTRELEASE|  
|Adoerums. RecordStatus. zustandscyverletzungs|  
|AdoEnums.RecordStatus.DBDELETED|  
|AdoEnums.RecordStatus.DELETED|  
|AdoEnums.RecordStatus.INTEGRITYVIOLATION|  
|AdoEnums.RecordStatus.INVALID|  
|Adoerums. RecordStatus. maxchangesexcegetretenen|  
|AdoEnums.RecordStatus.MODIFIED|  
|Adoerums. RecordStatus. multiplechanges|  
|AdoEnums.RecordStatus.NEW|  
|Adoerums. RecordStatus. objectopen|  
|Adoerums. RecordStatus. OK|  
|Adoerums. RecordStatus. oudefmemory|  
|Adoerums. RecordStatus. pdingchanges|  
|AdoEnums.RecordStatus.PERMISSIONDENIED|  
|AdoEnums.RecordStatus.SCHEMAVIOLATION|  
|AdoEnums.RecordStatus.UNMODIFIED|  
  
## <a name="applies-to"></a>Gilt für  
 [Status-Eigenschaft (ADO-Recordset)](./status-property-ado-recordset.md)