---
title: 'azdata bdc: Referenz'
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata bdc-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a4b619396c2dcdad589deff3f9fc6a03fe37c1d5
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73531689"
---
# <a name="azdata-bdc"></a>azdata bdc

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

Der folgende Artikel enthält Referenzinformationen zu `sql`-Befehlen im `azdata`-Tool. Weitere Informationen zu anderen `azdata`-Befehlen finden Sie in der [Referenz zu azdata](reference-azdata.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[azdata bdc create](#azdata-bdc-create) | Erstellen eines Big Data-Clusters.
[azdata bdc delete](#azdata-bdc-delete) | Löschen eines Big Data-Clusters.
[azdata bdc upgrade](#azdata-bdc-upgrade) | Aktualisieren Sie die Images, die in den Containern im SQL Server-Big Data-Cluster bereitgestellt werden.
[azdata bdc config](reference-azdata-bdc-config.md) | Konfigurationsbefehle
[azdata bdc endpoint](reference-azdata-bdc-endpoint.md) | Endpunktbefehle
[azdata bdc debug](reference-azdata-bdc-debug.md) | Befehle für Debuggen
[azdata bdc status](reference-azdata-bdc-status.md) | Statusbefehle für Big Data-Cluster
[azdata bdc control](reference-azdata-bdc-control.md) | Befehle für den Steuerungsdienst
[azdata bdc sql](reference-azdata-bdc-sql.md) | Befehle für den SQL-Dienst
[azdata bdc hdfs](reference-azdata-bdc-hdfs.md) | Befehle für den HDFS-Dienst
[azdata bdc spark](reference-azdata-bdc-spark.md) | Befehle für den Spark-Dienst
[azdata bdc gateway](reference-azdata-bdc-gateway.md) | Befehle für den Gatewaydienst
[azdata bdc app](reference-azdata-bdc-app.md) | Befehle für den App-Dienst
[azdata bdc spark](reference-azdata-bdc-spark.md) | Über die Spark-Befehle kann ein Benutzer mit dem Spark-System interagieren, indem Sitzungen, Anweisungen und Batches erstellt und verwaltet werden.
[azdata bdc hdfs](reference-azdata-bdc-hdfs.md) | Das HDFS-Modul stellt Befehle für Zugreifen auf ein HDFS-Dateisystem bereit.
## <a name="azdata-bdc-create"></a>azdata bdc create
Erstellt einen SQL Server-Big Data-Cluster – die Kubernetes-Konfiguration und die Umgebungsvariablen AZDATA_USERNAME und AZDATA_PASSWORD müssen auf Ihrem System vorhanden sein.
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
Das Konfigurationsprofil für den Big Data-Cluster, das zum Bereitstellen des Clusters verwendet wird: ['kubeadm-dev-test', 'kubeadm-prod', 'aks-dev-test', 'aks-dev-test-ha']
#### `--accept-eula -a`
Stimmen Sie den Lizenzbedingungen zu? [yes/no]. Wenn Sie dieses Argument nicht verwenden möchten, können Sie die Umgebungsvariable ACCEPT_EULA auf „yes“ festlegen. Die Lizenzbedingungen für azdata finden Sie unter https://aka.ms/eula-azdata-en. Die Lizenzbedingungen für Big Data-Cluster finden Sie für Enterprise unter https://go.microsoft.com/fwlink/?linkid=2104292, für Standard unter https://go.microsoft.com/fwlink/?linkid=2104294 und für Developer unter https://go.microsoft.com/fwlink/?linkid=2104079.
#### `--node-label -l`
Die Bezeichnung des Big Data-Clusterknotens. Hiermit wird bestimmt, auf welchem Knoten bereitgestellt werden soll.
#### `--force -f`
Das Erstellen wird erzwungen. Der Benutzer wird nicht zur Eingabe von Werten aufgefordert, und alle Probleme werden über stderr ausgegeben.
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
Ausführlichkeit der Protokollierung erhöhen. Verwenden Sie „--debug“ für vollständige Debugprotokolle.
## <a name="azdata-bdc-delete"></a>azdata bdc delete
Löscht den SQL Server-Big Data-Cluster – auf Ihrem System ist eine Kubernetes-Konfiguration erforderlich.
```bash
azdata bdc delete --name -n 
                  [--force -f]
```
### <a name="examples"></a>Beispiele
Löschung des Big Data-Clusters
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
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.
## <a name="azdata-bdc-upgrade"></a>azdata bdc upgrade
Aktualisieren Sie die Images, die in den Containern im SQL Server-Big Data-Cluster bereitgestellt werden. Die aktualisierten Images basieren auf dem übergebenen Docker-Image. Wenn die aktualisierten Images von einem anderen Docker-Imagerepository als die aktuell bereitgestellten Images stammen, ist auch der Parameter „repository“ erforderlich.
```bash
azdata bdc upgrade --name -n 
                   --tag -t  
                   [--repository -r]
```
### <a name="examples"></a>Beispiele
Big Data-Cluster-Upgrade auf das neue Imagetag „cu2“ aus demselben Repository
```bash
azdata bdc upgrade -t cu2
```
Big Data-Cluster-Upgrade auf neue Images mit dem Tag „cu2“ aus dem neuen Repository „foo/bar/baz“
```bash
azdata bdc upgrade -t cu2 -r foo/bar/baz
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--name -n`
Der Big Data-Clustername, der für kubernetes-Namespaces verwendet wird.
#### `--tag -t`
Das Zieltag des Docker-Images, auf das alle Container im Cluster aktualisiert werden sollen
### <a name="optional-parameters"></a>Optionale Parameter
#### `--repository -r`
Das Docker-Repository, aus dem alle Container im Cluster ihre Images abrufen sollen
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
