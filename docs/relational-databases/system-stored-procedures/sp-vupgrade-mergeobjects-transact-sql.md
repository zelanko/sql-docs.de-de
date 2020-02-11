---
title: sp_vupgrade_mergeobjects (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: ed0992ff1b6b7de6f93213b612ff05ebcbdb3df5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68042698"
---
# <a name="sp_vupgrade_mergeobjects-transact-sql"></a>sp_vupgrade_mergeobjects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Generiert die artikelspezifischen Trigger, die gespeicherten Prozeduren und Sichten erneut, die zum Nachverfolgen und Anwenden von Datenänderungen für die Mergereplikation verwendet werden. Führen Sie diese Prozedur in den folgenden Situationen aus:  
  
-   Wenn ein Objekt, das für die Replikation erforderlich ist, versehentlich gelöscht wird.  
  
-   Wenn Sie ein Update (beispielsweise ein Hotfix) anwenden, für das Änderungen an einem oder mehreren Replikationsobjekten erforderlich sind. Führen Sie die Prozedur für jeden Knoten aus, nachdem Sie das Update angewendet haben.  
  
 Für das Ausführen dieser gespeicherten Prozedur ist keine erneute Initialisierung der Abonnements erforderlich. Diese Prozedur ist nicht erforderlich, wenn Sie ein Service Pack installieren oder auf eine neue Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aktualisieren.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_vupgrade_mergeobjects [ [@login = ] 'login' ]  
    [ , [ @password = ] 'password' ]  
    [ , [ @security_mode = ] security_mode ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @login = ] 'login'`Der Anmelde Name des Systemadministrators, der beim Erstellen neuer Systemobjekte in der Verteilungs Datenbank verwendet werden soll. *Login* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Dieser Parameter ist nicht erforderlich, wenn *security_mode* auf **1**festgelegt ist. Dies ist die Windows-Authentifizierung.  
  
`[ @password = ] 'password'`Das Kennwort des Systemadministrators, das beim Erstellen neuer Systemobjekte in der Verteilungs Datenbank verwendet werden soll. *Password* ist vom **Datentyp vom Datentyp sysname**. der Standardwert ist **' '** (leere Zeichenfolge). Dieser Parameter ist nicht erforderlich, wenn *security_mode* auf **1**festgelegt ist. Dies ist die Windows-Authentifizierung.  
  
`[ @security_mode = ] 'security_mode'`Der Anmelde Sicherheitsmodus, der beim Erstellen neuer Systemobjekte in der Verteilungs Datenbank verwendet werden soll. *security_mode* ist vom Typ **Bit** und hat den Standardwert **1**. Wenn **** der Wert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 0 ist, wird die-Authentifizierung verwendet. Bei **1**wird die Windows-Authentifizierung verwendet. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_vupgrade_mergeobjects** wird nur für die Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Replikationsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [Aktualisieren von replizierten Datenbanken](../../database-engine/install-windows/upgrade-replicated-databases.md)  
  
  
