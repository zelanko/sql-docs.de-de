---
title: azdata-SQL-Referenz
titleSuffix: SQL Server big data clusters
description: Referenz Artikel für azdata-SQL-Befehle.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 90512592901fcf83e4697b5eefc80a6df7aeb032
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426020"
---
# <a name="azdata-sql"></a>azdata-SQL

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel enthält eine Referenz für die **SQL** -Befehle im **azdata** -Tool. Weitere Informationen zu anderen **azdata** -Befehlen finden Sie unter [azdata-Referenz](reference-azdata.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[azdata-SQL-Shell](#azdata-sql-shell) | Die SQL-Datenbank-CLI ermöglicht dem Benutzer die Interaktion mit SQL Server über T-SQL.
[azdata-SQL-Abfrage](#azdata-sql-query) | Der Abfragebefehl ermöglicht die Ausführung einer T-SQL-Abfrage.
## <a name="azdata-sql-shell"></a>azdata-SQL-Shell
Die SQL-Datenbank-CLI ermöglicht dem Benutzer die Interaktion mit SQL Server über T-SQL.
```bash
azdata sql shell 
```
### <a name="examples"></a>Beispiele
Beispiel Befehlszeile zum Starten der interaktiven Darstellung.
```bash
azdata sql shell
```
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöhen Sie die Protokollierungs Ausführlichkeit, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Diese Hilfe Meldung anzeigen und beenden.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: JSON, jsonc, Table, TSV.  Standardwert: JSON.
#### `--query -q`
Jmespath-Abfrage Zeichenfolge. Weitere [http://jmespath.org/](http://jmespath.org/]) Informationen und Beispiele finden Sie unter.
#### `--verbose`
Erhöhen Sie die Protokollierungs Ausführlichkeit. Verwenden Sie "--Debug" für vollständige Debugprotokolle.
## <a name="azdata-sql-query"></a>azdata-SQL-Abfrage
Der Abfragebefehl ermöglicht die Ausführung einer T-SQL-Abfrage.
```bash
azdata sql query --database -d 
                 -q
```
### <a name="examples"></a>Beispiele
Wählen Sie die Liste der Tabellennamen aus.  Datenbank ist standardmäßig auf Master eingestellt.
```bash
azdata sql query 'SELECT name FROM SYS.TABLES'
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--database -d`
Datenbank, in der die Abfrage ausgeführt werden soll.  Der Standardwert ist Master.
#### `-q`
Auszuführende T-SQL-Abfrage.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöhen Sie die Protokollierungs Ausführlichkeit, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Diese Hilfe Meldung anzeigen und beenden.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: JSON, jsonc, Table, TSV.  Standardwert: JSON.
#### `--query -q`
Jmespath-Abfrage Zeichenfolge. Weitere [http://jmespath.org/](http://jmespath.org/]) Informationen und Beispiele finden Sie unter.
#### `--verbose`
Erhöhen Sie die Protokollierungs Ausführlichkeit. Verwenden Sie "--Debug" für vollständige Debugprotokolle.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Installieren des Tools **azdata** finden [Sie unter Install azdata to Manage SQL Server 2019 Big Data Clusters](deploy-install-azdata.md).
