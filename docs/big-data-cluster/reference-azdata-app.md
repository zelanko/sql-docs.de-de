---
title: 'azdata app: Referenz'
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata app-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ec7e461705138905713b803e2f0f96934044d971
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70155297"
---
# <a name="azdata-app"></a>azdata app

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)] 

Dieser Artikel ist ein Referenz Artikel für **azdata**. 

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
azdata app init 
```
### <a name="examples"></a>Beispiele
Gerüst nur für eine neue Anwendung `spec.yaml`.
```bash
azdata app init --spec
```
Gerüstbau eines neuen Anwendungs Skeleton für R-Anwendungen `r` auf Grundlage der Vorlage.
```bash
azdata app init --name reduce --template r
```
Gerüstbau eines neuen python-Anwendungs Skeleton-Anwendungs `python` Skeleton basierend auf der Vorlage.
```bash
azdata app init --name reduce --template python
```
Gerüstbau eines neuen SSIS-Anwendungs Skeleton-Anwendungs `ssis` Skeleton basierend auf der Vorlage.
```bash
azdata app init --name reduce --template ssis            
```
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
azdata app create 
```
### <a name="examples"></a>Beispiele
Erstellen Sie eine neue Anwendung aus einem Verzeichnis, das eine gültige „spec.yaml“-Bereitstellungsspezifikation enthält.
```bash
azdata app create --spec /path/to/dir/with/spec/yaml
```
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
azdata app update 
```
### <a name="examples"></a>Beispiele
Aktualisieren Sie eine vorhandene Anwendung aus einem Verzeichnis, das eine gültige „spec.yaml“-Bereitstellungsspezifikation enthält.
```bash
azdata app update --spec /path/to/dir/with/spec/yaml    
```
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
azdata app list 
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
azdata app delete 
```
### <a name="examples"></a>Beispiele
Löschen Sie eine Anwendung nach Name und Version.
```bash
azdata app delete --name reduce --version v1    
```
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
azdata app run 
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
azdata app describe 
```
### <a name="examples"></a>Beispiele
Beschreiben Sie die Anwendung.
```bash
azdata app describe --name reduce --version v1    
```
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

- Weitere Informationen zu anderen **azdata**-Befehlen finden Sie unter [azdata](reference-azdata.md). 

- Weitere Informationen zum Installieren des Tools **azdata** finden Sie unter [Install azdata to manage SQL Server 2019 big data clusters (Installieren von azdata zum Verwalten von Big-Data-Clustern von SQL Server 2019)](deploy-install-azdata.md).
