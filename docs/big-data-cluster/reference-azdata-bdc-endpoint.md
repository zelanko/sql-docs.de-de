---
title: 'azdata bdc endpoint: Referenz'
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata bdc endpoint-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 71f52b8312518cf669751d50dcc857c3d892bd98
ms.sourcegitcommit: db1b6153f0bc2d221ba1ce15543ecc83e1045453
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2020
ms.locfileid: "82588076"
---
# <a name="azdata-bdc-endpoint"></a>azdata bdc endpoint

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

Der folgende Artikel enthält Referenzinformationen zum Befehl `bdc endpoint` im Tool `azdata`. Weitere Informationen zu anderen `azdata`-Befehlen finden Sie in der [Referenz zu azdata](reference-azdata.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[azdata bdc endpoint list](#azdata-bdc-endpoint-list) | Listet die Endpunkte für den Big Data-Cluster auf.
## <a name="azdata-bdc-endpoint-list"></a>azdata bdc endpoint list
Listet die Endpunkte für den Big Data-Cluster auf.

```bash
azdata bdc endpoint list [--endpoint-name -e] 
```

### <a name="optional-parameters"></a>Optionale Parameter

#### `--endpoint-name -e`

Name des Endpunkts des Big Data-Clusters.

### <a name="global-arguments"></a>Globale Argumente

#### `--debug`

Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.

#### `--help -h`

Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.

#### `--output -o`

Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.

#### `--query -q`

JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org/).

#### `--verbose`

Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu anderen `azdata`-Befehlen finden Sie in der [Referenz zu azdata](reference-azdata.md). Weitere Informationen zur Installation des `azdata`-Tools finden Sie unter [Installieren von azdata zum Verwalten von Big Data-Clustern für SQL Server 2019](deploy-install-azdata.md).
