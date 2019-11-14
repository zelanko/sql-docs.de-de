---
title: Beginnen Sie mit Assistent für Datenbankexperimente
description: Assistent für Datenbankexperimente (DEA) ist eine A/B-Testlösung für Änderungen in SQL Server Umgebungen, z. B. Upgrades oder neue Indizes.
ms.date: 10/22/2018
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: ajaykar
ms.reviewer: mathoma
ms.custom: seo-lt-2019
ms.openlocfilehash: 43f8c6bff909716bdd85a798dfd4e5a7431e31af
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056713"
---
# <a name="get-started-with-database-experimentation-assistant-sql-server"></a>Beginnen Sie mit Assistent für Datenbankexperimente (SQL Server)

Assistent für Datenbankexperimente (DEA) ist eine A/B-Testlösung für Änderungen in SQL Server Umgebungen, z. B. Upgrades oder neue Indizes. Mithilfe von DEA können Sie bewerten, wie die Arbeitsauslastung auf dem Quell Server (in Ihrer aktuellen Umgebung) in der neuen Umgebung durchgeführt wird. Mithilfe von DEA werden Sie durch die Ausführung eines A/B-Tests geführt, indem Sie drei Schritte ausführen: 

- Erfassung
- Zugeben
- Analyse

Dieser Artikel führt Sie durch die folgenden Schritte.

## <a name="capture"></a>Erfassung

Der erste Schritt SQL Server a/B-Tests besteht darin, eine Ablauf Verfolgung auf dem Quell Server zu erfassen. Der Quell Server ist normalerweise der Produktionsserver. Ablauf Verfolgungs Dateien erfassen die gesamte Arbeitsauslastung der Abfrage auf diesem Server, einschließlich Zeitstempel. Später wird diese Ablauf Verfolgung für die Analyse auf ihren Ziel Servern wiedergegeben. Der Analysebericht bietet Einblicke in den Unterschied in der Leistung der Arbeitsauslastung zwischen den beiden Ziel Servern.

Weitere Überlegungen:

- Stellen Sie sicher, dass Sie die Datenbanken sichern, von denen Sie eine Ablauf Verfolgung erfassen, bevor Sie mit der Erfassung der Ablauf Verfolgung beginnen.
- Ein DEA-Benutzer muss konfiguriert werden, um mithilfe der Windows-Authentifizierung eine Verbindung mit der Datenbank herzustellen.
- Ein SQL Server-Dienst Konto erfordert Zugriff auf den Pfad der Quelldatei für die Ablauf Verfolgungs Datei.
- Damit von DEA bestimmt wird, ob die Leistung einer Abfrage verbessert oder beeinträchtigt wird, muss diese Abfrage mindestens 15 Mal während des Erfassungs Zeitraums ausgeführt werden.  

So erfassen Sie eine Ablauf Verfolgung auf dem Quell Server:

1. Wechseln Sie in der DEA zu **alle** Erfassungen, indem Sie im linken Menü das Kamerasymbol auswählen.

   ![Linkes Navigationsmenü](./media/database-experimentation-assistant-get-started/dea-get-started-leftnav.png)

1. Geben Sie folgende Informationen ein, oder wählen Sie Sie aus:

   - Ablauf **Verfolgungs Name**: der Dateiname für die neue Ablauf Verfolgungs Datei, die Sie erstellen. Vermeiden Sie einen Ablauf Verfolgungs Namen, der die Benennungs Konvention für Rolloverdateien verwendet, z. b. capturename\_nnn.
   - **Dauer**: die Dauer für die Erfassung.
   - **SQL Server Instanzname**: die SQL Server Instanz, von der Sie eine Ablauf Verfolgung aufzeichnen möchten.
   - **Datenbankname**: der Name der Datenbank auf dem Computer, auf dem SQL Server ausgeführt wird und für den Sie eine Ablauf Verfolgung aufzeichnen möchten. Wenn das Feld leer gelassen wird, wird die Ablauf Verfolgung von allen Datenbanken auf dem Server aufgezeichnet.
   - **Pfad zum Speichern der Quelldatei der Ablauf Verfolgung auf SQL Server Computer**: der Ordner Pfad, in dem Sie die Ablauf Verfolgungs Datei speichern möchten.

1. Stellen Sie sicher, dass die Zieldatenbank gesichert ist. Aktivieren Sie dann das Kontrollkästchen Datenbank.
1. Wählen Sie **starten** , um die Erfassung zu starten.

Sie können den Status der Erfassung anzeigen, einschließlich Startzeit, Dauer und verbleibende Zeit. Sie können auch eine neue Erfassung starten, während Sie auf den Abschluss dieser Erfassung warten. Wenn Ihre Erfassung abgeschlossen ist, verwenden Sie die Ausgabedatei der Ablauf Verfolgung, um die zweite Phase zu starten: Wiedergeben der Ablauf Verfolgungs Datei auf den Ziel Servern.

Häufig gestellte Fragen zur Erfassung von Ablauf Verfolgungs Informationen finden Sie in den [FAQ](database-experimentation-assistant-capture-trace.md#frequently-asked-questions-about-trace-capture).

## <a name="replay"></a>Zugeben

Der zweite Schritt SQL Server A/B-Tests ist die Wiedergabe der Ablauf Verfolgungs Datei, die auf den Ziel Servern aufgezeichnet wurde. Erfassen Sie dann umfassende Ablauf Verfolgungen aus den Wiedergaben für die Analyse. 

Sie geben die Ablauf Verfolgungs Datei auf zwei Ziel Servern wieder: eine, die ihren Quell Server imitiert (Ziel 1), und eine, die ihre vorgeschlagene Änderung imitiert (Ziel 2). Die Hardware Konfigurationen von Ziel 1 und Ziel 2 sollten so ähnlich wie möglich sein, damit SQL Server die Leistungs Auswirkung ihrer vorgeschlagenen Änderungen genau analysieren kann.

Weitere Überlegungen:

- Zum Ausführen von Replay müssen die Computer so eingerichtet sein, dass Distributed Replay (dreplay)-Ablauf Verfolgungen ausgeführt werden. Weitere Informationen finden Sie unter [Distributed Replay Controller-und Client Setup](https://blogs.msdn.microsoft.com/datamigration/distributed-replay-controller-and-client-setup/).
- Stellen Sie sicher, dass Sie die Datenbanken auf ihren Ziel Servern wiederherstellen, indem Sie die Sicherung vom Quell Server verwenden.
- Das Zwischenspeichern von Abfragen in SQL Server kann die Auswertungs Ergebnisse beeinflussen. Es wird empfohlen, den SQL Server-Dienst (MSSQLSERVER) in der Dienste-Anwendung neu zu starten, um die Konsistenz der Bewertungsergebnisse zu verbessern.

So geben Sie die Ablauf Verfolgungs Datei wieder:

1. Wählen Sie in der DEA im linken Menü das Symbol wiedergeben aus, um zu **allen Wiederholungen**zu wechseln. Die Liste der bisherigen Wiederholungen, die während der Sitzung ausgeführt werden, wird ggf. angezeigt. Wählen Sie **neue Wiedergabe**aus, um eine neue Wiedergabe zu starten.

1. Geben Sie folgende Informationen ein, oder wählen Sie Sie aus:

   - **Replay Name**: der Dateiname für die Wiedergabe Ablauf Verfolgung.
   - **Controller Computername**: der Name des Distributed Replay Controller Computers.
   - **Pfad zur Quelldatei der Ablauf Verfolgung auf dem Controller**: der Dateipfad für die Quelldatei der Ablauf Verfolgung von [Capture](#capture).
   - **SQL Server Instanzname**: der Name der SQL Server Instanz, auf der die Quell Ablauf Verfolgung wiedergegeben werden soll.
   - **Pfad zum Speichern der Ziel Ablauf Verfolgungs Datei auf SQL Server Computer**: der Ordner Pfad für die resultierende Wiedergabe Datei der Ablauf Verfolgung.

1. Aktivieren Sie das Kontrollkästchen, um die Sicherung aus dem ersten Schritt wiederherzustellen.

1. Wählen Sie **starten** aus, um die Wiedergabe zu starten. 

Sie können den Status ihrer Wiedergabe anzeigen. Nachdem Sie die Quell Ablauf Verfolgung auf beiden Ziel Servern wiedergegeben haben, können Sie einen Analysebericht generieren.

Allgemeine Fragen zur Wiedergabe finden Sie in den häufig gestellten Fragen zur wieder [Gabe](database-experimentation-assistant-replay-trace.md#frequently-asked-questions-about-trace-replay).

## <a name="analysis"></a>Analyse

Der letzte Schritt besteht darin, einen Analysebericht mithilfe der Wiedergabe Ablauf Verfolgungen zu generieren. Der Analysebericht kann Ihnen helfen, Einblicke in die Auswirkungen auf die Leistung der vorgeschlagenen Änderung zu erhalten.

Weitere Überlegungen:

- Wenn eine oder mehrere Komponenten fehlen, wird eine Seite mit Links zu Downloads angezeigt, die angezeigt wird, wenn Sie versuchen, einen neuen Analysebericht zu generieren (Internetverbindung erforderlich).
- Um einen Bericht anzuzeigen, der in einer früheren Version des Tools generiert wurde, müssen Sie zuerst das Schema aktualisieren.

So generieren Sie einen Analysebericht:

1. Wechseln Sie im linken Menü zu **Analyseberichte**. Stellen Sie eine Verbindung mit dem Computer her, auf dem SQL Server ausgeführt wird Eine Liste aller Berichte auf dem Server wird angezeigt. Um einen neuen Bericht zu erstellen, wählen Sie **neuer Bericht**aus.

1. Geben Sie die zum Generieren eines Berichts erforderlichen Informationen ein, oder wählen Sie Sie aus:

   - **Report Name**: der Name des zu erstellenden Analyse Berichts.
   - Ablauf **Verfolgung für Ziel 1 SQL Server**: der Pfad für die Ablauf Verfolgungs Datei von der Wiedergabe an Ziel 1.
   - Ablauf **Verfolgung für Ziel 2 SQL Server**: der Pfad für die Ablauf Verfolgungs Datei von der Wiedergabe an Ziel 2.

1. Wählen Sie **starten** aus, um den Bericht zu generieren. Der neue Bericht wird oben in der Liste angezeigt. Das Symbol neben dem Bericht wird zu einem grünen Häkchen, wenn der Bericht generiert wurde.

Zeigen Sie nun den Analysebericht an, um Einblicke zu erhalten, die von Ihrem A/B-Test bereitgestellt werden

Häufig gestellte Fragen zu Analyseberichten finden Sie in den häufig gestellten Fragen zur [Analyse](database-experimentation-assistant-create-report.md#frequently-asked-questions-about-analysis-reports).

### <a name="analysis-report"></a>Analysebericht

Auf der ersten Seite des Berichts wird die Versions-und Buildinformationen für die Zielserver angezeigt, auf denen das Experiment ausgeführt wurde. Mit dem Schwellenwert können Sie die Empfindlichkeit oder Toleranz Ihrer A/B-Test Analyse anpassen. Standardmäßig ist der Schwellenwert auf 5% festgelegt. Alle Verbesserungen bei der Leistung von mehr als oder gleich 5% werden als **verbessert**kategorisiert. Wählen Sie im Dropdown Menü Optionen aus, um den Bericht mithilfe verschiedener Leistungs Schwellenwerte auszuwerten.

![Schwellenwert](https://msdnshared.blob.core.windows.net/media/2017/03/threshold.jpg)

Zwei Kreis Diagramme veranschaulichen die Auswirkungen auf die Leistung des Unterschieds zwischen den beiden Ziel Servern für ihre Arbeitsauslastung. Das linke Diagramm basiert auf der Ausführungs Anzahl. Das rechte Diagramm basiert auf unterschiedlichen Abfragen. Es gibt fünf mögliche Kategorien:

- **Verbessert**: statistisch lief die Abfrage auf Ziel 2 besser als auf Ziel 1.
- Herunter **gestuft: statistisch**führte die Abfrage auf Ziel 2 zu einer schlechteren Leistung als auf Ziel 1.
- **Identisch**: Es gibt keinen statistischen Unterschied Zwischenziel 1 und Ziel 2.
- **Auswerten nicht**möglich: die Stichprobengröße für die Abfrage ist zu klein für statistische Analysen. Für eine/B-Test Analyse benötigt DEA die gleichen Abfragen, damit für jedes Ziel mindestens 30 Ausführungen vorhanden sind.
- **Fehler**: die Abfrage hat mindestens ein Mal für eines der Ziele einen Fehler ausgegeben.

![Kreisdiagramm](./media/database-experimentation-assistant-get-started/dea-get-started-piechart.png)

Wählen Sie einen Slice aus, um einen Drilldown in eine bestimmte Kategorie auszuführen und Leistungsmetriken zu erhalten

Auf der drilldownseite für eine Leistungs Änderungs Kategorie wird eine Liste der Abfragen in dieser Kategorie angezeigt. Die **Fehler** Seite enthält drei Registerkarten:

- **Neue Fehler**: Fehler, die auf Ziel 2, aber nicht auf Ziel 1 aufgetreten sind.
- **Vorhandene Fehler**: Fehler, die auf Ziel 1 und Ziel 2 aufgetreten sind.
- Behobene **Fehler**: Fehler, die auf Ziel 1 aufgetreten sind, aber nicht auf Ziel 2.

   ![Fehlerseite](./media/database-experimentation-assistant-get-started/dea-get-started-errorpage.png)

Wählen Sie eine Abfrage aus, um zu einer **Vergleichs Zusammenfassungs** Seite für diese Abfrage zu wechseln.

Auf der Seite **Vergleichs Zusammenfassung** werden Zusammenfassungs Statistiken für diese Abfrage angezeigt. Die Zusammenfassung enthält die Anzahl der Ausführungen, die durchschnittliche Dauer, die mittlere CPU, durchschnittliche Lese-/Schreibvorgänge und die Fehler Anzahl.

![Zusammenfassungs Statistiken](./media/database-experimentation-assistant-get-started/dea-get-started-summarystats.png)

Wenn es sich bei der Abfrage um eine Fehler Abfrage handelt, werden auf der Registerkarte **Fehlerinformationen** Weitere Informationen zum Fehler angezeigt. Die Registerkarte **Abfrage Plan Informationen** enthält Informationen zu den Abfrage Plänen, die für die Abfrage auf Ziel 1 und Ziel 2 verwendet werden.

![Abfrageplan](./media/database-experimentation-assistant-get-started/dea-get-started-queryplan.png)

Wählen Sie auf einer beliebigen Seite des Analyse Berichts oben rechts die Schaltfläche **Drucken** aus, um alle sichtbaren Elemente zu drucken.

## <a name="next-steps"></a>Nächste Schritte

- Informationen zum Erstellen einer Ablauf Verfolgungs Datei, die ein Protokoll der Ereignisse enthält, die auf einem Server auftreten, finden Sie unter [Capture Trace](database-experimentation-assistant-capture-trace.md).

- Sehen Sie sich das folgende Video an, um die Einführung von DEA und Demo in 19 Minuten zu demonstrieren:

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
