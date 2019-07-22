---
title: Handbuch zur Architektur von Seiten und Blöcken | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/12/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- page and extent architecture guide
- guide, page and extent architecture
ms.assetid: 83a4aa90-1c10-4de6-956b-7c3cd464c2d2
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7ba569631723bc456ceae2429d7c0fa8acac9769
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68031669"
---
# <a name="pages-and-extents-architecture-guide"></a>Handbuch zur Architektur von Seiten und Blöcken
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Die Seite ist die grundlegende Einheit für die Datenspeicherung in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Ein Block ist eine Auflistung von acht physisch zusammenhängenden Seiten. Blöcke tragen zu einer effizienten Verwaltung von Seiten bei. In diesem Handbuch werden die Datenstrukturen beschrieben, die zum Verwalten von Seiten und Blöcken in allen Versionen von SQL Server verwendet werden. Kenntnisse der Architektur von Seiten und Blöcken sind Voraussetzung für das Entwerfen und Entwickeln von effizienten Datenbanken.

## <a name="pages-and-extents"></a>Seiten und Blöcke

Die grundlegende Einheit für die Datenspeicherung in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ist die Seite. Der Speicherplatz, der einer Datendatei (MDF- oder NDF-Datei) in einer Datenbank zugeordnet wird, ist logisch in Seiten unterteilt, die fortlaufend von 0 bis n nummeriert sind. Datenträger-E/A-Operationen werden auf Seitenebene ausgeführt. Dies bedeutet, dass SQL Server ganze Datenseiten liest oder schreibt.

Blöcke sind Auflistungen von acht physisch zusammenhängenden Seiten; sie werden zum effizienten Verwalten der Seiten verwendet. Alle Seiten werden in Blöcken gespeichert.

### <a name="pages"></a>Seiten

In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] beträgt die Seitengröße 8 KB. Dies bedeutet, dass [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Datenbanken über 128 Seiten pro 1 MB verfügen. Jede Seite beginnt mit einem 96 Byte umfassenden Header, der zum Speichern von Systeminformationen zu der betreffenden Seite verwendet wird. Diese Informationen umfassen die Seitennummer, den Typ der Seite, den Umfang des freien Speicherplatzes auf der Seite und die ID der Zuordnungseinheit, die Besitzer der Seite ist.

Die folgende Tabelle zeigt die Seitentypen, die in Datendateien einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Datenbank verwendet werden.

|Seitentyp | Inhalt |
|-------|-------|
|Data |Datenzeilen mit allen Daten, ausgenommen Daten der Typen text, ntext, image, nvarchar(max), varchar(max), varbinary(max) und xml, wenn „text in row“ auf ON festgelegt wurde. |
|Index |Indexeinträge |
|Text/Image |LOB-Datentypen (Large Object): (text, ntext, image, nvarchar(max), varchar(max), varbinary(max) und xml) <br> Spalten variabler Länge, wenn die Datenzeile 8 KB übersteigt: (varchar, nvarchar, varbinary und sql_variant) |
|Global Allocation Map, Shared Global Allocation Map |Informationen dazu, ob Blöcke zugeordnet sind. |
|Page Free Space (PFS) |Informationen zur Seitenzuordnung sowie zum freien Speicherplatz, der auf Seiten verfügbar ist. |
|Index Allocation Map (IAM) |Informationen zu Blöcken, die von einer Tabelle oder einem Index pro Zuordnungseinheit verwendet werden. |
|Bulk Changed Map |Informationen zu Blöcken, die seit der letzten Ausführung der BACKUP LOG-Anweisung pro Zuordnungseinheit durch Massenvorgänge geändert wurden. |
|Differential Changed Map |Informationen zu Blöcken, die seit der letzten Ausführung der BACKUP DATABASE-Anweisung pro Zuordnungseinheit geändert wurden. |

> [!NOTE]
> Protokolldateien enthalten keine Seiten; sie enthalten eine Folge von Protokolldatensätze.

Datenzeilen werden unmittelbar nach dem Header nacheinander auf der Seite gespeichert. Eine Zeilenoffsettabelle beginnt am Ende der Seite, und jede Zeilenoffsettabelle enthält einen Eintrag für jede Zeile auf der Seite. Jeder dieser Einträge zeichnet auf, wie weit das erste Byte der Zeile vom Beginn der Seite entfernt ist. Die Einträge in der Zeilenoffsettabelle befinden sich in umgekehrter Reihenfolge zur Reihenfolge der Zeilen auf der Seite.

![page_architecture](../relational-databases/media/page-architecture.gif)

#### <a name="large-row-support"></a>Unterstützung von umfangreichen Zeilen  

Zeilen können sich nicht über mehrere Seiten erstrecken, Teile der Zeile können jedoch von der Seite der Zeile verschoben werden; die Zeile kann auf diese Weise sehr umfangreich sein. Die maximale Menge an Daten und Overhead, die in einer einzelnen Zeile auf einer Seite enthalten sein können, beträgt 8.060 Byte (8 KB). Dies schließt jedoch nicht die Daten ein, die im Text/Image-Seitentyp gespeichert werden. 

Diese Einschränkung wurde für Tabellen gelockert, die varchar-, nvarchar-, varbinary- oder sql_variant-Spalten enthalten. Wenn die Gesamtzeilengröße aller festen und variablen Spalten in einer Tabelle den Grenzwert von 8.060 Bytes übersteigt, verschiebt [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] eine oder mehrere Spalten variabler Länge dynamisch auf Seiten in der ROW_OVERFLOW_DATA-Zuordnungseinheit. Dabei wird mit der Spalte mit der größten Breite begonnen. 

Dieser Vorgang wird immer ausgeführt, wenn die Gesamtgröße der Zeile durch einen Einfüge- oder Updatevorgang den Maximalwert von 8.060 Byte übersteigt. Wenn eine Spalte auf eine Seite in der ROW_OVERFLOW_DATA-Zuordnungseinheit verschoben wird, wird ein 24-Byte-Zeiger auf die ursprüngliche Seite in der IN_ROW_DATA-Zuordnungseinheit verwaltet. Falls eine nachfolgende Operation die Spaltengröße verringert, verschiebt [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] die Spalten dynamisch zurück auf die ursprüngliche Datenseite. 

##### <a name="row-overflow-considerations"></a>Überlegungen zum Zeilenüberlauf 

Wenn Sie Spalten der Datentypen „varchar“, „nvarchar“, „nvarchar“, „sql_variant“ oder Spalten mit CLR-benutzerdefinierten Datentypen miteinander kombinieren, die pro Zeile 8.060 Bytes überschreiten, muss Folgendes berücksichtigt werden: 
-  Das Verschieben großer Datensätze zu einer anderen Seite geschieht dynamisch, wenn die Datensätze im Ergebnis von Updatevorgängen verlängert wurden. Updatevorgänge, die zu einer Verkürzung von Datensätzen führen, können hingegen bewirken, dass Datensätze wieder zurück zur ursprünglichen Seite in der IN_ROW_DATA-Zuordnungseinheit verschoben werden. Abfragen und andere Auswahlvorgänge, wie z. B. Sortierungen oder Joins von großen Datensätzen mit Daten, bei denen Zeilenüberlauf vorkommt, bewirken eine Herabsetzung der Verarbeitungsgeschwindigkeit, weil diese Datensätze nicht asynchron, sondern synchron verarbeitet werden.   
   Deshalb sollten Sie beim Entwerfen einer Tabelle mit mehreren Spalten der Datentypen „varchar“, „nvarchar“, „varbinary“, „sql_variant“ oder mit CLR-benutzerdefinierten Datentypen auf den Prozentsatz der Zeilen achten, bei denen es wahrscheinlich zum Überlauf kommt. Außerdem sollten Sie die Häufigkeit berücksichtigen, mit der diese Überlaufdaten wahrscheinlich abgefragt werden. Wenn es wahrscheinlich häufig zu Abfragen von vielen Zeilen mit überlaufenden Daten kommt, sollten Sie eine Normalisierung der Tabelle in Betracht ziehen, damit einige Spalten in eine andere Tabelle verschoben werden. Diese können dann in einer asynchronen JOIN-Operation abgefragt werden. 
-  Die Länge der einzelnen Spalten muss bei den Datentypen „varchar“, „nvarchar“, „varbinary“, „sql_variant“ und CLR-benutzerdefinierten Datentypen weiterhin innerhalb des 8.000-Byte-Limits liegen. Lediglich ihre kombinierten Längen dürfen das Zeilenlimit von 8.060 Byte einer Tabelle überschreiten.
-  Die Summe der Spalten mit anderen Datentypen, wie „char“- und „nchar“-Daten, dürfen das Zeilenlimit von 8.060 Byte nicht übersteigen. Große Objektdaten sind ebenfalls vom 8.060-Byte-Zeilenlimit ausgenommen. 
-  Der Indexschlüssel eines gruppierten Indexes kann keine Spalten des Datentyps „varchar“ enthalten, bei denen Daten in der Zuordnungseinheit ROW_OVERFLOW_DATA vorhanden sind. Wird ein gruppierter Index für eine „varchar“-Spalte erstellt, bei der in der Zuordnungseinheit IN_ROW_DATA Daten vorhanden sind, erzeugen alle nachfolgenden Einfügungen und Updates der Spalte einen Fehler, bei der diese Daten aus der Zeile entfernt werden. Weitere Informationen zu Zuordnungseinheiten finden Sie unter „Organisationsstruktur von Tabellen und Indizes“.
-  Sie können Spalten, die Daten mit Zeilenüberlauf enthalten, als Schlüssel- oder Nichtschlüsselspalten eines nicht gruppierten Index einbeziehen.
-  Die Datensatzgrößenbeschränkung für Tabellen, die Sparsespalten verwenden, beträgt 8.018 Byte. Wenn die konvertierten Daten zusammen mit den vorhandenen Datensatzdaten 8.018 Byte überschreiten, wird [MSSQLSERVER ERROR 576](../relational-databases/errors-events/database-engine-events-and-errors.md) zurückgegeben. Wenn Spalten zwischen Typen mit geringer Dichte und anderen Typen konvertiert werden, behält die Datenbank-Engine eine Kopie der aktuellen Datensatzdaten bei. Dies verdoppelt vorübergehend den Speicher, der für den Datensatz erforderlich ist.
-  Zum Abrufen von Informationen zu Tabellen oder Indizes, die ggf. Daten mit Zeilenüberlauf enthalten, verwenden Sie die dynamische Verwaltungsfunktion [sys.dm_db_index_physical_stats](../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md).

### <a name="extents"></a>Extents 

Blöcke sind die Grundeinheit, in der Speicherplatz verwaltet wird. Ein Block umfasst acht zusammenhängende Seiten, also 64 KB. Dies bedeutet, dass SQL Server-Datenbanken über 16 Blöcke pro 1 MB verfügen.

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] verfügt über zwei Arten von Blöcken: 

* **Einheitliche** Blöcke befinden sich im Besitz eines einzigen Objekts; alle acht Seiten in dem Block können nur vom besitzenden Objekt verwendet werden.
* **Gemischte** Blöcke werden für bis zu acht Objekte freigegeben. Jede der acht Seiten im Block kann im Besitz eines anderen Objekts sein.

Bis einschließlich [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] ordnet [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Tabellen, die nur wenige Daten enthalten, keine ganzen Blöcke zu. Für eine neue Tabelle oder einen neuen Index werden normalerweise Seiten aus gemischten Blöcken zugewiesen. Wenn eine Tabelle oder ein Index so groß geworden ist, dass sie bzw. er acht Seiten umfasst, werden bei nachfolgenden Zuweisungen einheitliche Blöcke zugewiesen. Wenn Sie einen Index für eine vorhandene Tabelle erstellen, die über genügend Zeilen verfügt, um acht Seiten im Index zu generieren, erfolgen alle Zuweisungen für den Index in Form von einheitlichen Blöcken. Ab [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] jedoch sind einheitliche Blöcke der Standard für alle Zuordnungen in der Datenbank.

![Extents](../relational-databases/media/extents.gif)

> [!NOTE]
> Bis einschließlich [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] kann das Ablaufverfolgungsflag 1118 verwendet werden, um die Standardzuordnung so zu ändern, dass immer einheitliche Blöcke verwendet werden. Weitere Informationen zu diesem Ablaufverfolgungsflag finden Sie unter [DBCC TRACEON – Trace Flags](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md).   
>   
> Ab [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] wird die Funktionalität, die vom Ablaufverfolgungsflag 1118 bereitgestellt wird, für tempdb automatisch aktiviert. Für Benutzerdatenbanken wird dieses Verhalten durch die `SET MIXED_PAGE_ALLOCATION`-Option von `ALTER DATABASE` gesteuert. Der Standardwert ist auf OFF festgelegt, und das Ablaufverfolgungsflag 1118 hat keine Auswirkungen. Weitere Informationen finden Sie unter [ALTER DATABASE SET-Optionen (Transact-SQL)](../t-sql/statements/alter-database-transact-sql-set-options.md).

## <a name="managing-extent-allocations-and-free-space"></a>Verwalten von Blockzuordnungen und freiem Speicherplatz 

Die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Datenstrukturen, die Blockzuordnungen verwalten und freien Speicherplatz nachverfolgen, weisen eine relativ einfache Struktur auf. Dies bringt folgende Vorteile mit sich: 

* Die Informationen zum freien Speicherplatz sind dicht gepackt, sodass nur relativ wenig Seiten benötigt werden, um diese Informationen aufzunehmen.   
  Auf diese Weise wird die Geschwindigkeit erhöht, da die Anzahl der Lesevorgänge vom Datenträger reduziert wird, die erforderlich sind, um Zuordnungsinformationen abzurufen. Hierdurch wird auch die Wahrscheinlichkeit erhöht, dass die Zuordnungsseiten im Arbeitsspeicher verbleiben und somit keine weiteren Lesevorgänge erforderlich sind. 

* Der größte Teil der Zuordnungsinformationen ist nicht miteinander verkettet. Hierdurch wird die Verwaltung der Zuordnungsinformationen vereinfacht.    
  Das Zuordnen oder Aufheben der Zuordnung der einzelnen Seiten kann sehr schnell erfolgen. So wird die Anzahl der Konflikte zwischen gleichzeitig ausgeführten Tasks reduziert, die Seiten zuordnen oder die Zuordnung von Seiten aufheben müssen. 

### <a name="managing-extent-allocations"></a>Verwalten von Blockzuordnungen

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] verwendet zwei Arten von Zuordnungstabellen, um die Zuordnung von Blöcken zu erfassen: 

- **Global Allocation Map (GAM)**    
  GAM-Seiten zeichnen auf, welche Blöcke zugeordnet wurden. Jede GAM erfasst 64.000 Blöcke, was fast 4 GB an Daten entspricht. Die GAM verfügt über ein Bit für jeden Block in dem von ihr abgedeckten Intervall. Hat das Bit den Wert 1, ist der Block frei; hat das Bit den Wert 0, ist der Block zugeordnet. 

- **Shared Global Allocation Map (SGAM)**    
  SGAM-Seiten zeichnen auf, welche Blöcke zurzeit als gemischte Blöcke verwendet werden und über mindestens eine nicht verwendete Seite verfügen. Jede SGAM erfasst 64.000 Blöcke, was fast 4 GB an Daten entspricht. Die SGAM verfügt über ein Bit für jeden Block in dem von ihr abgedeckten Intervall. Wenn das Bit den Wert 1 hat, wird der Block als gemischter Block verwendet und verfügt über eine freie Seite. Wenn das Bit den Wert 0 hat, wird der Block nicht als gemischter Block verwendet, oder er wird als gemischter Block verwendet, aber alle seine Seiten werden verwendet. 

Für jeden Block wird auf der Grundlage der aktuellen Verwendung eines der folgenden Bitmuster in der GAM oder der SGAM festgelegt. 

|Aktuelle Blockverwendung | GAM-Biteinstellung | SGAM-Biteinstellung |
|---------|----------|------| 
|Frei, wird nicht verwendet |1 |0 |
|Einheitlicher Block oder vollständig belegter gemischter Block |0 |0 |
|Gemischter Block mit freien Seiten |0 |1 |
 
Dies führt zu einfachen Algorithmen für die Blockverwaltung. 
-   Um einen einheitlichen Block zuzuweisen, durchsucht [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] die GAM nach einem Bit mit dem Wert 1 und legt es auf 0 fest. 
-   Um einen gemischten Block mit freien Seiten zu finden, durchsucht [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] die SGAM nach einem Bit mit dem Wert 1. 
-   Um einen einheitlichen Block zuzuordnen, durchsucht [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] die GAM nach einem Bit mit dem Wert 1 und legt es auf 0 fest. Anschließend wird der entsprechende Wert in der SGAM auf 1 festgelegt. 
-   Um einen Block freizugeben, stellt [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] sicher, dass das GAM-Bit auf 1 und das SGAM-Bit auf 0 festgelegt wird. Die Algorithmen, die von [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] tatsächlich intern verwendet werden, sind komplexer als in diesem Artikel beschrieben, da [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Daten gleichmäßig in der Datenbank verteilt. Aber auch die wirklich verwendeten Algorithmen konnten vereinfacht werden, da nunmehr keine verketteten Blockzuordnungsinformationen verwaltet werden müssen.

### <a name="tracking-free-space"></a>Nachverfolgen von freiem Speicherplatz

**PFS-Seiten (Page Free Space)** zeichnen den Zuordnungsstatus der einzelnen Seiten auf, ob eine einzelne Seite zugeordnet wurde und die Menge des freien Speicherplatzes für die einzelnen Seiten. Der freie Speicherplatz verfügt über ein Byte pro Seite und zeichnet auf, ob die Seite zugeordnet ist. Wenn dies der Fall ist, wird auch aufgezeichnet, ob sie leer oder bis zu einem bestimmten Prozentsatz voll ist: 1 bis 50 Prozent, 51 bis 80 Prozent, 81 bis 95 Prozent oder 96 bis 100 Prozent.

Nachdem ein Block einem Objekt zugeordnet wurde, verwendet [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] die PFS-Seiten, um aufzuzeichnen, welche Seiten in dem jeweiligen Block zugeordnet und welche Seiten frei sind. Diese Informationen werden verwendet, wenn [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] eine neue Seite zuordnen muss. Die Menge des freien Speicherplatzes auf einer Seite wird nur für Heap- und Text/Image-Seiten verwaltet. Diese Information wird verwendet, wenn [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] eine Seite mit verfügbarem freien Speicherplatz sucht, um eine neu eingefügte Zeile aufzunehmen. Indizes erfordern nicht, dass der Page Free Space nachverfolgt werden soll, da die Stelle, an der eine neue Zeile eingefügt werden soll, von den Indexschlüsselwerten festgelegt wird.

Eine PFS-Seite ist nach der Dateiheaderseite die erste Seite in einer Datendatei (Seiten-ID 1). Auf diese folgt eine GAM-Seite (Seiten-ID 2) und anschließend eine SGAM-Seite (Seiten-ID 3). Nach der ersten PFS-Seite folgt etwa alle 8.000 Seiten eine neue PFS-Seite. 64.000 Blöcke nach der ersten GAM-Seite auf Seite 2 folgt eine weitere GAM-Seite. 64.000 Blöcke nach der ersten SGAM-Seite auf Seite 3 folgt eine weitere SGAM-Seite. Nach jeweils 64.000 Blöcken folgen weitere GAM- und SGAM-Seiten. Folgende Abbildung veranschaulicht die Abfolge der Seiten, die von [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] für das Zuordnen und Verwalten von Blöcken verwendet werden.

![manage_extents](../relational-databases/media/manage-extents.gif)

## <a name="managing-space-used-by-objects"></a>Verwalten des von Objekten belegten Speicherplatzes 

Eine **IAM-Seite (Index Allocation Map)** ordnet die Blöcke in einem 4-GB-Teil einer Datenbankdatei zu, die von einer Zuordnungseinheit verwendet wird. Eine Zuordnungseinheit entspricht einem von drei möglichen Typen:

- IN_ROW_DATA   
    Enthält eine Partition eines Heap oder eines Index.

- LOB_DATA   
   Enthält LOB-Datentypen (Large Object) wie xml, varbinary(max) und varchar(max).

- ROW_OVERFLOW_DATA   
   Enthält Daten variabler Länge, die in varchar-, nvarchar-, varbinary- oder sql_variant-Spalten gespeichert sind, die das Zeilengrößenlimit von 8.060 Bytes überschreiten. 

Jede Partition eines Heap oder Index enthält mindestens eine IN_ROW_DATA-Zuordnungseinheit. Sie kann je nach dem Heap- oder Indexschema auch eine LOB_DATA- oder ROW_OVERFLOW_DATA-Zuordnungseinheit enthalten.

Eine IAM-Seite deckt einen 4-GB-Bereich in einer Datei ab und besitzt dieselbe Erfassung wie eine GAM- oder SGAM-Seite. Wenn die Zuordnungseinheit Blöcke mehrerer Dateien oder mehrere 4-GB-Bereiche einer Datei enthält, werden mehrere IAM-Seiten zu einer IAM-Kette verknüpft. Deshalb hat jede Zuordnungseinheit mindestens eine IAM-Seite für jede Datei, aus der sie Blöcke enthält. Es kann auch mehrere IAM-Seiten für eine Datei geben, wenn der Bereich der Blöcke aus der Datei, die für die Zuordnungseinheit zugeordnet ist, den Bereich übersteigt, den eine einzelne IAM-Seite aufzeichnen kann. 

![iam_pages](../relational-databases/media/iam-pages.gif)

IAM-Seiten werden je nach Bedarf für jede Zuordnungseinheit zugeordnet und nach dem Zufallsprinzip in der Datei verteilt. Die Systemsicht „sys.system_internals_allocation_units“ verweist auf die erste IAM-Seite für eine Zuordnungseinheit. Alle IAM-Seiten für diese Zuordnungseinheit werden in einer Kette miteinander verknüpft.

> [!IMPORTANT]
> Die Systemsicht `sys.system_internals_allocation_units` ist nur zur internen Verwendung bestimmt und kann geändert werden. Kompatibilität wird nicht sichergestellt.

![iam_chain](../relational-databases/media/iam-chain.gif)
 
Pro Zuordnungseinheit in einer Kette verknüpfte IAM-Seiten. Eine IAM-Seite verfügt über einen Header, der den Anfangsblock des Bereichs von Blöcken kennzeichnet, die von der IAM-Seite zugeordnet werden. Die IAM-Seite verfügt darüber hinaus über ein großes Bitmuster, in dem jedes Bit einen Block darstellt. Das erste Bit in dem Bitmuster stellt den ersten Block im Bereich dar, das zweite Bit stellt den zweiten Block dar usw. Wenn ein Bit den Wert 0 hat, ist der Block, den es darstellt, nicht für die Zuordnungseinheit zugeordnet, die die IAM besitzt. Wenn das Bit den Wert 1 hat, ist der Block, den es darstellt, für die Zuordnungseinheit zugeordnet, die die IAM-Seite besitzt.

Wenn von [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] eine neue Zeile eingefügt werden muss und auf der aktuellen Seite kein Speicherplatz verfügbar ist, werden die IAM- und PFS-Seiten verwendet, um eine zuzuordnende Seite zu finden oder – bei einem Heap oder einer Text-/Image-Seite – um eine Seite mit ausreichend Platz zur Aufnahme der Zeile zu finden. [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] verwendet IAM-Seiten, um die Blöcke zu suchen, die für die Zuordnungseinheit zugeordnet sind. Für jeden Block durchsucht [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] die FPS-Seiten, um herauszufinden, ob eine geeignete Seite vorhanden ist. Jede IAM- und PFS-Seite erfasst viele Datenseiten, sodass in jeder Datenbank nur wenige IAM- und PFS-Seiten enthalten sind. Dies bedeutet, dass sich die IAM- und PFS-Seiten normalerweise im Arbeitsspeicher des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Pufferpools befinden, sodass sie schnell durchsucht werden können. Für Indizes wird die Einfügemarke für eine neue Zeile durch den Indexschlüssel festgelegt. Wenn jedoch eine neue Seite benötigt wird, wird der zuvor beschriebene Vorgang durchgeführt.

Ein neuer Block für eine Zuordnungseinheit wird nur dann von [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] zugeordnet, wenn es nicht schnell möglich ist, in einem vorhandenen Block eine Seite zu finden, die ausreichend Speicherplatz bietet, um die eingefügte Zeile aufnehmen zu können. 

<a name="ProportionalFill"></a> Die [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] ordnet Blöcke auf der Basis der verfügbaren Blöcke in der Dateigruppe zu und verwendet dazu einen **Zuordnungsalgorithmus zur proportionalen Füllung**. Wenn eine Dateigruppe zwei Dateien enthält, von denen die eine über doppelt so viel freien Speicherplatz wie die andere verfügt, werden in der Datei, die über mehr freien Speicherplatz verfügt, zwei Seiten für jede Seite zugeordnet, die in der anderen Datei zugeordnet wird. Dies bedeutet, dass der Anteil des verwendeten Speicherplatzes in allen Dateien einer Dateigruppe ähnlich groß sein sollte. 

## <a name="tracking-modified-extents"></a>Protokollieren geänderter Blöcke 

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] verwendet zwei interne Datenstrukturen zum Nachverfolgen von durch Massenkopiervorgänge geänderten Blöcken sowie von Blöcken, die seit der letzten vollständigen Sicherung geändert wurden. Diese Datenstrukturen beschleunigen differenzielle Sicherungen erheblich. Sie beschleunigen außerdem das Protokollieren von Massenkopiervorgängen, wenn eine Datenbank das Modell der massenprotokollierten Wiederherstellung verwendet. Ähnlich wie bei den GAM-Seiten (Global Allocation Map) und den SGAM-Seiten (Shared Global Allocation Map) handelt es sich bei diesen Strukturen um Bitmuster, wobei jedes Bit einen einzelnen Block darstellt. 

- **Differential Changed Map (DCM)**    
   DCM protokolliert die Blöcke, die seit der letzten Ausführung der `BACKUP DATABASE`-Anweisung geändert wurden. Falls das Bit für einen Block den Wert 1 besitzt, wurde der Block seit der letzten Ausführung der `BACKUP DATABASE`-Anweisung geändert. Falls das Bit den Wert 0 aufweist, wurde der Block nicht geändert. Differenzielle Sicherungen lesen nur die DCM-Seiten, um zu ermitteln, welche Blöcke geändert wurden. Dadurch wird die Anzahl an Seiten, die eine differenzielle Sicherung scannen muss, erheblich verringert. Die Dauer der Ausführung einer differenziellen Sicherung ist proportional zu der Anzahl an Blöcken, die seit der letzten Ausführung der BACKUP DATABASE-Anweisung geändert wurden, und nicht proportional zu der Gesamtgröße der Datenbank. 

- **Bulk Changed Map (BCM)**    
   BCM protokolliert die Blöcke, die seit der letzten Ausführung der `BACKUP LOG`-Anweisung durch massenprotokollierte Vorgänge geändert wurden. Falls das Bit für einen Block den Wert 1 aufweist, wurde der Block seit der letzten Ausführung der `BACKUP LOG`-Anweisung durch einen massenprotokollierten Vorgang geändert. Falls das Bit den Wert 0 besitzt, wurde der Block nicht durch massenprotokollierte Vorgänge geändert. BCM-Seiten treten in allen Datenbanken auf, sind jedoch nur dann relevant, wenn die Datenbank das Modell der massenprotokollierten Wiederherstellung verwendet. Wenn bei diesem Wiederherstellungsmodell eine `BACKUP LOG`-Anweisung ausgeführt wird, scannt der Sicherungsvorgang die BCM-Seiten nach Blöcken, die geändert wurden. Diese Blöcke werden dann in die Protokollsicherung eingeschlossen. Dadurch können die massenprotokollierten Vorgänge wiederhergestellt werden, wenn die Datenbank aus einer Datenbanksicherung und einer Folge von Transaktionsprotokollsicherungen wiederhergestellt wird. BCM-Seiten sind in einer Datenbank, die das einfache Wiederherstellungsmodell verwendet, nicht relevant, da keine massenprotokollierten Vorgänge protokolliert sind. Sie sind in einer Datenbank, die das Modell der vollständigen Wiederherstellung verwendet, relevant, da bei diesem Wiederherstellungsmodell massenprotokollierte Vorgänge wie vollständig protokollierte Vorgänge behandelt werden. 

Der Abstand zwischen DCM-Seiten und BCM-Seiten ist derselbe Abstand wie zwischen GAM- und SGAM-Seiten; 64.000 Blöcke. Die DCM- und BCM-Seiten befinden sich direkt hinter den GAM- und SGAM-Seiten in einer physischen Datei:

![special_page_order](../relational-databases/media/special-page-order.gif)

## <a name="see-also"></a>Weitere Informationen
[sys.allocation_units &#40;Transact-SQL&#41;](../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md)     
[Heaps &#40;Tabellen ohne gruppierte Indizes&#41;](../relational-databases/indexes/heaps-tables-without-clustered-indexes.md#heap-structures)       
[Lesen von Seiten](../relational-databases/reading-pages.md)   
[Schreiben von Seiten](../relational-databases/writing-pages.md)   
