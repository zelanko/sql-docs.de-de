---
title: sp_adjustpublisheridentityrange (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_adjustpublisheridentityrange_TSQL
- sp_adjustpublisheridentityrange
helpviewer_keywords:
- sp_adjustpublisheridentityrange
ms.assetid: 64f111fd-fb7d-4459-93f7-65f0f8dd7efe
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1f58c1a212c722873f66d940de691c89d13d08f5
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85716303"
---
# <a name="sp_adjustpublisheridentityrange-transact-sql"></a>sp_adjustpublisheridentityrange (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Passt den Identitätsbereich für eine Veröffentlichung an und ordnet neue Bereiche auf der Grundlage des Schwellenwerts für die Veröffentlichung neu zu. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_adjustpublisheridentityrange [ [ @publication = ] 'publication' ]  
    [ , [ @table_name = ] 'table_name' ]  
    [ , [ @table_owner= ] 'table_owner' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung, in der neue Identitäts Bereiche neu zugewiesen werden. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @table_name = ] 'table_name'`Der Name der Tabelle, in der neue Identitäts Bereiche erneut zugeordnet werden. *table_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @table_owner = ] 'table_owner'`Der Besitzer der Tabelle auf dem Verleger. *TABLE_OWNER* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Wenn *TABLE_OWNER* nicht angegeben ist, wird der Name des aktuellen Benutzers verwendet.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_adjustpublisheridentityrange** wird bei allen Replikations Typen verwendet.  
  
 Für eine Veröffentlichung mit aktiviertem automatischem Identitätsbereich ist der Verteilungs- oder Merge-Agent für die automatische Anpassung des Identitätsbereichs in einer Veröffentlichung auf der Basis des Schwellenwerts verantwortlich. Wenn jedoch aus irgendeinem Grund die Verteilungs-Agent oder Merge-Agent nicht innerhalb eines bestimmten Zeitraums ausgeführt wurden und die Identitäts Bereichs Ressource stark bis zum Schwellenwert verbraucht wurde, können Benutzer **sp_adjustpublisheridentityrange** aufzurufen, um einen neuen Wertebereich für einen Verleger zuzuordnen.  
  
 Beim Ausführen **sp_adjustpublisheridentityrange**muss entweder die *Veröffentlichung* oder die *table_name* angegeben werden. Wenn beide oder keiner der Parameter angegeben wird, wird ein Fehler zurückgegeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_adjustpublisheridentityrange**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replizieren von Identitäts Spalten](../../relational-databases/replication/publish/replicate-identity-columns.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
