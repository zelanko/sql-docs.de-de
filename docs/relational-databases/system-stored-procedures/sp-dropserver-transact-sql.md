---
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
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 2a8868c1654f93b3288509e3a099e5f41eb8208e
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830024"
---
# <a name="sp_dropserver-transact-sql"></a>sp_dropserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Entfernt einen Server aus der Liste der bekannten Remote- und Verbindungsserver auf der lokalen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz.  
  
 ![Linksymbol](../../database-engine/configure-windows/media/topic-link.gif "Linksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql  
sp_dropserver [ @server = ] 'server'   
     [ , [ @droplogins = ] { 'droplogins' | NULL} ]  
```  
  
## <a name="arguments"></a>Argumente  
 *Servers*  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Sicherheits Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_dropremotelogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropremotelogin-transact-sql.md)   
 [sp_helpremotelogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpremotelogin-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
