---
title: DISCOVER_LOCKS-Rowset | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- DISCOVER_LOCKS rowset
ms.assetid: dea48167-212c-40b7-a416-434042a1b697
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4458d9dac98fd35d54ff35c0d1d524a92b576ba5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37167597"
---
# <a name="discoverlocks-rowset"></a>DISCOVER_LOCKS-Rowset
  Stellt Informationen über die aktuellen Sperren auf dem Server bereit.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DISCOVER_LOCKS` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`LOCK_CREATION_TIME`|`DBTYPE_DBTIMESTAMP`||Die UTC-Serverzeit zum Zeitpunkt der Anforderung der Sperre.|  
|`LOCK_GRANT_TIME`|`DBTYPE_DBTIMESTAMP`||Die UTC-Serverzeit zum Zeitpunkt der Zuweisung der Sperre auf der Ressource.|  
|`LOCK_ID`|`DBTYPE_GUID`||Der eindeutige Bezeichner der Sperre als GUID.|  
|`LOCK_OBJECT_ID`|`DBTYPE_WSTR`||Der eindeutige Bezeichner des gesperrten Objekts.|  
|`LOCK_STATUS`|`DBTYPE_I4`||Der Status der Sperre:<br /><br /> 0 bedeutet "Warte auf Sperrung des Objekts".<br /><br /> 1 bedeutet "Sperre zugewiesen".|  
|`LOCK_TRANSACTION_ID`|`DBTYPE_GUID`||Der eindeutige Bezeichner der Transaktion als GUID.|  
|`LOCK_TYPE`|`DBTYPE_I4`||Eine Bitmaske von Sperrentypen. Weitere Informationen finden Sie im Abschnitt "Hinweise" in diesem Thema.|  
|`SPID`|`DBTYPE_I4`||Die Sitzungs-ID.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `DISCOVER_LOCKS` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
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
  
|Name der Sperre|value|Description|  
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
 [XML for Analysis – Schemarowsets](xml-for-analysis-schema-rowsets.md)  
  
  
