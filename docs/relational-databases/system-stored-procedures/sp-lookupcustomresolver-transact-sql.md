---
title: sp_lookupcustomresolver (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 274276a55a7b3e91ff85330a0810f01786a5a080
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67937907"
---
# <a name="sp_lookupcustomresolver-transact-sql"></a>sp_lookupcustomresolver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt die Informationen zu einem Geschäftslogikhandler oder den Wert des Klassenbezeichners (CLSID, Class Identifier) einer COM-basierten Komponente für benutzerdefinierte Konfliktlöser zurück, die auf dem Verteiler registriert sind. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
`[ @article_resolver = ] 'article_resolver'`Gibt den Namen der benutzerdefinierten Geschäftslogik an, deren Registrierung aufgehoben wird. *article_resolver* ist vom Datentyp **nvarchar (255)** und hat keinen Standardwert. Wenn die Geschäftslogik, die entfernt wird, eine COM-Komponente ist, ist dieser Parameter der angezeigte Name der Komponente. Wenn die Geschäftslogik eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework-Assembly ist, ist dieser Parameter der Name der Assembly.  
  
`[ @resolver_clsid = ] 'resolver_clsid' OUTPUT`Der CLSID-Wert des COM-Objekts, das dem Namen der benutzerdefinierten Geschäftslogik zugeordnet ist, die im *article_resolver* -Parameter angegeben ist. *resolver_clsid* ist vom Datentyp **nvarchar (50)** und hat den Standardwert NULL.  
  
`[ @is_dotnet_assembly = ] 'is_dotnet_assembly' OUTPUT`Gibt den Typ der benutzerdefinierten Geschäftslogik an, die registriert wird. *is_dotnet_assembly* ist vom Typ **Bit**. der Standardwert ist 0. **1** gibt an, dass die benutzerdefinierte Geschäftslogik, die registriert wird, eine Geschäftslogik Handler-Assembly ist. **0** gibt an, dass es sich um eine COM-Komponente handelt.  
  
`[ @dotnet_assembly_name = ] 'dotnet_assembly_name' OUTPUT`Der Name der Assembly, die den Geschäftslogik Handler implementiert. *dotnet_assembly_name* ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL.  
  
`[ @dotnet_class_name = ] 'dotnet_class_name' OUTPUT`Der Name der Klasse, die überschreibt <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> , um den Geschäftslogik Handler zu implementieren. *dotnet_class_name* ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL.  
  
`[ @publisher = ] 'publisher'`Der Name des Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Verwenden Sie diesen Parameter, wenn die gespeicherte Prozedur nicht vom Verleger aufgerufen wird. Wenn keine Angabe erfolgt, wird davon ausgegangen, dass der lokale Server der Verleger ist.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_lookupcustomresolver** wird bei der Mergereplikation verwendet.  
  
 **sp_lookupcustomresolver** gibt einen NULL-Wert für *resolver_clsid* zurück, wenn die Komponente nicht bei der Verteilung registriert ist, und den Wert "00000000-0000-0000-0000-000000000000", wenn die Registrierung zu einer .NET Framework Assembly gehört, die als Geschäftslogik Handler registriert ist.  
  
 **sp_lookupcustomresolver** wird von [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) und [sp_changemergearticle](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) aufgerufen, um die angegebene *article_resolver*zu überprüfen.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **db_owner** Fixed-Daten Bank Rolle in der Veröffentlichungs Datenbank können **sp_lookupcustomresolver**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Konflikterkennung und-Lösung bei der Mergereplikation](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Ausführen von Geschäftslogik während der Mergesynchronisierung](../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md)   
 [Implementieren eines Geschäftslogik Handlers für einen Mergeartikel](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)   
 [Angeben eines mergeartikelresolvers](../../relational-databases/replication/publish/specify-a-merge-article-resolver.md)   
 [sp_registercustomresolver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md)   
 [sp_unregistercustomresolver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
