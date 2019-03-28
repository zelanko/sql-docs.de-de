---
title: Sp_vupgrade_mergeobjects (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_vupgrade_mergeobjects
- sp_vupgrade_mergeobjects_TSQL
helpviewer_keywords:
- sp_vupgrade_mergeobjects
ms.assetid: 73257c2e-cc4c-48e7-9d66-7ef045bdd4f5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 293c00f0112dd35de9a546d8c34f237a8561ec40
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58532162"
---
# <a name="spvupgrademergeobjects-transact-sql"></a>sp_vupgrade_mergeobjects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Generiert die artikelspezifischen Trigger, die gespeicherten Prozeduren und Sichten erneut, die zum Nachverfolgen und Anwenden von Datenänderungen für die Mergereplikation verwendet werden. Führen Sie diese Prozedur in den folgenden Situationen aus:  
  
-   Wenn ein Objekt, das für die Replikation erforderlich ist, versehentlich gelöscht wird.  
  
-   Wenn Sie ein Update (beispielsweise ein Hotfix) anwenden, für das Änderungen an einem oder mehreren Replikationsobjekten erforderlich sind. Führen Sie die Prozedur für jeden Knoten aus, nachdem Sie das Update angewendet haben.  
  
 Für das Ausführen dieser gespeicherten Prozedur ist keine erneute Initialisierung der Abonnements erforderlich. Diese Prozedur ist nicht erforderlich, wenn Sie ein Service Pack installieren oder auf eine neue Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aktualisieren.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_vupgrade_mergeobjects [ [@login = ] 'login' ]  
    [ , [ @password = ] 'password' ]  
    [ , [ @security_mode = ] security_mode ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @login = ] 'login'` Ist Sie der Anmeldenamen des Systemadministrators zu verwenden, wenn neue Systemobjekte in der Verteilungsdatenbank zu erstellen. *login* ist vom Datentyp **sysname**und hat den Standardwert NULL. Dieser Parameter ist nicht erforderlich, wenn *Security_mode* nastaven NA hodnotu **1**, d. h. auf Windows-Authentifizierung.  
  
`[ @password = ] 'password'` Ist das Systemadministratorkennwort zu verwenden, wenn neue Systemobjekte in der Verteilungsdatenbank zu erstellen. *Kennwort* ist **Sysname**, hat den Standardwert **''** (leere Zeichenfolge). Dieser Parameter ist nicht erforderlich, wenn *Security_mode* nastaven NA hodnotu **1**, d. h. auf Windows-Authentifizierung.  
  
`[ @security_mode = ] 'security_mode'` Wird von der Anmeldemodus für die Sicherheit zu verwenden, wenn neue Systemobjekte in der Verteilungsdatenbank zu erstellen. *Security_mode* ist **Bit** hat den Standardwert des **1**. Wenn **0**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung verwendet werden. Wenn **1**, Windows-Authentifizierung verwendet werden. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_vupgrade_mergeobjects** wird nur für die Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** .  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Replikationsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [Aktualisieren von replizierten Datenbanken](../../database-engine/install-windows/upgrade-replicated-databases.md)  
  
  
