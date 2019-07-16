---
title: Mssqlctl Sql-Referenz
titleSuffix: SQL Server big data clusters
description: Der Referenzartikel für die Sql-Befehlen Mssqlctl.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ead81f324f6946903c490b254b026bbcd799c20d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67957903"
---
# <a name="mssqlctl-sql"></a>Mssqlctl sql

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel bietet Referenz für die **Sql** Befehle in der **Mssqlctl** Tool. Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[Mssqlctl Sql-shell](#mssqlctl-sql-shell) | Die SQL-DB-CLI ermöglicht den Benutzer für die Interaktion mit SQL Server über T-SQL.
[Mssqlctl Sql-Abfrage](#mssqlctl-sql-query) | Der Abfragebefehl ermöglicht das Ausführen einer T-SQL-Abfrage.
## <a name="mssqlctl-sql-shell"></a>Mssqlctl Sql-shell
Die SQL-DB-CLI ermöglicht den Benutzer für die Interaktion mit SQL Server über T-SQL.
```bash
mssqlctl sql shell 
```
### <a name="examples"></a>Beispiele
Beispielbefehlszeile, um die interaktive Umgebung zu starten.
```bash
mssqlctl sql shell
```
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöht die protokollierungsausführlichkeit, sodass alle Debugprotokolle angezeigt.
#### `--help -h`
Zeigen Sie diese hilfemeldung an und beendet.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: Json, Jsonc, Table, Tsv.  Standardwert: Json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Finden Sie unter [ http://jmespath.org/ ](http://jmespath.org/]) für Weitere Informationen und Beispiele.
#### `--verbose`
Erhöht die protokollierungsausführlichkeit. Verwenden Sie--Debug, wenn Sie vollständige Debugprotokolle wünschen.
## <a name="mssqlctl-sql-query"></a>Mssqlctl Sql-Abfrage
Der Abfragebefehl ermöglicht das Ausführen einer T-SQL-Abfrage.
```bash
mssqlctl sql query --database -d 
                   -q
```
### <a name="examples"></a>Beispiele
Wählen Sie die Liste der Tabellennamen.  Der Standardwert ist Master-Datenbank.
```bash
mssqlctl sql query 'SELECT name FROM SYS.TABLES'
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--database -d`
Die Datenbank zum Ausführen der Abfrage.  Der Standardwert ist master.
#### `-q`
Auszuführende T-SQL-Abfrage.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöht die protokollierungsausführlichkeit, sodass alle Debugprotokolle angezeigt.
#### `--help -h`
Zeigen Sie diese hilfemeldung an und beendet.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: Json, Jsonc, Table, Tsv.  Standardwert: Json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Finden Sie unter [ http://jmespath.org/ ](http://jmespath.org/]) für Weitere Informationen und Beispiele.
#### `--verbose`
Erhöht die protokollierungsausführlichkeit. Verwenden Sie--Debug, wenn Sie vollständige Debugprotokolle wünschen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Installieren der **Mssqlctl** finden Sie unter [Mssqlctl zum Verwalten von SQL Server-2019 big Data-Cluster installieren](deploy-install-mssqlctl.md).