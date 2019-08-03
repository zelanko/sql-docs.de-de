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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5ca3487a22989261f0d6039f065ae0c102e534a1
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2019
ms.locfileid: "68770866"
---
# <a name="spreplsetoriginator-transact-sql"></a>sp_replsetoriginator (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Wird zum Aufrufen der Loopbackerkennung und -verarbeitung bei der Transaktionsreplikation verwendet. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
