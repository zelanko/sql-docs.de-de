---
title: 'azdata sql: Referenz'
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata sql-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: b1e76076763186e2002fb3a7bbc2271b938cbf7e
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70158195"
---
# <a name="azdata-sql"></a>azdata sql

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

Dieser Artikel ist ein Referenz Artikel für **azdata**. 

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[azdata sql shell](#azdata-sql-shell) | Die SQL-Datenbank-CLI ermöglicht es dem Benutzer, über T-SQL mit SQL Server zu interagieren.
[azdata sql query](#azdata-sql-query) | Der query-Befehl ermöglicht das Ausführen einer T-SQL-Abfrage.
## <a name="azdata-sql-shell"></a>azdata sql shell
Die SQL-Datenbank-CLI ermöglicht es dem Benutzer, über T-SQL mit SQL Server zu interagieren.
```bash
azdata sql shell 
```
### <a name="examples"></a>Beispiele
Beispielbefehlszeile, um die interaktive Umgebung zu starten.
```bash
azdata sql shell
```
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. Verwenden Sie „--debug“ für vollständige Debugprotokolle.
## <a name="azdata-sql-query"></a>azdata sql query
Der query-Befehl ermöglicht das Ausführen einer T-SQL-Abfrage.
```bash
azdata sql query --database -d 
                 -q
```
### <a name="examples"></a>Beispiele
Wählen Sie die Liste der Tabellennamen aus.  In der Datenbank wird standardmäßig „master“ verwendet.
```bash
azdata sql query 'SELECT name FROM SYS.TABLES'
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--database -d`
Die Datenbank, in der die Abfrage ausgeführt werden soll.  Der Standard ist „master“.
#### `-q`
Die T-SQL-Abfrage, die ausgeführt werden soll.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.

## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen zu anderen **azdata**-Befehlen finden Sie unter [azdata](reference-azdata.md). 

- Weitere Informationen zum Installieren des Tools **azdata** finden Sie unter [Install azdata to manage SQL Server 2019 big data clusters (Installieren von azdata zum Verwalten von Big-Data-Clustern von SQL Server 2019)](deploy-install-azdata.md).
