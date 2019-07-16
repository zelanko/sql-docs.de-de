---
title: Sp_publication_validation (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: c7e6323c8a20aec7d464f7aa6f11a27fc24728d3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67896624"
---
# <a name="sppublicationvalidation-transact-sql"></a>sp_publication_validation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Initiiert eine Artikelüberprüfungsanforderung für jeden Artikel in der angegebenen Veröffentlichung. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_publication_validation [ @publication = ] 'publication'  
    [ , [ @rowcount_only = ] type_of_check_requested ]  
    [ , [ @full_or_fast = ] full_or_fast ]  
    [ , [ @shutdown_agent = ] shutdown_agent ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@publication=** ] **"** _Veröffentlichung"_  
 Der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
 [ **@rowcount_only=** ] *Rowcount_only*  
 Gibt an, ob nur die Zeilenanzahl für die Tabelle zurückgegeben werden soll. *Rowcount_only* ist **Smallint** und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**0**|Führt eine mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 kompatible Prüfsummenberechnung durch.<br /><br /> Hinweis: Wenn ein Artikel horizontal gefiltert wird, wird ein Vorgang für die Überprüfung der Zeilenanzahl anstelle einer prüfsummenberechnung ausgeführt.|  
|**1** (Standard)|Führt nur eine Überprüfung der Zeilenanzahl aus.|  
|**2**|Führt eine Überprüfung der Zeilenanzahl und der binären Prüfsumme aus.<br /><br /> Hinweis: Für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version 7.0-Abonnenten können nur eine Überprüfung der Zeilenanzahl wird ausgeführt.|  
  
 [ **@full_or_fast=** ] *Full_or_fast*  
 Die Methode, mit der die Zeilenanzahl berechnet wird. *Full_or_fast* ist **Tinyint** und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**0**|Führt eine vollständige Zählung mit COUNT(*) durch.|  
|**1**|Führt eine schnelle Zählung von **sysindexes.rows**. Zählen der Zeilen im [sys.sysindexes](../../relational-databases/system-compatibility-views/sys-sysindexes-transact-sql.md) ist wesentlich schneller als das Zählen von Zeilen in der eigentlichen Tabelle. Aber da [sys.sysindexes](../../relational-databases/system-compatibility-views/sys-sysindexes-transact-sql.md) nur verzögert aktualisiert, die Zeilenanzahl möglicherweise nicht ganz genau.|  
|**2** (Standardwert)|Führt eine bedingte schnelle Zählung durch, indem zunächst versucht wird, die schnelle Methode anzuwenden. Ergeben sich mit der schnellen Methode Unterschiede, wird die Methode für die vollständige Zählung verwendet. Wenn *Expected_rowcount* NULL ist und die gespeicherte Prozedur wird verwendet, um den Wert abzurufen, wird immer eine vollständige Zählung mit COUNT(*) verwendet.|  
  
`[ @shutdown_agent = ] shutdown_agent` Ist, gibt an, ob der Verteilungs-Agent sofort nach dem Abschluss der Überprüfung heruntergefahren werden soll. *Shutdown_agent* ist **Bit**, hat den Standardwert **0**. Wenn **0**, Replikations-Agent nicht heruntergefahren. Wenn **1**, Replikations-Agent nach der Überprüfung des letzten Artikels beendet.  
  
`[ @publisher = ] 'publisher'` Gibt einen nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger. *Publisher* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  *Publisher* sollte nicht verwendet werden, bei der Überprüfung auf Anforderung eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_publication_validation** wird in Transaktionsreplikationen verwendet.  
  
 **Sp_publication_validation** kann aufgerufen werden, zu einem beliebigen Zeitpunkt, nachdem die Artikel für die Veröffentlichung aktiviert wurden. Die Prozedur kann (einmalig) manuell ausgeführt werden oder als Bestandteil eines regelmäßig geplanten Auftrags, der die Daten überprüft.  
  
 Wenn die Anwendung sofort aktualisierbaren Abonnenten, **Sp_publication_validation** möglicherweise falsche Fehler erkennen. **Sp_publication_validation** berechnet zuerst die Zeilenanzahl oder Prüfsumme auf dem Verleger, und klicken Sie dann auf dem Abonnenten. Da der sofort aktualisierbare Trigger ein Update vom Abonnenten zum Verleger möglicherweise weitergibt, nachdem die Zeilenanzahl oder Prüfsumme am Verleger vollständig berechnet wurde, aber bevor die Zeilenanzahl oder Prüfsumme am Abonnenten vollständig berechnet ist, können sich die Werte möglicherweise ändern. Um sicherzustellen, dass die Werte auf dem Abonnenten und auf dem Verleger sich nicht ändern, während eine Veröffentlichung überprüft wird, müssen Sie den MS DTC-Dienst (Microsoft Distributed Transaction Coordinator) auf dem Verleger für die Zeit der Überprüfung beenden.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder die **Db_owner** feste Datenbankrolle können ausführen **Sp_publication_validation**.  
  
## <a name="see-also"></a>Siehe auch  
 [Überprüfen der Daten am Abonnenten](../../relational-databases/replication/validate-data-at-the-subscriber.md)   
 [sp_article_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md)   
 [Sp_table_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-validation-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
