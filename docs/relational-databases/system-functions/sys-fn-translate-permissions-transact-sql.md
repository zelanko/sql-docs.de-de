---
title: sys. fn_translate_permissions (Transact-SQL) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68055376"
---
# <a name="sysfn_translate_permissions-transact-sql"></a>sys.fn_translate_permissions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Übersetzt die von der SQL-Ablaufverfolgung zurückgegebene Bitmaske von Berechtigungen in eine Tabelle von Berechtigungsnamen.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.fn_translate_permissions ( level , perms )  
```  
  
## <a name="arguments"></a>Argumente  
 *geringen*  
 Die Art eines sicherungsfähigen Elements, für die die Berechtigung übernommen wird. *Ebene* ist vom Datentyp **nvarchar (60)**.  
  
 *perms*  
 Eine Bitmaske, die in der Berechtigungsspalte zurückgegeben wird. *perms* ist **varbinary (16)**.  
  
## <a name="returns"></a>Rückgabe  
 **glaub**  
  
## <a name="remarks"></a>Bemerkungen  
 Der in der Spalte **Berechtigungen** einer SQL-Ablauf Verfolgung zurückgegebene Wert ist eine ganzzahlige Darstellung einer Bitmaske, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet wird, um effektive Berechtigungen zu berechnen. Jede der 25 Arten sicherungsfähiger Elemente verfügt über einen eigenen Satz Berechtigungen mit entsprechenden numerischen Werten. **sys. fn_translate_permissions** übersetzt diese Bitmaske in eine Tabelle von Berechtigungs Namen.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="example"></a>Beispiel  
 Die folgende-Abfrage `sys.fn_builtin_permissions` verwendet, um die Berechtigungen anzuzeigen, die für Zertifikate gelten, `sys.fn_translate_permissions` und verwendet dann, um die Ergebnisse der Berechtigungs Bitmaske zurückzugeben.  
  
```  
SELECT * FROM sys.fn_builtin_permissions('CERTIFICATE');  
SELECT '0001' AS Input, * FROM sys.fn_translate_permissions('CERTIFICATE', 0001);  
SELECT '0010' AS Input, * FROM sys.fn_translate_permissions('CERTIFICATE', 0010);  
SELECT '0011' AS Input, * FROM sys.fn_translate_permissions('CERTIFICATE', 0011);  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berechtigungen &#40;Datenbank-Engine&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [sys. server_permissions &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)   
 [sys.database_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)  
  
  
