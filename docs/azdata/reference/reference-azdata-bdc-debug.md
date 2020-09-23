---
title: 'azdata bdc debug: Referenz'
titleSuffix: SQL Server big data clusters
description: Verwenden Sie diesen Referenzartikel, um die SQL-Befehle (insbesondere die „bdc debug“-Befehle) im azdata-Tool zu verstehen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e9d1f561666bf6aefdef6abf4b1daf568a5a89d8
ms.sourcegitcommit: 883435b4c7366f06ac03579752093737b098feab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2020
ms.locfileid: "89733817"
---
# <a name="azdata-bdc-debug"></a>azdata bdc debug

[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/sqlserver2019.md)]

Der folgende Artikel enthält Referenzinformationen zu den `sql`-Befehlen im `azdata`-Tool. Weitere Informationen zu anderen `azdata`-Befehlen finden Sie in der [Referenz zu azdata](reference-azdata.md).

## <a name="commands"></a>Befehle
| Get-Help | BESCHREIBUNG |
| --- | --- |
[azdata bdc debug copy-logs](#azdata-bdc-debug-copy-logs) | Kopieren von Protokollen.
[azdata bdc debug dump](#azdata-bdc-debug-dump) | Auslösen eines Speicherabbilds
## <a name="azdata-bdc-debug-copy-logs"></a>azdata bdc debug copy-logs
Kopiert die Debugprotokolle aus dem Big Data-Cluster – auf Ihrem System ist eine Kubernetes-Konfiguration erforderlich.
```bash
azdata bdc debug copy-logs --namespace -n 
                           [--container -c]  
                           
[--target-folder -d]  
                           
[--pod -p]  
                           
[--timeout -t]  
                           
[--skip-compress -sc]  
                           
[--exclude-dumps -ed]
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--namespace -n`
Der Big Data-Clustername, der für den kubernetes-Namespace verwendet wird.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--container -c`
Kopieren Sie die Protokolle für die Container mit ähnlichem Namen. Standardmäßig werden die Protokolle für alle Container kopiert. Dieser Parameter kann nicht mehrfach angegeben werden. Ist er mehrfach angegeben, wird der letzte Parameter verwendet.
#### `--target-folder -d`
Der Pfad des Zielordners, in den die Protokolle kopiert werden sollen. Optional. Standardmäßig wird das Ergebnis im lokalen Ordner erstellt.  Dieser Parameter kann nicht mehrfach angegeben werden. Ist er mehrfach angegeben, wird der letzte Parameter verwendet.
#### `--pod -p`
Kopieren Sie die Protokolle für die Pods mit ähnlichem Namen. Optional. Standardmäßig werden die Protokolle für alle Pods kopiert. Dieser Parameter kann nicht mehrfach angegeben werden. Ist er mehrfach angegeben, wird der letzte Parameter verwendet.
#### `--timeout -t`
Die Zeit in Sekunden, während der auf das Abschließen des Befehls gewartet wird. Der Standardwert ist „0“, d. h., das Warten ist unbegrenzt.
#### `--skip-compress -sc`
Gibt an, ob die Komprimierung des resultierenden Ordners übersprungen werden soll Der Standardwert ist „False“. Dadurch wird der resultierende Ordner komprimiert.
#### `--exclude-dumps -ed`
Gibt an, ob Sicherungsdateien aus dem resultierenden Ordner ausgeschlossen werden sollen Der Standardwert ist „False“. Dadurch werden Sicherungsdateien eingeschlossen.
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
## <a name="azdata-bdc-debug-dump"></a>azdata bdc debug dump
Lösen Sie ein Speicherabbild aus, und kopieren Sie es aus dem Container. Hierfür ist eine Kubernetes-Konfiguration auf Ihrem System erforderlich.
```bash
azdata bdc debug dump --namespace -n 
                      [--container -c]  
                      
[--target-folder -d]
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--namespace -n`
Der Big Data-Clustername, der für den kubernetes-Namespace verwendet wird.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--container -c`
Hierbei handelt es sich um den Zielcontainer, der zum Sichern der aktiven Prozesse ausgelöst werden soll. `controller`
#### `--target-folder -d`
Hierbei handelt es sich um den Zielordner, aus dem das Abbild kopiert wird. `./output/dump`
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

Weitere Informationen zu anderen `azdata`-Befehlen finden Sie in der [Referenz zu azdata](reference-azdata.md). Weitere Informationen zur Installation des `azdata`-Tools finden Sie unter [Installieren von azdata zum Verwalten von Big Data-Clustern für SQL Server 2019](../install/deploy-install-azdata.md).
