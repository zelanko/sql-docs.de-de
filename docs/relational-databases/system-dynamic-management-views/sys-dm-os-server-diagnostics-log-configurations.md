---
title: sys.dm_os_server_diagnostics_log_configurations | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_server_diagnostics_log_configurations
- sys.dm_os_server_diagnostics_log_configurations_TSQL
- dm_os_server_diagnostics_log_configurations
- dm_os_server_diagnostics_log_configurations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_os_server_diagnostics_log_configurations
- sys.dm_os_server_diagnostics_log_configurations
ms.assetid: c09ea433-d283-4f83-af69-d458aad59217
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9a3e03058b42e256991a525a70d6c1fe57e061e8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47752788"
---
# <a name="sysdmosserverdiagnosticslogconfigurations"></a>sys.dm_os_server_diagnostics_log_configurations
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Gibt eine Zeile mit der aktuellen Konfiguration für das Diagnoseprotokoll des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Failoverclusters zurück. Diese Eigenschafteneinstellungen bestimmen, ob die Diagnoseprotokollierung aktiviert oder deaktiviert ist, sowie den Speicherort, die Anzahl und die Größe der Protokolldateien.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|is_enabled|**bit**|Gibt an, ob die Protokollierung aktiviert oder deaktiviert ist.<br /><br /> 1 = Die Diagnoseprotokollierung ist aktiviert.<br /><br /> 0 = Die Diagnoseprotokollierung ist deaktiviert.|  
|max_size|**int**|Maximale Größe in Megabyte für jedes Diagnoseprotokoll. Die Standardeinstellung ist 100 MB.|  
|max_files|**int**|Maximale Anzahl von Diagnoseprotokolldateien, die auf dem Computer gespeichert werden können, bevor sie für neue Diagnoseprotokolle wiederverwendet werden.|  
|path|**nvarchar(260)**|Pfad, der den Speicherort für die Diagnoseprotokolle angibt. Der Standardspeicherort ist \<\MSSQL\Log> im Installationsordner der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Failoverclusterinstanz.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert VIEW SERVER STATE-Berechtigungen für die SQL Server-Failoverclusterinstanz.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden die Eigenschafteneinstellungen für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Failover-Diagnoseprotokolle mithilfe von "sys.dm_os_server_diagnostics_log_configurations" zurückgegeben.  
  
```  
SELECT <list of columns>  
FROM sys.dm_os_server_diagnostics_log_configurations;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|IS_ENABLED|PATH|MAX_SIZE|MAX_FILES|  
|-----------------|----------|---------------|----------------|  
|1|\<C:\Program Files\Microsoft SQL Server\MSSQL13\MSSQL\Log >|10|10|  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen und Lesen des Failoverclusterinstanz-Diagnoseprotokolls](../../sql-server/failover-clusters/windows/view-and-read-failover-cluster-instance-diagnostics-log.md)  
  
  
