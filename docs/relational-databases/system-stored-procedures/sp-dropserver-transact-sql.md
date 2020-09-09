---
description: sp_dropserver (Transact-SQL)
title: sp_dropserver (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/07/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropserver_TSQL
- sp_dropserver
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropserver
ms.assetid: 0fc83e35-0caa-49a3-a4b6-a1890d4f46ef
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: c6bb8e372ffa6a9bea01052f4185040dd9942157
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89549811"
---
# <a name="sp_dropserver-transact-sql"></a>sp_dropserver (Transact-SQL)
[!INCLUDE [SQL Server - ASDBMI](../../includes/applies-to-version/sql-asdbmi.md)]

  Entfernt einen Server aus der Liste der bekannten Remote- und Verbindungsserver auf der lokalen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz.  
  
 ![Linksymbol](../../database-engine/configure-windows/media/topic-link.gif "Linksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql  
sp_dropserver [ @server = ] 'server'   
     [ , [ @droplogins = ] { 'droplogins' | NULL} ]  
```  
  
## <a name="arguments"></a>Argumente  
 *server*  
 Der Server, der entfernt werden soll. *server* ist vom Datentyp **sysname**und hat keinen Standardwert. *server* muss vorhanden sein.  
  
 *droplogins*  
 Gibt an, dass die zugehörigen Remote- und Verbindungsserver-Anmeldenamen für *server* ebenfalls entfernt werden müssen, wenn **droplogins** angegeben wird. **`@droplogins`** ist vom Typ **char (10)** und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 Wird **sp_dropserver** auf einem Server ausgeführt, dem Einträge für Remote- und Verbindungsserver-Anmeldenamen zugeordnet sind oder der als Replikationsverleger konfiguriert ist, wird eine Fehlermeldung zurückgegeben. Verwenden Sie das **droplogins** -Argument, um beim Entfernen eines Servers alle Remote- und Verbindungsserver-Anmeldenamen für den Server zu entfernen.  
  
 **sp_dropserver** kann nicht innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert ALTER ANY LINKED SERVER-Berechtigung auf dem Server.  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel werden der Remoteserver `ACCOUNTS` und alle zugehörigen Remoteanmeldenamen von der lokalen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz entfernt.  
  
```  
sp_dropserver 'ACCOUNTS', 'droplogins';  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Security Stored Procedures &#40;Transact-SQL&#41; (Gespeicherte Sicherheitsprozeduren (Transact-SQL))](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_dropremotelogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropremotelogin-transact-sql.md)   
 [sp_helpremotelogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpremotelogin-transact-sql.md)   
 [sp_helpserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
