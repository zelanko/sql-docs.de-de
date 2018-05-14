---
title: DISCOVER_JOBS-Rowset | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e9d0d836d8fe44041aa541d71d86be327647dab9
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="discoverjobs-rowset"></a>DISCOVER_JOBS-Rowset
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Stellt Informationen über die aktiven Aufträge bereit, die auf dem Server ausgeführt werden. Ein Auftrag ist ein Teil eines Befehls, der für den Befehl einen bestimmten Task ausführt.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Das **DISCOVER_JOBS** -Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|**JOB_CREATION_TIME**|**DBTYPE_DBTIMESTAMP**||UTC-Datum und -Zeit des Servers, zu denen der Auftrag erstellt wurde.|  
|**JOB_DESCRIPTION**|**DBTYPE_WSTR**||Die vom Serverdienst zugeordnete Auftragsbeschreibung.|  
|**JOB_EXECUTION_TIME_MS**|**DBTYPE_I8**||Die Zeit in Millisekunden, die der Auftrag aktiv ist.|  
|**JOB_ID**|**DBTYPE_I4**||Der eindeutige Bezeichner des Auftrags.|  
|**JOB_START_TIME**|**DBTYPE_DBTIMESTAMP**||UTC-Datum und -Zeit des Servers, zu denen der Auftrag gestartet wurde.|  
|**JOB_THREADPOOL_ID**|**DBTYPE_I4**||Der Threadpool, aus dem der aktuelle Auftrag gestartet wurde.|  
|**JOB_TOTAL_TIME_MS**|**DBTYPE_I8**||Die Zeit in Millisekunden, seit der der Auftrag gestartet wurde.|  
|**SPID**|**DBTYPE_I4**||Die Sitzungs-ID.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Das **DISCOVER_JOBS** -Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|SPID|DBTYPE_I4|Optional.|  
|JOB_ID|DBTYPE_I4|Optional.|  
|JOB_DESCRIPTION|DBTYPE_WSTR|Optional.|  
|JOB_THREADPOOL_ID|DBTYPE_I4|Optional.|  
|JOB_MIN TOTAL_TIME_MS|DBTYPE_I8|Optional.|  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis-Schemarowsets](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
