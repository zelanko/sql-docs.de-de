---
title: Herstellen einer Verbindung mit einer SQL Server-Always On-Verfügbarkeitsgruppe in einem Kubernetes-Cluster
description: In diesem Artikel ist erläutert, wie eine Verbindung mit einer Always On-Verfügbarkeitsgruppe hergestellt wird.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f05bc51f587723414d3b0a4090fe2b27ad5fb837
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "67952603"
---
# <a name="connect-to-a-sql-server-always-on-availability-group-on-kubernetes"></a>Herstellen einer Verbindung mit einer SQL Server-Always On-Verfügbarkeitsgruppe in Kubernetes

Um Verbindungen mit SQL Server-Instanzen in Containern in einem Kubernetes-Cluster herzustellen, erstellen Sie einen [LoadBalancer-Dienst](https://kubernetes.io/docs/concepts/services-networking/service/#loadbalancer) (Lastenausgleichsdienst). Der Lastenausgleich ist ein Endpunkt. Er enthält eine IP-Adresse und leitet Anforderungen bezüglich der IP-Adresse an den Pod weiter, in dem die SQL Server-Instanz ausgeführt wird.

Um eine Verbindung mit einem Verfügbarkeitsgruppenreplikat herzustellen, erstellen Sie einen Dienst für verschiedene Replikattypen. Beispiele für Dienste für verschiedene Typen von Replikaten finden Sie in [sql-server-samples/ag-services.yaml](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files).

* `ag1-primary` verweist auf das primäre Replikat.
* `ag1-secondary` verweist auf das sekundäre Replikat.

Gibt es mehrere sekundäre Replikate, leitet Kubernetes die Verbindung mit den verschiedenen Replikaten auf Round-Robin-Art weiter.

## <a name="create-a-load-balancer-service"></a>Erstellen eines LoadBalancer-Diensts

Um je einen LoadBalancer-Dienst für das primäre und das sekundäre Replikat zu erstellen, kopieren Sie [`ag1-services.yaml`](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/ag-services.yaml) aus [sql-server-samples](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-file), und aktualisieren Sie die Datei entsprechend Ihrer Verfügbarkeitsgruppe.

Der folgende Befehl wendet die Konfiguration aus der `.yaml`-Datei auf den Cluster an:

```kubectl
kubectl apply -f ag1-services.yaml --namespace ag1
```

## <a name="get-the-ip-address-for-your-load-balancer-service"></a>Abrufen der IP-Adresse für den LoadBalancer-Dienst

Um die IP-Adresse für Ihren Lastenausgleichsdienst (LoadBalancer-Dienst) abzurufen, führen Sie folgenden Befehl aus:

```kubectl
kubectl get services
```

Ermitteln Sie die IP-Adresse des Diensts, mit dem Sie eine Verbindung herstellen möchten.

## <a name="connect-to-primary-replica"></a>Herstellen einer Verbindung mit dem primären Replikat

Um eine Verbindung mit dem primären Replikat mit SQL-Authentifizierung herzustellen, verwenden Sie das `sa`-Konto, den Wert für `sapassword` aus dem von Ihnen erstellten Geheimnis und diese IP-Adresse.

Beispiel:

```cmd
sqlcmd -S <0.0.0.0> -U sa -P "<MyC0m9l&xP@ssw0rd>"
```

## <a name="next-steps"></a>Nächste Schritte

[Verwalten einer SQL Server-Always On-Verfügbarkeitsgruppe in Kubernetes](sql-server-linux-kubernetes-manage.md)

[SQL Server-Verfügbarkeitsgruppe in einem Kubernetes-Cluster](sql-server-ag-kubernetes.md)
