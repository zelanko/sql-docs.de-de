---
title: Sp_upgrade_log_shipping (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_upgrade_log_shipping
- sp_upgrade_log_shipping_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_upgrade_log_shipping
ms.assetid: ee01092f-9caf-4e88-888b-ec7b84223705
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7e5b806f897a22c53688731067acf53f7b647acb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47737608"
---
# <a name="spupgradelogshipping-transact-sql"></a>sp_upgrade_log_shipping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die Prozedur Sp_upgrade_log_shipping gespeichert wird automatisch aufgerufen, zum Aktualisieren von Metadaten, die für den Protokollversand spezifisch sind.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_upgrade_log_shipping  
```  
  
## <a name="arguments"></a>Argumente  
 Keine.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Sonstiges)  
  
## <a name="result-sets"></a>Resultsets  
 Keine.  
  
## <a name="remarks"></a>Hinweise  
 Diese gespeicherte Prozedur wird automatisch aufgerufen, während der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade zum Aktualisieren von Metadaten für den Protokollversand. Sie müssen diese Prozedur nicht explizit aufrufen, es sei denn, beim Upgrade tritt ein Problem mit den Metadaten auf.  
  
 sp_upgrade_log_shipping muss in der master-Datenbank auf dem primären, sekundären oder Überwachungsserver ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** .  
  
## <a name="see-also"></a>Siehe auch  
 [Über den Protokollversand &#40;SQLServer&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
