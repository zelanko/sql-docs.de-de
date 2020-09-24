---
title: 'azdata app template: Referenz'
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata app template-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: seanw
ms.date: 09/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 334d3a6c1c0553342d27319ab4761dfe704844dc
ms.sourcegitcommit: d56f1eca807c55cf606a6316f3872585f014fec1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90914701"
---
# <a name="azdata-app-template"></a>azdata app template

Gilt für `azdata`e

Der folgende Artikel enthält Referenzinformationen zu den **sql**-Befehlen im **azdata**-Tool. Weitere Informationen zu anderen **azdata**-Befehlen finden Sie unter [azdata](reference-azdata.md).

## <a name="commands"></a>Befehle

|Get-Help|BESCHREIBUNG|
| --- | --- |
[azdata app template list](#azdata-app-template-list) | Abrufen von unterstützten Vorlagen.
[azdata app template pull](#azdata-app-template-pull) | Herunterladen von unterstützten Vorlagen.
## <a name="azdata-app-template-list"></a>azdata app template list
Abrufen von unterstützten Vorlagen aus dem GitHub-Repository unter der angegebenen [URL].
```bash
azdata app template list [--url -u] 
                         
```
### <a name="examples"></a>Beispiele
Rufen Sie alle Vorlagen ab, die sich im Standardspeicherort des Vorlagenrepositorys befinden.
```bash
azdata app template list
```
Rufen Sie alle Vorlagen ab, die sich in einem anderen Repositoryspeicherort befinden.
```bash
azdata app template list --url https://github.com/diffrent/templates.git
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--url -u`
Geben Sie einen anderen Speicherort für das Vorlagentepository an. Standard: https://github.com/Microsoft/SQLBDC-AppDeploy.git
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
## <a name="azdata-app-template-pull"></a>azdata app template pull
Herunterladen von unterstützten Vorlagen, die sich im GitHub-Repository unter der angegebenen [URL] befinden.
```bash
azdata app template pull [--name -n] 
                         [--url -u]  
                         
[--destination -d]
```
### <a name="examples"></a>Beispiele
Laden Sie alle Vorlagen herunter, die sich im Standardspeicherort des Vorlagenrepositorys befinden.
```bash
azdata app template pull
```
Laden Sie alle Vorlagen herunter, die sich in einem anderen Repositoryspeicherort befinden.
```bash
azdata app template list --url https://github.com/diffrent/templates.git
```
Laden Sie eine einzelne Vorlage über den Namen herunter.
```bash
azdata app template pull --name ssis            
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--name -n`
Vorlagenname Eine vollständige Liste der unterstützten Vorlagennamen erhalten Sie durch Ausführen von `azdata app template list`.
#### `--url -u`
Geben Sie einen anderen Speicherort für das Vorlagentepository an. Standard: https://github.com/Microsoft/SQLBDC-AppDeploy.git
#### `--destination -d`
Speicherort der Anwendungsgerüstvorlage.
`./templates`
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

