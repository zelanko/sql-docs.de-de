---
title: sp_replsetoriginator (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replsetoriginator
- sp_replsetoriginator_TSQL
helpviewer_keywords:
- sp_replsetoriginator
ms.assetid: 030e5226-0585-439f-b8cd-36f48367d86d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1811a523e23de9726517bfabd1ddf8417aa3c5fc
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85626733"
---
# <a name="sp_replsetoriginator-transact-sql"></a>sp_replsetoriginator (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Wird zum Aufrufen der Loopbackerkennung und -verarbeitung bei der Transaktionsreplikation verwendet. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_replsetoriginator [ @server_name= ] 'server_name'   
    , [ @database_name= ] 'database_name'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @server_name = ] 'server_name'`Der Name des Servers, auf dem die Transaktion angewendet wird. *originating_server* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @database_name = ] 'database_name'`Der Name der Datenbank, in der die Transaktion angewendet wird. *originating_db* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_replsetoriginator** wird vom Verteilungs-Agent ausgeführt, um die Quelle der von der Replikation angewendeten Transaktionen aufzuzeichnen. Mithilfe dieser Informationen wird die Loopbackerkennung für bidirektionale Transaktionsabonnements aufgerufen, bei denen die Loopbackeigenschaft festgelegt ist.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** auf dem Verleger, Mitglieder der festen Daten Bank Rolle **db_owner** in der Veröffentlichungs Datenbank oder Benutzer in der Veröffentlichungs Zugriffsliste (Publication Access List, PAL) können **sp_replsetoriginator**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
