---
title: Mssqlctl BDC-Referenz
titleSuffix: SQL Server big data clusters
description: Der Referenzartikel für die Mssqlctl BDC-Befehle.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a9da2de60248246bee3daeeaee40d3071da69c4b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67957957"
---
# <a name="mssqlctl-bdc"></a>Mssqlctl bdc

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel bietet Referenz für die **Bdc** Befehle in der **Mssqlctl** Tool. Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[Mssqlctl Bdc erstellen](#mssqlctl-bdc-create) | Big Data-Cluster zu erstellen.
[Mssqlctl BDC-löschen](#mssqlctl-bdc-delete) | Big Data-Cluster zu löschen.
[Mssqlctl BDC-Konfiguration](reference-mssqlctl-bdc-config.md) | Konfigurationsbefehle.
[Mssqlctl BDC-Endpunkt](reference-mssqlctl-bdc-endpoint.md) | Endpunktbefehle.
[Mssqlctl BDC-status](reference-mssqlctl-bdc-status.md) | Status-Befehle.
[Mssqlctl BDC-debug](reference-mssqlctl-bdc-debug.md) | Debug-Befehle.
[Mssqlctl Bdc-Speicherpool](reference-mssqlctl-bdc-storage-pool.md) | Speicher-Pool-Befehle.
[Mssqlctl BDC-Steuerelement](reference-mssqlctl-bdc-control.md) | Befehle.
[Mssqlctl BDC-pool](reference-mssqlctl-bdc-pool.md) | Befehle für Ressourcenpools.
## <a name="mssqlctl-bdc-create"></a>Mssqlctl Bdc erstellen
Erstellen eine SQL Server für Big Data-Cluster – Kube-Konfigurationsdatei muss auf Ihrem System sowie die folgenden Umgebungsvariablen ['CONTROLLER_USERNAME', "CONTROLLER_PASSWORD", "DOCKER_USERNAME", "DOCKER_PASSWORD", "MSSQL_SA_PASSWORD", 'KNOX_PASSWORD'].
```bash
mssqlctl bdc create [--config-profile -c] 
                    [--accept-eula -a]  
                    [--node-label -l]  
                    [--force -f]
```
### <a name="examples"></a>Beispiele
Praktische Anleitung für die BDC-Bereitstellung – erhalten Sie Anweisungen für die erforderlichen Werte.
```bash
mssqlctl bdc create
```
BDC-Bereitstellung mit Argumenten.
```bash
mssqlctl bdc create --accept-eula yes --config-profile aks-dev-test
```
BDC-Bereitstellung mit Argumenten - eingabeaufforderungen als--Force erhält, die-Flag verwendet wird.
```bash
mssqlctl bdc create --accept-eula yes --config-profile aks-dev-test --force
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--config-profile -c`
BDC-Config-Profil, für die Bereitstellung des Clusters verwendet: ["Aks-Dev-Test", "Kubeadm-Dev-Test", "Minikube-Dev-Test"]
#### `--accept-eula -a`
Stimmen Sie den Lizenzbedingungen zu? [Yes/No]. Wenn Sie nicht, verwenden Sie dieses Argument möchten, können Sie die Umgebungsvariable ACCEPT_EULA auf "Ja" festlegen.
#### `--node-label -l`
BDC-knotenbezeichnung, welche Knoten für die Bereitstellung auf festgelegt.
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
## <a name="mssqlctl-bdc-delete"></a>Mssqlctl BDC-löschen
Löschen die SQL Server für Big Data-Cluster – Kube-Konfigurationsdatei muss auf Ihrem System sowie die folgenden Umgebungsvariablen ['CONTROLLER_USERNAME', 'CONTROLLER_PASSWORD'].
```bash
mssqlctl bdc delete --name -n 
                    [--force -f]
```
### <a name="examples"></a>Beispiele
BDC-Löschung, in dem Controller-Benutzername und Kennwort bereits in Ihrer Umgebung festgelegt werden.
```bash
mssqlctl bdc delete --name <cluster_name>
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--name -n`
BDC-Name, der für Kubernetes-Namespace verwendet.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--force -f`
Erzwingen Sie das BDC löschen.
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
