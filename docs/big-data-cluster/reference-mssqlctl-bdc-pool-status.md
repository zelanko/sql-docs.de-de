---
title: Referenz für Mssqlctl BDC-datenbankpools-status
titleSuffix: SQL Server big data clusters
description: Der Referenzartikel für die Mssqlctl Bdc-Befehle für Ressourcenpools-Status.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: b6eba925adeb7f18adff133ba8110c6766bfed79
ms.sourcegitcommit: ce5770d8b91c18ba5ad031e1a96a657bde4cae55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2019
ms.locfileid: "67394312"
---
# <a name="mssqlctl-bdc-pool-status"></a>Status des Speicherpools von Mssqlctl bdc

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel bietet Referenz für die **Status des Speicherpools von BDC-** Befehle in der **Mssqlctl** Tool. Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[Mssqlctl BDC-Pool-Status anzeigen](#mssqlctl-bdc-pool-status-show) | Status des Speicherpools.
## <a name="mssqlctl-bdc-pool-status-show"></a>Mssqlctl BDC-Pool-Status anzeigen
Status des Speicherpools.
```bash
mssqlctl bdc pool status show --kind -k 
                              [--name -n]
```
### <a name="examples"></a>Beispiele
Ruft den Status des Speicherpools an.
```bash
mssqlctl bdc pool status show --kind storage --name default
```
Ruft den Status des Pools Daten.
```bash
mssqlctl bdc pool status show --kind data --name default
```
Ruft den Status des Compute-Pools.
```bash
mssqlctl bdc pool status show --kind compute --name default
```
Ruft den Status des master-Pools.
```bash
mssqlctl bdc pool status show --kind master --name default
```
Ruft den Status des Spark-Pools.
```bash
mssqlctl bdc pool status show --kind spark --name default
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--kind -k`
Art der BDC-Pool.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--name -n`
Name des BDC-Anwendungspools.
`default`
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