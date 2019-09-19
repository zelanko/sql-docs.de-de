---
title: 'azdata notebook: Referenz'
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata notebook-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 97b8cbae68e16dbdde6e9662b18e37f222a1af80
ms.sourcegitcommit: b016c01c47bc08351d093a59448d895cc170f8c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118154"
---
# <a name="azdata-notebook"></a>azdata notebook

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

Dieser Artikel ist ein Referenz Artikel für **azdata**. 

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[azdata notebook view](#azdata-notebook-view) | Anzeigen eines Notebooks.  Option zum Anhalten beim ersten Zellenausführungsfehler.
[azdata notebook run](#azdata-notebook-run) | Ausführen eines Notebooks.  Die Ausführung wird beim ersten Fehler angehalten.
## <a name="azdata-notebook-view"></a>azdata notebook view
Dieser Befehl kann eine Notebook-Datei einlesen und den Markdown, den Code und die Ausgabe in das Format für ein Farbterminal konvertieren.
```bash
azdata notebook view --path -p 
                     [--continue-on-error -c]
```
### <a name="examples"></a>Beispiele
Zeigen Sie ein Notebook an.  Hiermit werden alle Zellen angezeigt.
```bash
azdata notebook view --path '/home/me/notebooks/demo_notebook.ipynb'
```
Zeigen Sie ein Notebook an.  Hiermit werden alle Zellen angezeigt, es sei denn, es wird eine Zelle festgestellt, in deren Ausgabe ein Fehler vorliegt.  In diesem Fall wird die Ausgabe angehalten.
```bash
azdata notebook view --path '/home/me/notebooks/demo_notebook.ipynb' --stop-on-error
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--path -p`
Der Pfad zu dem Notebook, das angezeigt werden soll.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--continue-on-error -c`
Das Anzeigen weiterer Zellen wird fortgesetzt, und alle Zellenfehler, die in der Notebook-Ausgabe gefunden werden, werden ignoriert.  Das Standardverhalten ist, dass bei einem Fehler angehalten wird.  Durch das Anhalten ist es einfacher, die erste Zelle zu sehen, für ein Fehler aufgetreten ist.
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
## <a name="azdata-notebook-run"></a>azdata notebook run
Dieser Befehl erstellt ein temporäres Verzeichnis und führt das angegebene Notebook in diesem Verzeichnis aus, das als Arbeitsverzeichnis fungiert.

>[!NOTE]
>Überprüft mit azdata v 15.0.1900: der Run-Befehl wird nur für python 3-Notebooks unterstützt.

```bash
azdata notebook run --path -p 
                    [--output-path]  
                    [--output-html]  
                    [--arguments -a]  
                    [--interactive -i]  
                    [--clear -c]
```
### <a name="examples"></a>Beispiele
Führen Sie das Notebook aus.
```bash
azdata notebook run --path '/home/me/notebooks/demo_notebook.ipynb'
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--path -p`
Der Dateipfad zu dem Notebook, das ausgeführt werden soll.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--output-path`
Der Verzeichnispfad, der für die Notebook-Ausgabe verwendet werden soll.  Das Notebook mit Ausgabedaten und alle vom Notebook erstellten Dateien werden relativ zu diesem Verzeichnis generiert.
#### `--output-html`
Optionales Flag, das angibt, ob das Ausgabe Notebook zusätzlich in das HTML-Format konvertiert wird.  Erstellt eine zweite Ausgabedatei.
#### `--arguments -a`
Optionale Liste von Notebook-Argumenten, die in die Notebook-Ausführung eingefügt werden sollen.  Codiert als JSON-Wörterbuch.  Beispiel: "{" Name ":" Value "," name2 ":" Value2 "}"
#### `--interactive -i`
Führen Sie ein Notebook im interaktiven Modus aus.
#### `--clear -c`
Deaktivieren Sie im interaktiven Modus die Konsole, bevor Sie eine Zelle rendern.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.

## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen zu anderen **azdata**-Befehlen finden Sie unter [azdata](reference-azdata.md). 

- Weitere Informationen zum Installieren des Tools **azdata** finden Sie unter [Install azdata to manage SQL Server 2019 big data clusters (Installieren von azdata zum Verwalten von Big-Data-Clustern von SQL Server 2019)](deploy-install-azdata.md).
