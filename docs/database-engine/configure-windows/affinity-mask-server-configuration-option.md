---
title: Affinitätsmaske (Serverkonfigurationsoption)
description: In diesem Artikel erfahren Sie mehr über die Option „affinity mask“ in SQL Server. Außerdem finden Sie ein Beispiel, in dem Prozessoren mithilfe der Affinitätsmaske an bestimmte Threads gebunden werden.
ms.prod: sql
ms.prod_service: high-availability
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- default affinity mask option
- reloading processor cache
- processor cache [SQL Server]
- CPU [SQL Server], licensing
- deferred process call
- affinity mask option
- processor affinity [SQL Server]
- SMP
- DPC
ms.assetid: 5823ba29-a75d-4b3e-ba7b-421c07ab3ac1
author: markingmyname
ms.author: maghan
ms.reviewer: mikeray
ms.custom: ''
ms.date: 06/11/2020
ms.openlocfilehash: 94f8406af013bc0720bc16063d1a9881eda94c5a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715595"
---
# <a name="affinity-mask-server-configuration-option"></a>Affinitätsmaske (Serverkonfigurationsoption)

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

> [!NOTE]
> [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen [ALTER SERVER CONFIGURATION (Transact-SQL)](../../t-sql/statements/alter-server-configuration-transact-sql.md).

Zum Ausführen von Multitasking verschiebt [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows gelegentlich Prozessthreads zwischen verschiedenen Prozessoren. Obwohl dieses Vorgehen hinsichtlich des Betriebssystems effizient ist, kann es die Leistung von SQL Server bei starker Systemauslastung beeinträchtigen, da jeder Prozessorcache wiederholt mit Daten beladen wird. Unter diesen Bedingungen kann das Zuweisen bestimmter Threads zu bestimmten Prozessoren die Leistung verbessern, da das Neuladen von Prozessoren vermieden und die Migration zwischen Prozessoren verringert wird, was wiederum zu weniger Kontextwechseln führt. Eine solche Zuweisung zwischen einem Thread und einem Prozessor wird als Prozessoraffinität bezeichnet.

SQL Server unterstützt die Prozessoraffinität durch zwei Optionen für Affinitätsmasken: „affinity mask“ (auch **CPU-Affinitätsmaske** genannt) und „affinity I/O mask“. Weitere Informationen zur Option „affinity I/O mask“ finden Sie unter [affinity I/O mask (Serverkonfigurationsoption)](../../database-engine/configure-windows/affinity-input-output-mask-server-configuration-option.md). CPU- und E/A-Affinitätsunterstützung für Server mit 33–64 Prozessoren erfordert die zusätzliche Verwendung von [affinity64 mask (Serverkonfigurationsoption)](../../database-engine/configure-windows/affinity64-mask-server-configuration-option.md) bzw. [affinity64 Input-Output mask (Serverkonfigurationsoption)](../../database-engine/configure-windows/affinity64-input-output-mask-server-configuration-option.md).

> [!NOTE]  
> Affinitätsunterstützung für Server mit 33 bis 64 Prozessoren steht nur auf 64-Bit-Betriebssystemen zur Verfügung.

Mit der Option „affinity mask“ aus früheren SQL Server-Versionen wird die CPU-Affinität dynamisch gesteuert.

In SQL Server kann die Option „affinity mask“ konfiguriert werden, ohne dass ein Neustart der SQL Server-Instanz erforderlich ist. Wenn Sie „sp_configure“ verwenden, müssen Sie nach dem Festlegen einer Konfigurationsoption entweder RECONFIGURE oder RECONFIGURE WITH OVERRIDE ausführen. Wenn Sie [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] verwenden, ist ein Neustart erforderlich, falls Sie die Option „affinity mask“ ändern.

Änderungen an den Affinitätsmasken erfolgen dynamisch. Dies ermöglicht das bedarfsgesteuerte Starten und Herunterfahren der CPU-Planer, die Prozessthreads in SQL Server binden. Dies kann der Fall sein, wenn sich Bedingungen auf dem Server ändern. Wenn dem Server z. B. eine neue SQL Server-Instanz hinzugefügt wird, müssen Sie möglicherweise die Option „affinity mask“ anpassen, um die Prozessorlast neu zu verteilen.

Für Änderungen an den Affinitätsbitmasken muss SQL Server einen neuen CPU-Planer aktivieren und den vorhandenen CPU-Planer deaktivieren. Neue Batches können dann im neuen oder alten CPU-Zeitplanungsmodul verarbeitet werden.

Zum Starten eines neuen CPU-Planers erstellt SQL Server einen neuen CPU-Planer und fügt ihn der Liste der Standardplaner hinzu. Das neue Zeitplanungsmodul wird nur für die neuen eingehenden Batches verwendet. Die vorhandenen Batches werden weiterhin mit demselben Zeitplanungsmodul ausgeführt. Die Arbeitsthreads werden nach dem neuen Zeitplanungsmodul migriert, wenn sie freigegeben werden oder wenn neue Arbeitsthreads erstellt werden.

Zum Herunterfahren eines Zeitplanungsmoduls müssen alle Batches im Zeitplanungsmodul ihre Aktivitäten abschließen und beendet werden. Ein heruntergefahrenes Zeitplanungsmodul wird als offline gekennzeichnet, damit kein neuer Batch damit geplant wird.

Unabhängig davon, ob Sie einen neuen Planer hinzufügen oder entfernen, werden die permanenten Systemtasks wie die Sperrüberwachung, die Prüfpunkte, der Systemtaskthread (Verarbeitung von DTC) und die Signalverarbeitung weiterhin im Planer ausgeführt, während der Server in Betrieb ist. Diese permanenten Systemtasks werden nicht dynamisch migriert. Wenn Sie diese Prozessorlast für diese Systemtasks auf die Planer verteilen möchten, muss die SQL Server-Instanz neu gestartet werden. Falls SQL Server versucht, einen Planer für einen permanenten Systemtask herunterzufahren, wird der Task weiterhin im Offlineplaner ausgeführt (keine Migration). Dieser Planer ist an die Prozessoren in der geänderten Affinitätsmaske gebunden und lastet den Prozessor, an den der Planer vor der Änderung gebunden wurde, nicht aus. Zusätzliche Offlineplaner sollten keine signifikanten Auswirkungen auf die Systemlast haben. Wenn dies dennoch der Fall ist, ist ein Neustart des Datenbankservers erforderlich, um diese Tasks für die Planer neu zu konfigurieren, die mit der geänderten Affinitätsmaske verfügbar sind.

Legen Sie die Konfigurationswerte für „affinity mask“ und „affinity I/O mask“ von SQL Server nicht so fest, dass sie die gleichen CPUs verwenden. Wenn Sie einen Prozessor für die Workerthreadplanung und die E/A-Verarbeitung in SQL Server binden, kann dies die Leistung beeinträchtigen. Sie sollten daher sicherstellen, dass die Konfigurationswerte nicht auf denselben Prozessor festgelegt sind. Dasselbe gilt für „affinity64 mask“ und „affinity64 I/O mask“.  Damit sichergestellt ist, dass sich „affinity mask“ und „affinity IO mask“ nicht überlappen, wird mit dem Befehl [RECONFIGURE](../../t-sql/language-elements/reconfigure-transact-sql.md) überprüft, ob sich die normalen CPU- und E/A-Affinitäten gegenseitig ausschließen. Falls dies nicht der Fall ist, wird eine Fehlermeldung an die Clientsitzung und an das SQL Server-Fehlerprotokoll gesendet. Diese Fehlermeldung besagt, dass eine solche Einstellung nicht empfohlen wird.

```sql
 Msg 5834, Level 16, State 1, Line 1
 The affinity mask specified conflicts with the IO affinity mask specified. Use the override option to force this configuration
```

Das Ausführen von RECONFIGURE WITH OVERRIDE-Optionen ermöglicht CPU- und E/A-Affinitäten, die sich überlappen und nicht gegenseitig ausschließen.  

Die E/A-Affinitätsmaske hat direkte Auswirkungen auf die E/-A-Affinitätstasks (z. B. den verzögerten Schreiber und den Protokollschreiber). Falls der verzögerte Schreibtask und der Protokollschreibtask nicht gebunden sind, unterliegen sie denselben Regeln, die für die anderen permanenten Tasks wie die Sperrüberwachung oder die Prüfpunkte definiert sind.
Wenn Sie eine Affinitätsmaske angeben, die versucht, eine nicht vorhandene CPU zuzuordnen, sendet der Befehl RECONFIGURE eine Fehlermeldung an die Clientsitzung und an das SQL Server-Fehlerprotokoll. Die Verwendung der Option RECONFIGURE WITH OVERRIDE hat in diesem Fall keine Auswirkung, und der gleiche Konfigurationsfehler wird wiederum gemeldet.

Sie können SQL Server-Aktivitäten auch von bestimmten Arbeitsauslastungszuweisungen des Windows-Betriebssystems ausschließen. Wird ein Bit, das für einen Prozessor steht, auf 1 festgelegt, wird dieser Prozessor von der SQL Server-Datenbank-Engine für die Threadzuweisung ausgewählt. Wenn Sie **affinity mask** auf Null festlegen (Standardeinstellung), legen die Planungsalgorithmen von Microsoft Windows die Threadaffinität fest. Wenn Sie **affinity mask** auf einen Wert ungleich Null festlegen, legt die SQL Server-Affinität den Wert als Bitmaske aus, die die infrage kommenden Prozessoren angibt.  

Durch das Ausschließen der SQL Server-Threads von der Ausführung auf bestimmten Prozessoren kann Microsoft Windows die Verarbeitung von Windows-spezifischen Prozessen durch das System besser auswerten. Beispielsweise könnte der Systemadministrator auf einem Server mit 8 CPUs und zwei SQL Server-Instanzen (Instanz A und B) mithilfe der Option „affinity mask“ die ersten 4 CPUs der Instanz A sowie die nächsten 4 CPUs der Instanz B zuweisen. Wenn Sie mehr als 32 Prozessoren konfigurieren möchten, legen Sie die beiden Optionen „affinity mask“ und „affinity64 mask“ fest. Die Werte für **affinity mask** lauten wie folgt:

- Ein aus einem Byte bestehender Wert für **affinity mask** deckt bis zu 8 CPUs in einem Multiprozessorcomputer ab.

- Ein aus zwei Bytes bestehender Wert für **affinity mask** deckt bis zu 16 CPUs in einem Multiprozessorcomputer ab.

- Ein aus drei Bytes bestehender Wert für **affinity mask** deckt bis zu 24 CPUs in einem Multiprozessorcomputer ab.

- Ein aus vier Bytes bestehender Wert für **affinity mask** deckt bis zu 32 CPUs in einem Multiprozessorcomputer ab.

- Für einen Computer mit mehr als 32 CPUs konfigurieren Sie eine aus vier Bytes bestehende affinity mask für die ersten 32 CPUs und eine aus bis zu vier Bytes bestehende affinity64 mask für die restlichen CPUs.

Da es sich beim Festlegen der SQL Server-Prozessoraffinität um einen spezialisierten Vorgang handelt, sollten Sie diesen nur bei Bedarf verwenden. In den meisten Fällen kann eine optimale Leistung durch die standardmäßige Affinität von Microsoft Windows erzielt werden. Berücksichtigen Sie auch die CPU-Anforderungen für andere Anwendungen, wenn Sie die Affinitätsmasken festlegen. Weitere Informationen finden Sie in der Dokumentation zu Ihrem Windows-Betriebssystem.

> [!NOTE]
> Sie können den Windows-Systemmonitor zum Anzeigen und Analysieren der Auslastung einzelner Prozessoren verwenden.

Wenn Sie die Option „affinity I/O mask“ angeben, müssen Sie sie mit der Konfigurationsoption „affinity mask“ verwenden. Wie zuvor erwähnt, sollten Sie **affinity mask** und „affinity I/O mask“ unter keinen Umständen auf dieselbe CPU festlegen. Die Bits, die jeder CPU entsprechen, sollten einen der folgenden drei Status aufweisen:

- 0 für die Optionen Affinity Mask und Affinity I/O Mask.

- 1 für die Option Affinity Mask und 0 für die Option Affinity I/O Mask.

- 1 für die Option Affinity Mask und 1 für die Option Affinity I/O Mask.

> [!CAUTION]
> Konfigurieren Sie nie gleichzeitig die CPU-Affinität im Windows-Betriebssystem und die Affinitätsmaske in SQL Server. Diese Einstellungen zielen auf dasselbe Ergebnis. Wenn die Konfigurationen inkonsistent sind, kann dies zu unvorhersehbaren Ergebnissen führen. Die CPU-Affinität in SQL Server sollte am besten mit der Option „sp_configure“ in SQL Server konfiguriert werden.

## <a name="example"></a>Beispiel

Hier finden Sie ein Beispiel zum Festlegen der Option „affinity mask“: Wenn die Prozessoren 1, 2 und 5 als verfügbar ausgewählt wurden, indem die Bits 1, 2 und 5 auf 1 und die Bits 0, 3, 4, 6 und 7 auf 0 festgelegt wurden, muss der hexadezimale Wert 0x26 bzw. die äquivalente Dezimalzahl 38 verwendet werden. Nummerieren Sie die Bits von rechts nach links.

```sql
sp_configure 'show advanced options', 1;
RECONFIGURE;
GO
sp_configure 'affinity mask', 38;
RECONFIGURE;
GO
```

Nachfolgend werden die **affinity mask** -Werte für ein System mit 8 CPUs aufgeführt.  

|Dezimalzahl|Binäre Bitmaske|Ermöglicht SQL Server-Threads auf Prozessoren|  
|-------------------|---------------------|--------------------------------------------|  
|1|00000001|0|  
|3|00000011|0 und 1|  
|7|00000111|0, 1 und 2|  
|15|00001111|0, 1, 2 und 3|  
|31|00011111|0, 1, 2, 3 und 4|  
|63|00111111|0, 1, 2, 3, 4 und 5|  
|127|01111111|0, 1, 2, 3, 4, 5 und 6|  
|255|11111111|0, 1, 2, 3, 4, 5, 6 und 7|  

Bei Affinity Mask handelt es sich um eine erweiterte Option. Wenn Sie die Einstellung mithilfe der gespeicherten Systemprozedur „sp_configure“ ändern, können Sie **affinity mask** nur ändern, wenn **Erweiterte Optionen anzeigen** auf 1 festgelegt ist. Die neue Einstellung wird nach Ausführung des [!INCLUDE[tsql](../../includes/tsql-md.md)]-Befehls RECONFIGURE sofort wirksam, ohne dass die SQL Server-Instanz neu gestartet werden muss.  

## <a name="non-uniform-memory-access-numa"></a>Non-Uniform Memory Access (NUMA)

Wenn eine hardwarebasierte NUMA-Architektur (Non-Uniform Memory Access, nicht einheitlicher Speicherzugriff) verwendet wird und die Affinitätsmaske festgelegt ist, wird jeder Planer in einem Knoten an seine eigene CPU gebunden. Wenn die Affinitätsmaske nicht festgelegt ist, wird jeder Planer an die CPU-Gruppe innerhalb des NUMA-Knotens gebunden, und ein Planer, der dem NUMA-Knoten N1 zugeordnet ist, kann Vorgänge auf jeder CPU im Knoten planen, jedoch nicht auf CPUs, die einem anderen Knoten zugeordnet sind.  

Jeder Vorgang, der auf einem einzelnen NUMA-Knoten ausgeführt wird, kann nur Pufferseiten von diesem Knoten verwenden. Wenn ein Vorgang parallel auf CPUs von mehreren Knoten ausgeführt wird, kann Arbeitsspeicher von jedem beteiligten Knoten verwendet werden.  
  
## <a name="licensing-issues"></a>Lizenzierungsprobleme

Die dynamische Affinität wird durch die CPU-Lizenzierung streng reguliert. In SQL Server sind keine Konfigurationen von Affinitätsmaskenoptionen zulässig, die gegen die Lizenzierungsrichtlinien verstoßen.  

### <a name="startup"></a>Start

Wenn eine angegebene Affinitätsmaske während des Starts von SQL Server oder während des Anfügens einer Datenbank gegen die Lizenzierungsrichtlinien verstößt, führt die Engine-Schicht den Startprozess oder das Anfügen einer Datenbank bzw. den Wiederherstellungsvorgang aus. Anschließend wird der Ausführungswert von „sp_configure“ für die Affinitätsmaske auf Null zurückgesetzt, wodurch eine Fehlermeldung an das SQL Server-Fehlerprotokoll ausgegeben wird.  
  
### <a name="reconfigure"></a>Neu konfigurieren

Wenn eine angegebene Affinitätsmaske beim Ausführen des [!INCLUDE[tsql](../../includes/tsql-md.md)]-Befehls RECONFIGURE gegen die Lizenzierungsrichtlinien verstößt, wird eine Fehlermeldung an die Clientsitzung und an das SQL Server-Fehlerprotokoll gesendet. Der Datenbankadministrator muss dann die Affinitätsmaske neu konfigurieren. In diesem Fall ist der Befehl RECONFIGURE WITH OVERRIDE nicht zulässig.  

## <a name="next-steps"></a>Nächste Schritte

- [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)
- [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)
- [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)
- [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)
- [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-configuration-transact-sql.md)
