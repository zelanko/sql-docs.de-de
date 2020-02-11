---
title: sp_enum_login_for_proxy (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_enum_login_for_proxy_TSQL
- sp_enum_login_for_proxy
dev_langs:
- TSQL
helpviewer_keywords:
- sp_enum_login_for_proxy
ms.assetid: 62a75019-248a-44c8-a5cc-c79f55ea3acf
ms.author: vanto
author: VanMSFT
ms.openlocfilehash: ee6b6a701d4ff81863973c4c8e098bd9ed49c967
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68124684"
---
# <a name="sp_enum_login_for_proxy-transact-sql"></a>sp_enum_login_for_proxy (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Listet Zuordnungen zwischen Sicherheitsprinzipalen und Proxys auf.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_enum_login_for_proxy  
    [ @name = ] 'name'  
    [ @proxy_id = ] id,  
    [ @proxy_name = ] 'proxy_name'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @name = ] 'name'`Der Name einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Prinzipal-, Anmelde-, Server Rolle oder **msdb** -Daten Bank Rolle, für die Proxys aufgelistet werden sollen. Der Name ist vom Datentyp **nvarchar (256)** und hat den Standardwert NULL.  
  
`[ @proxy_id = ] id`Die Proxy-ID des Proxys, für den Informationen aufgelistet werden sollen. Der *proxy_id* ist vom Datentyp **int**und hat den Standardwert NULL. Es kann entweder die *ID* oder die *proxy_name* angegeben werden.  
  
`[ @proxy_name = ] 'proxy_name'`Der Name des Proxys, für den Informationen aufgelistet werden sollen. Der *proxy_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Es kann entweder die *ID* oder die *proxy_name* angegeben werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|ID des Proxys.|  
|**proxy_name**|**sysname**|Der Name des Proxys.|  
|**name**|**sysname**|Name des Sicherheitsprinzipals für die Zuordnung|  
|**fahren**|**int**|Typ des Sicherheitsprinzipals.<br /><br /> **** =  0[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmelde Name<br /><br /> **1** = Systemrolle wird korrigiert<br /><br /> **2** = Daten Bank Rolle in **msdb**|  
| &nbsp; | &nbsp; | &nbsp; |
  
## <a name="remarks"></a>Bemerkungen  
 Wenn keine Parameter angegeben werden, werden in **sp_enum_login_for_proxy** Informationen zu allen Anmeldungen in der-Instanz für jeden Proxy aufgelistet.  
  
 Wenn eine Proxy-ID oder ein Proxy Name bereitgestellt wird, werden in **sp_enum_login_for_proxy** Anmeldungen mit Zugriff auf den Proxy aufgeführt. Wenn ein Anmelde Name angegeben wird, werden in **sp_enum_login_for_proxy** die Proxys aufgelistet, auf die der Anmelde Name Zugriff hat.  
  
 Wenn sowohl ein Proxy als auch ein Anmeldename angegeben wird, gibt das Resultset eine Zeile zurück, falls der angegebene Anmeldename auf den angegebenen Proxy zugreifen kann.  
  
 Diese gespeicherte Prozedur befindet sich in **msdb**.  
  
## <a name="permissions"></a>Berechtigungen  
 Ausführungs Berechtigungen für diese Prozedur werden standardmäßig Mitgliedern der festen Server Rolle **sysadmin** zugewiesen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-listing-all-associations"></a>A. Auflisten aller Zuordnungen  
 Mit dem folgenden Beispiel werden alle Berechtigungen aufgelistet, die in der aktuellen Instanz zwischen Anmeldenamen und Proxys eingerichtet wurden.  
  
```sql
USE msdb ;  
GO  
  
EXEC dbo.sp_enum_login_for_proxy ;  
GO  
```  
  
### <a name="b-listing-proxies-for-a-specific-login"></a>B. Auflisten von Proxys für einen bestimmten Anmeldenamen  
 Mit dem folgenden Beispiel werden die Proxys aufgelistet, auf die der Anmeldename `terrid` zugreifen kann.  
  
```sql
USE msdb ;  
GO  
  
EXEC dbo.sp_enum_login_for_proxy  
    @name = 'terrid' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_help_proxy &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-proxy-transact-sql.md)   
 [sp_grant_login_to_proxy &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  
