---
title: 'azdata bdc: Referenz'
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata bdc-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 408b3c2d55d5e2515a2df979cd54b380a0d54704
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70155141"
---
# <a name="azdata-bdc"></a>azdata bdc

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

Dieser Artikel ist ein Referenz Artikel für **azdata**. 

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[azdata bdc create](#azdata-bdc-create) | Erstellen eines Big Data-Clusters.
[azdata bdc delete](#azdata-bdc-delete) | Löschen eines Big Data-Clusters.
[azdata bdc config](reference-azdata-bdc-config.md) | Konfigurationsbefehle
[azdata bdc endpoint](reference-azdata-bdc-endpoint.md) | Endpunktbefehle
[azdata bdc debug](reference-azdata-bdc-debug.md) | Befehle für Debuggen
[azdata bdc status](reference-azdata-bdc-status.md) | BDC-Status Befehle.
[azdata bdc control](reference-azdata-bdc-control.md) | Steuern von Dienst Befehlen.
[azdata BDC SQL](reference-azdata-bdc-sql.md) | SQL-Dienst Befehle.
[azdata bdc hdfs](reference-azdata-bdc-hdfs.md) | HDFS-Dienst Befehle.
[azdata bdc spark](reference-azdata-bdc-spark.md) | Spark-Dienst Befehle.
[azdata-BDC-Gateway](reference-azdata-bdc-gateway.md) | Befehle des Gatewaydiensts.
[azdata BDC-App](reference-azdata-bdc-app.md) | App Service-Befehle.
[azdata bdc hdfs](reference-azdata-bdc-hdfs.md) | Das HDFS-Modul stellt Befehle für Zugreifen auf ein HDFS-Dateisystem bereit.
[azdata bdc spark](reference-azdata-bdc-spark.md) | Über die Spark-Befehle kann ein Benutzer mit dem Spark-System interagieren, indem Sitzungen, Anweisungen und Batches erstellt und verwaltet werden.
## <a name="azdata-bdc-create"></a>azdata bdc create
Erstellen eines SQL Server Big Data-Clusters Kubernetes die Konfiguration ist auf Ihrem System zusammen mit den folgenden Umgebungsvariablen erforderlich [' CONTROLLER_USERNAME ', ' CONTROLLER_PASSWORD ', ' MSSQL_SA_PASSWORD ', ' KNOX_PASSWORD '].
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
Cluster Konfigurations Profil für Big Data, das zum Bereitstellen des Clusters verwendet wird: [' AKS-dev-Test ', ' kubeadm-Prod ', ' minikube-dev-Test ', ' kubeadm-dev-Test ']
#### `--accept-eula -a`
Stimmen Sie den Lizenzbedingungen zu? [yes/no]. Wenn Sie dieses Argument nicht verwenden möchten, können Sie die Umgebungsvariable ACCEPT_EULA auf „yes“ festlegen. Die Lizenzbedingungen für dieses Produkt finden Sie unter https://aka.ms/azdata-eula und https://go.microsoft.com/fwlink/?LinkId=2002534.
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
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. Verwenden Sie „--debug“ für vollständige Debugprotokolle.
## <a name="azdata-bdc-delete"></a>azdata bdc delete
Löschen Sie die SQL Server Big Data-Cluster Kubernetes die Konfiguration ist auf Ihrem System erforderlich.
```bash
azdata bdc delete --name -n 
                  [--force -f]
```
### <a name="examples"></a>Beispiele
BDC löschen.
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
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.

## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen zu anderen **azdata**-Befehlen finden Sie unter [azdata](reference-azdata.md). 

- Weitere Informationen zum Installieren des Tools **azdata** finden Sie unter [Install azdata to manage SQL Server 2019 big data clusters (Installieren von azdata zum Verwalten von Big-Data-Clustern von SQL Server 2019)](deploy-install-azdata.md).
