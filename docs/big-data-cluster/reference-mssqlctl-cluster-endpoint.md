---
title: Cluster-Endpunktverweis mssqlctl
titleSuffix: SQL Server big data clusters
description: Der Referenzartikel für die Cluster-endpunktbefehle Mssqlctl.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 05/22/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 66928c2201e1fb2b568838a77d115e1549abcfe3
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66779331"
---
# <a name="mssqlctl-cluster-endpoint"></a>mssqlctl-Clusterendpunkt

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel bietet Referenz für die **clusterendpunkt** Befehle in der **Mssqlctl** Tool. Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[Liste der Mssqlctl Cluster-Endpunkt](#mssqlctl-cluster-endpoint-list) | Die Endpunkte für den Cluster aufgeführt.
## <a name="mssqlctl-cluster-endpoint-list"></a>Liste der Mssqlctl Cluster-Endpunkt
Die Endpunkte für den Cluster aufgeführt.
```bash
mssqlctl cluster endpoint list [--endpoint-name -e] 
                               
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--endpoint-name -e`
Cluster-Endpunktname.
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