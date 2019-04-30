---
title: Mssqlctl Cluster-Referenz
titleSuffix: SQL Server big data clusters
description: Der Referenzartikel für die Mssqlctl Cluster-Befehle.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c69aeced2378e018376172e1fb6370d56706ecb7
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63473324"
---
# <a name="mssqlctl-cluster"></a>mssqlctl-Cluster

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel bietet Referenz für die **Cluster** Befehle in der **Mssqlctl** Tool. Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[Mssqlctl-Cluster erstellen](#mssqlctl-cluster-create) | Cluster zu erstellen.
[Mssqlctl Cluster löschen](#mssqlctl-cluster-delete) | Löschen Sie Cluster.
[Mssqlctl Cluster-Konfiguration](reference-mssqlctl-cluster-config.md) | Konfigurationsbefehle-Cluster.
[Mssqlctl Cluster Debuggen](reference-mssqlctl-cluster-debug.md) | Debug-Befehle.
## <a name="mssqlctl-cluster-create"></a>Mssqlctl-Cluster erstellen
Erstellen Sie eine SQL Server-Big Data-Cluster.
```bash
mssqlctl cluster create [--config-file -f] 
                        [--accept-eula -e]  
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--config-file -f`
Cluster-Config-Profil, für die Bereitstellung des Clusters verwendet: ["Aks-Dev-Test.json', ' Kubeadm-Dev-Test.json', ' Minikube-Dev-Test.json']
#### `--accept-eula -e`
Stimmen Sie den Lizenzbedingungen zu? [Yes/No].
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
## <a name="mssqlctl-cluster-delete"></a>Mssqlctl Cluster löschen
Löschen Sie die SQL Server-Big Data-Cluster.
```bash
mssqlctl cluster delete --name -n 
                        [--force -f]
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--name -n`
Clustername für Kubernetes-Namespace verwendet.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--force -f`
-Force-Delete Cluster.
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
