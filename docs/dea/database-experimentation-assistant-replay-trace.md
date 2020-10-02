---
title: Wiedergeben einer Ablauf Verfolgung für SQL Server Upgrades
description: Erfahren Sie, wie Sie eine aufgezeichnete Ablauf Verfolgung mit Assistent für Datenbankexperimente für SQL Server Upgrades wiedergeben.
ms.custom: seo-lt-2019
ms.date: 12/12/2019
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: pochiraju
ms.author: rajpo
ms.reviewer: mathoma
ms.openlocfilehash: fa37fb348aa94e59ac3816d523cc5a30bc314713
ms.sourcegitcommit: 71d2389cf27156fa0404a6e6f65fb7a61c40789a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2020
ms.locfileid: "91636170"
---
# <a name="replay-a-trace-in-database-experimentation-assistant"></a>Wiedergeben einer Ablauf Verfolgung in Assistent für Datenbankexperimente

In Assistent für Datenbankexperimente (DEA) können Sie eine aufgezeichnete Ablauf Verfolgungs Datei für eine aktualisierte Testumgebung wiedergeben. Nehmen wir beispielsweise an, eine produktionsworkloads, die auf SQL Server 2008 R2 ausgeführt wird. Die Ablauf Verfolgungs Datei für die Arbeitsauslastung muss zweimal wiedergegeben werden: einmal in einer Umgebung mit derselben Version von SQL Server, die in der Produktionsumgebung ausgeführt wird, und ein zweites Mal in einer Umgebung, die das upgradeziel SQL Server Version aufweist, wie z. b. SQL Server 2016.

> [!NOTE]
> Die Wiedergabe einer Ablauf Verfolgung erfordert, dass Sie virtuelle Computer oder physische Computer manuell einrichten, um Distributed Replay Ablauf Verfolgungen auszuführen. Weitere Informationen finden Sie unter [Konfigurieren von Distributed Replay für Assistent für Datenbankexperimente](database-experimentation-assistant-configure-replay.md).
>

## <a name="configure-a-trace-replay-for-target-1"></a>Konfigurieren einer Ablauf Verfolgungs Wiedergabe für Ziel 1

Zunächst müssen Sie eine Ablauf Verfolgungs Wiedergabe für Ziel 1 ausführen, das Ihre vorhandene Produktionsumgebung repräsentiert.

1. Wählen Sie in der linken Navigationsleiste auf der linken Seite das Pfeilsymbol aus, und wählen Sie dann auf der Seite **alle wieder** gaben die Option **neue Wiedergabe**aus.

    ![Erstellen einer Wiedergabe in der DEA](./media/database-experimentation-assistant-replay-trace/dea-create-replay.png)

    > [!NOTE]
    > Der Distributed Replay Controller-Computer erfordert Berechtigungen für das Benutzerkonto, das Sie für die Remote Verbindung verwenden.

2. Geben Sie auf der Seite **neue Wiedergabe** unter **Wiedergabe Details**die folgenden Informationen ein, oder wählen Sie Sie aus:

    - **Wiedergabe Name**: Geben Sie einen Namen für die Wiedergabe der Ablauf Verfolgung ein.
    - **Format der Quell**Ablauf Verfolgung: Geben Sie das Format (Trace oder xevents) der Quelldatei der Ablauf Verfolgung an.
    - **Vollständiger Pfad zur Quelldatei**: Geben Sie den vollständigen Pfad zur Quelldatei der Ablauf Verfolgung an. Wenn Sie dreplay verwenden, muss die Datei auf dem Computer vorhanden sein, der als dreplay-Controller fungiert, und das Benutzerkonto muss auf die Datei und den Ordner zugreifen können.
    - **Wiedergabe Tool**: Geben Sie das Replay-Tool an (dreplay oder inbuild).
    - **Controller Computername**: Geben Sie den Namen des Computers an, der als Distributed Replay Controller fungiert.
    - **Speicherort der Wiedergabe Ablauf Verfolgung**: Geben Sie den Pfad zum Speichern der Ablauf Verfolgungs Dateien/der der Ablauf Verfolgungs Wiedergabe zugeordneten xevents an

        > [!NOTE]
        > Für eine Azure SQL-Datenbank oder eine Azure SQL-verwaltete Instanz müssen Sie den SAS-URI des Azure BLOB Storage-Kontos bereitstellen.

3. Vergewissern Sie sich, dass Sie die Datenbank (en) wieder hergestellt haben, indem Sie das Kontrollkästchen **Ja, ich habe die Datenbank (en) manuell wieder hergestellt** .

4. Geben Sie unter **SQL Server Verbindungsdetails**die folgenden Informationen ein, oder wählen Sie Sie aus:

    - **Servertyp**: Geben Sie den SQL Server-Typ an (**SQLServer**, **azuresqldb**, **azuresqlmanagedinstance**).
    - **Servername**: Geben Sie den Servernamen oder die IP-Adresse Ihres SQL Server an.
    - **Authentifizierungstyp**: Wählen Sie als Authentifizierungstyp **Windows**aus.
    - **Datenbankname**: Geben Sie einen Namen für eine Datenbank ein, auf der eine serverseitige Ablauf Verfolgung gestartet werden soll. Wenn Sie keine Datenbank angeben, wird die Ablauf Verfolgung für alle Datenbanken auf dem Server aufgezeichnet.

5. Aktivieren bzw. deaktivieren Sie die Kontrollkästchen **Verbindung verschlüsseln** und **Serverzertifikat vertrauen** entsprechend Ihrem Szenario.

    ![Neue Wiedergabe Seite](./media/database-experimentation-assistant-replay-trace/dea-new-replay.png)

## <a name="start-the-trace-replay-on-target-1"></a>Ablauf Verfolgungs Wiedergabe auf Ziel 1 starten

- Nachdem Sie die erforderlichen Informationen eingegeben oder ausgewählt haben, klicken Sie auf **starten** , um die Ablauf Verfolgungs Wiedergabe zu initiieren.

  Wenn die eingegebenen Informationen gültig sind, wird der Distributed Replay Prozess gestartet. Andernfalls werden die Textfelder, die falsche Informationen enthalten, rot hervorgehoben. Stellen Sie sicher, dass die eingegebenen Werte richtig sind, und klicken Sie dann auf **starten**.

  ![Wiedergabe Fortschritt für Ziel 1](./media/database-experimentation-assistant-replay-trace/dea-run-replay-target1.png)

  Sie können den Prozess nach Bedarf überwachen. Wenn die Wiedergabe abgeschlossen ist, speichert DEA die Ergebnisse in einer Datei an dem Speicherort, den Sie angegeben haben.

  ![Wiedergabe für Ziel 1 ist beendet](./media/database-experimentation-assistant-replay-trace/dea-replay-target1-complete.png)

## <a name="perform-the-trace-replay-against-target-2"></a>Ausführen der Ablauf Verfolgungs Wiedergabe für Ziel 2

Nachdem Sie die Ablauf Verfolgungs Wiedergabe für Ziel 1 abgeschlossen haben, müssen Sie die gleichen Schritte für das zweite Ziel ausführen, das die gewünschte Upgradeumgebung darstellt.

1. Konfigurieren Sie die Wiedergabe einer Ablauf Verfolgung. verwenden Sie dieses Mal Details, die der Zielumgebung 2 zugeordnet sind.
2. Starten Sie die Ablauf Verfolgungs Wiedergabe auf Ziel 2.

   Sie können den Prozess nach Bedarf überwachen. Wenn die Wiedergabe abgeschlossen ist, speichert DEA die Ergebnisse in einer Datei an dem Speicherort, den Sie angegeben haben.

## <a name="frequently-asked-questions-about-trace-replay"></a>Häufig gestellte Fragen zur Wiedergabe der Ablauf Verfolgung

**F: welche Sicherheits Berechtigungen benötige ich, um eine Wiedergabe Erfassung auf meinem Zielserver zu starten?**

- Der Windows-Benutzer, der den Ablauf Verfolgungs Vorgang in der DEA-Anwendung durchführt, muss über Systemadministrator Rechte auf dem Zielcomputer verfügen, auf dem SQL Server ausgeführt wird. Diese Benutzerrechte sind erforderlich, um eine Ablauf Verfolgung zu starten.
- Das Dienst Konto, unter dem der Zielcomputer mit SQL Server ausgeführt wird, muss über Schreibzugriff auf den angegebenen Pfad der Ablauf Verfolgungs Datei verfügen.
- Das Dienst Konto, unter dem die Distributed Replay Client Dienste ausgeführt werden, muss über Benutzerrechte verfügen, um eine Verbindung mit dem Zielcomputer herzustellen, auf dem SQL Server ausgeführt wird, und um Abfragen auszuführen

**F: kann ich mehr als eine Wiedergabe in derselben Sitzung starten?**

Ja, Sie können mehrere Wiederholungen starten und diese bis zum Abschluss in derselben Sitzung nachverfolgen.

**F: kann ich mehr als eine Wiedergabe parallel starten?**

Ja, jedoch nicht mit derselben Gruppe von Computern, die in **Controller plus Clients**ausgewählt sind. Der Controller und die Clients werden ausgelastet sein. Richten Sie eine separate Gruppe von Computern unter **Controller Plus Client** ein, um eine parallele Wiedergabe zu starten.

**F: wie lange dauert es in der Regel, bis die Wiedergabe abgeschlossen ist?**

Eine Wiedergabe dauert normalerweise denselben Zeitraum wie die Quell Ablauf Verfolgung zuzüglich der Zeitspanne, die für die Vorverarbeitung der Quell Ablauf Verfolgung benötigt wird. Wenn die Client Computer, die mit dem Controller registriert sind, jedoch nicht ausreichen, um die Last zu verwalten, die von der Wiedergabe erzeugt wird, kann es länger dauern, bis die Wiedergabe ausgeführt wird. Sie können bis zu 16 Client Computer mit dem Controller registrieren.

**F: wie groß sind die Zieldateien für die Ablauf Verfolgung?**

Die Ziel-Ablauf Verfolgungs Dateien können zwischen der 5-und 15-fachen Größe der Quell Ablauf Verfolgung liegen. Die Dateigröße basiert darauf, wie viele Abfragen ausgeführt werden. Beispielsweise können Abfrageplan-blobspeicher groß sein. Wenn sich die Statistiken für diese Abfragen häufig ändern, werden weitere Ereignisse aufgezeichnet.

**F: Warum muss ich Datenbanken wiederherstellen?**

SQL Server ist ein Zustands behaftetes relationales Datenbankverwaltungssystem. Um einen A/B-Test ordnungsgemäß auszuführen, muss der Status der Datenbank immer beibehalten werden. Andernfalls werden möglicherweise Fehler in Abfragen während der Wiedergabe angezeigt, die nicht in der Produktionsumgebung angezeigt werden. Um diese Fehler zu vermeiden, empfiehlt es sich, direkt vor der Quell Erfassung eine Sicherung durchführen. Ebenso ist die Wiederherstellung der Sicherung auf dem Zielcomputer mit SQL Server erforderlich, um Fehler während der Wiedergabe zu verhindern.

**F: Was bedeutet "Pass%" auf der Wiedergabe Seite?**

" **Pass%** " bedeutet, dass nur ein Prozentsatz von Abfragen bestanden wurde. Sie können diagnostizieren, ob die Anzahl der Fehler erwartet wird. Die Fehler werden möglicherweise erwartet, oder die Fehler treten auf, weil die Datenbank die Integrität verloren hat. Wenn der Wert für " **Pass%** " nicht Ihren Erwartungen entspricht, können Sie die Ablauf Verfolgung abbrechen und die Ablauf Verfolgungs Datei in SQL Profiler sehen, um festzustellen, welche Abfragen nicht erfolgreich waren.

**F: Wie kann ich die Ablauf Verfolgungs Ereignisse untersuchen, die während der Wiedergabe erfasst wurden?**

Öffnen Sie eine Ziel Ablauf Verfolgungs Datei, und zeigen Sie Sie in SQL Profiler an. Wenn Sie Änderungen an der Wiedergabe Erfassung vornehmen möchten, finden Sie alle SQL Server Skripts unter C: \\ Programme (x86) \\ Microsoft Corporation \\ Assistent für Datenbankexperimente \\ Scripts \\ startreplaycapture. SQL.

**F: welche Ablauf Verfolgungs Ereignisse werden von DEA während der Wiedergabe gesammelt?**

Mit der DEA werden Ablauf Verfolgungs Ereignisse erfasst, die leistungsbezogene Informationen enthalten. Die Aufzeichnungs Konfiguration befindet sich im Skript startreplaycapturetrace. SQL. Diese Ereignisse sind typische SQL Server Ablauf Verfolgungs Ereignisse, die in der [sp_trace_setevent (Transact-SQL)-Referenz Dokumentation](../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)aufgeführt sind.

## <a name="troubleshoot-trace-replay"></a>Problembehandlung bei der Ablauf Verfolgungs Wiedergabe

**F: Warum kann ich keine Verbindung mit dem Computer herstellen, auf dem SQL Server ausgeführt wird?**

- Vergewissern Sie sich, dass der Name des Computers, der SQL Server ausgeführt wird, gültig ist. Versuchen Sie, eine Verbindung mit dem Server herzustellen, indem Sie SQL Server Management Studio (SSMS) verwenden.
- Vergewissern Sie sich, dass die Firewall-Konfiguration keine Verbindungen mit dem Computer blockiert, der SQL Server ausgeführt wird
- Vergewissern Sie sich, dass der Benutzer über die erforderlichen Benutzerrechte verfügt.
- Vergewissern Sie sich, dass das Dienst Konto des Distributed Replay Clients Zugriff auf den Computer hat, auf dem SQL Server ausgeführt wird.

Weitere Details finden Sie in den Protokollen unter% Temp% \\ Dea. Wenn das Problem weiterhin besteht, wenden Sie sich an das Produktteam.

**F: Warum kann ich keine Verbindung mit dem Distributed Replay Controller herstellen?**

- Überprüfen Sie, ob der Distributed Replay Controller-Dienst auf dem Controller Computer ausgeführt wird. Um dies zu überprüfen, verwenden Sie die Distributed Replay Verwaltungs Tools (führen Sie den Befehl aus `dreplay.exe status -f 1` ).
- Wenn die Wiedergabe Remote gestartet wird:
  - Vergewissern Sie sich, dass der Computer, auf dem "DEA" ausgeführt wird, ein Ping Vergewissern Sie sich, dass die Firewalleinstellungen Verbindungen gemäß den Anweisungen auf der Seite " **Wiedergabe Umgebung konfigurieren** " zulassen. Weitere Informationen finden Sie im Artikel [SQL Server Distributed Replay](../tools/distributed-replay/sql-server-distributed-replay.md?view=sql-server-2017).
  - Stellen Sie sicher, dass DCOM-Remote Start und Remote Aktivierung für den Benutzer des Distributed Replay Controllers zulässig sind.
  - Stellen Sie sicher, dass die DCOM-RAS-Benutzerrechte für den Benutzer des Distributed Replay Controllers zulässig sind.

**F: der Pfad der Ablauf Verfolgungs Datei ist auf dem Computer vorhanden. Warum kann Distributed Replay Controller Sie nicht finden?**

Distributed Replay können nur auf lokale Datenträger Ressourcen zugreifen. Sie müssen Quelldateien der Ablauf Verfolgung auf den Distributed Replay Controller-Computer kopieren, bevor Sie die Wiedergabe starten. Außerdem müssen Sie den Pfad auf der **neuen Wiedergabe** Seite von DEA angeben.

UNC-Pfade sind nicht mit Distributed Replay kompatibel. Distributed Replay Pfade müssen lokale, absolute Pfade zur ersten Quelldatei der Ablauf Verfolgung sein, einschließlich der Erweiterung.

**F: Warum kann ich auf der neuen Wiedergabe Seite nicht nach Dateien suchen?**

Da es nicht möglich ist, Ordner auf einem Remote Computer zu durchsuchen, ist das Suchen nach Dateien nicht hilfreich. Es ist effizienter, die absoluten Pfade zu kopieren und einzufügen.

**F: Ich habe die Wiedergabe mit einer Ablauf Verfolgung gestartet, Distributed Replay jedoch keine Ereignisse wiedergegeben. Dafür?**

Das Problem kann auftreten, wenn die Ablauf Verfolgungs Datei weder die wieder aufwiedergabe Ereignisse enthält noch Informationen zum Wiedergeben von Ereignissen enthält. Vergewissern Sie sich, dass der Pfad der Ablauf Verfolgungs Datei auf eine Quelldatei der Ablauf Verfolgung verweist. Die Quelldatei der Ablauf Verfolgung wird erstellt, indem die im Skript "startcapturetrace. SQL" bereitgestellte Konfiguration verwendet wird.

**F: Ich sehe, dass ein unerwarteter Fehler aufgetreten ist, wenn ich versuche, meine Ablauf Verfolgungs Dateien mit dem SQL Server 2017 Distributed Replay Controller vorzuverarbeiten. Dafür?**

Dieses Problem ist in der RTM-Version von SQL Server 2017 bekannt. Weitere Informationen finden Sie unter [unerwarteter Fehler bei Verwendung der dreplay-Funktion zum Wiedergeben einer aufgezeichneten Ablauf Verfolgung in SQL Server 2017](https://support.microsoft.com/help/4045678/fix-unexpected-error-when-you-use-the-dreplay-feature-to-replay-a).  
  
Das Problem wurde im aktuellen kumulativen Update 1 für SQL Server 2017 behoben. Laden Sie die neueste Version von [kumulativem Update 1 für SQL Server 2017](https://support.microsoft.com/help/4038634/cumulative-update-1-for-sql-server-2017)herunter.

## <a name="see-also"></a>Weitere Informationen

- Informationen zum Erstellen eines Analyse Berichts, mit dem Sie Einblicke in vorgeschlagene Änderungen erhalten, finden Sie unter [Erstellen von Berichten](database-experimentation-assistant-create-report.md).