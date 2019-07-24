---
title: Referenz zum Debuggen von azdata BDC
titleSuffix: SQL Server big data clusters
description: Referenz Artikel für azdata BDC-Debugbefehle.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 38c327287273ae6596326d88d9e0d67c8e014d47
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426230"
---
# <a name="azdata-bdc-debug"></a>Debuggen von azdata BDC

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel enthält einen Verweis auf die **BDC-Debugbefehle** im **azdata** -Tool. Weitere Informationen zu anderen **azdata** -Befehlen finden Sie unter [azdata-Referenz](reference-azdata.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[azdata BDC debugkopieren-Protokolle](#azdata-bdc-debug-copy-logs) | Kopieren von Protokollen.
[azdata BDC-debugdump](#azdata-bdc-debug-dump) | Protokollierung der Protokollierung.
## <a name="azdata-bdc-debug-copy-logs"></a>azdata BDC debugkopieren-Protokolle
Kopieren Sie die Debugprotokolle aus dem Big Data-Cluster. die Kube-Konfiguration ist auf Ihrem System erforderlich.
```bash
azdata bdc debug copy-logs --namespace -n 
                           [--container -c]  
                           [--target-folder -d]  
                           [--pod -p]  
                           [--timeout -t]
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--namespace -n`
Big Data-Cluster Name, der für den kubernetes-Namespace verwendet wird.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--container -c`
Kopieren Sie die Protokolle für die Container mit dem gleichen Namen, optional, kopiert standardmäßig Protokolle für alle Container. Kann nicht mehrmals angegeben werden. Wenn die Angabe mehrmals angegeben ist, wird die letzte verwendet.
#### `--target-folder -d`
Der Zielordner Pfad, in den Protokolle kopiert werden sollen. Optional: erstellt das Ergebnis standardmäßig im lokalen Ordner.  Kann nicht mehrmals angegeben werden. Wenn die Angabe mehrmals angegeben ist, wird die letzte verwendet.
#### `--pod -p`
Kopieren Sie die Protokolle für die Pods mit ähnlichem Namen. Optional: kopiert standardmäßig Protokolle für alle Pods. Kann nicht mehrmals angegeben werden. Wenn die Angabe mehrmals angegeben ist, wird die letzte verwendet.
#### `--timeout -t`
Die Anzahl der Sekunden, die auf den Abschluss des Befehls gewartet werden soll. Der Standardwert ist 0 (null).
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
## <a name="azdata-bdc-debug-dump"></a>azdata BDC-debugdump
Die Protokollierung der Auslöse Protokollierung und das Kopieren aus der Container-Kube-Konfiguration ist auf Ihrem System erforderlich.
```bash
azdata bdc debug dump --namespace -n 
                      --container -c  
                      [--target-folder -d]
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--namespace -n`
Big Data-Cluster Name, der für den kubernetes-Namespace verwendet wird.
#### `--container -c`
Kopieren Sie die Protokolle für die Container mit dem gleichen Namen, optional, kopiert standardmäßig Protokolle für alle Container. Kann nicht mehrmals angegeben werden. Wenn die Angabe mehrmals angegeben ist, wird die letzte verwendet.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--target-folder -d`
Der Zielordner Pfad, in den Protokolle kopiert werden sollen. Optional: erstellt das Ergebnis standardmäßig im lokalen Ordner.  Kann nicht mehrmals angegeben werden. Wenn die Angabe mehrmals angegeben ist, wird die letzte verwendet.`./output/dump`
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
