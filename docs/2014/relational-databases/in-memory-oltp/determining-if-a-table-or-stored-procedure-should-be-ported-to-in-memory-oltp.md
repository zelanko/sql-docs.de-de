---
title: Bestimmen, ob eine Tabelle oder eine gespeicherte Prozedur zu In-Memory OLTP portiert werden soll | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
helpviewer_keywords:
- Analyze, Migrate, Report
- AMR
ms.assetid: c1ef96f1-290d-4952-8369-2f49f27afee2
author: rothja
ms.author: jroth
ms.openlocfilehash: 8e517cff394bc0c813e34763469f75147a0a16c5
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050242"
---
# <a name="determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp"></a>Bestimmen, ob eine Tabelle oder eine gespeicherte Prozedur zu In-Memory OLTP portiert werden soll
  Der Transaktions Leistungs Sammler in unter [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] stützt Sie bei der Auswertung, ob in-Memory-OLTP die Leistung Ihrer Datenbankanwendung verbessern wird. Der Transaktionsleistungsanalysebericht gibt außerdem an, wie viel Arbeit notwendig ist, um In-Memory OLTP in Ihrer Anwendung zu aktivieren. Nachdem Sie eine datenträgerbasierte Tabelle identifiziert haben, die Sie zur Verwendung von In-Memory-OLTP portieren, können Sie die Tabellenmigration mit dem [Ratgeber für die Speicheroptimierung](memory-optimization-advisor.md)vereinfachen. In ähnlicher Weise unterstützt Sie der [Ratgeber für native Kompilierung](native-compilation-advisor.md) bei der Portierung einer gespeicherten Prozedur in eine nativ kompilierte gespeicherte Prozedur.  
  
 In diesem Thema wird Folgendes erläutert:  
  
-   Konfigurieren des Verwaltungs-Data Warehouse  
  
-   Konfigurieren der Datensammlung  
  
-   Generieren von Transaktionsleistungsanalyseberichten, um leistungskritische Tabellen und gespeicherte Prozeduren zu identifizieren  
  
 Informationen zu Migrationsmethoden finden Sie unter [in-Memory OLTP-allgemeine Arbeits Auslastungs Muster und Überlegungen zur Migration](https://msdn.microsoft.com/library/dn673538.aspx).  
  
 Der Transaktionsleistungssammler und die Transaktionsleistungsanalyseberichte helfen Ihnen, die folgenden Aufgaben auszuführen:  
  
-   Analysieren Ihrer Arbeitsauslastung, um zu bestimmen, ob In-Memory OLTP die Leistung verbessert. Der Transaktionsleistungssammler sammelt und wertet die Leistungsmerkmale Ihrer Arbeitsauslastung aus. . Der Transaktionsleistungsanalysebericht empfiehlt Tabellen und gespeicherte Prozeduren, die von der Konvertierung in In-Memory OLTP am meisten profitieren würden.  
  
-   Hilfe bei der Planung und Durchführung der Migration zu In-Memory OLTP. Der Migrationspfad von einer datenträgerbasierten Tabelle zu einer speicheroptimierten Tabelle kann zeitaufwendig sein. Mit dem Ratgeber für die Speicheroptimierung können Sie Inkompatibilitäten in Ihrer Tabelle identifizieren, die Sie entfernen müssen, bevor Sie die Tabelle zu In-Memory OLTP verschieben. Der Ratgeber für die Speicheroptimierung gibt außerdem Aufschluss über die Auswirkungen, die die Migration einer Tabelle zu einer speicheroptimierten Tabelle auf Ihre Anwendung haben wird.  
  
     Sie können ermitteln, ob Ihre Anwendung von In-Memory OLTP profitieren würde. Außerdem können Sie OLTP verwenden, um die Migration zu In-Memory OLTP zu planen und um einige Ihrer Tabellen und gespeicherten Prozeduren zu In-Memory OLTP zu migrieren.  
  
    > [!IMPORTANT]  
    >  Die Leistung eines Datenbanksystems hängt von verschiedenen Faktoren ab, die jedoch nicht alle durch den Transaktionsleistungssammler beobachtet und gemessen werden können. Daher gewährleistet der Transaktionsleistungsanalysebericht nicht, dass die tatsächlichen Leistungssteigerungen den ggf. getroffenen Vorhersagen entsprechen.  
  
 Der Transaktions Leistungs Sammler und die Möglichkeit, einen Transaktions Leistungsanalyse Bericht zu generieren, werden installiert, wenn Sie bei der Installation von die Option **Verwaltungs Tools-einfach** oder **Verwaltungs Tools-erweitert** auswählen [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] .  
  
## <a name="best-practices"></a>Bewährte Methoden  
 Der empfohlene Workflow wird im folgenden Flussdiagramm veranschaulicht. Die gelben Knoten stellen optionale Prozeduren dar:  
  
 ![AMR-Workflow](../../database-engine/media/amr-1.gif "AMR-Workflow")  
  
 Sie können eine andere Methode verwenden, um eine Leistungsbasislinie zu erstellen, z. B. Leistungsindikatorprotokolle oder den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Aktivitätsmonitor. In der Leistungsbasislinie und in Ihren Vergleichen verwenden Sie folgende Informationen:  
  
-   CPU-Nutzung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
  
-   Arbeitsspeichernutzung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
  
-   E/A-Aktivität von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
  
-   Transaktionsdurchsatz der Instanz während der Verarbeitung von Transaktionen  
  
 Der Transaktionsleistungssammler zeichnet alle 15 Minuten Daten auf. Um aussagekräftige Ergebnisse zu erhalten, führen Sie den Transaktionsleistungssammler mindestens eine Stunde lang aus. Optimale Ergebnisse erhalten Sie, indem Sie den Transaktionsleistungssammler so lange ausführen, bis ausreichend Daten für Ihre primäre Szenarien erfasst wurden. Generieren Sie erst einen Transaktionsleistungsanalysebericht, nachdem Sie die Datensammlung abgeschlossen haben.  
  
 Konfigurieren Sie Transaktionsleistungssammler wie folgt: Das Tool sollte auf der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz in der Produktionsumgebung ausgeführt werden, und die Daten sollten auf einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz in der Entwicklungsumgebung (Testumgebung) gesammelt werden, um den Aufwand gering zu halten. Informationen zum Speichern von Daten in einer Verwaltungs Data Warehouse-Datenbank auf einer-Remote [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Instanz finden Sie unter [Konfigurieren der Datensammlung auf einer Remote SQL Server-Instanz](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md#xxx).  
  
## <a name="performance-impacts"></a>Auswirkungen auf die Leistung  
 Der Transaktionsleistungssammler besteht aus zwei Datensammlungssätzen:  
  
-   Analyse der Tabellenverwendung  
  
-   Analyse gespeicherter Prozeduren  
  
 Mit den Sammlungssätzen werden in Abständen von 15 Minuten Daten aus drei dynamischen Verwaltungssichten (DMVs) gesammelt. Anschließend werden die Daten in die als Verwaltungs-Data Warehouse konfigurierte Datenbank hochgeladen. Das Hochladen der gesammelten Daten wirkt sich nur minimal auf die Leistung aus.  
  
## <a name="use-the-transaction-performance-collector"></a>Verwenden des Transaktionsleistungssammlers  
 Für die folgenden Schritte ist [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] erforderlich.  
  
> [!IMPORTANT]  
>  Ändern Sie das Schema während der Profilerstellung nicht (beispielsweise durch Hinzufügen oder Entfernen von Datenbanken oder Erstellen oder Löschen von Tabellen). Wenn Sie das Schema einer Datenbank ändern, während Daten gesammelt werden, wird die Datenbank möglicherweise nicht korrekt in den Bericht eingeschlossen.  
  
### <a name="configure-management-data-warehouse"></a>Konfigurieren des Verwaltungs-Data Warehouse  
 Das Verwaltungs-Data Warehouse muss für den Transaktionsleistungssammler konfiguriert sein.  
  
 Die Version der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz, auf der Sie Daten sammeln (das Profil erstellen), sollte die gleiche Version oder eine niedrigere Version aufweisen als der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], auf dem das Verwaltungs-Data Warehouse konfiguriert ist.  
  
1.  Erweitern Sie im Objekt-Explorer den Knoten **Verwaltung**.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Datensammlung** , und wählen Sie **Tasks** und dann **Verwaltungs Data Warehouse konfigurieren** Der **Assistent zum Konfigurieren der Verwaltungs Data Warehouse** wird gestartet.  
  
3.  Klicken Sie auf **weiter** , um die Datenbank auszuwählen, die als Verwaltungs Data Warehouse fungieren soll.  
  
4.  Klicken Sie auf **neu** , um eine neue Datenbank zum Speichern der Profildaten zu erstellen. Nachdem Sie die Erstellung der Datenbank abgeschlossen haben, klicken Sie im Assistenten auf **weiter** .  
  
5.  Im nächsten Schritt des Assistenten können Sie Benutzer und Anmeldenamen hinzufügen. Sie können Anmeldenamen Rollenmitgliedschaften für die MDW-Instanz zuordnen. Dies ist nicht erforderlich, um Daten von der lokalen Instanz zu sammeln. Wenn Sie keine Daten von der lokalen Instanz sammeln, können Sie die die Mitgliedschaft in der Datenbankrolle `mdw_admin` dem Konto erteilen, das Transaktionen ausführt, die zur Profilerstellung verwendet werden. Klicken Sie anschließend auf **Weiter**.  
  
6.  Stellen Sie sicher, dass der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Agent ausgeführt wird.  
  
7.  Klicken Sie auf dem nächsten Bildschirm auf **Fertig** stellen, um den Assistenten zu beenden.  
  
### <a name="configure-data-collection-on-a-local-ssnoversion-instance"></a>Konfigurieren der Datensammlung auf einer lokalen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz  
 Für die Datensammlung muss der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Agent gestartet werden. Sie müssen auf einem Server nur einen Datensammler konfigurieren.  
  
 Ein Datensammler kann auf einem SQL Server 2012 oder einer höheren Version von konfiguriert werden [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 So konfigurieren Sie die Datensammlung für Uploads in eine als Verwaltungs-Data Warehouse konfigurierte Datenbank auf derselben Instanz  
  
1.  Erweitern Sie in **Objekt-Explorer**den Knoten **Verwaltung**.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Datensammlung**, wählen Sie **Tasks**und dann **Datensammlung konfigurieren**aus. Der **Assistent zum Konfigurieren der Datensammlung** wird gestartet.  
  
3.  Klicken Sie auf **weiter** , um die Datenbank auszuwählen, in der die Profildaten gesammelt werden sollen.  
  
4.  Wählen Sie die aktuelle [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz und eine als Verwaltungs-Data Warehouse konfigurierte Datenbank auf dieser Instanz aus.  
  
5.  Wählen Sie im Feld mit der Bezeichnung **Datensammler Sätze auswählen, die Sie aktivieren möchten**die Option **Transaktions Leistungsdaten-Sammlungs Sätze**aus. Klicken Sie, sobald Sie fertig sind, auf **Weiter**.  
  
6.  Überprüfen Sie die Auswahl. Klicken Sie auf **zurück** , um die Einstellungen zu ändern. Klicken Sie anschließend auf **Fertig stellen** .  
  
###  <a name="configure-data-collection-on-a-remote-ssnoversion-instance"></a><a name="xxx"></a>Konfigurieren der Datensammlung auf einer Remote [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Instanz  
 Die Datensammlung erfordert, dass der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Agent für die Instanz gestartet wird, die die Daten sammeln soll.  
  
 Ein Datensammler kann auf einem SQL Server 2012 oder einer höheren Version von konfiguriert werden [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 Sie benötigen einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Agent-Proxy, der mit den korrekten Anmeldeinformationen erstellt wurde, damit ein Datensammler Daten auf eine als Verwaltungs-Data Warehouse konfigurierte Datenbank einer Instanz hochladen kann, die sich von denjenigen unterscheidet, auf denen Profile für Transaktionen erstellt werden. Um einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Agent-Proxy zu aktivieren, müssen Sie zuerst Anmeldeinformationen mit einem domänenaktivierten Anmeldenamen erstellen. Der domänenaktivierte Anmeldename muss Mitglied der Gruppe `mdw_admin` für die Datenbank des Verwaltungs-Data Warehouse sein. Weitere Informationen zum Erstellen von Anmelde Informationen finden Sie unter Vorgehens [Weise: Erstellen von Anmelde Informationen (SQL Server Management Studio)](../security/authentication-access/create-a-credential.md) .  
  
 So konfigurieren Sie die Datensammlung für Uploads in eine als Verwaltungs-Data Warehouse konfigurierte Datenbank auf einer anderen Instanz  
  
1.  Erweitern Sie auf der-Instanz, die die Datenträger basierten Objekte enthält, die Sie zu in-Memory OLTP migrieren möchten, den Knoten **Verwaltung** in Objekt-Explorer.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Datensammlung** , und wählen Sie **Tasks** und dann **Datensammlung konfigurieren** Der **Assistent zum Konfigurieren der Datensammlung** wird gestartet.  
  
3.  Klicken Sie auf **weiter** , um die Datenbank auszuwählen, in der die Profildaten gesammelt werden sollen.  
  
4.  Stellen Sie sicher, dass eine als Verwaltungs-Data Warehouse konfigurierte Datenbank auf der anderen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz vorhanden ist.  
  
5.  Wählen Sie eine andere [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz und eine Verwaltungs-Data Warehouse-Datenbank auf dieser Instanz aus.  
  
     Die Version der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz, auf der Sie Daten sammeln (das Profil erstellen), sollte die gleiche Version oder eine niedrigere Version aufweisen als der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], auf dem das Verwaltungs-Data Warehouse konfiguriert ist.  
  
6.  Wählen Sie im Feld mit der Bezeichnung **Datensammler Sätze auswählen, die Sie aktivieren möchten**die Option **Transaktions Leistungsdaten-Sammlungs Sätze**aus.  
  
7.  Wählen Sie ** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent-Proxy für Remote Uploads verwenden aus**.  
  
8.  Klicken Sie, sobald Sie fertig sind, auf **Weiter**.  
  
9. Wählen Sie den Proxy aus.  
  
     Wenn Sie einen neuen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Agent-Proxy erstellen möchten:  
  
    1.  Klicken Sie auf **neu** , um das Dialogfeld **Neues Proxy Konto** anzuzeigen.  
  
    2.  Geben Sie im Dialogfeld **Neues Proxy Konto** den Namen des Proxys ein, wählen Sie die Anmelde Informationen aus, und geben Sie optional eine Beschreibung ein. Klicken Sie dann auf **Prinzipale**.  
  
    3.  Klicken Sie auf **Hinzufügen** , und wählen Sie **msdb** Role  
  
    4.  `dc_proxy`Klicken Sie auf **OK**. Klicken Sie dann erneut auf **OK**.  
  
     Nachdem Sie den richtigen Proxy ausgewählt haben, klicken Sie auf **weiter**.  
  
10. Überprüfen Sie zum Konfigurieren von System Sammlungs Sätzen die **System Sammlungs Sätze** , und klicken Sie auf **weiter**.  
  
11. Überprüfen Sie die Auswahl. Klicken Sie auf **zurück** , um die Einstellungen zu ändern. Wenn Sie fertig sind, klicken Sie auf **Fertig** stellen.  
  
 Datensammlungssätze sollten jetzt konfiguriert sein und auf Ihrer Instanz ausgeführt werden.  
  
### <a name="generate-reports"></a>Generieren von Berichten  
 Sie können Berichte zur Transaktions Leistungsanalyse generieren, indem Sie mit der rechten Maustaste auf die Datenbank des Verwaltungs Data Warehouse klicken und **Berichte**, dann **Verwaltungs Data Warehouse**und anschließend **Übersicht über Transaktions Leistungsanalyse**auswählen.  
  
 Im Bericht werden Informationen über alle Benutzerdatenbanken auf dem Arbeitsauslastungsserver gesammelt. Wenn sich die MDW-Datenbank (Verwaltungs-Data Warehouse) auf dem lokalen Computer befindet, werden die MDW-Datenbank(en) im Bericht aufgeführt.  
  
 Eine gespeicherte Prozedur mit hoher CPU-Zeit im Verhältnis zur verstrichenen Zeit ist ein Kandidat für die Migration. Der Bericht zeigt alle Tabellenverweise an, da systemintern kompilierte gespeicherte Prozeduren nur auf speicheroptimierte Tabellen verweisen können. Das kann den Migrationsaufwand weiter erhöhen.  
  
 Der Detailbericht für eine Tabelle umfasst drei Abschnitte:  
  
-   Abschnitt zur Scanstatistik  
  
     Dieser Abschnitt enthält eine einzelne Tabelle mit den Statistiken, die zu Scans für die Datenbanktabelle gesammelt wurden. Folgende Spalten sind enthalten:  
  
    -   Prozent der Gesamtzahl der Zugriffe. Der Prozentsatz der Scans und Suchvorgänge für diese Tabelle im Verhältnis zur Aktivität für die gesamte Datenbank. Je höher der Prozentsatz, desto stärker wird die Tabelle im Vergleich zu anderen Tabellen in der Datenbank verwendet.  
  
    -   Statistik zu Suchläufen/Bereichsscans. In dieser Spalte wird die Anzahl der Punktsuchen und Bereichsscans (Indexscans und Tabellenscans) aufgeführt, die während der Profilerstellung für die Tabelle durchgeführt wurden. Der Durchschnitt je Transaktion beruht auf einer Schätzung.  
  
    -   Interop-Zunahme und systemeigene Zunahme. Diese Spalten enthalten Schätzungen des Leistungszuwachses, der bei einer Punktsuche oder einem Bereichsscan erzielt werden könnte, wenn die Tabelle in eine speicheroptimierte Tabelle konvertiert wird.  
  
-   Abschnitt zur Konfliktstatistik  
  
     Dieser Abschnitt enthält eine Tabelle mit den Konflikten für die Datenbanktabelle. Weitere Informationen zu datenbanklatches und-Sperren finden Sie unter [Sperr Architektur](https://msdn.microsoft.com/library/aa224738\(v=sql.80\).aspx). Es gibt folgende Spalten:  
  
    -   Prozent der Gesamtwartevorgänge. Der Prozentsatz der Latch- und Sperrenwartevorgänge für diese Datenbanktabelle im Verhältnis zur Aktivität für die Datenbank. Je höher der Prozentsatz, desto stärker wird die Tabelle im Vergleich zu anderen Tabellen in der Datenbank verwendet.  
  
    -   Latchstatistik. In diesen Spalten wird die Anzahl der Latchwartevorgänge bei Abfragen, die diese Tabelle betreffen, aufgeführt. Weitere Informationen zu Latches finden Sie unter [Latching](https://msdn.microsoft.com/library/aa224727\(v=SQL.80\).aspx). Je höher diese Zahl ist, desto mehr Latchkonflikte treten für die Tabelle auf.  
  
    -   Sperrenstatistik. In dieser Gruppe von Spalten wird die Anzahl der Sperrenerhalt- und -wartevorgänge für Seiten bei Abfragen, die diese Tabelle betreffen, aufgeführt. Weitere Informationen zu Sperren finden Sie Untergrund Legendes zu sperren [in SQL Server](https://msdn.microsoft.com/library/aa213039\(v=SQL.80\).aspx). Je höher die Anzahl der Wartevorgänge ist, desto mehr Sperrenkonflikte treten für die Tabelle auf.  
  
-   Abschnitt zu Migrationsproblemen  
  
     Dieser Abschnitt enthält eine Tabelle, die angibt, wie schwierig es ist, diese Datenbanktabelle in eine speicheroptimierte Tabelle zu konvertieren. Je höher die Schwierigkeitsbewertung, desto schwieriger ist die Konvertierung der Tabelle. Verwenden Sie den Ratgeber für die [Speicher Optimierung](memory-optimization-advisor.md), um Details zum Konvertieren dieser Datenbanktabelle anzuzeigen.  
  
 Scan-und Konflikt Statistiken für den Tabellen Detail Bericht werden aus [sys. dm_db_index_operational_stats &#40;Transact-SQL-&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql)gesammelt und aggregiert.  
  
 Der Detailbericht für eine gespeicherte Prozedur umfasst zwei Abschnitte:  
  
-   Abschnitt zur Ausführungsstatistik  
  
     Dieser Abschnitt enthält eine Tabelle mit den Statistiken, die zur Ausführung der gespeicherten Prozedur gesammelt wurden. Es gibt folgende Spalten:  
  
    -   Cachezeit. Die Zwischenspeicherungsdauer des Ausführungsplans. Wenn die gespeicherte Prozedur aus dem Plancache entfernt und wieder hinzugefügt wird, werden Zeiten für jeden Cache angegeben.  
  
    -   Gesamte CPU-Zeit. Die gesamte CPU-Zeit, die die gespeicherte Prozedur während der Profilerstellung genutzt hat. Je höher diese Zahl ist, desto mehr CPU-Leistung hat die gespeicherte Prozedur genutzt.  
  
    -   Gesamtausführungszeit. Die Gesamtdauer der Ausführungszeit, die die gespeicherte Prozedur während der Profilerstellung genutzt hat. Je höher die Differenz zwischen dieser Zahl und der CPU-Zeit ist, desto weniger effizient nutzt die gespeicherte Prozedur die CPU.  
  
    -   Cachefehler gesamt. Die Anzahl der Cachefehler (Lesevorgänge aus dem physischen Speicher), die durch die Ausführung der gespeicherten Prozedur während der Profilerstellung verursacht wurden.  
  
    -   Ausführungsanzahl. Gibt an, wie oft diese gespeicherte Prozedur während der Profilerstellung ausgeführt wurde.  
  
-   Abschnitt zu Tabellenverweisen  
  
     Dieser Abschnitt enthält eine Tabelle mit den Tabellen, auf die diese gespeicherte Prozedur verweist. Vor dem Konvertieren der gespeicherten Prozedur in eine systemintern kompilierte gespeicherte Prozedur müssen alle diese Tabellen in speicheroptimierte Tabellen konvertiert werden, und sie müssen auf demselben Server und in derselben Datenbank verbleiben.  
  
 Die Ausführungs Statistik für den Bericht "Details gespeicherter Prozeduren" wird von [sys. dm_exec_procedure_stats &#40;Transact-SQL-&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql)gesammelt und aggregiert. Die Verweise werden aus [sys. sql_expression_dependencies &#40;Transact-SQL-&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)abgerufen.  
  
 Um Details zum Konvertieren einer gespeicherten Prozedur in eine System intern kompilierte gespeicherte Prozedur anzuzeigen, verwenden Sie den [Ratgeber für Native Kompilierung](native-compilation-advisor.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Migrieren zu in-Memory-OLTP](migrating-to-in-memory-oltp.md)  
  
  
