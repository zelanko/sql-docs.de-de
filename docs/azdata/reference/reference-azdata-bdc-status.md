---
title: 'azdata bdc status: Referenz'
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata bdc status-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: seanw
ms.date: 09/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 536e9b87cd6c6477b235746a792f3585e4f3259d
ms.sourcegitcommit: 29a2be59c56f8a4b630af47760ef38d2bf56a3eb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92358368"
---
# <a name="azdata-bdc-status"></a>azdata bdc status

Gilt für [!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)]e

Der folgende Artikel enthält Referenzinformationen zu den **sql**-Befehlen im **azdata**-Tool. Weitere Informationen zu anderen **azdata**-Befehlen finden Sie unter [azdata](reference-azdata.md).

## <a name="commands"></a>Befehle

|Get-Help|BESCHREIBUNG|
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

Weitere Informationen zu anderen **azdata**-Befehlen finden Sie unter [azdata](reference-azdata.md). 

Weitere Informationen zur Installation des Tools **azdata** finden Sie unter [Installieren von azdata](..\install\deploy-install-azdata.md).

