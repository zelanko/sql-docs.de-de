---
title: 'azdata bdc status: Referenz'
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata bdc status-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: daf3115a7ccdd73f86dbaa9766049cd5be1e1eb9
ms.sourcegitcommit: 883435b4c7366f06ac03579752093737b098feab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2020
ms.locfileid: "89733691"
---
# <a name="azdata-bdc-status"></a>azdata bdc status

[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/sqlserver2019.md)]

Der folgende Artikel enthält Referenzinformationen zu den `sql`-Befehlen im `azdata`-Tool. Weitere Informationen zu anderen `azdata`-Befehlen finden Sie in der [Referenz zu azdata](reference-azdata.md).

## <a name="commands"></a>Befehle
| Get-Help | BESCHREIBUNG |
| --- | --- |
[azdata bdc status show](#azdata-bdc-status-show) | Zeigt den BDC-Status an.
## <a name="azdata-bdc-status-show"></a>azdata bdc status show
Zeigt den BDC-Status an.
```bash
azdata bdc status show [--resource -r] 
                       [--all -a]
```
### <a name="examples"></a>Beispiele
BDC-Status, in dem der Benutzer angemeldet ist.
```bash
azdata bdc status show
```
BDC-Status mit allen Instanzen der enthaltenen Ressourcen.
```bash
azdata bdc status show --all
```
BDC-Status der Dienste, die die Ressource des Steuerelements enthalten.
```bash
azdata bdc status show --resource control
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--resource -r`
Ruft die Dienste ab, die dieser Ressource zugeordnet sind.
#### `--all -a`
Zeigt alle Instanzen jeder Ressource innerhalb der Dienste an.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu anderen `azdata`-Befehlen finden Sie in der [Referenz zu azdata](reference-azdata.md). Weitere Informationen zur Installation des `azdata`-Tools finden Sie unter [Installieren von azdata zum Verwalten von Big Data-Clustern für SQL Server 2019](../install/deploy-install-azdata.md).
