---
title: Referenz zu azdata bdc app status
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata bdc app status-Befehlen
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 4435a1683b42b48e83aa2902aaba59c4b7a2ab22
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73531872"
---
# <a name="azdata-bdc-app-status"></a>azdata bdc app status

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

Der folgende Artikel enthält Referenzinformationen zu `sql`-Befehlen im `azdata`-Tool. Weitere Informationen zu anderen `azdata`-Befehlen finden Sie in der [Referenz zu azdata](reference-azdata.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[azdata bdc app status show](#azdata-bdc-app-status-show) | Status des App-Diensts
## <a name="azdata-bdc-app-status-show"></a>azdata bdc app status show
Status des App-Diensts
```bash
azdata bdc app status show [--resource -r] 
                           [--all -a]
```
### <a name="examples"></a>Beispiele
Ruft den Status des App-Diensts ab
```bash
azdata bdc app status show
```
Ruft den Status des App-Diensts mit allen Instanzen ab
```bash
azdata bdc app status show --all
```
Ruft den Status der App-Proxyressource im App-Dienst ab
```bash
azdata bdc app status show --resource appproxy
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--resource -r`
Ruft diese Ressource in diesem Dienst ab
#### `--all -a`
Zeigt alle Instanzen jeder Ressource im Dienst an
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu anderen `azdata`-Befehlen finden Sie in der [Referenz zu azdata](reference-azdata.md). Weitere Informationen zur Installation des `azdata`-Tools finden Sie unter [Installieren von azdata zum Verwalten von Big Data-Clustern für SQL Server 2019](deploy-install-azdata.md).
