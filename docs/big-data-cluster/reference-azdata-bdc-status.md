---
title: 'azdata bdc status: Referenz'
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata bdc status-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 15fec084fc6ff5d7b3e62ec0b775047aa9bc59db
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68426050"
---
# <a name="azdata-bdc-status"></a>azdata bdc status

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel enthält Referenzinformationen zu den **bdc status**-Befehlen im **azdata**-Tool. Weitere Informationen zu anderen **azdata**-Befehlen finden Sie unter [azdata](reference-azdata.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[azdata bdc status show](#azdata-bdc-status-show) | Anzeigen des Status des Big Data-Clusters.
## <a name="azdata-bdc-status-show"></a>azdata bdc status show
Anzeigen des Status des Big Data-Clusters.
```bash
azdata bdc status show 
```
### <a name="examples"></a>Beispiele
BDC-Status, in dem der Benutzer angemeldet ist.
```bash
azdata bdc status show
```
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

Weitere Informationen zu anderen **azdata**-Befehlen finden Sie unter [azdata](reference-azdata.md). Weitere Informationen zum Installieren des Tools **azdata** finden Sie unter [Install azdata to manage SQL Server 2019 big data clusters (Installieren von azdata zum Verwalten von Big Data-Clustern von SQL Server 2019)](deploy-install-azdata.md).
