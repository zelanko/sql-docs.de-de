---
title: Sp_droplinkedsrvlogin (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_droplinkedsrvlogin_TSQL
- sp_droplinkedsrvlogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_droplinkedsrvlogin
ms.assetid: 75a4a040-72d5-4d29-8304-de0aa481ad4b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 505e75dfab9ea4e2ba44d8ef12f0ba5c7eecbde2
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58533512"
---
# <a name="spdroplinkedsrvlogin-transact-sql"></a>sp_droplinkedsrvlogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Entfernt eine vorhandene Zuordnung zwischen einem Anmeldenamen auf dem lokalen Server, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird, und einem Anmeldenamen auf dem Verbindungsserver.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_droplinkedsrvlogin [ @rmtsrvname= ] 'rmtsrvname' ,   
   [ @locallogin= ] 'locallogin'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @rmtsrvname = ] 'rmtsrvname'` Der Name eines Verbindungsservers, der die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -anmeldenamenzuordnung gilt. *Rmtsrvname* ist **Sysname**, hat keinen Standardwert. *Rmtsrvname* muss bereits vorhanden sein.  
  
`[ @locallogin = ] 'locallogin'` Ist die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldenamen auf dem lokalen Server, die eine Zuordnung mit dem Verbindungsserver *Rmtsrvname*. *Locallogin* ist **Sysname**, hat keinen Standardwert. Eine Zuordnung für *Locallogin* zu *Rmtsrvname* muss bereits vorhanden sein. Wenn der Wert NULL ist, erstellt die standardzuordnung von **Sp_addlinkedserver**, die alle Anmeldenamen auf dem lokalen Server Anmeldenamen auf dem Verbindungsserver zuordnet, gelöscht.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Wenn die vorhandene Zuordnung für einen Anmeldenamen gelöscht wird, der lokale Server verwendet die standardzuordnung von erstellten **Sp_addlinkedserver** Wenn sie eine Verbindung mit dem Verbindungsserver für diesen Anmeldenamen. Um die standardzuordnung zu ändern, verwenden **Sp_addlinkedsrvlogin**.  
  
 Wenn die standardzuordnung auch gelöscht wird, nur Anmeldungen, die explizit eine anmeldenamenzuordnung auf den Verbindungsserver mit erteilt wurden **Sp_addlinkedsrvlogin**, können Zugriff auf den Verbindungsserver.  
  
 **Sp_droplinkedsrvlogin** kann nicht innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER ANY LOGIN-Berechtigung auf dem Server.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-removing-the-login-mapping-for-an-existing-user"></a>A. Entfernen der Anmeldenamenzuordnung für einen vorhandenen Benutzer  
 Im folgenden Beispiel wird die Zuordnung für den Anmeldenamen `Mary` vom lokalen Server zum Verbindungsserver `Accounts` entfernt. Daher verwendet der Anmeldename `Mary` die standardmäßige Anmeldenamenzuordnung.  
  
```  
EXEC sp_droplinkedsrvlogin 'Accounts', 'Mary';  
```  
  
### <a name="b-removing-the-default-login-mapping"></a>B. Entfernen der Standardanmeldenamenzuordnung  
 Im folgenden Beispiel wird die standardmäßige Anmeldenamenzuordnung entfernt, die durch das Ausführen von `sp_addlinkedserver` auf dem Verbindungsserver `Accounts` erstellt wurde.  
  
```  
EXEC sp_droplinkedsrvlogin 'Accounts', NULL;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
