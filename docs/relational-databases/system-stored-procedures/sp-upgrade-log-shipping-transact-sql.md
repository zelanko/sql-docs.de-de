---
title: sp_upgrade_log_shipping (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8afb57d3660f9c69c3ded45f55ed393531a044c4
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85891251"
---
# <a name="sp_upgrade_log_shipping-transact-sql"></a>sp_upgrade_log_shipping (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Die gespeicherte Prozedur sp_upgrade_log_shipping wird automatisch zum Aktualisieren von Metadaten aufgerufen, die für den Protokoll Versand spezifisch sind.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
 Diese gespeicherte Prozedur wird automatisch während [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Upgrades aufgerufen, um Metadaten für den Protokollversand zu aktualisieren. Sie müssen diese Prozedur nicht explizit aufrufen, es sei denn, beim Upgrade tritt ein Problem mit den Metadaten auf.  
  
 sp_upgrade_log_shipping muss in der master-Datenbank auf dem primären, sekundären oder Überwachungsserver ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Server Rolle **sysadmin** .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Informationen zum Protokollversand &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
