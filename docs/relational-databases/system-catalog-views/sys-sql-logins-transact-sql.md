---
description: sys.sql_logins (Transact-SQL)
title: sys. sql_logins (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/20/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sql_logins_TSQL
- sql_logins_TSQL
- sys.sql_logins
- sql_logins
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sql_logins catalog view
ms.assetid: 0d9c5b09-86fe-40ff-baab-00b7c051402f
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bfa2b330d03b7480021487983e9ff1a3a210ad11
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88375506"
---
# <a name="syssql_logins-transact-sql"></a>sys.sql_logins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

  Gibt eine Zeile für jeden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldenamen zurück.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**\<inherited columns>**|--|Erbt von **sys. server_principals**.|  
|**is_policy_checked**|**bit**|Kennwortrichtlinie wird überprüft.|  
|**is_expiration_checked**|**bit**|Ablauf des Kennworts wird überprüft.|  
|**password_hash**|**varbinary (256)**|Hash des SQL-Anmeldekennworts. Ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] werden gespeicherte Kennwortinformationen mithilfe der SHA-512-Komponente des mit Salt verschlüsselten Kennworts berechnet.|  
  
 Eine Liste der Spalten, die diese Sicht erbt, finden Sie unter [sys. server_principals &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md). Die Spalten `owning_principal_id` und werden `is_fixed_role` nicht von sys. server_principals geerbt.
  
## <a name="remarks"></a>Bemerkungen  
 Informationen zum Anzeigen von Authentifizierungs Anmeldungen und Anmelde Namen für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows-Authentifizierung finden Sie unter [sys. server_principals &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md).  
  
 Wenn eigenständige Datenbankbenutzer aktiviert sind, können Verbindungen ohne Anmeldungen hergestellt werden. Informationen zu diesen Konten finden Sie unter  [sys. database_principals &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Jeder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierungsanmeldung werden der eigene Anmeldename und die sa-Anmeldung angezeigt. Zum Anzeigen anderer Anmeldenamen ist ALTER ANY LOGIN oder eine Berechtigung für den Anmeldenamen erforderlich.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Sicherheitskatalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Kenn Wort Richtlinie](../../relational-databases/security/password-policy.md)   
 [Prinzipale &#40;Datenbank-Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
