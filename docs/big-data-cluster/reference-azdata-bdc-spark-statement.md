---
title: azdata BDC Spark-Anweisungs Referenz
titleSuffix: SQL Server big data clusters
description: Referenz Artikel für azdata BDC Spark-Anweisungs Befehle.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 778980ac6b93e7db79d59182fbd18ab4cfdb8b75
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426090"
---
# <a name="azdata-bdc-spark-statement"></a>azdata BDC Spark-Anweisung

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)] 

Der folgende Artikel enthält eine Referenz für die Befehle der **BDC Spark-Anweisung** im **azdata** -Tool. Weitere Informationen zu anderen **azdata** -Befehlen finden Sie unter [azdata-Referenz](reference-azdata.md) .

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[azdata BDC Spark-Anweisungs Liste](#azdata-bdc-spark-statement-list) | Listet alle Anweisungen in der angegebenen Spark-Sitzung auf.
[azdata BDC Spark-Anweisung erstellen](#azdata-bdc-spark-statement-create) | Erstellen Sie eine neue Spark-Anweisung in der angegebenen Sitzung.
[Informationen zur azdata BDC Spark-Anweisung](#azdata-bdc-spark-statement-info) | Informationen über die angeforderte Anweisung in der angegebenen Spark-Sitzung erhalten.
[azdata BDC Spark-Anweisung abbrechen](#azdata-bdc-spark-statement-cancel) | Abbrechen einer Anweisung innerhalb der angegebenen Spark-Sitzung.
## <a name="azdata-bdc-spark-statement-list"></a>azdata BDC Spark-Anweisungs Liste
Listet alle Anweisungen in der angegebenen Spark-Sitzung auf.
```bash
azdata bdc spark statement list --session-id -i 
                                
```
### <a name="examples"></a>Beispiele
Listet alle Sitzungs Anweisungen auf.
```bash
azdata spark statement list --session-id 0
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
## <a name="azdata-bdc-spark-statement-create"></a>azdata BDC Spark-Anweisung erstellen
Dadurch wird eine neue Anweisung in der angegebenen Sitzung erstellt und ausgeführt.  Wenn die Ausführung schneller ist, enthält das Ergebnis die Ausgabe der Ausführung.  Andernfalls kann das Ergebnis mithilfe von "Spark-Sitzungsinformationen" abgerufen werden, nachdem die-Anweisung beendet wurde.
```bash
azdata bdc spark statement create --session-id -i 
                                  --code -c
```
### <a name="examples"></a>Beispiele
Führen Sie eine-Anweisung aus.
```bash
azdata spark statement create --session-id 0 --code "2+2"
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--session-id -i`
ID-Nummer der Spark-Sitzung.
#### `--code -c`
Zeichenfolge, die den Code enthält, der als Teil der Anweisung ausgeführt wird.
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
## <a name="azdata-bdc-spark-statement-info"></a>Informationen zur azdata BDC Spark-Anweisung
Dies ruft den Ausführungs Status und die Ausführungs Ergebnisse ab, wenn die Anweisung abgeschlossen wurde. Die Anweisungs-ID wird von "Spark Statement Create" zurückgegeben.
```bash
azdata bdc spark statement info --session-id -i 
                                --statement-id -s
```
### <a name="examples"></a>Beispiele
Get-Anweisungs Informationen für die Sitzung mit der ID 0 und der Anweisungs-ID 0.
```bash
azdata spark statement info --session-id 0 --statement-id 0
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--session-id -i`
ID-Nummer der Spark-Sitzung.
#### `--statement-id -s`
Die ID-Nummer der Spark-Anweisung innerhalb der angegebenen Sitzungs-ID.
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
## <a name="azdata-bdc-spark-statement-cancel"></a>azdata BDC Spark-Anweisung abbrechen
Dadurch wird eine-Anweisung innerhalb der angegebenen Spark-Sitzung abgebrochen. Die Anweisungs-ID wird von "Spark Statement Create" zurückgegeben.
```bash
azdata bdc spark statement cancel --session-id -i 
                                  --statement-id -s
```
### <a name="examples"></a>Beispiele
Abbrechen einer-Anweisung.
```bash
azdata spark statement cancel --session-id 0 --statement-id 0
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--session-id -i`
ID-Nummer der Spark-Sitzung.
#### `--statement-id -s`
Die ID-Nummer der Spark-Anweisung innerhalb der angegebenen Sitzungs-ID.
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
