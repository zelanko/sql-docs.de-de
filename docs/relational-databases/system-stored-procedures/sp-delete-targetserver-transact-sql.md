---
title: sp_delete_targetserver (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_targetserver
- sp_delete_targetserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_targetserver
ms.assetid: cc438701-ad91-419d-9f23-ebc4c548c700
author: stevestein
ms.author: sstein
ms.openlocfilehash: 487d88a7580432bf947893920d307e2f0adffd18
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68111994"
---
# <a name="sp_delete_targetserver-transact-sql"></a>sp_delete_targetserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Entfernt den angegebenen Server aus der Liste der verfügbaren Zielserver.  
   
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_delete_targetserver [ @server_name = ] 'server'   
     [ , [ @clear_downloadlist = ] clear_downloadlist ]  
     [ , [ @post_defection = ] post_defection ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @server_name = ] 'server'`Der Name des Servers, der als verfügbarer Zielserver entfernt werden soll. der *Server* ist vom Datentyp **nvarchar (30)** und hat keinen Standardwert.  
  
`[ @clear_downloadlist = ] clear_downloadlist`Gibt an, ob die Download Liste für den Zielserver gelöscht werden soll. *clear_downloadlist* ist vom Typ **Bit**und hat den Standardwert **1**. Wenn *clear_downloadlist* **1**ist, löscht die Prozedur die Download Liste für den Server, bevor der Server gelöscht wird. Wenn *clear_downloadlist* **0**ist, wird die Download Liste nicht gelöscht.  
  
`[ @post_defection = ] post_defection`Gibt an, ob eine Mängel Anweisung auf dem Zielserver gepostet werden soll. *post_defection* ist vom Typ **Bit**und hat den Standardwert 1. Wenn *post_defection* **1**ist, sendet die Prozedur eine Mängel Anweisung an den Zielserver, bevor der Server gelöscht wird. Wenn *post_defection* **0**ist, stellt die Prozedur keine Fehler Anweisung auf dem Zielserver bereit.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Der normale Weg zum Löschen eines Zielservers besteht darin, **sp_msx_defect** auf dem Zielserver aufzurufen. Verwenden Sie **sp_delete_targetserver** nur, wenn eine manuelle abaktivierung erforderlich ist.  
  
## <a name="permissions"></a>Berechtigungen  
 Zum Ausführen dieser gespeicherten Prozedur muss den Benutzern die festen Server Rolle **sysadmin** erteilt werden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Server `LONDON1` aus der Liste der verfügbaren Auftragsserver entfernt.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_targetserver  
  @server_name = N'LONDON1' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_help_targetserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-targetserver-transact-sql.md)   
 [sp_msx_defect &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-msx-defect-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
