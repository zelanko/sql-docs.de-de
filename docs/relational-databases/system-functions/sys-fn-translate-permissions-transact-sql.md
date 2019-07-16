---
title: Sys. fn_translate_permissions (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_translate_permissions
- sys.fn_translate_permissions_TSQL
- fn_translate_permissions
- fn_translate_permissions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- permissions bitmask [SQL Server]
- sys.fn_translate_permissions function
- fn_translate_permissions function
ms.assetid: ac97121f-2bd0-4f71-8e45-42c8584edbc5
author: rothja
ms.author: jroth
ms.openlocfilehash: c08fd2235750a8a7be99b5290813331141ddf0de
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68055376"
---
# <a name="sysfntranslatepermissions-transact-sql"></a>sys.fn_translate_permissions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Übersetzt die von der SQL-Ablaufverfolgung zurückgegebene Bitmaske von Berechtigungen in eine Tabelle von Berechtigungsnamen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.fn_translate_permissions ( level , perms )  
```  
  
## <a name="arguments"></a>Argumente  
 *level*  
 Die Art eines sicherungsfähigen Elements, für die die Berechtigung übernommen wird. *Ebene* ist **nvarchar(60)** .  
  
 *perms*  
 Eine Bitmaske, die in der Berechtigungsspalte zurückgegeben wird. *Perms* ist **varbinary(16)** .  
  
## <a name="returns"></a>Rückgabewert  
 **table**  
  
## <a name="remarks"></a>Hinweise  
 Der zurückgegebene Wert in der **Berechtigungen** Spalte mit einer SQL-Ablaufverfolgung ist eine ganzzahlige Darstellung einer Bitmaske, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] effektive Berechtigungen berechnet. Jede der 25 Arten sicherungsfähiger Elemente verfügt über einen eigenen Satz Berechtigungen mit entsprechenden numerischen Werten. **Sys. fn_translate_permissions** übersetzt diese Bitmaske in eine Tabelle von Berechtigungsnamen.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="example"></a>Beispiel  
 Die folgende Abfrage verwendet `sys.fn_builtin_permissions` gelten für Zertifikate, und verwendet dann die Berechtigungen angezeigt `sys.fn_translate_permissions` zum Zurückgeben der Bitmaske von Berechtigungen.  
  
```  
SELECT * FROM sys.fn_builtin_permissions('CERTIFICATE');  
SELECT '0001' AS Input, * FROM sys.fn_translate_permissions('CERTIFICATE', 0001);  
SELECT '0010' AS Input, * FROM sys.fn_translate_permissions('CERTIFICATE', 0010);  
SELECT '0011' AS Input, * FROM sys.fn_translate_permissions('CERTIFICATE', 0011);  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Berechtigungen &#40;Datenbank-Engine&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [sys.server_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)   
 [sys.database_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)  
  
  
