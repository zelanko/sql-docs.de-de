---
title: Leistung, bewährte Methoden für SQL Server unter Linux | Microsoft-Dokumentation
description: In diesem Artikel werden bewährte Methoden für Leistung und Richtlinien für die Ausführung von SQL Server 2017 unter Linux bieten.
author: rgward
ms.author: bobward
manager: craigg
ms.date: 09/14/2017
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: f27cda67baa5d4101f94a8351bacd1ef3ecbff05
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39101138"
---
# <a name="performance-best-practices-and-configuration-guidelines-for-sql-server-on-linux"></a>Bewährte Methoden für Leistung und von Konfigurationsrichtlinien für das SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dieser Artikel enthält bewährte Methoden und Empfehlungen zum Maximieren der Leistung von datenbankanwendungen, die mit SQL Server unter Linux verbinden. Diese Empfehlungen gelten speziell für die Ausführung auf der Linux-Plattform. Alle normalen SQL Server-Empfehlungen, wie z. B. Indexentwurf, gelten weiterhin.

Die folgenden Richtlinien enthalten Empfehlungen zum Konfigurieren von SQL Server und Linux-Betriebssystem.

## <a name="sql-server-configuration"></a>SQL Server-Konfiguration

Es wird empfohlen, um die folgenden Konfigurationsaufgaben ausführen, nach der Installation von SQL Server für Linux, um die optimale Leistung für Ihre Anwendung zu erzielen.

### <a name="best-practices"></a>Bewährte Methoden

- **Verwenden Sie die PROZESSAFFINITÄT für CPUs und/oder den Knoten**

   Es wird empfohlen, verwenden Sie `ALTER SERVER CONFIGURATION` festzulegende `PROCESS AFFINITY` für alle der **NUMANODEs** und/oder CPUs Sie verwenden für SQL Server (in der Regel für alle Knoten und CPUs) auf Linux-Betriebssystem. Prozessor-Affinität kann effizient Linux und Planen von SQL-Verhalten zu verwalten. Mithilfe der **NUMANODE** Option ist die einfachste Methode. Beachten Sie, verwenden Sie **PROZESSAFFINITÄT** auch wenn Sie nur einen einzelnen NUMA-Knoten auf Ihrem Computer verfügen.  Finden Sie unter den [ALTER SERVER CONFIGURATION](../t-sql/statements/alter-server-configuration-transact-sql.md) Dokumentation für Weitere Informationen zum Festlegen von **PROZESSAFFINITÄT**.

- **Konfigurieren Sie mehrere Tempdb-Datendateien**

   Da es sich bei einer SQL Server auf Linux-Installation keine Option zum Konfigurieren mehrerer Tempdb-Dateien bietet, wird empfohlen, die Sie berücksichtigen, erstellen mehrere Tempdb-Datendateien, nach der Installation. Weitere Informationen finden Sie in der Anleitung im Artikel [Empfehlungen zur zuweisungskonflikt in SQL Server-Tempdb-Datenbank zu vermeiden](https://support.microsoft.com/en-us/help/2154845/recommendations-to-reduce-allocation-contention-in-sql-server-tempdb-d).

### <a name="advanced-configuration"></a>Erweiterte Konfiguration

Die folgenden Empfehlungen sind optionale-Konfigurationseinstellungen, die Sie festlegen können, ob nach der Installation von SQL Server unter Linux ausführen. Diese Optionen basieren auf den Anforderungen Ihrer Workload und die Konfiguration von Ihrem Linux-Betriebssystem.

- **Legen Sie ein Arbeitsspeicherlimit mit Mssql-conf**

   Um sicherzustellen, dass genügend freier physischer Arbeitsspeicher für das Linux-Betriebssystem vorhanden ist, werden nur 80 % des physischen Arbeitsspeichers von SQL Server-Prozess wird standardmäßig verwendet. Für einige Systeme, die große Menge an physischen RAM, 20 % möglicherweise, eine erhebliche Anzahl. Beispielsweise würde auf einem System mit 1 TB RAM, die Standardeinstellung beibehalten ca. 200 GB RAM nicht verwendete. In diesem Fall empfiehlt es sich möglicherweise so konfigurieren Sie die Begrenzung der Menge auf einen höheren Wert. Finden Sie in der Dokumentation für die **Mssql-Conf** Tool und die [memory.memorylimitmb](sql-server-linux-configure-mssql-conf.md#memorylimit) festlegen, die steuert, des Arbeitsspeichers für SQL Server (in Einheiten von MB) sichtbar.

   Wenn Sie diese Einstellung zu ändern, achten Sie darauf, dass Sie nicht auf ein zu hoher Wert festgelegt. Wenn Sie nicht genügend Arbeitsspeicher verfügbar ist, können Sie Probleme mit Linux-Betriebssystem und anderen Linux-Anwendungen auftreten.

## <a name="linux-os-configuration"></a>Linux-Betriebssystem-Konfiguration

Erwägen Sie die folgenden Linux-Betriebssystem-Konfigurationseinstellungen, um die beste Leistung für SQL Server-Installationen auftreten.

### <a name="kernel-settings-for-high-performance"></a>Kerneleinstellungen für eine hohe Leistung
Dies sind die empfohlenen Linux-Betriebssystem-Einstellungen im Zusammenhang mit hoher Leistung und Durchsatz für eine SQL Server-Installation. Finden Sie in Ihrer Linux-Betriebssystem-Dokumentation für den Prozess zum Konfigurieren dieser Einstellungen.



> [!Note]
> Für Benutzer von Red Hat Enterprise Linux (RHEL) wird das Profil für die durchsatzleistung diese Einstellungen automatisch (mit Ausnahme von C-Status) konfiguriert.

Die folgende Tabelle enthält Empfehlungen für die CPU-Einstellungen:

| Einstellung | value | Weitere Informationen |
|---|---|---|
| CPU-Frequenz Ressourcenkontrolle | Leistung | Finden Sie unter den **Cpupower** Befehl |
| ENERGY_PERF_BIAS | Leistung | Finden Sie unter den **x86_energy_perf_policy** Befehl |
| min_perf_pct | 100 | Finden Sie in der Dokumentation auf Intel-p-Status |
| C-Status | Nur C1 | Finden Sie unter der Dokumentation zu Linux oder System dazu, wie ein, um sicherzustellen, dass C-Status nur das C1 festgelegt ist |

Die folgende Tabelle enthält Empfehlungen für die datenträgereinstellungen:

| Einstellung | value | Weitere Informationen |
|---|---|---|
| Datenträger-Read-Aheads | 4096 | Finden Sie unter den **Blockdev** Befehl |
| Sysctl-Einstellungen | Kernel.sched_min_granularity_ns = 10000000<br/>Kernel.sched_wakeup_granularity_ns 15000000 =<br/>vm.dirty_ratio = 40<br/>vm.dirty_background_ratio = 10<br/>vm.swappiness=10 | Finden Sie unter den **Sysctl** Befehl |

### <a name="kernel-setting-auto-numa-balancing-for-multi-node-numa-systems"></a>Kernel-Einstellung automatisch Numa Lastenausgleich für NUMA-Systemen mit mehreren Knoten

Bei der Installation von SQL Server auf mehreren Knoten **NUMA** Systeme, die folgenden **kernel.numa_balancing** Kernel-Einstellung ist standardmäßig aktiviert. Um SQL Server zu verarbeitende maximale Effizienz ermöglichen eine **NUMA** System, deaktivieren automatisch Numa Lastenausgleich auf einem NUMA-System mit mehreren Knoten:

```bash
sysctl -w kernel.numa_balancing=0
```

### <a name="kernel-settings-for-virtual-address-space"></a>Kerneleinstellungen für den virtuellen Adressraum.

Die Standardeinstellung von **vm.max_map_count** (was 65536 ist) möglicherweise nicht hoch genug ist, für eine SQL Server-Installation. Ändern Sie diesen Wert (das obere Limit erreicht ist), auf 256 KB.

```bash
sysctl -w vm.max_map_count=262144
```

### <a name="disable-last-accessed-datetime-on-file-systems-for-sql-server-data-and-log-files"></a>Deaktivieren des letzten Zugriffs auf Datum/Uhrzeit in Dateisystemen für SQL Server Daten und Protokolldateien

Verwenden der **Noatime** Attribut mit einem beliebigen Dateisystem, das zum Speichern von SQL Server-Daten und Protokolldateien verwendet wird. Finden Sie in der Linux-Dokumentation zum Festlegen dieses Attributs.

### <a name="leave-transparent-huge-pages-thp-enabled"></a>Lassen Sie Transparent Huge Pages (THP) aktiviert

Bei den meisten Linux-Installationen sollten diese Option standardmäßig auf, auf. Es wird empfohlen, für die konsistenteste Leistungsverhalten zu bieten, diese Konfigurationsoption aktiviert lassen.

### <a name="swapfile"></a>Auslagerungsdatei

Stellen Sie sicher, dass man auf eine ordnungsgemäß konfigurierte Auslagerungsdatei, einer unzureichenden Arbeitsspeicher zu vermeiden. In der Dokumentation für das Erstellen und die ordnungsgemäße Größe einer Auslagerungsdatei Linux.

### <a name="virtual-machines-and-dynamic-memory"></a>Virtuelle Computer und dynamischer Arbeitsspeicher

Wenn Sie SQL Server unter Linux auf einem virtuellen Computer ausführen, stellen Sie sicher, dass Sie Optionen auswählen, beheben Sie die Menge an Arbeitsspeicher für den virtuellen Computer reserviert. Verwenden Sie keine Features wie Hyper-V Dynamic Memory.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu SQL Server-Funktionen, die Leistung verbessern, finden Sie unter [erste Schritte mit Leistungsfeatures](sql-server-linux-performance-get-started.md).

Weitere Informationen zu SQL Server unter Linux finden Sie unter [Übersicht über SQL Server unter Linux](sql-server-linux-overview.md).
