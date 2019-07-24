---
title: Referenz zu azdata BDC-Spark-Sitzungen
titleSuffix: SQL Server big data clusters
description: Referenz Artikel zu azdata BDC-Spark-Sitzungs Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 20b7ac3dcf72482e80278ce0f0df922026232a6d
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426100"
---
# <a name="azdata-bdc-spark-session"></a>azdata BDC-Spark-Sitzung

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)] 

Der folgende Artikel enthält eine Referenz für die **BDC-Spark-Sitzungs** Befehle im **azdata** -Tool. Weitere Informationen zu anderen **azdata** -Befehlen finden Sie unter [azdata-Referenz](reference-azdata.md) .

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[azdata BDC Spark-Sitzung erstellen](#azdata-bdc-spark-session-create) | Erstellen Sie eine neue Spark-Sitzung.
[azdata BDC Spark-Sitzungs Liste](#azdata-bdc-spark-session-list) | Auflisten aller aktiven Sitzungen in Spark.
[Informationen zu azdata BDC Spark-Sitzungen](#azdata-bdc-spark-session-info) | Hier erhalten Sie Informationen zu einer aktiven Spark-Sitzung.
[azdata BDC Spark-Sitzungsprotokoll](#azdata-bdc-spark-session-log) | Ausführungs Protokolle für eine aktive Spark-Sitzung erhalten.
[azdata BDC Spark-Sitzungs Status](#azdata-bdc-spark-session-state) | Ausführungs Status für eine aktive Spark-Sitzung erhalten.
[Löschen von azdata BDC Spark-Sitzungen](#azdata-bdc-spark-session-delete) | Löschen Sie eine Spark-Sitzung.
## <a name="azdata-bdc-spark-session-create"></a>azdata BDC Spark-Sitzung erstellen
Dadurch wird eine neue interaktive Spark-Sitzung erstellt. Der Aufrufer muss den Typ der Spark-Sitzung angeben. Diese Sitzung geht über die Lebensdauer einer azdata-Ausführung hinaus und muss mit "Löschen der Spark-Sitzung" gelöscht werden.
```bash
azdata bdc spark session create [--session-kind -k] 
                                [--jar-files -j]  
                                [--py-files -p]  
                                [--files -f]  
                                [--driver-memory]  
                                [--driver-cores]  
                                [--executor-memory]  
                                [--executor-cores]  
                                [--executor-count]  
                                [--archives -a]  
                                [--queue -q]  
                                [--name -n]  
                                [--config -c]  
                                [--timeout-seconds -t]
```
### <a name="examples"></a>Beispiele
Erstellen Sie eine Sitzung.
```bash
azdata spark session create --session-kind pyspark
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--session-kind -k`
Der Name des zu erstellenden Sitzungs Typs.  Eine von Spark, pyspark, sparkr oder SQL.
#### `--jar-files -j`
Liste der JAR-Dateipfade.  Um eine Liste zu übergeben, codieren Sie die Werte.  Beispiel: "[" entry1 "," Entry2 "]".
#### `--py-files -p`
Liste der python-Dateipfade.  Um eine Liste zu übergeben, codieren Sie die Werte.  Beispiel: "[" entry1 "," Entry2 "]".
#### `--files -f`
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
#### `--archives -a`
Liste der Archive-Pfade.  Um eine Liste zu übergeben, codieren Sie die Werte.  Beispiel: "[" entry1 "," Entry2 "]".
#### `--queue -q`
Der Name der Spark-Warteschlange, in der die Sitzung ausgeführt werden soll.
#### `--name -n`
Der Name der Spark-Sitzung.
#### `--config -c`
Liste von Name-Wert-Paaren, die Spark-Konfigurationswerte enthalten.  Codiert als JSON-Wörterbuch.  Beispiel: "{" Name ":" Value "," name2 ":" Value2 "}".
#### `--timeout-seconds -t`
Timeout für Sitzung im Leerlauf in Sekunden.
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
## <a name="azdata-bdc-spark-session-list"></a>azdata BDC Spark-Sitzungs Liste
Auflisten aller aktiven Sitzungen in Spark.
```bash
azdata bdc spark session list 
```
### <a name="examples"></a>Beispiele
Listet alle aktiven Sitzungen auf.
```bash
azdata spark session list
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
## <a name="azdata-bdc-spark-session-info"></a>Informationen zu azdata BDC Spark-Sitzungen
Dadurch werden die Sitzungsinformationen für eine aktive Spark-Sitzung mit der angegebenen ID abgerufen.  Die Sitzungs-ID wird von "Spark Session Create" zurückgegeben.
```bash
azdata bdc spark session info --session-id -i 
                              
```
### <a name="examples"></a>Beispiele
Sitzungsinformationen für die Sitzung mit der ID "0" erhalten.
```bash
azdata spark session info --session-id 0
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--session-id -i`
ID-Nummer der Spark-Sitzung.
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
## <a name="azdata-bdc-spark-session-log"></a>azdata BDC Spark-Sitzungsprotokoll
Hiermit werden die Sitzungsprotokoll Einträge für eine aktive Spark-Sitzung mit der angegebenen ID abgerufen.  Die Sitzungs-ID wird von "Spark Session Create" zurückgegeben.
```bash
azdata bdc spark session log --session-id -i 
                             
```
### <a name="examples"></a>Beispiele
Das Sitzungsprotokoll für die Sitzung mit der ID "0" wird angezeigt.
```bash
azdata spark session log --session-id 0
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--session-id -i`
ID-Nummer der Spark-Sitzung.
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
## <a name="azdata-bdc-spark-session-state"></a>azdata BDC Spark-Sitzungs Status
Dadurch wird der Sitzungszustand für eine aktive Spark-Sitzung mit der angegebenen ID abgerufen.  Die Sitzungs-ID wird von "Spark Session Create" zurückgegeben.
```bash
azdata bdc spark session state --session-id -i 
                               
```
### <a name="examples"></a>Beispiele
Der Sitzungs Status für die Sitzung mit der ID "0" wird angezeigt.
```bash
azdata spark session state --session-id 0
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--session-id -i`
ID-Nummer der Spark-Sitzung.
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
## <a name="azdata-bdc-spark-session-delete"></a>Löschen von azdata BDC Spark-Sitzungen
Dadurch wird eine interaktive Spark-Sitzung gelöscht. Die Sitzungs-ID wird von "Spark Session Create" zurückgegeben.
```bash
azdata bdc spark session delete --session-id -i 
                                
```
### <a name="examples"></a>Beispiele
Löschen Sie eine Sitzung.
```bash
azdata spark session delete --session-id 0
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--session-id -i`
ID-Nummer der Spark-Sitzung.
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
