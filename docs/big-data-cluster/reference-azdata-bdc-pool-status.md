---
title: 'azdata bdc pool status: Referenz'
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata bdc pool status-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ee49ee09107c98047bd5aea849b9ae486eb6736a
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70153111"
---
# <a name="azdata-bdc-pool-status"></a>azdata bdc pool status

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)] 

Dieser Artikel ist ein Referenz Artikel für **azdata**. 

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[azdata bdc pool status show](#azdata-bdc-pool-status-show) | Poolstatus
## <a name="azdata-bdc-pool-status-show"></a>azdata bdc pool status show
Poolstatus
```bash
azdata bdc pool status show --kind -k 
                            [--name -n]
```
### <a name="examples"></a>Beispiele
Rufen Sie den Status des Speicherpools ab.
```bash
azdata bdc pool status show --kind storage --name default
```
Rufen Sie den Status des Datenpools ab.
```bash
azdata bdc pool status show --kind data --name default
```
Rufen Sie den Status des Computepools ab.
```bash
azdata bdc pool status show --kind compute --name default
```
Rufen Sie den Status des Masterpools ab.
```bash
azdata bdc pool status show --kind master --name default
```
Rufen Sie den Status des Spark-Pools ab.
```bash
azdata bdc pool status show --kind spark --name default
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--kind -k`
Die Art des Big-Data-Clusterpools.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--name -n`
Der Name des Big-Data-Clusterpools.
`default`
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
