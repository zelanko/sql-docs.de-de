---
title: Referenz zu azdata context
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata context-Befehlen
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: seanw
ms.date: 09/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 1d48ef786389c5ef32b1f3fd49c88b0a9d3aac18
ms.sourcegitcommit: d56f1eca807c55cf606a6316f3872585f014fec1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90914739"
---
# <a name="azdata-context"></a>azdata context

Gilt für `azdata`e

Der folgende Artikel enthält Referenzinformationen zu den **sql**-Befehlen im **azdata**-Tool. Weitere Informationen zu anderen **azdata**-Befehlen finden Sie unter [azdata](reference-azdata.md).

## <a name="commands"></a>Befehle

|Get-Help|BESCHREIBUNG|
| --- | --- |
[azdata context list](#azdata-context-list) | Listet die verfügbaren Kontexte im Benutzerprofil auf
[azdata context delete](#azdata-context-delete) | Löscht den Kontext mit dem angegebenen Namespace aus dem Benutzerprofil
[azdata context set](#azdata-context-set) | Legt den Kontext mit dem angegebenen Namespace als den aktiven Kontext im Benutzerprofil fest
## <a name="azdata-context-list"></a>azdata context list
Sie können beliebige Kontexte mit `azdata context set` oder `azdata context delete` festlegen oder löschen. Verwenden Sie `azdata login`, um sich bei einem neuen Kontext anzumelden.
```bash
azdata context list [--active -a] 
                    
```
### <a name="examples"></a>Beispiele
Listet alle verfügbaren Kontexte im Benutzerprofil auf.
```bash
azdata context list
```
Listet den aktiven Kontext im Benutzerprofil auf.
```bash
azdata context list --active
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--active -a`
Listet nur den derzeit aktiven Kontext auf.
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
## <a name="azdata-context-delete"></a>azdata context delete
Ist der gelöschte Kontext aktiv, muss der Benutzer einen neuen aktiven Kontext festlegen. Mit `azdata context list` können Sie die Kontexte anzeigen, die zum Festlegen oder Löschen verfügbar sind.
```bash
azdata context delete --namespace -ns 
                      
```
### <a name="examples"></a>Beispiele
Hiermit wird „contextNamespace“ aus dem Benutzerprofil gelöscht.
```bash
azdata context delete -n contextNamespace
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--namespace -ns`
Namespace des Kontexts, den Sie löschen möchten.
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
## <a name="azdata-context-set"></a>azdata context set
Mit `azdata context list` können Sie die Kontexte anzeigen, die zum Festlegen verfügbar sind. Werden keine Kontexte angezeigt, müssen Sie sich mit `azdata login` anmelden, um in Ihrem Benutzerprofil einen Kontext zu erstellen. Der Kontext, bei dem Sie sich anmelden, wird zu Ihrem aktiven Kontext. Wenn Sie sich bei mehreren Entitäten anmelden, können Sie mit diesem Befehl zwischen den aktiven Kontexten wechseln. Mit `azdata context list --active` wird der derzeit aktive Kontext angezeigt.
```bash
azdata context set --namespace -ns 
                   
```
### <a name="examples"></a>Beispiele
Legt contextNamespace als den aktiven Kontext im Benutzerprofil fest.
```bash
azdata context set -n contextNamespace
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--namespace -ns`
Namespace des Kontexts, den Sie festlegen möchten.
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

