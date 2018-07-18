---
title: DISCOVER_LOCKS-Rowset | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7f0b52b875793df4074e9feb4e0cc1737224a901
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34031761"
---
# <a name="discoverlocks-rowset"></a>DISCOVER_LOCKS-Rowset
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Stellt Informationen über die aktuellen Sperren auf dem Server bereit.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Das **DISCOVER_LOCKS** -Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|**LOCK_CREATION_TIME**|**DBTYPE_DBTIMESTAMP**||Die UTC-Serverzeit zum Zeitpunkt der Anforderung der Sperre.|  
|**LOCK_GRANT_TIME**|**DBTYPE_DBTIMESTAMP**||Die UTC-Serverzeit zum Zeitpunkt der Zuweisung der Sperre auf der Ressource.|  
|**LOCK_ID**|**DBTYPE_GUID**||Der eindeutige Bezeichner der Sperre als GUID.|  
|**LOCK_OBJECT_ID**|**DBTYPE_WSTR**||Der eindeutige Bezeichner des gesperrten Objekts.|  
|**LOCK_STATUS**|**DBTYPE_I4**||Der Status der Sperre:<br /><br /> 0 bedeutet "Warte auf Sperrung des Objekts".<br /><br /> 1 bedeutet "Sperre zugewiesen".|  
|**LOCK_TRANSACTION_ID**|**DBTYPE_GUID**||Der eindeutige Bezeichner der Transaktion als GUID.|  
|**LOCK_TYPE**|**DBTYPE_I4**||Eine Bitmaske von Sperrentypen. Weitere Informationen finden Sie im Abschnitt "Hinweise" in diesem Thema.|  
|**SPID**|**DBTYPE_I4**||Die Sitzungs-ID.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Das **DISCOVER_LOCKS** -Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|SPID|DBTYPE_I4|Optional.|  
|LOCK_TRANSACTION_ID|DBTYPE_GUID|Optional.|  
|LOCK_OBJECT_ID|DBTYPE_WSTR|Optional.|  
|LOCK_STATUS|DBTYPE_I4|Optional.|  
|LOCK_TYPE|DBTYPE_I4|Optional.|  
|LOCK_MIN_TOTAL_MS|DBTYPE_I8|Optional.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="lock-types"></a>Typen von Sperren  
  
|Name der Sperre|Wert|Description|  
|---------------|-----------|-----------------|  
|LOCK_NONE|0x0000000|Keine Sperre.|  
|LOCK_SESSION_LOCK|0x0000001|Inaktive Sitzung, führt nicht zu Einschränkungen von anderen Sperren.|  
|LOCK_READ|0x0000002|Lesesperre während der Verarbeitung.|  
|LOCK_WRITE|0x0000004|Schreibsperre während der Verarbeitung.|  
|LOCK_COMMIT_READ|0x0000008|Commitsperre, freigegeben.|  
|LOCK_COMMIT_WRITE|0x0000010|Commitsperre, exklusiv.|  
|LOCK_COMMIT_ABORTABLE|0x0000020|Bricht einen Commitvorgang ab.|  
|LOCK_COMMIT_INPROGRESS|0x0000040|Commit wird ausgeführt.|  
|LOCK_INVALID|0x0000080|Ungültige Sperre.|  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis-Schemarowsets](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
