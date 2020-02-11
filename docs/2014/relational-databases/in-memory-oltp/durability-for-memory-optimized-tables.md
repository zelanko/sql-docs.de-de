---
title: Dauerhaftigkeit für speicheroptimierte Tabellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: d304c94d-3ab4-47b0-905d-3c8c2aba9db6
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 3a35d5cdb9db4c56579a4229b2d08014a99da542
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63072753"
---
# <a name="durability-for-memory-optimized-tables"></a>Dauerhaftigkeit für speicheroptimierte Tabellen
  
  [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] bietet vollständige Dauerhaftigkeit für speicheroptimierte Tabellen. Wenn für eine Transaktion, durch die eine speicheroptimierte Tabelle geändert wurde, ein Commit ausgeführt wird, gewährleistet [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (genauso wie bei datenträgerbasierten Tabellen), dass die Änderungen dauerhaft sind (bei einem Neustart der Datenbank erhalten bleiben), vorausgesetzt der zugrunde liegende Speicher ist verfügbar. Die Dauerhaftigkeit basiert auf zwei Hauptmechanismen: der Transaktionsprotokollierung und der dauerhaften Speicherung von Datenänderungen auf einem Datenträger.  
  
## <a name="transaction-log"></a>Transaktionsprotokoll  
 Alle Änderungen, die an datenträgerbasierten oder dauerhaften speicheroptimierten Tabellen vorgenommen werden, werden in einem oder mehreren Transaktionsprotokoll-Datensätzen erfasst. Wenn für eine Transaktion ein Commit ausgeführt wird, werden die mit der Transaktion verknüpften Protokolldatensätze von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf den Datenträger geschrieben, bevor der Anwendung oder Benutzersitzung mitgeteilt wird, dass der Commit für die Transaktion abgeschlossen wurde. So wird sichergestellt, dass die von der Transaktion vorgenommenen Änderungen dauerhaft sind. Das Transaktionsprotokoll für speicheroptimierte Tabellen ist vollständig in den Protokolldatenstrom integriert, der auch von datenträgerbasierten Tabellen verwendet wird. Durch diese Integration sind vorhandene, für das Transaktionsprotokoll ausgeführte Sicherungs- und Wiederherstellungsvorgänge ohne zusätzliche Schritte weiterhin funktionsfähig. Da der Transaktionsdurchsatz der Arbeitsauslastung durch [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] jedoch deutlich anwachsen kann, müssen Sie sicherstellen, dass der Transaktionsprotokollspeicher für die Verarbeitung der erhöhten E/A-Anforderungen entsprechend konfiguriert wird.  
  
## <a name="data-and-delta-files"></a>Daten- und Änderungsdateien  
 Die Daten in speicheroptimierten Tabellen werden als Freiform-Datenzeilen gespeichert, die durch mindestens einen Index im Arbeitsspeicher verknüpft sind. Datenzeilen weisen im Gegensatz zu datenträgerbasierten Tabellen keine Seitenstrukturen auf. Sobald von der Anwendung ein Commit für die Transaktion ausgeführt werden kann, werden die Protokolldatensätze für die Transaktion von [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] generiert. Die Persistenz speicheroptimierter Tabellen wird mit einer Reihe von Daten- und Änderungsdateien unter Verwendung eines Hintergrundthreads erzielt. Die Daten- und Änderungsdateien sind in einem oder mehreren Containern enthalten (und nutzen denselben Mechanismus wie für FILESTREAM-Daten). Diese Container werden einer neuen Art von Dateigruppe, einer sogenannten speicheroptimierten Dateigruppe, zugeordnet.  
  
 Daten werden in diese Dateien streng sequenziell geschrieben. Dadurch wird die Datenträgerlatenz für herkömmliche Medien minimiert. Sie können mehrere Container auf verschiedenen Datenträgern verwenden, um die E/A-Aktivität zu verteilen. Daten- und Änderungsdateien in mehreren Containern auf verschiedenen Datenträgern verbessern die Wiederherstellungsleistung, wenn Daten aus den Daten- und Änderungsdateien auf dem Datenträger in den Arbeitsspeicher gelesen werden.  
  
 Eine Anwendung greift nicht direkt auf Daten- und Änderungsdateien zu. Alle Datenlese- und -schreibvorgänge verwenden speicherinterne Daten.  
  
### <a name="the-data-file"></a>Die Datendatei  
 Eine Datendatei enthält Zeilen aus einer oder mehreren speicheroptimierten Tabellen, die von mehreren Transaktionen im Rahmen eines INSERT- oder UPDATE-Vorgangs eingefügt wurden. Beispielsweise können eine Zeile aus der speicheroptimierten Tabelle T1 und die nächste Zeile aus der speicheroptimierten Tabelle T2 stammen. Die Zeilen werden an die Datendatei in der Transaktionsreihenfolge im Transaktionsprotokoll angefügt, sodass sequenzieller Datenzugriff gewährleistet wird. Dies ermöglicht im Vergleich zu zufälliger E/A einen erheblich besseren E/A-Durchsatz. Auf Computern mit einer Arbeitsspeicherkapazität über 16 GB beträgt die Größe jeder Datendatei ungefähr 128 MB, und auf Computern mit einer Arbeitsspeicherkapazität bis 16 GB beträgt die Größe 16 MB. Sobald die Datendatei voll ist, werden die Zeilen, die durch neue Transaktionen eingefügt werden, in einer weiteren Datendatei gespeichert. Im Laufe der Zeit werden die Zeilen aus dauerhaften speicheroptimierten Tabellen in einer oder mehreren Datendateien gespeichert, die Zeilen aus einem disjunkten, aber zusammenhängenden Bereich von Transaktionen enthalten. Beispielsweise enthält eine Datendatei, deren Zeitstempel für den Transaktionscommit im Bereich (100, 200) liegt, alle Zeilen, die von Transaktionen mit einem Commitzeitstempel größer als 100 und kleiner oder gleich 200 eingefügt wurden. Beim Commitzeitstempel handelt es sich um eine monoton ansteigende Zahl, die einer Transaktion zugewiesen wird, sobald sie für den Commit bereit ist. Jede Transaktion besitzt einen eindeutigen Commitzeitstempel.  
  
 Wenn eine Zeile gelöscht oder aktualisiert wird, wird die Zeile in der Datendatei nicht entfernt oder direkt geändert. Stattdessen werden die gelöschten Zeilen in einem anderen Typ von Datei, der Änderungsdatei, nachverfolgt. Updatevorgänge werden für jede einzelne Zeile als Tupel von Lösch- und Einfügevorgängen verarbeitet. Dadurch werden zufällige E/A-Vorgänge für die Datendatei verhindert.  
  
### <a name="the-delta-file"></a>Die Änderungsdatei  
 Jeder Datendatei ist eine entsprechende Änderungsdatei zugeordnet, die den gleichen Transaktionsbereich besitzt und die gelöschten Zeilen nachverfolgt, die von Transaktionen im Transaktionsbereich eingefügt wurden. Die Daten- und Änderungsdatei wird als Prüfpunktdateipaar (CFP, Checkpoint File Pair) bezeichnet. Sie stellt die Zuordnungs- und die Zuordnungsaufhebungseinheit sowie die Einheit für Zusammenführungsvorgänge dar. Beispielsweise werden in einer Änderungsdatei, die dem Transaktionsbereich (100, 200) entspricht, gelöschte Zeilen gespeichert, die von Transaktionen im Bereich (100, 200) eingefügt wurden. Genau wie bei Datendateien wird auf Änderungsdateien sequenziell zugegriffen.  
  
 Wenn eine Zeile gelöscht wird, wird die Zeile nicht aus der Datendatei entfernt, sondern es wird ein Verweis auf die Zeile an die Änderungsdatei angefügt, die dem Transaktionsbereich zugeordnet ist, in dem diese Zeile eingefügt wurde. Da die zu löschende Zeile bereits in der Datendatei vorhanden ist, werden in der Änderungsdatei nur die Verweisinformationen `{inserting_tx_id, row_id, deleting_tx_id }` gespeichert, und sie folgt dabei der Reihenfolge der ursprünglichen DELETE- oder UPDATE-Vorgänge im Transaktionsprotokoll.  
  
## <a name="populating-data-and-delta-files"></a>Auffüllen von Daten- und Änderungsdateien  
 Daten- und Änderungsdateien werden von einem Hintergrundthread aufgefüllt, der Offline-Prüfpunkt genannt wird. Dieser Thread liest die Datensätze des Transaktionsprotokolls, die von Transaktionen für speicheroptimierte Tabellen generiert wurden, für die ein Commit ausgeführt wurde. Die Informationen über die eingefügten und gelöschten Zeilen werden an die entsprechenden Daten- und Änderungsdateien angehängt. Im Gegensatz zu datenträgerbasierte Tabellen, bei denen Daten-/Indexseiten in zufälligen E/A-Vorgängen nach einem Prüfpunkt geleert werden, wird die Persistenz von speicheroptimierten Tabellen in einem kontinuierlichen Hintergrundvorgang erreicht. Es wird auf mehrere Änderungsdateien zugegriffen, da alle Zeilen, die durch beliebige vorherige Transaktionen eingefügt wurden, durch eine Transaktion gelöscht oder aktualisiert werden können. Löschinformationen werden immer am Ende der Änderungsdatei angefügt. Eine Transaktion mit einem Commitzeitstempel von 600 fügt eine neue Zeile ein und löscht Zeilen, die durch Transaktionen mit einem Commitzeitstempel von 150, 250 und 450 eingefügt wurden, wie in der Abbildung unten dargestellt. Alle vier Datei-E/A-Vorgänge (drei für gelöschte Zeilen und einer für neu eingefügte Zeilen) sind reine Anfügungen an die entsprechenden Änderungs- und Datendateien.  
  
 ![Lesen Sie die Protokolldatensätze für speicheroptimierte Tabellen.](../../database-engine/media/read-logs-hekaton.gif "Lesen Sie die Protokolldatensätze für speicheroptimierte Tabellen.")  
  
## <a name="accessing-data-and-delta-files"></a>Zugreifen auf Daten- und Änderungsdateien  
 Auf Daten-/Änderungsdateipaare wird in den folgenden Fällen zugegriffen:  
  
 Offline-Prüfpunktthread  
 Durch diesen Thread werden Einfügungen und Löschungen in speicheroptimierte Datenzeilen an die entsprechenden Daten-/Änderungsdateipaare angefügt.  
  
 Zusammenführungsvorgang  
 Der Vorgang führt eines oder mehrere Daten-/Änderungsdateipaare zusammen und erstellt ein neues Daten-/Änderungsdateipaar.  
  
 Während der Wiederherstellung nach einem Systemabsturz  
 Wenn [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] neu gestartet wird oder die Datenbank wieder online geschaltet wird, werden die speicheroptimierten Daten unter Verwendung der Daten-/Änderungsdateipaare aufgefüllt. Die Änderungsdatei dient beim Lesen der Zeilen aus der entsprechenden Datendatei als Filter für die gelöschten Zeilen. Da alle Daten-/Änderungsdateipaare unabhängig sind, werden diese Dateien parallel geladen, um die Zeit zum Laden der Daten in den Arbeitsspeicher zu verkürzen. Sobald die Daten in den Arbeitsspeicher geladen wurden, wendet die In-Memory-OLTP-Engine die aktiven, von den Prüfpunktdateien noch nicht verarbeiteten Transaktionsprotokolldatensätze an, um die speicheroptimierten Daten zu vervollständigen.  
  
 Während des Wiederherstellungsvorgangs  
 Die In-Memory OLTP-Prüfpunktdateien werden aus der Datenbanksicherung erstellt. Anschließend wird mindestens eine Transaktionsprotokollsicherung angewendet. Wie bei der Wiederherstellung nach einem Systemabsturz lädt die In-Memory-OLTP-Engine Daten parallel in den Arbeitsspeicher, um die Auswirkungen auf die Wiederherstellungszeit zu minimieren.  
  
## <a name="merging-data-and-delta-files"></a>Zusammenführen von Daten- und Änderungsdateien  
 Die Daten für speicheroptimierte Tabellen werden in mindestens einem Daten-/Änderungsdateipaar gespeichert (auch als Prüfpunktdateipaar oder CFP (Checkpoint File Pair) bezeichnet). Eingefügte Zeilen werden in Datendateien gespeichert, und in Änderungsdateien werden Verweise auf gelöschte Zeilen gespeichert. Während der Ausführung einer OLTP-Arbeitsauslastung werden beim Aktualisieren, Einfügen und Löschen von Zeilen durch DML-Vorgänge neue CFPs erstellt, um die neuen Zeilen persistent zu speichern, und der Verweis auf die gelöschten Zeilen wird an die Änderungsdateien angefügt.  
  
 Die Metadaten aller zuvor geschlossen und derzeit aktiven CFPs werden in einer internen Arraystruktur gespeichert, die als Speicherarray bezeichnet wird. Dabei handelt es sich um ein Array von CFPs mit beschränkter Größe (8.192 Einträge). Die Reihenfolge der Einträge im Speicherarray richtet sich nach dem Transaktionsbereich. Die CFPs im Speicherarray (zusammen mit dem Protokollfragment) stellen den gesamten Status auf dem Datenträger dar, der erforderlich ist, um eine Datenbank mit speicheroptimierten Tabellen wiederherzustellen.  
  
 Bei DML-Vorgängen nimmt die Anzahl der CFPs im Laufe der Zeit zu, wodurch die maximale Kapazität des Speicherarrays erreicht wird und sich folgende Herausforderungen stellen:  
  
-   Gelöschte Zeilen.  Gelöschte Zeilen verbleiben in der Datendatei, werden aber in der entsprechenden Änderungsdatei als gelöscht gekennzeichnet. Diese Zeilen werden nicht mehr benötigt und werden aus dem Arbeitsspeicher entfernt. Wenn gelöschte Zeilen nicht aus CFPs entfernt werden, wird unnötigerweise Speicherplatz belegt, wodurch sich die Wiederherstellungszeit erhöhen würde.  
  
-   Speicherarray ist voll. Wenn im Speicherarray 8.000 Einträge zugeordnet sind (192 Arrayeinträge sind für konkurrierende, vorhandene Zusammenführungen oder manuelle Zusammenführungen reserviert), können keine neuen DML-Transaktionen für dauerhafte speicheroptimierte Tabellen ausgeführt werden. Nur Prüfpunkt- und MERGE-Operationen dürfen die verbleibenden Einträge verwenden. Dadurch wird sichergestellt, dass DML-Transaktionen das Array nicht füllen und dass einige Einträge im Array für die Zusammenführung vorhandener Dateien und die Freigabe von Speicherplatz im Array reserviert bleiben.  
  
-   Mehraufwand für Änderungen des Speicherarrays. Interne Prozesse durchsuchen das Speicherarray nach Vorgängen, z. B. um die Änderungsdatei zu finden, an die Informationen über eine gelöschte Zeile angehängt werden sollen. Der Aufwand dieser Vorgänge steigt mit der Anzahl der Einträge.  
  
 Zur Vermeidung dieser Ineffizienzen werden ältere geschlossene CFPs entsprechend der weiter unten beschriebenen Zusammenführungsrichtlinie zusammengeführt, sodass das Speicherarray komprimiert wird, um den gleichen Satz von Daten mit einer geringeren Anzahl von CFPs darzustellen.  
  
 Die Gesamtgröße aller dauerhaften Tabellen in einer Datenbank sollte im Arbeitsspeicher maximal 250 GB betragen. Dauerhafte Tabellen, die bis zu 250 GB Arbeitsspeicher nutzen, erfordern in der Annahme, dass Einfüge-, Lösch- und Updatevorgänge stattfinden, durchschnittlich 500 GB Speicherplatz. Zur Unterstützung von 500 GB Speicherplatz sind 4.000 Daten-/Änderungsdateipaare in der speicheroptimierten Dateigruppe erforderlich.  
  
 Ein kurzfristiger Anstieg der Datenbankaktivität kann zu einer Verzögerung von Prüfpunkt- und Zusammenführungsvorgängen führen, wodurch sich die Anzahl der erforderlichen Daten-/Änderungsdateipaare erhöht. Um kurzfristige Spitzen in der Datenbankaktivität auszugleichen, kann das Speichersystem bis zu 8.000 Daten-/Änderungsdateipaare mit einer maximalen Gesamtspeicherkapazität von 1 TB zuordnen. Nach Erreichen dieses Grenzwerts können in der Datenbank erst wieder neue Transaktionen ausgeführt werden, nachdem verzögerte Prüfpunktvorgänge aufgeholt wurden. Wenn die Größe dauerhafter Tabellen im Arbeitsspeicher längere Zeit über 250 GB liegt, kann der Grenzwert von 8.000 Dateipaaren erreicht werden.  
  
 Der Zusammenführungsvorgang akzeptiert als Eingabe eines oder mehrere angrenzende geschlossene CFPs (die sogenannte Zusammenführungsquelle) auf Grundlage einer intern definierten Zusammenführungsrichtlinie und erstellt ein resultierendes CFP (das sogenannte Zusammenführungsziel). Die Einträge in jeder Änderungsdatei der Quell-CFPs werden zum Filtern der Zeilen aus der entsprechenden Datendatei verwendet, um die nicht benötigten Datensätze zu entfernen. Die verbleibenden Zeilen in den Quell-CFPs werden zu einem Ziel-CFP zusammengefasst. Nach Abschluss des Zusammenführungsvorgangs werden die Quell-CFPs (Zusammenführungsquellen) durch das CFP des Zusammenführungsziels ersetzt. Die CFPs der Zusammenführungsquelle durchlaufen eine Übergangsphase, bevor sie aus dem Speicher entfernt werden.  
  
 Im Beispiel unten sind für die speicheroptimierte Tabellendateigruppe vier Daten-/Änderungsdateipaare mit Daten aus vorhergehenden Transaktionen bei Zeitstempel 500 vorhanden. Beispielsweise entsprechen die ersten Zeilen in der Datendatei Transaktionen mit einem Zeitstempel, der größer als 100 und kleiner oder gleich 200 ist, alternativ ausgedrückt als (100, 200). Die zweite und dritte Datendatei werden nach Berücksichtigung der als gelöscht gekennzeichneten Zeilen zu weniger als 50 % gefüllt angezeigt. Der Zusammenführungsvorgang kombiniert diese beiden CFPs und erstellt ein neues CFP mit Transaktionen, deren Zeitstempel größer als 200 und kleiner oder gleich 400 ist. Dies entspricht dem kombinierten Bereich dieser beiden CFPs. Es wird ein weiteres CFP mit dem Bereich (500, 600) angezeigt, und eine nicht leere Änderungsdatei für den Transaktionsbereich (200, 400) gibt an, dass der Zusammenführungsvorgang parallel zur Transaktionsaktivität erfolgen kann, einschließlich des Löschens mehrerer Zeilen aus den Quell-CFPs.  
  
 ![Diagramm zeigt eine speicheroptimierte Tabellendateigruppe an](../../database-engine/media/storagediagram-hekaton.png "Diagramm zeigt eine speicheroptimierte Tabellendateigruppe an")  
  
 In einem Hintergrundthread werden alle geschlossenen CFPs mithilfe einer Zusammenführungsrichtlinie ausgewertet und dann eine oder mehrere Zusammenführungsanforderungen für die qualifizierenden CFPs initiiert. Diese Zusammenführungsanforderungen werden vom Offline-Prüfpunktthread verarbeitet. Die Auswertung der Zusammenführungsrichtlinie erfolgt in regelmäßigen Abständen sowie beim Schließen eines Prüfpunkts.  
  
### <a name="includesssql14includessssql14-mdmd-merge-policy"></a>[!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]Merge-Richtlinie  
 
  [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] implementiert die folgende Zusammenführungsrichtlinie:  
  
-   Eine Zusammenführung wird geplant, wenn mindestens zwei aufeinanderfolgende CFPs konsolidiert werden können, nachdem gelöschte Zeilen berücksichtigt wurden, sodass die resultierenden Zeilen in einem CFP idealer Größe Platz finden. Die ideale CFP-Größe wird wie folgt bestimmt:  
  
    -   Wenn ein Computer 16 GB Arbeitsspeicher oder weniger aufweist, beträgt die Größe der Datendatei 16 MB und der Änderungsdatei 1 MB.  
  
    -   Wenn ein Computer mehr als 16 GB Arbeitsspeicher aufweist, beträgt die Größe der Datendatei 128 MB und der Änderungsdatei 16 MB.  
  
-   Ein einzelnes CFP kann mit sich selbst zusammengeführt werden, wenn die Datendatei 256 MB überschreitet und mehr als die Hälfte der Zeilen gelöscht werden. Eine Datendatei kann beispielsweise über 128 MB anwachsen, wenn durch eine einzelne oder mehrere gleichzeitige Transaktionen eine große Datenmenge eingefügt oder aktualisiert wird und die Vergrößerung der Datendatei über die ideale Größe hinaus erzwungen wird, weil eine Transaktion nicht auf mehrere CFPs verteilt werden kann.  
  
 Im Folgenden finden Sie einige Beispiele, die veranschaulichen, welche CFPs gemäß der Zusammenführungsrichtlinie zusammengeführt werden:  
  
|Angrenzende CFP-Quelldateien (% voll)|Zusammenführungsauswahl|  
|-------------------------------------------|---------------------|  
|CFP0 (30 %), CFP1 (50 %), CFP2 (50 %), CFP3 (90 %)|(CFP0, CFP1)<br /><br /> CFP2 wird nicht ausgewählt, da andernfalls die resultierende Datendatei größer als 100 % der idealen Größe wird.|  
|CFP0 (30 %), CFP1 (20 %), CFP2 (50 %), CFP3 (10 %)|(CFP0, CFP1, CFP2). Dateien werden von links nach rechts ausgewählt.<br /><br /> CTP3 wird nicht ausgewählt, da andernfalls die resultierende Datendatei größer als 100 % der idealen Größe wird.|  
|CFP0 (80 %), CFP1 (30 %), CFP2 (10 %), CFP3 (40 %)|(CFP1, CFP2, CFP3). Dateien werden von links nach rechts ausgewählt.<br /><br /> CFP0 wird übersprungen, da die resultierende Datendatei bei Kombination mit CFP1 größer als 100 % der idealen Größe wird.|  
  
 Nicht alle CFPs mit verfügbarem Speicherplatz kommen für die Zusammenführung infrage. Wenn beispielsweise zwei aufeinanderfolgende CFPs zu 60 % gefüllt sind, kommen sie für eine Zusammenführung nicht infrage, und jedes dieser CFPs weist 40 % nicht genutzten Speicherplatz auf. Im ungünstigsten Fall sind alle CFPs zu 50 % gefüllt, was einer Speicherauslastung von nur 50 % entspricht. Auch wenn die gelöschten Zeilen möglicherweise im Speicher vorhanden sind, da die CFPs für eine Zusammenführung nicht infrage kommen, wurden die gelöschten Zeilen möglicherweise bereits von der In-Memory-Garbage Collection aus dem Arbeitsspeicher entfernt. Die Verwaltung des Speichers und des Arbeitsspeichers erfolgt unabhängig von der Garbage Collection. Der Speicher, der von aktiven CFPs belegt wird (nicht alle CFPs werden aktualisiert), kann doppelt so groß wie bei dauerhaften Tabellen im Arbeitsspeicher ausfallen.  
  
 Bei Bedarf kann eine manuelle Zusammenführung explizit durch Aufrufen von [sys. sp_xtp_merge_checkpoint_files &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-merge-checkpoint-files-transact-sql)ausgeführt werden.  
  
### <a name="life-cycle-of-a-cfp"></a>Lebenszyklus eines CFP  
 CPFs durchlaufen mehrere Zustände, bevor ihre Zuordnung aufgehoben werden kann. CFPs können sich jeweils in einer der folgenden Phasen befinden: PRECREATED, UNDER CONSTRUCTION, ACTIVE, MERGE TARGET, MERGED SOURCE, REQUIRED FOR BACKUP/HA, IN TRANSITION TO TOMBSTONE und TOMBSTONE. Eine Beschreibung dieser Phasen finden Sie unter [sys.dm_db_xtp_checkpoint_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql).  
  
 Nach Berücksichtigung des von CFPs mit den verschiedenen Statusphasen belegten Speichers kann der insgesamt von dauerhaften speicheroptimierten Tabellen belegte Speicher deutlich mehr als das Doppelte der Größe der Tabellen im Arbeitsspeicher betragen. Die DMV [sys. dm_db_xtp_checkpoint_files &#40;Transact-SQL-&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql) kann abgefragt werden, um alle Cfps in der Speicher optimierten Datei Gruppe einschließlich ihrer Phase aufzulisten. Der Übergang von CFPs vom MERGE SOURCE-Status zum TOMBSTONE-Status und die abschließende Garbage Collection können bis zu fünf Prüfpunkte beanspruchen, wobei auf jeden Prüfpunkt eine Transaktionsprotokollsicherung folgt, wenn die Datenbank für das vollständige oder massenprotokollierte Wiederherstellungsmodell konfiguriert ist.  
  
 Sie können den Prüfpunkt gefolgt von einer Protokollsicherung manuell erzwingen, um die Garbage Collection zu beschleunigen. Dadurch werden jedoch 5 leere CFPs hinzugefügt (5 Daten-/Änderungsdateipaare mit einer jeweils 128 MB großen Datendatei). In Produktionsszenarien durchlaufen CFPs aufgrund der automatischen Prüfpunkte und Protokollsicherungen, die im Rahmen der Sicherungsstrategie ausgeführt werden, diese Phasen nahtlos, ohne dass ein manueller Eingriff erforderlich ist. Als Folge des Garbage Collection-Vorgangs weisen Datenbanken mit speicheroptimierten Tabellen gegenüber ihrer Größe im Arbeitsspeicher möglicherweise eine höhere Größe im Speicher auf. Es ist nicht ungewöhnlich, dass CFPs bis zu viermal so groß werden können wie die dauerhaften speicheroptimierten Tabellen im Arbeitsspeicher.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen und Verwalten von Speicher für speicheroptimierte Objekte](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
