---
title: Bewährte Methoden für die Leistung für SQL Server für Linux
description: Dieser Artikel enthält bewährte Methoden für die Leistung sowie Ausführungsrichtlinien für SQL Server für Linux.
author: rgward
ms.author: bobward
ms.reviewer: vanto
ms.date: 09/14/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 543488eada46a088f3c634ce2326c7e2db2a97a5
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "68105444"
---
# <a name="performance-best-practices-and-configuration-guidelines-for-sql-server-on-linux"></a>Bewährte Methoden für die Leistung und Konfigurationsrichtlinien für SQL Server für Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dieser Artikel enthält bewährte Methoden und Empfehlungen, um die Leistung für Datenbankanwendungen zu maximieren, die mit SQL Server für Linux verbunden sind. Diese Empfehlungen gelten speziell für die Ausführung auf der Linux-Plattform. Alle normalen SQL Server Empfehlungen wie der Indexentwurf gelten weiterhin.

Im Folgenden erhalten Sie Empfehlungen zum Konfigurieren von SQL Server und des Linux-Betriebssystems.

## <a name="sql-server-configuration"></a>SQL Server-Konfiguration

Es wird empfohlen, nach der Installation von SQL Server für Linux die folgenden Konfigurationsaufgaben auszuführen, um eine optimale Leistung für Ihre Anwendung zu erzielen.

### <a name="best-practices"></a>Bewährte Methoden

- **Verwenden von PROCESS AFFINITY für Knoten und/oder CPUs**

   Es wird empfohlen, `ALTER SERVER CONFIGURATION` zu verwenden, um `PROCESS AFFINITY` für alle **NUMANODE**-Elemente und/oder CPUs festzulegen, die Sie für SQL Server (in der Regel für alle Knoten und CPUs) unter Linux verwenden. Die Prozessoraffinität hilft dabei, das Verhalten von Linux und SQL effizient zu planen. Die Verwendung der Option **NUMANODE** ist die einfachste Methode. Beachten Sie, dass Sie **PROCESS AFFINITY** auch dann verwenden sollten, wenn auf Ihrem Computer nur ein einzelner NUMA-Knoten vorhanden ist.  Weitere Informationen zum Festlegen von [PROCESS AFFINITY](../t-sql/statements/alter-server-configuration-transact-sql.md) finden Sie in der Dokumentation zu **ALTER SERVER CONFIGURATION**.

- **Konfigurieren mehrerer tempdb-Datendateien**

   Da die Installation von SQL Server für Linux keine Option zum Konfigurieren mehrerer tempdb-Dateien umfasst, empfiehlt es sich, erst nach der Installation die tempdb-Datendateien zu erstellen. Weitere Informationen finden Sie im Artikel [Empfehlungen zum Reduzieren von Konflikten bei der Zuweisung in tempdb-Datenbank für SQL Server](https://support.microsoft.com/help/2154845/recommendations-to-reduce-allocation-contention-in-sql-server-tempdb-d).

### <a name="advanced-configuration"></a>Erweiterte Konfiguration

Die folgenden Empfehlungen stellen optionale Konfigurationseinstellungen dar, die Sie nach der Installation von SQL Server für Linux durchführen können. Diese Optionen basieren auf den Anforderungen Ihrer Workload und der Konfiguration Ihres Linux-Betriebssystems.

- **Festlegen eines Arbeitsspeicherlimits mithilfe von mssql-conf**

   Damit immer genügend physischer Speicherplatz für Linux vorhanden ist, verwendet der SQL Server-Prozess standardmäßig nur 80 % des physischen Speichers. Bei großen Systemen können 20 % einen beachtlichen Unterschied darstellen. Bei einem System mit 1 TB RAM werden durch diese Standardeinstellung ca. 200 GB RAM freigelassen. In diesem Fall sollten Sie das Arbeitsspeicherlimit auf einen höheren Wert festlegen. Weitere Informationen finden Sie in der Dokumentation zum Tool **mssql-config** und der Einstellung [memory.memorylimitmb](sql-server-linux-configure-mssql-conf.md#memorylimit), die den für SQL Server sichtbaren Speicherplatz (in MB) steuert.

   Wenn Sie diese Einstellung ändern, achten Sie darauf, diesen Wert nicht zu hoch festzulegen. Wenn nicht genügend Arbeitsspeicher frei ist, können Probleme mit dem Linux-Betriebssystem und anderen Linux-Anwendungen auftreten.

## <a name="linux-os-configuration"></a>Konfigurieren des Linux-Betriebssystems

Verwenden Sie die folgenden Konfigurationseinstellungen für das Linux-Betriebssystem, um bei einer SQL Server-Installation die beste Leistung zu erzielen.

### <a name="kernel-settings-for-high-performance"></a>Kerneleinstellungen für hohe Leistung
Für das Linux-Betriebssystem werden die folgenden Einstellungen empfohlen, um bei einer SQL Server-Installation hohe Leistung und einen hohen Durchsatz zu erzielen. Der Prozess zum Konfigurieren dieser Einstellungen wird in der Linux-Dokumentation beschrieben.



> [!Note]
> Für Red Hat Enterprise Linux-Benutzer (RHEL) konfiguriert das Profil „throughput-performance“ diese Einstellungen automatisch (mit Ausnahme von C-Status).

In der folgenden Tabelle finden Sie Empfehlungen für die CPU-Einstellungen:

| Einstellung | value | Weitere Informationen |
|---|---|---|
| CPU frequency governor (Kontrolle der CPU-Häufigkeit) | Leistung | Dokumentation zum Befehl **cpupower** |
| ENERGY_PERF_BIAS | Leistung | Dokumentation zum Befehl **x86_energy_perf_policy** |
| min_perf_pct | 100 | Dokumentation zum Status „intel p“ |
| C-States (C-Status) | C1 only (Nur C1) | In der Linux- oder Systemdokumentation erhalten Sie Informationen dazu, wie Sie sicherstellen können, dass die Einstellung „C-States“ (C-Status) auf „C1 only“ (Nur C1) festgelegt ist. |

In der folgenden Tabelle finden Sie Empfehlungen für die Datenträgereinstellungen:

| Einstellung | value | Weitere Informationen |
|---|---|---|
| disk readahead | 4096 | Dokumentation zum Befehl **blockdev** |
| sysctl-Einstellungen | kernel.sched_min_granularity_ns = 10.000.000<br/>kernel.sched_wakeup_granularity_ns = 15.000.000<br/>vm.dirty_ratio = 40<br/>vm.dirty_background_ratio = 10<br/>vm.swappiness = 10 | Dokumentation zum Befehl **sysctl** |

### <a name="kernel-setting-auto-numa-balancing-for-multi-node-numa-systems"></a>Kernel-Einstellung für den automatischen NUMA-Ausgleich für NUMA-Systeme mit mehreren Knoten

Wenn Sie SQL Server auf einem **NUMA**-System mit mehreren Knoten installieren, ist die folgende **kernel.numa_balancing**-Kerneleinstellung standardmäßig aktiviert. Deaktivieren Sie den automatischen NUMA-Ausgleich für das **NUMA**-System mit mehreren Knoten, damit SQL Server auf diesem mit bestmöglicher Effizienz arbeiten können:

```bash
sysctl -w kernel.numa_balancing=0
```

### <a name="kernel-settings-for-virtual-address-space"></a>Kerneleinstellungen für virtuelle Adressräume

Die Standardeinstellung für **vm.max_map_count** (65536) ist für eine SQL Server-Installation möglicherweise nicht hoch genug. Ändern Sie diesen Wert, der die Obergrenze darstellt, in 256.000.

```bash
sysctl -w vm.max_map_count=262144
```

### <a name="disable-last-accessed-datetime-on-file-systems-for-sql-server-data-and-log-files"></a>Deaktivieren von Datum/Uhrzeit des letzten Zugriffs auf Dateisysteme für SQL Server-Daten- und -Protokolldateien

Verwenden Sie das Attribut **noatime** mit einem beliebigen Dateisystem, das zum Speichern von SQL Server-Daten- und -Protokolldateien verwendet wird. Informationen zum Festlegen dieses Attributs finden Sie in der Linux-Dokumentation.

### <a name="leave-transparent-huge-pages-thp-enabled"></a>Lassen Sie die Option „Transparent Huge Pages“ aktiviert.

Bei den meisten Linux-Installationen sollte diese Option standardmäßig aktiviert sein. Es wird empfohlen, dies nicht zu ändern, damit die Leistung konstant gut bleibt.

### <a name="swapfile"></a>Auslagerungsdatei

Stellen Sie sicher, dass Sie über eine ordnungsgemäß konfigurierte Auslagerungsdatei verfügen, damit keine Probleme mit dem Arbeitsspeicher auftreten. In der Linux-Dokumentation erhalten Sie Informationen über die Erstellung und ordnungsgemäße Größenanpassung von Auslagerungsdateien.

### <a name="virtual-machines-and-dynamic-memory"></a>Virtuelle Computer und dynamischer Arbeitsspeicher

Wenn Sie SQL Server für Linux auf einem virtuellen Computer ausführen, stellen Sie sicher, dass Sie entsprechende Optionen auswählen, um dem für den virtuellen Computer reservierten Arbeitsspeicher gerecht zu werden. Verwenden Sie keine Features wie Hyper-V Dynamic Memory.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu SQL Server-Features, die die Leistung verbessern, finden Sie unter [Erste Schritte mit den Leistungsfeatures](sql-server-linux-performance-get-started.md).

Weitere Informationen zu SQL Server für Linux finden Sie in der [Übersicht für SQL Server für Linux](sql-server-linux-overview.md).
