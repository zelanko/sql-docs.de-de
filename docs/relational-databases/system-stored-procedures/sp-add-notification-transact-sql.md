---
title: sp_add_notification (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_notification_TSQL
- sp_add_notification
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_notification
ms.assetid: 0525e0a2-ed0b-4e69-8a4c-a9e3e3622fbd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fcf55efd5b50f73d15e0fc488cfe4298b99d9eb7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85646483"
---
# <a name="sp_add_notification-transact-sql"></a>sp_add_notification (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Richtet eine Benachrichtigung für eine Warnung ein.  
  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_add_notification [ @alert_name = ] 'alert' ,   
    [ @operator_name = ] 'operator' ,   
    [ @notification_method = ] notification_method  
```  
  
## <a name="arguments"></a>Argumente  
`[ @alert_name = ] 'alert'`Die Warnung für diese Benachrichtigung. *Alert* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @operator_name = ] 'operator'`Der Operator, der benachrichtigt werden soll, wenn die Warnung auftritt. *Operator* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @notification_method = ] notification_method`Die Methode, mit der der Operator benachrichtigt wird. *notification_method* ist vom Datentyp **tinyint**und hat keinen Standardwert. *notification_method* können einen oder mehrere dieser Werte in Kombination mit einem logischen **or** -Operator aufweisen.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|E-Mail|  
|**2**|Pager|  
|**4**|**NET SEND**|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_add_notification** müssen von der **msdb** -Datenbank aus ausgeführt werden.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] kann das gesamte Warnungssystem auf einfache Weise über eine grafische Oberfläche verwaltet werden. Für die Konfiguration einer Warnungsinfrastruktur sollte [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] verwendet werden.  
  
 Zum Senden einer Benachrichtigung als Reaktion auf eine Warnung müssen Sie zunächst den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent für das Senden von E-Mail konfigurieren.  
  
 Wenn beim Senden einer E-Mail- oder Pagerbenachrichtigung ein Fehler auftritt, wird der Fehler im Fehlerprotokoll des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Diensts aufgezeichnet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_add_notification**ausführen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine E-Mail-Benachrichtigung für die angegebene Warnung (`Test Alert`) hinzugefügt.  
  
> **Hinweis:** In diesem Beispiel wird davon ausgegangen, dass `Test Alert` bereits vorhanden `François Ajenstat` ist und ein gültiger Operator Name ist.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_notification  
 @alert_name = N'Test Alert',  
 @operator_name = N'François Ajenstat',  
 @notification_method = 1 ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_delete_notification &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-notification-transact-sql.md)   
 [sp_help_notification &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-notification-transact-sql.md)   
 [sp_update_notification &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-update-notification-transact-sql.md)   
 [sp_add_operator &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
