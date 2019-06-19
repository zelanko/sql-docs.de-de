---
title: DROP WORKLOAD CLASSIFIER (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/01/2019
ms.prod: sql
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- WORKLOAD CLASSIFIER
- WORKLOAD_CLASSIFIER_TSQL
- DROP_WORKLOAD_CLASSIFIER_TSQL
- DROP WORKLOAD GROUP
dev_langs:
- TSQL
helpviewer_keywords:
- DROP WORKLOAD CLASSIFIER statement
ms.assetid: ''
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: 67909db180af056add12324622cfd6094d8729fe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65105834"
---
# <a name="drop-workload-classifier-transact-sql"></a>DROP WORKLOAD CLASSIFIER (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Löscht einen vorhandenen benutzerdefinierten Arbeitsauslastungsverwaltungsklassifizierer.  
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Syntax  

```
DROP WORKLOAD CLASSIFIER classifier_name;
```

## <a name="arguments"></a>Argumente

*classifier_name*  
Gibt den Namen an, mit dem der Arbeitsauslastungsklassifizierer identifiziert werden kann.  „classifier_name“ ist vom Datentyp „sysname“.  Dieses Argument kann bis zu 128 Zeichen lang sein und muss innerhalb der Instanz einen eindeutigen Namen haben.
  
## <a name="remarks"></a>Remarks

Die Anweisung DROP WORKLOAD CLASSIFIER ist nicht erlaubt auf Systemarbeitsauslastungsklassifizierern.

Wenn Anforderungen ausgeführt werden oder sich in der Anforderungswarteschlange im Status „Angehalten“ befinden, behalten sie ihre Klassifizierung und der Klassifizierer kann sofort gelöscht werden.  Einen Klassifizierer zu löschen und mit einer Priorität neu zu erstellen hat keine Auswirkungen auf eine bereits klassifizierte Anforderung.

## <a name="permissions"></a>Berechtigungen

Erfordert die CONTROL DATABASE-Berechtigung.  
  
## <a name="examples"></a>Beispiele

Das folgende Beispiel löscht den Arbeitsauslastungsklassifizierer mit dem Namen `wgcELTROLE`.  

```sql
DROP WORKLOAD CLASSIFIER wgcELTRole;
```

> [!NOTE]
> Eine Anforderung, die ohne übereinstimmenden Klassifizierer übermittelt wird, fällt in die Kategorie der standardmäßigen Arbeitsauslastungsgruppe.  Die Standardarbeitsauslastungsgruppe ist die Ressourcenklasse „smallrc“.
  
## <a name="see-also"></a>Weitere Informationen

[CREATE WORKLOAD CLASSIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-classifier-transact-sql.md)</br>
[SQL Data Warehouse Workload Classification (SQL Data Warehouse Arbeitsauslastungsklassifikation)](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification)
