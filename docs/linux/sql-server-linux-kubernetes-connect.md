---
title: Verbinden Sie mit SQL Server AlwaysOn-Verfügbarkeitsgruppe in Kubernetes-cluster
description: In diesem Artikel wird erläutert, wie die Verbindung zu einer AlwaysOn-Verfügbarkeitsgruppe
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6352fc7be129f485175b1144d14aa380b2d99e1f
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51671999"
---
# <a name="connect-to-a-sql-server-always-on-availability-group-on-kubernetes"></a>Verbinden Sie mit einer SQLServer Always On-Verfügbarkeitsgruppe auf Kubernetes

Erstellen Sie zum Verbinden mit SQL Server-Instanzen in Containern in einem Kubernetes-Cluster eine [Lastenausgleichsmodul-Dienst](https://kubernetes.io/docs/concepts/services-networking/service/#loadbalancer). Der Load Balancer ist ein Endpunkt an. Es enthält eine IP-Adresse und leitet Anforderungen für die IP-Adresse in den Pod, der SQL Server-Instanz ausgeführt wird.

Erstellen Sie einen Dienst für die anderen Replikat-Typen, zum Verbinden mit einem Replikat der verfügbarkeitsgruppe. Sehen Sie Beispiele für Dienste für verschiedene Arten von Replikaten in [Sql-Server-Beispiele/ag-services.yaml](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files).

* `ag1-primary` verweist auf das primäre Replikat.
* `ag1-secondary` verweist auf ein sekundäres Replikat.

Wenn mehr als leitet ein sekundäres Replikat, Kubernetes die Verbindung mit den anderen Replikaten in einer Round-Robin-Basis.

## <a name="create-a-load-balancer-service"></a>Erstellen Sie einen Load Balancer-Dienst

Um Load Balancer-Dienste für die primäre und die Replikate zu erstellen, kopieren [ `ag1-services.yaml` ](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/ag-services.yaml) aus [Sql Server Samples](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-file) und aktualisieren Sie es für Ihre verfügbarkeitsgruppe.

Der folgende Befehl wendet die Konfiguration der `.yaml` Datei Cluster:

```kubectl
kubectl apply -f ag1-services.yaml --namespace ag1
```

## <a name="get-the-ip-address-for-your-load-balancer-service"></a>Rufen Sie die IP-Adresse für den Load Balancer-Dienst

Rufen Sie die IP-Adresse des Load Balancers für den Load Balancer-Dienst ausführen.

```kubectl
kubectl get services
```

Identifizieren Sie die IP-Adresse des Diensts, die Sie herstellen möchten.

## <a name="connect-to-primary-replica"></a>Verbinden mit primärem Replikat

Verwenden Sie zum Verbinden mit dem primären Replikat mit der SQL-Authentifizierung die `sa` -Konto, das den Wert für `sapassword` aus den geheimen Schlüssel, die Sie erstellt haben, und diese IP-Adresse.

Zum Beispiel:

```cmd
sqlcmd -S <0.0.0.0> -U sa -P "<MyC0m9l&xP@ssw0rd>"
```

## <a name="next-steps"></a>Nächste Schritte

[Verwalten von SQL Server-verfügbarkeitsgruppe in Kubernetes-cluster](sql-server-linux-kubernetes-manage.md)

[SQL Server-verfügbarkeitsgruppe in Kubernetes-cluster](sql-server-ag-kubernetes.md)
