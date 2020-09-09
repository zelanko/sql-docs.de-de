---
description: sp_registercustomresolver (Transact-SQL)
title: sp_registercustomresolver (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_registercustomresolver
- sp_registercustomresolver_TSQL
helpviewer_keywords:
- sp_registercustomresolver
ms.assetid: 6d2b0472-0e1f-4005-833c-735d1940fe93
author: markingmyname
ms.author: maghan
ms.openlocfilehash: bd973ace7e8edbd7a5ec561fd53a19f8a7a05a92
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89543165"
---
# <a name="sp_registercustomresolver-transact-sql"></a>sp_registercustomresolver (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Registriert einen Geschäftslogikhandler oder einen COM-basierten benutzerdefinierten Konfliktlöser, der während der Synchronisierung der Mergereplikation aufgerufen werden kann. Diese gespeicherte Prozedur wird auf dem Verteiler ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_registercustomresolver [ @article_resolver = ] 'article_resolver'   
    [ , [ @resolver_clsid = ] 'resolver_clsid' ]  
    [ , [ @is_dotnet_assembly = ] 'is_dotnet_assembly' ]  
    [ , [ @dotnet_assembly_name = ] 'dotnet_assembly_name' ]  
    [ , [ @dotnet_class_name = ] 'dotnet_class_name' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @article_resolver = ] 'article_resolver'` Gibt den anzeigen Amen für die benutzerdefinierte Geschäftslogik an, die registriert wird. *article_resolver* ist vom Datentyp **nvarchar (255)** und hat keinen Standardwert.  
  
`[ @resolver_clsid = ] 'resolver_clsid'` Gibt den CLSID-Wert des COM-Objekts an, das registriert wird. Die benutzerdefinierte Geschäftslogik *resolver_clsid* ist vom Datentyp **nvarchar (50)** und hat den Standardwert NULL. Dieser Parameter muss auf eine gültige CLSID oder auf NULL festgelegt werden, wenn Sie eine Assembly für einen Geschäftslogikhandler registrieren.  
  
`[ @is_dotnet_assembly = ] 'is_dotnet_assembly'` Gibt den Typ der benutzerdefinierten Geschäftslogik an, die registriert wird. *is_dotnet_assembly* ist vom Datentyp **nvarchar (50)** und hat den Standardwert false. **true** gibt an, dass die benutzerdefinierte Geschäftslogik, die registriert wird, eine Geschäftslogik Handler-Assembly ist. **false** gibt an, dass es sich um eine COM-Komponente handelt.  
  
`[ @dotnet_assembly_name = ] 'dotnet_assembly_name'` Der Name der Assembly, die den Geschäftslogik Handler implementiert. *dotnet_assembly_name* ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL. Sie müssen den vollständigen Pfad zur Assembly angeben, falls sie nicht im gleichen Verzeichnis wie die ausführbare Datei für den Merge-Agent, im gleichen Verzeichnis wie die Anwendung, mit der der Merge-Agent synchron gestartet wird, oder im globalen Assemblycache (GAC) bereitgestellt wird.  
  
`[ @dotnet_class_name = ] 'dotnet_class_name'` Der Name der Klasse, die überschreibt <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> , um den Geschäftslogik Handler zu implementieren. Der Name muss im Format **Namespace. ClassName**angegeben werden. *dotnet_class_name* ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_registercustomresolver** wird bei der Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_registercustomresolver**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Implementieren eines Geschäftslogikhandlers für einen Mergeartikel](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)   
 [Implementieren eines benutzerdefinierten Konflikt Lösers für einen Mergeartikel](../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md)   
 [sp_lookupcustomresolver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-lookupcustomresolver-transact-sql.md)   
 [sp_unregistercustomresolver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
