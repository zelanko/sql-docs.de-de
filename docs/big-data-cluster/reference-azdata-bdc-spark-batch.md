---
title: Referenz zu azdata BDC Spark-Batches
titleSuffix: SQL Server big data clusters
description: Referenz Artikel zu Befehlen von azdata BDC Spark Batch.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 6e242b26f439b49dbf0b3cf5ab50ea46c273f45f
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426160"
---
# <a name="azdata-bdc-spark-batch"></a>azdata BDC Spark-Batch

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel enthält eine Referenz für die **BDC Spark-Batch** Befehle im **azdata** -Tool. Weitere Informationen zu anderen **azdata** -Befehlen finden Sie unter [azdata-Referenz](reference-azdata.md) .

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[azdata BDC Spark Batch erstellen](#azdata-bdc-spark-batch-create) | Erstellen Sie einen neuen Spark-Batch.
[azdata BDC Spark-Batch Liste](#azdata-bdc-spark-batch-list) | Listet alle Batches in Spark auf.
[Informationen zu azdata BDC Spark-Batch](#azdata-bdc-spark-batch-info) | Hier erhalten Sie Informationen zu einem aktiven Spark-Batch.
[azdata BDC Spark-Batch Protokoll](#azdata-bdc-spark-batch-log) | Sie erhalten Ausführungs Protokolle für einen Spark-Batch.
[azdata BDC Spark-Batch Status](#azdata-bdc-spark-batch-state) | Den Ausführungs Status für einen Spark-Batch erhalten.
[azdata BDC Spark-Batch löschen](#azdata-bdc-spark-batch-delete) | Löschen eines Spark-Batches.
## <a name="azdata-bdc-spark-batch-create"></a>azdata BDC Spark Batch erstellen
Dadurch wird ein neuer Batch Spark-Auftrag erstellt, der den bereitgestellten Code ausführt.
```bash
azdata bdc spark batch create --file -f 
                              [--class-name -c]  
                              [--arguments -a]  
                              [--jar-files -j]  
                              [--py-files -p]  
                              [--files]  
                              [--driver-memory]  
                              [--driver-cores]  
                              [--executor-memory]  
                              [--executor-cores]  
                              [--executor-count]  
                              [--archives]  
                              [--queue -q]  
                              [--name -n]  
                              [--config]
```
### <a name="examples"></a>Beispiele
Erstellen Sie einen neuen Spark-Batch.
```bash
azdata spark batch create --code "2+2"
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--file -f`
Pfad zur auszuführenden Datei.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--class-name -c`
Der Name der Klasse, die beim Übergeben einer oder mehrerer JAR-Dateien ausgeführt werden soll.
#### `--arguments -a`
Die Liste der Argumente.  Um eine Liste zu übergeben, codieren Sie die Werte.  Beispiel: "[" entry1 "," Entry2 "]".
#### `--jar-files -j`
Liste der JAR-Dateipfade.  Um eine Liste zu übergeben, codieren Sie die Werte.  Beispiel: "[" entry1 "," Entry2 "]".
#### `--py-files -p`
Liste der python-Dateipfade.  Um eine Liste zu übergeben, codieren Sie die Werte.  Beispiel: "[" entry1 "," Entry2 "]".
#### `--files`
Liste der Dateipfade.  Um eine Liste zu übergeben, codieren Sie die Werte.  Beispiel: "[" entry1 "," Entry2 "]".
#### `--driver-memory`
Die Menge an Arbeitsspeicher, die dem Treiber zuzuordnen ist.  Legen Sie Einheiten als Teil des Werts fest.  Beispiel 512 m oder 2G.
#### `--driver-cores`
Menge der CPU-Kerne, die dem Treiber zuzuordnen sind.
#### `--executor-memory`
Die Menge an Arbeitsspeicher, die dem Executor zuzuordnen ist.  Legen Sie Einheiten als Teil des Werts fest.  Beispiel 512 m oder 2G.
#### `--executor-cores`
Menge der CPU-Kerne, die dem Executor zuzuordnen sind.
#### `--executor-count`
Anzahl der zu testenden Ausführungs Instanzen des Executor.
#### `--archives`
Liste der Archive-Pfade.  Um eine Liste zu übergeben, codieren Sie die Werte.  Beispiel: "[" entry1 "," Entry2 "]".
#### `--queue -q`
Der Name der Spark-Warteschlange, in der die Sitzung ausgeführt werden soll.
#### `--name -n`
Der Name der Spark-Sitzung.
#### `--config`
Liste von Name-Wert-Paaren, die Spark-Konfigurationswerte enthalten.  Codiert als JSON-Wörterbuch.  Beispiel: "{" Name ":" Value "," name2 ":" Value2 "}".
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
## <a name="azdata-bdc-spark-batch-list"></a>azdata BDC Spark-Batch Liste
Listet alle Batches in Spark auf.
```bash
azdata bdc spark batch list 
```
### <a name="examples"></a>Beispiele
Listet alle aktiven Batches auf.
```bash
azdata spark batch list
```
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
## <a name="azdata-bdc-spark-batch-info"></a>Informationen zu azdata BDC Spark-Batch
Dadurch werden die Informationen für einen Spark-Batch mit der angegebenen ID abgerufen.  Die Batch-ID wird von "Spark Batch Create" zurückgegeben.
```bash
azdata bdc spark batch info --batch-id -i 
                            
```
### <a name="examples"></a>Beispiele
Batch Informationen für Batch mit der ID "0" erhalten.
```bash
azdata spark batch info --batch-id 0
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--batch-id -i`
Spark-Batch-ID-Nummer.
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
## <a name="azdata-bdc-spark-batch-log"></a>azdata BDC Spark-Batch Protokoll
Dadurch werden die Batch Protokolleinträge für einen Spark-Batch mit der angegebenen ID abgerufen.  Die Batch-ID wird von "Spark Batch Create" zurückgegeben.
```bash
azdata bdc spark batch log --batch-id -i 
                           
```
### <a name="examples"></a>Beispiele
Batch Protokoll für Batch mit der ID "0" erhalten.
```bash
azdata spark batch log --batch-id 0
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--batch-id -i`
Spark-Batch-ID-Nummer.
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
## <a name="azdata-bdc-spark-batch-state"></a>azdata BDC Spark-Batch Status
Dadurch wird der Batch Status für einen Spark-Batch mit der angegebenen ID abgerufen.  Die Batch-ID wird von "Spark Batch Create" zurückgegeben.
```bash
azdata bdc spark batch state --batch-id -i 
                             
```
### <a name="examples"></a>Beispiele
Der Batch Status für den Batch mit der ID "0" wird angezeigt.
```bash
azdata spark batch state --batch-id 0
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--batch-id -i`
Spark-Batch-ID-Nummer.
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
## <a name="azdata-bdc-spark-batch-delete"></a>azdata BDC Spark-Batch löschen
Dadurch wird ein Spark-Batch gelöscht. Die Batch-ID wird von "Spark Batch Create" zurückgegeben.
```bash
azdata bdc spark batch delete --batch-id -i 
                              
```
### <a name="examples"></a>Beispiele
Löschen eines Batches.
```bash
azdata spark batch delete --batch-id 0
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--batch-id -i`
Spark-Batch-ID-Nummer.
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
