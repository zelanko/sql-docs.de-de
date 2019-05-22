---
title: Mssqlctl Cluster-Status-Referenz
titleSuffix: SQL Server big data clusters
description: Der Referenzartikel für die Befehle zum Mssqlctl-Cluster.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 05/22/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 76838876dba8fc52ba8a4c92f9e428d61140bc21
ms.sourcegitcommit: be09f0f3708f2e8eb9f6f44e632162709b4daff6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65995058"
---
# <a name="mssqlctl-cluster-status"></a>Clusterstatus mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel bietet Referenz für die **Clusterstatus** Befehle in der **Mssqlctl** Tool. Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[Mssqlctl Cluster Status anzeigen](#mssqlctl-cluster-status-show) | Zeigt den Status des Clusters.
## <a name="mssqlctl-cluster-status-show"></a>Mssqlctl Cluster Status anzeigen
Zeigt den Status des Clusters.
```bash
mssqlctl cluster status show 
```
### <a name="examples"></a>Beispiele
Status des Clusters, in denen der Benutzer angemeldet ist.
```bash
mssqlctl cluster status show
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

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md). Weitere Informationen zum Installieren der **Mssqlctl** finden Sie unter [Mssqlctl zum Verwalten von SQL Server-2019 big Data-Cluster installieren](deploy-install-mssqlctl.md).