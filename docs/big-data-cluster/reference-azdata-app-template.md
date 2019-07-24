---
title: Referenz zur azdata-App-Vorlage
titleSuffix: SQL Server big data clusters
description: Referenz Artikel zu Befehlen der azdata-App-Vorlage.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 3b257a2bacc56a7907ab0d25f492ed0ebd605543
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426330"
---
# <a name="azdata-app-template"></a>azdata-App-Vorlage

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel enthält einen Verweis auf die Befehle der **App-Vorlage** im **azdata** -Tool. Weitere Informationen zu anderen **azdata** -Befehlen finden Sie unter [azdata-Referenz](reference-azdata.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[Vorlage der azdata-App-Vorlage](#azdata-app-template-list) | Abrufen unterstützter Vorlagen.
[azdata-App-Vorlagen-Pull](#azdata-app-template-pull) | Unterstützte Vorlagen herunterladen.
## <a name="azdata-app-template-list"></a>Vorlage der azdata-App-Vorlage
Abrufen unterstützter Vorlagen unter dem angegebenen [URL] GitHub-Repository.
```bash
azdata app template list [--url -u] 
                         
```
### <a name="examples"></a>Beispiele
Rufen Sie alle Vorlagen unter dem Standard Speicherort des vorlagenrepository ab.
```bash
azdata app template list
```
Abrufen aller Vorlagen unter einem anderen Repository-Speicherort
```bash
azdata app template list --url https://github.com/diffrent/templates.git
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--url -u`
Geben Sie einen anderen Speicherort für das Repository an. Vorgegebene https://github.com/Microsoft/SQLBDC-AppDeploy.git
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöhen Sie die Protokollierungs Ausführlichkeit, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Diese Hilfe Meldung anzeigen und beenden.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: JSON, jsonc, Table, TSV.  Standardwert: JSON.
#### `--query -q`
Jmespath-Abfrage Zeichenfolge. Weitere [http://jmespath.org/](http://jmespath.org/]) Informationen und Beispiele finden Sie unter.
#### `--verbose`
Erhöhen Sie die Protokollierungs Ausführlichkeit. Verwenden Sie "--Debug" für vollständige Debugprotokolle.
## <a name="azdata-app-template-pull"></a>azdata-App-Vorlagen-Pull
Herunterladen unterstützter Vorlagen unter dem angegebenen [URL] GitHub-Repository.
```bash
azdata app template pull [--name -n] 
                         [--url -u]  
                         [--destination -d]
```
### <a name="examples"></a>Beispiele
Laden Sie alle Vorlagen unter dem Standard Speicherort des vorlagenrepository herunter.
```bash
azdata app template pull
```
Laden Sie alle Vorlagen unter einem anderen Repository-Speicherort herunter.
```bash
azdata app template list --url https://github.com/diffrent/templates.git
```
Einzelne Vorlage nach Namen herunterladen.
```bash
azdata app template pull --name ssis            
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--name -n`
Vorlagen Name. Vollständige Liste der unterstützten Vorlagen namesrun`azdata app template list`
#### `--url -u`
Geben Sie einen anderen Speicherort für das Repository an. Vorgegebene https://github.com/Microsoft/SQLBDC-AppDeploy.git
#### `--destination -d`
Wo die Anwendungs Skelett Vorlage platziert werden soll.
`./templates`
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöhen Sie die Protokollierungs Ausführlichkeit, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Diese Hilfe Meldung anzeigen und beenden.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: JSON, jsonc, Table, TSV.  Standardwert: JSON.
#### `--query -q`
Jmespath-Abfrage Zeichenfolge. Weitere [http://jmespath.org/](http://jmespath.org/]) Informationen und Beispiele finden Sie unter.
#### `--verbose`
Erhöhen Sie die Protokollierungs Ausführlichkeit. Verwenden Sie "--Debug" für vollständige Debugprotokolle.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu anderen **azdata** -Befehlen finden Sie unter [azdata-Referenz](reference-azdata.md). Weitere Informationen zum Installieren des Tools **azdata** finden [Sie unter Install azdata to Manage SQL Server 2019 Big Data Clusters](deploy-install-azdata.md).
