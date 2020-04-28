---
title: sp_configure_peerconflictdetection (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_configure_peerconflictdetection_TSQL
- sp_configure_peerconflictdetection
helpviewer_keywords:
- sp_configure_peerconflictdetection
ms.assetid: 45117cb2-3247-433f-ba3d-7fa19514b1c3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8a8cc9930ddf85dea60999e3b63dbcebaaf42d8f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68215945"
---
# <a name="sp_configure_peerconflictdetection-transact-sql"></a>sp_configure_peerconflictdetection (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Konfiguriert die Konflikterkennung für eine Veröffentlichung, die Teil einer Peer-zu-Peer-Transaktionsreplikationstopologie ist. Weitere Informationen finden Sie unter [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md). Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_configure_peerconflictdetection [ @publication = ] 'publication'  
    [ , [ @action = ] 'action']  
    [ , [ @originator_id = ] originator_id ]  
    [ , [ @conflict_retention = ] conflict_retention ]  
    [ , [ @continue_onconflict = ] 'continue_onconflict']  
    [ , [ @local = ] 'local']  
    [ , [ @timeout = ] timeout ]  
  
```  
  
## <a name="arguments"></a>Argumente  
 [ @publication=] "*Veröffentlichung*"  
 Der Name der Veröffentlichung, für die die Konflikterkennung konfiguriert werden soll. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
 [ @action= ] "*Action*"  
 Gibt an, ob die Konflikterkennung für eine Veröffentlichung aktiviert oder deaktiviert werden soll. *Action* ist vom Datentyp **nvarchar (5)**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**fähigen**|Aktiviert die Konflikterkennung für eine Veröffentlichung.|  
|**ier**|Deaktiviert die Konflikterkennung für eine Veröffentlichung.|  
|NULL (Standard)||  
  
 [ @originator_id= ] *originator_id*  
 Gibt eine ID für einen Knoten in einer Peer-zu-Peer-Topologie an. *originator_id* ist vom Datentyp **int**und hat den Standardwert NULL. Diese ID wird für die Konflikterkennung verwendet, wenn *Action* auf **enable**festgelegt ist. Geben Sie eine positive ID ungleich 0 an, die in der Topologie noch nicht verwendet wurde. Zum Anzeigen einer Liste der bereits verwendeten IDs fragen Sie die [Mspeer_originatorid_history](../../relational-databases/system-tables/mspeer-originatorid-history-transact-sql.md) -Systemtabelle ab.  
  
 [ @conflict_retention= ] *conflict_retention*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ @continue_onconflict= ] '*continue_onconflict*']  
 Legt fest, ob der Verteilungs-Agent nach Erkennung eines Konflikts die Verarbeitung von Änderungen fortsetzt. *continue_onconflict* ist vom Datentyp **nvarchar (5)** und hat den Standardwert false.  
  
> [!CAUTION]  
>  Es wird empfohlen, den Standardwert FALSE zu verwenden. Wenn diese Option auf TRUE festgelegt wird, versucht der Verteilungs-Agent, die Datenkonvergenz in der Topologie herbeizuführen, indem die konfliktverursachende Zeile von dem Knoten mit der höchsten Absender-ID angewendet wird. Bei dieser Methode ist keine Konvergenz garantiert. Sie sollten sicherstellen, dass die Topologie nach der Erkennung eines Konflikts konsistent ist. Weitere Informationen finden Sie im Abschnitt "Konfliktbehandlung" unter [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).  
  
 [ @local= ] "*local*"  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ @timeout= ] *Timeout*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 sp_configure_peerconflictdetection wird in der Peer-zu-Peer-Transaktionsreplikation verwendet. Zur Verwendung der Konflikterkennung müssen auf allen Knoten oder [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] höhere Versionen ausgeführt werden. und die Erkennung muss für alle Knoten aktiviert sein.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle sysadmin oder in der festen Datenbankrolle db_owner.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konflikterkennung bei der Peer-zu-Peer-Replikation](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)   
 [Peer-zu-Peer-Transaktions Replikation](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
