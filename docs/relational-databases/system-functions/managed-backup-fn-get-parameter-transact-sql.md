---
title: managed_backup. fn_get_parameter (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/03/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- smart_admin.fn_get_parameter_TSQL
- smart_admin.fn_get_parameter
- fn_get_parameter_TSQL
- fn_get_parameter
dev_langs:
- TSQL
helpviewer_keywords:
- fn_get_parameter
- smart_admin.fn_get_parameter
ms.assetid: ed94e54d-4516-4806-a8ce-f013d3a04122
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 63894f891d633e5b8c2f32f32b1be6573bb97baa
ms.sourcegitcommit: 703968b86a111111a82ef66bb7467dbf68126051
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "86053426"
---
# <a name="managed_backupfn_get_parameter-transact-sql"></a>managed_backup. fn_get_parameter (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Gibt eine Tabelle mit 0, 1 oder mehr Zeilen von Parameter/Wert-Paaren zurück.  
  
 Überprüfen Sie mit dieser gespeicherten Prozedur alle oder bestimmte Konfigurationseinstellungen für Smart Admin.  
  
 Wenn der Parameter nicht konfiguriert wurde, gibt die Funktion 0 Zeilen zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql  
managed_backup.fn_get_parameter ('parameter_name' | '' | NULL )  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a>Argumentation  
 parameter_name  
 Der Name des Parameters. parameter_name ist vom Datentyp **nvarchar (128)**. Wenn NULL oder eine leere Zeichenfolge als Argument für die Funktion angegeben wird, werden Name/Wert-Paare für alle konfigurierten Smart Admin-Parameter zurückgegeben.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|parameter_name|NVARCHAR(128)|Der Name des Parameters. Im Folgenden finden Sie eine aktuelle Liste der zurückgegebenen Parameter:<br/><br/>**Fileretentiondebug-Ereignis**<br/><br/>**SSMBackup2WADebugXevent**<br/><br/>**SSMBackup2WANotificationEmailIds**<br/><br/>**SSMBackup2WAEnableUserDefinedPolicy**<br/><br/>**SSMBackup2WAEverConfigured**<br/><br/>**Storageoperationdebug-Ereignis**|  
|parameter_value|NVARCHAR(128)|Derzeit festgelegter Wert des Parameters.|  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert SELECT-Berechtigungen für die Funktion.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden alle Parameter, die mindestens einmal konfiguriert wurden, und deren aktuelle Werte zurückgegeben.  
  
```  
USE MSDB  
GO  
SELECT *   
FROM managed_backup.fn_get_parameter (NULL)  
  
```  
  
 Im folgenden Beispiel wird die E-Mail-ID zurückgegeben, die für das Empfangen der Fehlerbenachrichtigungen angegeben wurde. Wenn keine Zeilen zurückgegeben werden, bedeutet das, dass die Option für E-Mail-Benachrichtigungen nicht aktiviert wurde.  
  
```  
USE MSDB  
GO  
SELECT *  
FROM managed_backup.fn_get_parameter ('SSMBackup2WANotficationEmailIds')  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwaltete SQL Server-Sicherung in Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  
  
  
