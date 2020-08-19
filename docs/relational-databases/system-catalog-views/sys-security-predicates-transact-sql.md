---
description: sys. security_predicates (Transact-SQL)
title: sys. security_predicates (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: c2ba8b6c9c4a2fc2f6b3beb562edfac0728678fe
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88490133"
---
# <a name="syssecurity_predicates-transact-sql"></a>sys. security_predicates (Transact-SQL)
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa.md)]

  Gibt eine Zeile für jedes Sicherheits Prädikat in der Datenbank zurück.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|object_id|**int**|Die ID der Sicherheitsrichtlinie, die das Prädikat enthält.|  
|security_predicate_id|**int**|Prädikat-ID innerhalb dieser Richtlinie.|  
|target_object_id|**int**|Die ID des Objekts, an das das Sicherheitsprädikat gebunden ist.|  
|predicate_definition|**nvarchar(max)**|Der vollqualifizierte Name der Funktion, die als Sicherheitsprädikat verwendet wird, einschließlich der Argumente. Beachten Sie, dass der Name der `schema.function` sowie alle anderen Elemente im Text (aus Konsistenzgründen) u. U. normalisiert (d. h. durch Escapezeichen ersetzt) werden. Beispiel:<br /><br /> `[dbo].[fn_securitypredicate]([wing], [startTime], [endTime])`|  
|predicate_type|**int**|Der Typ des Prädikats, das von der Sicherheitsrichtlinie verwendet wird:<br /><br /> 0 = Filter Prädikat<br /><br /> 1 = Block Prädikat|  
|predicate_type_desc|**nvarchar(60)**|Der Typ des Prädikats, das von der Sicherheitsrichtlinie verwendet wird:<br /><br /> FILTER<br /><br /> BLOCKIEREN|  
|operation|**int**|Der für das Prädikat angegebene Vorgangstyp:<br /><br /> NULL = alle anwendbaren Vorgänge<br /><br /> 1 = nach dem Einfügen<br /><br /> 2 = nach dem Update<br /><br /> 3 = vor Update<br /><br /> 4 = vor dem Löschen|  
|operation_desc|**nvarchar(60)**|Der für das Prädikat angegebene Vorgangstyp:<br /><br /> NULL<br /><br /> nach dem Einfügen<br /><br /> AFTER UPDATE<br /><br /> vor dem Update<br /><br /> vor dem Löschen|  
  
## <a name="permissions"></a>Berechtigungen  
 Prinzipale mit der **ALTER ANY Security Policy** -Berechtigung haben Zugriff auf alle-Objekte in dieser Katalog Sicht sowie alle Benutzer mit **Sicht Definition** für das-Objekt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheit auf Zeilenebene](../../relational-databases/security/row-level-security.md)   
 [sys.security_policies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-security-policies-transact-sql.md)   
 [CREATE SECURITY POLICY &#40;Transact-SQL&#41;](../../t-sql/statements/create-security-policy-transact-sql.md)   
 [Sicherheitskatalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Prinzipale &#40;Datenbank-Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
