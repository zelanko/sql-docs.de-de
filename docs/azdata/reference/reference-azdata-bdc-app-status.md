---
title: Referenz zu azdata bdc app status
titleSuffix: SQL Server big data clusters
description: Verwenden Sie diesen Referenzartikel, um ein Verständnis der SQL-Befehle im azdata-Tool zu erwerben, insbesondere des bdc app status-Befehls.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: fd6288649db641bc846b8ebed3b997aa0092d36e
ms.sourcegitcommit: 883435b4c7366f06ac03579752093737b098feab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2020
ms.locfileid: "89733830"
---
# <a name="azdata-bdc-app-status"></a>azdata bdc app status

[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/sqlserver2019.md)]

Der folgende Artikel enthält Referenzinformationen zu den `sql`-Befehlen im `azdata`-Tool. Weitere Informationen zu anderen `azdata`-Befehlen finden Sie in der [Referenz zu azdata](reference-azdata.md).

## <a name="commands"></a>Befehle
| Get-Help | BESCHREIBUNG |
| --- | --- |
[azdata bdc app status show](#azdata-bdc-app-status-show) | Status des App-Diensts
## <a name="azdata-bdc-app-status-show"></a>azdata bdc app status show
Status des App-Diensts
```bash
azdata bdc app status show [--resource -r] 
                           [--all -a]
```
### <a name="examples"></a>Beispiele
Ruft den Status des App-Diensts ab
```bash
azdata bdc app status show
```
Ruft den Status des App-Diensts mit allen Instanzen ab
```bash
azdata bdc app status show --all
```
Ruft den Status der App-Proxyressource im App-Dienst ab
```bash
azdata bdc app status show --resource appproxy
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--resource -r`
Abrufen dieser Ressource in diesem Dienst
#### `--all -a`
Anzeigen aller Instanzen jeder Ressource im Dienst
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
