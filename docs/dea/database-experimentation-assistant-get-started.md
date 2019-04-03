---
title: Erste Schritte mit der Datenbank-experimentieren-Assistenten für SQL Server-upgrades
description: Erste Schritte mit der Datenbank-experimentieren-Assistenten
ms.custom: ''
ms.date: 10/22/2018
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: ajaykar
ms.reviewer: douglasl
manager: craigg
ms.openlocfilehash: 7630aee7ab39f98f372af7c33f277e7272042f43
ms.sourcegitcommit: 1a4aa8d2bdebeb3be911406fc19dfb6085d30b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2019
ms.locfileid: "58872240"
---
# <a name="get-started-with-database-experimentation-assistant"></a>Erste Schritte mit der Datenbank-experimentieren-Assistenten

Datenbank experimentieren-Assistenten (DEA) ist ein A / B-testlösung für Änderungen in SQL Server-Umgebungen wie Upgrades oder neue Indizes. DEA hilft bei Evaluierung, wie die arbeitsauslastung auf dem Quellserver (in der aktuellen Umgebung) in die neue Umgebung ausführt. DEA führt Sie durch das Ausführen eines A / B-Tests von drei Schritten: 

- Erfassung
- Wiedergeben
- Analyse

Dieser Artikel führt Sie durch die folgenden Schritte aus.

## <a name="capture"></a>Erfassung

Der erste Schritt des SQL Server A / B-Tests ist, um eine Ablaufverfolgung auf dem Quellserver zu erfassen. Der Quellserver ist in der Regel dem Produktionsserver. Ablaufverfolgungsdateien erfassen Sie die gesamte abfragearbeitsauslastung auf diesem Server, einschließlich Zeitstempeln. Diese Ablaufverfolgung wird später auf Zielservern für die Analyse wiedergegeben. Der Bericht bietet Einblicke in den Unterschied in Bezug auf die Leistung der Workload zwischen zwei Zielservern.

Weitere Überlegungen:

- Bevor Sie Ihrer Erfassung Ablaufverfolgung starten, stellen Sie sicher, dass Sie die Datenbanken sichern von dem Sie eine Ablaufverfolgung aufzeichnen.
- DEA Benutzer muss für die Verbindung mit der Datenbank mithilfe der Windows-Authentifizierung konfiguriert werden.
- Ein SQL Server-Dienstkonto erfordert Zugriff auf den Pfad der Quelldatei-Ablaufverfolgung.

Um eine Ablaufverfolgung auf dem Quellserver zu erfassen:

1. Wechseln Sie in DEA zu **alle erfasst** wählen Sie im linken Menü das Symbol "Kamera".

   ![Im linken Navigationsmenü](./media/database-experimentation-assistant-get-started/dea-get-started-leftnav.png)

1. Geben Sie ein, oder wählen Sie die folgende Informationen:

   - **Ablaufverfolgungsname**: Der Dateiname für die neue Datei, die Sie erstellen. Vermeiden Sie eine Ablaufverfolgung ein, mit dem der Rollover-Benennungskonvention, z. B. CaptureName\_"nnn".
   - **Dauer**: Die Dauer für die Erfassung.
   - **SQL Server-Instanzname**: Die SQL Server-Instanz, von der Sie eine Ablaufverfolgung erfassen möchten.
   - **Name der Datenbank**: Der Name der Datenbank auf dem Computer mit SQL Server, möchten Sie eine Ablaufverfolgung zu erfassen. Wenn leer, wird die Ablaufverfolgung aus allen Datenbanken auf dem Server erfasst.
   - **Pfad zum Speichern von Ablaufverfolgungs-Quelldatei auf SQL Server-Computer**: Der Ordnerpfad, in dem die Ablaufverfolgungsdatei gespeichert werden soll.

1. Stellen Sie sicher, dass die Zieldatenbank gesichert wurde. Wählen Sie das Kontrollkästchen für die Datenbank an.
1. Wählen Sie **starten** um die Erfassung zu starten.

Sie können den Fortschritt Ihrer Erfassung, einschließlich Startzeit, Dauer und verbleibende Zeit anzeigen. Sie können auch eine neue Aufzeichnung starten, während Sie warten, dass dieser Erfassung, um den Vorgang abzuschließen. Wenn Ihrer Erfassung abgeschlossen ist, verwenden Sie die Ausgabedatei der Ablaufverfolgung die zweite Phase gestartet: die Ablaufverfolgungsdatei auf Zielservern wiedergeben.

Häufig gestellte Fragen zur Erfassung der Ablaufverfolgung finden Sie unter den [erfassen – häufig gestellte Fragen](database-experimentation-assistant-capture-trace.md#frequently-asked-questions-about-trace-capture).

## <a name="replay"></a>Wiedergeben

Im zweiten Schritt des SQL Server A / B-Tests ist die Ablaufverfolgungsdatei wiedergegeben, die auf Zielservern erfasst wurde. Klicken Sie dann erfassen Sie umfangreiche Ablaufverfolgung aus der Replays für die Analyse und. 

Sie die Ablaufverfolgungsdatei auf Zielservern zwei wiedergeben: eine, die den Quellserver (Ziel 1) imitiert und eine, die die vorgeschlagene Änderung (Ziel 2) imitiert. Der Hardwarekonfigurationen für Ziel 1 und 2 des Ziels sollte so ähnlich wie möglich sein, damit SQL Server die leistungsbezogenen Auswirkungen der vorgeschlagenen Änderungen genau analysieren können.

Weitere Überlegungen:

- Um Replay auszuführen, müssen Ihre Computer zum Ausführen der Distributed Replay (DReplay) ablaufverfolgungen eingerichtet werden. Weitere Informationen finden Sie unter [Distributed Replay Controller- und Clientdienste Setup](https://blogs.msdn.microsoft.com/datamigration/distributed-replay-controller-and-client-setup/).
- Stellen Sie sicher, dass Sie die Datenbanken auf Ihrem Zielserver wiederherstellen, indem Sie mithilfe der Sicherung des Quellservers.
- Abfrage in SQL Server-Cache kann sich auf die auswertungsergebnisse auswirken. Es wird empfohlen, dass Sie die SQL Server-Dienst (MSSQLSERVER) neu starten, in der dienstanwendung zur Verbesserung der Konsistenz in der auswertungsergebnisse.

Die Ablaufverfolgungsdatei wiedergegeben werden soll:

1. Wählen Sie die Play-Symbol im linken Menü zu wechseln, in DEA, **alle Wiedergaben**. Die Liste der letzten Replays, die während der Sitzung ausgeführt werden soll, wenn vorhanden, angezeigt werden. Wählen Sie zum Starten einer neuen Wiedergabe **neue wiedergeben**.

1. Geben Sie ein, oder wählen Sie die folgende Informationen:

   - **Name der Wiedergabe**: Der Dateiname für die ablaufverfolgungswiedergabe.
   - **Der Name des Controllercomputers**: Der Name des dem Distributed Replay Controller-Computer.
   - **Pfad zum Ablaufverfolgungs-Quelldatei auf Controller**: Der Dateipfad für die Ablaufverfolgungs-Quelldatei aus [erfassen](#capture).
   - **SQL Server-Instanzname**: Der Name der SQL Server-Instanz auf dem die Quelle Ablaufverfolgung wiedergegeben werden soll.
   - **Pfad zum Speichern von Ziel-Ablaufverfolgungsdatei auf SQL Server-Computer**: Der Ordnerpfad für die Wiedergabe Ergebnisdatei der Ablaufverfolgung.

1. Wählen Sie das Kontrollkästchen zum Wiederherstellen der Sicherung aus dem ersten Schritt ein.

1. Wählen Sie **starten** um die Wiedergabe zu starten. 

Sie können den Status Ihrer Wiedergabe anzeigen. Nachdem Sie die Quell-Ablaufverfolgung auf Zielservern wiedergeben, können Sie einen Bericht zu generieren.

Häufig gestellte Fragen zur Wiedergabe finden Sie unter den [wiedergeben – häufig gestellte Fragen](database-experimentation-assistant-replay-trace.md#frequently-asked-questions-about-trace-replay).

## <a name="analysis"></a>Analyse

Der letzte Schritt ist, um einen Analysebericht zu generieren, das Wiedergeben von ablaufverfolgungen mit. Der Analysebericht können Sie wertvolle Einblicke in die Auswirkungen auf die Leistung der vorgeschlagenen Änderung an.

Weitere Überlegungen:

- Wenn eine oder mehrere Komponenten fehlen, wird eine Seite über erforderliche Komponenten und Links zu Downloads angezeigt, wenn Sie versuchen, einen neuen Bericht (Internetverbindung erforderlich) zu generieren.
- Um einen Bericht anzuzeigen, der in einer früheren Version des Tools generiert wurde, müssen Sie zunächst das Schema aktualisieren.

So generieren Sie einen Analysebericht:

1. Navigieren Sie im linken Menü zu **Analyseberichte**. Verbinden Sie mit dem Computer mit SQL Server, in dem Sie Ihre Berichtsserver-Datenbanken gespeichert. Eine Liste aller Berichte auf dem Server angezeigt. Wählen Sie zum Erstellen eines neuen Berichts **neuer Bericht**.

1. Geben Sie ein, oder wählen Sie die Informationen, die erforderlich ist, um einen Bericht zu generieren:

   - **Name des Berichts**: Der Name der der Analysebericht zu erstellen.
   - **Ablaufverfolgung für SQL-Zielserver 1**: Der Pfad für die Ablaufverfolgungsdatei aus der Wiedergabe auf 1.
   - **Ablaufverfolgung für SQL-Zielserver 2**: Der Pfad für die Ablaufverfolgungsdatei aus der Wiedergabe auf Ziel-2.

1. Wählen Sie **starten** zum Generieren des Berichts. Der neue Bericht wird am oberen Rand der Liste angezeigt. Das Symbol neben dem Bericht wird ein grünes Häkchen aus, wenn der Bericht generiert wurde.

Sehen Sie sich nun der Analysebericht gewinnen Erkenntnisse aus Ihrer ein / B-Tests.

Häufig gestellte Fragen zu Berichten finden Sie unter den [Analyse – häufig gestellte Fragen](database-experimentation-assistant-create-report.md#frequently-asked-questions-about-analysis-reports).

### <a name="analysis-report"></a>Analysebericht zu

Auf der ersten Seite des Berichts sehen Sie Versions- und Buildnummer Informationen für den Zielserver, die auf denen das Experiment ausgeführt wurde. Können Sie anpassen, die Vertraulichkeit oder Toleranz für die ein Schwellenwert / B-Test-Analyse. Standardmäßig ist der Schwellenwert auf 5 % festgelegt. Leistungsverbesserungen, die größer als oder gleich 5 % ist, wird als kategorisiert **verbesserte**. Wählen Sie Optionen im Dropdown-Menü auf den Bericht mit anderen Leistungsschwellenwerte auswerten.

![Schwellenwert](https://msdnshared.blob.core.windows.net/media/2017/03/threshold.jpg)

Zwei Kreisdiagramme zeigen die Auswirkungen auf die Leistung des Unterschieds zwischen den zwei Zielservern für Ihre Workload. Das linke Diagramm basiert auf der Anzahl von Ausführungen. Das rechte Diagramm basiert auf unterschiedlichen Abfragen. Es gibt fünf mögliche Kategorien:

- **Verbesserte**:  Statistisch gesehen führte die Abfrage auf Ziel 2 als Ziel 1 eine bessere.
- **Heruntergestuft**: Statistisch gesehen führte die Abfrage auf Ziel 2 als Ziel 1 schlechter.
- **Gleiche**: Es gibt keine statistischen Unterschied für die Abfrage zwischen Ziel 1 und 2 für Ziel.
- **Kann nicht ausgewertet werden**: Die Größe der Stichprobe für die Abfrage ist zu klein für statistische Analysen. Für A / B-Tests Analysis, DEA erfordert mindestens 30 Ausführungen für jedes Ziel verfügen, die gleichen Abfragen.
- **Fehler:** Die Abfrage, die sich mindestens einmal auf eines der Ziele Fehler aufgetreten.

![Kreisdiagramm](./media/database-experimentation-assistant-get-started/dea-get-started-piechart.png)

Wählen Sie ein Segment, um einen Drilldown in einer bestimmten Kategorie und Leistungsmetriken, einschließlich der **kann nicht ausgewertet werden** kreisslice angezeigt.

Drilldown für eine Leistung ändern Kategorie zeigt eine Liste von Abfragen in dieser Kategorie. Die **Fehler** Seite enthält drei Registerkarten:

- **Neue Fehler**: Fehler, die für die Ziel-2 jedoch nicht für Ziel 1 angezeigt.
- **Vorhandenen Fehler**: Fehler, die auf Ziel 1 und 2 für Ziel angezeigt.
- **Fehler aufgelöst**: Fehler, die auf dem Ziel 1 jedoch nicht auf Ziel 2 angezeigt.

   ![Fehler (Seite)](./media/database-experimentation-assistant-get-started/dea-get-started-errorpage.png)

Wählen Sie eine Abfrage, fahren Sie mit einer **Zusammenfassung** Seite für diese Abfrage.

Die **Vergleich Zusammenfassung** Seite zeigt zusammenfassende Statistiken für diese Abfrage. Die Zusammenfassung enthält die Anzahl der Ausführungen, durchschnittliche Dauer, CPU-Mittelwert, mittlere Lese-/Schreibvorgänge und Fehleranzahl.

![Zusammenfassende Statistiken](./media/database-experimentation-assistant-get-started/dea-get-started-summarystats.png)

Wenn die Abfrage eine Abfrage für Fehler, die **Fehlerinformationen** Registerkarte zeigt Informationen zu diesem Fehler. Die **Informationen zum Planen der** Registerkarte zeigt Informationen über die Abfragepläne, die für die Abfrage auf das Ziel 1 und 2 für Ziel verwendet werden.

![Abfrageplan](./media/database-experimentation-assistant-get-started/dea-get-started-queryplan.png)

Wählen Sie auf jeder Seite des Analyseberichts der **Drucken** Schaltfläche oben Recht, alles zu drucken, der angezeigt wird.

## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen, um eine Ablaufverfolgungsdatei zu erstellen, die ein Protokoll mit Ereignissen, die auf einem Server auftreten, finden Sie unter [Ablaufverfolgung erfassen](database-experimentation-assistant-capture-trace.md).

- Für einen 19-minütige Einführung in DEA und Demonstrationen im folgenden Video:

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
