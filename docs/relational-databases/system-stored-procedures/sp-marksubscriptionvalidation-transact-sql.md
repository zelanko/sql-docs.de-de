---
title: sp_marksubscriptionvalidation (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_marksubscriptionvalidation
- sp_marksubscriptionvalidation_TSQL
helpviewer_keywords:
- sp_marksubscriptionvalidation
ms.assetid: e68fe0b9-5993-4880-917a-b0f661f8459b
author: stevestein
ms.author: sstein
ms.openlocfilehash: bb8c38d24fbf6c96c61a7b2e83874d15218797c3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68092674"
---
# <a name="sp_marksubscriptionvalidation-transact-sql"></a>sp_marksubscriptionvalidation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Markiert die aktuelle geöffnete Transaktion als Validierungs Transaktion auf Abonnement Ebene für den angegebenen Abonnenten. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_marksubscriptionvalidation [ @publication = ] 'publication'  
        , [ @subscriber = ] 'subscriber'  
        , [ @destination_db = ] 'destination_db'  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @subscriber = ] 'subscriber'`Der Name des Abonnenten. *Subscriber* ist vom Datentyp sysname und hat keinen Standardwert.  
  
`[ @destination_db = ] 'destination_db'`Der Name der Zieldatenbank. *destination_db* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publisher = ] 'publisher'`Gibt einen nicht- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verleger an. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  *Publisher* sollte nicht für eine Veröffentlichung verwendet werden, die zu einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger gehört.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_marksubscriptionvalidation** wird bei der Transaktions Replikation verwendet.  
  
 **sp_marksubscriptionvalidation** unterstützt keine nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Abonnenten.  
  
 Bei nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verlegern können **sp_marksubscriptionvalidation** nicht innerhalb einer expliziten Transaktion ausgeführt werden. Das liegt daran, dass explizite Transaktionen nicht über die Verbindung eines Verbindungsservers unterstützt werden, die für den Zugriff auf den Verleger verwendet wird.  
  
 **sp_marksubscriptionvalidation** müssen in Verbindung mit [sp_article_validation &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md)verwendet werden, wobei der Wert **1** für *subscription_level*angegeben und mit anderen Aufrufen von **sp_marksubscriptionvalidation** verwendet werden kann, um die aktuelle geöffnete Transaktion für andere Abonnenten zu markieren.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_marksubscriptionvalidation**ausführen.  
  
## <a name="example"></a>Beispiel  
 Die folgende Abfrage kann auf die Verlegerdatenbank angewendet werden, um Befehle mit Überprüfung auf Abonnementebene bereitzustellen. Diese Befehle werden von den Verteilungs-Agents der angegebenen Abonnenten erfasst. Beachten Sie, dass die erste Transaktion den Artikel "**art1**" überprüft, während die zweite Transaktion "**art2**" überprüft. Beachten Sie außerdem, dass die Aufrufe von **sp_marksubscriptionvalidation** und [sp_article_validation &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) in einer Transaktion gekapselt wurden. Es wird nur ein [sp_article_validation &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) pro Transaktion empfohlen. Dies liegt daran, dass [sp_article_validation &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) für die Dauer der Transaktion eine freigegebene Tabellensperre für die Quell Tabelle enthält. Die Transaktion muss so kurz wie möglich sein, um die Parallelität zu maximieren.  
  
```  
begin tran  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub', @destination_db = 'SubDB'  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub2', @destination_db = 'SubDB'  
  
exec sp_article_validation @publication = 'pub1', @article = 'art1',  
 @rowcount_only = 0, @full_or_fast = 0, @shutdown_agent = 0,  
 @subscription_level = 1  
  
commit tran  
  
begin tran  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub', @destination_db = 'SubDB'  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub2', @destination_db = 'SubDB'  
  
exec sp_article_validation @publication = 'pub1', @article = 'art2',  
 @rowcount_only = 0, @full_or_fast = 0, @shutdown_agent = 0,  
 @subscription_level = 1  
  
commit tran  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Überprüfen von replizierten Daten](../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
  
