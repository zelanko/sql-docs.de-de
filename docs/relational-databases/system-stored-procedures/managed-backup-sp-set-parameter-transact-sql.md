---
description: managed_backup. sp_set_parameter (Transact-SQL)
title: managed_backup. sp_set_parameter (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_set_parameter_TSQL
- sp_set_parameter
- smart_admin.sp_set_parameter
- smart_admin.sp_set_parameter_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_set_parameter
- smart_admin.sp_set_parameter
ms.assetid: bd8ae5fd-1337-4b7f-b0a4-153cbca9fa5f
author: markingmyname
ms.author: maghan
ms.openlocfilehash: dfb0a9ddbdec9ebe94dd3bda4307a5fdf31e1c29
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89546272"
---
# <a name="managed_backupsp_set_parameter-transact-sql"></a>managed_backup. sp_set_parameter (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Legt den Wert des angegebenen Smart Admin-Systemparameters fest.  
  
 Die verfügbaren Parameter beziehen sich auf [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Mit diesen Parametern werden die E-Mail-Benachrichtigungen festgelegt, bestimmte erweiterte Ereignisse aktiviert und auf benutzerdefinierten Richtlinien basierende Verwaltungsrichtlinien aktiviert. Sie müssen die Paare aus Parametername und Parameterwert angeben.  

  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql  
EXEC managed_backup.sp_set_parameter   
    [@parameter_name = ] {'SSMBackup2WANotificationEmailIds' | 'SSMBackup2WAEnableUserDefinedPolicy' | 'SSMBackup2WADebugXevent' | 'FileRetentionDebugXevent' | 'StorageOperationDebugXevent'}  
    ,[@parameter_value = ] 'parameter_value'  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a>Argumente  
 @parameter_name  
 Der Name des Parameters, dessen Wert festgelegt werden soll. @parameter_name ist vom Datentyp nvarchar (128). Die verfügbaren Parameternamen lauten **SSMBackup2WANotificationEmailIds**, **SSMBackup2WADebugXevent**, **SSMBackup2WAEnableUserDefinedPolicy**, **fileretentiondebug XEvent**und **storageoperationdebug-Ereignis**.  
  
 @parameter_value  
 Der Wert des Parameters, der festgelegt werden soll. @parameter der Wert ist nvarchar (128).  Im Folgenden sind die zulässigen Parametername/Parameterwert-Paare aufgeführt:  
  
-   @parameter_name = ' SSMBackup2WANotificationEmailIds ': @parameter_value  = ' Email '  
  
-   @parameter_name = ' SSMBackup2WAEnableUserDefinedPolicy ': @parameter_value  = {' true ' | ' false '}  
  
-   @parameter_name = ' SSMBackup2WADebugXevent ': @parameter_value  = {' true ' | ' false '}  
  
-   @parameter_name = ' Fileretentiondebug-XEvent ': @parameter_value  = {' true ' | ' false '}  
  
-   @parameter_name = ' Storageoperationentbugxevent ' = {' true ' | ' false '}  
  
## <a name="return-code-value"></a>Rückgabecodewert  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="best-practices"></a>Bewährte Methoden  
 Optionaler Abschnitt, der bewährte Methoden beschreibt, die der Benutzer beim Ausführen der Anweisung oder Routine befolgen sollte.  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert **Ausführungs** Berechtigungen für die gespeicherte Prozedur **managed_backup. sp_set_parameter** .  
  
## <a name="examples"></a>Beispiele  
 In den folgenden Beispielen werden erweiterte operationale und Debugereignisse aktiviert.  
  
```  
-- to enable operational events  
Use msdb;  
Go  
         EXEC managed_backup.sp_set_parameter 'FileRetentionOperationalXevent', 'True'  
--  to enable debug events  
Use msdb;  
Go  
         EXEC managed_backup.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
```  
  
 Im folgenden Beispiel werden E-Mail-Benachrichtigungen über Fehler sowie Warnungen aktiviert; zudem wird die emailID festgelegt, an die die Benachrichtigungen gesendet werden sollen:  
  
```  
Use msdb  
Go  
EXEC managed_backup.sp_set_parameter @parameter_name = 'SSMBackup2WANotificationEmailIds', @parameter_value = '<email address>'  
  
```  
  
  
