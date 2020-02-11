---
title: Einführung in speicheroptimierte Tabellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: ef1cc7de-63be-4fa3-a622-6d93b440e3ac
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ff434efd0a9f4fcb3316143e598e636bff85f487
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63157829"
---
# <a name="introduction-to-memory-optimized-tables"></a>Einführung in speicheroptimierte Tabellen
  Speicheroptimierte Tabellen sind Tabellen, die mit [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) erstellt wurden.  
  
 Die speicheroptimierten Tabellen befinden sich im Arbeitsspeicher. Zeilen in der Tabelle werden aus dem Arbeitsspeicher gelesen und in diesen geschrieben. Die gesamte Tabelle befindet sich im Arbeitsspeicher. Eine zweite Kopie der Tabellendaten wird auf Festplatte gespeichert, aber nur zu Dauerhaftigkeitszwecken.  
  
 In-Memory OLTP ist in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] integriert, um in allen Bereichen wie Entwicklung, Bereitstellung, Verwaltbarkeit und Unterstützbarkeit eine reibungslose Benutzererfahrung zu ermöglichen. Eine Datenbank kann speicherinterne wie auch datenträgerbasierte Objekte enthalten.  
  
 Für Zeilen in speicheroptimierten Tabellen wird die Versionsverwaltung verwendet. Dies bedeutet, dass für jede Zeile in der Tabelle möglicherweise mehrere Versionen vorliegen. Alle Zeilenversionen werden in derselben Tabellendatenstruktur verwaltet. Die Zeilenversionsverwaltung wird verwendet, um gleichzeitige Lese- und Schreibvorgänge für dieselbe Zeile zuzulassen. Weitere Informationen zu gleichzeitigen Lese-und Schreibvorgängen in derselben Zeile finden Sie unter [Transaktionen in Speicher optimierten Tabellen](memory-optimized-tables.md).  
  
 Die folgende Abbildung veranschaulicht die Multiversionsverwaltung. Die Abbildung zeigt eine Tabelle mit drei Zeilen, und jede Zeile weist unterschiedliche Versionen auf.  
  
 ![Multiversionsverwaltung.](../../database-engine/media/hekaton-tables-1.gif "Multiversionsverwaltung.")  
  
 Die Tabelle enthält drei Zeilen: r1, r2 und r3. r1 verfügt über drei Versionen, r2 über zwei Versionen und r3 über vier Versionen. Beachten Sie, dass unterschiedliche Versionen derselben Zeile nicht unbedingt aufeinander folgende Speicheradressen belegen. Die unterschiedlichen Zielversionen können über die Tabellendatenstruktur verteilt sein.  
  
 Die speicheroptimierte Tabellendatenstruktur kann als Auflistung von Zeilenversionen gesehen werden. Während Zeilen in datenträgerbasierten Tabellen in Seiten und Blöcken angeordnet sind und einzelne Zeilen mithilfe der Seitenzahl und des Seitenoffsets adressiert werden, werden Zeilenversionen in speicheroptimierten Tabellen mithilfe von 8-Byte-Speicherzeigern adressiert.  
  
## <a name="durability"></a>Beständigkeit  
 Speicheroptimierte Tabellen sind standardmäßig vollständig dauerhaft und bieten, wie Transaktionen in (herkömmlichen) datenträgerbasierten Tabellen, vollständige ACID-Eigenschaften (atomar, konsistent, isoliert und beständig). Speicheroptimierte Tabellen und systemintern kompilierte gespeicherte Prozeduren unterstützen eine Teilmenge von [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 In-Memory OLTP unterstützt dauerhafte Tabellen mit verzögerter Transaktionsdauerhaftigkeit. Verzögerte dauerhafte Transaktionen werden auf einem Datenträger gespeichert, sobald ein Commit für eine entsprechende Transaktion ausgeführt wurde. Im Austausch für die höhere Leistung besteht die Gefahr, dass Transaktionen, die noch nicht auf dem Datenträger gespeichert wurden, bei einem Absturz oder Failover des Servers verloren gehen.  
  
 Neben den standardmäßig dauerhaften speicheroptimierten Tabellen unterstützt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auch nicht dauerhafte speicheroptimierte Tabellen, die nicht protokolliert und deren Daten nicht auf dem Datenträger beibehalten werden. Das bedeutet, dass Transaktionen in diesen Tabellen keine Datenträger-E/A-Vorgänge erfordern, die Daten aber bei einem Serverabsturz oder einem Failover nicht wiederhergestellt werden können.  
  
## <a name="accessing-data-in-memory-optimized-tables"></a>Zugriff auf Daten in speicheroptimierten Tabellen  
 Der Datenzugriff in speicheroptimierten Tabellen erfolgt auf zwei Arten:  
  
-   Durch interpretiertes [!INCLUDE[tsql](../../../includes/tsql-md.md)] (außerhalb einer systemintern kompilierten gespeicherten Prozedur). Diese [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisungen können sich entweder in interpretierten gespeicherten Prozeduren befinden oder als Ad-hoc- [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisungen vorliegen.  
  
-   Durch systemintern kompilierte gespeicherte Prozeduren  
  
 Auf speicheroptimierte Tabellen kann am effizientesten mit systemintern kompilierten gespeicherten Prozeduren ([Systemintern kompilierte gespeicherte Prozeduren](natively-compiled-stored-procedures.md)) zugegriffen werden. Auf speicheroptimierte Tabellen kann außerdem mit (herkömmlichem) interpretiertem [!INCLUDE[tsql](../../../includes/tsql-md.md)]zugegriffen werden. "Interpretiertes [!INCLUDE[tsql](../../../includes/tsql-md.md)] " bezieht sich auf den Zugriff auf speicheroptimierte Tabellen ohne eine systemintern kompilierte gespeicherte Prozedur. Beispiele für den Zugriff auf interpretiertes [!INCLUDE[tsql](../../../includes/tsql-md.md)] sind der Zugriff auf eine speicheroptimierte Tabelle über einen DML-Trigger, einen Ad-Hoc- [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Batch, eine Sicht und eine Tabellenwertfunktion.  
  
 In der folgenden Tabelle wird der systemeigene und interpretierte [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Zugriff für verschiedene Objekte zusammengefasst.  
  
|Funktion|Zugriff mithilfe einer systemintern kompilierten gespeicherten Prozedur|Interpretierter [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Zugriff|CLR-Zugriff|  
|-------------|-------------------------------------------------------|-------------------------------------------|----------------|  
|Speicheroptimierte Tabellen|Ja|Ja|Nein <sup>1</sup>|  
|[Speicheroptimierte Tabellenvariablen](../../database-engine/memory-optimized-table-variables.md)|Ja|Ja|Nein|  
|[Nativ kompilierte gespeicherte Prozeduren](https://msdn.microsoft.com/library/dn133184.aspx)|Sie können die EXECUTE-Anweisung nicht verwenden, um eine gespeicherte Prozedur über eine systemintern kompilierte gespeicherte Prozedur auszuführen.|Ja|Nein <sup>1</sup>|  
  
 <sup>1</sup> Sie können nicht über die Kontext Verbindung (die Verbindung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , wenn ein CLR-Modul ausgeführt wird) auf eine Speicher optimierte Tabelle oder eine System intern kompilierte gespeicherte Prozedur zugreifen. Sie können jedoch eine andere Verbindung erstellen und öffnen, über die Sie auf speicheroptimierte Tabellen und systemintern kompilierte gespeicherte Prozeduren zugreifen können. Weitere Informationen finden Sie unter [reguläre und Kontext Verbindungen](../clr-integration/data-access/context-connections-vs-regular-connections.md).  
  
## <a name="performance-and-scalability"></a>Leistung und Skalierbarkeit  
 Die folgenden Faktoren beeinflussen die Leistungsvorteile, die mit In-Memory OLTP erreicht werden können:  
  
 Kommunikation  
 Eine Anwendung mit vielen Aufrufen kurzer gespeicherter Prozeduren erzielt möglicherweise einen kleineren Leistungszuwachs als eine Anwendung, bei der weniger Aufrufe und zusätzliche Funktionen in jede gespeicherte Prozedur implementiert sind.  
  
 [!INCLUDE[tsql](../../../includes/tsql-md.md)]Niederlage  
 In-Memory OLTP gewährleistet die beste Leistung bei systemintern kompilierten gespeicherten Prozeduren im Gegensatz zu interpretierten gespeicherten Prozeduren oder Abfrageausführungen. Gespeicherte Prozeduren, durch die andere gespeicherte Prozeduren ausgeführt werden, können nicht systemintern kompiliert werden. Allerdings kann der Zugriff auf speicheroptimierte Tabellen aus solchen gespeicherten Prozeduren von Nutzen sein.  
  
 Bereichsscan vs. Punktsuche  
 Speicheroptimierte, nicht gruppierte Indizes unterstützen Bereichsscans und sortierte Scans. Bei Punktsuchen erzielen Sie mit speicheroptimierten Hashindizes eine bessere Leistung als mit speicheroptimierten, nicht gruppierten Indizes. Speicheroptimierte, nicht gruppierte Indizes weisen eine bessere Leistung auf als datenträgerbasierte Indizes.  
  
 Indexvorgänge werden nicht protokolliert und sie sind nur im Arbeitsspeicher vorhanden.  
  
 Parallelität  
 Anwendungen, deren Leistung durch Parallelität auf Engine-Ebene wie Latchkonflikte oder Blockierungen beeinträchtigt wird, verzeichnen eine erhebliche Leistungssteigerung, wenn die Anwendung auf In-Memory OLTP umgestellt wird.  
  
 In der folgenden Tabelle werden die Leistungs- und Skalierbarkeitsprobleme, die häufig in relationalen Datenbanken auftreten, zusammen mit einer möglichen Leistungssteigerung durch In-Memory OLTP aufgeführt.  
  
|Problem|Einfluss durch In-Memory OLTP|  
|-----------|----------------------------|  
|Leistung<br /><br /> Intensive Ressourcennutzung (CPU, E/A, Netzwerk oder Arbeitsspeicher)|CPU<br /> Durch systemintern kompilierte gespeicherte Prozeduren kann die CPU-Nutzung erheblich gesenkt werden, da sie deutlich weniger Anweisungen als interpretierte gespeicherte Prozeduren benötigen, um eine [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisung auszuführen.<br /><br /> In-Memory OLTP kann die erforderlichen Hardwareinvestitionen bei horizontal skalierten Arbeitsauslastungen reduzieren, da ein Server so potenziell den Durchsatz von fünf bis 10 Servern erzielen kann.<br /><br /> E/A<br /> Wenn bei der Verarbeitung ein E/A-Engpass aufgrund der Verarbeitung von Daten oder Indexseiten auftritt, lässt sich dieser durch In-Memory OLTP u. U. reduzieren. Zudem wird der Prüfpunktalgorithmus von In-Memory OLTP-Objekten kontinuierlich durchgeführt und führt nicht zu einem plötzlichen Anstieg von E/A-Vorgängen. Wenn jedoch das Workingset der leistungskritischen Tabellen zu groß für den Arbeitsspeicher ist, steigert In-Memory OLTP nicht die Leistung, da dieser Datenbanktyp speicherresidente Daten benötigt. Wenn bei der Protokollierung ein E/A-Engpass auftritt, kann In-Memory OLTP diesen Engpass verringern, da weniger Protokollierungsaktivität durchgeführt wird. Wenn eine oder mehrere speicheroptimierte Tabellen als nicht dauerhafte Tabellen konfiguriert sind, können Sie dadurch die Protokollierung für Daten eliminieren.<br /><br /> Arbeitsspeicher<br /> In-Memory OLTP bietet keine Leistungssteigerung. In-Memory OLTP kann den Arbeitsspeicher zusätzlich belasten, da die Objekte speicherresident sein müssen.<br /><br /> Netzwerk<br /> In-Memory OLTP bietet keine Leistungssteigerung. Die Daten müssen von der Datenebene an die Anwendungsebene übertragen werden.|  
|Skalierbarkeit<br /><br /> Die meisten Skalierungsprobleme bei [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anwendungen werden durch Parallelitätsprobleme wie Konflikten bei Sperren, Latches und Spinlocks verursacht.|Latchkonflikte<br /> Ein typisches Szenario ist ein Konflikt auf der letzten Seite eines Indexes, wenn Zeilen gleichzeitig in Schlüsselreihenfolge einfügt werden. Da In-Memory OLTP beim Datenzugriff keine Latches verwendet, werden Skalierbarkeitsprobleme aufgrund von Latchkonflikten vollständig eliminiert.<br /><br /> Spinlock-Konflikt<br /> Da In-Memory OLTP beim Datenzugriff keine Latches verwendet, werden Skalierbarkeitsprobleme aufgrund von Spinlock-Konflikten vollständig eliminiert.<br /><br /> Konflikte aufgrund von Sperren<br /> Wenn in der Datenbankanwendung Blockierungen zwischen Lese- und Schreibvorgängen auftreten, werden diese Blockierungsprobleme durch In-Memory OLTP beseitigt, da es eine neue Art der optimistischen Nebenläufigkeitssteuerung für die Implementierung der Transaktionsisolationsstufen verwendet. In-Memory OLTP verwendet nicht TempDB, um Zeilenversionen zu speichern.<br /><br /> Wenn das Skalierungsproblem durch einen Konflikt zwischen zwei Schreibvorgängen verursacht wird, etwa zwei Transaktionen, die gleichzeitig dieselbe Zeile zu aktualisieren versuchen, führt In-Memory OLTP eine Transaktion erfolgreich durch und beendet die andere. Die fehlgeschlagene Transaktion muss zur Wiederholung explizit oder implizit erneut gesendet werden. In beiden Fällen müssen Sie Änderungen an der Anwendung vornehmen.<br /><br /> Wenn in der Anwendung häufig Konflikte zwischen zwei Schreibvorgängen auftreten, wird der Wert der optimistischen Sperre verringert. Die Anwendung ist für In-Memory OLTP nicht geeignet. Die meisten OLTP-Anwendungen weisen keine Schreibkonflikte auf, sofern diese nicht durch Sperrenausweitung verursacht werden.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](in-memory-oltp-in-memory-optimization.md)  
  
  
