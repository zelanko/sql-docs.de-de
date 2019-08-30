---
title: 'azdata bdc debug: Referenz'
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata bdc debug-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9e14528baf80d08841f6e9e17a0476dfa81fd48d
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70153195"
---
# <a name="azdata-bdc-debug"></a>azdata bdc debug

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

Dieser Artikel ist ein Referenz Artikel für **azdata**. 

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[azdata bdc debug copy-logs](#azdata-bdc-debug-copy-logs) | Kopieren von Protokollen.
[azdata bdc debug dump](#azdata-bdc-debug-dump) | Auslösen einer Protokollierungssicherung.
## <a name="azdata-bdc-debug-copy-logs"></a>azdata bdc debug copy-logs
Kopieren Sie die Debugprotokolle aus dem Big Data-Cluster Kubernetes die Konfiguration ist auf Ihrem System erforderlich.
```bash
azdata bdc debug copy-logs --namespace -n 
                           [--container -c]  
                           [--target-folder -d]  
                           [--pod -p]  
                           [--timeout -t]
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
## <a name="azdata-bdc-debug-dump"></a>azdata bdc debug dump
Protokollieren der Protokollierung und Kopieren der Datei aus dem Container Kubernetes auf Ihrem System ist eine Konfiguration erforderlich.
```bash
azdata bdc debug dump --namespace -n 
                      --container -c  
                      [--target-folder -d]
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--namespace -n`
Der Big Data-Clustername, der für den kubernetes-Namespace verwendet wird.
#### `--container -c`
Kopieren Sie die Protokolle für die Container mit ähnlichem Namen. Standardmäßig werden die Protokolle für alle Container kopiert. Dieser Parameter kann nicht mehrfach angegeben werden. Ist er mehrfach angegeben, wird der letzte Parameter verwendet.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--target-folder -d`
Der Pfad des Zielordners, in den die Protokolle kopiert werden sollen. Optional. Standardmäßig wird das Ergebnis im lokalen Ordner erstellt.  Dieser Parameter kann nicht mehrfach angegeben werden. Ist er mehrfach angegeben, wird der letzte Parameter verwendet (`./output/dump`).
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
