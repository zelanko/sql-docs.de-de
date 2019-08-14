---
title: 'azdata bdc debug: Referenz'
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata bdc debug-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 38c327287273ae6596326d88d9e0d67c8e014d47
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68426230"
---
# <a name="azdata-bdc-debug"></a>azdata bdc debug

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel enthält Referenzinformationen zu den **bdc debug**-Befehlen im **azdata**-Tool. Weitere Informationen zu anderen **azdata**-Befehlen finden Sie unter [azdata](reference-azdata.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[azdata bdc debug copy-logs](#azdata-bdc-debug-copy-logs) | Kopieren von Protokollen.
[azdata bdc debug dump](#azdata-bdc-debug-dump) | Auslösen einer Protokollierungssicherung.
## <a name="azdata-bdc-debug-copy-logs"></a>azdata bdc debug copy-logs
Kopiert die Debugprotokolle aus dem Big Data-Cluster. Auf Ihrem System ist eine Kube-Konfiguration erforderlich.
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
Erhöhen Sie die Ausführlichkeit der Protokollierung, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Erhöhen Sie die Ausführlichkeit der Protokollierung. Verwenden Sie „--debug“ für vollständige Debugprotokolle.
## <a name="azdata-bdc-debug-dump"></a>azdata bdc debug dump
Sie lösen eine Protokollierungssicherung aus, und diese wird aus dem Container kopiert. Es ist eine Kube-Konfiguration auf Ihrem System erforderlich.
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
Erhöhen Sie die Ausführlichkeit der Protokollierung, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Erhöhen Sie die Ausführlichkeit der Protokollierung. Verwenden Sie „--debug“ für vollständige Debugprotokolle.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu anderen **azdata**-Befehlen finden Sie unter [azdata](reference-azdata.md). Weitere Informationen zum Installieren des Tools **azdata** finden Sie unter [Install azdata to manage SQL Server 2019 big data clusters (Installieren von azdata zum Verwalten von Big Data-Clustern von SQL Server 2019)](deploy-install-azdata.md).
