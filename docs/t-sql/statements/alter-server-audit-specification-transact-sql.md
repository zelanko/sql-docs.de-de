---
description: ALTER SERVER AUDIT SPECIFICATION (Transact-SQL)
title: ALTER SERVER AUDIT SPECIFICATION (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/01/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ALTER SERVER AUDIT SPECIFICATION
- ALTER_SERVER_AUDIT_SPECIFICATION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- server audit [SQL Server]
- audits [SQL Server], specification
- ALTER SERVER AUDIT SPECIFICATION statement
ms.assetid: 9cac288b-940e-4c16-88d6-de06aeed2b47
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ca119bfb4b94aee36270315a29e97613f3d28ce5
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96124215"
---
# <a name="alter-server-audit-specification-transact-sql"></a>ALTER SERVER AUDIT SPECIFICATION (Transact-SQL)
[!INCLUDE [SQL Server - ASDBMI](../../includes/applies-to-version/sql-asdbmi.md)]

  Ändert ein Serverüberwachungsspezifikations-Objekt mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Audit-Features. Weitere Informationen finden Sie unter [SQL Server Audit &#40;Datenbank-Engine&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
ALTER SERVER AUDIT SPECIFICATION audit_specification_name  
{  
    [ FOR SERVER AUDIT audit_name ]  
    [ { { ADD | DROP } ( audit_action_group_name )  
      } [, ...n] ]  
    [ WITH ( STATE = { ON | OFF } ) ]  
}  
[ ; ]  
```  
  

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *audit_specification_name*  
 Der Name der Überwachungsspezifikation.  
  
 *audit_name*  
 Der Name der Überwachung, auf die diese Spezifikation angewendet wird.  
  
 *audit_action_group_name*  
 Name einer Gruppe von überwachbaren Aktionen auf Serverebene. Eine Liste der Überwachungsaktionsgruppen finden Sie unter [SQL Server Audit-Aktionsgruppen und -Aktionen](../../relational-databases/security/auditing/sql-server-audit-action-groups-and-actions.md).  
  
 WITH **(** STATE **=** { ON | OFF } **)**  
 Aktiviert oder deaktiviert das Sammeln von Datensätzen durch die Überwachung für diese Überwachungsspezifikation.  
  
## <a name="remarks"></a>Hinweise  
 Sie müssen den Status einer Überwachungsspezifikation auf die Option OFF festlegen, um Änderungen an der Überwachungsspezifikation vornehmen zu können. Wenn ALTER SERVER AUDIT SPECIFICATION ausgeführt wird, während eine Überwachungsspezifikation mit einer anderen Option als STATE=OFF aktiviert ist, erhalten Sie eine Fehlermeldung.  
  
## <a name="permissions"></a>Berechtigungen  
 Benutzer mit der Berechtigung ALTER ANY SERVER AUDIT können Serverüberwachungsspezifikationen ändern und sie an eine beliebige Überwachung binden.  
  
 Sobald eine Serverüberwachungsspezifikation erstellt wurde, kann sie von Prinzipalen mit den folgenden Berechtigungen eingesehen werden: CONTROL SERVER oder ALTER ANY SERVER AUDIT. Außerdem kann sie von Prinzipalen eingesehen werden, die über das -Konto oder expliziten Zugriff auf die Überwachung verfügen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine Serverüberwachungsspezifikation mit dem Namen `HIPAA_Audit_Specification` erstellt. Mit ihr wird die Überwachungsaktionsgruppe für fehlgeschlagene Anmeldungen gelöscht und eine Überwachungsaktionsgruppe für Datenbankobjektzugriffe für eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Überwachung mit dem Namen `HIPAA_Audit` hinzugefügt.  
  
```sql  
ALTER SERVER AUDIT SPECIFICATION HIPAA_Audit_Specification  
FOR SERVER AUDIT HIPAA_Audit  
    DROP (FAILED_LOGIN_GROUP),  
    ADD (DATABASE_OBJECT_ACCESS_GROUP)  
    WITH (STATE=ON);  
GO  
```  
  
 Ein vollständiges Beispiel für das Erstellen einer Überwachung finden Sie unter [SQL Server Audit &#40;Datenbank-Engine&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  

## <a name="see-also"></a>Siehe auch  
 [CREATE SERVER AUDIT &#40;Transact-SQL&#41;](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT &#40;Transact-SQL&#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [CREATE SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [CREATE DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [DROP DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sys.fn_get_audit_file &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [sys.server_audits &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [sys.server_file_audits &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [sys.server_audit_specifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [sys.server_audit_specification_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [sys.database_audit_specifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys.database_audit_specification_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys.dm_server_audit_status &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys.dm_audit_actions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [Erstellen einer Serverüberwachung und einer Serverüberwachungsspezifikation](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
