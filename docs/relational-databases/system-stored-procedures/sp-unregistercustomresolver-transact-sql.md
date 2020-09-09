---
description: sp_unregistercustomresolver (Transact-SQL)
title: sp_unregistercustomresolver (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_unregistercustomresolver_TSQL
- sp_unregistercustomresolver
helpviewer_keywords:
- sp_unregistercustomresolver
ms.assetid: 08bd20c8-c6be-4be2-be9f-2b5e1d7bee43
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 54d4b4ff0b08f0cd5a2a1275c0f1bc65d462137e
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89547310"
---
# <a name="sp_unregistercustomresolver-transact-sql"></a>sp_unregistercustomresolver (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Hebt die Registrierung eines zuvor registrierten Geschäftslogikmoduls auf. Geschäftslogik kann in Form einer COM-Komponente oder einer [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework-Assembly vorliegen. Diese gespeicherte Prozedur wird auf dem Verteiler ausgeführt, auf dem die benutzerdefinierte Geschäftslogik registriert wurde.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_unregistercustomresolver [ @article_resolver = ] 'article_resolver'   
```  
  
## <a name="arguments"></a>Argumente  
`[ @article_resolver = ] 'article_resolver'` Gibt den Namen der benutzerdefinierten Geschäftslogik an, deren Registrierung aufgehoben wird. *article_resolver* ist vom Datentyp **nvarchar (255)** und hat keinen Standardwert. Wenn es sich bei der zu entfernenden Geschäftslogik um eine COM-Komponente handelt, ist dieser Parameter der Anzeigename der Komponente. Handelt es sich bei der Geschäftslogik um eine .NET Framework-Assembly, ist dieser Parameter der Name der Assembly.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_unregistercustomresolver** wird bei der Mergereplikation verwendet.  
  
 Verwenden Sie [sp_enumcustomresolvers](../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) auf einem beliebigen Server in der Replikations Topologie, um die Liste der registrierten benutzerdefinierten Geschäftslogik Module oder der für die Topologie verfügbaren com-Resolver zurückzugeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_unregistercustomresolver**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_lookupcustomresolver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-lookupcustomresolver-transact-sql.md)   
 [sp_registercustomresolver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
