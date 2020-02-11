---
title: sys. server_permissions (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/20/2019
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.server_permissions_TSQL
- sys.server_permissions
- server_permissions
- server_permissions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_permissions catalog view
ms.assetid: 7d78bf17-6c64-4166-bd0b-9e9e20992136
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cbfa717aa70bb057734a285e2b6d84fdc6f4961a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "71163930"
---
# <a name="sysserver_permissions-transact-sql"></a>sys.server_permissions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Gibt eine Zeile für jede Berechtigung auf Serverebene zurück.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**klassi**|**tinyint**|Identifiziert die Klasse, in der die Berechtigung vorhanden ist.<br /><br /> 100 = Server<br /><br /> 101 = Serverprinzipal<br /><br /> 105 = Endpunkt|  
|**class_desc**|**nvarchar (60)**|Beschreibung der Klasse, in der die Berechtigung vorhanden ist. Einer der folgenden Werte:<br /><br /> **Servers**<br /><br /> **SERVER_PRINCIPAL**<br /><br /> **ENDPOINT**|  
|**major_id**|**int**|ID des sicherbaren Elements, für das die Berechtigung vorhanden ist. Der Wert wird gemäß der Klasse interpretiert. Bei den meisten Elementen ist dies die ID, die die Klasse darstellt. Die Interpretation für Elemente, die nicht dem Standard entsprechen, lautet wie folgt:<br /><br /> 100 = immer 0|  
|**minor_id**|**int**|Sekundäre ID des Elements, für das die Berechtigung vorhanden ist. Der Wert wird gemäß der Klasse interpretiert.|  
|**grantee_principal_id**|**int**|Serverprinzipal-ID, der die Berechtigungen erteilt werden.|  
|**grantor_principal_id**|**int**|Serverprinzipal-ID des Berechtigenden dieser Berechtigungen.|  
|**type**|**char (4)**|Typ der Serverberechtigung. Eine Liste der Berechtigungstypen finden Sie in der folgenden Tabelle.|  
|**permission_name**|**nvarchar(128)**|Berechtigungsname.|  
|**Land**|**char (1)**|Der Berechtigungsstatus:<br /><br /> D = Verweigern<br /><br /> R = Aufheben<br /><br /> G = Erteilen<br /><br /> W = Mit Grant-Option erteilen|  
|**state_desc**|**nvarchar (60)**|Beschreibung des Berechtigungsstatus:<br /><br /> VERWEIGERN<br /><br /> REVOKE<br /><br /> GRANT<br /><br /> GRANT_WITH_GRANT_OPTION|  
  
|Berechtigungstyp|Berechtigungsname|Betroffenes sicherungsfähiges Element|  
|---------------------|---------------------|--------------------------|  
|AAES|ALTER ANY EVENT SESSION|SERVER|
|ADBO|ADMINISTER BULK OPERATIONS|SERVER|  
|AL|ALTER|ENDPOINT, LOGIN|  
|ALAA|ALTER ANY SERVER AUDIT|SERVER|
|ALAG|ALTER ANY AVAILABILITY GROUP|SERVER|
|ALCD|ALTER ANY CREDENTIAL|SERVER|  
|ALCO|ALTER ANY CONNECTION|SERVER|  
|ALDB|ALTER ANY DATABASE|SERVER|  
|ALES|ALTER ANY EVENT NOTIFICATION|SERVER|  
|ALHE|ALTER ANY ENDPOINT|SERVER|  
|ALLG|ALTER ANY LOGIN|SERVER|  
|ALLS|ALTER ANY LINKED SERVER|SERVER|  
|ALRS|ALTER RESOURCES|SERVER|
|ALSR|ALTER ANY SERVER ROLE|SERVER|  
|ALSS|ALTER SERVER STATE|SERVER|  
|ALST|ALTER SETTINGS|SERVER|  
|ALTR|ALTER TRACE|SERVER|  
|AUTH|AUTHENTICATE SERVER|SERVER|
|CADB|CONNECT ANY DATABASE|SERVER|  
|CL|CONTROL|ENDPOINT, LOGIN|  
|CL|CONTROL SERVER|SERVER|  
|CO|CONNECT|ENDPOINT|  
|COSQ|CONNECT SQL|SERVER|
|CRAC|CREATE AVAILABILITY GROUP|SERVER|  
|CRDB|CREATE ANY DATABASE|SERVER|  
|CRDE|CREATE DDL EVENT NOTIFICATION|SERVER|  
|CRHE|CREATE ENDPOINT|SERVER|
|CRSR|CREATE SERVER ROLE|SERVER|  
|CRTE|CREATE TRACE EVENT NOTIFICATION|SERVER|
|IAL|IMPERSONATE ANY LOGIN|SERVER|  
|IM|IMPERSONATE|LOGIN|  
|SHDN|SHUTDOWN|SERVER|
|SUS|SELECT ALL USER SECURABLES|SERVER|
|TO|TAKE OWNERSHIP|ENDPOINT|  
|VW|VIEW DEFINITION|ENDPOINT, LOGIN|  
|VWAD|VIEW ANY DEFINITION|SERVER|  
|VWDB|VIEW ANY DATABASE|SERVER|  
|VWSS|VIEW SERVER STATE|SERVER|  
|XA|EXTERNAL ACCESS|SERVER|
|XU|UNSAFE ASSEMBLY|SERVER|
  
## <a name="permissions"></a>Berechtigungen  
 Jedem Benutzer werden die eigenen Berechtigungen angezeigt. Zum Anzeigen der Berechtigungen für andere Anmeldungen ist die VIEW DEFINITION-Berechtigung, die ALTER ANY LOGIN-Berechtigung oder eine beliebige Berechtigung für die betreffende Anmeldung erforderlich. Zum Anzeigen benutzerdefinierter Serverrollen ist ALTER ANY SERVER ROLE oder die Mitgliedschaft in der Rolle erforderlich.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Beispiele  
 Mit der folgenden Abfrage werden die Berechtigungen aufgelistet, die Serverprinzipalen ausdrücklich gewährt oder verweigert wurden.  
  
> [!IMPORTANT]  
> Die Berechtigungen von festen Serverrollen werden nicht in sys.server_permissions aufgeführt. Daher können Serverprinzipale über zusätzliche Berechtigungen verfügen, die hier nicht aufgeführt werden.  
  
```  
SELECT pr.principal_id, pr.name, pr.type_desc,   
    pe.state_desc, pe.permission_name   
FROM sys.server_principals AS pr   
JOIN sys.server_permissions AS pe   
    ON pe.grantee_principal_id = pr.principal_id;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheitskatalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Sicherungs fähige Elemente](../../relational-databases/security/securables.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Berechtigungen &#40;Datenbank-Engine&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Berechtigungshierarchie &#40;Datenbank-Engine&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)  
