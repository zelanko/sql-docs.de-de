---
title: 'azdata bdc: Referenz'
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata bdc-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 488394cbf4b52a952ffc46ab2ec6c9a273466bd5
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68426040"
---
# <a name="azdata-bdc"></a>azdata bdc

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel enthält Referenzinformationen zu **bdc**-Befehlen im **azdata**-Tool. Weitere Informationen zu anderen **azdata**-Befehlen finden Sie unter [azdata](reference-azdata.md).

## <a name="commands"></a>Befehle

|     |     |
| --- | --- |
[azdata bdc create](#azdata-bdc-create) | Erstellen eines Big Data-Clusters.
[azdata bdc delete](#azdata-bdc-delete) | Löschen eines Big Data-Clusters.
[azdata bdc config](reference-azdata-bdc-config.md) | Konfigurationsbefehle
[azdata bdc endpoint](reference-azdata-bdc-endpoint.md) | Endpunktbefehle
[azdata bdc status](reference-azdata-bdc-status.md) | Statusbefehle
[azdata bdc debug](reference-azdata-bdc-debug.md) | Befehle für Debuggen
[azdata bdc control](reference-azdata-bdc-control.md) | Steuerungsbefehle
[azdata bdc pool](reference-azdata-bdc-pool.md) | Poolbefehle
[azdata bdc hdfs](reference-azdata-bdc-hdfs.md) | Das HDFS-Modul stellt Befehle für Zugreifen auf ein HDFS-Dateisystem bereit.
[azdata bdc spark](reference-azdata-bdc-spark.md) | Über die Spark-Befehle kann ein Benutzer mit dem Spark-System interagieren, indem Sitzungen, Anweisungen und Batches erstellt und verwaltet werden.
## <a name="azdata-bdc-create"></a>azdata bdc create
Erstellen eines Big Data-Clusters für SQL Server. Auf Ihrem System ist eine Kube-Konfiguration zusammen mit den folgenden Umgebungsvariablen erforderlich: [CONTROLLER_USERNAME, CONTROLLER_PASSWORD, MSSQL_SA_PASSWORD, KNOX_PASSWORD].
```bash
azdata bdc create [--name -n] 
                  [--config-profile -c]  
                  [--accept-eula -a]  
                  [--node-label -l]  
                  [--force -f]
```
### <a name="examples"></a>Beispiele

Geführtes Ausführen einer BDC-Bereitstellung: Sie erhalten Eingabeaufforderungen für die erforderlichen Werte.

```bash
azdata bdc create
```

BDC-Bereitstellung mit Argumenten.

```bash
azdata bdc create --accept-eula yes --config-profile aks-dev-test
```
BDC-Bereitstellung mit angegebenem Namen anstelle des Standardnamens im Profil.
```bash
azdata bdc create --name <cluster_name> --accept-eula yes --config-profile aks-dev-test --force
```

BDC-Bereitstellung mit Argumenten. Es werden keine Eingabeaufforderungen angezeigt, weil das Flag „--force“ verwendet wird.

```bash
azdata bdc create --accept-eula yes --config-profile aks-dev-test --force
```

### <a name="optional-parameters"></a>Optionale Parameter
#### `--name -n`
Der Big Data-Clustername, der für kubernetes-Namespaces verwendet wird.
#### `--config-profile -c`
Das Konfigurationsprofil für den Big Data-Cluster, das zum Bereitstellen des Clusters verwendet wird: ['aks-dev-test', 'kubeadm-dev-test', 'minikube-dev-test']
#### `--accept-eula -a`
Stimmen Sie den Lizenzbedingungen zu? [yes/no]. Wenn Sie dieses Argument nicht verwenden möchten, können Sie die Umgebungsvariable ACCEPT_EULA auf „yes“ festlegen. Die Lizenzbedingungen für dieses Produkt finden Sie unter https://aka.ms/azdata-eula und https://go.microsoft.com/fwlink/?LinkId=2002534.
#### `--node-label -l`
Die Bezeichnung des Big Data-Clusterknotens. Hiermit wird bestimmt, auf welchem Knoten bereitgestellt werden soll.
#### `--force -f`
Das Erstellen wird erzwungen. Der Benutzer wird nicht zur Eingabe von Werten aufgefordert, und alle Probleme werden über stderr ausgegeben.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöhen Sie die Ausführlichkeit der Protokollierung, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Erhöhen Sie die Ausführlichkeit der Protokollierung. Verwenden Sie „--debug“ für vollständige Debugprotokolle.
## <a name="azdata-bdc-delete"></a>azdata bdc delete
Löschen eines Big Data-Clusters für SQL Server. Auf Ihrem System ist eine Kube-Konfiguration zusammen mit den folgenden Umgebungsvariablen erforderlich: [CONTROLLER_USERNAME, CONTROLLER_PASSWORD].
```bash
azdata bdc delete --name -n 
                  [--force -f]
```
### <a name="examples"></a>Beispiele
BDC-Löschung, wobei der Benutzername und das Kennwort für den Controller bereits in Ihrer Systemumgebung festgelegt sind.
```bash
azdata bdc delete --name <cluster_name>
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--name -n`
Der Big Data-Clustername, der für den kubernetes-Namespace verwendet wird.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--force -f`
Erzwingen Sie das Löschen eines Big Data-Clusters.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöhen Sie die Ausführlichkeit der Protokollierung, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Erhöhen Sie die Ausführlichkeit der Protokollierung. Verwenden Sie „--debug“ für vollständige Debugprotokolle.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu anderen **azdata**-Befehlen finden Sie unter [azdata](reference-azdata.md). Weitere Informationen zum Installieren des Tools **azdata** finden Sie unter [Install azdata to manage SQL Server 2019 big data clusters (Installieren von azdata zum Verwalten von Big Data-Clustern von SQL Server 2019)](deploy-install-azdata.md).
