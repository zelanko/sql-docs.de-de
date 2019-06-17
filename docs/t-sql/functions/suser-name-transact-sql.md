---
title: SUSER_NAME (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
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
manager: craigg
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 507e198a12ad613602ffe77295313851f72ecb60
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65947993"
---
# <a name="susername-transact-sql"></a>SUSER_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

Gibt den Anmeldenamen des Benutzers zurück.  
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SUSER_NAME ( [ server_user_id ] )   
```  
  
## <a name="arguments"></a>Argumente  
_server\_user\_id_  
Die numerische Anmelde-ID des Benutzers. _server\_user\_id_ (optional) entspricht dem Datentyp **int**. _server\_user\_id_ kann die Anmelde-ID einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldung oder eines [!INCLUDE[msCoName](../../includes/msconame-md.md)]-Windows-Benutzers (oder einer Benutzergruppe) sein, der die Berechtigung zum Herstellen einer Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aufweist. Wird _server\_user\_id_ nicht angegeben, wird der Anmeldename für den aktuellen Benutzer zurückgegeben. Wenn der Parameter das Wort NULL enthalten ist, wird NULL zurückgegeben.  
  
## <a name="return-types"></a>Rückgabetypen  
**nvarchar(128)**  
  
## <a name="remarks"></a>Remarks  
In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 ersetzt die Sicherheits-ID (SID, Security Identification Number) die ID des Serverbenutzers (SUID, Server User Identification Number).  
  
SUSER_NAME gibt einen Anmeldenamen nur für eine Anmeldung zurück, für die es einen Eintrag in der **syslogins**-Systemtabelle gibt.  
  
SUSER_NAME kann in einer Auswahlliste, in einer WHERE-Klausel und überall dort verwendet werden, wo ein Ausdruck zulässig ist. Verwenden Sie Klammern nach SUSER_NAME, auch wenn kein Parameter angegeben wird.  
  
## <a name="examples"></a>Beispiele  
Das folgende Beispiel gibt die Anmelde-ID des Benutzers mit der numerischen Anmelde-ID `1` zurück.  
  
```  
SELECT SUSER_NAME(1);  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[SUSER_ID &#40;Transact-SQL&#41;](../../t-sql/functions/suser-id-transact-sql.md)   
[Prinzipale &#40;Datenbank-Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
