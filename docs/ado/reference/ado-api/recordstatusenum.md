---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 233b2f84b6a60c7b5162edce6c1b76b63946ae81
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67931285"
---
# <a name="recordstatusenum"></a>RecordStatusEnum
Gibt den [Status](../../../ado/reference/ado-api/status-property-ado-recordset.md) eines Datensatzes in Bezug auf Batch Updates und andere Massen Vorgänge an.  
  
|Dauerhaft|value|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adrecabgeb Rochen**|0x100|Gibt an, dass der Datensatz nicht gespeichert wurde, weil der Vorgang abgebrochen wurde.|  
|**adreccantrelease**|0x400|Gibt an, dass der neue Datensatz nicht gespeichert wurde, weil der vorhandene Datensatz gesperrt war.|  
|**adrecbeizuvorkomm unverletzung**|0x800|Gibt an, dass der Datensatz nicht gespeichert wurde, weil die optimistische Parallelität verwendet wurde.|  
|**adrecdbdeleted**|0x40000|Gibt an, dass der Datensatz bereits aus der Datenquelle gelöscht wurde.|  
|**adrecdeleted**|0x4|Gibt an, dass der Datensatz gelöscht wurde.|  
|**adrecintegrityverletzungs**|0x1000|Gibt an, dass der Datensatz nicht gespeichert wurde, weil der Benutzer die Integritäts Einschränkungen verletzt hat.|  
|**adrecinvalid**|0x10|Gibt an, dass der Datensatz nicht gespeichert wurde, weil sein Lesezeichen ungültig ist.|  
|**adrecmaxchangesexceging**|0x2000|Gibt an, dass der Datensatz nicht gespeichert wurde, weil zu viele ausstehende Änderungen vorhanden sind.|  
|**adrecmodified**|0x2|Gibt an, dass der Datensatz geändert wurde.|  
|**adrecmultiplechanges**|0x40|Gibt an, dass der Datensatz nicht gespeichert wurde, da er sich auf mehrere Datensätze ausgewirkt hätte.|  
|**adrecnew**|0x1|Gibt an, dass der Datensatz neu ist.|  
|**adrecobjectopen**|0x4000|Gibt an, dass der Datensatz aufgrund eines Konflikts mit einem geöffneten Speicher Objekt nicht gespeichert wurde.|  
|**adrecok**|0|Gibt an, dass der Datensatz erfolgreich aktualisiert wurde.|  
|**adrecouto-Memory**|0x8000|Gibt an, dass der Datensatz nicht gespeichert wurde, weil der Computer nicht über genügend Arbeitsspeicher verfügt.|  
|**adrecpdingchanges**|0x80|Gibt an, dass der Datensatz nicht gespeichert wurde, weil er auf einen ausstehenden Einfügevorgang verweist.|  
|**adrecpermissiondenied**|0x10000|Gibt an, dass der Datensatz nicht gespeichert wurde, da der Benutzer nicht über ausreichende Berechtigungen verfügt.|  
|**adrecschemaverletzung**|0x20000|Gibt an, dass der Datensatz nicht gespeichert wurde, weil er gegen die Struktur der zugrunde liegenden Datenbank verstößt.|  
|**adrecunmodified**|0x8|Gibt an, dass der Datensatz nicht geändert wurde.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 AdoEnums.RecordStatus.  
  
 Paket: **com. ms. wfc. Data**  
  
|Dauerhaft|  
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
 [Status-Eigenschaft (ADO-Recordset)](../../../ado/reference/ado-api/status-property-ado-recordset.md)
