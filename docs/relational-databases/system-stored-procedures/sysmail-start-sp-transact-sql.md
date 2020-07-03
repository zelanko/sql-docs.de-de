---
title: sysmail_start_sp (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: e2986749f21982e5eee75772e794a9461545b967
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85890831"
---
# <a name="sysmail_start_sp-transact-sql"></a>sysmail_start_sp (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Startet Datenbank-E-Mail durch Starten der vom externen Programm verwendeten [!INCLUDE[ssSB](../../includes/sssb-md.md)]-Objekte.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sysmail_start_sp  
```  
  
## <a name="arguments"></a>Argumente  
 Keine  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Datenbank-E-Mail ist bei der Installation nicht aktiviert oder installiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Verwenden Sie den Assistenten zum Konfigurieren von Datenbank-E-Mail zum Aktivieren und Installieren der Datenbank-E-Mail-Objekte.  
  
 Diese gespeicherte Prozedur wird in der **msdb** -Datenbank gespeichert. Diese gespeicherte Prozedur startet die Datenbank-E-Mail-Warteschlange, die ausgehende Benachrichtigungsanforderungen enthält, und aktiviert die [!INCLUDE[ssSB](../../includes/sssb-md.md)]-Unterstützung für das externe Programm.  
  
 Wenn die Warteschlangen gestartet werden, kann das externe Datenbank-E-Mail-Programm Nachrichten verarbeiten. Mit diesem Verfahren können Sie die Warteschlangen neu starten, nachdem die Warteschlangen mit der gespeicherten Prozedur **sysmail_stop_sp** beendet wurden.  
  
> [!NOTE]  
>  Mit dieser gespeicherten Prozedur werden nur die Warteschlangen der Datenbank-E-Mail gestartet. Diese gespeicherte Prozedur aktiviert die [!INCLUDE[ssSB](../../includes/sssb-md.md)]-Nachrichtenübermittlung in der Datenbank nicht.  
  
## <a name="permissions"></a>Berechtigungen  
 Über die Ausführungsberechtigungen für diese Prozedur verfügen standardmäßig die Mitglieder der festen Serverrolle **sysadmin** .  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt das Starten von Datenbank-E-Mail in der **msdb** -Datenbank. Im Rahmen des Beispiels wird davon ausgegangen, dass die Datenbank-E-Mail aktiviert wurde.  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sysmail_start_sp ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-E-Mail](../../relational-databases/database-mail/database-mail.md)   
 [Datenbank-E-Mail XPS (Server Konfigurations Option)](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md)   
 [sysmail_stop_sp &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sysmail-stop-sp-transact-sql.md)   
 [Datenbank-E-Mail gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
