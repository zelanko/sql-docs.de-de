---
title: Verwenden von curl, um Daten in HDFS zu laden | Microsoft-Dokumentation
titleSuffix: SQL Server big data clusters
description: Verwenden Sie curl, um Daten auf [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]in HDFS zu laden.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c65ce7fb6752240f0dd23a6dab195539146e7933
ms.sourcegitcommit: 4fb6bc7c81a692a2df706df063d36afad42816af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2019
ms.locfileid: "73049880"
---
# <a name="use-curl-to-load-data-into-hdfs-on-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Verwenden von curl zum Laden von Daten in HDFS auf [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird erläutert, wie Sie **curl** zum Laden von Daten in HDFS auf [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (Vorschau) verwenden.

## <a id="prereqs"></a> Prerequisites

- [Laden von Beispieldaten in Ihren Big Data-Cluster](tutorial-load-sample-data.md)

## <a name="obtain-the-service-external-ip"></a>Abrufen der externen IP des Diensts

WebHDFS wird gestartet, wenn die Bereitstellung abgeschlossen ist, und dessen Zugriff erfolgt über Knox. Der Knox-Endpunkt wird über einen Kubernetes-Dienst namens **gateway-svc-external** verfügbar gemacht.  Um die WebHDFS-URL zu erstellen, die zum Hochladen/Herunterladen von Dateien erforderlich ist, benötigen Sie die externe IP-Adresse des **gateway-svc-external**-Diensts und den Namen Ihres Big Data-Clusters. Sie können die externe IP-Adresse des **gateway-svc-external**-Diensts abrufen, indem Sie den folgenden Befehl ausführen:

```bash
kubectl get service gateway-svc-external -n <big data cluster name> -o json | jq -r .status.loadBalancer.ingress[0].ip
```

> [!NOTE]
> Der `<big data cluster name>` hier ist der Name des Clusters, den Sie in der Bereitstellungskonfigurationsdatei angegeben haben. Der Standardname ist `mssql-cluster`.

## <a name="construct-the-url-to-access-webhdfs"></a>Erstellen der URL für den Zugriff auf WebHDFS

Nun können Sie die URL für den Zugriff auf das WebHDFS wie folgt erstellen:

`https://<gateway-svc-external service external IP address>:30443/gateway/default/webhdfs/v1/`

Beispiel:

`https://13.66.190.205:30443/gateway/default/webhdfs/v1/`

## <a name="list-a-file"></a>Auflisten einer Datei

Verwenden Sie den folgenden curl-Befehl, um die Datei unter **HDFS:///product_review_data**aufzulisten:

```bash
curl -i -k -u root:root-password -X GET 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/product_review_data/?op=liststatus'
```

## <a name="put-a-local-file-into-hdfs"></a>Ablegen einer lokalen Datei in HDFS

Um eine neue Datei " **Test. CSV** " aus dem lokalen Verzeichnis in das Verzeichnis "product_review_data" einzufügen, verwenden Sie den folgenden curl-Befehl (der **Content-Type-** Parameter ist erforderlich):

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/product_review_data/test.csv?op=create' -H 'Content-Type: application/octet-stream' -T 'test.csv'
```

## <a name="create-a-directory"></a>Erstellen eines Verzeichnisses

Um das Verzeichnis **test** unter `hdfs:///` zu erstellen, verwenden Sie den folgenden Befehl:

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/test?op=MKDIRS'
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen über Big Data-Cluster für SQL Serverfinden Sie unter [Was sind SQL Server-Big Data-Cluster?](big-data-cluster-overview.md).
