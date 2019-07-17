---
title: Sp_delete_targetserver (Transact-SQL) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68111994"
---
# <a name="spdeletetargetserver-transact-sql"></a>sp_delete_targetserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Entfernt den angegebenen Server aus der Liste der verfügbaren Zielserver.  
   
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_delete_targetserver [ @server_name = ] 'server'   
     [ , [ @clear_downloadlist = ] clear_downloadlist ]  
     [ , [ @post_defection = ] post_defection ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @server_name = ] 'server'` Der Name des Servers, der als verfügbarer Zielserver entfernt werden soll. *Server* ist **nvarchar(30)** , hat keinen Standardwert.  
  
`[ @clear_downloadlist = ] clear_downloadlist` Gibt an, ob die Downloadliste für den Zielserver gelöscht werden soll. *Clear_downloadlist* Typ **Bit**, hat den Standardwert **1**. Wenn *Clear_downloadlist* ist **1**, die Prozedur löscht die Downloadliste für den Server vor dem Löschen des Servers. Wenn *Clear_downloadlist* ist **0**, die Downloadliste nicht deaktiviert ist.  
  
`[ @post_defection = ] post_defection` Gibt an, ob eine austrittsanweisung auf dem Zielserver bereitgestellt werden soll. *Post_defection* Typ **Bit**, hat den Standardwert 1. Wenn *Post_defection* ist **1**, die Prozedur eine austrittsanweisung auf dem Zielserver vor dem Löschen des Servers. Wenn *Post_defection* ist **0**, bucht die Prozedur keine austrittsanweisung auf dem Zielserver nicht.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 Wird die normale Methode zum Löschen eines Zielservers aufzurufen **Sp_msx_defect** auf dem Zielserver. Verwendung **Sp_delete_targetserver** nur ab, wenn ein manueller Austritt erforderlich ist.  
  
## <a name="permissions"></a>Berechtigungen  
 Um diese gespeicherte Prozedur auszuführen, müssen Benutzer gewährt werden die **Sysadmin** -Serverrolle sein.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Server `LONDON1` aus der Liste der verfügbaren Auftragsserver entfernt.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_targetserver  
  @server_name = N'LONDON1' ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_help_targetserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-targetserver-transact-sql.md)   
 [sp_msx_defect &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-msx-defect-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
