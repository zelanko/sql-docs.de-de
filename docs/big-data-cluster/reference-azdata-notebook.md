---
title: azdata Notebook-Referenz
titleSuffix: SQL Server big data clusters
description: Referenz Artikel zu azdata Notebook-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: b96c5e06ec51f53964a28cac86f385d6b42c1dc4
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426010"
---
# <a name="azdata-notebook"></a>azdata-Notebook

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel enthält einen Verweis auf die **Notebook** -Befehle im **azdata** -Tool. Weitere Informationen zu anderen **azdata** -Befehlen finden Sie unter [azdata-Referenz](reference-azdata.md) .

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[azdata-Notebook-Ansicht](#azdata-notebook-view) | Anzeigen eines Notebooks.  Option zum Abbrechen beim ersten Fehler bei der Zellen Ausführung.
[Ausführen von azdata Notebook](#azdata-notebook-run) | Ausführen eines Notebooks.  Die Ausführung wird beim ersten Fehler beendet.
## <a name="azdata-notebook-view"></a>azdata-Notebook-Ansicht
Dieser Befehl kann eine Notebook-Datei annehmen und markdown, Code und Ausgabe in das farbterminal Format konvertieren.
```bash
azdata notebook view --path -p 
                     [--continue-on-error -c]
```
### <a name="examples"></a>Beispiele
Notebook anzeigen.  Dadurch werden alle Zellen angezeigt.
```bash
azdata notebook view --path '/home/me/notebooks/demo_notebook.ipynb'
```
Notebook anzeigen.  Dadurch werden alle Zellen angezeigt, es sei denn, es ist eine Zelle mit einem Fehler in der Ausgabe aufgetreten.  In diesem Fall wird die Ausgabe angehalten.
```bash
azdata notebook view --path '/home/me/notebooks/demo_notebook.ipynb' --stop-on-error
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--path -p`
Der Pfad zu dem Notebook, das angezeigt werden soll.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--continue-on-error -c`
Weitere Zellen anzeigen, die alle Zellen Fehler ignorieren, die in der Notebook-Ausgabe gefunden werden.  Das Standardverhalten besteht darin, bei einem Fehler anzuhalten.  Durch das Anhalten wird die erste Zelle, bei der ein Fehler aufgetreten ist, einfacher angezeigt.
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
## <a name="azdata-notebook-run"></a>Ausführen von azdata Notebook
Dieser Befehl erstellt ein temporäres Verzeichnis und führt das angegebene Notebook darin als Arbeitsverzeichnis aus.
```bash
azdata notebook run --path -p 
                    [--output-path]  
                    [--output-html]
```
### <a name="examples"></a>Beispiele
Notebook ausführen.
```bash
azdata notebook run --path '/home/me/notebooks/demo_notebook.ipynb'
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--path -p`
Der Dateipfad für das Notebook, das ausgeführt werden soll.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--output-path`
Verzeichnispfad, der für die Notebook Ausgabe verwendet werden soll.  Das Notebook mit Ausgabedaten und alle von Notebook generierten Dateien werden relativ zu diesem Verzeichnis generiert.
#### `--output-html`
Optionales Flag, ob das Ausgabe Notebook zusätzlich in das HTML-Format konvertiert werden soll.  Erstellt eine zweite Ausgabedatei.
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

Weitere Informationen zum Installieren des Tools **azdata** finden [Sie unter Install azdata to Manage SQL Server 2019 Big Data Clusters](deploy-install-azdata.md).
