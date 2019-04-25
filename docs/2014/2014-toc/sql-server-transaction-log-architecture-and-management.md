---
title: SQL Serverarchitektur des Transaktionsprotokolls und-Verwaltung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 4d1a4f97-3fe4-44af-9d4f-f884a6eaa457
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 2495b9487a633fff6c5214a07e589f58fafa5e61
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62512746"
---
# <a name="sql-server-transaction-log-architecture-and-management"></a>SQL Server Architektur und Verwaltung von Transaktionsprotokollen

[!INCLUDE[appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Jede [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenbank verfügt über ein Transaktionsprotokoll, in dem alle Transaktionen und Datenbankänderungen aufgezeichnet werden, die von den einzelnen Transaktionen vorgenommen werden. Das Transaktionsprotokoll ist eine wichtige Komponente der Datenbank und wird im Falle eines Systemfehlers ggf. benötigt, um einen konsistenten Status der Datenbank wiederherzustellen. Dieses Handbuch enthält Informationen zur physischen und logischen Architektur des Transaktionsprotokolls. Eine gute Kenntnis der Architektur kann Ihnen dabei helfen, Transaktionsprotokolle effizienter zu verwalten.  

  
##  <a name="Logical_Arch"></a> Logische Architektur des Transaktionsprotokolls  

 Das [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Transaktionsprotokoll wird logisch so verwendet, als handele es sich um eine Folge von Protokolleinträgen. Jeder Protokolleintrag wird durch eine Protokollsequenznummer (LSN, Log Sequence Number) gekennzeichnet. Jeder neue Protokolleintrag wird an das logische Ende des Protokolls geschrieben und erhält eine LSN, die höher ist als die LSN des vorherigen Eintrags. Protokolleinträge werden nacheinander in der Reihenfolge ihres Erstellens gespeichert. Jeder Protokolleintrag enthält die ID der Transaktion, zu der er gehört. Für jede Transaktion werden alle Protokolleinträge, die mit dieser Transaktion verbunden sind, individuell zu einer Kette verknüpft. Dies erfolgt mithilfe von Rückwärtszeigern, durch die der Rollback der Transaktion beschleunigt wird.  
  
 Protokolleinträge für Datenänderungen zeichnen entweder die durchgeführte logische Operation oder die Anfangs- und Endimages der geänderten Daten auf. Ein Anfangsimage ist eine Kopie der Daten vor der Durchführung der Operation. Ein Endimage ist eine Kopie der Daten, nachdem die Operation durchgeführt wurde.  
  
 Die Schritte zum Wiederherstellen einer Operation hängen von der Art des Protokolleintrags ab:  
  
-   Protokollierung der logischen Operation  
  
    -   Um einen Rollforward für die logische Operation auszuführen, wird sie erneut durchgeführt.  
  
    -   Um einen Rollback für die logische Operation auszuführen, wird der logische Umkehrvorgang durchgeführt.  
  
-   Protokollierung der Anfangs- und Endimages  
  
    -   Um einen Rollforward für die Operation auszuführen, wird das Endimage übernommen.  
  
    -   Um einen Rollback für die Operation auszuführen, wird das Anfangsimage übernommen.  
  
 Im Transaktionsprotokoll werden viele Operationsarten aufgezeichnet. Dazu zählen die Operationen:  
  
-   Der Beginn und das Ende jeder Transaktion.  
  
-   Jede Datenänderung (Einfügung, Update oder Löschung). Hierzu zählen auch Änderungen, die von gespeicherten Systemprozeduren oder DDL-Anweisungen (Data Definition Language, Datendefinitionssprache) an beliebigen Tabellen, einschließlich den Systemtabellen, vorgenommen werden.  
  
-   Jede Zuordnung oder Zuordnungsaufhebung von Blöcken und Seiten  
  
-   Erstellen oder Löschen einer Tabelle oder eines Indexes.  
  
 Rollback-Operationen werden ebenfalls protokolliert. Jede Transaktion reserviert Speicherplatz im Transaktionsprotokoll, um sicherzustellen, dass ausreichend Speicherplatz vorhanden ist, um einen Rollback infolge einer expliziten Rollback-Anweisung oder im Falle eines Fehlers zu unterstützen. Die Menge des reservierten Speicherplatzes hängt von den in der Transaktion durchgeführten Vorgängen ab, entspricht jedoch im Allgemeinen dem Speicherplatz, der zum Protokollieren der einzelnen Vorgänge verwendet wird. Dieser reservierte Speicherplatz wird freigegeben, sobald die Transaktion abgeschlossen ist.  
  
 Als aktiver Teil des Protokolls bzw. *aktives Protokoll*wird der Abschnitt der Protokolldatei aus dem ersten Protokolleintrag bezeichnet, der für einen erfolgreichen Rollback der gesamten Datenbank auf den zuletzt geschriebenen Protokolleintrag benötigt wird. Dies ist der Teil des Protokolls, der für eine vollständige Wiederherstellung der Datenbank erforderlich ist. Vom aktiven Teil des Protokolls kann niemals ein Teil abgeschnitten werden. Die Protokollfolgenummer (Log Sequence Number, LSN) des ersten Protokolldatensatzes wird als Mindestwiederherstellungs-LSN (*MinLSN*) bezeichnet.  
  
##  <a name="physical_arch"></a> Physische Architektur des Transaktionsprotokolls  

 Das Transaktionsprotokoll in einer Datenbank erstreckt sich über eine oder mehrere physische Dateien. Konzeptionell ist die Protokolldatei eine Folge von Protokolldatensätzen. Physisch wird die Folge von Protokolldatensätzen effizient in dem Satz physischer Dateien gespeichert, die das Transaktionsprotokoll implementieren. Für jede Datenbank muss mindestens eine Protokolldatei vorhanden sein.  
  
 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] teilt jede physische Protokolldatei intern in mehrere virtuelle Protokolldateien auf. Virtuelle Protokolldateien haben keine feste Größe, und es gibt keine feststehende Anzahl virtueller Protokolldateien für eine physische Protokolldatei. [!INCLUDE[ssDE](../includes/ssde-md.md)] wählt die Größe der virtuellen Protokolldateien dynamisch beim Erstellen oder Erweitern von Protokolldateien aus. [!INCLUDE[ssDE](../includes/ssde-md.md)] versucht, immer nur eine kleine Anzahl virtueller Dateien aufrechtzuerhalten. Welche Größe die virtuellen Dateien haben, nachdem eine Protokolldatei erweitert wurde, hängt von der zusammengenommenen Größe des vorhandenen Protokolls und dem Umfang der Dateierweiterung ab. Die Größe oder Anzahl der virtuellen Protokolldateien kann nicht von Administratoren konfiguriert oder festgelegt werden.  
  
 Virtuelle Protokolldateien wirken sich nur dann auf die Systemleistung aus, wenn die physischen Protokolldateien mit geringen Werten für *size* und *growth_increment* definiert sind. Der *size* -Wert entspricht der Anfangsgröße der Protokolldatei und der *growth_increment* -Wert der Menge von Speicherplatz, die der Datei immer dann hinzugefügt wird, wenn neuer Speicherplatz erforderlich wird. Wenn die Protokolldateien durch viele kleine Schritte auf eine beträchtliche Größe anwachsen, enthalten sie zahlreiche virtuelle Protokolldateien. Hierdurch werden möglicherweise das Starten der Datenbank sowie Protokollsicherungs- und -wiederherstellungsvorgänge verlangsamt. Es wird empfohlen, den Protokolldateien einen *size*-Wert zuzuweisen, der ungefähr der endgültigen erforderlichen Größe entspricht, und darüber hinaus einen relativ hohen Wert für *growth_increment* festzulegen. Weitere Informationen zu diesen Parametern finden Sie unter [ALTER DATABASE-Optionen für Dateien und Dateigruppen &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options).  
  
 Das Transaktionsprotokoll ist eine umbrechende Protokolldatei. Nehmen Sie beispielsweise an, eine Datenbank verfügt über eine physische Protokolldatei, die in vier virtuelle Protokolldateien unterteilt ist. Wenn die Datenbank erstellt wird, beginnt die logische Protokolldatei am Anfang der ersten physischen Protokolldatei. Neue Protokolldatensätze werden am Ende des logischen Protokolls hinzugefügt, das in Richtung des Endes des physischen Protokolls erweitert wird. Beim Abschneiden eines Protokolls werden alle virtuellen Protokolle freigegeben, deren Datensätze sich ohne Ausnahme vor der Mindestwiederherstellungs-Protokollfolgenummer (Minimum Recovery Log Sequence Number, MinLSN) befinden. *MinLSN* ist die Protokollfolgenummer des ältesten Protokolldatensatzes, der für einen erfolgreichen Rollback der gesamten Datenbank benötigt wird. Das Transaktionsprotokoll in der Beispieldatenbank würde in etwa so aussehen wie das Protokoll in der folgenden Abbildung.  
  
 ![Protokolldatei unterteilt in vier virtuelle Protokolldateien](media/tranlog3.gif "Protokolldatei unterteilt in vier virtuelle Protokolldateien")  
  
 Wenn das Ende des logischen Protokolls das Ende der physischen Protokolldatei erreicht, erfolgt ein Umbruch, und neue Protokolldatensätze werden nun wieder am Anfang der physischen Protokolldatei eingefügt.  
  
 ![Protokolldatensätze Wrap rund um auf den Anfang der Protokolldatei](media/tranlog4.gif "Protokolldatensätze umschließen etwa zum Starten der Protokolldatei")  
  
 Solange das Ende des logischen Protokolls nicht den Anfang des logischen Protokolls erreicht, wird dieser Kreislauf endlos wiederholt. Wenn die alten Protokolldatensätze häufig genug abgeschnitten werden, um ausreichend Platz für alle neuen Protokolldatensätze freizugeben, die bis zum nächsten Prüfpunkt erstellt werden, wird das Protokoll nie vollständig aufgefüllt. Wenn das Ende des logischen Protokolls jedoch den Anfang des logischen Protokolls erreicht, wird eine der beiden folgenden Aktionen eingeleitet:  
  
-   Wenn die FILEGROWTH-Einstellung für das Protokoll aktiviert und auf dem Datenträger Speicherplatz verfügbar ist, wird die Datei um die Menge vergrößert, die im *growth_increment*-Parameter angegeben ist, und der Erweiterung werden neue Protokolldatensätze hinzugefügt. Weitere Informationen zur FILEGROWTH-Einstellung finden Sie unter [ALTER DATABASE-Optionen für Dateien und Dateigruppen &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options).  
  
-   Wenn die FILEGROWTH-Einstellung nicht aktiviert ist oder der Datenträger mit der Protokolldatei über weniger freien Speicherplatz verfügt als in *growth_increment* angegeben, wird der Fehler 9002 generiert.  
  
 Wenn das Protokoll mehrere physische Protokolldateien enthält, durchläuft das logische Protokoll alle physischen Protokolldateien, bevor es umbricht und neue Einträge am Anfang der ersten physischen Protokolldatei einfügt.  
  
### <a name="log-truncation"></a>Protokollkürzung  

 Die Protokollkürzung ist wichtig, um ein Auffüllen des Protokolls verhindern zu können. Durch die Protokollkürzung werden inaktive virtuelle Protokolldateien aus dem logischen Transaktionsprotokoll einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenbank gelöscht, wodurch Speicherplatz im logischen Protokoll zur Wiederverwendung durch das physische Transaktionsprotokoll freigegeben wird. Wird ein Transaktionsprotokoll nicht gekürzt, füllt sich dadurch möglicherweise der gesamte Speicherplatz des Datenträgers auf, der den zugehörigen physischen Protokolldateien zugeordnet ist. Bevor das Protokoll jedoch gekürzt werden kann, ist ein Prüfpunktvorgang erforderlich. Durch einen Prüfpunktvorgang werden die aktuellen, im Arbeitsspeicher geänderten Seiten (auch als modifizierte Seiten bezeichnet) sowie Transaktionsprotokollinformationen vom Arbeitsspeicher auf den Datenträger geschrieben. Beim Ausführen des Prüfpunkts wird der inaktive Teil des Transaktionsprotokolls als wiederverwendbar markiert. Anschließend kann der inaktive Teil durch Abschneiden des Protokolls freigegeben werden. Weitere Informationen zu Prüfpunkten finden Sie unter [Datenbankprüfpunkte &#40;SQL Server&#41;](../relational-databases/logs/database-checkpoints-sql-server.md).  
  
 Die folgenden Abbildungen zeigen ein Transaktionsprotokoll vor und nach dem Abschneiden. In der ersten Abbildung wird ein Transaktionsprotokoll gezeigt, das noch nie abgeschnitten wurde. Aktuell verwendet das logische Protokoll vier virtuelle Protokolldateien. Das logische Protokoll beginnt am Anfang der ersten virtuellen Protokolldatei und endet beim virtuellen Protokoll 4. Der MinLSN-Datensatz befindet sich im virtuellen Protokoll 3. Das virtuelle Protokoll 1 und das virtuelle Protokoll 2 enthalten nur inaktive Protokolldatensätze. Diese Datensätze können abgeschnitten werden. Das virtuelle Protokoll 5 wurde noch nicht verwendet und ist nicht Teil des aktuellen logischen Protokolls.  
  
 ![Transaktionsprotokoll mit vier virtuellen Protokollen](media/tranlog2.gif "Transaktionsprotokoll mit vier virtuellen Protokollen")  
  
 Die zweite Abbildung zeigt das Protokoll, nachdem es abgeschnitten wurde. Die virtuellen Protokolle 1 und 2 wurden für die Wiederverwendung freigegeben. Das logische Protokoll beginnt nun am Anfang des virtuellen Protokolls 3. Das virtuelle Protokoll 5 wurde noch nicht verwendet und ist nicht Teil des aktuellen logischen Protokolls.  
  
 ![Protokolldatei unterteilt in vier virtuelle Protokolldateien](media/tranlog3.gif "Protokolldatei unterteilt in vier virtuelle Protokolldateien")  
  
 Die Protokollkürzung erfolgt automatisch wie folgt, außer es tritt aus irgendeinem Grund eine Verzögerung auf:  
  
-   Unter dem einfachen Wiederherstellungsmodell, nach einem Prüfpunkt.  
  
-   Unter dem vollständigen oder massenprotokollierten Wiederherstellungsmodell, nach einer Protokollsicherung, wenn seit der vorherigen Sicherung ein Prüfpunkt aufgetreten ist.  
  
 Die Protokollkürzung kann durch verschiedene Faktoren verzögert werden. Im Falle einer langen Verzögerung der Protokollkürzung kann sich das Transaktionsprotokoll füllen. Weitere Informationen finden Sie unter [Faktoren, die die Protokollkürzung verzögern können](../relational-databases/logs/the-transaction-log-sql-server.md#FactorsThatDelayTruncation) und [Problembehandlung bei vollen Transaktionsprotokollen &#40;SQL Server Error 9002&#41;](../relational-databases/logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md).  
  
##  <a name="WAL"></a> Write-Ahead-Transaktionsprotokoll  

 In diesem Abschnitt wird die Aufgabe des Write-Ahead-Transaktionsprotokolls beim Aufzeichnen von Datenänderungen auf dem Datenträger beschrieben. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] verwendet ein Write-Ahead-Protokoll, durch das sichergestellt wird, dass Datenänderungen erst dann auf den Datenträger geschrieben werden, nachdem der entsprechende Protokolldatensatz auf den Datenträger geschrieben wurde. Dies schützt die ACID-Eigenschaften einer Transaktion.  
  
 Um die Funktionsweise des Write-Ahead-Protokolls zu verstehen, müssen Sie zunächst wissen, wie geänderte Daten auf den Datenträger geschrieben werden. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] verwaltet einen Puffercache, in den Datenseiten gelesen werden, wenn Daten abgerufen werden müssen. Eine Seite, die im Puffercache geändert wurde, wird nicht sofort auf den Datenträger geschrieben, sondern als *geändert*markiert. Auf einer Datenseite können mehrere logische Schreibvorgänge ausgeführt werden, bevor sie physisch auf den Datenträger geschrieben wird. Für jeden logischen Schreibvorgang wird ein Transaktionsprotokoll-Datensatz in den Protokollcache geschrieben, der die Änderung aufzeichnet. Die Protokolldatensätze müssen auf den Datenträger geschrieben werden, bevor die zugehörige modifizierte Seite aus dem Puffercache entfernt und auf den Datenträger geschrieben wird. Mit dem Prüfpunktprozess (checkpoint) wird der Puffercache regelmäßig auf Puffer mit Seiten aus einer angegebenen Datenbank überprüft, und alle modifizierten Seiten werden auf den Datenträger geschrieben. Durch Prüfpunkte kann bei einer späteren Wiederherstellung Zeit eingespart werden, da ein Punkt erstellt wird, an dem auf jeden Fall alle modifizierten Seiten auf den Datenträger geschrieben worden sind.  
  
 Wird eine geänderte Datenseite aus dem Puffercache auf den Datenträger geschrieben, wird dies als Leeren der Seite bezeichnet. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Durch die Logik von wird verhindert, dass eine geänderte Seite geleert wird, bevor der zugehörige Protokolldatensatz geschrieben wurde. Protokolldatensätze werden auf den Datenträger geschrieben, wenn ein Commit für die Transaktionen ausgeführt wird.  
  
##  <a name="Backups"></a> Transaktionsprotokollsicherungen  

 In diesem Abschnitt werden Konzepte zum Sichern und Wiederherstellen (Anwenden) von Transaktionsprotokollen vorgestellt. Beim vollständigen und beim massenprotokollierten Wiederherstellungsmodell müssen zur Wiederherstellung von Daten routinemäßige Sicherungen der Transaktionsprotokolle (*Protokollsicherungen*) ausgeführt werden. Sie können das Protokoll sichern, während eine vollständige Sicherung ausgeführt wird. Weitere Informationen zu Wiederherstellungsmodellen finden Sie unter [Sichern und Wiederherstellen von SQL Server-Datenbanken](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).  
  
 Bevor Sie die erste Protokollsicherung erstellen können, müssen Sie eine vollständige Sicherung erstellen, z. B. eine Datenbanksicherung oder die erste von mehreren Dateisicherungen. Die Wiederherstellung einer Datenbank, für die nur Dateisicherungen verwendet werden, kann komplex werden. Deshalb wird empfohlen, wenn möglich mit einer vollständigen Datenbanksicherung zu beginnen. Anschließend ist das regelmäßige Sichern des Transaktionsprotokolls erforderlich. Dadurch wird nicht nur die Gefahr von Datenverlusten minimiert, sondern es wird auch die Kürzung des Transaktionsprotokolls ermöglicht. Üblicherweise wird das Transaktionsprotokoll nach jeder konventionellen Protokollsicherung abgeschnitten.  
  
 Es wird empfohlen, entsprechend Ihren Geschäftsanforderungen ausreichend häufige Protokollsicherungen auszuführen. Die Häufigkeit sollte sich danach richten, inwiefern Sie Datenverlust (beispielsweise durch ein beschädigtes Protokolllaufwerk) tolerieren können. Beim Festlegen einer geeigneten Häufigkeit gilt es, einen Kompromiss aus Ihrer Toleranz gegenüber der Gefahr von Datenverlust und Ihrer Fähigkeit zum Speichern, Verwalten und zum möglichen Wiederherstellen von Protokollsicherungen zu finden. Es kann ausreichen, alle 15 bis 30 Minuten eine Protokollsicherung auszuführen. Wenn es für Ihr Geschäft erforderlich ist, die Gefahr des Datenverlusts zu minimieren, können Sie Protokollsicherungen häufiger ausführen. Häufigere Protokollsicherungen bieten zusätzlich den Vorteil, dass das Protokoll häufiger abgeschnitten wird, wodurch kleinere Protokolldateien entstehen.  
  
 Um die Anzahl der zum Wiederherstellen benötigten Protokollsicherungen zu begrenzen, ist es wichtig, Daten regelmäßig zu sichern. Beispielsweise können Sie eine wöchentliche vollständige Datenbanksicherung und tägliche differenzielle Datenbanksicherungen planen.  
  
### <a name="the-log-chain"></a>Die Protokollkette  

 Eine fortlaufende Abfolge von Protokollsicherungen wird als *Protokollkette*bezeichnet. Eine Protokollkette beginnt mit einer vollständigen Sicherung der Datenbank. Gewöhnlich wird eine neue Protokollkette nur gestartet, wenn die Datenbank zum ersten Mal gesichert wird oder wenn vom einfachen zum vollständigen oder massenprotokollierten Wiederherstellungsmodell gewechselt wird. Die bestehende Protokollkette bleibt intakt, es sei denn, Sie überschreiben beim Erstellen einer vollständigen Datenbanksicherung bestehende Sicherungssätze. Mit einer intakten Protokollkette können Sie Ihre Datenbank aus einer beliebigen vollständigen Datenbanksicherung im Mediensatz wiederherstellen, gefolgt von allen weiteren Protokollsicherungen bis zum Wiederherstellungspunkt. Der Wiederherstellungspunkt kann das Ende der letzten Protokollsicherung oder ein bestimmter Wiederherstellungspunkt in einer beliebigen Protokollsicherung sein. Weitere Informationen finden Sie unter [Transaktionsprotokollsicherungen &#40;SQL Server&#41;](../relational-databases/backup-restore/transaction-log-backups-sql-server.md).  
  
 Um eine Datenbank bis zu dem Punkt, an dem ein Fehler aufgetreten ist, wiederherzustellen, muss die Protokollkette intakt sein. Das heißt, eine ununterbrochene Sequenz von Transaktionsprotokollsicherungen muss sich bis zum Zeitpunkt des Fehlers erstrecken. Wo diese Protokollsequenz anfangen muss, richtet sich nach dem Typ der Datensicherungen, die Sie wiederherstellen: Datenbank-, Teil- oder Dateisicherung. Bei einer Datenbank- oder Teilsicherung muss die Sequenz der Protokollsicherungen am Ende einer Datenbank- oder Teilsicherung beginnen. Bei einer Gruppe von Dateisicherungen muss die Sequenz der Protokollsicherungen mit dem Anfang einer vollständigen Gruppe von Dateisicherungen beginnen. Weitere Informationen finden Sie unter [Anwenden von Transaktionsprotokollsicherungen &#40;SQL Server&#41;](../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md).  
  
### <a name="restore-log-backups"></a>Wiederherstellen von Protokollsicherungen  

 Beim Wiederherstellen einer Protokollsicherung wird ein Rollforward für die im Transaktionsprotokoll aufgezeichneten Änderungen ausgeführt, um den genauen Zustand der Datenbank zu dem Zeitpunkt, als der Protokollsicherungsvorgang gestartet wurde, wiederherzustellen. Wenn Sie eine Datenbank wiederherstellen, müssen Sie die Protokollsicherungen wiederherstellen, die nach der vollständigen Datenbanksicherung erstellt wurden, die Sie wiederherstellen, oder die Protokollsicherungen ab dem Start der ersten Dateisicherung, die Sie wiederherstellen. Nach dem Wiederherstellen der aktuellsten Daten oder der aktuellsten differenziellen Sicherung müssen Sie normalerweise eine Reihe von Protokollsicherungen wiederherstellen, bis Sie den Wiederherstellungspunkt erreichen. Dann stellen Sie die Datenbank wieder her. Dabei wird ein Rollback aller Transaktionen ausgeführt, die beim Start der Wiederherstellung unvollständig waren, und die Datenbank wird online geschaltet. Nach der Wiederherstellung der Datenbank können keine weiteren Sicherungen wiederhergestellt werden. Weitere Informationen finden Sie unter [Anwenden von Transaktionsprotokollsicherungen &#40;SQL Server&#41;](../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md).  
  
## <a name="additional-reading"></a>Zusätzliches Lesematerial  

 In den folgenden empfohlenen Artikeln und Büchern finden Sie zusätzliche Informationen zu Transaktionsprotokollen.  
  
 [Grundlegendes zur Protokollierung und Wiederherstellung in SQL Server von Paul Randall](https://technet.microsoft.com/magazine/2009.02.logging.aspx)  
  
 [Verwaltung von SQL Server-Transaktionsprotokollen von Tony Davis und Gail Shaw](http://www.simple-talk.com/books/sql-books/sql-server-transaction-log-management-by-tony-davis-and-gail-shaw/)  
  
  
