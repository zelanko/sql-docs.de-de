---
title: Mssqlctl Cluster Debug-Referenz
titleSuffix: SQL Server big data clusters
description: Der Referenzartikel für die Mssqlctl Cluster Debug-Befehle.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 05/22/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 4eafc3838d153a2616e34e98aed041374c04292d
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66779399"
---
# <a name="mssqlctl-cluster-debug"></a>Debuggen des mssqlctl-Clusters

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel bietet Referenz für die **Cluster Debug** Befehle in der **Mssqlctl** Tool. Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[Mssqlctl Cluster Debug-Protokolle kopieren](#mssqlctl-cluster-debug-copy-logs) | Kopieren Sie Protokolle.
[Mssqlctl Cluster debugdumpdateien](#mssqlctl-cluster-debug-dump) | Dump der Trigger-Protokollierung.
## <a name="mssqlctl-cluster-debug-copy-logs"></a>Mssqlctl Cluster Debug-Protokolle kopieren
Kopieren Sie die Debugprotokolle aus dem Cluster - Kube-Konfigurationsdatei muss auf Ihrem System.
```bash
mssqlctl cluster debug copy-logs --namespace -n 
                                 [--container -c]  
                                 [--target-folder -d]  
                                 [--pod -p]  
                                 [--timeout -t]
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--namespace -n`
Clustername für Kubernetes-Namespace verwendet.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--container -c`
Kopieren Sie die Protokolle für Container mit einem ähnlichen Namen, Optional, standardmäßig kopiert Protokolle für alle Container. Kann nicht mehrmals angegeben werden. Wenn mehrere Male angegeben wird, wird zuletzt eine verwendet
#### `--target-folder -d`
Ziel-Ordnerpfad zum Kopieren der Protokolle an. Optional, erstellt standardmäßig das Ergebnis in den lokalen Ordner.  Kann nicht mehrmals angegeben werden. Wenn mehrere Male angegeben wird, wird zuletzt eine verwendet
#### `--pod -p`
Kopieren Sie die Protokolle für die Pods mit ähnlichen Namen ein. Optional, Kopien der Standardprotokolle für alle Pods. Kann nicht mehrmals angegeben werden. Wenn mehrere Male angegeben wird, wird zuletzt eine verwendet
#### `--timeout -t`
Die Anzahl der Sekunden warten, bis der Befehl ausgeführt werden soll. Der Standardwert ist 0 unbegrenzt ist
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöht die protokollierungsausführlichkeit, sodass alle Debugprotokolle angezeigt.
#### `--help -h`
Zeigen Sie diese hilfemeldung an und beendet.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: Json, Jsonc, Table, Tsv.  Standardwert: Json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Finden Sie unter [ http://jmespath.org/ ](http://jmespath.org/]) für Weitere Informationen und Beispiele.
#### `--verbose`
Erhöht die protokollierungsausführlichkeit. Verwenden Sie--Debug, wenn Sie vollständige Debugprotokolle wünschen.
## <a name="mssqlctl-cluster-debug-dump"></a>Mssqlctl Cluster debugdumpdateien
Protokollierung Dump auslösen, und kopieren sie Sie aus Container - Kube-Konfigurationsdatei muss auf Ihrem System.
```bash
mssqlctl cluster debug dump --namespace -n 
                            --container -c  
                            [--target-folder -d]
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--namespace -n`
Clustername für Kubernetes-Namespace verwendet.
#### `--container -c`
Kopieren Sie die Protokolle für Container mit einem ähnlichen Namen, Optional, standardmäßig kopiert Protokolle für alle Container. Kann nicht mehrmals angegeben werden. Wenn mehrere Male angegeben wird, wird zuletzt eine verwendet
### <a name="optional-parameters"></a>Optionale Parameter
#### `--target-folder -d`
Ziel-Ordnerpfad zum Kopieren der Protokolle an. Optional, erstellt standardmäßig das Ergebnis in den lokalen Ordner.  Kann nicht mehrmals angegeben werden. Wenn mehrere Male angegeben wird, wird zuletzt eine verwendet `./output/dump`
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöht die protokollierungsausführlichkeit, sodass alle Debugprotokolle angezeigt.
#### `--help -h`
Zeigen Sie diese hilfemeldung an und beendet.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: Json, Jsonc, Table, Tsv.  Standardwert: Json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Finden Sie unter [ http://jmespath.org/ ](http://jmespath.org/]) für Weitere Informationen und Beispiele.
#### `--verbose`
Erhöht die protokollierungsausführlichkeit. Verwenden Sie--Debug, wenn Sie vollständige Debugprotokolle wünschen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md). Weitere Informationen zum Installieren der **Mssqlctl** finden Sie unter [Mssqlctl zum Verwalten von SQL Server-2019 big Data-Cluster installieren](deploy-install-mssqlctl.md).