---
title: Sys.sql_feature_restrictions (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/07/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sql_sql_feature_restrictions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sql_feature_restrictions catalog view
author: vainolo
ms.author: arib
manager: tomerw
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: b583afef9f52da7801384d4a7a9c76deaf8d4ee4
ms.sourcegitcommit: 96090bb369ca8aba364c2e7f60b37165e5af28fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/10/2019
ms.locfileid: "66822678"
---
# <a name="syssqlfeaturerestrictions-transact-sql"></a>Sys.sql_feature_restrictions (Transact-SQL)

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Gibt eine Zeile für jede Einschränkung in der Datenbank zurück.
  
| Spaltenname | Datentyp | Description |
|-------------|-----------|-------------|
| class       | nvarchar(128) | Klasse des Objekts, für die die Einschränkung gilt. |
| Objekt (object)      | nvarchar(256) | Name des Objekts, für die die Einschränkung gilt. |
| Funktion     | nvarchar(128) | Funktion, die eingeschränkt ist. |
  
## <a name="remarks"></a>Hinweise

Derzeit können die folgenden Funktionen eingeschränkt werden:

| Funktion          | Description |
|------------------|-------------|
| N'ErrorMessages' | Wenn eingeschränkt ist, werden alle Benutzerdaten in der Fehlermeldung maskiert werden. |
| N'Waitfor'       | Wenn eingeschränkt ist, gibt der Befehl sofort ohne Verzögerung zurück. |
  
## <a name="permissions"></a>Berechtigungen

Der Ausführende Prinzipal müssen die `CONTROL` Berechtigung für die Datenbank.
  
## <a name="see-also"></a>Siehe auch

 [Featureeinschränkungen](../../relational-databases/security/feature-restrictions.md)
