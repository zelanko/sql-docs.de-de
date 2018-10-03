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
ms.openlocfilehash: 6092f15fe64c96ed004d352408ae6cdac034def9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47852158"
---
# <a name="connect-to-a-sql-server-always-on-availability-group-on-kubernetes"></a>Verbinden Sie mit einer SQLServer Always On-Verfügbarkeitsgruppe auf Kubernetes

Erstellen Sie zum Verbinden mit SQL Server-Instanzen in Containern in einem Kubernetes-Cluster eine [Lastenausgleichsmodul-Dienst](http://kubernetes.io/docs/concepts/services-networking/service/#loadbalancer). Anforderungen für die IP-Adresse in den Pod, der SQL Server-Instanz ausgeführt wird, leitet der Load Balancer.

Erstellen Sie einen Dienst für die anderen Replikat-Typen, zum Verbinden mit einem Replikat der verfügbarkeitsgruppe. Sehen Sie Beispiele für Dienste für verschiedene Arten von Replikaten in [Sql Server Samples](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/ag-services.yaml).

* `ag1-primary` verweist auf das primäre Replikat.
* `ag1-secondary-sync` verweist auf die synchronen sekundären Replikat.
* `ag1-secondary-async` verweist auf ein asynchrones sekundäres Replikat.

Wenn mehr als ein sekundäres Replikat des gleichen Typs vorhanden ist, leitet Kubernetes die Verbindung mit den anderen Replikaten in einer Round-Robin-Basis.

## <a name="create-a-load-balancer-service"></a>Erstellen Sie einen Load Balancer-Dienst

Kopieren Sie zum Erstellen eines Load Balancer-Diensts für das primäre Replikat `ag1-primary.yaml` aus [Sql Server Samples]()und aktualisieren Sie es für Ihre verfügbarkeitsgruppe.

Der folgende Befehl wendet die yaml-Datei in Ihrem Cluster:

```kubectl
kubectl apply -f ag1-primary.yaml
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
