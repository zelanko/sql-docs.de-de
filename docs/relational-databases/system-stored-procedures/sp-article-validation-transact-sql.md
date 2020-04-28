---
title: sp_article_validation (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_article_validation_TSQL
- sp_article_validation
helpviewer_keywords:
- sp_article_validation
ms.assetid: 44e7abcd-778c-4728-a03e-7e7e78d3ce22
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6f5ee076163ff3cf0f69daab7ceff115bf5876a6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68769025"
---
# <a name="sp_article_validation-transact-sql"></a>sp_article_validation (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Initiiert eine Datenüberprüfungsanforderung für den angegebenen Artikel. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank und auf dem Abonnenten für die Abonnementdatenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_article_validation [ @publication = ] 'publication'  
    [ , [ @article = ] 'article' ]  
    [ , [ @rowcount_only = ] type_of_check_requested ]  
    [ , [ @full_or_fast = ] full_or_fast ]  
    [ , [ @shutdown_agent = ] shutdown_agent ]  
    [ , [ @subscription_level = ] subscription_level ]  
    [ , [ @reserved = ] reserved ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung, in der der Artikel vorhanden ist. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @article = ] 'article'`Der Name des zu validierenden Artikels. der *Artikel* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @rowcount_only = ] type_of_check_requested`Gibt an, ob nur die Zeilen Anzahl für die Tabelle zurückgegeben wird. *type_of_check_requested* ist vom Datentyp **smallint**. der Standardwert ist **1**.  
  
 Wenn der Wert **0**ist, führen Sie eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Zeilen Anzahl und eine 7,0 kompatible Prüfsumme aus.  
  
 Wenn **1**, wird nur eine Überprüfung der Zeilen Anzahl durchgeführt.  
  
 Wenn **2**, führen Sie eine Zeilen Anzahl und eine binäre Prüfsumme aus.  
  
`[ @full_or_fast = ] full_or_fast`Die Methode, die zum Berechnen der Zeilen Anzahl verwendet wird. *full_or_fast* ist vom Datentyp **tinyint**. die folgenden Werte sind möglich:  
  
|**Wert**|**Beschreibung**|  
|---------------|---------------------|  
|**0**|Führt die vollständige Anzahl mithilfe von count (*) aus.|  
|**1**|Führt eine schnelle Anzahl von **sysindexes. Rows**aus. Das zählen von Zeilen in **sysindexes** ist schneller als das zählen der Zeilen in der eigentlichen Tabelle. **Sysindexes** wird jedoch verzögert aktualisiert, und die Zeilen Anzahl ist möglicherweise nicht korrekt.|  
|**2** (Standardwert)|Führt die bedingte schnelle Zählung durch, indem zuerst die schnelle Methode versucht wird. Ergeben sich mit der schnellen Methode Unterschiede, wird die Methode für die vollständige Zählung verwendet. Wenn *expected_rowcount* NULL ist und die gespeicherte Prozedur verwendet wird, um den Wert zu erhalten, wird immer eine vollständige Anzahl (*) verwendet.|  
  
`[ @shutdown_agent = ] shutdown_agent`Gibt an, ob der Verteilungs-Agent unmittelbar nach Abschluss der Überprüfung heruntergefahren werden soll. *shutdown_agent* ist vom Typ **Bit**. der Standardwert ist **0**. Wenn der Wert **0**ist, wird der Verteilungs-Agent nicht heruntergefahren. Wenn der Wert **1**ist, wird der Verteilungs-Agent nach der Validierung des Artikels heruntergefahren.  
  
`[ @subscription_level = ] subscription_level`Gibt an, ob die Überprüfung von einer Gruppe von Abonnenten übernommen wird. *subscription_level* ist vom Typ **Bit**. der Standardwert ist **0**. Wenn der Wert **0**ist, wird die Überprüfung auf alle Abonnenten angewendet. Wenn der Wert **1**ist, wird die Validierung nur auf eine Teilmenge der Abonnenten angewendet, die durch Aufrufe von **sp_marksubscriptionvalidation** in der aktuellen geöffneten Transaktion angegeben werden.  
  
`[ @reserved = ] reserved` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @publisher = ] 'publisher'`Gibt einen nicht- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verleger an. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  der *Verleger* sollte nicht verwendet werden, wenn die über [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Prüfung auf einem Verleger angefordert wird.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_article_validation** wird bei der Transaktions Replikation verwendet.  
  
 **sp_article_validation** bewirkt, dass Validierungs Informationen für den angegebenen Artikel erfasst und eine Überprüfungs Anforderung an das Transaktionsprotokoll gesendet werden. Wenn der Verteilungs-Agent diese Anforderung empfängt, vergleicht er die Überprüfungsinformationen in der Anforderung mit der Abonnententabelle. Die Ergebnisse der Überprüfung werden im Replikationsmonitor und in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Warnungen angezeigt.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Benutzer mit der Option Alle Berechtigungen für die Quell Tabelle für den zu validierenden Artikel können **sp_article_validation**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replizierte Daten überprüfen](../../relational-databases/replication/validate-data-at-the-subscriber.md)   
 [sp_marksubscriptionvalidation &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-marksubscriptionvalidation-transact-sql.md)   
 [sp_publication_validation &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-publication-validation-transact-sql.md)   
 [sp_table_validation &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-table-validation-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
