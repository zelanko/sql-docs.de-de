---
title: Referenz zum azdata-BDC-Steuerungs Status
titleSuffix: SQL Server big data clusters
description: Referenz Artikel zu Befehlen des Befehls "azdata BDC Control".
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d1f7e2e5931ec55cd2fd2632072de223db252b84
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426250"
---
# <a name="azdata-bdc-control-status"></a>Status des azdata-BDC-Steuer Elements

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel enthält einen Verweis auf die **BDC-Steuerungs Status** -Befehle im **azdata** -Tool. Weitere Informationen zu anderen **azdata** -Befehlen finden Sie unter [azdata-Referenz](reference-azdata.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[Statusanzeige für azdata-BDC-Steuerelement](#azdata-bdc-control-status-show) | Steuern des Status.
## <a name="azdata-bdc-control-status-show"></a>Statusanzeige für azdata-BDC-Steuerelement
Steuern des Status.
```bash
azdata bdc control status show 
```
### <a name="examples"></a>Beispiele
Gibt den Status des Steuer Elements an.
```bash
azdata bdc control status show
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

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Installieren des Tools **azdata** finden [Sie unter Install azdata to Manage SQL Server 2019 Big Data Clusters](deploy-install-azdata.md).
