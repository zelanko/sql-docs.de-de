---
title: Bewährte Methoden für die Leistung für SQL Server-Big Data-Cluster
description: Dieser Artikel enthält bewährte Methoden für die Leistung und Richtlinien zum Ausführen von SQL Server-Big Data-Cluster in Kubernetes
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 06/30/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: abb5a73f472ccefa53517c54a3d403af82d0beb2
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85906234"
---
# <a name="performance-best-practices-and-configuration-guidelines-for-sql-server-big-data-clusters"></a>Bewährte Methoden für die Leistung und Konfigurationsrichtlinien für SQL Server-Big Data-Cluster

[!INCLUDE [sqlserver2019](../includes/applies-to-version/sqlserver2019.md)]

Dieser Artikel enthält bewährte Methoden und Empfehlungen zum Maximieren der Leistung für Anwendungen, die auf Dienste ausgerichtet sind, die in Big Data-Cluster ausgeführt werden.

Die folgenden Richtlinien konzentrieren sich auf Empfehlungen zum Konfigurieren des Linux-Betriebssystems, das die Kubernetes-Workerknoten enthält, auf denen Big Data-Cluster bereitgestellt wird. Es wird empfohlen, das Optimierungsprofil vor der Bereitstellung von Big Data-Cluster zu konfigurieren. Die im vorgeschlagenen Optimierungsprofil enthaltenen Einstellungen wurden im Rahmen der Fallstudie geprüft, die von Microsoft und Intel durchgeführt wurde. Die Ergebnisse der Studie sind in diesem [Whitepaper](https://aka.ms/sql-bdc-spark-perf/) enthalten, das zum Download zur Verfügung steht.

> [!TIP]
> Informationen zur Optimierung von Konfigurationen für SQL Server für Linux finden Sie unter [Bewährte Methoden für die Leistung und Konfigurationsrichtlinien für SQL Server für Linux](../linux/sql-server-linux-performance-best-practices.md). Außerdem gelten weiterhin andere bewährte Methoden wie Indexentwürfe für SQL Server-Datenbanken.

## <a name="proposed-linux-settings-using-a-tuned-mssql-bdc-profile"></a>Empfohlene Linux-Einstellungen für ein optimiertes `mssql-bdc`-Profil

Erstellen Sie ein **TUNED.CONF**-Konfigurationsprofil mit dem folgenden Inhalt.

```bash
[main]
summary=Optimize for Microsoft SQL Server Big Data Clusters TPC-DS performance
include=throughput-performance
 
[sysctl]
#network tunings
net.ipv4.conf.default.rp_filter=1
net.ipv4.tcp_timestamps=0
net.ipv4.tcp_sack = 1
net.core.netdev_max_backlog = 25000
net.core.rmem_max = 2147483647
net.core.wmem_max = 2147483647
net.core.rmem_default = 33554431
net.core.wmem_default = 33554432
net.core.optmem_max = 33554432
net.ipv4.tcp_rmem =8192 33554432 2147483647
net.ipv4.tcp_wmem =8192 33554432 2147483647
net.ipv4.tcp_low_latency=1
net.ipv4.tcp_adv_win_scale=1
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv4.conf.all.arp_filter=1
net.ipv4.tcp_retries2=5
net.ipv6.conf.lo.disable_ipv6 = 1
net.core.somaxconn = 65535
 
#memory cache settings
vm.swappiness=1
vm.overcommit_memory=0
vm.dirty_background_ratio=1
 
#kernel NUMA
kernel.numa_balancing=0

#filesystem
fs.aio-max-nr=1048576
 
[vm]
#should be revisited for SQL large pages use in master/data/compute pods
transparent_hugepages=never
```

## <a name="install-tuned-utility-on-all-the-kubernetes-worker-nodes"></a>Installieren Sie das Hilfsprogramm **tuned** auf allen Kubernetes-Workerknoten.

Führen Sie zum Installieren von **tuned** folgenden Code aus:

```bash
apt-get -y install tuned
```

## <a name="apply-tuning-settings-to-all-kubernetes-worker-nodes"></a>Übernehmen von Optimierungseinstellungen für alle Kubernetes-Workerknoten

Kopieren Sie auf jedem der Zielworkerknoten die oben erstellte **TUNED-CONFIG**-Datei.

```bash
cd /usr/lib/tuned
scp -r <sourcePath> ./mssql-bdc
```

Sie können dieses optimierte **mssql-bdc**-Profil aktivieren, indem Sie diese Definitionen in einer **TUNED.CONF**-Datei in einem `/usr/lib/tuned/mssql-bdc`-Ordner für alle Kubernetes-Workerknoten speichern und das Profil mithilfe des folgenden Codes aktivieren:

```bash
chmod +x /usr/lib/tuned/mssql-bdc/tuned.conf
tuned-adm profile mssql-bdc
```

Vergewissern Sie sich mit diesem Befehl, dass das Profil aktiviert ist:

```bash
tuned-adm active
```

oder

```bash
tuned-adm list
```

Wenn das Profil dynamisch geändert wird, müssen Sie **tuned** auf allen betroffenen Workerknoten neu starten, damit die neuen Änderungen wirksam werden:

```bash
systemctl restart tuned
```
 
Protokolle für den Dienst **tuned** finden Sie unter */var/log/tuned/tuned.log*.

Optional können Sie das Optimierungsprofil auf einem Knoten im Kubernetes-Cluster konfigurieren und das folgende Skript verwenden, um es zu kopieren und auf den verbleibenden Knoten zu konfigurieren.

```bash
#!/bin/bash -e
# This script takes a list of servers (IPs like `cat ~administrator/workerhosts)) as input
# and update these servers with the local version of mssql-bdc tuned.conf.
 
is_root() {
    local is_root_set=0
    if [ "$EUID" -ne 0 ]; then
        echo "Please run as root"
    else
        is_root_set=1
    fi
    return "${is_root_set}"
}
 
# function main
if is_root -eq 0; then
    exit 0
fi
 
while [ $# -gt 0 ]
do
    # sometimes, people add non-breaking space characters to their *host* files.
    WORKER_IP=$(echo "$1" | sed -e 's/\xC2\xA0//g')
    echo -e "updating mssql-bdc tuned on \e[42m${WORKER_IP}\e[0m"
    # the following commands assume tuned was not set up and active...
    # TODO: add the tuned install and status checks
    ssh "${WORKER_IP}" mkdir -p /usr/lib/tuned/mssql-bdc
    scp ~administrator/tuned.conf "${WORKER_IP}":/usr/lib/tuned/mssql-bdc/tuned.conf
    ssh "${WORKER_IP}" tuned-adm profile mssql-bdc
    ssh "${WORKER_IP}" systemctl restart tuned
    ssh "${WORKER_IP}" tuned-adm active
    shift
done

```

## <a name="next-steps"></a>Nächste Schritte

Weitere Ressourcen, einschließlich Referenzarchitekturen für SQL Server-Big Data-Cluster, finden Sie unter:

* [Fallstudie: SQL-Workloads, die auf Apache Spark in MS SQL Server 2019-Big Data-Cluster ausgeführt werden](https://aka.ms/sql-bdc-spark-perf/)

* [HPE Reference Architecture for delivering insight across all your data with Microsoft SQL Server 2019 Big Data Clusters (HPE-Referenzarchitektur für die Bereitstellung von Erkenntnissen für alle Ihre Daten mithilfe von Microsoft SQL Server 2019-Big Data-Cluster)](https://h20195.www2.hpe.com/V2/GetDocument.aspx?docname=a50001963enw)

* [Dell EMC PowerStore: Microsoft SQL Server 2019 Big Data Clusters (Dell EMC PowerStore: Microsoft SQL Server 2019-Big Data-Cluster)](https://www.dellemc.com/resources/en-us/asset/white-papers/products/storage/h18231-dell-emc-powerstore-sql-server-big-data-clusters.pdf)

* [Microsoft SQL Server 2019 Big Data Clusters: A Big Data Solution Using Dell EMC Infrastructure (Microsoft SQL Server 2019-Big Data-Cluster: eine Big Data-Lösung unter Verwendung der Dell EMC-Infrastruktur)](https://infohub.delltechnologies.com/t/microsoft-sql-server-2019-big-data-clusters-a-big-data-solution-using-dell-emc-infrastructure/)

* [Microsoft SQL Server 2019 Big Data Clusters on Cisco UCS Reference Architecture (Microsoft SQL Server 2019-Big Data-Cluster in der Cisco UCS-Referenzarchitektur)](https://www.cisco.com/c/en/us/solutions/collateral/data-center-virtualization/unified-computing/sql-server-on-big-data-cluster-on-ucs.html)