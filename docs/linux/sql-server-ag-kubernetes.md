---
title: Always On-Verfügbarkeitsgruppen für Container unter Linux
titleSuffix: SQL Server
description: Dieser Artikel bietet eine Einführung in Verfügbarkeitsgruppen in SQL Server-Containern.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3910c74be803b7fc63c8bf560fc637387e06ee15
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "67910469"
---
# <a name="always-on-availability-groups-for-sql-server-containers"></a>Always On-Verfügbarkeitsgruppen für SQL Server-Container

SQL Server 2019 unterstützt Verfügbarkeitsgruppen in Containern in einem Kubernetes-Cluster. Stellen Sie den [Kubernetes-Operator](https://coreos.com/blog/introducing-operators.html) von SQL Server in Ihrem Kubernetes-Cluster bereit, um Verfügbarkeitsgruppen zu nutzen. Der Operator hilft beim Packen, Bereitstellen und Verwalten der Verfügbarkeitsgruppe in einem Cluster.

![Verfügbarkeitsgruppe in Kubernetes-Container](media/tutorial-sql-server-ag-containers-kubernetes/KubernetesCluster.png)

In der obigen Abbildung hostet ein Kubernetes-Cluster mit vier Knoten eine Verfügbarkeitsgruppe mit drei Replikaten. Die Lösung enthält folgende Komponenten:

* Eine Kubernetes-[*Bereitstellung*](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/). Die Bereitstellung umfasst den Operator und eine Konfigurationszuordnung. Diese stellen das Containerimage, die Software und die Anweisungen bereit, die erforderlich sind, um SQL Server-Instanzen für die Verfügbarkeitsgruppe bereitzustellen.

* Drei Knoten, von denen jeder ein [*StatefulSet*](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/) hostet. Das StatefulSet enthält einen [*Pod*](https://kubernetes.io/docs/concepts/workloads/pods/pod-overview/). Jeder Pod umfasst Folgendes:
  * Einen SQL Server-Container, der eine Instanz von SQL Server ausführt.
  * Einen Verfügbarkeitsgruppen-Agent. 

* Zwei [*ConfigMaps*](https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/) zur Verfügbarkeitsgruppe. Die ConfigMaps bieten Informationen über Folgendes:
  * Die Bereitstellung für den Operator.
  * Die Verfügbarkeitsgruppe.

 * [*Persistente Volumes*](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) sind Speicherelemente. Ein *Anspruch auf persistente Volumes* (Persistent Volume Claim, PVC) ist eine von einem Benutzer gestellte Anforderung an Speicher. Jeder Container ist für die Speicherung von Daten und Protokollen mit einem PVC verbunden. In Azure Kubernetes Service (AKS) [erstellen Sie einen Anspruch auf persistente Volumes](https://docs.microsoft.com/azure/aks/azure-disks-dynamic-pv), um Speicher automatisch basierend auf einer Speicherklasse bereitzustellen.


Außerdem speichert der Cluster [*Geheimnisse*](https://kubernetes.io/docs/concepts/configuration/secret/) für die Kennwörter, Zertifikate, Schlüssel und andere vertrauliche Informationen.

## <a name="deploy-the-availability-group-in-kubernetes"></a>Bereitstellen der Verfügbarkeitsgruppe in Kubernetes

So stellen Sie eine Verfügbarkeitsgruppe in Kubernetes bereit:

1. Erstellen des Kubernetes-Clusters

   Erstellen Sie für eine Verfügbarkeitsgruppe mindestens drei Knoten für SQL Server plus einen Knoten für den Master.

1. Bereitstellen des Operators

1. Konfigurieren des Speichers

1. Bereitstellen des StatefulSet

   Der Operator lauscht auf Anweisungen zum Bereitstellen des StatefulSet. Er erstellt automatisch die SQL Server-Instanzen auf drei separaten Knoten und konfiguriert die Verfügbarkeitsgruppe mit einem externen Cluster-Manager.

1. Erstellen der Datenbanken und Anfügen an die Verfügbarkeitsgruppe

Eine detaillierte Anleitung hierfür finden Sie unter [Always On-Verfügbarkeitsgruppen für SQL Server-Container](sql-server-ag-kubernetes.md).

## <a name="sql-server-kubernetes-operator"></a>SQL Server-Kubernetes-Operator

Nachdem Sie den Operator bereitgestellt haben, registriert er eine benutzerdefinierte SQL Server-Ressource. Verwenden Sie den Operator, um diese Ressource bereitzustellen.  Jede Ressource entspricht einer Instanz von SQL Server und enthält bestimmte Eigenschaften wie `sapassword` und `monitoring policy`. Der-Operator analysiert die Ressource und stellt ein Kubernetes-StatefulSet bereit.

Das StatefulSet enthält Folgendes:

* mssql-server container

* mssql-ha-supervisor container

Der Code für den Operator, den Hochverfügbarkeitssupervisor und SQL Server ist in einem Docker-Image namens `mcr.microsoft.com/mssql/ha` gepackt. Dieses Image enthält die folgenden Binärdateien:

* `mssql-operator`

    Dieser Prozess wird als separate Kubernetes-Bereitstellung bereitgestellt. Er registriert die [benutzerdefinierte Kubernetes](https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/)-Ressource mit dem Namen `SqlServer` (sqlservers.mssql.microsoft.com). Dann überwacht er, ob solche Ressourcen im Kubernetes-Cluster erstellt oder aktualisiert werden. Bei jedem solchen Ereignis erstellt oder aktualisiert er die Kubernetes-Ressourcen für die entsprechende Instanz (z.B. das StatefulSet oder einen `mssql-server-k8s-init-sql`-Auftrag).

* `mssql-server-k8s-health-agent`

    Dieser Webserver dient für Kubernetes-[Livetests](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-probes/), um die Integrität einer SQL Server-Instanz zu ermitteln. Er überwacht die Integrität Zustand der lokalen SQL Server Instanz durch Aufrufen von `sp_server_diagnostics` und Vergleichen der Ergebnisse mit Ihrer Überwachungsrichtlinie.

* `mssql-ha-supervisor`

   Verwaltet das Zertifikat und den Endpunkt der Verfügbarkeitsgruppe. 

* `mssql-server-k8s-ag-agent`
  
    Dieser Prozess überwacht die Integrität eines Verfügbarkeitsgruppenreplikats auf einer einzelnen SQL Server-Instanz und führt Failover durch.

    Er verwaltet auch die Leaderauswahl.

* `mssql-server-k8s-init-sql`
  
    Dieser Kubernetes-[Auftrag](https://kubernetes.io/docs/concepts/workloads/controllers/jobs-run-to-completion/) wendet eine Konfiguration des gewünschten Zustands auf eine SQL Server-Instanz an. Der Auftrag wird bei jeder Erstellung oder Aktualisierung einer SqlServer-Ressource vom Operator erstellt. Er stellt sicher, dass die SQL Server-Zielinstanz, die zur benutzerdefinierten Ressource gehört, über die in der Ressource beschrieben gewünschte Konfiguration verfügt.

    Wenn beispielsweise eine der folgenden Einstellungen erforderlich ist, führt der Auftrag den entsprechenden Vorgang aus:
  * Aktualisieren des Systemadministratorkennworts
  * Erstellen der SQL-Anmeldung für die Agents
  * Erstellen des DBM-Endpunkts

* `mssql-server-k8s-rotate-creds`
  
    Dieser Kubernetes-Auftrag implementiert den Task zum Rotieren von Anmeldeinformationen. Erstellen Sie diesen Auftrag, um Aktualisierungen des Systemadministratorkennworts, des SQL-Anmeldekennworts für den Agent, des DBM-Zertifikats usw. anzufordern. Das Systemadministratorkennwort ist als Auftragsparameter angegeben. Die anderen Angaben werden automatisch generiert.

* `mssql-server-k8s-failover`

   Ein Kubernetes-Auftrag, der den Workflow für manuelles Failover implementiert.

### <a name="notes"></a>Hinweise

Unabhängig von der Konfiguration der Verfügbarkeitsgruppe stellt der Operator immer den Hochverfügbarkeitssupervisor bereit. Wenn die SqlServer-Ressource keine Verfügbarkeitsgruppe aufführt, stellt der Operator diesen Container trotzdem bereit.

Die Version für das Operatorimage ist identisch mit der Version für das SQL Server-Image.

## <a name="next-steps"></a>Nächste Schritte

> [SQL Server-Container in Kubernetes](tutorial-sql-server-containers-kubernetes.md)
