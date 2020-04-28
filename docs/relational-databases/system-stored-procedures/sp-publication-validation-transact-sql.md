---
title: sp_publication_validation (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_publication_validation
- sp_publication_validation_TSQL
helpviewer_keywords:
- sp_publication_validation
ms.assetid: 06be2363-00c0-4936-97c1-7347f294a936
author: stevestein
ms.author: sstein
ms.openlocfilehash: bdfe70e3df86f792d250cd7abcc3ef3013e9df19
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "74056236"
---
# <a name="sp_publication_validation-transact-sql"></a>sp_publication_validation (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Initiiert eine Artikelüberprüfungsanforderung für jeden Artikel in der angegebenen Veröffentlichung. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_publication_validation [ @publication = ] 'publication'  
    [ , [ @rowcount_only = ] type_of_check_requested ]  
    [ , [ @full_or_fast = ] full_or_fast ]  
    [ , [ @shutdown_agent = ] shutdown_agent ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @rowcount_only = ] 'rowcount_only'`Gibt an, ob nur die Zeilen Anzahl für die Tabelle zurückgegeben werden soll. *rowcount_only* ist vom Datentyp **smallint** und kann einen der folgenden Werte aufweisen.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**0**|Führt eine mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 kompatible Prüfsummenberechnung durch.<br /><br /> Hinweis: Wenn ein Artikel horizontal gefiltert wird, wird anstelle eines Prüfsummen Vorgangs ein ROWCOUNT-Vorgang ausgeführt.|  
|**1** (Standard)|Führt nur eine Überprüfung der Zeilenanzahl aus.|  
|**2**|Führt eine Überprüfung der Zeilenanzahl und der binären Prüfsumme aus.<br /><br /> Hinweis: für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnenten der Version 7,0 wird nur eine Überprüfung der Zeilen Anzahl durchgeführt.|  
  
`[ @full_or_fast = ] 'full_or_fast'`Die Methode, die zum Berechnen der Zeilen Anzahl verwendet wird. *full_or_fast* ist vom Datentyp **tinyint** und kann einen der folgenden Werte aufweisen.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**0**|Führt eine vollständige Zählung mit COUNT(*) durch.|  
|**1**|Führt eine schnelle Anzahl von **sysindexes. Rows**aus. Das zählen von Zeilen in [sys. sysindexes](../../relational-databases/system-compatibility-views/sys-sysindexes-transact-sql.md) ist wesentlich schneller als das zählen der Zeilen in der eigentlichen Tabelle. Da [sys. sysindexes](../../relational-databases/system-compatibility-views/sys-sysindexes-transact-sql.md) jedoch verzögert aktualisiert wird, ist die Zeilen Anzahl möglicherweise nicht korrekt.|  
|**2** (Standardwert)|Führt eine bedingte schnelle Zählung durch, indem zunächst versucht wird, die schnelle Methode anzuwenden. Ergeben sich mit der schnellen Methode Unterschiede, wird die Methode für die vollständige Zählung verwendet. Wenn *expected_rowcount* NULL ist und die gespeicherte Prozedur verwendet wird, um den Wert zu erhalten, wird immer eine vollständige Anzahl (*) verwendet.|  
  
`[ @shutdown_agent = ] 'shutdown_agent'`Gibt an, ob der Verteilungs-Agent sofort nach Abschluss der Überprüfung heruntergefahren werden soll. *shutdown_agent* ist vom Typ **Bit**. der Standardwert ist **0**. Bei **0**wird der Replikations-Agent nicht heruntergefahren. Wenn der Wert **1**ist, wird der Replikations-Agent nach der Überprüfung des letzten Artikels heruntergefahren.  
  
`[ @publisher = ] 'publisher'`Gibt einen nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verleger an. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  der *Verleger* sollte nicht verwendet werden, wenn die über [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Prüfung auf einem Verleger angefordert wird.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_publication_validation** wird bei der Transaktions Replikation verwendet.  
  
 **sp_publication_validation** können jederzeit aufgerufen werden, nachdem die Artikel, die der Veröffentlichung zugeordnet sind, aktiviert wurden. Die Prozedur kann (einmalig) manuell ausgeführt werden oder als Bestandteil eines regelmäßig geplanten Auftrags, der die Daten überprüft.  
  
 Wenn Ihre Anwendung Abonnenten mit sofortigem Update hat, können **sp_publication_validation** falsche Fehler erkennen. **sp_publication_validation** berechnet zuerst die Zeilen Anzahl oder Prüfsumme auf dem Verleger und dann auf dem Abonnenten. Da der sofort aktualisierbare Trigger ein Update vom Abonnenten zum Verleger möglicherweise weitergibt, nachdem die Zeilenanzahl oder Prüfsumme am Verleger vollständig berechnet wurde, aber bevor die Zeilenanzahl oder Prüfsumme am Abonnenten vollständig berechnet ist, können sich die Werte möglicherweise ändern. Um sicherzustellen, dass die Werte auf dem Abonnenten und auf dem Verleger sich nicht ändern, während eine Veröffentlichung überprüft wird, müssen Sie den MS DTC-Dienst (Microsoft Distributed Transaction Coordinator) auf dem Verleger für die Zeit der Überprüfung beenden.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_publication_validation**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überprüfen von Daten auf dem Abonnenten](../../relational-databases/replication/validate-data-at-the-subscriber.md)   
 [sp_article_validation &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md)   
 [sp_table_validation &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-table-validation-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
