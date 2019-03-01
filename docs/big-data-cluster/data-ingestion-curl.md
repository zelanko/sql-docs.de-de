---
title: Verwenden Sie Curl zum Laden von Daten in HDFS in SQL Server-2019 big Data-Clustern | Microsoft-Dokumentation
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 1a7c7691ec20f459f39a39270e9a78fc9d8ad96f
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/01/2019
ms.locfileid: "57017546"
---
# <a name="use-curl-to-load-data-into-hdfs-on-sql-server-2019-big-data-clusters"></a>Laden von Daten in HDFS in SQL Server-2019 big Data-Clustern mithilfe von curl

In diesem Artikel wird erläutert, wie Sie mit **curl** zum Laden von Daten in HDFS in SQL Server-2019 big Data-Clustern (Vorschau).

## <a name="obtain-the-service-external-ip"></a>Dienst für die externe IP-Adresse abrufen

WebHDFS wird gestartet, wenn die Bereitstellung abgeschlossen ist, und der Zugriff von Knox durchläuft. Die Knox-Endpunkt verfügbar gemacht wird, über einen Kubernetes-Dienst wird aufgerufen, **endpunktsicherheit**.  Um die erforderlichen WebHDFS-URL zum Hoch-und Herunterladen von Dateien zu erstellen, müssen Sie die **endpunktsicherheit** -externe IP-Adresse und den Namen Ihres Clusters. Sie erhalten die **endpunktsicherheit** service externe IP-Adresse mithilfe des folgenden Befehls:

```bash
kubectl get service endpoint-security -n <cluster name> -o json | jq -r .status.loadBalancer.ingress[0].ip
```

> [!NOTE]
> Die `<cluster name>` ist hier der Name des Clusters, den Sie angegeben, bei der Ausführung `mssqlctl cluster create --name <cluster name>`.

## <a name="construct-the-url-to-access-webhdfs"></a>Erstellen Sie die URL für den Zugriff auf WebHDFS

Sie können nun die URL, um die WebHDFS zugreifen, wie folgt erstellen:

`https://<endpoint-security service external IP address>:30443/gateway/default/webhdfs/v1/`

Zum Beispiel:

`https://13.66.190.205:30443/gateway/default/webhdfs/v1/`

## <a name="list-a-file"></a>Auflisten einer Datei

Um die Datei unter **Hdfs: / / / Airlinedata**, verwenden Sie den folgenden Curl-Befehl:

```bash
curl -i -k -u root:root-password -X GET 'https://<endpoint-security IP external address>:30443/gateway/default/webhdfs/v1/airlinedata/?op=liststatus'
```

## <a name="put-a-local-file-into-hdfs"></a>Speichern Sie eine lokale Datei in HDFS

Stellen Sie eine neue Datei **test.csv** aus lokalen Verzeichnis Airlinedata-Verzeichnis verwenden Sie den folgenden Curl-Befehl (der **Content-Type** -Parameter ist erforderlich):

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<endpoint-security IP external address>:30443/gateway/default/webhdfs/v1/airlinedata/test.csv?op=create' -H 'Content-Type: application/octet-stream' -T 'test.csv'
```

## <a name="create-a-directory"></a>Erstellen Sie ein Verzeichnis

Zum Erstellen eines Verzeichnisses **testen** unter `hdfs:///`, verwenden Sie den folgenden Befehl:

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<endpoint-security IP external address>:30443/gateway/default/webhdfs/v1/test?op=MKDIRS'
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu SQL Server-big Data-Cluster, finden Sie unter [neuerungen von SQL Server-big Data-Cluster?](big-data-cluster-overview.md).
