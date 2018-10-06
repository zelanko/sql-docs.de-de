---
title: Hohe Verfügbarkeit für SQL Server-Container
description: In diesem Artikel werden die hohen Verfügbarkeit für SQL Server-Container
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-2017||>=sql-server-linux-2017||=sqlallproducts-allversions'
ms.openlocfilehash: 1f5c3cc4756c305ba82af4c110488722ec24a9af
ms.sourcegitcommit: 4832ae7557a142f361fbf0a4e2d85945dbf8fff6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2018
ms.locfileid: "48251987"
---
# <a name="high-availability-for-sql-server-containers"></a>Hohe Verfügbarkeit für SQL Server-Container

Erstellen Sie und verwalten Sie Ihre SQL Server-Instanzen nativ in Kubernetes.

Bereitstellen von SQL Server Docker-Containern, die von verwalteten [Kubernetes](https://kubernetes.io/). In Kubernetes kann Container mit einer SQL Server-Instanz automatisch wiederherstellen, für den Fall, dass ein Clusterknoten ein Fehler auftritt. Konfigurieren Sie SQL Server Always On-verfügbarkeitsgruppe für robustere Verfügbarkeit mit SQL Server-Instanzen in Containern in einem Kubernetes-Cluster. Dieser Artikel vergleicht die beiden Lösungen.

## <a name="compare-sql-server-versions-on-kubernetes"></a>Vergleichen Sie SQL Server-Versionen in Kubernetes

SQL Server 2017 bietet ein Docker-Image, das Bereitstellen in Kubernetes. Sie können das Image mit einem Kubernetes-permanenter volumeanspruch (PVC) konfigurieren. Kubernetes überwacht SQL Server-Prozess im Container. Wenn der Prozess, der Pod, Container oder Knoten ausfallen, Kubernetes wird automatisch ein Bootstrap für eine andere Instanz und erneut eine Verbindung, in den Speicher herstellt.

SQL Server-2019 (Vorschau) wird eine stabilere Architektur mit einem Kubernetes StatefulSet eingeführt. Kubernetes orchestriert die Instanzen von SQL Server-Container-Images, die in einer SQL Server AlwaysOn-Verfügbarkeitsgruppe beteiligt sind. Dieses Muster bietet verbesserte Überwachung, schnellere Wiederherstellung, Sicherung der Auslagerung und read Scale out.  

## <a name="container-with-sql-server-instance-on-kubernetes"></a>Container mit SQL Server-Instanz in Kubernetes

Kubernetes 1.6 und höher bietet Unterstützung für [ *Speicherklassen*](http://kubernetes.io/docs/concepts/storage/storage-classes/), [ *persistentes Volume Ansprüche*](http://kubernetes.io/docs/concepts/storage/storage-classes/#persistentvolumeclaims), und die [  *Azure-Datenträger Volumetyp*](https://github.com/kubernetes/examples/tree/master/staging/volumes/azure_disk). 

In dieser Konfiguration eingepackt Kubernetes der containerorchestrator. 

![Diagramm der SQL Server von Kubernetes-cluster](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql.png)

Im obigen Diagramm `mssql-server` befindet sich in eine SQL Server-Instanz (Container) einer [ *Pod*](http://kubernetes.io/docs/concepts/workloads/pods/pod/). Ein [Replikatgruppe](http://kubernetes.io/docs/concepts/workloads/controllers/replicaset/) wird sichergestellt, dass der Pod automatisch nach einem Knotenausfall wiederhergestellt wird. Anwendungen eine Verbindung mit dem Dienst herstellen. In diesem Fall stellt der Dienst einen Load Balancer, der eine IP-Adresse hostet, die gleich nach einem Ausfall der bleibt die `mssql-server`.

Kubernetes orchestriert die Ressourcen im Cluster. Fällt ein Knoten, die einen SQL Server-Instanz-Container gehostet, startet einen neuen Container mit einer SQL Server-Instanz und fügt ihn an den gleichen persistenten Speicher.

SQL Server 2017 und höher unterstützt Container in Kubernetes.

Zum Erstellen eines Containers in Kubernetes finden Sie unter [bereitstellen ein SQL Server-Containers in Kubernetes](tutorial-sql-server-containers-kubernetes.md)

## <a name="a-sql-server-always-on-availability-group-on-sql-server-containers-in-kubernetes"></a>Eine SQL Server Always On-verfügbarkeitsgruppe in SQL Server-Containern in Kubernetes

SQL Server-2019 unterstützt Verfügbarkeitsgruppen für in einem Kubernetes-Container. Bereitstellen von SQL Server für Verfügbarkeitsgruppen [Kubernetes-Operator](http://coreos.com/blog/introducing-operators.html) in Ihrem Kubernetes-Cluster. Der Operator packen, bereitstellen und Verwalten von SQL Server-Instanzen und der verfügbarkeitsgruppe in einem Cluster.

![Verfügbarkeitsgruppe im Kubernetes-Container](media/tutorial-sql-server-ag-containers-kubernetes/KubernetesCluster.png)

In der Abbildung oben hostet ein vier-Knoten-Kubernetes-Cluster eine verfügbarkeitsgruppe mit drei Replikaten. Die Lösung umfasst die folgenden Komponenten:

* Eine Kubernetes [ *Bereitstellung*](http://kubernetes.io/docs/concepts/workloads/controllers/deployment/). Die Bereitstellung umfasst auch den Operator und einer Zuordnung für die Konfiguration. Die Bereitstellung beschreibt das containerimage, Software und Anweisungen zur Bereitstellung von SQL Server-Instanzen für die verfügbarkeitsgruppe erforderlich.

* Drei Knoten, die jede Hosten einer [ *StatefulSet*](http://kubernetes.io/docs/concepts/workloads/controllers/statefulset/). Die StatefulSet enthält einen Pod. Jedem Pod enthält:
  * Ein SQL Server-Container mit einer Instanz von SQL Server.
  * Supervisor `mcr.microsoft.com/mssql/ha` die verfügbarkeitsgruppe zu verwalten.

* Zwei [ *ConfigMaps* ](http://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/) im Zusammenhang mit der verfügbarkeitsgruppe. Die ConfigMaps enthalten Informationen über:
  * Die Bereitstellung für den Operator.
  * Die Verfügbarkeitsgruppe.

 * Persistente Volumes für jede Instanz von SQL Server stellen die Speicher für die Daten und Protokolldateien bereit.

Der Cluster darüber hinaus speichert [ *Geheimnisse* ](http://kubernetes.io/docs/concepts/configuration/secret/) für die Kennwörter, Zertifikate, Schlüssel und andere vertrauliche Informationen.

## <a name="compare-sql-server-high-availability-on-containers-with-and-without-the-availability-group"></a>Vergleichen Sie SQL Server-hochverfügbarkeit in Containern mit und ohne die verfügbarkeitsgruppe

Die folgende Tabelle vergleicht die hohe Verfügbarkeit von SQL Server in Containern in Kubernetes mit und ohne eine verfügbarkeitsgruppe an:

| |Mit einer verfügbarkeitsgruppe | Eigenständige-Containerinstanz<br/> Keine verfügbarkeitsgruppe
|:------|:------|:------
|Vom Ausfall eines Knotens wird automatisch wiederhergestellt. | Benutzerkontensteuerung | Benutzerkontensteuerung
|Automatische Wiederherstellung von Pod-Fehler | Benutzerkontensteuerung | Benutzerkontensteuerung
|Schnelleres failover |Benutzerkontensteuerung |
|Automatische Wiederherstellung von SQL Server-Instanz Fehler | Benutzerkontensteuerung | 
|Automatische Wiederherstellung von Datenbankfehlern für Integrität überprüfen | Benutzerkontensteuerung | 
|Bereitstellen von schreibgeschützten Replikaten | Benutzerkontensteuerung |
|Sicherung des sekundären Replikats | Benutzerkontensteuerung | 
|Als einem StatefulSet ausgeführt wird | Benutzerkontensteuerung | 

Ein Hauptunterschied ist, dass die Wiederherstellung (oder einem Failover) Zeit schneller mit einer verfügbarkeitsgruppe als mit einer einzelnen Instanz von SQL Server in einem Container. Diese Verbesserung ist, da die SQL Server-verfügbarkeitsgruppe sekundäre Replikate auf anderen Knoten im Cluster beibehält. Bei einem Failover ein sekundäres Replikat ausgewählt und zum primären Replikat heraufgestuft. Anwendungen, die mit dem Dienst verbunden werden an das neue primäre Replikat weitergeleitet.

Ohne die verfügbarkeitsgruppe, und wenn einen Failover von Kubernetes erkannt wird, muss den Container zu erstellen, verbinden es mit dem Speicher, und klicken Sie dann mit dem Dienst verbundene Anwendungen wiederhergestellt werden. Die genaue Failoverzeit, hängt davon ab, in denen das Failover wurde und wie er erkannt wurde. 

Im Allgemeinen wird die Failoverzeit für eine verfügbarkeitsgruppe in Sekunden gemessen, während die Failoverzeit für einzelne Instanz ein Containers Wiederherstellen bis zu 10 Minuten sein kann.

## <a name="next-steps"></a>Nächste Schritte

Zum Bereitstellen von SQL Server-Containern in Azure Kubernetes Service (AKS) finden Sie in diesen Beispielen:

* [Bereitstellen von SQL Server in Docker-container](sql-server-linux-configure-docker.md)
* [Bereitstellen eines SQL Server-Containers in Kubernetes](tutorial-sql-server-containers-kubernetes.md)
* [Always On-Verfügbarkeitsgruppen für SQL Server-Container](sql-server-ag-kubernetes.md)

