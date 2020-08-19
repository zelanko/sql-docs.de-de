---
description: sysmail_help_profile_sp (Transact-SQL)
title: sysmail_help_profile_sp (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_help_profile_sp_TSQL
- sysmail_help_profile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_profile_sp
ms.assetid: d7169a8e-92b1-49eb-9124-3b2f69755ddb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 372f2309176b9fcf9cbb36fbcaf89d710393bb44
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419294"
---
# <a name="sysmail_help_profile_sp-transact-sql"></a>sysmail_help_profile_sp (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Führt Informationen zu mindestens einem Mailprofil auf.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sysmail_help_profile_sp  [   [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @profile_id = ] profile_id` Die Profil-ID, für die Informationen zurückgegeben werden. *profile_id* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @profile_name = ] 'profile_name'` Der Profilname, für den Informationen zurückgegeben werden sollen. *profile_name* ist vom Datentyp **sysname**und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Gibt ein Resultset mit den folgenden Spalten zurück.  
  
| Spaltenname | Datentyp | BESCHREIBUNG |
| ----------- | --------- | ----------- |
|**profile_id**|**int**|Die Profil-ID des Profils.|  
|**name**|**sysname**|Der Profilname des Profils.|  
|**Beschreibung**|**nvarchar(256)**|Die Beschreibung des Profils.|  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn ein Profilname oder eine Profil-ID angegeben ist, gibt **sysmail_help_profile_sp** Informationen zu diesem Profil zurück. Andernfalls gibt **sysmail_help_profile_sp** Informationen zu jedem Profil in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz zurück.  
  
 Die gespeicherte Prozedur **sysmail_help_profile_sp** befindet sich in der **msdb** -Datenbank und im Besitz des **dbo** -Schemas. Handelt es sich bei der aktuellen Datenbank nicht um **msdb**, muss die Prozedur mit einem dreiteiligen Namen ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Über die Ausführungsberechtigungen für diese Prozedur verfügen standardmäßig die Mitglieder der festen Serverrolle **sysadmin** .  
  
## <a name="examples"></a>Beispiele  
 **A. Auflisten aller Profile**  
  
 Im folgenden Beispiel werden alle Profile in der Instanz aufgelistet.  
  
```  
EXECUTE msdb.dbo.sysmail_help_profile_sp;  
```  
  
 Es folgt ein Beispielresultset, das auf Zeilenlänge umformatiert wurde:  
  
```  
profile_id  name                          description  
----------- ----------------------------- ------------------------------  
56          AdventureWorks Administrator  Administrative mail profile.    
57          AdventureWorks Operator       Operator mail profile.          
```  
  
 **B. Auflisten eines bestimmten Profils**  
  
 Im folgenden Beispiel werden Informationen für das `AdventureWorks Administrator`-Profil aufgelistet.  
  
```  
EXECUTE msdb.dbo.sysmail_help_profile_sp  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
 Es folgt ein Beispielresultset, das auf Zeilenlänge umformatiert wurde:  
  
```  
profile_id  name                          description  
----------- ----------------------------- ------------------------------  
56          AdventureWorks Administrator  Administrative mail profile.    
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-E-Mail](../../relational-databases/database-mail/database-mail.md)   
 [Datenbank-E-Mail gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
