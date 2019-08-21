---
title: 'azdata app template: Referenz'
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata app template-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 265f8be659594ee549bf0aa2c5ffcf19263a2294
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653209"
---
# <a name="azdata-app-template"></a>azdata app template

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel enthält Referenzinformationen zu den **app template**-Befehlen im **azdata**-Tool. Weitere Informationen zu anderen **azdata**-Befehlen finden Sie unter [azdata](reference-azdata.md).

## <a name="commands"></a>Befehle
|     |     |
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
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. Verwenden Sie „--debug“ für vollständige Debugprotokolle.
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
Vorlagenname. Eine vollständige Liste der unterstützten Vorlagennamen erhalten Sie durch Ausführen von `azdata app template list`.
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
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu anderen **azdata**-Befehlen finden Sie unter [azdata](reference-azdata.md). Weitere Informationen zum Installieren des Tools **azdata** finden Sie unter Installieren von [azdata [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]zur Verwaltung ](deploy-install-azdata.md)von.
