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
monikerRange: =azure-sqldw-latest
ms.openlocfilehash: 4402f8a8b7b0f3bb887557fceb4eba2ab19775ac
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97478451"
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
