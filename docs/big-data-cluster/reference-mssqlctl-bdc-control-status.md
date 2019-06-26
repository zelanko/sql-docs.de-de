---
title: Referenz für die Mssqlctl BDC-ressourcensteuerungs-status
titleSuffix: SQL Server big data clusters
description: Der Referenzartikel für die Befehle zur Mssqlctl BDC-Status.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 714ed2152dfff071193a7c33ed29e5fcb9ec8f17
ms.sourcegitcommit: ce5770d8b91c18ba5ad031e1a96a657bde4cae55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2019
ms.locfileid: "67394392"
---
# <a name="mssqlctl-bdc-control-status"></a>Status der BDC-mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel bietet Referenz für die **Bdc-Quellcodeverwaltungsstatus** Befehle in der **Mssqlctl** Tool. Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[Mssqlctl BDC-Steuerelement Status anzeigen](#mssqlctl-bdc-control-status-show) | Status des Steuerelements.
## <a name="mssqlctl-bdc-control-status-show"></a>Mssqlctl BDC-Steuerelement Status anzeigen
Status des Steuerelements.
```bash
mssqlctl bdc control status show 
```
### <a name="examples"></a>Beispiele
Ruft den Status des Steuerelements.
```bash
mssqlctl bdc control status show
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

Weitere Informationen zum Installieren der **Mssqlctl** finden Sie unter [Mssqlctl zum Verwalten von SQL Server-2019 big Data-Cluster installieren](deploy-install-mssqlctl.md).