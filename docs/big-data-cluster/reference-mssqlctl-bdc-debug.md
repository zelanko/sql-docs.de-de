---
title: Mssqlctl BDC-Debug-Referenz
titleSuffix: SQL Server big data clusters
description: Der Referenzartikel für die Mssqlctl BDC-Debug-Befehle.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: dde99490805ec0f78c9acbaa3875f1ae1406e77f
ms.sourcegitcommit: ce5770d8b91c18ba5ad031e1a96a657bde4cae55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2019
ms.locfileid: "67394342"
---
# <a name="mssqlctl-bdc-debug"></a>Mssqlctl BDC-debug

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel bietet Referenz für die **BDC-Debug** Befehle in der **Mssqlctl** Tool. Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[Mssqlctl BDC-Debug-Protokolle kopieren](#mssqlctl-bdc-debug-copy-logs) | Kopieren Sie Protokolle.
[mssqlctl bdc debug dump](#mssqlctl-bdc-debug-dump) | Dump der Trigger-Protokollierung.
## <a name="mssqlctl-bdc-debug-copy-logs"></a>Mssqlctl BDC-Debug-Protokolle kopieren
Kopieren Sie die Debugprotokolle aus dem Big Data-Cluster – Kube-Konfigurationsdatei muss auf Ihrem System.
```bash
mssqlctl bdc debug copy-logs --namespace -n 
                             [--container -c]  
                             [--target-folder -d]  
                             [--pod -p]  
                             [--timeout -t]
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--namespace -n`
BDC-Name, der für Kubernetes-Namespace verwendet.
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
## <a name="mssqlctl-bdc-debug-dump"></a>Mssqlctl Bdc-debugdumpdateien
Protokollierung Dump auslösen, und kopieren sie Sie aus Container - Kube-Konfigurationsdatei muss auf Ihrem System.
```bash
mssqlctl bdc debug dump --namespace -n 
                        --container -c  
                        [--target-folder -d]
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--namespace -n`
BDC-Name, der für Kubernetes-Namespace verwendet.
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