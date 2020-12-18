---
title: Bewährte Methoden für die Leistung für SQL Server für Linux
description: Dieser Artikel enthält bewährte Methoden für die Leistung sowie Ausführungsrichtlinien für SQL Server für Linux.
author: tejasaks
ms.author: tejasaks
ms.reviewer: vanto
ms.date: 12/11/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 89b8a7c087fb87ed911be640126ec81021b045a7
ms.sourcegitcommit: 2991ad5324601c8618739915aec9b184a8a49c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323505"
---
# <a name="performance-best-practices-and-configuration-guidelines-for-sql-server-on-linux"></a>Bewährte Methoden für die Leistung und Konfigurationsrichtlinien für SQL Server für Linux

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

Dieser Artikel enthält bewährte Methoden und Empfehlungen, um die Leistung für Datenbankanwendungen zu maximieren, die mit SQL Server für Linux verbunden sind. Diese Empfehlungen gelten speziell für die Ausführung auf der Linux-Plattform. Alle normalen SQL Server Empfehlungen wie der Indexentwurf gelten weiterhin.

Im Folgenden erhalten Sie Empfehlungen zum Konfigurieren von SQL Server und des Linux-Betriebssystems.

## <a name="linux-os-configuration"></a>Konfigurieren des Linux-Betriebssystems

Verwenden Sie die folgenden Konfigurationseinstellungen für das Linux-Betriebssystem, um bei einer SQL Server-Installation die beste Leistung zu erzielen.

### <a name="storage-configuration-recommendation"></a>Empfehlungen für die Speicherkonfiguration

#### <a name="use-storage-subsystem-with-appropriate-iops-throughput-and-redundancy"></a>Verwenden des Speichersubsystems mit angemessenen Werten für IOPS, Durchsatz und Redundanz

Das Speichersubsystem, in dem die Daten, Transaktionsprotokolle und weitere dazugehörige Dateien (z. B. Prüfpunktdateien für In-Memory-OLTP) gehostet sind, sollte in der Lage sein, sowohl durchschnittliche Workloads als auch Spitzenworkloads ordnungsgemäß zu verwalten. Normalerweise unterstützen Speicheranbieter in lokalen Umgebungen angemessene RAID-Konfigurationen für Hardware mit Striping für mehrere Datenträger, um für angemessene Werte für IOPS, Durchsatz und Redundanz zu sorgen. Dies kann für verschiedene Speicheranbieter und verschiedene Speicherangebote mit unterschiedlichen Architekturen jedoch variieren.

Für auf Azure-VMs bereitgestellte SQL Server für Linux-Instanzen sollten Sie die Verwendung von Software-RAID in Erwägung ziehen, um sicherzustellen, dass die entsprechenden Anforderungen an IOPS und Durchsatz erfüllt werden. Sehen Sie sich zu ähnlichen Speicheraspekten den folgenden Artikel an, wenn Sie SQL Server auf Azure-VMs konfigurieren: [Speicherkonfiguration für SQL Server-VMs](https://docs.microsoft.com/azure/azure-sql/virtual-machines/windows/storage-configuration)

Unten sehen Sie ein Beispiel dafür, wie Software-RAID unter Linux auf Azure-VMs erstellt werden kann. Unten finden Sie ein Beispiel, Sie sollten jedoch eine angemessene Anzahl an Datenträgern für die erforderlichen Werte für Durchsatz und IOPS für Volumes basierend auf den Anforderungen an Daten, Transaktionsprotokolle und tempdb-EA verwenden. In diesem Beispiel wurden acht Datenträger an die Azure-VM angefügt: vier, um die Datendateien zu hosten, zwei für die Transaktionsprotokolle und zwei für die tempdb-Workload.

```bash
# To locate the devices (for example /dev/sdc) for RAID creation, use the lsblk command
# For Data volume, using 4 devices, in RAID 5 configuration with 8KB stripes
mdadm --create --verbose /dev/md0 --level=raid5 --chunk=8K --raid-devices=4 /dev/sdc /dev/sdd /dev/sde /dev/sdf

# For Log volume, using 2 devices in RAID 10 configuration with 64KB stripes
mdadm --create --verbose /dev/md1 --level=raid10 --chunk=64K --raid-devices=2 /dev/sdg /dev/sdh

# For tempdb volume, using 2 devices in RAID 0 configuration with 64KB stripes
mdadm --create --verbose /dev/md2 --level=raid0 --chunk=64K --raid-devices=2 /dev/sdi /dev/sdj
```

#### <a name="file-system-configuration-recommendation"></a>Empfehlungen für die Dateisystemkonfiguration

SQL Server unterstützt sowohl EXT4- als auch XFS-Dateisysteme als Host für Datenbank, Transaktionsprotokolle und weitere Dateien wie Prüfpunktdateien für In-Memory-OLTP in SQL Server. Microsoft empfiehlt die Verwendung des XFS-Dateisystems für das Hosten der SQL Server-Daten und Transaktionsprotokolldateien.

```bash
# Formatting the volume with XFS filesystem
mkfs.xfs /dev/md0 -f -L datavolume
mkfs.xfs /dev/md1 -f -L logvolume
mkfs.xfs /dev/md2 -f -L tempdb
```

> [!NOTE]
> Es ist möglich, das XFS-Dateisystem so zu konfigurieren, dass Groß-/Kleinbuchstaben keine Rolle spielen, wenn das XFS-Volume erstellt und formatiert wird. Dabei handelt es sich um keine häufig genutzte Konfiguration im Linux-Ökosystem. Aus Kompatibilitätsgründen ist die Verwendung jedoch möglich.
>
> Beispiel: mkfs.xfs /dev/md0 -f -n version=ci -L datavolume
>
> Im Beispiel werden die Parameter `-n version=ci` verwendet, um das XFS-Dateisystem so zu konfigurieren, dass Groß-/Kleinbuchstaben keine Rolle spielen.

##### <a name="persistent-memory-filesystem-recommendation"></a>Empfehlungen für das PMEM-Dateisystem

Für die Konfiguration des Dateisystems für PMEM-Geräte sollte die Blockzuordnung für das zugrunde liegende Dateisystem 2 MB betragen. Weitere Informationen zu diesem Thema finden Sie unter [Technische Überlegungen](sql-server-linux-configure-pmem.md#technical-considerations).

#### <a name="disable-last-accessed-datetime-on-file-systems-for-sql-server-data-and-log-files"></a>Deaktivieren von Datum/Uhrzeit des letzten Zugriffs auf Dateisysteme für SQL Server-Daten- und -Protokolldateien

An das System angefügte Laufwerke müssen der Datei `/etc/fstab` hinzugefügt werden, um sicherzustellen, dass sie nach einem Neustart automatisch wieder eingebunden werden. Außerdem wird dringend empfohlen, den UUID (Universally Unique Identifier, universell eindeutiger Bezeichner) in `/etc/fstab` zu verwenden, um auf das Laufwerk und nicht auf den Gerätenamen (z. B. `/dev/sdc1`) zu verweisen.

Die Verwendung des Attributs **noatime** mit einem beliebigen Dateisystem, das zum Speichern von SQL Server-Daten- und -Protokolldateien verwendet wird, wird ausdrücklich empfohlen. Informationen zum Festlegen dieses Attributs finden Sie in der Linux-Dokumentation. Unten finden Sie ein Beispiel, wie die Option **noatime** für ein mit einer Azure-VM verknüpftes Volume aktiviert wird.

Unten sehen Sie den Eintrag für den Bereitstellungspunkt in **_/etc/fstab_* _.

```bash
UUID="xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" /data1 xfs,rw,attr2,noatime 0 0
```

Im Beispiel oben steht der UUID für das Gerät, das Sie mithilfe des _*_blkid_*_-Befehls finden können.

#### <a name="sql-server-and-forced-unit-access-fua-io-subsystem-capability"></a>FUA-EA-Subsystemfunktion (Forced Unit Access) in SQL Server

In bestimmten Versionen unterstützter Linux-Distributionen steht Unterstützung für die FUA-EA-Subsystemfunktion zur Verfügung, um für Dauerhaftigkeit für Daten zu sorgen. SQL Server verwendet die FUA-Funktion, um für hocheffiziente und zuverlässige Eingabe/Ausgabe für SQL Server-Workloads zu sorgen. Weitere Informationen zur Unterstützung für FUA durch Linux und den Auswirkungen auf SQL Server finden Sie im folgenden Blog: [SQL Server unter Linux: Informationen zu FUA (Forced Unit Access)](https://bobsql.com/sql-server-on-linux-forced-unit-access-fua-internals/)

Ab SUSE Linux Enterprise Server 12 SP5 und Red Hat Enterprise Linux 8.0 wird die FUA-Funktion im E/A-Subsystem unterstützt. Wenn Sie SQL Server 2017 CU6 und höher oder SQL Server 2019 verwenden, sollten Sie die folgende Konfiguration für eine leistungsstarke und effiziente E/A-Implementierung mit FUA von SQL Server verwenden.

Verwenden Sie die unten aufgeführten empfohlenen Konfigurationen, wenn die folgenden Bedingungen erfüllt sind.

- Sie verwenden SQL Server 2017 CU6 oder höher oder SQL Server 2019.
- Sie verwenden eine Linux-Distribution und -Version, die die FUA-Funktion unterstützt (Red Hat Enterprise Linux 8.0 oder höher oder SUSE Linux Enterprise Server 12 SP5).
- Sie nutzen ein Speichersubsystem und/oder Hardware, die die FUA-Funktion unterstützt und entsprechend konfiguriert ist.

Empfohlene Konfiguration:

1. Aktivieren Sie den Ablaufverfolgungsflag 3979 als Startparameter.
2. Verwenden Sie _ *mssql-conf** zum Konfigurieren von `control.writethrough = 1` und `control.alternatewritethrough = 0`.

Für beinahe alle anderen Konfigurationen, die die vorherigen Bedingungen nicht erfüllen, lautet die empfohlene Konfiguration wie folgt:

1. Aktivieren Sie das Ablaufverfolgungsflag 3982 als Startparameter (dies ist der Standardwert für SQL Server im Linux-Ökosystem), und sorgen Sie dabei dafür, dass das Ablaufverfolgungsflag 3979 nicht als Startparameter aktiviert ist.
2. Verwenden Sie **mssql-conf** zum Konfigurieren von `control.writethrough = 1` und `control.alternatewritethrough = 1`.

### <a name="kernel-and-cpu-settings-for-high-performance"></a>Kerneleinstellungen und CPU-Einstellungen für hohe Leistung

Im folgenden Abschnitt werden die für das Linux-Betriebssystem empfohlenen Einstellungen erläutert, um bei einer SQL Server-Installation hohe Leistung und einen hohen Durchsatz zu erzielen. Der Prozess zum Konfigurieren dieser Einstellungen wird in der Linux-Dokumentation beschrieben. Wenn [**_Tuned_* _](https://tuned-project.org) wie beschrieben verwendet wird, unterstützt Sie dies bei der Konfiguration vieler der unten beschriebenen CPUs und Kernelkonfigurationen.

#### <a name="using-__tuned__-to-configure-kernel-settings"></a>Verwenden von _*_Tuned_*_ zum Konfigurieren von Kerneleinstellungen

Für Red Hat Enterprise Linux-Benutzer (RHEL) konfiguriert das [Tuned](https://tuned-project.org)-Profil für Durchsatz und Leistung einige Kerneleinstellungen und CPU-Einstellungen automatisch (mit Ausnahme von C-Status). Ab RHEL 8.0 bietet ein _*_Tuned_*_-Profil namens _ *mssql**, das in Zusammenarbeit mit Red Hat entwickelt wurde, genauer abgestimmte Linux-Leistungsoptimierungen für SQL Server-Workloads. Dieses Profil enthält das RHEL-Profil „throughput-performance“. Die Definitionen dieses Profils werden im Folgenden veranschaulicht, damit Sie es anderen Linux-Distributionen und RHEL-Releases ohne dieses Profil gegenüberstellen können.

Für SUSE Linux Enterprise Server 12 SP5, Ubuntu 18.04 und Red Hat Enterprise Linux 7.x kann das **_Tuned_ *_-Paket manuell installiert werden. Es kann verwendet werden, um das _* mssql**-Profil wie unten beschrieben zu erstellen und zu konfigurieren.

##### <a name="proposed-linux-settings-using-a-tuned-mssql-profile"></a>Empfohlene Linux-Einstellungen mit einem mssql-Tuned-Profil

```bash
#
# A Tuned configuration for SQL Server on Linux
#

[main]
summary=Optimize for Microsoft SQL Server
include=throughput-performance

[cpu]
force_latency=5

[sysctl]
vm.swappiness = 1
vm.dirty_background_ratio = 3
vm.dirty_ratio = 80
vm.dirty_expire_centisecs = 500
vm.dirty_writeback_centisecs = 100
vm.transparent_hugepages=always
# For multi-instance SQL deployments, use
# vm.transparent_hugepages=madvise
vm.max_map_count=1600000
net.core.rmem_default = 262144
net.core.rmem_max = 4194304
net.core.wmem_default = 262144
net.core.wmem_max = 1048576
kernel.numa_balancing=0
kernel.sched_latency_ns = 60000000
kernel.sched_migration_cost_ns = 500000
kernel.sched_min_granularity_ns = 15000000
kernel.sched_wakeup_granularity_ns = 2000000
```

Zum Aktivieren dieses Tuned-Profils speichern Sie diese Definitionen in einer Datei namens **tuned.conf** im Ordner `/usr/lib/tuned/mssql`, und aktivieren Sie das Profil mithilfe der folgenden Befehle:

```bash
chmod +x /usr/lib/tuned/mssql/tuned.conf
tuned-adm profile mssql
```

Überprüfen Sie mit dem folgenden Befehl, ob das Profil aktiviert wurde:

```bash
tuned-adm active
```

oder

```bash
tuned-adm list
```

#### <a name="cpu-settings-recommendation"></a>Empfehlung für CPU-Einstellungen

In der folgenden Tabelle finden Sie Empfehlungen für die CPU-Einstellungen:

| Einstellung | value | Weitere Informationen |
|---|---|---|
| CPU frequency governor (Kontrolle der CPU-Häufigkeit) | Leistung | Dokumentation zum Befehl **cpupower** |
| ENERGY_PERF_BIAS | Leistung | Dokumentation zum Befehl **x86_energy_perf_policy** |
| min_perf_pct | 100 | Dokumentation zum Status „intel p“ |
| C-States (C-Status) | C1 only (Nur C1) | In der Linux- oder Systemdokumentation erhalten Sie Informationen dazu, wie Sie sicherstellen können, dass die Einstellung „C-States“ (C-Status) auf „C1 only“ (Nur C1) festgelegt ist. |

Wenn **_Tuned_ *_ wie zuvor beschrieben verwendet wird, werden die Einstellungen „CPU frequency governor“, „ENERGY_PERF_BIAS“ und „min_perf_pct“ automatisch entsprechend konfiguriert. Dies liegt daran, dass das Profil für Durchsatz und Leistung als Basis für das _* mssql**-Profil verwendet wird. C-Statusparameter müssen manuell entsprechend der von Linux oder dem Systemvertriebspartner bereitgestellten Dokumentation konfiguriert werden.

#### <a name="disk-settings-recommendations"></a>Empfehlungen zu Datenträgereinstellungen

In der folgenden Tabelle finden Sie Empfehlungen für die Datenträgereinstellungen:

| Einstellung | value | Weitere Informationen |
|---|---|---|
| disk `readahead` | 4096 | Dokumentation zum Befehl `blockdev` |
| sysctl-Einstellungen | kernel.sched_min_granularity_ns = 10.000.000<br/>kernel.sched_wakeup_granularity_ns = 15.000.000<br/>vm.dirty_ratio = 40<br/>vm.dirty_background_ratio = 10<br/>vm.swappiness = 1 | Dokumentation zum Befehl **sysctl** |

**Beschreibung:**

- **vm.swappiness:** Dieser Parameter steuert die relative Gewichtung für den Austausch von Runtimearbeitsspeicher durch Begrenzung des Kernels. So können Arbeitsspeicherseiten des SQL Server-Prozesses ausgetauscht werden.

- **vm.dirty_\** _: Schreibzugriffe auf SQL Server-Dateien werden nicht zwischengespeichert, um die Anforderungen an Datenintegrität zu erfüllen. Diese Parameter ermöglichen eine effiziente asynchrone Schreibleistung und senken die E/A-Speicherauswirkung von Cacheschreibvorgängen unter Linux, indem ermöglicht wird, dass der Umfang für das Zwischenspeichern eine ausreichende Größe aufweist und Leervorgänge gedrosselt werden.

- _*kernel.sched_\**_: Diese Parameterwerte sind die aktuelle Empfehlung für das Anpassen des CFS-Algorithmus (Completely Fair Scheduling) im Linux-Kernel, um den Durchsatz des Netzwerks und E/A-Speicheraufrufe zu optimieren. Dabei wird vorzeitige Entfernung während Prozessen und die Wiederaufnahme von Threads berücksichtigt.

Die Verwendung des *_*_Tuned_*-Profils *mssql*_* konfiguriert die Einstellungen _*vm.swappiness**, **vm.dirty_\* *_ und _* kernel.sched_\**_. Die `readahead`-Datenträgerkonfiguration mithilfe des `blockdev`-Befehls erfolgt pro Gerät und muss manuell ausgeführt werden.

#### <a name="kernel-setting-auto-numa-balancing-for-multi-node-numa-systems"></a>Kernel-Einstellung für den automatischen NUMA-Ausgleich für NUMA-Systeme mit mehreren Knoten

Wenn Sie SQL Server auf einem _ *NUMA**-System mit mehreren Knoten installieren, ist die folgende **kernel.numa_balancing**-Kerneleinstellung standardmäßig aktiviert. Deaktivieren Sie den automatischen NUMA-Ausgleich für das **NUMA**-System mit mehreren Knoten, damit SQL Server auf diesem mit bestmöglicher Effizienz arbeiten können:

```bash
sysctl -w kernel.numa_balancing=0
```

Die Verwendung des **_Tuned_ *_-Profils **mssql** konfiguriert die Option _* kernel.numa_balancing**.

#### <a name="kernel-settings-for-virtual-address-space"></a>Kerneleinstellungen für virtuelle Adressräume

Die Standardeinstellung für **vm.max_map_count** (65536) ist für eine SQL Server-Installation möglicherweise nicht hoch genug. Ändern Sie aus diesem Grund für eine SQL Server-Bereitstellung den Wert **vm.max_map_count** mindestens in 262144, und lesen Sie den Abschnitt [Empfohlene Linux-Einstellungen für ein mssql-Tuned-Profil](#proposed-linux-settings-using-a-tuned-mssql-profile), um weitere Informationen zu Optimierungen für diese Kernelparameter zu erhalten. Der Maximalwert für „.max_map_count“ ist 2147483647.

```bash
sysctl -w vm.max_map_count=1600000
```

Die Verwendung des **_Tuned_ *_-Profils **mssql** konfiguriert die Option _* vm.max_map_count**.

#### <a name="leave-transparent-huge-pages-thp-enabled"></a>Lassen Sie die Option „Transparent Huge Pages“ aktiviert.

Bei den meisten Linux-Installationen sollte diese Option standardmäßig aktiviert sein. Es wird empfohlen, dies nicht zu ändern, damit die Leistung konstant gut bleibt. Bei hoher Arbeitsspeicherauslastung in SQL Server-Bereitstellungen mit mehreren Instanzen (z. B. bei SQL Server-Ausführung mit anderen anspruchsvollen Anwendungen auf dem Server) wird jedoch empfohlen, dass Sie die Leistung Ihrer Anwendungen nach Ausführung des folgenden Befehls testen:

```bash
echo madvise > /sys/kernel/mm/transparent_hugepage/enabled
```

Alternativ können Sie das **mssql** * *-_Tuned_* _-Profil mit der folgenden Zeile versehen:

```bash
vm.transparent_hugepages=madvise
```

Aktivieren Sie das Profil _ *mssql** außerdem nach der Änderung:

```bash
tuned-adm off
tuned-adm profile mssql
```

Die Verwendung des **_Tuned_ *_-Profils **mssql** konfiguriert die Option _* transparent_hugepage**.

#### <a name="additional-advanced-kernelos-configuration"></a>Zusätzliche erweiterte Kernel-/Betriebssystemkonfiguration

1. Für eine optimale E/A-Speicherleistung wird die Verwendung einer Planung mit mehreren Warteschlagen für Blockgeräte empfohlen. So kann die Leistung der Blockebene gut mit schnellen SSD-Datenträgern und Systemen mit mehreren Kernen skaliert werden. In der Dokumentation können Sie herausfinden, ob diese Option für Ihre Linux-Distribution standardmäßig aktiviert ist. In den meisten anderen Fällen wird die Option durch Starten des Kernels mit **scsi_mod.use_blk_mq=y** aktiviert. Möglicherweise finden Sie in der Dokumentation zur verwendeten Linux-Distribution aber auch weitere Anweisungen dazu. Dies ist für den Linux-Upstreamkernel konsistent.

1. Da EA mit mehreren Pfaden oft für SQL Server-Bereitstellungen verwendet wird, sollte das Ziel mit mehreren Pfaden für die Gerätezuordnung (Device Mapper, DM) ebenfalls so konfiguriert werden, dass die `blk-mq`-Infrastruktur verwendet wird, indem die Kernelstartoption **dm_mod.use_blk_mq=y** aktiviert wird. Der Standardwert lautet `n` (Deaktiviert). Diese Einstellung senkt den Sperraufwand auf der DM-Ebene, wenn die zugrunde liegenden SCSI-Geräte `blk-mq` verwenden. In der Dokumentation zur verwendeten Linux-Distribution erhalten Sie weitere Anweisungen zur Konfiguration.

#### <a name="configure-swapfile"></a>Konfigurieren der Auslagerungsdatei

Stellen Sie sicher, dass Sie über eine ordnungsgemäß konfigurierte Auslagerungsdatei verfügen, damit keine Probleme mit dem Arbeitsspeicher auftreten. In der Linux-Dokumentation erhalten Sie Informationen über die Erstellung und ordnungsgemäße Größenanpassung von Auslagerungsdateien.

#### <a name="virtual-machines-and-dynamic-memory"></a>Virtuelle Computer und dynamischer Arbeitsspeicher

Wenn Sie SQL Server für Linux auf einer VM ausführen, stellen Sie sicher, dass Sie entsprechende Optionen auswählen, um dem für die VM reservierten Arbeitsspeicher gerecht zu werden. Verwenden Sie keine Features wie Hyper-V Dynamic Memory.

## <a name="sql-server-configuration"></a>SQL Server-Konfiguration

Es wird empfohlen, nach der Installation von SQL Server für Linux die folgenden Konfigurationsaufgaben auszuführen, um eine optimale Leistung für Ihre Anwendung zu erzielen.

### <a name="best-practices"></a>Bewährte Methoden

- **Verwenden von PROCESS AFFINITY für Knoten und/oder CPUs**

   Es wird empfohlen, `ALTER SERVER CONFIGURATION` zu verwenden, um `PROCESS AFFINITY` für alle **NUMANODE**-Elemente und/oder CPUs festzulegen, die Sie für SQL Server (in der Regel für alle Knoten und CPUs) unter Linux verwenden. Die Prozessoraffinität hilft dabei, das Verhalten von Linux und SQL effizient zu planen. Die Verwendung der Option **NUMANODE** ist die einfachste Methode. Beachten Sie, dass Sie **PROCESS AFFINITY** auch dann verwenden sollten, wenn auf Ihrem Computer nur ein einzelner NUMA-Knoten vorhanden ist. Weitere Informationen zum Festlegen von [PROCESS AFFINITY](../t-sql/statements/alter-server-configuration-transact-sql.md) finden Sie im Artikel **ALTER SERVER CONFIGURATION (Transact-SQL)** .

- **Konfigurieren mehrerer tempdb-Datendateien**

   Da die Installation von SQL Server für Linux keine Option zum Konfigurieren mehrerer tempdb-Dateien umfasst, empfiehlt es sich, erst nach der Installation die tempdb-Datendateien zu erstellen. Weitere Informationen finden Sie im Artikel [Empfehlungen zum Reduzieren von Konflikten bei der Zuweisung in tempdb-Datenbank für SQL Server](https://support.microsoft.com/help/2154845/recommendations-to-reduce-allocation-contention-in-sql-server-tempdb-d).

### <a name="advanced-configuration"></a>Erweiterte Konfiguration

Die folgenden Empfehlungen stellen optionale Konfigurationseinstellungen dar, die Sie nach der Installation von SQL Server für Linux durchführen können. Diese Optionen basieren auf den Anforderungen Ihrer Workload und der Konfiguration Ihres Linux-Betriebssystems.

- **Festlegen eines Arbeitsspeicherlimits mithilfe von mssql-conf**

   Damit immer genügend physischer Speicherplatz für Linux vorhanden ist, verwendet der SQL Server-Prozess standardmäßig nur 80 Prozent des physischen Speichers. Bei großen Systemen können 20 Prozent einen beachtlichen Unterschied darstellen. Bei einem System mit 1 TB RAM werden durch diese Standardeinstellung ca. 200 GB RAM freigelassen. In diesem Fall sollten Sie das Arbeitsspeicherlimit auf einen höheren Wert festlegen. Weitere Informationen finden Sie in der Dokumentation zum Tool **mssql-config** und der Einstellung [memory.memorylimitmb](sql-server-linux-configure-mssql-conf.md#memorylimit), die den für SQL Server sichtbaren Speicherplatz (in MB) steuert.

   Wenn Sie diese Einstellung ändern, achten Sie darauf, diesen Wert nicht zu hoch festzulegen. Wenn nicht genügend Arbeitsspeicher frei ist, können Probleme mit dem Linux-Betriebssystem und anderen Linux-Anwendungen auftreten.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu SQL Server-Features, die die Leistung verbessern, finden Sie unter [Erste Schritte mit den Leistungsfeatures](sql-server-linux-performance-get-started.md).

Weitere Informationen zu SQL Server für Linux finden Sie in der [Übersicht für SQL Server für Linux](sql-server-linux-overview.md).
