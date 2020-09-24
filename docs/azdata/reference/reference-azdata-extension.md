---
title: azdata-Erweiterungsreferenz
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata-Erweiterungsbefehlen
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: seanw
ms.date: 09/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 16facb611565f02d1b07ae8a46f53ba2b83b3bfc
ms.sourcegitcommit: d56f1eca807c55cf606a6316f3872585f014fec1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90914402"
---
# <a name="azdata-extension"></a>azdata-Erweiterung

Gilt für `azdata`e

Der folgende Artikel enthält Referenzinformationen zu den **sql**-Befehlen im **azdata**-Tool. Weitere Informationen zu anderen **azdata**-Befehlen finden Sie unter [azdata](reference-azdata.md).

## <a name="commands"></a>Befehle

|Get-Help|BESCHREIBUNG|
| --- | --- |
[azdata extension add](#azdata-extension-add) | Hinzufügen einer Erweiterung
[azdata extension remove](#azdata-extension-remove) | Entfernen einer Erweiterung
[azdata extension list](#azdata-extension-list) | Auflisten aller installierten Erweiterungen
## <a name="azdata-extension-add"></a>azdata extension add
Fügen Sie eine Erweiterung hinzu.
```bash
azdata extension add --source -s 
                     [--index]  
                     
[--pip-proxy]  
                     
[--pip-extra-index-urls]  
                     
[--yes -y]
```
### <a name="examples"></a>Beispiele
Fügen Sie eine Erweiterung aus einer URL hinzu.
```bash
azdata extension add --source https://contoso.com/some_ext-0.0.1-py2.py3-none-any.whl```
Add extension from local disk.
```bash
azdata extension add --source ~/some_ext-0.0.1-py2.py3-none-any.whl```
Add extension from local disk and use pip proxy for dependencies.
```bash
azdata extension add --source ~/some_ext-0.0.1-py2.py3-none-any.whl --pip-proxy https://user:pass@proxy.server:8080
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--source -s`
Pfad zu einem Erweiterungsrad auf einem Datenträger oder einer URL zu einer Erweiterung
### <a name="optional-parameters"></a>Optionale Parameter
#### `--index`
Haupt-URL des Python-Paketindexes (Standard: https://pypi.org/simple). Dies sollte auf ein Repository verweisen, das mit PEP 503 konform ist (die einfache Repository-API), oder auf ein lokales Verzeichnis, das im gleichen Format angeordnet ist.
#### `--pip-proxy`
Der Proxy für PIP, der für Erweiterungsabhängigkeiten in Form von [user:passwd@]proxy.server:port verwendet werden soll.
#### `--pip-extra-index-urls`
Durch Leerzeichen getrennte Liste mit zusätzlichen URLs von von Paketindizes, die verwendet werden sollen. Dies sollte auf ein Repository verweisen, das mit PEP 503 konform ist (die einfache Repository-API), oder auf ein lokales Verzeichnis, das im gleichen Format angeordnet ist.
#### `--yes -y`
Nicht zur Bestätigung auffordern
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
## <a name="azdata-extension-remove"></a>azdata extension remove
Entfernen Sie eine Erweiterung.
```bash
azdata extension remove --name -n 
                        [--yes -y]
```
### <a name="examples"></a>Beispiele
Entfernen Sie eine Erweiterung.
```bash
azdata extension remove --name some-ext
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--name -n`
Der Name der Erweiterung
### <a name="optional-parameters"></a>Optionale Parameter
#### `--yes -y`
Nicht zur Bestätigung auffordern
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
## <a name="azdata-extension-list"></a>azdata extension list
Listen Sie alle installierten Erweiterungen auf.
```bash
azdata extension list 
```
### <a name="examples"></a>Beispiele
Listen Sie die Erweiterungen auf.
```bash
azdata extension list
```
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

