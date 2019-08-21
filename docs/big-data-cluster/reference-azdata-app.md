---
title: 'azdata app: Referenz'
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata app-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 031d8283f14e06515394bb26aa94049a43b6b79f
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653226"
---
# <a name="azdata-app"></a>azdata app

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel enthält Referenzinformationen zu den **app**-Befehlen im **azdata**-Tool. Weitere Informationen zu anderen **azdata**-Befehlen finden Sie unter [azdata](reference-azdata.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[azdata app template](reference-azdata-app-template.md) | Vorlagen.
[azdata app init](#azdata-app-init) | Starten eines neuen Anwendungsgerüsts.
[azdata app create](#azdata-app-create) | Erstellen einer Anwendung.
[azdata app update](#azdata-app-update) | Ausführen eines Updates einer Anwendung.
[azdata app list](#azdata-app-list) | Auflisten von Anwendungen.
[azdata app delete](#azdata-app-delete) | Löschen einer Anwendung.
[azdata app run](#azdata-app-run) | Ausführen einer Anwendung.
[azdata app describe](#azdata-app-describe) | Beschreiben einer Anwendung.
## <a name="azdata-app-init"></a>azdata app init
Unterstützt Sie beim Starten eines neuen Anwendungsgerüsts und/oder einer neuen Spezifikationsdatei auf Basis von Laufzeitumgebungen.
```bash
azdata app init [--spec -s] 
                [--name -n]  
                [--version -v]  
                [--template -t]  
                [--destination -d]  
                [--url -u]
```
### <a name="examples"></a>Beispiele
Gerüst nur für eine neue Anwendung `spec.yaml`.
```bash
azdata app init --spec
```
Gerüst für eine neue R-Anwendung auf Basis der `r`-Vorlage.
```bash
azdata app init --name reduce --template r
```
Gerüst für eine neue Python-Anwendung auf Basis der `python`-Vorlage.
```bash
azdata app init --name reduce --template python
```
Gerüst für eine neue SSIS-Anwendung auf Basis der `ssis`-Vorlage.
```bash
azdata app init --name reduce --template ssis            
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--spec -s`
Generieren von lediglich einer Anwendung „spec.yaml“.
#### `--name -n`
Anwendungsname
#### `--version -v`
Anwendungsversion
#### `--template -t`
Vorlagenname Eine vollständige Liste der unterstützten Vorlagennamen erhalten Sie durch Ausführen von `azdata app template list`.
#### `--destination -d`
Speicherort des Anwendungsgerüsts. Standard: das aktuelle Arbeitsverzeichnis.
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
## <a name="azdata-app-create"></a>azdata app create
Erstellen einer Anwendung.
```bash
azdata app create --spec -s 
                  
```
### <a name="examples"></a>Beispiele
Erstellen Sie eine neue Anwendung aus einem Verzeichnis, das eine gültige „spec.yaml“-Bereitstellungsspezifikation enthält.
```bash
azdata app create --spec /path/to/dir/with/spec/yaml
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--spec -s`
Der Pfad zu einem Verzeichnis mit einer YAML-Spezifikationsdatei, in der die Anwendung beschrieben ist.
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
## <a name="azdata-app-update"></a>azdata app update
Aktualisieren einer Anwendung.
```bash
azdata app update [--spec -s] 
                  [--yes -y]
```
### <a name="examples"></a>Beispiele
Aktualisieren Sie eine vorhandene Anwendung aus einem Verzeichnis, das eine gültige „spec.yaml“-Bereitstellungsspezifikation enthält.
```bash
azdata app update --spec /path/to/dir/with/spec/yaml    
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--spec -s`
Der Pfad zu einem Verzeichnis mit einer YAML-Spezifikationsdatei, in der die Anwendung beschrieben ist.
#### `--yes -y`
Nicht zu einer Bestätigung auffordern, wenn eine Anwendung aus der „spec.yaml“-Datei aktualisiert wird, die sich im aktuellen Arbeitsverzeichnis befindet.
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
## <a name="azdata-app-list"></a>azdata app list
Auflisten von Anwendungen.
```bash
azdata app list [--name -n] 
                [--version -v]
```
### <a name="examples"></a>Beispiele
Listen Sie eine Anwendung nach Name und Version auf.
```bash
azdata app list --name reduce  --version v1
```
Listen Sie alle Anwendungsversionen nach Namen auf.
```bash
azdata app list --name reduce
```
Listen Sie alle Anwendungsversionen nach Namen auf.
```bash
azdata app list
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--name -n`
Anwendungsname
#### `--version -v`
Anwendungsversion
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
## <a name="azdata-app-delete"></a>azdata app delete
Löschen einer Anwendung.
```bash
azdata app delete --name -n 
                  --version -v
```
### <a name="examples"></a>Beispiele
Löschen Sie eine Anwendung nach Name und Version.
```bash
azdata app delete --name reduce --version v1    
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--name -n`
Anwendungsname
#### `--version -v`
Anwendungsversion
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
## <a name="azdata-app-run"></a>azdata app run
Ausführen einer Anwendung.
```bash
azdata app run --name -n 
               --version -v  
               [--inputs]
```
### <a name="examples"></a>Beispiele
Führen Sie eine Anwendung ohne Eingabeparameter aus.
```bash
azdata app run --name reduce --version v1
```
Führen Sie eine Anwendung mit einem Eingabeparameter aus.
```bash
azdata app run --name reduce --version v1 --inputs x=10
```
Führen Sie eine Anwendung mit mehreren Eingabeparametern aus.
```bash
azdata app run --name reduce --version v1 --inputs x=10,y5.6    
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--name -n`
Anwendungsname
#### `--version -v`
Anwendungsversion
### <a name="optional-parameters"></a>Optionale Parameter
#### `--inputs`
Anwendungseingabeparameter im CSV-Format als `name=value`.
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
## <a name="azdata-app-describe"></a>azdata app describe
Beschreiben einer Anwendung.
```bash
azdata app describe [--spec -s] 
                    [--name -n]  
                    [--version -v]
```
### <a name="examples"></a>Beispiele
Beschreiben Sie die Anwendung.
```bash
azdata app describe --name reduce --version v1    
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--spec -s`
Der Pfad zu einem Verzeichnis mit einer YAML-Spezifikationsdatei, in der die Anwendung beschrieben ist.
#### `--name -n`
Anwendungsname
#### `--version -v`
Anwendungsversion
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
