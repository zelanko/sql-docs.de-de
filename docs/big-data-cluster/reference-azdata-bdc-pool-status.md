---
title: Status Referenz für den azdata-BDC-Pool
titleSuffix: SQL Server big data clusters
description: Referenz Artikel für azdata BDC-Pool-Status Befehle.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d0a5925af4f16f2147988b2318880d9acec664c3
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426130"
---
# <a name="azdata-bdc-pool-status"></a>Status des azdata-BDC-Pools

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel enthält einen Verweis auf die Status Befehle des **BDC-Pools** im **azdata** -Tool. Weitere Informationen zu anderen **azdata** -Befehlen finden Sie unter [azdata-Referenz](reference-azdata.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[azdata BDC-Pool Status anzeigen](#azdata-bdc-pool-status-show) | Pool Status
## <a name="azdata-bdc-pool-status-show"></a>azdata BDC-Pool Status anzeigen
Pool Status
```bash
azdata bdc pool status show --kind -k 
                            [--name -n]
```
### <a name="examples"></a>Beispiele
Status des Speicherpools erhalten.
```bash
azdata bdc pool status show --kind storage --name default
```
Der Status des Datenpools wird angezeigt.
```bash
azdata bdc pool status show --kind data --name default
```
Status des computepools erhalten.
```bash
azdata bdc pool status show --kind compute --name default
```
Status des Master Pools erhalten.
```bash
azdata bdc pool status show --kind master --name default
```
Status des Spark-Pools erhalten.
```bash
azdata bdc pool status show --kind spark --name default
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--kind -k`
Big Data-clusterpoolart.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--name -n`
Name des Big Data-Cluster Pools.
`default`
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
