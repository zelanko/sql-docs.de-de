---
title: Sp_marksubscriptionvalidation (Transact-SQL) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: e49099c2bf0ecd7974531c9f1b840e77805cf218
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54131350"
---
# <a name="spmarksubscriptionvalidation-transact-sql"></a>sp_marksubscriptionvalidation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Markiert die aktuelle geöffnete Transaktion für den angegebenen Abonnenten eine Abonnementstufe Überprüfung-Transaktion ausgeführt werden. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_marksubscriptionvalidation [ @publication = ] 'publication'  
        , [ @subscriber = ] 'subscriber'  
        , [ @destination_db = ] 'destination_db'  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@publication**=] **"***Veröffentlichung***"**  
 Der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
 [ **@subscriber**=] **"***Abonnenten***"**  
 Der Name des Abonnenten. *Abonnenten* ist vom Datentyp Sysname und hat keinen Standardwert.  
  
 [  **@destination_db=**] **"***Destination_db***"**  
 Der Name der Zieldatenbank. *Destination_db* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@publisher=** ] **"***Verleger***"**  
 Gibt einen nicht- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger. *Publisher* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  *Publisher* sollte nicht verwendet werden, für eine Veröffentlichung, zu dem gehört eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_marksubscriptionvalidation** wird in Transaktionsreplikationen verwendet.  
  
 **Sp_marksubscriptionvalidation** unterstützt keine nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnenten.  
  
 Für nicht - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Herausgeber, Sie können nicht ausgeführt werden **Sp_marksubscriptionvalidation** aus einer expliziten Transaktion heraus. Das liegt daran, dass explizite Transaktionen nicht über die Verbindung eines Verbindungsservers unterstützt werden, die für den Zugriff auf den Verleger verwendet wird.  
  
 **Sp_marksubscriptionvalidation** muss verwendet werden, zusammen mit [Sp_article_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md), geben Sie einen Wert **1** für  *Subscription_level*, und kann verwendet werden, mit anderen Aufrufen von **Sp_marksubscriptionvalidation** um die aktuell geöffnete Transaktion für andere Abonnenten zu markieren.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_marksubscriptionvalidation**.  
  
## <a name="example"></a>Beispiel  
 Die folgende Abfrage kann auf die Verlegerdatenbank angewendet werden, um Befehle mit Überprüfung auf Abonnementebene bereitzustellen. Diese Befehle werden von den Verteilungs-Agents der angegebenen Abonnenten erfasst. Beachten Sie, dass es sich bei die erste Transaktion Artikel überprüft "**art1**", während die zweite Transaktion überprüft"**art2**". Beachten Sie, dass die Aufrufe an **Sp_marksubscriptionvalidation** und [Sp_article_validation &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) in einer Transaktion gekapselt wurden. Es wird empfohlen, nur einen Aufruf von [Sp_article_validation &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) pro Transaktion. Grund hierfür ist, [Sp_article_validation &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) enthält eine freigegebene Tabellensperre für die Quelltabelle für die Dauer der Transaktion. Die Transaktion muss so kurz wie möglich sein, um die Parallelität zu maximieren.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Überprüfen von replizierten Daten](../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
  
