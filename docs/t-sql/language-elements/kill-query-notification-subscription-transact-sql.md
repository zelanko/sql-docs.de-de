---
title: KILL QUERY NOTIFICATION SUBSCRIPTION
description: Entfernt Abfragebenachrichtigungsabonnements aus einer Instanz. Mit dieser Anweisung können bestimmte Abonnements bzw. alle Abonnements entfernt werden.
titleSuffix: SQL Server (Transact-SQL)
ms.custom: seo-lt-2019
ms.date: 07/27/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- KILL QUERY NOTIFICATION SUBSCRIPTION
- KILL_QUERY_NOTIFICATION_SUBSCRIPTION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- KILL QUERY NOTIFICATION SUBSCRIPTION statement
- removing subscriptions
- subscriptions [SQL Server query notifications], stopping
- query notifications [SQL Server], subscriptions
ms.assetid: 8aeadf51-286c-4748-bef2-d25858b250bf
author: rothja
ms.author: jroth
ms.openlocfilehash: a4f31f58cdac2032338c2a4a1b6096f1c82070b0
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2020
ms.locfileid: "81636018"
---
# <a name="kill-query-notification-subscription-transact-sql"></a>KILL QUERY NOTIFICATION SUBSCRIPTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Entfernt Abfragebenachrichtigungsabonnements aus der Instanz. Mit dieser Anweisung können bestimmte Abonnements bzw. alle Abonnements entfernt werden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
  
KILL QUERY NOTIFICATION SUBSCRIPTION   
   { ALL | subscription_id }  
```  
  
## <a name="arguments"></a>Argumente  
 ALL  
 Entfernt alle Abonnements in der Instanz.  
  
 *subscription_id*  
 Entfernt das Abonnement mit der Abonnement-ID *subscription_id*.  
  
## <a name="remarks"></a>Bemerkungen  
 Die KILL QUERY NOTIFICATION SUBSCRIPTION-Anweisung entfernt Abfragebenachrichtigungsabonnements, ohne dass eine Benachrichtigungsmeldung erstellt wird.  
  
 Wie in der dynamischen Verwaltungssicht *sys.dm_qn_subscriptions &#40;Transact-SQL&#41;* gezeigt wird, ist [subscription_id](../../relational-databases/system-dynamic-management-views/query-notifications-sys-dm-qn-subscriptions.md) die Abonnement-ID.  
  
 Falls die angegebene Abonnement-ID nicht vorhanden ist, gibt die Anweisung einen Fehler zurück.  
  
## <a name="permissions"></a>Berechtigungen  
 Die Ausführungsberechtigungen für diese Anweisung sind beschränkt auf Mitglieder der festen Serverrolle **sysadmin**.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-removing-all-query-notification-subscriptions-in-the-instance"></a>A. Entfernen aller Abfragebenachrichtigungsabonnements in der Instanz  
 Im folgenden Beispiel werden alle Abfragebenachrichtigungsabonnements in der Instanz entfernt.  
  
```  
KILL QUERY NOTIFICATION SUBSCRIPTION ALL ;  
```  
  
### <a name="b-removing-a-single-query-notification-subscription"></a>B. Entfernen eines einzelnen Abfragebenachrichtigungsabonnements  
 Im folgenden Beispiel wird das Abfragebenachrichtigungsabonnement mit der ID  `73` entfernt.  
  
```  
KILL QUERY NOTIFICATION SUBSCRIPTION 73 ;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys.dm_qn_subscriptions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/query-notifications-sys-dm-qn-subscriptions.md)  
  
  
