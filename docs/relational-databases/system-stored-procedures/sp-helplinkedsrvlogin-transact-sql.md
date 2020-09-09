---
description: sp_helplinkedsrvlogin (Transact-SQL)
title: sp_helplinkedsrvlogin (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helplinkedsrvlogin_TSQL
- sp_helplinkedsrvlogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helplinkedsrvlogin
ms.assetid: a2b1eba0-bf71-47e7-a4c7-9f55feec82a3
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 4468902fc983e94656a7f00c457b51e26a752a82
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89541742"
---
# <a name="sp_helplinkedsrvlogin-transact-sql"></a>sp_helplinkedsrvlogin (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Stellt Informationen zu den für einen bestimmten Verbindungsserver definierten Anmeldenamenzuordnungen bereit, die für verteilte Abfragen und gespeicherte Remoteprozeduren verwendet werden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helplinkedsrvlogin [ [ @rmtsrvname = ] 'rmtsrvname' ]   
     [ , [ @locallogin = ] 'locallogin' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @rmtsrvname = ] 'rmtsrvname'` Der Name des Verbindungs Servers, für den die Anmelde Namen Zuordnung gilt. *rmzrvname* ist vom Datentyp **vom Datentyp sysname**und hat den Standardwert NULL. Mit NULL werden alle Anmeldenamenzuordnungen zurückgegeben, die für alle auf dem lokalen Computer mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] definierten Verbindungsserver definiert werden.  
  
`[ @locallogin = ] 'locallogin'` Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmelde Name auf dem lokalen Server, der eine Zuordnung zum Verbindungs Server *rmzrvname*aufweist. *loczuweisung* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. NULL gibt an, dass alle für *rmtrvname* definierten Anmeldungs Zuordnungen zurückgegeben werden. Wenn der Wert nicht NULL ist, muss bereits eine Zuordnung für *loczuweisung* zu *rmzrvname* vorhanden sein. *loczuweisung* kann ein- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmelde Name oder ein Windows-Benutzer sein. Dem Windows-Benutzer müssen die Zugriffsrechte auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erteilt worden sein. Dies kann entweder direkt oder über seine Mitgliedschaft in einer Windows-Gruppe erfolgen, der die Zugriffsrechte erteilt wurden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**Verbindungs Server**|**sysname**|Name des Verbindungsservers.|  
|**Lokale Anmeldung**|**sysname**|Lokaler Anmeldename, für den die Zuordnung gilt.|  
|**Is Self Mapping**|**smallint**|0 = der **lokale Anmelde Name** wird **entfernte Anmeldung** zugeordnet, wenn eine Verbindung mit dem Verbindungs **Server**hergestellt wird.<br /><br /> 1 = der **lokale Anmelde Name** wird demselben Anmelde Namen und Kennwort zugeordnet, wenn eine Verbindung mit dem Verbindungs **Server**hergestellt wird.|  
|**Remote Login**|**sysname**|Der Anmelde Name auf dem **LinkedServer** , der **loczumapping** zugeordnet ist, wenn **isselfmapping** den Wert 0 hat. Wenn **isselfmapping** den Wert 1 hat, ist **RemoteLogin** NULL.|  
  
## <a name="remarks"></a>Hinweise  
 Bevor Sie Anmelde Namen Zuordnungen löschen, verwenden Sie **sp_helplinkedsrvlogin** , um die beteiligten Verbindungs Server zu ermitteln.  
  
## <a name="permissions"></a>Berechtigungen  
 Es werden keine Berechtigungen geprüft.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-displaying-all-login-mappings-for-all-linked-servers"></a>A. Anzeigen aller Anmeldenamenzuordnungen für alle Verbindungsserver  
 Im folgenden Beispiel werden alle Anmeldenamenzuordnungen für alle Verbindungsserver angezeigt, die auf dem lokalen Computer mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] definiert sind.  
  
```  
EXEC sp_helplinkedsrvlogin;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Linked Server    Local Login   Is Self Mapping Remote Login   
---------------- ------------- --------------- --------------   
Accounts         NULL          1               NULL  
Sales            NULL          1               NULL  
Sales            Mary          0               sa  
Marketing        NULL          1               NULL  
  
(4 row(s) affected)  
```  
  
### <a name="b-displaying-all-login-mappings-for-a-linked-server"></a>B. Anzeigen aller Anmeldenamenzuordnungen für einen Verbindungsserver  
 Im folgenden Beispiel werden alle lokal definierten Anmeldenamenzuordnungen für den `Sales`-Verbindungsserver angezeigt.  
  
```  
EXEC sp_helplinkedsrvlogin 'Sales';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Linked Server    Local Login   Is Self Mapping Remote Login   
---------------- ------------- --------------- --------------   
Sales            NULL          1               NULL  
Sales            Mary          0               sa  
  
(2 row(s) affected)  
```  
  
### <a name="c-displaying-all-login-mappings-for-a-local-login"></a>C. Anzeigen aller Anmeldenamenzuordnungen für eine lokale Anmeldung  
 Im folgenden Beispiel werden alle lokal definierten Anmeldenamenzuordnungen für den Anmeldenamen `Mary` angezeigt.  
  
```  
EXEC sp_helplinkedsrvlogin NULL, 'Mary';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Linked Server    Local Login   Is Self Mapping Remote Login   
---------------- ------------- --------------- --------------   
Sales            NULL          1               NULL  
Sales            Mary          0               sa  
  
(2 row(s) affected)  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Security Stored Procedures &#40;Transact-SQL&#41; (Gespeicherte Sicherheitsprozeduren (Transact-SQL))](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_droplinkedsrvlogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-droplinkedsrvlogin-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
