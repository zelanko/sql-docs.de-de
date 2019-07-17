---
title: Sys. security_predicates (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- SYS.SECURITY_PREDICATES
- SECURITY_PREDICATES
- SECURITY_PREDICATES_TSQL
- SYS.SECURITY_PREDICATES_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.security_predicates catalog view
- security_predicates catalog view
ms.assetid: c7a2f28c-98da-463d-8b8a-8e5619e2c6a6
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=azure-sqldw-latest||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6cf464370c5c2ca3f5075205c6783e9332309f12
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68135215"
---
# <a name="syssecuritypredicates-transact-sql"></a>Sys. security_predicates (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Gibt eine Zeile für jedes sicherheitsprädikat in der Datenbank zurück.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|object_id|**int**|Die ID der Sicherheitsrichtlinie, die das Prädikat enthält.|  
|security_predicate_id|**int**|Prädikat-ID innerhalb dieser Richtlinie.|  
|target_object_id|**int**|Die ID des Objekts, an das das Sicherheitsprädikat gebunden ist.|  
|predicate_definition|**nvarchar(max)**|Der vollqualifizierte Name der Funktion, die als Sicherheitsprädikat verwendet wird, einschließlich der Argumente. Beachten Sie, dass der Name der `schema.function` sowie alle anderen Elemente im Text (aus Konsistenzgründen) u. U. normalisiert (d. h. durch Escapezeichen ersetzt) werden. Zum Beispiel:<br /><br /> `[dbo].[fn_securitypredicate]([wing], [startTime], [endTime])`|  
|predicate_type|**int**|Der Typ des Prädikats, die von der Sicherheitsrichtlinie verwendet werden soll:<br /><br /> 0 = FILTERPRÄDIKAT<br /><br /> 1 = BLOCK-PRÄDIKAT|  
|predicate_type_desc|**nvarchar(60)**|Der Typ des Prädikats, die von der Sicherheitsrichtlinie verwendet werden soll:<br /><br /> FILTER<br /><br /> BLOCK|  
|Vorgang|**int**|Der Typ des Vorgangs für das Prädikat angegeben:<br /><br /> NULL = alle anwendbaren Vorgänge<br /><br /> 1 = AFTER INSERT<br /><br /> 2 = NACH UPDATE<br /><br /> 3 = VOR DER AKTUALISIERUNG<br /><br /> 4 = VOR DEM LÖSCHEN|  
|operation_desc|**nvarchar(60)**|Der Typ des Vorgangs für das Prädikat angegeben:<br /><br /> NULL<br /><br /> NACH DEM EINFÜGEN<br /><br /> AFTER UPDATE<br /><br /> VOR DER AKTUALISIERUNG<br /><br /> VOR DEM LÖSCHEN|  
  
## <a name="permissions"></a>Berechtigungen  
 Prinzipale mit den **ALTER ANY SECURITY POLICY** -Berechtigung haben Zugriff auf alle Objekte in dieser Katalogsicht sowie jede Person mit **SICHTDEFINITION** für das Objekt.  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheit auf Zeilenebene](../../relational-databases/security/row-level-security.md)   
 [sys.security_policies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-security-policies-transact-sql.md)   
 [CREATE SECURITY POLICY &#40;Transact-SQL&#41;](../../t-sql/statements/create-security-policy-transact-sql.md)   
 [Sicherheitskatalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Prinzipale &amp;amp;#40;Datenbank-Engine&amp;amp;#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
