---
title: Wiedergeben einer Ablauf Verfolgung für SQL Server Upgrades
description: Wiedergeben einer Ablauf Verfolgung mit Assistent für Datenbankexperimente für SQL Server Upgrades
ms.custom: seo-lt-2019
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
ms.openlocfilehash: b1607aefdc8495f374b2586b0b896f20e87f62d1
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056699"
---
# <a name="replay-a-trace-in-database-experimentation-assistant"></a>Wiedergeben einer Ablauf Verfolgung in Assistent für Datenbankexperimente

In Assistent für Datenbankexperimente (DEA) können Sie eine aufgezeichnete Ablauf Verfolgungs Datei für eine aktualisierte Testumgebung wiedergeben. Nehmen wir beispielsweise an, eine produktionsworkloads, die auf SQL Server 2008 R2 ausgeführt wird. Die Ablauf Verfolgungs Datei für die Arbeitsauslastung muss zweimal wiedergegeben werden: einmal in einer Umgebung mit derselben Version von SQL Server, die in der Produktionsumgebung und erneut in einer Umgebung ausgeführt wird, die das upgradeziel SQL Server Version aufweist, wie z. b. SQL Server 2016.

> [!NOTE]
> Zum Ausführen dieser Aktion müssen Sie manuell virtuelle Computer oder physische Computer einrichten, um Distributed Replay Ablauf Verfolgungen auszuführen. Weitere Informationen finden Sie unter [Distributed Replay-Controller-und-Client-Setup](https://blogs.msdn.microsoft.com/datamigration/distributed-replay-controller-and-client-setup/).
>
>

## <a name="create-a-trace-replay"></a>Erstellen einer Ablauf Verfolgungs Wiedergabe

Wählen Sie in der DEA das Menü Symbol aus. Wählen Sie im erweiterten Menü wieder **Gabe** -Ablauf Verfolgungen neben dem Wiedergabe Symbol aus.

![Wiedergabe Ablauf Verfolgungen im Menü auswählen](./media/database-experimentation-assistant-replay-trace/dea-replay-trace-open.png)

> [!NOTE]
> Der Distributed Replay Controller-Computer benötigt Berechtigungen für das Benutzerkonto, das Sie für die Remote Verwendung verwenden.
>

### <a name="grant-access-to-the-distributed-replay-controller"></a>Gewähren des Zugriffs auf den Distributed Replay Controller

1. Geben Sie an einer Eingabeaufforderung **DCOMCNFG** ein, um die Schnittstelle für **Komponenten Dienste** zu öffnen.
1. Erweitern Sie **Komponenten Dienste** > **Computer** > **Arbeitsplatz** > **DCOM-Konfiguration** > **dreplaycontroller**.
1. Klicken Sie mit der rechten Maustaste auf **dreplaycontroller**, und wählen Sie dann **Eigenschaften**aus.
1. Wählen Sie auf der Registerkarte **Sicherheit** die Option **Bearbeiten** aus, um das Benutzerkonto hinzuzufügen.
1. Wählen Sie **OK**.

### <a name="verify-setup"></a>Setup überprüfen

1.  **SQL Server Installationspfad**: Geben Sie den Pfad für die Installation von SQL Server ein. Beispiel: C:\\-Programmdateien (x86)\\Microsoft SQL Server\\120.
1.  **Controller Computername**: Geben Sie einen Namen für den Computer ein, der als Controller eingerichtet wurde. Auf diesem Computer wird der Windows-Dienst mit dem Namen SQL Server Distributed Replay Controller ausgeführt. Der Distributed Replay Controller orchestriert die Aktionen der Distributed Replay Clients. Es kann in jeder Distributed Replay-Umgebung jeweils nur eine Controllerinstanz geben.
1.  **Client Computernamen**: Geben Sie einen Namen für jeden Client Computer ein, der durch Kommas getrennt ist. Beispiel: CLIENT1, client2. Sie können bis zu fünf Client Controller haben. Bei Clients handelt es sich um einen oder mehrere physische oder virtuelle Computer, auf denen der Windows-Dienst mit dem Namen SQL Server Distributed Replay-Clients ausgeführt wird. Die Distributed Replay Clients simulieren gemeinsam Arbeitsauslastungen auf einer Instanz von SQL Server. In jeder Distributed Replay-Umgebung kann sich mindestens ein Client befinden.
1.  Wählen Sie **Weiter**aus.

### <a name="select-a-trace"></a>Ablauf Verfolgung auswählen

1.  **Pfad zur Ablauf Verfolgungs Datei**: Geben Sie den Pfad zur Eingabedatei (TRC-Datei) ein.
1.  **Pfad zum Speichern der Wiedergabe Vorverarbeitungs Ausgabe**:  
    Wenn Sie nicht bereits über die UNF-Datei verfügen, geben Sie den Pfad zu dem Speicherort ein, an dem Sie die UNF-Datei speichern möchten, und andere Vorverarbeitungs Ausgaben. \-  
    Wenn Sie bereits über die UNF-Datei verfügen, geben Sie den Pfad zu den UNF-Dateien ein. \-
1. Wählen Sie **Weiter**aus.

### <a name="replay-a-trace"></a>Wiedergeben einer Ablauf Verfolgung

1.  **Name der Ablauf Verfolgungs Datei**: Geben Sie den Namen der Ablauf Verfolgungs Datei ein
1.  **Maximale Dateigröße (MB)** : Geben Sie einen Wert für die rollovergröße der Ablauf Verfolgungs Datei ein. Der Standardwert ist 200 MB. Sie können einen benutzerdefinierten Wert eingeben.
1.  **Pfad zum Speichern der Wiedergabe-Ablauf Verfolgungs Ausgabe**: Geben Sie den Pfad für die TRC-Ausgabedatei ein.
1.  **SQL Server Instanzname**: Geben Sie den Namen der SQL Server Instanz ein, auf der Ablauf Verfolgungen wiedergegeben werden sollen.
1.  Wählen Sie **Starten** aus.

Wenn die eingegebenen Informationen gültig sind, wird der Distributed Replay Prozess gestartet. Andernfalls werden die Text-Boses, die falsche Informationen enthalten, rot hervorgehoben. Stellen Sie sicher, dass die eingegebenen Werte richtig sind, und klicken Sie dann auf **starten**.

Warten Sie, bis die Wiedergabe abgeschlossen ist, um den von Ihnen angegebenen Speicherort anzuzeigen. Wählen Sie das Glocken Symbol unten im linken Menü aus, um den Wiedergabe Fortschritt zu überwachen.

![Verlauf der Wiedergabe Ablauf Verfolgungen](./media/database-experimentation-assistant-replay-trace/dea-replay-trace-progress.png)

## <a name="frequently-asked-questions-about-trace-replay"></a>Häufig gestellte Fragen zur Wiedergabe der Ablauf Verfolgung

### <a name="what-security-permissions-do-i-need-to-start-a-replay-capture-on-my-target-server"></a>Welche Sicherheits Berechtigungen benötige ich, um eine Wiedergabe Erfassung auf meinem Zielserver zu starten?

- Der Windows-Benutzer, der den Ablauf Verfolgungs Vorgang in der DEA-Anwendung durchführt, muss über Systemadministrator Rechte auf dem Zielcomputer verfügen, auf dem SQL Server ausgeführt wird. Diese Benutzerrechte sind erforderlich, um eine Ablauf Verfolgung zu starten.
- Das Dienst Konto, unter dem der Zielcomputer mit SQL Server ausgeführt wird, muss über Schreibzugriff auf den angegebenen Pfad der Ablauf Verfolgungs Datei verfügen.
- Das Dienst Konto, unter dem die Distributed Replay Client Dienste ausgeführt werden, muss über Benutzerrechte verfügen, um eine Verbindung mit dem Zielcomputer herzustellen, auf dem SQL Server ausgeführt wird, und um Abfragen auszuführen

### <a name="can-i-start-more-than-one-replay-in-the-same-session"></a>Kann ich mehr als eine Wiedergabe in derselben Sitzung starten?

Ja, Sie können mehrere Wiederholungen starten und diese bis zum Abschluss in derselben Sitzung nachverfolgen.

### <a name="can-i-start-more-than-one-replay-in-parallel"></a>Kann ich mehr als eine Wiedergabe parallel starten?

Ja, aber nicht mit derselben Gruppe von Computern, die in **Controller plus Clients**ausgewählt sind. Der Controller und die Clients werden ausgelastet sein. Richten Sie einen separaten Satz von Computern unter **Controller Plus Client** ein, um eine parallele Wiedergabe zu starten.

### <a name="how-long-does-a-replay-typically-take-to-finish"></a>Wie lange dauert es in der Regel, bis die Wiedergabe abgeschlossen ist?

Eine Wiedergabe dauert normalerweise denselben Zeitraum wie die Quell Ablauf Verfolgung zuzüglich der Zeitspanne, die für die Vorverarbeitung der Quell Ablauf Verfolgung benötigt wird. Wenn die Client Computer, die beim Controller registriert sind, jedoch nicht ausreichen, um die Last zu verwalten, die von der Wiedergabe erzeugt wird, kann die Wiedergabe länger dauern. Sie können bis zu 16 Client Computer mit dem Controller registrieren.

### <a name="how-large-do-target-trace-files-get"></a>Wie hoch sind Ablauf Verfolgungs Dateien für große Ziele?

Die Ziel-Ablauf Verfolgungs Dateien können zwischen der 5-bis 15-fachen Größe der Quell Ablauf Verfolgung liegen. Die Dateigröße basiert darauf, wie viele Abfragen ausgeführt werden. Beispielsweise können Abfrageplan-blobspeicher groß sein. Wenn sich die Statistiken für diese Abfragen häufig ändern, werden weitere Ereignisse aufgezeichnet.

### <a name="why-do-i-need-to-restore-databases"></a>Warum muss ich Datenbanken wiederherstellen?

SQL Server ist ein Zustands behaftetes relationales Datenbankverwaltungssystem. Um einen A/B-Test ordnungsgemäß auszuführen, muss der Status der Datenbank immer beibehalten werden. Andernfalls werden möglicherweise Fehler in Abfragen während der Wiedergabe angezeigt, die nicht in der Produktionsumgebung angezeigt werden. Um diese Fehler zu vermeiden, empfiehlt es sich, direkt vor der Quell Erfassung eine Sicherung durchführen. Ebenso ist die Wiederherstellung der Sicherung auf dem Zielcomputer mit SQL Server erforderlich, um Fehler während der Wiedergabe zu verhindern.

### <a name="what-does-pass--on-the-replay-page-mean"></a>Was bedeutet "Pass%" auf der Wiedergabe Seite?

" **Pass%** " bedeutet, dass nur ein Prozentsatz von Abfragen bestanden wurde. Sie können diagnostizieren, ob die Anzahl der Fehler erwartet wird. Die Fehler werden möglicherweise erwartet, oder die Fehler treten auf, weil die Datenbank die Integrität verloren hat. Wenn der Wert für " **Pass%** " nicht Ihren Erwartungen entspricht, können Sie die Ablauf Verfolgung abbrechen und die Ablauf Verfolgungs Datei in SQL Profiler sehen, um festzustellen, welche Abfragen nicht erfolgreich waren.

### <a name="how-can-i-look-at-the-trace-events-that-were-collected-during-replay"></a>Wie kann ich die Ablauf Verfolgungs Ereignisse untersuchen, die während der Wiedergabe erfasst wurden?

Öffnen Sie eine Ziel Ablauf Verfolgungs Datei, und zeigen Sie Sie in SQL Profiler an. Wenn Sie Änderungen an der Wiedergabe Erfassung vornehmen möchten, finden Sie alle SQL Server Skripts unter C:\\Programme (x86)\\Microsoft Corporation\\Assistent für Datenbankexperimente\\Scripts\\startreplaycapture. SQL.

### <a name="what-trace-events-does-dea-collect-during-replay"></a>Welche Ablauf Verfolgungs Ereignisse werden von DEA während der Wiedergabe gesammelt?

Mit der DEA werden Ablauf Verfolgungs Ereignisse erfasst, die leistungsbezogene Informationen enthalten. Die Aufzeichnungs Konfiguration befindet sich im Skript startreplaycapturetrace. SQL. Diese Ereignisse sind typische SQL Server Ablauf Verfolgungs Ereignisse, die in der [sp_trace_setevent (Transact-SQL)-Referenz Dokumentation](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)aufgeführt sind.

## <a name="troubleshoot-trace-replay"></a>Problembehandlung bei der Ablauf Verfolgungs Wiedergabe

### <a name="i-cant-connect-to-the-computer-thats-running-sql-server"></a>Ich kann keine Verbindung mit dem Computer herstellen, auf dem ausgeführt wird SQL Server

- Vergewissern Sie sich, dass der Name des Computers, der SQL Server ausgeführt wird, gültig ist. Versuchen Sie, eine Verbindung mit dem Server herzustellen, indem Sie SQL Server Management Studio (SSMS) verwenden.
- Vergewissern Sie sich, dass die Firewall-Konfiguration keine Verbindungen mit dem Computer blockiert, der SQL Server ausgeführt wird
- Vergewissern Sie sich, dass der Benutzer über die erforderlichen Benutzerrechte verfügt.
- Vergewissern Sie sich, dass das Dienst Konto des Distributed Replay Clients Zugriff auf den Computer hat, auf dem SQL Server ausgeführt wird.

Weitere Details finden Sie in den Protokollen unter% Temp%\\Dea. Wenn das Problem weiterhin besteht, wenden Sie sich an das Produktteam.

### <a name="i-cant-connect-to-the-distributed-replay-controller"></a>Ich kann keine Verbindung mit dem Distributed Replay Controller herstellen.

- Überprüfen Sie, ob der Distributed Replay Controller-Dienst auf dem Controller Computer ausgeführt wird. Um dies zu überprüfen, verwenden Sie die Distributed Replay-Verwaltungs Tools (führen Sie den Befehl `dreplay.exe status -f 1`aus).
- Wenn die Wiedergabe Remote gestartet wird:
  - Vergewissern Sie sich, dass der Computer, auf dem die DEA ausgeführt wird, erfolgreich ein Ping Vergewissern Sie sich, dass die Firewalleinstellungen Verbindungen gemäß den Anweisungen auf der Seite " **Wiedergabe Umgebung konfigurieren** " zulassen. Weitere Informationen finden Sie im Artikel [SQL Server Distributed Replay](https://docs.microsoft.com/sql/tools/distributed-replay/sql-server-distributed-replay?view=sql-server-2017).
  - Stellen Sie sicher, dass DCOM-Remote Start und Remote Aktivierung für den Benutzer des Distributed Replay Controllers zulässig sind.
  - Stellen Sie sicher, dass die DCOM-RAS-Benutzerrechte für den Benutzer Distributed Replay Controllers zulässig sind.

### <a name="the-trace-file-path-exists-on-my-machine-why-cant-distributed-replay-controller-find-it"></a>Der Pfad der Ablauf Verfolgungs Datei ist auf dem Computer vorhanden. Warum kann Distributed Replay Controller Sie nicht finden?

Distributed Replay können nur auf lokale Datenträger Ressourcen zugreifen. Sie müssen Quelldateien der Ablauf Verfolgung auf den Distributed Replay Controller-Computer kopieren, bevor Sie die Wiedergabe starten. Außerdem müssen Sie den Pfad auf der **neuen Wiedergabe** Seite von DEA angeben. 

UNC-Pfade sind nicht mit Distributed Replay kompatibel. Distributed Replay Pfade müssen lokale, absolute Pfade zur ersten Quelldatei der Ablauf Verfolgung sein, einschließlich der Erweiterung.

### <a name="why-cant-i-browse-for-files-on-the-new-replay-page"></a>Warum kann ich auf der neuen Wiedergabe Seite nicht nach Dateien suchen?

Da wir die Ordner eines Remote Computers nicht durchsuchen können, ist das Durchsuchen von Dateien nicht hilfreich. Das Kopieren und Einfügen der absoluten Pfade ist effizienter.

### <a name="i-started-replay-with-a-trace-but-distributed-replay-didnt-replay-any-events"></a>Die Wiedergabe wurde mit einer Ablauf Verfolgung gestartet, Distributed Replay aber keine Ereignisse wiedergegeben.

Dieses Problem tritt möglicherweise auf, weil die Ablauf Verfolgungs Datei entweder keine wieder aufwiedergabe Ereignisse enthält oder keine Informationen zum Wiedergeben von Ereignissen enthält. Vergewissern Sie sich, dass es sich bei dem angegebenen Pfad der Ablauf Verfolgungs Datei um eine Quelldatei Die Quelldatei der Ablauf Verfolgung wird erstellt, indem die im Skript "startcapturetrace. SQL" bereitgestellte Konfiguration verwendet wird.

### <a name="i-see-unexpected-error-occurred-when-i-try-to-preprocess-my-trace-files-by-using-the-sql-server-2017-distributed-replay-controller"></a>Ich sehe, dass ein unerwarteter Fehler aufgetreten ist. bei der Vorverarbeitung meiner Ablauf Verfolgungs Dateien mit dem SQL Server 2017 Distributed Replay Controller

Dieses Problem ist in der RTM-Version von SQL Server 2017 bekannt. Weitere Informationen finden Sie unter [unerwarteter Fehler bei Verwendung der dreplay-Funktion zum Wiedergeben einer aufgezeichneten Ablauf Verfolgung in SQL Server 2017](https://support.microsoft.com/help/4045678/fix-unexpected-error-when-you-use-the-dreplay-feature-to-replay-a).  
  
Das Problem wurde im aktuellen kumulativen Update 1 für SQL Server 2017 behoben. Laden Sie die neueste Version von [kumulativem Update 1 für SQL Server 2017](https://support.microsoft.com/help/4038634/cumulative-update-1-for-sql-server-2017)herunter.

## <a name="next-steps"></a>Nächste Schritte

- Informationen zum Erstellen eines Analyse Berichts, mit dem Sie Einblicke in vorgeschlagene Änderungen erhalten, finden Sie unter [Erstellen von Berichten](database-experimentation-assistant-create-report.md).

- Sehen Sie sich das folgende Video an, um die Einführung von DEA und Demo in 19 Minuten zu demonstrieren:

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
