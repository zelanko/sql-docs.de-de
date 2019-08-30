---
title: azdata BDC HDFS-Status Referenz
titleSuffix: SQL Server big data clusters
description: Referenz Artikel für azdata BDC HDFS-Status Befehle.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 3853e23a0def787a65febf142de4c1d8d8216df7
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70158085"
---
# <a name="azdata-bdc-hdfs-status"></a>azdata BDC HDFS-Status

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

Dieser Artikel ist ein Referenz Artikel für **azdata**. 

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[azdata BDC HDFS-Status anzeigen](#azdata-bdc-hdfs-status-show) | Status des HDFS-Dienstanbieter
## <a name="azdata-bdc-hdfs-status-show"></a>azdata BDC HDFS-Status anzeigen
Status des HDFS-Dienstanbieter
```bash
azdata bdc hdfs status show [--resource -r] 
                            [--all -a]
```
### <a name="examples"></a>Beispiele
Der Status des HDFS-Dienstanbieter wird angezeigt.
```bash
azdata bdc hdfs status show
```
Den Status des HDFS-Dienstanbieter mit allen Instanzen erhalten.
```bash
azdata bdc hdfs status show --all
```
Der Status der Speicher Ressource im HDFS-Dienst wird angezeigt.
```bash
azdata bdc hdfs status show --resource storage-0
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--resource -r`
Diese Ressource in diesem Dienst erhalten.
#### `--all -a`
Alle Instanzen der einzelnen Ressourcen im Dienst anzeigen.
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
