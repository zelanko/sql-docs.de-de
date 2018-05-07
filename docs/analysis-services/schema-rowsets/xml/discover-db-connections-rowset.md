---
title: DISCOVER_DB_CONNECTIONS-Rowset | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3ccdd4496b075c976bfaecb4d7eb9db43560f3c3
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="discoverdbconnections-rowset"></a>DISCOVER_DB_CONNECTIONS-Rowset
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Stellt Informationen zur Ressourcenauslastung und Aktivität der zurzeit geöffneten Verbindungen vom Server in einer Datenbank bereit.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Das **DISCOVER_DB_CONNECTIONS** -Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CONNECTION_CATALOG_NAME**|**DBTYPE_WSTR**||Der Name der Datenbank, mit der zurzeit eine Verbindung besteht.|  
|**CONNECTION_ID**|**DBTYPE_I4**||Eine eindeutige Zahl, die die Verbindung identifiziert.|  
|**CONNECTION_IDLE_TIME_MS**|**DBTYPE_I8**||Die Leerlaufzeit in Millisekunden seit dem Start der Verbindung.|  
|**CONNECTION_IN_USE**|**DBTYPE_I4**||Gibt an, ob die Verbindung aktiv ist (1) oder sich im Leerlauf befindet (0).|  
|**CONNECTION_LAST_COMMAND_END_TIME**|**DBTYPE_DBTIMESTAMP**||UTC-Datum und -Zeit des Servers, zu denen der letzte Befehl seine Ausführung beendet hat.|  
|**CONNECTION_LAST_COMMAND_START_TIME**|**DBTYPE_DBTIMESTAMP**||UTC-Datum und -Zeit des Servers, zu denen der letzte Befehl seine Ausführung initiiert hat.|  
|**CONNECTION_SERVER_NAME**|**DBTYPE_WSTR**||Der Name des Servers, mit dem zurzeit eine Verbindung besteht.|  
|**CONNECTION_SPID**|**DBTYPE_I4**||Die Sitzungs-ID.|  
|**CONNECTION_START_TIME**|**DBTYPE_DBTIMESTAMP**||UTC-Datum und -Zeit des Servers, zu denen die Verbindung initiiert wurde.|  
|**CONNECTION_USAGE_TIME_MS**|**DBTYPE_I8**||Die Aktivitätszeit der Verbindung in Millisekunden seit dem Start der Verbindung.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
> [!IMPORTANT]  
>  Das **DISCOVER_DB_CONNECTIONS** -Rowset zeigt nur Informationen an, wenn der Dienst mit der relationalen Datenquelle verbunden ist.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Das **DISCOVER_DB_CONNECTIONS** -Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|CONNECTION_ID|DBTYPE_I4|Optional.|  
|CONNECTION_IN_USE|DBTYPE_I4|Optional.|  
|CONNECTION_SERVER_NAME|DBTYPE_WSTR|Optional.|  
|CONNECTION_CATALOG_NAME|DBTYPE_WSTR|Erforderlich.|  
|CONNECTION_SPID|DBTYPE_I4|Optional.|  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis-Schemarowsets](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
