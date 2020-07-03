---
title: sp_helppeerresponses (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helppeerresponses_TSQL
- sp_helppeerresponses
helpviewer_keywords:
- sp_helppeerresponses
ms.assetid: e55789d1-43fb-4a37-9e5e-60ccef122a5d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7b6e6ed76873abba0988045a1c336b4a34fb5d48
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85893529"
---
# <a name="sp_helppeerresponses-transact-sql"></a>sp_helppeerresponses (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt alle Antworten auf eine bestimmte Status Anforderung zurück, die von einem Teilnehmer in einer Peer-zu-Peer-Replikations Topologie empfangen wurde, in der die Anforderung durch Ausführen von [sp_helppeerrequests](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md) in einer beliebigen veröffentlichten Datenbank in der Topologie initiiert wurde. Diese gespeicherte Prozedur wird für die Veröffentlichungsdatenbank auf einem Verleger ausgeführt, der an der Peer-zu-Peer-Replikationstopologie beteiligt ist. Weitere Informationen finden Sie unter [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helppeerresponses [ @request_id = ] request_id  
```  
  
## <a name="arguments"></a>Argumente  
`[ @request_id = ] request_id`Die ID einer bestimmten Status Anforderung. *request_id* ist vom Datentyp **int**und hat keinen Standardwert.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**request_id**|**int**|ID der Statusanforderung.|  
|**chtern**|**sysname**|Der Name des Peers, der die Antwort generiert hat.|  
|**peer_db**|**sysname**|Der Datenbankname auf dem Peer, der die Antwort generiert hat.|  
|**received_date**|**datetime**|Datum und Uhrzeit, zu dem der Anforderer die vom Peer gesendete Antwort erhalten hat.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_helppeerresponses** wird in der Peer-zu-Peer-Transaktions Replikation verwendet.  
  
 **sp_helppeerresponses** Prozedur wird verwendet, wenn eine in einer Peer-zu-Peer-Topologie veröffentlichte Datenbank wieder hergestellt wird.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_helppeerresponses**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_deletepeerrequesthistory &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-deletepeerrequesthistory-transact-sql.md)   
 [sp_helppeerrequests &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helppeerrequests-transact-sql.md)  
  
  
