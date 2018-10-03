---
title: FilterGroupEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FilterGroupEnum
helpviewer_keywords:
- FilterGroupEnum enumeration [ADO]
ms.assetid: b22e725e-84bd-4286-a070-290c278c3783
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7c200e1ed569db288d92a6322cba2adc5c00f7c7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47649818"
---
# <a name="filtergroupenum"></a>FilterGroupEnum
Gibt die Gruppe von Datensätzen, die von gefiltert werden eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Konstante|value|Description|  
|--------------|-----------|-----------------|  
|**adFilterAffectedRecords**|2|Filter für die Anzeige von nur Datensätze, die von der letzten betroffen [löschen](../../../ado/reference/ado-api/delete-method-ado-recordset.md), [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), oder [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) aufrufen.|  
|**adFilterConflictingRecords**|5|Die Filter zum Anzeigen der Datensätze, die Fehler bei der letzten Batchaktualisierung.|  
|**adFilterFetchedRecords**|3|Filter zum Anzeigen der Datensätze im aktuellen Cache – d. h. die Ergebnisse der dem letzten Aufruf von Datensätzen aus der Datenbank abzurufen.|  
|**adFilterNone**|0|Entfernt den aktuellen Filter und alle Datensätze für die Anzeige wiederhergestellt.|  
|**adFilterPendingRecords**|1|Filter für das Anzeigen von Datensätzen, die geändert haben, aber noch nicht an den Server gesendet wurden. Gilt nur für den Modus "Batch-Update".|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Paket: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.FilterGroup.AFFECTEDRECORDS|  
|AdoEnums.FilterGroup.CONFLICTINGRECORDS|  
|AdoEnums.FilterGroup.FETCHEDRECORDS|  
|AdoEnums.FilterGroup.NONE|  
|AdoEnums.FilterGroup.PENDINGRECORDS|  
  
## <a name="applies-to"></a>Gilt für  
 [Filter-Eigenschaft](../../../ado/reference/ado-api/filter-property.md)
