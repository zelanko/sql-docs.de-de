---
title: Berechtigungshierarchie (Datenbank-Engine) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/23/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.server.permissions.f1--May use common.permissions
helpviewer_keywords:
- security [SQL Server], denying access
- hierarchies [SQL Server], permissions
- securables [SQL Server]
- security [SQL Server], permissions
- permissions [SQL Server], hierarchy
- security [SQL Server], granting access
ms.assetid: f6d20a55-ef03-4e14-85f9-009902889866
caps.latest.revision: 37
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d411e1840ef3b763e295cc0a21918c46c4ff9e75
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2018
ms.locfileid: "39109032"
---
# <a name="permissions-hierarchy-database-engine"></a>Berechtigungshierarchie (Datenbank-Engine)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  In [!INCLUDE[ssDE](../../includes/ssde-md.md)] wird eine hierarchische Auflistung der Entitäten verwaltet, die mit Berechtigungen gesichert werden können. Diese Entitäten werden als *sicherungsfähige Elemente*bezeichnet. Die wichtigsten sicherungsfähigen Elemente sind Server und Datenbanken, diskrete Berechtigungen können jedoch auf einer viel differenzierteren Ebene festgelegt werden. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] reguliert die Aktionen von Prinzipalen auf sicherungsfähigen Elementen, indem überprüft wird, ob ihnen entsprechende Berechtigungen gewährt wurden.  
  
 In der folgenden Abbildung werden die Beziehungen zwischen den [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Berechtigungshierarchien dargestellt.  
  
 Das Berechtigungssystem funktioniert in allen Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)], [!INCLUDE[ssDW](../../includes/ssdw-md.md)]und [!INCLUDE[ssAPS](../../includes/ssaps-md.md)]gleich, aber manche Features sind nicht in allen Versionen verfügbar. Beispielsweise kann die Berechtigung auf Serverebene nicht in Azure-Produkten konfiguriert werden.  
  
 ![Diagramm mit Datenbankmodul-Berechtigungshierarchien](../../relational-databases/security/media/wj-security-layers.gif "Diagram of Database Engine permissions hierarchies")  
  
## <a name="chart-of-sql-server-permissions"></a>Diagramm der SQL Server-Berechtigungen  
 Navigieren Sie zu [https://aka.ms/sql-permissions-poster](https://aka.ms/sql-permissions-poster), um ein Diagramm aller [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Berechtigungen im PDF-Format abzurufen.  
  
## <a name="working-with-permissions"></a>Arbeiten mit Berechtigungen  
 Berechtigungen können mit den bekannten [!INCLUDE[tsql](../../includes/tsql-md.md)] -Abfragen GRANT, DENY und REVOKE geändert werden. Informationen über Berechtigungen finden Sie in den Katalogsichten [sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md) und [sys.database_permissions](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md) . Zudem wird die Abfrage von Berechtigungsinformationen mithilfe von integrierten Funktionen unterstützt.  
  
 Informationen zum Entwerfen eines Berechtigungssystems finden Sie unter [Getting Started with Database Engine Permissions](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Sichern von SQL Server](../../relational-databases/security/securing-sql-server.md)   
 
  [Berechtigungen &amp;#40;Datenbank-Engine&amp;#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Securables](../../relational-databases/security/securables.md)   
 
  [Prinzipale &amp;#40;Datenbank-Engine&amp;#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)   
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/has-perms-by-name-transact-sql.md)   
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [sys.server_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)   
 [sys.database_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)  
  
  
