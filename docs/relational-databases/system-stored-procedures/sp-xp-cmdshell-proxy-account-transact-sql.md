---
description: sp_xp_cmdshell_proxy_account (Transact-SQL)
title: sp_xp_cmdshell_proxy_account (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_xp_cmdshell_proxy_account
- sp_xp_cmdshell_proxy_account_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_xp_cmdshell_proxy_account
- xp_cmdshell
ms.assetid: f807c373-7fbc-4108-a2bd-73b48a236003
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: dab49c59b04c09dc550e9fa922ec6f40dbb3fd6d
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97466781"
---
# <a name="sp_xp_cmdshell_proxy_account-transact-sql"></a>sp_xp_cmdshell_proxy_account (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Erstellt Proxyanmeldeinformationen für **xp_cmdshell**.  
  
> [!NOTE]  
>  **xp_cmdshell** ist standardmäßig deaktiviert. Informationen zum Aktivieren von **xp_cmdshell** finden Sie unter [xp_cmdshell Server Konfigurations Option](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_xp_cmdshell_proxy_account [ NULL | { 'account_name' , 'password' } ]  
```  
  
## <a name="arguments"></a>Argumente  
 NULL  
 Gibt an, dass die Proxyanmeldeinformationen gelöscht werden sollen.  
  
 *account_name*  
 Gibt einen Windows-Anmeldenamen an, der als Proxy verwendet wird.  
  
 *password*  
 Gibt das Kennwort des Windows-Kontos an.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 Die Proxyanmeldeinformationen besitzen den Namen **##xp_cmdshell_proxy_account##**.  
  
 Bei Ausführung mit der NULL-Option werden die Proxyanmeldeinformationen von **sp_xp_cmdshell_proxy_account** gelöscht.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die CONTROL SERVER-Berechtigung.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-creating-the-proxy-credential"></a>A. Erstellen der Proxyanmeldeinformationen  
 Im folgenden Beispiel wird das Erstellen von Proxyanmeldeinformationen für das Windows-Konto `ADVWKS\Max04` mit dem Kennwort `ds35efg##65`gezeigt.  
  
```  
EXEC sp_xp_cmdshell_proxy_account 'ADVWKS\Max04', 'ds35efg##65';  
GO  
```  
  
### <a name="b-dropping-the-proxy-credential"></a>B. Löschen der Proxyanmeldeinformationen  
 Im folgenden Beispiel werden die Proxyanmeldeinformationen aus dem Anmeldeinformationenspeicher entfernt.  
  
```  
EXEC sp_xp_cmdshell_proxy_account NULL;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [xp_cmdshell &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/xp-cmdshell-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Gespeicherte Sicherheitsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)  
  
  
