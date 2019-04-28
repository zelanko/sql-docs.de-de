---
title: Sp_lookupcustomresolver (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_lookupcustomresolver_TSQL
- sp_lookupcustomresolver
helpviewer_keywords:
- sp_lookupcustomresolver
ms.assetid: 356a7b8a-ae53-4fb5-86ee-fcfddbf23ddd
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b7f1bfc868b34ac16e1c38aedc9193002d35d5b8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62959640"
---
# <a name="splookupcustomresolver-transact-sql"></a>sp_lookupcustomresolver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt die Informationen zu einem Geschäftslogikhandler oder den Wert des Klassenbezeichners (CLSID, Class Identifier) einer COM-basierten Komponente für benutzerdefinierte Konfliktlöser zurück, die auf dem Verteiler registriert sind. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_lookupcustomresolver [ @article_resolver = ] 'article_resolver'   
    [, [ @resolver_clsid = ] 'resolver_clsid' OUTPUT ]  
    [ , [ @is_dotnet_assembly = ] is_dotnet_assembly OUTPUT ]  
    [ , [ @dotnet_assembly_name = ] 'dotnet_assembly_name' OUTPUT ]  
    [ , [ @dotnet_class_name = ] 'dotnet_class_name' OUTPUT ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @article_resolver = ] 'article_resolver'` Gibt den Namen der benutzerdefinierten Geschäftslogik an, deren Registrierung aufgehoben. *Article_resolver* ist **nvarchar(255)**, hat keinen Standardwert. Wenn die Geschäftslogik, die entfernt wird, eine COM-Komponente ist, ist dieser Parameter der angezeigte Name der Komponente. Wenn die Geschäftslogik eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework-Assembly ist, ist dieser Parameter der Name der Assembly.  
  
`[ @resolver_clsid = ] 'resolver_clsid' OUTPUT` Ist der CLSID-Wert, der das COM-Objekt, das durch den Namen der benutzerdefinierten Geschäftslogik im Zusammenhang der *Article_resolver* Parameter. *Resolver_clsid* ist **nvarchar(50)**, hat den Standardwert NULL.  
  
`[ @is_dotnet_assembly = ] 'is_dotnet_assembly' OUTPUT` Gibt den Typ der benutzerdefinierten Geschäftslogik, der registriert wird. *Is_dotnet_assembly* ist **Bit**, hat den Standardwert 0. **1** gibt an, dass die benutzerdefinierte Geschäftslogik registriert eine Geschäftslogikhandler-Assembly **0** gibt an, dass es sich um eine COM-Komponente ist.  
  
`[ @dotnet_assembly_name = ] 'dotnet_assembly_name' OUTPUT` Ist der Name der Assembly, die den Geschäftslogikhandler implementiert. *Dotnet_assembly_name* ist **nvarchar(255)**, hat den Standardwert NULL.  
  
`[ @dotnet_class_name = ] 'dotnet_class_name' OUTPUT` Der Name der Klasse, die überschreibt <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> den Geschäftslogikhandler implementiert. *Dotnet_class_name* ist **nvarchar(255)**, hat den Standardwert NULL.  
  
`[ @publisher = ] 'publisher'` Ist der Name des Verlegers. *Publisher* ist **Sysname**, hat den Standardwert NULL. Verwenden Sie diesen Parameter, wenn die gespeicherte Prozedur nicht vom Verleger aufgerufen wird. Wenn keine Angabe erfolgt, wird davon ausgegangen, dass der lokale Server der Verleger ist.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_lookupcustomresolver** wird bei der Mergereplikation verwendet.  
  
 **Sp_lookupcustomresolver** gibt einen Nullwert für *Resolver_clsid* Wenn die Komponente ist nicht registriert an der Verteilung und den Wert "00000000-0000-0000-0000-000000000000" bei die Registrierung zu gehört ein .NET Framework-Assembly, die als Geschäftslogikhandler registriert werden.  
  
 **Sp_lookupcustomresolver** wird aufgerufen, indem [Sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) und [Sp_changemergearticle](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) zur Überprüfung des angegebenen *Article_resolver*.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Db_owner** festen Datenbankrolle für die Veröffentlichungsdatenbank können ausführen **Sp_lookupcustomresolver**.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterte Konflikterkennung und -lösung bei der Mergereplikation](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Ausführen der Geschäftslogik während der Mergesynchronisierung](../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md)   
 [Implementieren eines Geschäftslogikhandlers für einen Mergeartikel](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)   
 [Angeben eines Mergeartikelkonfliktlösers](../../relational-databases/replication/publish/specify-a-merge-article-resolver.md)   
 [sp_registercustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md)   
 [sp_unregistercustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
