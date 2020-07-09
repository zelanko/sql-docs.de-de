---
title: Name der SQL Server-Sortierung (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/21/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- collations [SQL Server], SQL collations
- SQL collations
- names [SQL Server], collations
ms.assetid: 56483d24-add7-483d-9b96-c6fda460ddbc
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 94fa842b9af3fed45e9ad40e04c0029ffc135097
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86009225"
---
# <a name="sql-server-collation-name-transact-sql"></a>SQL Server-Sortierungsname (Transact-SQL)

[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Eine einzelne Zeichenfolge, die den Sortierungsnamen für eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sortierung angibt.

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt Windows-Sortierungen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt darüber hinaus eine begrenzte Anzahl (< 80) von Sortierungen, die als [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sortierungen bezeichnet werden und entwickelt wurden, bevor Windows-Sortierungen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt wurden. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sortierungen werden weiterhin aus Gründen der Abwärtskompatibilität unterstützt, sollten für neue Entwicklungen jedoch nicht verwendet werden. Weitere Informationen zur Windows-Sortierung finden Sie unter [Name der Windows-Sortierung](../../t-sql/statements/windows-collation-name-transact-sql.md).

![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

## <a name="syntax"></a>Syntax

```syntaxsql
<SQL_collation_name> :: =
SQL_SortRules[_Pref]_CPCodepage_<ComparisonStyle>

<ComparisonStyle> ::=
_CaseSensitivity_AccentSensitivity | _BIN
```

## <a name="arguments"></a>Argumente

*SortRules* Eine Zeichenfolge, die das Alphabet oder die Sprache, dessen oder deren Sortierungsregeln beim Angeben der Wörterbuchsortierung angewendet werden, identifiziert. Beispiele sind Latin1_General oder Polish.

**Pref** Gibt an, dass Großschreibung bevorzugt wird. Selbst wenn bei Vergleichen wird die Groß-/Kleinschreibung nicht beachtet wird, stehen Großbuchstaben in der Sortierreihenfolge vor ihren entsprechenden Kleinbuchstaben, wenn es davon abgesehen keine Unterschiede gibt.

*Codepage* Gibt eine ein- bis vierstellige Zahl an, die die von der Sortierung verwendete Codepage identifiziert. **CP1** gibt die Codepage 1252 an – für alle anderen Codepages wird die vollständige Nummer angegeben. **CP1251** gibt beispielsweise die Codepage 1251 an, und **CP850** gibt die Codepage 850 an.

*CaseSensitivity*
**CI** gibt keine Unterscheidung nach Groß-/Kleinschreibung an. Bei **CS** erfolgt eine Unterscheidung.

*AccentSensitivity*
**AI** gibt keine Unterscheidung nach Akzent an. Bei **AS** erfolgt eine Unterscheidung.

**BIN** Gibt die zu verwendende binäre Sortierreihenfolge an.

## <a name="remarks"></a>Bemerkungen

Führen Sie die folgende Abfrage aus, um die vom Server unterstützten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sortierungen aufzulisten.

```sql
SELECT * FROM sys.fn_helpcollations()
WHERE name LIKE 'SQL%';
```

> [!NOTE]
> Verwenden Sie für die Sortierreihenfolgen-ID 80 eine der Windows-Sortierungen mit der Codepage 1250 und der Binärreihenfolge. Beispiel: Albanian_BIN, Croatian_BIN, Czech_BIN, Romanian_BIN, Slovak_BIN, Slovenian_BIN.

## <a name="see-also"></a>Weitere Informationen

- [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md)
- [Konstanten](../../t-sql/data-types/constants-transact-sql.md)
- [CREATE DATABASE](../../t-sql/statements/create-database-transact-sql.md?view=sql-server-2017)
- [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md)
- [DECLARE @local_variable](../../t-sql/language-elements/declare-local-variable-transact-sql.md)
- [Tabelle](../../t-sql/data-types/table-transact-sql.md)
- [sys.fn_helpcollations](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)
