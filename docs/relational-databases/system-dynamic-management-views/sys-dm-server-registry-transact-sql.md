---
title: sys. dm_server_registry (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_server_registry_TSQL
- sys.dm_server_registry
- dm_server_registry
- sys.dm_server_registry_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_server_registry dynamic management view
ms.assetid: 9b3e0c74-2e99-4996-a383-104d51831e97
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 241f6df631098fedbf4b7f5a9849d9b7ea9f3fa0
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85775205"
---
# <a name="sysdm_server_registry-transact-sql"></a>sys.dm_server_registry (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Gibt Konfigurations- und Installationsinformationen zurück, die für die aktuelle Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]in der Windows-Registrierung gespeichert sind. Gibt eine Zeile pro Registrierungsschlüssel zurück. Verwenden Sie diese dynamische Verwaltungssicht, um Informationen für die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zurückzugeben, z. B. die auf dem Hostcomputer verfügbaren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienste oder die Werte der Netzwerkkonfiguration.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|registry_key|**nvarchar(256)**|Registrierungsschlüsselname. Lässt NULL-Werte zu.|  
|value_name|**nvarchar(256)**|Schlüsselwertname. Dies ist das Element, das in der Spalte **Name** des Registrierungs-Editors angezeigt wird. Lässt NULL-Werte zu.|  
|value_data|**sql_variant**|Der Wert der Schlüsseldaten. Dies ist der Wert, der für einen Eintrag in der Spalte **Daten** des Registrierungs-Editors angezeigt wird. Lässt NULL-Werte zu.|  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-display-the-sql-server-services"></a>A. Anzeigen der SQL Server-Dienste  
 Im folgenden Beispiel werden die Registrierungsschlüsselwerte für den SQL Server-Dienst und den SQL Server-Agent-Dienst für die aktuelle Instanz von SQL Server zurückgegeben.  
  
```  
SELECT registry_key, value_name, value_data  
FROM sys.dm_server_registry  
WHERE registry_key LIKE N'%ControlSet%';  
```  
  
### <a name="b-display-the-sql-server-agent-registry-key-values"></a>B. Anzeigen der Registrierungsschlüsselwerte für den SQL Server-Agent  
 Im folgenden Beispiel werden die Registrierungsschlüsselwerte für den SQL Server-Agent für die aktuelle Instanz von SQL Server zurückgegeben.  
  
```  
SELECT registry_key, value_name, value_data  
FROM sys.dm_server_registry  
WHERE registry_key LIKE N'%SQLAgent%';  
```  
  
### <a name="c-display-the-current-version-of-the-instance-of-sql-server"></a>C. Anzeigen der aktuellen Version der Instanz von SQL Server  
 Im folgenden Beispiel wird die Version der aktuellen Instanz von SQL Server zurückgegeben.  
  
```  
SELECT registry_key, value_name, value_data  
FROM sys.dm_server_registry  
WHERE value_name = N'CurrentVersion';  
```  
  
### <a name="d-display-the-parameters-passed-to-the-instance-of-sql-server-during-startup"></a>D: Anzeigen der Parameter, die beim Start an die Instanz von SQL Server übergeben wurden  
 Im folgenden Beispiel werden die Parameter zurückgegeben, die beim Start an die Instanz von SQL Server übergeben wurden.  
  
```  
SELECT registry_key, value_name, value_data  
FROM sys.dm_server_registry  
WHERE registry_key LIKE N'%Parameters';  
```  
  
### <a name="e-return-network-configuration-information-for-the-instance-of-sql-server"></a>E. Zurückgeben der Netzwerkkonfigurationsinformationen für die Instanz von SQL Server  
 Im folgenden Beispiel werden die Werte der Netzwerkkonfiguration für die aktuelle Instanz von SQL Server zurückgegeben.  
  
```  
SELECT registry_key, value_name, value_data  
FROM sys.dm_server_registry  
WHERE registry_key LIKE N'%SuperSocketNetLib%';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys. dm_server_services &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-services-transact-sql.md)  
  
  
