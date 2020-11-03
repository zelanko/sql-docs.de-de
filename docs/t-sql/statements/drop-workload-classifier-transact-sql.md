---
description: DROP WORKLOAD Classifier (Transact-SQL)
title: DROP WORKLOAD CLASSIFIER (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2019
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
author: ronortloff
ms.author: rortloff
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: 89fca3ce657b036578eb5f1b90e9b307799f4a95
ms.sourcegitcommit: 894c1a23e922dc29b82c1d2c34c7b0ff28b38654
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93067404"
---
# <a name="drop-workload-classifier-transact-sql"></a>DROP WORKLOAD CLASSIFIER (Transact-SQL)

[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

Löscht eine vorhandene benutzerdefinierte Workloadverwaltungsklassifizierung.  Wenn Anforderungen ausgeführt werden oder sich in der Anforderungswarteschlange im Status „Angehalten“ befinden, behalten sie ihre Klassifizierung und der Klassifizierer kann sofort gelöscht werden. Einen Klassifizierer zu löschen und mit einer Priorität neu zu erstellen hat keine Auswirkungen auf eine bereits klassifizierte Anforderung.
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Syntax  

```syntaxsql
DROP WORKLOAD CLASSIFIER classifier_name;
```
[!INCLUDE[synapse-analytics-od-unsupported-syntax](../../includes/synapse-analytics-od-unsupported-syntax.md)]

[!INCLUDE[synapse-analytics-od-unsupported-syntax](../../includes/synapse-analytics-od-unsupported-syntax.md)]

## <a name="arguments"></a>Argumente

*classifier_name*  
Gibt den Namen an, mit dem der Arbeitsauslastungsklassifizierer identifiziert werden kann.
  
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
[[!INCLUDE[ssSDW](../../includes/sssdwfull-md.md)] Workloadklassifizierung](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification)
