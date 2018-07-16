---
title: Konfigurieren von SQLServer zur Verwendung von Soft-NUMA (SQLServer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/12/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- NUMA
- non-uniform memory access
ms.assetid: 1af22188-e08b-4c80-a27e-4ae6ed9ff969
caps.latest.revision: 38
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 434e569b17fa70b6f6b3f4763e54e08e271dc99b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37279558"
---
# <a name="configure-sql-server-to-use-soft-numa-sql-server"></a>Konfigurieren von SQL Server zur Verwendung von Soft-NUMA (SQL Server)
Moderne Prozessoren verfügen über mehrere bis viele Kerne pro Socket. Jeder Socket wird in der Regel als ein einzelner NUMA-Knoten dargestellt. Die SQL Server-Datenbank-Engine partitioniert pro NUMA-Knoten verschiedene interne Strukturen und Dienstthreads für Partitionen. Erhöht sich mit Prozessoren, die 10 oder mehr Kernen pro Socket enthält, verwenden die Software NUMA (Soft-NUMA), um die Hardware-NUMA-Knoten in der Regel aufgeteilt, Skalierbarkeit und Leistung.   

> [!NOTE]
> Hot-Add-Prozessoren werden von Soft-NUMA nicht unterstützt.
  
## <a name="automatic-soft-numa"></a>Automatischer Soft-NUMA

Ab SQL Server 2014 Service Pack 2, wenn die Datenbank-Engine-Server mehr als 8 physische Prozessoren beim Start erkennt, werden Soft-NUMA-Knoten automatisch erstellt, wenn das Ablaufverfolgungsflag 8079 als Startparameter aktiviert ist. Prozessorkerne mit Hyperthreading werden nicht berücksichtigt beim Zählen der physischer Prozessoren. Wenn die Anzahl der physischen Prozessoren, die erkannt, mehr als 8 pro Socket ist, wird die Datenbank-Engine-Dienst Soft-NUMA-Knoten erstellt, die im Idealfall enthalten 8 Kerne, jedoch kann auf 5 oder bis zu 9 logische Prozessoren pro Knoten ausfallen. Die Größe des Hardwareknotens kann durch eine CPU-Affinitätsmaske eingeschränkt werden. Die Anzahl von NUMA-Knoten wird nie die maximale Anzahl von unterstützten NUMA-Knoten übersteigen.

Ohne das Ablaufverfolgungsflag wird Soft-NUMA standardmäßig deaktiviert. Sie können Soft-NUMA verwenden das Ablaufverfolgungsflag 8079. Nach der Änderung des Werts dieser Einstellung ist ein Neustart der Datenbank-Engine erforderlich, damit diese wirksam wird.

Die folgende Abbildung zeigt die Art der Informationen zu Soft-NUMA, die Sie in der SQL Server-Fehlerprotokoll angezeigt wird, wenn SQL Server NUMA-hardwareknoten mit mehr als 8 logische Prozessoren erkennt und das Ablaufverfolgungsflag 8079 aktiviert ist.

![Soft-NUMA](./media/soft-numa-sql-server/soft-numa.PNG)

## <a name="manual-soft-numa"></a>Manueller Soft-NUMA
  
So konfigurieren Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] um Soft-NUMA manuell verwenden zu können, müssen Sie die Registrierung, um eine Affinitätsmaske für die Knoten-Konfiguration hinzufügen bearbeiten. Die Soft-NUMA-Maske kann als binärer Eintrag, als DWORD-Registrierungseintrag (hexadezimal oder dezimal) oder als QWORD-Registrierungseintrag (hexadezimal oder dezimal) angegeben werden. Verwenden Sie QWORD- oder BINARY-Registrierungseinträge, um mehr als die ersten 32 CPUs zu konfigurieren. (Die Verwendung von QWORD-Werten ist in Versionen vor Version [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] nicht möglich.) Zum Konfigurieren von Soft-NUMA müssen Sie [!INCLUDE[ssDE](../../includes/ssde-md.md)] neu starten.  
  
> [!TIP]  
>  Die Nummerierung der CPUs beginnt mit 0.  
  
 [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
 Betrachten Sie das folgende Beispiel. Ein Computer mit acht CPUs verfügt über keine NUMA-Hardware. Drei Soft-NUMA-Knoten werden konfiguriert. [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz A wird für die Verwendung der CPUs 0 bis 3 konfiguriert. Eine zweite [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz wird installiert und für die Verwendung der CPUs 4 bis 7 konfiguriert. Das Beispiel kann wie folgt visuell dargestellt werden:  
  
 `CPUs          0  1  2  3  4  5  6  7`  
  
 `Soft-NUMA   <-N0--><-N1-><----N2---->`  
  
 `SQL Server  <instance A ><instance B>`  
  
 Instanz A, auf der ein hohes Maß an E/A-Aktivität stattfindet, verfügt nun über zwei E/A-Threads und einen Thread für LAZY WRITER-Prozesse (verzögertes Schreiben), während Instanz B, auf der prozessorintensive Vorgänge ausgeführt werden, nur über einen E/A-Thread und einen Thread für LAZY WRITER-Prozesse verfügt. Den Instanzen können zwar unterschiedliche Mengen an Arbeitsspeicher zugewiesen werden, aber im Unterschied zu Hardware-NUMA erhalten beide Instanzen den Arbeitsspeicher aus demselben Betriebssystem-Speicherblock und es ist keine Speicher-Prozessor-Affinität vorhanden.  
  
 Der LAZY WRITER-Thread ist an die SQL OS-Sicht der physischen NUMA-Arbeitsspeicherknoten gebunden. Daher entsprechen die physischen NUMA-Knoten der Hardware der Anzahl der erstellten LAZY WRITER-Threads. Weitere Informationen finden Sie unter [How It Works: Soft NUMA, I/O Completion Thread, Lazy Writer Workers and Memory Nodes](http://blogs.msdn.com/b/psssql/archive/2010/04/02/how-it-works-soft-numa-i-o-completion-thread-lazy-writer-workers-and-memory-nodes.aspx).  
  
> [!NOTE]  
>  Die **Soft-NUMA** -Registrierungsschlüssel werden nicht kopiert, wenn Sie eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="set-the-cpu-affinity-mask"></a>Festlegen der CPU-Affinitätsmaske  
  
1.  Führen Sie auf Instanz A die folgende Anweisung aus, um die Instanz durch Festlegen der CPU-Affinitätsmaske für die Verwendung der CPUs 0, 1, 2 und 3 zu konfigurieren:  
  
    ```  
    ALTER SERVER CONFIGURATION   
    SET PROCESS AFFINITY CPU=0 TO 3;  
    ```  
  
2.  Führen Sie auf Instanz B die folgende Anweisung aus, um die Instanz durch Festlegen der CPU-Affinitätsmaske für die Verwendung der CPUs 4, 5, 6 und 7 zu konfigurieren:  
  
    ```  
    ALTER SERVER CONFIGURATION   
    SET PROCESS AFFINITY CPU=4 TO 7;  
    ```  
  
### <a name="map-soft-numa-nodes-to-cpus"></a>Zuordnen von Soft-NUMA-Knoten zu den CPUs  
  
-   Fügen Sie mithilfe des Registrierungs-Editors (regedit.exe) die folgenden Registrierungsschlüssel hinzu, um den CPUs 0 und 1 den Soft-NUMA-Knoten 0, den CPUs 2 und 3 den Soft-NUMA-Knoten 1 und den CPUs 4, 5, 6 und 7 den Soft-NUMA-Knoten 2 zuzuordnen.  
  
     Legen Sie für das folgende Beispiel einen DL580 G9-Server mit 18 Kernen pro Fassung (in 4 Fassungen) zugrunde, wobei jede Fassung eine eigene K-Gruppe darstellt. Eine Soft-NUMA-Konfiguration, die Sie dafür erstellen, könnte etwa so aussehen. (6 Kerne pro Knoten, 3 Knoten pro Gruppe, 4 Gruppen).  
  
    |Beispiel für einen [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] -Server mit mehreren K-Gruppen|Typ|Wertname|Wertdaten|  
    |------------------------------------------------------------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node0|DWORD|CPUMask|0x3F|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node0|DWORD|Gruppieren|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node1|DWORD|CPUMask|0x0fc0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node1|DWORD|Gruppieren|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node2|DWORD|CPUMask|0x3f000|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node2|DWORD|Gruppieren|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node3|DWORD|CPUMask|0x3F|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node3|DWORD|Gruppieren|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node4|DWORD|CPUMask|0x0fc0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node4|DWORD|Gruppieren|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node5|DWORD|CPUMask|0x3f000|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node5|DWORD|Gruppieren|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node6|DWORD|CPUMask|0x3F|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node6|DWORD|Gruppieren|2|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node7|DWORD|CPUMask|0x0fc0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node7|DWORD|Gruppieren|2|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node8|DWORD|CPUMask|0x3f000|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node8|DWORD|Gruppieren|2|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node9|DWORD|CPUMask|0x3F|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node9|DWORD|Gruppieren|3|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node10|DWORD|CPUMask|0x0fc0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node10|DWORD|Gruppieren|3|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node11|DWORD|CPUMask|0x3f000|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node11|DWORD|Gruppieren|3|  
  
     Zusätzliche Beispiele:  
  
    |[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|Typ|Wertname|Wertdaten|  
    |---------------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node0|DWORD|CPUMask|0x03|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node0|DWORD|Gruppieren|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node1|DWORD|CPUMask|0x0c|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node1|DWORD|Gruppieren|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node2|DWORD|CPUMask|0xf0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node2|DWORD|Gruppieren|0|  
  
    > [!TIP]  
    >  Verwenden Sie zum Angeben der CPUs 60 bis 63 den QWORD-Wert F000000000000000 oder den BINARY-Wert 1111000000000000000000000000000000000000000000000000000000000000.  
  
    |[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|Typ|Wertname|Wertdaten|  
    |---------------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node0|DWORD|CPUMask|0x03|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node0|DWORD|Gruppieren|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node1|DWORD|CPUMask|0x0c|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node1|DWORD|Gruppieren|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node2|DWORD|CPUMask|0xf0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node2|DWORD|Gruppieren|0|  
  
    |SQL Server 2008 R2|Typ|Wertname|Wertdaten|  
    |------------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node0|DWORD|CPUMask|0x03|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node0|DWORD|Gruppieren|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node1|DWORD|CPUMask|0x0c|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node1|DWORD|Gruppieren|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node2|DWORD|CPUMask|0xf0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node2|DWORD|Gruppieren|0|  
  
    |SQL Server 2008|Typ|Wertname|Wertdaten|  
    |---------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node0|DWORD|CPUMask|0x03|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node1|DWORD|CPUMask|0x0c|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node2|DWORD|CPUMask|0xf0|  
  
    |SQL Server 2005|Typ|Wertname|Wertdaten|  
    |---------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\90\NodeConfiguration\Node0|DWORD|CPUMask|0x03|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\90\NodeConfiguration\Node1|DWORD|CPUMask|0x0c|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\90\NodeConfiguration\Node2|DWORD|CPUMask|0xf0|  
  
## <a name="see-also"></a>Siehe auch  
 [Zuordnen von TCP/IP-Ports zu NUMA-Knoten &#40;SQL Server&#41;](map-tcp-ip-ports-to-numa-nodes-sql-server.md)   
 [Affinitätsmaske (Serverkonfigurationsoption)](affinity-mask-server-configuration-option.md)   
 [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql)  
  
  
