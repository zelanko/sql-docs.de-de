---
title: sys. login_token (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- login_token_TSQL
- sys.login_token_TSQL
- sys.login_token
- login_token
dev_langs:
- TSQL
helpviewer_keywords:
- sys.login_token catalog view
- logins [SQL Server], security tokens
- tokens [SQL Server]
ms.assetid: 86e06938-9d0a-44e5-99e2-55c8ef5f2f84
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 892a1ff4570f209b89866e1287cb55691d9b6189
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85635297"
---
# <a name="syslogin_token-transact-sql"></a>sys.login_token (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Gibt eine Zeile für jeden Serverprinzipal zurück, der Teil des Anmeldetoken ist.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**principal_id**|**int**|ID des Prinzipals. Dieser Wert ist innerhalb des Servers eindeutig.|  
|**sid**|**varbinary(85)**|Sicherheits- ID des Prinzipals. Wenn dies ein Windows-Prinzipal ist, **sid** = Windows-SID. Wenn die Anmeldung einem Zertifikat zugeordnet ist, **sid** = GUID aus dem Zertifikat.|  
|**name**|**nvarchar(128)**|Name des Prinzipals. Dieser Wert ist innerhalb des Servers eindeutig.|  
|**type**|**nvarchar(128)**|Beschreibung des Prinzipaltyps. Alle Typen werden **sid**zugeordnet. Der Wert kann in folgenden Formen vorliegen:<br /><br /> SQL LOGIN<br /><br /> WINDOWS LOGIN<br /><br /> WINDOWS GROUP<br /><br /> SERVER ROLE<br /><br /> LOGIN MAPPED TO CERTIFICATE<br /><br /> LOGIN MAPPED TO ASYMMETRIC KEY<br /><br /> CERTIFICATE<br /><br /> ASYMMETRIC KEY|  
|**ungs**|**nvarchar(128)**|Zeigt an, dass der Prinzipal an der Auswertung von GRANT- oder DENY-Berechtigungen teilnimmt oder als Authentifikator dient.<br /><br /> Die folgenden Werte sind möglich:<br /><br /> GRANT OR DENY<br /><br /> DENY ONLY<br /><br /> AUTHENTICATOR|  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys. user_token &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-user-token-transact-sql.md)   
 [sys. server_principals &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sys. database_principals &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [Prinzipale &#40;Datenbank-Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
