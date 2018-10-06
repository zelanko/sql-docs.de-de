---
title: Verwalten einer SQL Server Always On Availability Group Kubernetes
description: In diesem Artikel wird erläutert, wie Sie eine SQL Server AlwaysOn-Verfügbarkeitsgruppe in Kubernetes zu verwalten.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 7f713ed7dd5d0260df6441698371b33f94813d7e
ms.sourcegitcommit: 4832ae7557a142f361fbf0a4e2d85945dbf8fff6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2018
ms.locfileid: "48251977"
---
# <a name="manage-sql-server-always-on-availability-group-kubernetes"></a>Verwalten von SQLServer Always On-Verfügbarkeitsgruppe Kubernetes

Verwalten einer AlwaysOn-Verfügbarkeitsgruppe in Kubernetes, erstellen Sie ein Manifest, und klicken Sie auf den Cluster anwenden. Das Manifest ist eine `.yaml` Datei.  

In die Beispielen in diesem Artikel gelten für alle Kubernetes-Cluster. Die Szenarien in diesen Beispielen werden für einen Cluster in Azure Kubernetes Service angewendet.

Sehen Sie ein Beispiel für die vollständige Bereitstellung im [Always On-Verfügbarkeitsgruppen für SQL Server-Containern](sql-server-ag-kubernetes.md).

## <a name="fail-over---sql-server-availability-group-on-kubernetes"></a>Failover – SQL Server-verfügbarkeitsgruppe auf Kubernetes

Verwenden Sie einen Auftrag für ein Failover von einem primären Replikat der verfügbarkeitsgruppe zu einem anderen Knoten im Kubernetes. Diesem Artikel werden die Umgebungsvariablen für diesen Auftrag identifiziert.

Die folgende Manifestdatei beschreibt einen Auftrag zum Ausführen des manuellen Failovers einer verfügbarkeitsgruppe. 

Kopieren Sie den Inhalt des Beispiels in eine neue Datei namens `failover.yaml`.

[Failover.yaml](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-deployment-script/templates/failover.yaml)

Verwenden Sie zum Bereitstellen des Auftrags `Kubectl`.

```azurecli
kubectl apply -f failover.yaml
```

Nachdem Sie den manifest-Datei anwenden, führt Kubernetes den Auftrag an. Der Auftrag wird den Supervisor einen neuen übergeordneten Knoten und das primäre Replikat mit der SQL Server-Instanz, von der übergeordneten Instanz verschiebt.

Nachdem der Auftrag ausgeführt wird, löschen Sie sie. Das Auftragsobjekt in Kubernetes bleibt nach dem Abschluss, damit Sie deren Status anzeigen können. Sie müssen die alten Aufträge manuell zu löschen, nach deren Status zu beachten. Den Auftrag gelöscht wird, auch die Kubernetes-Protokolle. Wenn Sie den Auftrag nicht löschen, fehl, wenn Sie den Namen des Auftrags und die Pod-Auswahl ändern, zukünftige Failover-Aufträgen auf. Weitere Informationen finden Sie unter [Ausführen von Aufträgen – bis zum Abschluss](https://kubernetes.io/docs/concepts/workloads/controllers/jobs-run-to-completion/).

## <a name="rotate-credentials"></a>Rotieren von Anmeldeinformationen

Drehen Sie die Anmeldeinformationen, um die Sicherheitszuordnung und der Hauptschlüssel zu aktualisieren.

Kopieren der [drehen creds.yaml](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-deployment-script) lokal verwenden `kubectl` , die sie in Ihrem Cluster anwenden.

```azurecli
kubectl apply -f rotate-creds.yaml
```

## <a name="next-steps"></a>Nächste Schritte

[Zugriff auf das Kubernetes-Dashboard mit Azure Kubernetes Service (AKS)](https://docs.microsoft.com/azure/aks/kubernetes-dashboard)

[SQL Server-verfügbarkeitsgruppe in Kubernetes-cluster](sql-server-ag-kubernetes.md)
