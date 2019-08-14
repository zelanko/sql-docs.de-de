---
title: 'azdata bdc pool status: Referenz'
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata bdc pool status-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d0a5925af4f16f2147988b2318880d9acec664c3
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68426130"
---
# <a name="azdata-bdc-pool-status"></a>azdata bdc pool status

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel enthält Referenzinformationen zu den **bdc pool status**-Befehlen im **azdata**-Tool. Weitere Informationen zu anderen **azdata**-Befehlen finden Sie unter [azdata](reference-azdata.md).

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
Erhöhen Sie die Ausführlichkeit der Protokollierung, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Erhöhen Sie die Ausführlichkeit der Protokollierung. Verwenden Sie „--debug“ für vollständige Debugprotokolle.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Installieren des Tools **azdata** finden Sie unter [Install azdata to manage SQL Server 2019 big data clusters (Installieren von azdata zum Verwalten von Big Data-Clustern von SQL Server 2019)](deploy-install-azdata.md).
