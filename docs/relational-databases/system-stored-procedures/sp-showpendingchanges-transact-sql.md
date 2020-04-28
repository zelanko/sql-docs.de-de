---
title: sp_showpendingchanges (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_showpendingchanges
- sp_showpendingchanges_TSQL
helpviewer_keywords:
- sp_showpendingchanges
ms.assetid: 8013a792-639d-4550-b262-e65d30f9d291
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6b09069cb5289e28d978a4f3b3483e14e63cebb2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "73632744"
---
# <a name="sp_showpendingchanges-transact-sql"></a>sp_showpendingchanges (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt ein Resultset zurück, das die Änderungen anzeigt, die noch repliziert werden müssen. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank und auf dem Abonnenten für die Abonnementdatenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
> [!NOTE]  
>  Diese Prozedur liefert einen geschätzten Wert für die Anzahl der Änderungen und die an diesen Änderungen beteiligten Zeilen. Beispielsweise ruft die Prozedur Informationen entweder vom Verleger oder vom Abonnenten ab, jedoch nicht beides gleichzeitig. Informationen, die im anderen Knoten gespeichert sind, ergeben möglicherweise einen kleineren Änderungssatz für die Synchronisierung als von der Prozedur geschätzt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_showpendingchanges [ [ @destination_server = ] 'destination_server' ]  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article']  
    [ , [ @show_rows = ] show_rows]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @destination_server = ] 'destination_server'`Der Name des Servers, auf den die replizierten Änderungen angewendet werden. *destination_server* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Wenn die *Veröffentlichung* angegeben wird, werden die Ergebnisse nur auf die angegebene Veröffentlichung beschränkt.  
  
`[ @article = ] 'article'`Der Name des Artikels. der *Artikel* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Wenn der *Artikel* angegeben wird, sind die Ergebnisse nur auf den angegebenen Artikel beschränkt.  
  
`[ @show_rows = ] 'show_rows'`Gibt an, ob das Resultset spezifischere Informationen zu ausstehenden Änderungen enthält. der Standardwert ist **0**. Wenn ein Wert von **1** angegeben wird, enthält das Resultset die Spalten is_delete und ROWGUID.  
  
## <a name="result-set"></a>Resultset  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|destination_server|**sysname**|Name des Servers, auf den die Änderungen repliziert werden|  
|pub_name|**sysname**|Der Name der Veröffentlichung.|  
|destination_db_name|**sysname**|Name der Datenbank, in die die Änderungen repliziert werden|  
|is_dest_subscriber|**bit**|Gibt an, ob Änderungen auf einen Abonnenten repliziert werden. Der Wert **1** gibt an, dass die Änderungen auf einen Abonnenten repliziert werden. der Wert **0** bedeutet, dass Änderungen auf einen Verleger repliziert werden.|  
|article_name|**sysname**|Der Name des Artikels für die Tabelle, aus der die Änderungen stammen.|  
|pending_deletes|**int**|Die Anzahl von Löschvorgängen, die auf die Replikation warten.|  
|pending_ins_and_upd|**int**|Die Anzahl von Einfügungen und Updates, die auf die Replikation warten.|  
|is_delete|**bit**|Gibt an, ob die anstehende Änderung ein Löschvorgang ist. Der Wert **1** gibt an, dass die Änderung ein Löschvorgang ist. Erfordert den Wert **1** für @show_rows.|  
|rowguid|**uniqueidentifier**|Die GUID, die die geänderte Zeile identifiziert. Erfordert den Wert **1** für @show_rows.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 sp_showpendingchanges wird für die Mergereplikation verwendet.  
  
 sp_showpendingchanges wird für die Problembehandlung der Mergereplikation verwendet.  
  
 Das Ergebnis von sp_showpendingchanges enthält keine Zeilen in Generation 0.  
  
 Wenn ein für den *Artikel* angegebener Artikel nicht zu der für die *Veröffentlichung* angegebenen Veröffentlichung gehört, wird für pending_deletes und pending_ins_and_upd der Wert 0 zurückgegeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Serverrolle sysadmin oder der festen Datenbankrolle db_owner können sp_showpendingchanges ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
