---
title: Mssqlctl Cluster-Referenz
titleSuffix: SQL Server big data clusters
description: Der Referenzartikel für die Mssqlctl Cluster-Befehle.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 05/22/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 654888bc27fec43abb8a8f511b0de7a4972e4377
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66779255"
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
[clusterendpunkt mssqlctl](reference-mssqlctl-cluster-endpoint.md) | Endpunktbefehle.
[Clusterstatus mssqlctl](reference-mssqlctl-cluster-status.md) | Status-Befehle.
[Mssqlctl Cluster Debuggen](reference-mssqlctl-cluster-debug.md) | Debug-Befehle.
[Mssqlctl-clusterspeicherpools](reference-mssqlctl-cluster-storage-pool.md) | Verwalten von Cluster-Speicherpools.
## <a name="mssqlctl-cluster-create"></a>Mssqlctl-Cluster erstellen
Erstellen eine SQL Server für Big Data-Cluster – Kube-Konfigurationsdatei muss auf Ihrem System sowie die folgenden Umgebungsvariablen ['CONTROLLER_USERNAME', "CONTROLLER_PASSWORD", "DOCKER_USERNAME", "DOCKER_PASSWORD", "MSSQL_SA_PASSWORD", 'KNOX_PASSWORD'].
```bash
mssqlctl cluster create [--config-file -c] 
                        [--accept-eula -a]  
                        [--node-label -l]  
                        [--force -f]
```
### <a name="examples"></a>Beispiele
Praktische Anleitung für Cluster-Bereitstellung – erhalten Sie Anweisungen für die erforderlichen Werte.
```bash
mssqlctl cluster create
```
Clusterbereitstellung mit Argumenten.
```bash
mssqlctl cluster create --accept-eula yes --config-file aks-dev-test.json
```
Bereitstellung des Clusters mit Argumenten - eingabeaufforderungen als--Force erhält, die-Flag verwendet wird.
```bash
mssqlctl cluster create --accept-eula yes --config-file aks-dev-test.json --force
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--config-file -c`
Cluster-Config-Profil, für die Bereitstellung des Clusters verwendet: ["Aks-Dev-Test.json', ' Kubeadm-Dev-Test.json', ' Minikube-Dev-Test.json']
#### `--accept-eula -a`
Stimmen Sie den Lizenzbedingungen zu? [Yes/No]. Wenn Sie nicht, verwenden Sie dieses Argument möchten, können Sie die Umgebungsvariable ACCEPT_EULA auf "Ja" festlegen.
#### `--node-label -l`
Cluster-knotenbezeichnung, welche Knoten für die Bereitstellung auf festgelegt.
#### `--force -f`
Erstellvorgang erzwingen, der Benutzer wird nicht für eine beliebige Werte aufgefordert werden, und alle Probleme werden als Teil des "stderr" ausgegeben werden.
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
Löschen die SQL Server für Big Data-Cluster – Kube-Konfigurationsdatei muss auf Ihrem System sowie die folgenden Umgebungsvariablen ['CONTROLLER_USERNAME', 'CONTROLLER_PASSWORD'].
```bash
mssqlctl cluster delete --name -n 
                        [--force -f]
```
### <a name="examples"></a>Beispiele
Cluster löschen, die, in dem Controller-Benutzername und Kennwort bereits in Ihrer Umgebung festgelegt werden.
```bash
mssqlctl cluster delete --name <cluster_name>
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
