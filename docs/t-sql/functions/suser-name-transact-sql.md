---
description: SUSER_NAME (Transact-SQL)
title: SUSER_NAME (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/12/2020
ms.prod: sql
ms.prod_service: sql-data-warehouse, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SUSER_NAME
- SUSER_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- security identification names [SQL Server]
- logins [SQL Server], users
- identification names for logins [SQL Server]
- users [SQL Server], logins
- SUSER_NAME function
- logins [SQL Server], names
- names [SQL Server], logins
ms.assetid: ae598d9f-9baa-49b8-b1c1-042854206de4
author: VanMSFT
ms.author: vanto
monikerRange: =azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 880d2405053d4dad832e0efa7d8c4c5c9d7395f3
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97484102"
---
# <a name="suser_name-transact-sql"></a>SUSER_NAME (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Gibt den Anmeldenamen des Benutzers zurück.  
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
SUSER_NAME ( [ server_user_id ] )   
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
_server\_user\_id_  
Die numerische Anmelde-ID des Benutzers. _server\_user\_id_ (optional) entspricht dem Datentyp **int**. _server\_user\_id_ kann die Anmelde-ID einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldung oder eines [!INCLUDE[msCoName](../../includes/msconame-md.md)]-Windows-Benutzers (oder einer Benutzergruppe) sein, der die Berechtigung zum Herstellen einer Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aufweist. Wird _server\_user\_id_ nicht angegeben, wird der Anmeldename für den aktuellen Benutzer zurückgegeben. Wenn der Parameter das Wort NULL enthalten ist, wird NULL zurückgegeben.  
  
## <a name="return-types"></a>Rückgabetypen  
**nvarchar(128)**  
  
## <a name="remarks"></a>Hinweise  
In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 ersetzt die Sicherheits-ID (SID, Security Identification Number) die ID des Serverbenutzers (SUID, Server User Identification Number).  
  
SUSER_NAME gibt einen Anmeldenamen nur für eine Anmeldung zurück, für die es einen Eintrag in der **syslogins**-Systemtabelle gibt.  
  
SUSER_NAME kann in einer Auswahlliste, in einer WHERE-Klausel und überall dort verwendet werden, wo ein Ausdruck zulässig ist. Verwenden Sie Klammern nach SUSER_NAME, auch wenn kein Parameter angegeben wird.  

> [!NOTE]
> Obwohl die SUSER_NAME-Funktion in Azure SQL-Datenbank unterstützt wird, wird die Verwendung von *Ausführen als* mit SUSER_NAME nicht in Azure SQL-Datenbank unterstützt. 
  
## <a name="examples"></a>Beispiele  
Das folgende Beispiel gibt die Anmelde-ID des Benutzers mit der numerischen Anmelde-ID `1` zurück.  
  
```sql
SELECT SUSER_NAME(1);  
```  
  
## <a name="see-also"></a>Siehe auch  
[SUSER_ID &#40;Transact-SQL&#41;](../../t-sql/functions/suser-id-transact-sql.md)   
[Prinzipale &#40;Datenbank-Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
