---
title: Sysmail_start_sp (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_start_sp
- sysmail_start_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_start_sp
ms.assetid: 25fd7bb6-cfdd-463f-bea8-c6fcb805d3f5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 877fa31954cb0bf7255d831475c875fb43d002b8
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53210009"
---
# <a name="sysmailstartsp-transact-sql"></a>sysmail_start_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Startet Datenbank-E-Mail durch Starten der vom externen Programm verwendeten [!INCLUDE[ssSB](../../includes/sssb-md.md)]-Objekte.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sysmail_start_sp  
```  
  
## <a name="arguments"></a>Argumente  
 None  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 Datenbank-e-Mails ist nicht aktiviert oder installiert werden, bei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation. Verwenden Sie den Assistenten zum Konfigurieren von Datenbank-E-Mail zum Aktivieren und Installieren der Datenbank-E-Mail-Objekte.  
  
 Diese gespeicherte Prozedur wird in der **msdb** -Datenbank gespeichert. Diese gespeicherte Prozedur startet die Datenbank-E-Mail-Warteschlange, die ausgehende Benachrichtigungsanforderungen enthält, und aktiviert die [!INCLUDE[ssSB](../../includes/sssb-md.md)]-Unterstützung für das externe Programm.  
  
 Wenn die Warteschlangen gestartet werden, kann das externe Datenbank-E-Mail-Programm Nachrichten verarbeiten. Mit dieser Prozedur können Sie die Warteschlangen erneut starten, nachdem die Warteschlangen beendet wurden die **Sysmail_stop_sp** gespeicherte Prozedur.  
  
> [!NOTE]  
>  Mit dieser gespeicherten Prozedur werden nur die Warteschlangen der Datenbank-E-Mail gestartet. Diese gespeicherte Prozedur aktiviert die [!INCLUDE[ssSB](../../includes/sssb-md.md)]-Nachrichtenübermittlung in der Datenbank nicht.  
  
## <a name="permissions"></a>Berechtigungen  
 Über die Ausführungsberechtigungen für diese Prozedur verfügen standardmäßig die Mitglieder der festen Serverrolle **sysadmin** .  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt, starten Datenbank-e-Mails in die **Msdb** Datenbank. Im Rahmen des Beispiels wird davon ausgegangen, dass die Datenbank-E-Mail aktiviert wurde.  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sysmail_start_sp ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-E-Mail](../../relational-databases/database-mail/database-mail.md)   
 [Database Mail XPs-Serverkonfigurationsoption](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md)   
 [sysmail_stop_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-stop-sp-transact-sql.md)   
 [Datenbank-e-Mails gespeicherte Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
