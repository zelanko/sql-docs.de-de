---
title: sp_requestpeertopologyinfo (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_requestpeertopologyinfo
- sp_requestpeertopologyinfo_TSQL
helpviewer_keywords:
- sp_requestpeertopologyinfo
ms.assetid: 15cd28bd-5a72-41fb-ae1b-726baaa6fad5
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c88b25976af9914d21ea4ee80d165e893360bdf0
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85899272"
---
# <a name="sp_requestpeertopologyinfo-transact-sql"></a>sp_requestpeertopologyinfo (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Füllt die [MSpeer_topologyresponse](../../relational-databases/system-tables/mspeer-topologyresponse-transact-sql.md) Systemtabelle mit Informationen über eine Peer-zu-Peer-Transaktions Replikations Topologie. Führen Sie [sp_gettopologyinfo](../../relational-databases/system-stored-procedures/sp-gettopologyinfo-transact-sql.md) aus, um Informationen aus der Tabelle im XML-Format zu erhalten.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_requestpeertopologyinfo [ @publication = ] 'publication'  
        [ ,[ @requestid=] request_id OUTPUT  
```  
  
## <a name="arguments"></a>Argumente  
 [ @publication =] '*Veröffentlichung*'  
 Der Name der Veröffentlichung, für die eine topologieübergreifende Statusanforderung ausgeführt werden soll. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
 [ @request_id =] *request_id*  
 Die ID-Nummer, die der Topologiestatusanforderung zugewiesen wird. *request_id* ist vom Datentyp **int**und hat den Standardwert NULL. Diese ID kann von [sp_gettopologyinfo](../../relational-databases/system-stored-procedures/sp-gettopologyinfo-transact-sql.md)verwendet werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 sp_requestpeertopologyinfo wird in einer Peer-zu-Peer-Transaktionsreplikation verwendet. Führen Sie sp_requestpeertopologyinfo aus, bevor Sie [sp_gettopologyinfo](../../relational-databases/system-stored-procedures/sp-gettopologyinfo-transact-sql.md)ausführen. Diese Prozeduren werden vom Assistenten zum Konfigurieren der Peer-zu-Peer-Topologie verwendet, können jedoch auch direkt verwendet werden, wenn Sie Topologiedaten in einem XML-Format benötigen. Wenn Sie Tabellen Ergebnisse bevorzugen, Fragen Sie die [MSpeer_topologyresponse](../../relational-databases/system-tables/mspeer-topologyresponse-transact-sql.md) Systemtabelle ab.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle sysadmin oder in der festen Datenbankrolle db_owner.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Peer-zu-Peer-Transaktions Replikation](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
