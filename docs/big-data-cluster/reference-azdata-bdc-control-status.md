---
title: 'azdata bdc control status: Referenz'
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata bdc control status-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 5036e7646a847edfa38998694ace8b35d649dd5e
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86942908"
---
# <a name="azdata-bdc-control-status"></a>azdata bdc control status

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

Der folgende Artikel enthält Referenzinformationen zu den `sql`-Befehlen im `azdata`-Tool. Weitere Informationen zu anderen `azdata`-Befehlen finden Sie in der [Referenz zu azdata](reference-azdata.md).

## <a name="commands"></a>Befehle
| Get-Help | BESCHREIBUNG |
| --- | --- |
[azdata bdc control status show](#azdata-bdc-control-status-show) | Status des Steuerungsdiensts
## <a name="azdata-bdc-control-status-show"></a>azdata bdc control status show
Status des Steuerungsdiensts
```bash
azdata bdc control status show [--resource -r] 
                               [--all -a]
```
### <a name="examples"></a>Beispiele
Abrufen des Status von Diensten
```bash
azdata bdc control status show
```
Abrufen des Status des Steuerungsdiensts mit allen Instanzen
```bash
azdata bdc control status show --all
```
Abrufen des Status der Steuerungsressource innerhalb des Steuerungsdiensts
```bash
azdata bdc control status show --resource control
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

Weitere Informationen zu anderen `azdata`-Befehlen finden Sie in der [Referenz zu azdata](reference-azdata.md). Weitere Informationen zur Installation des `azdata`-Tools finden Sie unter [Installieren von azdata zum Verwalten von Big Data-Clustern für SQL Server 2019](deploy-install-azdata.md).
