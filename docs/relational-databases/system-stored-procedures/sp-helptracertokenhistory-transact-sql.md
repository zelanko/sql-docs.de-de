---
title: sp_helptracertokenhistory (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helptracertokenhistory_TSQL
- sp_helptracertokenhistory
helpviewer_keywords:
- sp_helptracertokenhistory
ms.assetid: 96910d1c-be76-43eb-9c93-4477e6761749
author: stevestein
ms.author: sstein
ms.openlocfilehash: b8755bea5e318d1ded2631a2253134fd8721a421
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68771153"
---
# <a name="sp_helptracertokenhistory-transact-sql"></a>sp_helptracertokenhistory (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Gibt detaillierte Latenzzeitinformationen für die angegebenen Überwachungstoken zurück, wobei für jeden Abonnenten eine Zeile zurückgegeben wird. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank oder auf dem Verteiler für die Verteilungsdatenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helptracertokenhistory [ @publication = ] 'publication'   
        , [ @tracer_id = ] tracer_id  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publisher_db' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung, in die das Überwachungs Token eingefügt wurde. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @tracer_id = ] tracer_id`Die ID des Überwachungs Tokens in der [MStracer_tokens &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md) Tabelle, für die Verlaufs Informationen zurückgegeben werden. *tracer_id* ist vom Datentyp **int**und hat keinen Standardwert.  
  
`[ @publisher = ] 'publisher'`Der Name des Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]
>  Dieser Parameter sollte nur für nicht-- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger angegeben werden.  
  
`[ @publisher_db = ] 'publisher_db'`Der Name der Veröffentlichungs Datenbank. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Dieser Parameter wird ignoriert, wenn die gespeicherte Prozedur auf dem Verleger ausgeführt wird.  
  
## <a name="result-set"></a>Resultset  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**distributor_latency**|**BIGINT**|Anzahl der Sekunden zwischen dem Commit des Überwachungstokendatensatzes auf dem Verleger und dem Commit des Datensatzes auf dem Verteiler|  
|**Abonnenten**|**sysname**|Name des Abonnenten, der das Überwachungstoken empfing|  
|**subscriber_db**|**sysname**|Name der Abonnementdatenbank, in die der Überwachungstokendatensatz eingefügt wurde|  
|**subscriber_latency**|**BIGINT**|Anzahl der Sekunden zwischen dem Commit des Überwachungstokendatensatzes auf dem Verteiler und dem Commit des Datensatzes auf dem Abonnenten|  
|**overall_latency**|**BIGINT**|Anzahl der Sekunden zwischen dem Commit des Überwachungstokendatensatzes auf dem Verleger und dem Commit des Datensatzes auf dem Abonnenten|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_helptracertokenhistory** wird bei der Transaktions Replikation verwendet.  
  
 Führen Sie [sp_helptracertokens &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql.md) aus, um eine Liste der Überwachungs Token für die Veröffentlichung zu erhalten.  
  
 Der Wert NULL im Resultset bedeutet, dass keine Latenzzeitstatistik berechnet werden kann. Dies liegt daran, dass das Überwachungstoken nicht auf dem Verteiler oder einem der Abonnenten empfangen wurde.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_tracertokens](../../relational-databases/replication/codesnippet/tsql/sp-helptracertokenhistor_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** , der festen Daten Bank Rolle **db_owner** in der Veröffentlichungs Datenbank oder **db_owner** festen Datenbank-oder **replmonitor** -Rollen in der Verteilungs Datenbank können **sp_helptracertokenhistory**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Messen der Latenzzeit und Überprüfen der Verbindungen bei Transaktionsreplikationen](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)   
 [sp_deletetracertokenhistory &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-deletetracertokenhistory-transact-sql.md)  
  
  
