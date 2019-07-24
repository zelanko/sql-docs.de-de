---
title: Referenz zu azdata-BDC
titleSuffix: SQL Server big data clusters
description: Referenz Artikel zu azdata BDC-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 488394cbf4b52a952ffc46ab2ec6c9a273466bd5
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426040"
---
# <a name="azdata-bdc"></a>azdata-BDC

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel enthält einen Verweis auf die **BDC** -Befehle im **azdata** -Tool. Weitere Informationen zu anderen **azdata** -Befehlen finden Sie unter [azdata-Referenz](reference-azdata.md).

## <a name="commands"></a>Befehle

|     |     |
| --- | --- |
[azdata BDC Create](#azdata-bdc-create) | Erstellen Sie einen Big Data-Cluster.
[azdata BDC DELETE](#azdata-bdc-delete) | Löschen Sie den Big Data-Cluster.
[azdata-BDC-Konfiguration](reference-azdata-bdc-config.md) | Konfigurations Befehle.
[azdata-BDC-Endpunkt](reference-azdata-bdc-endpoint.md) | Endpunkt Befehle.
[azdata-BDC-Status](reference-azdata-bdc-status.md) | Status Befehle.
[Debuggen von azdata BDC](reference-azdata-bdc-debug.md) | Debug-Befehle.
[azdata-BDC-Steuerelement](reference-azdata-bdc-control.md) | Steuern von Befehlen.
[azdata-BDC-Pool](reference-azdata-bdc-pool.md) | Pool Befehle.
[azdata-BDC-HDFS](reference-azdata-bdc-hdfs.md) | Das HDFS-Modul bietet Befehle für den Zugriff auf ein HDFS-Dateisystem.
[azdata BDC Spark](reference-azdata-bdc-spark.md) | Mithilfe der Spark-Befehle kann der Benutzer mit dem Spark-System interagieren, indem Sitzungen, Anweisungen und Batches erstellt und verwaltet werden.
## <a name="azdata-bdc-create"></a>azdata BDC Create
Erstellen Sie eine SQL Server Big Data-Cluster-Kube-Konfiguration ist auf Ihrem System zusammen mit den folgenden Umgebungsvariablen erforderlich [' CONTROLLER_USERNAME ', ' CONTROLLER_PASSWORD ', ' MSSQL_SA_PASSWORD ', ' KNOX_PASSWORD '].
```bash
azdata bdc create [--name -n] 
                  [--config-profile -c]  
                  [--accept-eula -a]  
                  [--node-label -l]  
                  [--force -f]
```
### <a name="examples"></a>Beispiele

Geführte BDC-Bereitstellung: Sie erhalten Eingabe Aufforderungen für erforderliche Werte.

```bash
azdata bdc create
```

BDC-Bereitstellung mit Argumenten.

```bash
azdata bdc create --accept-eula yes --config-profile aks-dev-test
```
BDC-Bereitstellung mit dem angegebenen Namen anstelle des Standard namens im Profil.
```bash
azdata bdc create --name <cluster_name> --accept-eula yes --config-profile aks-dev-test --force
```

BDC-Bereitstellung mit Argumenten: Es werden keine Eingabe Aufforderungen angegeben, da das Flag "--Force" verwendet wird.

```bash
azdata bdc create --accept-eula yes --config-profile aks-dev-test --force
```

### <a name="optional-parameters"></a>Optionale Parameter
#### `--name -n`
Big Data-Cluster Name, der für kubernetes-Namespaces verwendet wird.
#### `--config-profile -c`
Cluster Konfigurations Profil für Big Data, das zum Bereitstellen des Clusters verwendet wird: [' AKS-dev-Test ', ' kubeadm-dev-Test ', ' minikube-dev-Test ']
#### `--accept-eula -a`
Akzeptieren Sie die Lizenzbedingungen? [Ja/Nein]. Wenn Sie dieses arg nicht verwenden möchten, können Sie die Umgebungsvariable ACCEPT_EULA auf "yes" festlegen. Die Lizenzbedingungen für dieses Produkt können unter https://aka.ms/azdata-eula und https://go.microsoft.com/fwlink/?LinkId=2002534 angezeigt werden.
#### `--node-label -l`
Bezeichnung "Big Data-Cluster Knoten", mit der die Knoten bestimmt werden, in denen die Bereitstellung durch
#### `--force -f`
Create Create, der Benutzer wird nicht zur Eingabe von Werten aufgefordert, und alle Probleme werden als Teil von stderr ausgegeben.
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
## <a name="azdata-bdc-delete"></a>azdata BDC DELETE
Löschen Sie die SQL Server Big Data-Cluster-Kube-Konfiguration ist auf Ihrem System zusammen mit den folgenden Umgebungsvariablen erforderlich [' CONTROLLER_USERNAME ', ' CONTROLLER_PASSWORD '].
```bash
azdata bdc delete --name -n 
                  [--force -f]
```
### <a name="examples"></a>Beispiele
BDC-Löschung, bei der der Benutzername und das Kennwort des Controllers bereits in Ihrer Systemumgebung festgelegt sind
```bash
azdata bdc delete --name <cluster_name>
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--name -n`
Big Data-Cluster Name, der für den kubernetes-Namespace verwendet wird.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--force -f`
Erzwingt das Löschen Big Data Clusters.
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
