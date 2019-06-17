---
title: Verwenden Sie Curl zum Laden von Daten in HDFS | Microsoft-Dokumentation
titleSuffix: SQL Server big data clusters
description: Verwenden Sie Curl, um Daten in HDFS in SQL Server-2019 big Data-Clustern zu laden.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: d1e8da7430048381a320936abef35cdd64bad134
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66800708"
---
# <a name="use-curl-to-load-data-into-hdfs-on-sql-server-big-data-clusters"></a>Laden von Daten in HDFS in SQL Server-big Data-Clustern mithilfe von curl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird erläutert, wie Sie mit **curl** zum Laden von Daten in HDFS in SQL Server-2019 big Data-Clustern (Vorschau).

## <a name="obtain-the-service-external-ip"></a>Dienst für die externe IP-Adresse abrufen

WebHDFS wird gestartet, wenn die Bereitstellung abgeschlossen ist, und der Zugriff von Knox durchläuft. Die Knox-Endpunkt verfügbar gemacht wird, über einen Kubernetes-Dienst wird aufgerufen, **Gateway-svc-External**.  Um die erforderlichen WebHDFS-URL zum Hoch-und Herunterladen von Dateien zu erstellen, müssen Sie die **Gateway-svc-External** -externe IP-Adresse und den Namen des Ihrer big Data-Cluster. Sie erhalten die **Gateway-svc-External** service externe IP-Adresse mithilfe des folgenden Befehls:

```bash
kubectl get service gateway-svc-external -n <big data cluster name> -o json | jq -r .status.loadBalancer.ingress[0].ip
```

> [!NOTE]
> Die `<big data cluster name>` ist hier der Name des Clusters, den Sie in der Konfigurationsdatei der Bereitstellung angegeben. Der Standardname lautet `mssql-cluster`.

## <a name="construct-the-url-to-access-webhdfs"></a>Erstellen Sie die URL für den Zugriff auf WebHDFS

Sie können nun die URL, um die WebHDFS zugreifen, wie folgt erstellen:

`https://<gateway-svc-external service external IP address>:30443/gateway/default/webhdfs/v1/`

Zum Beispiel:

`https://13.66.190.205:30443/gateway/default/webhdfs/v1/`

## <a name="list-a-file"></a>Auflisten einer Datei

Um die Datei unter **Hdfs: / / / Airlinedata**, verwenden Sie den folgenden Curl-Befehl:

```bash
curl -i -k -u root:root-password -X GET 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/airlinedata/?op=liststatus'
```

## <a name="put-a-local-file-into-hdfs"></a>Speichern Sie eine lokale Datei in HDFS

Stellen Sie eine neue Datei **test.csv** aus lokalen Verzeichnis Airlinedata-Verzeichnis verwenden Sie den folgenden Curl-Befehl (der **Content-Type** -Parameter ist erforderlich):

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/airlinedata/test.csv?op=create' -H 'Content-Type: application/octet-stream' -T 'test.csv'
```

## <a name="create-a-directory"></a>Erstellen Sie ein Verzeichnis

Zum Erstellen eines Verzeichnisses **testen** unter `hdfs:///`, verwenden Sie den folgenden Befehl:

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/test?op=MKDIRS'
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu SQL Server-big Data-Cluster, finden Sie unter [neuerungen von SQL Server-big Data-Cluster?](big-data-cluster-overview.md).
