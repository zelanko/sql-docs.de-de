---
title: Verwenden von curl, um Daten in HDFS zu laden | Microsoft-Dokumentation
titleSuffix: SQL Server big data clusters
description: Verwenden Sie curl, um Daten in HDFS in Big Data-Clustern für SQL Server 2019 zu laden.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/22/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ae893bb1e291b244b5101ccfb2ed66bcf765f049
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91866844"
---
# <a name="use-curl-to-load-data-into-hdfs-on-big-data-clusters-2019"></a>Verwenden von curl, um Daten in HDFS in [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] zu laden

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

In diesem Artikel wird erläutert, wie Sie **curl** verwenden, um Daten in HDFS in [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] zu laden.

## <a name="prerequisites"></a><a id="prereqs"></a> Voraussetzungen

- [Laden von Beispieldaten in einen Big Data-Cluster von SQL Server](tutorial-load-sample-data.md)

## <a name="obtain-the-service-external-ip"></a>Abrufen der externen IP des Diensts

WebHDFS wird gestartet, wenn die Bereitstellung abgeschlossen ist, und dessen Zugriff erfolgt über Knox. Der Knox-Endpunkt wird über einen Kubernetes-Dienst namens **gateway-svc-external** verfügbar gemacht.  Um die WebHDFS-URL zu erstellen, die zum Hochladen/Herunterladen von Dateien erforderlich ist, benötigen Sie die externe IP-Adresse des **gateway-svc-external**-Diensts und den Namen Ihres Big Data-Clusters. Sie können die externe IP-Adresse des **gateway-svc-external**-Diensts abrufen, indem Sie den folgenden Befehl ausführen:

```terminal
kubectl get service gateway-svc-external -n <big data cluster name> -o json | jq -r .status.loadBalancer.ingress[0].ip
```

> [!NOTE]
> Der `<big data cluster name>` hier ist der Name des Clusters, den Sie in der Bereitstellungskonfigurationsdatei angegeben haben. Der Standardname ist `mssql-cluster`.

## <a name="construct-the-url-to-access-webhdfs"></a>Erstellen der URL für den Zugriff auf WebHDFS

Nun können Sie die URL für den Zugriff auf das WebHDFS wie folgt erstellen:

`https://<gateway-svc-external service external IP address>:30443/gateway/default/webhdfs/v1/`

Beispiel:

`https://13.66.190.205:30443/gateway/default/webhdfs/v1/`

## <a name="authentication-with-active-directory"></a>Authentifizierung mit Active Directory

Verwenden Sie für Bereitstellungen mit Active Directory den Authentifizierungsparameter mit `curl` mit Aushandlungsauthentifizierung. 

Führen Sie diesen Befehl aus, um `curl` mit Active Directory-Authentifizierung zu verwenden:

```
kinit <username>
```

Der Befehl generiert ein Kerberos-Token für die Verwendung durch `curl`. Die in den nächsten Abschnitten vorgestellten Befehle geben den `--anyauth`-Parameter für `curl` an. Für URLs, die Aushandlungsauthentifizierung erfordern, erkennt `curl` automatisch das generierte Kerberos-Token und verwendet es anstelle von Benutzername und Kennwort für die Authentifizierung bei der URL.

## <a name="list-a-file"></a>Auflisten einer Datei

Um die Datei unter **hdfs:///product_review_data** aufzulisten, verwenden Sie den folgenden curl-Befehl:

```terminal
curl -i -k --anyauth -u root:<AZDATA_PASSWORD> -X GET 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/product_review_data/?op=liststatus'
```

[!INCLUDE [big-data-cluster-root-user](../includes/big-data-cluster-root-user.md)]

Verwenden Sie für Endpunkte ohne Stamm den folgenden curl-Befehl:

```terminal
curl -i -k --anyauth -u <AZDATA_USERNAME>:<AZDATA_PASSWORD> -X GET 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/product_review_data/?op=liststatus'
```

## <a name="put-a-local-file-into-hdfs"></a>Ablegen einer lokalen Datei in HDFS

Um die neue Datei **test.csv** aus dem lokalen Verzeichnis im Verzeichnis „product_review_data“ abzulegen, verwenden Sie den folgenden curl-Befehl (der **Content-Type**-Parameter ist erforderlich):

```terminal
curl -i -L -k --anyauth -u root:<AZDATA_PASSWORD> -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/product_review_data/test.csv?op=create' -H 'Content-Type: application/octet-stream' -T 'test.csv'
```

[!INCLUDE [big-data-cluster-root-user](../includes/big-data-cluster-root-user.md)]

Verwenden Sie für Endpunkte ohne Stamm den folgenden curl-Befehl:

```terminal
curl -i -L -k --anyauth -u <AZDATA_USERNAME>:<AZDATA_PASSWORD> -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/product_review_data/test.csv?op=create' -H 'Content-Type: application/octet-stream' -T 'test.csv'
```

## <a name="create-a-directory"></a>Erstellen eines Verzeichnisses

Um das Verzeichnis **test** unter `hdfs:///` zu erstellen, verwenden Sie den folgenden Befehl:

```terminal
curl -i -L -k --anyauth -u root:<AZDATA_PASSWORD> -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/test?op=MKDIRS'
```

[!INCLUDE [big-data-cluster-root-user](../includes/big-data-cluster-root-user.md)]
Verwenden Sie für Endpunkte ohne Stamm den folgenden curl-Befehl:

```terminal
curl -i -L -k --anyauth -u <AZDATA_USERNAME>:<AZDATA_PASSWORD> -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/test?op=MKDIRS'
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen über Big Data-Cluster für SQL Serverfinden Sie unter [Was sind SQL Server-Big Data-Cluster?](big-data-cluster-overview.md).
