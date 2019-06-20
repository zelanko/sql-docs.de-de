---
title: Wiedergeben einer Ablaufverfolgungs mit dem Datenbank-experimentieren-Assistenten für SQL Server-upgrades
description: Wiedergeben einer Ablaufverfolgungs mit dem Datenbank-experimentieren-Assistenten
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
ms.reviewer: mathoma
manager: jroth
ms.openlocfilehash: 7db0e6a83997a3be7b204f780f3c0a7ad856b0d8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66794449"
---
# <a name="replay-a-trace-in-database-experimentation-assistant"></a>Wiedergeben einer Ablaufverfolgungs im Datenbank-experimentieren-Assistenten

In Datenbank experimentieren-Assistenten (DEA), können Sie eine aufgezeichnete Ablaufverfolgung-Datei anhand einer aktualisierten testumgebung wiedergeben. Betrachten Sie beispielsweise eine produktionsworkload, die auf SQL Server 2008 R2 ausgeführt wird. Die Ablaufverfolgungsdatei für die arbeitsauslastung zweimal wiedergegeben werden muss: einmal in einer Umgebung mit der gleichen Version von SQL Server, der ausgeführt wird, auf die Produktion und erneut auf eine Umgebung mit Upgrade Ziel SQL Server-Version, z. B. SQL Server 2016.

> [!NOTE]
> Um diese Aktion auszuführen, müssen Sie manuell virtuelle oder physische Computer einrichten, führen Sie die Distributed Replay-ablaufverfolgungen. Weitere Informationen finden Sie unter [Distributed Replay Controller und Clients Setup](https://blogs.msdn.microsoft.com/datamigration/distributed-replay-controller-and-client-setup/).
>
>

## <a name="create-a-trace-replay"></a>Erstellen Sie einen ablaufverfolgungswiedergabe

Wählen Sie in DEA das Symbol "Menü" ein. Wählen Sie im erweiterten Menü **Wiedergeben von Ablaufverfolgungen** neben dem Play-Symbol.

![Wählen Sie im Menü wiedergeben von Ablaufverfolgungen](./media/database-experimentation-assistant-replay-trace/dea-replay-trace-open.png)

> [!NOTE]
> Der Distributed Replay Controller-Computer erfordert Berechtigungen für das Benutzerkonto, mit denen Sie auf den Remotecomputer.
>

### <a name="grant-access-to-the-distributed-replay-controller"></a>Gewähren des Zugriffs auf den Distributed Replay-controller

1. Geben Sie an einer Eingabeaufforderung den Befehl **Dcomcnfg** zum Öffnen der **Komponentendienste** Schnittstelle.
1. Erweitern Sie **Komponentendienste** > **Computer** > **Arbeitsplatz** > **DCOM-Konfiguration**  >  **DReplayController**.
1. Mit der rechten Maustaste **DReplayController**, und wählen Sie dann **Eigenschaften**.
1. Auf der **Sicherheit** Registerkarte **bearbeiten** auf das Benutzerkonto hinzuzufügen.
1. Wählen Sie **OK**.

### <a name="verify-setup"></a>Überprüfen der Installation

1.  **SQL Server-Installationspfad**: Geben Sie den Pfad zum Speicherort von SQL Server. Z. B. "c:"\\Programmdateien (x86)\\Microsoft SQL Server\\120.
1.  **Der Name des Controllercomputers**: Geben Sie einen Namen für den Computer, der als Controller eingerichtet wurde. Dieser Computer wird die Windows-Dienst, der mit dem Namen SQL Server Distributed Replay Controller ausgeführt. Der Distributed Replay Controller koordiniert die Aktionen der Distributed Replay Clients an. Es kann in jeder Distributed Replay-Umgebung jeweils nur eine Controllerinstanz geben.
1.  **Client-Computernamen**: Geben Sie einen Namen für jeden Clientcomputer, die durch Kommas getrennt ein. Beispiel: client1 client2. Sie können bis zu fünf Client-Controller verfügen. Clients können einen oder mehrere Computer, entweder physisch oder virtuell, die der Windows-Dienst, der mit dem Namen SQL Server Distributed Replay Client ausgeführt werden. Die Distributed Replay Clients simulieren gemeinsam Arbeitsauslastungen auf einer Instanz von SQL Server. In jeder Distributed Replay-Umgebung kann sich mindestens ein Client befinden.
1.  Wählen Sie **Weiter**aus.

### <a name="select-a-trace"></a>Wählen Sie eine Ablaufverfolgung

1.  **Pfad zur Ablaufverfolgungsdatei**: Geben Sie den Pfad der Eingabe-Ablaufverfolgungsdatei (TRC).
1.  **Pfad zum Speichern von Replay vorverarbeiten Ausgabe**:  
    \- Wenn Sie die Datei IRF noch nicht, geben Sie den Pfad zum Speicherort, in dem Sie die IRF-Datei speichern möchten, und andere vorverarbeitung gibt.  
    \- Wenn Sie bereits die IRF-Datei verfügen, geben Sie den Pfad zu den IRF-Dateien.
1. Wählen Sie **Weiter**aus.

### <a name="replay-a-trace"></a>Wiedergeben einer Ablaufverfolgungs

1.  **Name der Ablaufverfolgungsdatei**: Geben Sie einen Dateinamen für die Ablaufverfolgung aus.
1.  **Maximale Dateigröße (MB)** : Geben Sie einen Ablaufverfolgung Rollover Wert für die Dateigröße. Der Standardwert ist 200 MB. Sie können einen benutzerdefinierten Wert eingeben.
1.  **Pfad zum Speichern der Ablaufverfolgungsausgabe Replay**: Geben Sie den Pfad für die Ausgabe TRC-Datei ein.
1.  **SQL Server-Instanzname**:  Geben Sie den Namen der SQL Server-Instanz für die Wiedergabe von ablaufverfolgungen aus.
1.  Wählen Sie **Starten** aus.

Wenn die Informationen, die Sie eingegeben haben, gültig ist, wird der Distributed Replay-Prozess gestartet. Der Text Boses, die falsche Informationen enthalten sind, andernfalls mit roten hervorgehoben. Stellen Sie sicher, dass die eingegebenen Werte richtig sind, und Sie dann wählen **starten**.

Warten Sie bis zum Abschluss der Wiedergabe ausgeführt wird, um den Speicherort anzuzeigen, die Sie angegeben haben. Wählen Sie das Glockensymbol am unteren Rand im linken Menü die Replay-Status überwachen.

![Wiedergeben von Ablaufverfolgungen wird ausgeführt](./media/database-experimentation-assistant-replay-trace/dea-replay-trace-progress.png)

## <a name="frequently-asked-questions-about-trace-replay"></a>Häufig gestellte Fragen zur Wiedergabe von ablaufverfolgungen

### <a name="what-security-permissions-do-i-need-to-start-a-replay-capture-on-my-target-server"></a>Welche Sicherheitsberechtigungen muss ich eine Replay-Erfassung auf Meine Zielserver zu starten?

- Der Windows-Benutzer, der der Trace-Vorgang, in der Anwendung DEA ausgeführt wird muss über Systemadministratorrechte auf dem Zielcomputer mit SQL Server verfügen. Diese Berechtigungen sind erforderlich, beim Starten einer Ablaufverfolgung.
- Das Dienstkonto, unter dem der Zielcomputer mit SQL Server ausgeführt wird, benötigen Schreibzugriff auf den Dateipfad für die angegebene Ablaufverfolgung.
- Das Dienstkonto, unter dem die Distributed Replay Client-Dienste ausgeführt werden, müssen die Benutzerrechte für die Verbindung mit dem Zielcomputer mit SQL Server sowie zum Ausführen von Abfragen.

### <a name="can-i-start-more-than-one-replay-in-the-same-session"></a>Kann ich mehr als eine Wiedergabe in der gleichen Sitzung starten?

Ja, können Sie mehrere Replays gestartet und bis zum Abschluss in der gleichen Sitzung verfolgen.

### <a name="can-i-start-more-than-one-replay-in-parallel"></a>Kann ich mehr als eine Wiedergabe parallel starten?

Ja, aber nicht mit dem gleichen festgelegt, der Computer im ausgewählten **Controller sowie Clients**. Der Controller und -Clients werden ausgelastet sein. Richten Sie eine separate Gruppe von Computern unter **Controller und Client** um eine parallele Wiedergabe zu starten.

### <a name="how-long-does-a-replay-typically-take-to-finish"></a>Wie lange dauert eine Wiedergabe in der Regel abgeschlossen?

Eine Wiedergabe dauert in der Regel die gleiche Menge an Zeit wie die Quell-Ablaufverfolgung sowie die Menge der Zeitaufwand zum vorverarbeiten der Source-Ablaufverfolgungs. Wenn die Clientcomputer, die mit dem Controller registriert sind nicht ausreichen, um die Last, die erzeugt wird aus der Wiedergabe verwaltet, kann die Wiedergabe jedoch mehr Zeit in Anspruch dauern. Sie können bis zu 16 Clientcomputer mit dem Controller registrieren.

### <a name="how-large-do-target-trace-files-get"></a>Wie groß erhalte Ablaufverfolgungsdateien Ziel?

Die Ziel-Ablaufverfolgung, die Dateien möglicherweise zwischen 5 und 15 Mal die Größe der Quelle der Ablaufverfolgung. Die Größe basiert auf wie viele Abfragen ausgeführt werden. Abfrage-Plan Blobs können z. B. groß sein. Wenn die Statistiken für diese Abfragen häufig ändern, werden weitere Ereignisse erfasst.

### <a name="why-do-i-need-to-restore-databases"></a>Warum muss ich Datenbanken wiederherstellen?

SQL Server ist ein zustandsbehafteter relationalen Datenbankverwaltungssystem. Zur ordnungsgemäßen Ausführung der einen A / B-Tests, den Status der Datenbank jederzeit beibehalten werden muss. Andernfalls werden möglicherweise Fehler in Abfragen während der Wiedergabe angezeigt, die in der Produktion nicht angezeigt wird. Um diesen Fehler zu vermeiden, empfehlen wir, dass Sie eine Sicherung direkt vor dem Quelle ausführen. Ebenso ist das Wiederherstellen der Sicherung auf dem Zielcomputer mit SQL Server erforderlich, um Fehler zu vermeiden, während der Wiedergabe.

### <a name="what-does-pass--on-the-replay-page-mean"></a>Was "% auf den Mittelwert der Wiedergabe pass"?

**Übergeben Sie %** bedeutet, die nur ein prozentualer Anteil der Abfragen zu übergeben. Sie können erkennen, ob die Anzahl der Fehler erwartet wird. Die Fehler ggf. erwartet werden, oder der Fehler können auftreten, da die Datenbank, seine Integrität verloren hat. Wenn der Wert für **Pass %** ist nicht, was Sie erwarten, können Sie die Ablaufverfolgung beendet und sehen Sie sich die Datei in SQL Profiler, um festzustellen, welche Abfragen nicht erfolgreich war.

### <a name="how-can-i-look-at-the-trace-events-that-were-collected-during-replay"></a>Wie kann ich die Ablaufverfolgungsereignisse betrachten, die während der Wiedergabe erfasst wurden?

Öffnen Sie eine Zieldatei für die Ablaufverfolgung, und in SQL Profiler anzeigen. Oder, wenn Sie Änderungen an der Wiedergabe Erfassung vornehmen möchten, die alle SQL Server-Skripts finden Sie unter "c:"\\Programmdateien (x86)\\Microsoft Corporation\\Database experimentieren Assistant\\Skripts\\ StartReplayCapture.sql.

### <a name="what-trace-events-does-dea-collect-during-replay"></a>Welche Ablaufverfolgungsereignissen erfasst DEA während der Wiedergabe?

DEA erfasst Ablaufverfolgungsereignisse, die leistungsbezogene Informationen enthalten. Die Capture-Konfiguration befindet sich im Skript StartReplayCaptureTrace.sql. Diese Ereignisse sind typische SQL Server-Ablaufverfolgungsereignisse, die in aufgeführt sind die [Sp_trace_setevent (Transact-SQL)-Referenzdokumentation](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql).

## <a name="troubleshoot-trace-replay"></a>Problembehandlung bei der Wiedergabe von ablaufverfolgungen

### <a name="i-cant-connect-to-the-computer-thats-running-sql-server"></a>Ich kann nicht auf dem Computer eine Verbindung herstellen, auf denen SQL Server ausgeführt wird

- Vergewissern Sie sich, dass der Name der SQL Server-Computers gültig ist. Versuchen Sie, mit dem Server hergestellt werden soll, mithilfe von SQL Server Management Studio (SSMS), um zu bestätigen.
- Vergewissern Sie sich, dass die Konfiguration der Firewall Verbindungen mit dem Computer mit SQL Server nicht blockiert.
- Vergewissern Sie sich, dass der Benutzer die erforderlichen Benutzerrechte verfügt.
- Vergewissern Sie sich, dass der Distributed Replay Client Dienstkonto Zugriff auf den Computer, auf denen SQL Server ausgeführt wird.

Sie erhalten weitere Informationen in den Protokollen im % temp %\\DEA. Wenn das Problem weiterhin besteht, wenden Sie sich an das Produktteam.

### <a name="i-cant-connect-to-the-distributed-replay-controller"></a>Ich kann nicht mit dem Distributed Replay-Controller verbinden.

- Stellen Sie sicher, dass der Distributed Replay Controller-Dienst auf dem Controllercomputer ausgeführt wird. Um sicherzustellen, verwenden Sie die Distributed Replay-Verwaltungstools (führen Sie den Befehl `dreplay.exe status -f 1`).
- Wenn die Wiedergabe Remote gestartet wird:
  - Vergewissern Sie sich, dass den Controller wurde erfolgreich von der Computer mit DEA Pingen kann. Bestätigen Sie, dass die Firewall-Einstellungen die Verbindungen gemäß den Anweisungen auf ermöglichen die **Replay-Umgebung konfigurieren** Seite. Weitere Informationen finden Sie im Artikel [SQL Server Distributed Replay](https://docs.microsoft.com/sql/tools/distributed-replay/sql-server-distributed-replay?view=sql-server-2017).
  - Stellen Sie sicher, dass DCOM Remotestart und Remoteaktivierung für den Benutzer des Distributed Replay-Controller zulässig sind.
  - Stellen Sie sicher, dass DCOM Remote Access Benutzerrechte für den Benutzer des Distributed Replay-Controller zulässig sind.

### <a name="the-trace-file-path-exists-on-my-machine-why-cant-distributed-replay-controller-find-it"></a>Der Dateipfad für die Ablaufverfolgung, die auf meinem Computer vorhanden ist. Warum gefunden nicht Distributed Replay-Controller?

Distributed Replay kann nur lokalen Datenträger auf Ressourcen zugreifen. Sie müssen die Quelldateien für die Ablaufverfolgung mit dem Distributed Replay Controller-Computer kopieren, vor dem Starten der Wiedergabe. Darüber hinaus müssen Sie den Pfad angeben, auf die DEA **neue Replay** Seite. 

UNC-Pfade nicht mit Distributed Replay kompatibel sind. Distributed Replay-Pfade muss sich auf lokalen, absoluten Pfade zu den ersten Ablaufverfolgungs-Quelldatei, einschließlich der Erweiterung.

### <a name="why-cant-i-browse-for-files-on-the-new-replay-page"></a>Warum zugreifen ich kann nicht für Dateien auf der Seite "neue Replay"?

Da wir Ordner von einem Remotecomputer nicht durchsuchen können, ist das Durchsuchen von Dateien nicht nützlich. Kopieren und Einfügen die absolute Pfade ist effizienter.

### <a name="i-started-replay-with-a-trace-but-distributed-replay-didnt-replay-any-events"></a>Ich habe die Wiedergabe mit einer Ablaufverfolgung begonnen, aber Distributed Replay keine Ereignisse wiedergeben

Dieses Problem kann auftreten, da die Datei entweder keine wiedergebbaren Ereignisse oder es muss keine Informationen dazu, wie Ereignisse wiederzugeben. Überprüfen Sie, ob die angegebene Ablaufverfolgung-Dateipfad eine Ablaufverfolgungs-Quelldatei ist. Die Ablaufverfolgungs-Quelldatei wird erstellt, mit der Konfiguration, die im Skript StartCaptureTrace.sql bereitgestellt.

### <a name="i-see-unexpected-error-occurred-when-i-try-to-preprocess-my-trace-files-by-using-the-sql-server-2017-distributed-replay-controller"></a>Ich finden Sie unter "Unerwarteter Fehler aufgetreten!" Beim versuch, meinen Ablaufverfolgungsdateien vorverarbeiten, mit der SQL Server 2017 Distributed Replay-controller

Dieses Problem wird in der RTM-Version von SQL Server 2017 bezeichnet. Weitere Informationen finden Sie unter [unerwarteter Fehler auf, wenn Sie die DReplay-Funktion verwenden, um eine aufgezeichnete Ablaufverfolgung in SQL Server 2017 wiedergeben](https://support.microsoft.com/help/4045678/fix-unexpected-error-when-you-use-the-dreplay-feature-to-replay-a).  
  
Das Problem wurde in das neueste kumulative Update 1 für SQL Server 2017 behoben. Herunterladen der neuesten Version von [kumulative Update 1 für SQL Server 2017](https://support.microsoft.com/help/4038634/cumulative-update-1-for-sql-server-2017).

## <a name="next-steps"></a>Nächste Schritte

- Um einen Analysebericht zu erstellen, mit dem Sie Einblicke in die vorgeschlagenen Änderungen zu gewinnen können, finden Sie unter [Erstellen von Berichten](database-experimentation-assistant-create-report.md).

- Für einen 19-minütige Einführung in DEA und Demonstrationen im folgenden Video:

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
