---
title: DISCOVER_JOBS-Rowset | Microsoft-Dokumentation
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
- DISCOVER_JOBS rowset
ms.assetid: b4d83bb6-aed3-4513-b516-cefadf95dad2
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6a23a3e3dae0a03bf31a7b73b8cb505e834cff27
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37246060"
---
# <a name="discoverjobs-rowset"></a>DISCOVER_JOBS-Rowset
  Stellt Informationen über die aktiven Aufträge bereit, die auf dem Server ausgeführt werden. Ein Auftrag ist ein Teil eines Befehls, der für den Befehl einen bestimmten Task ausführt.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DISCOVER_JOBS` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`JOB_CREATION_TIME`|`DBTYPE_DBTIMESTAMP`||UTC-Datum und -Zeit des Servers, zu denen der Auftrag erstellt wurde.|  
|`JOB_DESCRIPTION`|`DBTYPE_WSTR`||Die vom Serverdienst zugeordnete Auftragsbeschreibung.|  
|`JOB_EXECUTION_TIME_MS`|`DBTYPE_I8`||Die Zeit in Millisekunden, die der Auftrag aktiv ist.|  
|`JOB_ID`|`DBTYPE_I4`||Der eindeutige Bezeichner des Auftrags.|  
|`JOB_START_TIME`|`DBTYPE_DBTIMESTAMP`||UTC-Datum und -Zeit des Servers, zu denen der Auftrag gestartet wurde.|  
|`JOB_THREADPOOL_ID`|`DBTYPE_I4`||Der Threadpool, aus dem der aktuelle Auftrag gestartet wurde.|  
|`JOB_TOTAL_TIME_MS`|`DBTYPE_I8`||Die Zeit in Millisekunden, seit der der Auftrag gestartet wurde.|  
|`SPID`|`DBTYPE_I4`||Die Sitzungs-ID.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `DISCOVER_JOBS` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|SPID|DBTYPE_I4|Optional.|  
|JOB_ID|DBTYPE_I4|Optional.|  
|JOB_DESCRIPTION|DBTYPE_WSTR|Optional.|  
|JOB_THREADPOOL_ID|DBTYPE_I4|Optional.|  
|JOB_MIN TOTAL_TIME_MS|DBTYPE_I8|Optional.|  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis – Schemarowsets](xml-for-analysis-schema-rowsets.md)  
  
  
