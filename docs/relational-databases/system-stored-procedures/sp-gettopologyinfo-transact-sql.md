---
title: sp_gettopologyinfo (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_gettopologyinfo_TSQL
- sp_gettopologyinfo
helpviewer_keywords:
- sp_gettopologyinfo
ms.assetid: 8bbe8a06-a4aa-4219-8402-12db6a4682c6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f847e529ef9f01b873393c2db67d7258ad912071
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85731622"
---
# <a name="sp_gettopologyinfo-transact-sql"></a>sp_gettopologyinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Gibt Informationen über eine Peer-zu-Peer-Transaktionsreplikationstopologie zurück. Führen Sie [sp_requestpeertopologyinfo](../../relational-databases/system-stored-procedures/sp-requestpeertopologyinfo-transact-sql.md) aus, um Informationen zu sammeln, bevor Sie dieses Verfahren ausführen.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_gettopologyinfo [ @request_id = ] request_id  
```  
  
## <a name="arguments"></a>Argumente  
 [ @request_id =] *request_id*  
 Die ID einer Topologiestatusanforderung. *request_id* ist vom Datentyp **int**und hat den Standardwert NULL. Verwenden Sie zum Abrufen einer ID den @request_id Output-Parameter aus [sp_requestpeertopologyinfo](../../relational-databases/system-stored-procedures/sp-requestpeertopologyinfo-transact-sql.md) , oder Fragen Sie die [Mspeer_topologyrequest](../../relational-databases/system-tables/mspeer-topologyrequest-transact-sql.md) Systemtabelle ab.  
  
## <a name="result-sets"></a>Resultsets  
 sp_gettopologyinfo gibt ein Resultset zurück, das aus einer einzelnen XML-Spalte besteht. Die Daten in der XML-Spalte sind identisch mit den Daten in der [MSpeer_topologyresponse](../../relational-databases/system-tables/mspeer-topologyresponse-transact-sql.md) -Systemtabelle.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 sp_gettopologyinfo wird in der Peer-zu-Peer-Transaktionsreplikation verwendet. Führen Sie [sp_requestpeertopologyinfo](../../relational-databases/system-stored-procedures/sp-requestpeertopologyinfo-transact-sql.md) aus, bevor Sie sp_gettopologyinfo ausführen. Diese Prozeduren werden vom Assistenten zum Konfigurieren der Peer-zu-Peer-Topologie verwendet, können jedoch auch direkt verwendet werden, wenn Sie Topologiedaten in einem XML-Format benötigen. Wenn Sie Tabellen Ergebnisse bevorzugen, Fragen Sie die [MSpeer_topologyresponse](../../relational-databases/system-tables/mspeer-topologyresponse-transact-sql.md) Systemtabelle ab.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle sysadmin oder in der festen Datenbankrolle db_owner.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Peer-zu-Peer-Transaktions Replikation](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
