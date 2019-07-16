---
title: Sp_help_log_shipping_primary_secondary (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_log_shipping_primary_secondary
- sp_help_log_shipping_primary_secondary_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_log_shipping_primary_secondary
ms.assetid: bc0044b4-7831-4ff9-8856-825c76aa9893
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3d1c93bb6fecea955e139688b1a8f4f2c1dccc75
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68066822"
---
# <a name="sphelplogshippingprimarysecondary-transact-sql"></a>sp_help_log_shipping_primary_secondary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Diese gespeicherte Prozedur gibt Informationen zu allen sekundären Datenbanken für eine bestimmte primäre Datenbank zurück.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_log_shipping_primary_secondary  
[ @primary_database = ] 'primary_database'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @primary_database = ] 'primary_database'` Ist der Name der Datenbank auf dem primären Server. *primary_database* ist vom Datentyp **sysname**und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Beschreibung|  
|-----------------|-----------------|  
|**secondary_server**|Der Name der sekundären Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in der Protokollversandkonfiguration.|  
|**secondary_database**|Der Name der sekundären Datenbank in der Protokollversandkonfiguration.|  
  
## <a name="remarks"></a>Hinweise  
 **sp_help_log_shipping_primary_secondary** muss aus der **master** -Datenbank auf dem primären Server ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Serverrolle **sysadmin** können diese Prozedur ausführen.  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel wird gezeigt, wie **sp_help_log_shipping_primary_secondary** verwendet wird, um eine Liste sekundärer Datenbanken abzurufen, die der primären [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank zugeordnet sind.  
  
```  
EXECUTE master.dbo.sp_help_log_shipping_primary_secondary @primary_database=N'AdventureWorks';  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Über den Protokollversand &#40;SQLServer&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
