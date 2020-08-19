---
description: sysmail_delete_profile_sp (Transact-SQL)
title: sysmail_delete_profile_sp (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_delete_profile_sp
- sysmail_delete_profile_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_delete_profile_sp
ms.assetid: 71998653-4a02-446d-b6f7-50646a29e8a2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 58139a6b9f0471d499c1419f33be28e6a8bbc5f3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419424"
---
# <a name="sysmail_delete_profile_sp-transact-sql"></a>sysmail_delete_profile_sp (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Löscht ein von Datenbank-E-Mail verwendetes E-Mail-Profil.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sysmail_delete_profile_sp  { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' }  
```  
  
## <a name="arguments"></a>Argumente  
`[ @profile_id = ] profile_id` Die Profil-ID des Profils, das gelöscht werden soll. *profile_id* ist vom Datentyp **int**und hat den Standardwert NULL. Es muss entweder *profile_id* oder *profile_name* angegeben werden.  
  
`[ @profile_name = ] 'profile_name'` Der Name des Profils, das gelöscht werden soll. *profile_name* ist vom Datentyp **sysname**und hat den Standardwert NULL. Es muss entweder *profile_id* oder *profile_name* angegeben werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Durch das Löschen eines Profils werden die von diesem Profil verwendeten Konten nicht gelöscht.  
  
 Durch diese gespeicherte Prozedur wird das Profil unabhängig davon gelöscht, ob Benutzer auf das Profil zugreifen können. Gehen Sie vorsichtig vor, wenn Sie das private Standardprofil für einen Benutzer oder das öffentliche Standardprofil für die **msdb** -Datenbank entfernen. Wenn kein Standardprofil verfügbar ist, ist für **sp_send_dbmail** der Name eines Profils als Argument erforderlich. Daher kann das Entfernen eines Standard Profils dazu führen, dass Aufrufe von **sp_send_dbmail** fehlschlagen. Weitere Informationen finden Sie unter [sp_send_dbmail &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md).  
  
 Die gespeicherte Prozedur **sysmail_delete_profile_sp** wird in der **msdb** -Datenbank gespeichert und befindet sich im Besitz des **dbo** -Schemas. Handelt es sich bei der aktuellen Datenbank nicht um **msdb**, muss die Prozedur mit einem dreiteiligen Namen ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Über die Ausführungsberechtigungen für diese Prozedur verfügen standardmäßig die Mitglieder der festen Serverrolle **sysadmin** .  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird gezeigt, wie das Profil `AdventureWorks Administrator` gelöscht wird.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_profile_sp  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-E-Mail](../../relational-databases/database-mail/database-mail.md)   
 [Konfigurationsobjekte Datenbank-E-Mail](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Datenbank-E-Mail gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
