---
title: Hochverfügbarkeit für SQL Server-Container
description: Dieser Artikel bietet eine Einführung in die Hochverfügbarkeit für SQL Server-Container.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-2017||>=sql-server-linux-2017||=sqlallproducts-allversions'
ms.openlocfilehash: aa54849c16ea9dfb821404b553b1e9183b61d66a
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68077481"
---
# <a name="high-availability-for-sql-server-containers"></a>Hochverfügbarkeit für SQL Server-Container

Erstellen und verwalten Sie Ihre SQL Server-Instanzen nativ in Kubernetes.

Stellen Sie SQL Server an Docker-Container bereit, die von [Kubernetes](https://kubernetes.io/) verwaltet werden. In Kubernetes kann ein Container mit einer SQL Server-Instanz automatisch wiederhergestellt werden, wenn ein Clusterknoten ausfällt. Sie können eine SQL Server-Always On-Verfügbarkeitsgruppe mit SQL Server-Instanzen in Containern auf einem Kubernetes-Cluster konfigurieren, um die Verfügbarkeit stabiler zu machen. In diesem Artikel werden die beiden Lösungen verglichen.

## <a name="compare-sql-server-versions-on-kubernetes"></a>Vergleich der SQL Server-Versionen auf Kubernetes

SQL Server 2017 bietet ein Docker-Image für die Bereitstellung auf Kubernetes. Sie können das Image mit einem PersistentVolumeClaim (PVC) von Kubernetes konfigurieren. Kubernetes überwacht den SQL Server-Prozess im Container. Wenn Prozess, Pod, Container oder Knoten ausfallen, startet Kubernetes automatisch eine andere Instanz und stellt die Verbindung zum Speicher wieder her.

Mit SQL Server 2019 (Preview) wird eine stabilere Architektur mit einem StatefulSet von Kubernetes eingeführt. Kubernetes orchestriert SQL Server-Instanzen in Containerimages, die an einer SQL Server-Always On-Verfügbarkeitsgruppe beteiligt sind. Dieses Muster bietet verbesserte Integritätsüberwachung, schnellere Wiederherstellung, ausgelagerte Sicherung und horizontale Leseskalierung.  

## <a name="container-with-sql-server-instance-on-kubernetes"></a>Container mit SQL Server-Instanz auf Kubernetes

Kubernetes 1.6 und höher unterstützt [*Speicherklassen*](https://kubernetes.io/docs/concepts/storage/storage-classes/), [*PersistentVolumeClaims*](https://kubernetes.io/docs/concepts/storage/storage-classes/#persistentvolumeclaims) und den [*Volumetyp Azure-Datenträger*](https://github.com/kubernetes/examples/tree/master/staging/volumes/azure_disk). 

In dieser Konfiguration spielt Kubernetes die Rolle des Containerorchestrators. 

![Diagramm eines Kubernetes-SQL Server-Clusters](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql.png)

Im obigen Diagramm ist `mssql-server` eine SQL Server-Instanz (Container) in einem [*Pod*](https://kubernetes.io/docs/concepts/workloads/pods/pod/). Eine [Replikatgruppe](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/) stellt sicher, dass der Pod nach dem Ausfall eines Knotens automatisch wiederhergestellt wird. Anwendungen stellen eine Verbindung zum Dienst her. In diesem Fall stellt der Dienst einen Lastenausgleich dar, der eine IP-Adresse hostet, die sich nach dem Ausfall des `mssql-server` nicht ändert.

Kubernetes orchestriert die Ressourcen im Cluster. Wenn ein Knoten, der einen SQL Server-Instanzcontainer hostet, fehlschlägt, startet er einen neuen Container mit einer SQL Server-Instanz und fügt sie an denselben beständigen Speicher an.

SQL Server 2017 und höher unterstützt Container auf Kubernetes.

Informationen zum Erstellen eines Containers in Kubernetes finden Sie unter [Deploy a SQL Server container in Kubernetes (Bereitstellen eines SQL Server-Containers in Kubernetes)](tutorial-sql-server-containers-kubernetes.md).

## <a name="a-sql-server-always-on-availability-group-on-sql-server-containers-in-kubernetes"></a>SQL Server-Always On-Verfügbarkeitsgruppe auf SQL Server-Containern in Kubernetes

SQL Server 2019 unterstützt Verfügbarkeitsgruppen auf Containern in Kubernetes. Stellen Sie den [Kubernetes-Operator](https://coreos.com/blog/introducing-operators.html) von SQL Server an Ihren Kubernetes-Cluster bereit, um Verfügbarkeitsgruppen zu nutzen. Der Operator hilft beim Packen, Bereitstellen und Verwalten von SQL Server-Instanzen und der Verfügbarkeitsgruppe in einem Cluster.

![Verfügbarkeitsgruppe in Kubernetes-Container](media/tutorial-sql-server-ag-containers-kubernetes/KubernetesCluster.png)

In der obigen Abbildung hostet ein Kubernetes-Cluster mit vier Knoten eine Verfügbarkeitsgruppe mit drei Replikaten. Die Lösung umfasst folgende Komponenten:

* Eine Kubernetes-[*Bereitstellung*](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/). Die Bereitstellung umfasst den Operator und eine Konfigurationszuordnung. Die Bereitstellung beschreibt das Containerimage, die Software und die Anweisungen, die erforderlich sind, um SQL Server-Instanzen für die Verfügbarkeitsgruppe bereitzustellen.

* Drei Knoten, von denen jeder ein [*StatefulSet*](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/) hostet. Das StatefulSet enthält einen Pod. Jeder Pod enthält wiederum Folgendes:
  * Einen SQL Server-Container, der eine Instanz von SQL Server ausführt.
  * Den Supervisor `mcr.microsoft.com/mssql/ha` zur Verwaltung der Verfügbarkeitsgruppe.

* Zwei [*ConfigMaps*](https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/), die mit der Verfügbarkeitsgruppe zusammenhängen. Die ConfigMaps bieten Informationen über Folgendes:
  * Die Bereitstellung für den Operator.
  * Die Verfügbarkeitsgruppe.

 * Beständige Volumes stellen für jede Instanz von SQL Server den Speicher für die Daten und Protokolldateien bereit.

Außerdem speichert der Cluster [*Geheimnisse*](https://kubernetes.io/docs/concepts/configuration/secret/) für die Kennwörter, Zertifikate, Schlüssel und andere vertrauliche Informationen.

## <a name="compare-sql-server-high-availability-on-containers-with-and-without-the-availability-group"></a>Vergleich der Hochverfügbarkeit von SQL Server auf Containern mit und ohne Verfügbarkeitsgruppe

In der folgenden Tabelle wird die Hochverfügbarkeit von SQL Server in Containern auf Kubernetes mit und ohne Verfügbarkeitsgruppe verglichen:

| |Mit Verfügbarkeitsgruppe | Eigenständige Containerinstanz<br/> Ohne Verfügbarkeitsgruppe
|:------|:------|:------
|Automatische Wiederherstellung nach dem Ausfall eines Knotens | Ja | Ja
|Automatische Wiederherstellung nach dem Ausfall eines Pods | Ja | Ja
|Schnelleres Failover |Ja |
|Automatische Wiederherstellung nach dem Ausfall einer SQL Server-Instanz | Ja | 
|Automatische Wiederherstellung nach dem Fehlschlagen der Überprüfung der Datenbankintegrität | Ja | 
|Bereitstellung schreibgeschützter Replikate | Ja |
|Sicherung sekundärer Replikate | Ja | 
|Ausführung als StatefulSet | Ja | 

Einer der Hauptunterschiede besteht darin, dass die Zeit für die Wiederherstellung (oder das Failover) mit einer Verfügbarkeitsgruppe kürzer ist als bei einer einzelnen SQL Server-Instanz in einem Container. Diese Verbesserung ergibt sich daraus, dass die SQL Server-Verfügbarkeitsgruppe sekundäre Replikate auf anderen Knoten im Cluster beibehält. Beim Failover wird ein sekundäres Replikat ausgewählt und zum primären Replikat höher gestuft. Anwendungen, die mit dem Dienst verbunden sind, werden zum neuen primären Replikat umgeleitet.

Wenn keine Verfügbarkeitsgruppe vorhanden ist und Kubernetes ein Failover erkennt, muss es den Container erstellen und mit dem Speicher verbinden. Dann werden mit dem Dienst verbundene Anwendungen erneut verbunden. Die genaue Failoverzeit hängt davon ab, wo das Failover stattgefunden hat und wie es erkannt wurde. 

Die Failoverzeit für eine Verfügbarkeitsgruppe liegt in der Regel im Sekundenbereich. Die Failoverzeit für eine einzelne Instanz zur Wiederherstellung eines Containers kann jedoch bis zu 10 Minuten betragen.

## <a name="next-steps"></a>Nächste Schritte

Informationen zum Bereitstellen von SQL Server-Containern in Azure Kubernetes Service (AKS) finden Sie in folgenden Beispielen:

* [Bereitstellen von SQL Server in einem Docker-Container](sql-server-linux-configure-docker.md)
* [Bereitstellen eines SQL Server-Containers in Kubernetes](tutorial-sql-server-containers-kubernetes.md)
* [Always On-Verfügbarkeitsgruppen für SQL Server-Container](sql-server-ag-kubernetes.md)

