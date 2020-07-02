---
title: sp_helpdbfixedrole (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpdbfixedrole
- sp_helpdbfixedrole_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpdbfixedrole
ms.assetid: ad87e9a0-b901-4e37-9950-aa517d680fc3
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 16a0c7ffa2c12e43404f17eaa36fa787c2ae11cc
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85738513"
---
# <a name="sp_helpdbfixedrole-transact-sql"></a>sp_helpdbfixedrole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Gibt eine Liste der festen Datenbankrollen zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpdbfixedrole [ [ @rolename = ] 'role' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @rolename = ] 'role'`Der Name einer Fixed-Daten Bank Rolle. *role* ist vom Datentyp **sysname**und hat den Standardwert NULL. Wenn *Role* angegeben ist, werden nur Informationen zu dieser Rolle zurückgegeben. Andernfalls wird eine Liste und eine Beschreibung aller fester Daten bankrollen zurückgegeben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**DbFixedRole**|**sysname**|Name der festen Datenbankrolle.|  
|**Beschreibung**|**nvarchar (70)**|Beschreibung von **DbFixedRole.**|  
  
## <a name="remarks"></a>Hinweise  
 Feste Datenbankrollen werden, wie in der folgenden Tabelle dargestellt, auf Datenbankebene definiert und besitzen Berechtigungen, um spezifische Verwaltungsaktivitäten auf Datenbankebene auszuführen. Feste Datenbankrollen können nicht hinzugefügt oder entfernt werden. Die für eine feste Datenbankrolle erteilten Berechtigungen können nicht geändert werden.  
  
|Fixed-Daten Bank Rolle|BESCHREIBUNG|  
|-------------------------|-----------------|  
|**db_owner**|Datenbankbesitzer|  
|**db_accessadmin**|Administratoren für den Datenbankzugriff|  
|**db_securityadmin**|Administratoren für die Datenbanksicherheit|  
|**db_ddladmin**|Datenbank-DDL-Administratoren|  
|**db_backupoperator**|Datenbanksicherungs-Operatoren|  
|**db_datareader**|Datenbank-Datenleser|  
|**db_datawriter**|Datenbank-Datenschreiber|  
|**db_denydatareader**|Datenbank-Verweigerungsdatenleser|  
|**db_denydatawriter**|Datenbank-Verweigerungsdatenschreiber|  
  
 In der folgenden Tabelle werden die gespeicherten Prozeduren gezeigt, mit denen Datenbankrollen geändert werden.  
  
|Gespeicherte Prozedur|Aktion|  
|----------------------|------------|  
|**sp_addrolemember**|Fügt einer festen Datenbankrolle einen Datenbankbenutzer hinzu.|  
|**sp_helprole**|Zeigt eine Liste der Mitglieder einer festen Datenbankrolle an.|  
|**sp_droprolemember**|Entfernt ein Mitglied aus einer festen Datenbankrolle.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
 Die zurückgegebenen Informationen unterliegen den Einschränkungen, die für den Zugriff auf Metadaten gelten. Entitäten, für die der Prinzipal keine Berechtigungen besitzt, werden nicht angezeigt. Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine Liste aller festen Datenbankrollen angezeigt.  
  
```  
EXEC sp_helpdbfixedrole;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Sicherheits Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_dbfixedrolepermission &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dbfixedrolepermission-transact-sql.md)   
 [sp_droprolemember &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [sp_helprole &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helprole-transact-sql.md)   
 [sp_helprolemember &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helprolemember-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
