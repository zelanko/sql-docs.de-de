---
title: Sp_showpendingchanges (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: cc02137e23c3871066c01ae1a7e9655232c349c7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68032897"
---
# <a name="spshowpendingchanges-transact-sql"></a>sp_showpendingchanges (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt ein Resultset zurück, das die Änderungen anzeigt, die noch repliziert werden müssen. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank und auf dem Abonnenten für die Abonnementdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
 [ @destination_server **=** ] **"***Destination_server***"**  
 Der Name des Servers, auf dem die replizierten Änderungen angewendet werden. *Destination_server* ist **Sysname**, mit dem Standardwert NULL.  
  
 [ @publication **=** ] **"***Veröffentlichung***"**  
 Der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat den Standardwert NULL. Wenn *Veröffentlichung* angegeben ist, werden die Ergebnisse nur für die angegebene Veröffentlichung beschränkt.  
  
 [ @article **=** ] **"***Artikel***"**  
 Der Name des Artikels. *Artikel* ist **Sysname**, hat den Standardwert NULL. Wenn *Artikel* angegeben ist, werden die Ergebnisse nur für den angegebenen Artikel beschränkt.  
  
 [ @show_rows **=** ] *Show_rows*  
 Gibt an, ob das Resultset Weitere Informationen über ausstehende Änderungen mit einem Standardwert von enthält **0**. Wenn ein Wert von **1** angegeben ist, wird das Resultset enthält die Spalten Is_delete und Rowguid.  
  
## <a name="result-set"></a>Resultset  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|destination_server|**sysname**|Name des Servers, auf den die Änderungen repliziert werden|  
|pub_name|**sysname**|Der Name der Veröffentlichung.|  
|destination_db_name|**sysname**|Name der Datenbank, in die die Änderungen repliziert werden|  
|is_dest_subscriber|**bit**|Gibt an, ob Änderungen auf einen Abonnenten repliziert werden. Der Wert **1** gibt an, dass die Änderungen an einen Abonnenten repliziert werden. **0** bedeutet, dass die Änderungen zu einem Verleger repliziert werden.|  
|article_name|**sysname**|Der Name des Artikels für die Tabelle, aus der die Änderungen stammen.|  
|pending_deletes|**int**|Die Anzahl von Löschvorgängen, die auf die Replikation warten.|  
|pending_ins_and_upd|**int**|Die Anzahl von Einfügungen und Updates, die auf die Replikation warten.|  
|is_delete|**bit**|Gibt an, ob die anstehende Änderung ein Löschvorgang ist. Der Wert **1** gibt an, dass die Änderung ein Löschvorgang ist. Erfordert einen Wert von **1** für @show_rows.|  
|rowguid|**uniqueidentifier**|Die GUID, die die geänderte Zeile identifiziert. Erfordert einen Wert von **1** für @show_rows.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 sp_showpendingchanges wird für die Mergereplikation verwendet.  
  
 sp_showpendingchanges wird für die Problembehandlung der Mergereplikation verwendet.  
  
 Das Ergebnis von sp_showpendingchanges enthält keine Zeilen in Generation 0.  
  
 Wenn ein Artikel für angegebene *Artikel* gehört nicht zu die für die angegebene Veröffentlichung *Veröffentlichung* Wert 0 wird für Pending_deletes und Pending_ins_and_upd zurückgegeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Serverrolle sysadmin oder der festen Datenbankrolle db_owner können sp_showpendingchanges ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
