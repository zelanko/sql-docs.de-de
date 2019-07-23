---
title: mssqlctl-App-Referenz
titleSuffix: SQL Server big data clusters
description: Referenz Artikel zu mssqlctl-App-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d0df3e9ca007fb6546310236f4c23d1775687cc5
ms.sourcegitcommit: d667fa9d6f1c8035f15fdb861882bd514be020d9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68388387"
---
# <a name="mssqlctl-app"></a>mssqlctl-App

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel enthält einen Verweis auf die **App** -Befehle im **mssqlctl** -Tool. Weitere Informationen zu anderen **mssqlctl** -Befehlen finden Sie unter [mssqlctl Reference](reference-mssqlctl.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[mssqlctl-App-Vorlage](reference-mssqlctl-app-template.md) | Betrachtet.
[mssqlctl-App-init](#mssqlctl-app-init) | Starten Sie ein neues Anwendungs Skelett.
[mssqlctl-app erstellen](#mssqlctl-app-create) | Erstellen Sie eine Anwendung.
[mssqlctl-App-Update](#mssqlctl-app-update) | Aktualisieren Sie die Anwendung.
[mssqlctl-App-Liste](#mssqlctl-app-list) | Listet die Anwendung (en) auf.
[mssqlctl-app löschen](#mssqlctl-app-delete) | Löschen Sie die Anwendung.
[mssqlctl-app ausführen](#mssqlctl-app-run) | Anwendung ausführen.
[Beschreibung der mssqlctl-App](#mssqlctl-app-describe) | Beschreiben Sie die Anwendung.
## <a name="mssqlctl-app-init"></a>mssqlctl-App-init
Unterstützt Sie beim Starten neuer Anwendungs Skelett-und/oder spec-Dateien basierend auf Laufzeitumgebungen.
```bash
mssqlctl app init [--spec -s] 
                  [--name -n]  
                  [--version -v]  
                  [--template -t]  
                  [--destination -d]  
                  [--url -u]
```
### <a name="examples"></a>Beispiele
Gerüst für eine neue Anwendung `spec.yaml` .
```bash
mssqlctl app init --spec
```
Gerüstbau eines neuen R-Anwendungs Skeleton basierend `r` auf der Vorlage.
```bash
mssqlctl app init --name reduce --template r
```
Gerüstbau eines neuen python-Anwendungs Skeleton basierend `python` auf der Vorlage.
```bash
mssqlctl app init --name reduce --template python
```
Gerüstbau eines neuen SSIS-Anwendungs Skeleton basierend `ssis` auf der Vorlage.
```bash
mssqlctl app init --name reduce --template ssis            
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--spec -s`
Generieren Sie nur eine Application spec. YAML.
#### `--name -n`
Anwendungsname
#### `--version -v`
Anwendungs Version.
#### `--template -t`
Vorlagen Name. Vollständige Liste der unterstützten Vorlagen Namen ausführen`mssqlctl app template list`
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
## <a name="mssqlctl-app-create"></a>mssqlctl-app erstellen
Erstellen Sie eine Anwendung.
```bash
mssqlctl app create --spec -s 
                    
```
### <a name="examples"></a>Beispiele
Erstellen Sie eine neue Anwendung aus einem Verzeichnis mit einer gültigen Bereitstellungs Spezifikation für "spec. YAML".
```bash
mssqlctl app create --spec /path/to/dir/with/spec/yaml
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
## <a name="mssqlctl-app-update"></a>mssqlctl-App-Update
Aktualisieren einer Anwendung.
```bash
mssqlctl app update [--spec -s] 
                    [--yes -y]
```
### <a name="examples"></a>Beispiele
Aktualisieren einer vorhandenen Anwendung aus einem Verzeichnis mit einer gültigen Bereitstellungs Spezifikation für "spec. YAML".
```bash
mssqlctl app update --spec /path/to/dir/with/spec/yaml    
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
## <a name="mssqlctl-app-list"></a>mssqlctl-App-Liste
Listet eine Anwendung (en) auf.
```bash
mssqlctl app list [--name -n] 
                  [--version -v]
```
### <a name="examples"></a>Beispiele
Listet die Anwendung nach Name und Version auf.
```bash
mssqlctl app list --name reduce  --version v1
```
Listet alle Anwendungsversionen nach Namen auf.
```bash
mssqlctl app list --name reduce
```
Listet alle Anwendungsversionen nach Namen auf.
```bash
mssqlctl app list
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
## <a name="mssqlctl-app-delete"></a>mssqlctl-app löschen
Löschen Sie eine Anwendung.
```bash
mssqlctl app delete --name -n 
                    --version -v
```
### <a name="examples"></a>Beispiele
Löschen Sie die Anwendung nach Name und Version.
```bash
mssqlctl app delete --name reduce --version v1    
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
## <a name="mssqlctl-app-run"></a>mssqlctl-app ausführen
Führen Sie eine Anwendung aus.
```bash
mssqlctl app run --name -n 
                 --version -v  
                 [--inputs]
```
### <a name="examples"></a>Beispiele
Anwendung ohne Eingabeparameter ausführen.
```bash
mssqlctl app run --name reduce --version v1
```
Führen Sie die Anwendung mit einem Eingabeparameter aus.
```bash
mssqlctl app run --name reduce --version v1 --inputs x=10
```
Ausführen einer Anwendung mit mehreren Eingabe Parametern.
```bash
mssqlctl app run --name reduce --version v1 --inputs x=10,y5.6    
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
## <a name="mssqlctl-app-describe"></a>Beschreibung der mssqlctl-App
Beschreiben einer Anwendung.
```bash
mssqlctl app describe [--spec -s] 
                      [--name -n]  
                      [--version -v]
```
### <a name="examples"></a>Beispiele
Beschreiben Sie die Anwendung.
```bash
mssqlctl app describe --name reduce --version v1    
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

Weitere Informationen zu anderen **mssqlctl** -Befehlen finden Sie unter [mssqlctl Reference](reference-mssqlctl.md). Weitere Informationen zum Installieren des Tools **mssqlctl** finden [Sie unter Installieren von mssqlctl zum Verwalten von SQL Server 2019 Big Data Clustern](deploy-install-mssqlctl.md).