---
description: sysmail_help_configure_sp (Transact-SQL)
title: sysmail_help_configure_sp (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_help_configure_sp
- sysmail_help_configure_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_configure_sp
ms.assetid: e598d4c8-3041-4965-b046-dce3a8e3d3e0
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c030fbc4ee2c329f8c13e525c07961794b28608e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88488957"
---
# <a name="sysmail_help_configure_sp-transact-sql"></a>sysmail_help_configure_sp (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Zeigt Konfigurationseinstellungen für Datenbank-E-Mail an.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sysmail_help_configure_sp  [ [ @parameter_name = ] 'parameter_name' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @parameter_name = ] 'parameter_name'` Der Name der abzurufenden Konfigurationseinstellung. Wenn angegeben, wird der Wert der Konfigurationseinstellung im ** \@ parameter_value** Output-Parameter zurückgegeben. Wenn keine ** \@ parameter_name** angegeben wird, gibt diese gespeicherte Prozedur ein Resultset zurück, das alle Datenbank-E-Mail Konfigurationseinstellungen in der-Instanz enthält.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Wenn keine ** \@ parameter_name** angegeben wird, gibt ein Resultset mit den folgenden Spalten zurück.  
  
| Spaltenname | Datentyp | BESCHREIBUNG |
| ----------- | --------- | ----------- |
|**paramName**|**nvarchar(256)**|Der Name des Konfigurationsparameters.|  
|**angegebene paramValue**|**nvarchar(256)**|Der Wert des Konfigurationsparameters.|  
|**Beschreibung**|**nvarchar(256)**|Die Beschreibung des Konfigurationsparameters.|  
  
## <a name="remarks"></a>Bemerkungen  
 Die gespeicherte Prozedur **sysmail_help_configure_sp** führt die aktuellen Konfigurationseinstellungen für Datenbank-E-Mail für die Instanz auf.  
  
 Wenn eine ** \@ parameter_name** angegeben wird, für ** \@ parameter_value**jedoch kein Ausgabeparameter bereitgestellt wird, erzeugt diese gespeicherte Prozedur keine Ausgabe.  
  
 Die gespeicherte Prozedur **sysmail_help_configure_sp** befindet sich in der **msdb** -Datenbank und im Besitz des **dbo** -Schemas. Handelt es sich bei der aktuellen Datenbank nicht um **msdb**, muss die Prozedur mit einem dreiteiligen Namen aufgerufen werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Über die Ausführungsberechtigungen für diese Prozedur verfügen standardmäßig die Mitglieder der festen Serverrolle **sysadmin** .  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Liste der Konfigurationseinstellungen für Datenbank-E-Mail für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz gezeigt.  
  
```  
EXECUTE msdb.dbo.sysmail_help_configure_sp ;  
```  
  
 Es folgt ein Beispielresultset, das auf Zeilenlänge umformatiert wurde:  
  
```  
paramname                       paramvalue      description  
------------------------------- --------------- -----------------------------------------------------------------------------  
AccountRetryAttempts            1               Number of retry attempts for a mail server  
AccountRetryDelay               5000            Delay between each retry attempt to mail server  
DatabaseMailExeMinimumLifeTime  600             Minimum process lifetime in seconds  
DefaultAttachmentEncoding       MIME            Default attachment encoding  
LoggingLevel                    2               Database Mail logging level: normal - 1, extended - 2 (default), verbose - 3  
MaxFileSize                     1000000         Default maximum file size  
ProhibitedExtensions            exe,dll,vbs,js  Extensions not allowed in outgoing mails  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-E-Mail](../../relational-databases/database-mail/database-mail.md)   
 [Datenbank-E-Mail gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
