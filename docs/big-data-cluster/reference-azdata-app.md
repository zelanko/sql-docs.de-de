---
title: azdata-App-Referenz
titleSuffix: SQL Server big data clusters
description: Referenz Artikel zu azdata-App-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 793edde26ebebf9e55c5751adbedf662142280de
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426280"
---
# <a name="azdata-app"></a>azdata-App

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel enthält einen Verweis auf die **App** -Befehle im **azdata** -Tool. Weitere Informationen zu anderen **azdata** -Befehlen finden Sie unter [azdata-Referenz](reference-azdata.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[azdata-App-Vorlage](reference-azdata-app-template.md) | Betrachtet.
[azdata-App-init](#azdata-app-init) | Starten Sie ein neues Anwendungs Skelett.
[azdata-app erstellen](#azdata-app-create) | Erstellen Sie eine Anwendung.
[Update der azdata-App](#azdata-app-update) | Aktualisieren Sie die Anwendung.
[azdata-App-Liste](#azdata-app-list) | Listet die Anwendung (en) auf.
[azdata-app löschen](#azdata-app-delete) | Löschen Sie die Anwendung.
[Ausführen der azdata-App](#azdata-app-run) | Anwendung ausführen.
[Beschreibung der azdata-App](#azdata-app-describe) | Beschreiben Sie die Anwendung.
## <a name="azdata-app-init"></a>azdata-App-init
Unterstützt Sie beim Starten neuer Anwendungs Skelett-und/oder spec-Dateien basierend auf Laufzeitumgebungen.
```bash
azdata app init [--spec -s] 
                [--name -n]  
                [--version -v]  
                [--template -t]  
                [--destination -d]  
                [--url -u]
```
### <a name="examples"></a>Beispiele
Gerüst für eine neue Anwendung `spec.yaml` .
```bash
azdata app init --spec
```
Gerüstbau eines neuen R-Anwendungs Skeleton basierend `r` auf der Vorlage.
```bash
azdata app init --name reduce --template r
```
Gerüstbau eines neuen python-Anwendungs Skeleton basierend `python` auf der Vorlage.
```bash
azdata app init --name reduce --template python
```
Gerüstbau eines neuen SSIS-Anwendungs Skeleton basierend `ssis` auf der Vorlage.
```bash
azdata app init --name reduce --template ssis            
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--spec -s`
Generieren Sie nur eine Application spec. YAML.
#### `--name -n`
Anwendungsname
#### `--version -v`
Anwendungs Version.
#### `--template -t`
Vorlagen Name. Vollständige Liste der unterstützten Vorlagen Namen ausführen`azdata app template list`
#### `--destination -d`
Speicherort des Anwendungs Skeleton. Standard: Aktuelles Arbeitsverzeichnis.
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
## <a name="azdata-app-create"></a>azdata-app erstellen
Erstellen Sie eine Anwendung.
```bash
azdata app create --spec -s 
                  
```
### <a name="examples"></a>Beispiele
Erstellen Sie eine neue Anwendung aus einem Verzeichnis mit einer gültigen Bereitstellungs Spezifikation für "spec. YAML".
```bash
azdata app create --spec /path/to/dir/with/spec/yaml
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--spec -s`
Pfad zu einem Verzeichnis mit einer YAML-spec-Datei, die die Anwendung beschreibt.
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
## <a name="azdata-app-update"></a>Update der azdata-App
Aktualisieren einer Anwendung.
```bash
azdata app update [--spec -s] 
                  [--yes -y]
```
### <a name="examples"></a>Beispiele
Aktualisieren einer vorhandenen Anwendung aus einem Verzeichnis mit einer gültigen Bereitstellungs Spezifikation für "spec. YAML".
```bash
azdata app update --spec /path/to/dir/with/spec/yaml    
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--spec -s`
Pfad zu einem Verzeichnis mit einer YAML-spec-Datei, die die Anwendung beschreibt.
#### `--yes -y`
Fordern Sie beim Aktualisieren einer Anwendung aus der Datei "spec. YAML" von CWD keine Bestätigung an.
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
## <a name="azdata-app-list"></a>azdata-App-Liste
Listet eine Anwendung (en) auf.
```bash
azdata app list [--name -n] 
                [--version -v]
```
### <a name="examples"></a>Beispiele
Listet die Anwendung nach Name und Version auf.
```bash
azdata app list --name reduce  --version v1
```
Listet alle Anwendungsversionen nach Namen auf.
```bash
azdata app list --name reduce
```
Listet alle Anwendungsversionen nach Namen auf.
```bash
azdata app list
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--name -n`
Anwendungsname
#### `--version -v`
Anwendungs Version.
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
## <a name="azdata-app-delete"></a>azdata-app löschen
Löschen Sie eine Anwendung.
```bash
azdata app delete --name -n 
                  --version -v
```
### <a name="examples"></a>Beispiele
Löschen Sie die Anwendung nach Name und Version.
```bash
azdata app delete --name reduce --version v1    
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--name -n`
Anwendungsname
#### `--version -v`
Anwendungs Version.
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
## <a name="azdata-app-run"></a>Ausführen der azdata-App
Führen Sie eine Anwendung aus.
```bash
azdata app run --name -n 
               --version -v  
               [--inputs]
```
### <a name="examples"></a>Beispiele
Anwendung ohne Eingabeparameter ausführen.
```bash
azdata app run --name reduce --version v1
```
Führen Sie die Anwendung mit einem Eingabeparameter aus.
```bash
azdata app run --name reduce --version v1 --inputs x=10
```
Ausführen einer Anwendung mit mehreren Eingabe Parametern.
```bash
azdata app run --name reduce --version v1 --inputs x=10,y5.6    
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--name -n`
Anwendungsname
#### `--version -v`
Anwendungs Version.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--inputs`
Anwendungs Eingabeparameter im CSV `name=value` -Format.
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
## <a name="azdata-app-describe"></a>Beschreibung der azdata-App
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
Pfad zu einem Verzeichnis mit einer YAML-spec-Datei, die die Anwendung beschreibt.
#### `--name -n`
Anwendungsname
#### `--version -v`
Anwendungs Version.
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
