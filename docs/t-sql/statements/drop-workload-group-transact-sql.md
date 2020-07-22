---
title: DROP WORKLOAD GROUP (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/10/2020
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP_WORKLOAD_GROUP_TSQL
- DROP WORKLOAD GROUP
dev_langs:
- TSQL
helpviewer_keywords:
- DROP WORKLOAD GROUP statement
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azure-sqldw-latest||=azuresqldb-mi-current'
ms.openlocfilehash: 74725f71656141c4e441f80b4ba059012b4b65bb
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86552755"
---
# <a name="drop-workload-group-transact-sql"></a>DROP WORKLOAD GROUP (Transact-SQL)

[!INCLUDE[select-product](../../includes/select-product.md)]

::: moniker range=">=sql-server-2016||>=sql-server-linux-2017||=sqlallproducts-allversions"

||||
|---|---|---|
|**_\* SQL Server \*_** &nbsp;|[SQL-Datenbank<br />verwaltete Instanz](drop-workload-group-transact-sql.md?view=azuresqldb-mi-current)|[Azure Synapse<br />Analytics](drop-workload-group-transact-sql.md?view=azure-sqldw-latest)|
||||

&nbsp;

## <a name="sql-server-and-sql-database-managed-instance"></a>Verwaltete SQL Server- und SQL-Datenbank-Instanz

[!INCLUDE [DROP WORKLOAD GROUP](../../includes/drop-workload-group.md)]
  
::: moniker-end
::: moniker range="=azuresqldb-mi-current||=sqlallproducts-allversions"

||||
|---|---|---|
|[SQL Server](drop-workload-group-transact-sql.md?view=sql-server-2017)|**_\* SQL-Datenbank<br />verwaltete Instanz \*_** &nbsp;|[Azure Synapse<br />Analytics](drop-workload-group-transact-sql.md?view=azure-sqldw-latest)|
||||

&nbsp;

##  <a name="sql-server-and-sql-database-managed-instance"></a>Verwaltete SQL Server- und SQL-Datenbank-Instanz

[!INCLUDE [DROP WORKLOAD GROUP](../../includes/drop-workload-group.md)]

::: moniker-end
::: moniker range="=azure-sqldw-latest||=sqlallproducts-allversions"

||||
|---|---|---|
|[SQL Server](drop-workload-group-transact-sql.md?view=sql-server-2017)|[SQL-Datenbank<br />verwaltete Instanz](drop-workload-group-transact-sql.md?view=azuresqldb-mi-current)| **_\* Azure Synapse<br />Analytics \*_** &nbsp;|
||||

&nbsp;

## <a name="azure-synapse-analytics"></a>Azure Synapse Analytics 

Löscht eine Arbeitsauslastungsgruppe.  Sobald die Anweisung abgeschlossen ist, sind die Einstellungen wirksam.

![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).

## <a name="syntax"></a>Syntax

```syntaxsql
DROP WORKLOAD GROUP group_name  
```

## <a name="arguments"></a>Argumente

*group_name*  
Der Name einer vorhandenen benutzerdefinierten Arbeitsauslastungsgruppe.

## <a name="remarks"></a>Bemerkungen

Eine Arbeitsauslastungsruppe kann nicht gelöscht werden, wenn Klassifizierungen für die Arbeitsauslastungsgruppe existieren.  Löschen Sie die Klassifizierungen, bevor die Arbeitsauslastungsgruppe gelöscht wird.  Wenn es aktive Anforderungen gibt, die Ressourcen aus der zu löschenden Arbeitsauslastungsgruppe verwenden, wird die Anweisung zum Löschen der Arbeitsauslastung dahinter gesperrt.

## <a name="examples"></a>Beispiele

Verwenden Sie das folgende Codebeispiel, um festzustellen, welche Klassifizierungen gelöscht werden müssen, bevor die Arbeitsauslastungsgruppe gelöscht werden kann.

```sql
SELECT c.name as classifier_name
      ,'DROP WORKLOAD CLASSIFIER '+c.name as drop_command
  FROM sys.workload_management_workload_classifiers c
  JOIN sys.workload_management_workload_groups g
    ON c.group_name = g.name
  WHERE g.name = 'wgXYZ' --change the filter to the workload being dropped
```

## <a name="permissions"></a>Berechtigungen

Erfordert die CONTROL DATABASE-Berechtigung

## <a name="see-also"></a>Weitere Informationen

- [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-group-transact-sql.md)
- [ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-workload-group-transact-sql.md)
- [sys.workload_management_workload_groups](../../relational-databases/system-catalog-views/sys-workload-management-workload-groups-transact-sql.md)
- [sys.dm_workload_management_workload_groups_stats](../../relational-databases/system-dynamic-management-views/sys-dm-workload-management-workload-group-stats-transact-sql.md)
- [Schnellstart: Konfigurieren der Arbeitsauslastungsisolation mithilfe von T-SQL](/azure/sql-data-warehouse/quickstart-configure-workload-isolation-tsql)

::: moniker-end
