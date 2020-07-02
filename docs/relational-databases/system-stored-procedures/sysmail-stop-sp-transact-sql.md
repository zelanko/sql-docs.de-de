---
title: sysmail_stop_sp (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_stop_sp_TSQL
- sysmail_stop_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_stop_sp
ms.assetid: 045ee36f-5bf0-4626-b5ee-e84db06ce16f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c6ed9d4a05759495090a35224e5aa5ef805e520f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85783697"
---
# <a name="sysmail_stop_sp-transact-sql"></a>sysmail_stop_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Beendet Datenbank-E-Mail durch Beenden der vom externen Programm verwendeten [!INCLUDE[ssSB](../../includes/sssb-md.md)] -Objekte.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sysmail_stop_sp  
```  
  
## <a name="arguments"></a>Argumente  
 Keine  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Diese gespeicherte Prozedur wird in der **msdb** -Datenbank gespeichert.  
  
 Diese gespeicherte Prozedur beendet die Datenbank-E-Mail-Warteschlange, die ausgehende Benachrichtigungsanforderungen enthält, und deaktiviert die [!INCLUDE[ssSB](../../includes/sssb-md.md)] -Aktivierung für das externe Programm.  
  
 Wenn die Warteschlangen beendet werden, verarbeitet das externe Datenbank-E-Mail-Programm keine Nachrichten. Diese gespeicherte Prozedur ermöglicht Ihnen das Beenden von Datenbank-E-Mail für die Problembehandlung oder Wartungsaufgaben.  
  
 Starten Sie Datenbank-E-Mail mithilfe von **sysmail_start_sp**. **sp_send_dbmail** nimmt E-Mail auch dann an, wenn die [!INCLUDE[ssSB](../../includes/sssb-md.md)] -Objekte beendet werden.  
  
> [!NOTE]  
>  Mit dieser gespeicherten Prozedur werden nur die Warteschlangen von Datenbank-E-Mail beendet. Die gespeicherte Prozedur deaktiviert die [!INCLUDE[ssSB](../../includes/sssb-md.md)] -Nachrichtenübermittlung in der Datenbank nicht. Mit dieser gespeicherten Prozedur werden die erweiterten gespeicherten Prozeduren von Datenbank-E-Mail zur Oberflächenreduzierung nicht deaktiviert. Verwenden Sie zum Deaktivieren der erweiterten gespeicherten Prozeduren die Option [Database Mail XPs](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md) der gespeicherten Systemprozedur **sp_configure** .  
  
## <a name="permissions"></a>Berechtigungen  
 Über die Ausführungsberechtigungen für diese Prozedur verfügen standardmäßig die Mitglieder der festen Serverrolle **sysadmin** .  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird das Beenden von Datenbank-E-Mail in der **msdb** -Datenbank veranschaulicht. Im Rahmen des Beispiels wird davon ausgegangen, dass die Datenbank-E-Mail aktiviert wurde.  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sysmail_stop_sp ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-E-Mail](../../relational-databases/database-mail/database-mail.md)   
 [sysmail_start_sp &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sysmail-start-sp-transact-sql.md)   
 [Datenbank-E-Mail gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
