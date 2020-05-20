---
title: sp_reinitsubscription (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_reinitsubscription
- sp_reinitsubscription_TSQL
helpviewer_keywords:
- sp_reinitsubscription
ms.assetid: d56ae218-6128-4ff9-b06c-749914505c7b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ee9af1ee7057b7a64a62e0ead12ba7e386839587
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82828248"
---
# <a name="sp_reinitsubscription-transact-sql"></a>sp_reinitsubscription (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Kennzeichnet das Abonnement für die erneute Initialisierung. Diese gespeicherte Prozedur wird auf dem Verleger für Pushabonnements ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_reinitsubscription [ [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
        , [ @subscriber = ] 'subscriber'  
    [ , [ @destination_db = ] 'destination_db']  
    [ , [ @for_schema_change = ] 'for_schema_change']  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @ignore_distributor_failure = ] ignore_distributor_failure ]   
    [ , [ @invalidate_snapshot = ] invalidate_snapshot ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert all.  
  
`[ @article = ] 'article'`Der Name des Artikels. der *Artikel* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert all. Bei einer Veröffentlichung mit sofortigem Update *article* muss der Artikel **alle**lauten. andernfalls überspringt die gespeicherte Prozedur die Veröffentlichung und meldet einen Fehler.  
  
`[ @subscriber = ] 'subscriber'`Der Name des Abonnenten. *Subscriber* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @destination_db = ] 'destination_db'`Der Name der Zieldatenbank. *destination_db* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert all.  
  
`[ @for_schema_change = ] 'for_schema_change'`Gibt an, ob die erneute Initialisierung als Ergebnis einer Schema Änderung in der Veröffentlichungs Datenbank erfolgt. *for_schema_change* ist vom Typ **Bit**. der Standardwert ist 0. Wenn der Wert **0**ist, werden aktive Abonnements für Veröffentlichungen, die sofortiges Aktualisieren zulassen, erneut aktiviert, solange die gesamte Veröffentlichung und nicht nur einige der zugehörigen Artikel erneut initialisiert werden. Die erneute Initialisierung wird demnach als Ergebnis von Schemaänderungen initiiert. Bei **1**werden aktive Abonnements erst wieder aktiviert, wenn die Momentaufnahmen-Agent ausgeführt wird.  
  
`[ @publisher = ] 'publisher'`Gibt einen nicht-- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger an. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  *Publisher* sollte nicht für Verleger verwendet werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
`[ @ignore_distributor_failure = ] ignore_distributor_failure`Lässt die erneute Initialisierung zu, auch wenn der Verteiler nicht vorhanden oder offline ist. *ignore_distributor_failure* ist vom Typ **Bit**. der Standardwert ist 0. Wenn der Wert **0**ist, schlägt die erneute Initialisierung fehl, wenn der Verteiler nicht vorhanden oder offline ist.  
  
`[ @invalidate_snapshot = ] invalidate_snapshot`Erklärt die vorhandene Veröffentlichungs Momentaufnahme für ungültig. *invalidate_snapshot* ist vom Typ **Bit**. der Standardwert ist 0. Wenn der Wert **1**ist, wird für die Veröffentlichung eine neue Momentaufnahme generiert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_reinitsubscription** wird bei der Transaktions Replikation verwendet.  
  
 **sp_reinitsubscription** wird für die Peer-zu-Peer-Transaktions Replikation nicht unterstützt.  
  
 Für Abonnements, bei denen die Anfangsmomentaufnahme automatisch angewendet wird und bei denen die Veröffentlichung keine aktualisierbaren Abonnements zulässt, muss der Momentaufnahme-Agent ausgeführt werden, nachdem diese gespeicherte Prozedur ausgeführt wird, sodass Programmdateien für das Schema- und Massenkopieren vorbereitet werden und die Verteilungs-Agents in der Lage sind, die Abonnements neu zu synchronisieren.  
  
 Für Abonnements, bei denen die Anfangsmomentaufnahme automatisch angewendet wird und bei denen die Veröffentlichung aktualisierbare Abonnements zulässt, führt der Verteilungs-Agent eine erneute Synchronisierung für das Abonnement durch, indem die neuesten Programmdateien für das Schema- und Massenkopieren verwendet werden, die zuvor vom Momentaufnahme-Agent erstellt wurden. Der Verteilungs-Agent synchronisiert das Abonnement nach dem Ausführen **sp_reinitsubscription**neu, wenn der Verteilungs-Agent nicht ausgelastet ist. Andernfalls kann die Synchronisierung nach dem Nachrichten Intervall erfolgen (angegeben durch Verteilungs-Agent Befehlszeilenparameter: **MessageInterval**).  
  
 **sp_reinitsubscription** hat keine Auswirkung auf Abonnements, bei denen die Anfangs Momentaufnahme manuell angewendet wird.  
  
 Zum erneuten Synchronisieren anonymer Abonnements für eine Veröffentlichung übergeben Sie **all** oder NULL als *Abonnenten*.  
  
 Die Transaktionsreplikation unterstützt die erneute Initialisierung von Abonnements auf Artikelebene. Die Momentaufnahme des Artikels wird während der nächsten Synchronisierung erneut auf den Abonnenten angewendet, nachdem der Artikel für die erneute Initialisierung markiert wurde. Wenn jedoch abhängige Artikel vorhanden sind, die von demselben Abonnenten abonniert werden, kann die erneute Anwendung der Momentaufnahme auf den Artikel möglicherweise einen Fehler erzeugen, wenn in der Veröffentlichung nicht auch abhängige Artikel unter bestimmten Umständen automatisch erneut initialisiert werden:  
  
-   Wenn 'drop' als Vorabbefehl vor der Erstellung des entsprechenden Artikels verwendet wird, werden Artikel für schemagebundene Sichten und schemagebundene gespeicherte Prozeduren für das Basisobjekt des Artikels ebenfalls für die erneute Initialisierung markiert.  
  
-   Wenn die Schemaoption für den Artikel das Erstellen von Skripts für die deklarative referenzielle Integrität der Primärschlüssel einbezieht, werden Artikel, die über Basistabellen mit Fremdschlüsselbeziehungen zu Basistabellen des erneut initialisierten Artikels verfügen, ebenfalls für die erneute Initialisierung markiert.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_reinittranpushsub](../../relational-databases/replication/codesnippet/tsql/sp-reinitsubscription-tr_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** , Mitglieder der festen Daten Bank Rolle **db_owner** oder der Ersteller des Abonnements können **sp_reinitsubscription**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erneutes Initialisieren eines Abonnements](../../relational-databases/replication/reinitialize-a-subscription.md)   
 [Abonnements erneut initialisieren](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
