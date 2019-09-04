---
title: DENY (Berechtigungen von Service Broker) (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/09/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- denying permissions [Service Broker]
- routes [Service Broker], permissions
- Service Broker, permissions
- DENY statement, Service Broker
- remote service bindings [Service Broker], permissions
- permissions [Service Broker]
- message types [Service Broker], permissions
- denying permissions [SQL Server], Service Broker
- contracts [Service Broker], permissions
- services [Service Broker], permissions
ms.assetid: 7c6de71b-865c-41db-9413-ad9b3562e579
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 346044530087c40c468abe9d304231ce06220845
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67984431"
---
# <a name="deny-service-broker-permissions-transact-sql"></a>DENY (Berechtigungen von Service Broker) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Verweigert Berechtigungen für einen Vertrag, Nachrichtentyp, eine Remotedienstbindung, Route oder einen Dienst von [!INCLUDE[ssSB](../../includes/sssb-md.md)].  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
DENY permission  [ ,...n ] ON  
    {    
       [ CONTRACT :: contract_name ]   
       | [ MESSAGE TYPE :: message_type_name ]    
       | [ REMOTE SERVICE BINDING :: remote_binding_name ]    
       | [ ROUTE :: route_name ]   
       | [ SERVICE :: service_name ]      
        }  
    TO database_principal [ ,...n ]   
    [ CASCADE ]  
        [ AS denying_principal ]  
```  
  
## <a name="arguments"></a>Argumente  
 *permission*  
 Gibt eine Berechtigung an, die für ein sicherbares Element von [!INCLUDE[ssSB](../../includes/sssb-md.md)] verweigert werden kann. Eine Liste der Berechtigungen finden Sie im Abschnitt zu den Hinweisen weiter unten in diesem Thema.  
  
 CONTRACT **::** _contract_name_  
 Gibt den Vertrag an, für den die Berechtigung verweigert wird. Der Bereichsqualifizierer **::** ist erforderlich.  
  
 MESSAGE TYPE **::** _message_type_name_  
 Gibt den Nachrichtentyp an, für den die Berechtigung verweigert wird. Der Bereichsqualifizierer **::** ist erforderlich.  
  
 REMOTE SERVICE BINDING **::** _remote_binding_name_  
 Gibt die Remotedienstbindung an, für die die Berechtigung verweigert wird. Der Bereichsqualifizierer **::** ist erforderlich.  
  
 ROUTE **::** _route_name_  
 Gibt die Route an, für die die Berechtigung verweigert wird. Der Bereichsqualifizierer **::** ist erforderlich.  
  
 SERVICE **::** _message_type_name_  
 Gibt den Dienst an, für den die Berechtigung verweigert wird. Der Bereichsqualifizierer **::** ist erforderlich.  
  
 *database_principal*  
 Gibt den Prinzipal an, für den die Berechtigung verweigert wird. Einer der folgenden Typen:  
  
-   Datenbankbenutzer  
-   Datenbankrolle  
-   Anwendungsrolle  
-   Einem Windows-Anmeldenamen zugeordneter Datenbankbenutzer  
-   Einer Windows-Gruppe zugeordneter Datenbankbenutzer  
-   Einem Zertifikat zugeordneter Datenbankbenutzer  
-   Einem asymmetrischen Schlüssel zugeordneter Datenbankbenutzer  
-   Keinem Serverprinzipal zugeordneter Datenbankbenutzer.  
  
CASCADE  
 Gibt an, dass die verweigerte Berechtigung auch anderen Prinzipalen verweigert wird, denen diese Berechtigung von diesem Prinzipal erteilt wurde.  
  
*denying_principal*  
 Gibt einen Prinzipal an, von dem der Prinzipal, der diese Abfrage ausführt, das Recht zum Verweigern der Berechtigung ableitet. Einer der folgenden Typen:  
  
-   Datenbankbenutzer  
-   Datenbankrolle  
-   Anwendungsrolle  
-   Einem Windows-Anmeldenamen zugeordneter Datenbankbenutzer  
-   Einer Windows-Gruppe zugeordneter Datenbankbenutzer  
-   Einem Zertifikat zugeordneter Datenbankbenutzer  
-   Einem asymmetrischen Schlüssel zugeordneter Datenbankbenutzer  
-   Keinem Serverprinzipal zugeordneter Datenbankbenutzer.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="service-broker-contracts"></a>Service Broker-Verträge  
 Ein [!INCLUDE[ssSB](../../includes/sssb-md.md)]-Vertrag ist ein sicherbares Element auf Datenbankebene in der Datenbank, die das übergeordnete Element in der Berechtigungshierarchie ist. Die spezifischsten und am meisten beschränkten Berechtigungen, die für einen [!INCLUDE[ssSB](../../includes/sssb-md.md)]-Vertrag verweigert werden können, sind unten aufgeführt. Auch die allgemeineren Berechtigungen sind aufgeführt, die diese implizit enthalten.  
  
|Service Broker-Vertragsberechtigung|Impliziert durch Service Broker-Vertragsberechtigung|Impliziert durch Datenbankberechtigung|  
|----------------------------------------|---------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY CONTRACT|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-message-types"></a>Service Broker-Nachrichtentypen  
 Ein [!INCLUDE[ssSB](../../includes/sssb-md.md)]-Nachrichtentyp ist ein sicherbares Element auf Datenbankebene in der Datenbank, die das übergeordnete Element in der Berechtigungshierarchie ist. Die spezifischsten und am meisten beschränkten Berechtigungen, die für einen [!INCLUDE[ssSB](../../includes/sssb-md.md)]-Nachrichtentyp verweigert werden können, sind unten aufgeführt. Auch die allgemeineren Berechtigungen sind aufgeführt, die diese implizit enthalten.  
  
|Service Broker-Nachrichtentypberechtigung|Impliziert durch Service Broker-Nachrichtentypberechtigung|Impliziert durch Datenbankberechtigung|  
|--------------------------------------------|-------------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY MESSAGE TYPE|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-remote-service-bindings"></a>Service Broker-Remotedienstbindungen  
 Eine [!INCLUDE[ssSB](../../includes/sssb-md.md)]-Remotedienstbindung ist ein sicherbares Element auf Datenbankebene in der Datenbank, die das übergeordnete Element in der Berechtigungshierarchie ist. Die spezifischsten und am meisten beschränkten Berechtigungen, die für eine [!INCLUDE[ssSB](../../includes/sssb-md.md)]-Remotedienstbindung verweigert werden können, sind unten aufgeführt. Auch die allgemeineren Berechtigungen sind aufgeführt, die diese implizit enthalten.  
  
|Berechtigung für Service Broker-Remotedienstbindung|Impliziert durch Berechtigung für Service Broker-Remotedienstbindung|Impliziert durch Datenbankberechtigung|  
|------------------------------------------------------|-----------------------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY REMOTE SERVICE BINDING|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-routes"></a>Service Broker-Routen  
 Eine [!INCLUDE[ssSB](../../includes/sssb-md.md)]-Route ist ein sicherbares Element auf Datenbankebene in der Datenbank, die das übergeordnete Element in der Berechtigungshierarchie ist. Die spezifischsten und am meisten beschränkten Berechtigungen, die für eine [!INCLUDE[ssSB](../../includes/sssb-md.md)]-Route verweigert werden können, sind unten aufgeführt. Auch die allgemeineren Berechtigungen sind aufgeführt, die diese implizit enthalten.  
  
|Service Broker-Routenberechtigung|Impliziert durch Service Broker-Routenberechtigung|Impliziert durch Datenbankberechtigung|  
|-------------------------------------|------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ROUTE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
### <a name="service-broker-services"></a>Service Broker-Dienste  
 Ein [!INCLUDE[ssSB](../../includes/sssb-md.md)]-Dienst ist ein sicherbares Element auf Datenbankebene in der Datenbank, die das übergeordnete Element in der Berechtigungshierarchie ist. Die spezifischsten und am meisten beschränkten Berechtigungen, die für einen [!INCLUDE[ssSB](../../includes/sssb-md.md)]-Dienst verweigert werden können, sind unten aufgeführt. Auch die allgemeineren Berechtigungen sind aufgeführt, die diese implizit enthalten.  
  
|Service Broker-Dienstberechtigung|Impliziert durch Service Broker-Dienstberechtigung|Impliziert durch Datenbankberechtigung|  
|---------------------------------------|--------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|SEND|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY SERVICE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die CONTROL-Berechtigung für den Vertrag, Nachrichtentyp, die Remotedienstbindung, Route oder den Dienst von [!INCLUDE[ssSB](../../includes/sssb-md.md)]. Falls die AS-Klausel verwendet wird, muss der angegebene Prinzipal der Besitzer des sicherbaren Elements sein, für das Berechtigungen verweigert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Prinzipale &#40;Datenbank-Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [REVOKE (Berechtigungen von Service Broker) &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)   
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [Berechtigungen &#40;Datenbank-Engine&#41;](../../relational-databases/security/permissions-database-engine.md)  
  
  
