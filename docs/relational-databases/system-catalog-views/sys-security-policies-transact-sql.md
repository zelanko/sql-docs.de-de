---
title: sys. security_policies (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- SYS.SECURITY_POLICIES_TSQL
- SECURITY_POLICIES_TSQL
- SYS.SECURITY_POLICIES
- SECURITY_POLICIES
dev_langs:
- TSQL
helpviewer_keywords:
- sys.security_policies catalog view
- security_policies catalog view
ms.assetid: 35362f5b-e601-4049-9e1d-c5307e823831
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=azure-sqldw-latest||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d6eec5c523e2bdd321af145f19d0b5e7e7cba39b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68135310"
---
# <a name="syssecurity_policies-transact-sql"></a>sys. security_policies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Gibt eine Zeile für jede Sicherheitsrichtlinie in der Datenbank zurück.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|name|**sysname**|Der Name der Sicherheitsrichtlinie, der innerhalb der Datenbank eindeutig ist.|  
|object_id|**int**|Die ID der Sicherheitsrichtlinie.|  
|principal_id|**int**|Die ID des Besitzers der Sicherheitsrichtlinie gemäß der Registrierung in der Datenbank. NULL, wenn der Besitzer über das Schema bestimmt wird.|  
|schema_id|**int**|Die ID des Schemas, in dem sich das Objekt befindet.|  
|parent_object_id|**int**|Die ID des Objekts, zu dem die Richtlinie gehört. Muss den Wert 0 (null) haben.|  
|type|**vachar (2)**|Muss **SP**sein.|  
|type_desc|**nvarchar(60)**|**SECURITY_POLICY**.|  
|create_date|**datetime**|Das UTC-Datum, an dem die Sicherheitsrichtlinie erstellt wurde.|  
|modify_date|**datetime**|Das UTC-Datum, an dem die Sicherheitsrichtlinie zuletzt geändert wurde.|  
|is_ms_shipped|**bit**|Immer false.|  
|is_enabled|**bit**|Spezifikationsstatus der Sicherheitsrichtlinie:<br /><br /> 0 = deaktiviert<br /><br /> 1 = aktiviert|  
|is_not_for_replication|**bit**|Die Richtlinie wurde mit der Option NOT FOR REPLICATION erstellt.|  
|uses_database_collation|**bit**|Verwendet dieselbe Sortierung wie die Datenbank.|  
|is_schemabinding_enabled|**bit**|SCHEMABINDING-Status für die Sicherheitsrichtlinie:<br /><br /> 0 oder NULL = aktiviert<br /><br /> 1 = deaktiviert|  
  
## <a name="permissions"></a>Berechtigungen  
 Prinzipale mit der **ALTER ANY Security Policy** -Berechtigung haben Zugriff auf alle-Objekte in dieser Katalog Sicht sowie alle Benutzer mit **Sicht Definition** für das-Objekt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheit auf Zeilenebene](../../relational-databases/security/row-level-security.md)   
 [sys. security_predicates &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-security-predicates-transact-sql.md)   
 [Erstellen einer Sicherheitsrichtlinie &#40;Transact-SQL-&#41;](../../t-sql/statements/create-security-policy-transact-sql.md)   
 [Sicherheits Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Prinzipale &#40;Datenbank-Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
