---
title: Aufzeichnen einer Ablauf Verfolgung für SQL Server Upgrades
description: Verwenden Sie Assistent für Datenbankexperimente (DEA) zum Erstellen einer Ablauf Verfolgungs Datei mit einem Protokoll erfasster Server Ereignisse.
ms.custom: seo-lt-2019
ms.date: 12/12/2019
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: rajsell
ms.reviewer: mathoma
ms.openlocfilehash: c560aa2c5ba4b5113ce711601a4e85aab2788240
ms.sourcegitcommit: b80364e31739d7b08cc388c1f83bb01de5dd45c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87565592"
---
# <a name="capture-a-trace-in-database-experimentation-assistant"></a>Aufzeichnen einer Ablauf Verfolgung in Assistent für Datenbankexperimente

Sie können Assistent für Datenbankexperimente (DEA) verwenden, um eine Ablauf Verfolgungs Datei mit einem Protokoll erfasster Server Ereignisse zu erstellen. Ein erfasstes Server Ereignis ist ein Ereignis, das während eines bestimmten Zeitraums auf einem bestimmten Server auftritt. Eine Ablauf Verfolgungs Erfassung muss einmal pro Server ausgeführt werden.

Bevor Sie eine Ablauf Verfolgungs Erfassung starten, müssen Sie sicherstellen, dass Sie alle Ziel Datenbanken sichern.

Das Zwischenspeichern von Abfragen in SQL Server kann sich auf Auswertungs Ergebnisse auswirken Es wird empfohlen, den SQL Server-Dienst (MSSQLSERVER) in der Dienste-Anwendung neu zu starten, um die Konsistenz der Auswertungs Ergebnisse zu verbessern.

## <a name="configure-a-trace-capture"></a>Konfigurieren einer Ablauf Verfolgungs Erfassung

1. Wählen Sie in der linken Navigationsleiste auf der linken Seite das Kamerasymbol aus, und wählen Sie dann auf der Seite **alle** Erfassungen die Option **neue Erfassung**aus.

    ![Erstellen einer Erfassung in der DEA](./media/database-experimentation-assistant-capture-trace/dea-initiate-capture.png)

2. Geben Sie auf der Seite **neue Erfassung** unter **Aufzeichnungsdetails**die folgenden Informationen ein, oder wählen Sie Sie aus:

    - **Erfassungs Name**: Geben Sie einen Namen für die Ablauf Verfolgungs Datei für ihre Erfassung ein.
    - **Format**: Geben Sie das Format (Trace oder xevents) für die Erfassung an.
    - **Dauer**: Wählen Sie die Zeitdauer (in Minuten) aus, für die die Ablauf Verfolgungs Erfassung ausgeführt werden soll.
    - **Erfassungs Speicherort**: Wählen Sie den Zielpfad für die Ablauf Verfolgungs Datei aus.

        > [!NOTE]
        > Der Dateipfad zur Ablauf Verfolgungs Datei muss sich auf dem Computer befinden, auf dem SQL Server ausgeführt wird. Wenn der SQL Server-Dienst nicht für ein bestimmtes Konto festgelegt ist, benötigt der Dienst möglicherweise Schreibberechtigungen für den angegebenen Ordner, damit die Ablauf Verfolgungs Datei geschrieben werden kann.

3. Stellen Sie sicher, dass Sie eine Sicherung durchgeführt haben, indem Sie die Option **Ja, ich habe die Sicherung manuell erstellt...** .

4. Geben Sie unter **Aufzeichnungsdetails**die folgenden Informationen ein, oder wählen Sie Sie aus:

    - **Servertyp**: Geben Sie den SQL Server-Typ an (**SQLServer**, **azuresqldb**, **azuresqlmanagedinstance**).
    - **Servername**: Geben Sie den Servernamen oder die IP-Adresse Ihres SQL Server an.
    - **Authentifizierungstyp**: Wählen Sie als Authentifizierungstyp **Windows**aus.
    - **Datenbankname**: Geben Sie einen Namen für eine Datenbank ein, mit der eine Daten Bank Ablauf Verfolgung gestartet werden soll. Wenn Sie keine Datenbank angeben, wird die Ablauf Verfolgung für alle Datenbanken auf dem Server aufgezeichnet.

5. Aktivieren bzw. deaktivieren Sie die Kontrollkästchen **Verbindung verschlüsseln** und **Serverzertifikat vertrauen** entsprechend Ihrem Szenario.

    ![Neue Erfassungs Seite](./media/database-experimentation-assistant-capture-trace/dea-new-capture.png)

## <a name="start-the-trace-capture"></a>Starten der Ablauf Verfolgungs Erfassung

1. Nachdem Sie die erforderlichen Informationen eingegeben oder ausgewählt haben, klicken Sie auf **starten** , um die Ablauf Verfolgungs Erfassung zu initiieren.

    Wenn die eingegebenen Informationen gültig sind, beginnt der Ablauf Verfolgungs Erfassungs Vorgang. Andernfalls werden Textfelder mit ungültigen Einträgen rot hervorgehoben. Wenn Fehler auftreten, korrigieren Sie alle erforderlichen Einträge, und wählen Sie dann erneut **starten** aus.

    Während die Ablauf Verfolgungs Erfassung ausgeführt wird, werden unter **Aufzeichnungsdetails**der Status und der Fortschritt des Ablauf Verfolgungs Erfassungs Prozesses angezeigt.

    ![Überwachen des Aufzeichnungsstatus](./media/database-experimentation-assistant-capture-trace/dea-capture-running.png)

2. Wenn die Ausführung der Ablauf Verfolgungs Erfassung abgeschlossen ist, wird die neue Ablauf Verfolgungs Datei (. trc) an dem **Erfassungs Speicherort** gespeichert, den Sie bei der Erstkonfiguration festgestellt haben.

    ![Abgeschlossene Ablauf Verfolgungs Erfassung](./media/database-experimentation-assistant-capture-trace/dea-capture-complete.png)

    Die Ablauf Verfolgungs Datei enthält Ablauf Verfolgungs Ergebnisse der Aktivität einer SQL Server Datenbank. TRC-Dateien sind so konzipiert, dass Sie weitere Informationen zu Fehlern bereitstellen, die von SQL Server erkannt und gemeldet werden.

## <a name="frequently-asked-questions-about-trace-capture"></a>Häufig gestellte Fragen zur Ablauf Verfolgungs Erfassung

Im folgenden finden Sie einige häufig gestellte Fragen zur Erfassung von Ablauf Verfolgungen in Dea.

**F: welche Ereignisse werden aufgezeichnet, wenn ich eine Ablauf Verfolgungs Erfassung für eine Produktionsdatenbank führe?**

In der folgenden Tabelle werden die Ereignisse und die entsprechenden Spaltendaten aufgelistet, die von DEA für Ablauf Verfolgungen erfasst werden:
  
|Veranstaltungsname|Textdaten (1)|Binärdaten (2)|Datenbank-ID (3)|Hostname (8)|Anwendungs Name (10)|Anmelde Name (11)|SPID (12)|Startzeit (14)|Endzeit (15)|Datenbankname (35)|Ereignis Sequenz (51)|IsSystem (60)|  
|---|---|---|---|---|---|---|---|---|---|---|---|---|  
|**RPC: abgeschlossen (10)**||*|*|*|*|*|*|*|*|*|*|*|  
|**RPC: wird gestartet (11)**||*|*|*|*|*|*|*||*|*|*|  
|**RPC-Ausgabe Parameter (100)**|*||*|*|*|*|*|*||*|*|*|  
|**SQL: batchabgeschlossene (12)**|*||*|*|*|*|*|*|*|*|*|*|  
|**SQL: BatchStarting (13)**|*||*|*|*|*|*|*||*|*|*|  
|**Audit Login (14)**|*|*|*|*|*|*|*|*||*|*|*|  
|**Abmelde protokolerung (15)**|*||*|*|*|*|*|*|*|*|*|*|  
|**ExistingConnection (17)**|*|*|*|*|*|*|*|*||*|*|*|  
|**Cursor Open (53)**|*||*|*|*|*|*|*||*|*|*|  
|**Cursor Vorbereitung (70)**|*||*|*|*|*|*|*||*|*|*|  
|**Prepare SQL (71)**|||*|*|*|*|*|*||*|*|*|  
|**Exec Prepared SQL (72)**|||*|*|*|*|*|*||*|*|*|  
|**Cursor Execute (74)**|*||*|*|*|*|*|*||*|*|*|  
|**Currsorunprepare (77)**|*||*|*|*|*|*|*||*|*|*|  
|**Cursor schließen (78)**|*||*|*|*|*|*|*||*|*|*|  

**F: gibt es einen Leistungs Effekt auf dem Produktionsserver, wenn die Ablauf Verfolgungs Erfassung ausgeführt wird?**

Ja, es gibt eine minimale Leistungs Auswirkung während der Ablauf Verfolgungs Sammlung. In unseren Tests haben wir ungefähr eine Speicherauslastung von 3% festgestellt.

**F: welche Art von Berechtigungen sind zum Erfassen von Ablauf Verfolgungen für eine produktionsworkloads erforderlich?**

- Der Windows-Benutzer, der den Ablauf Verfolgungs Vorgang in der DEA-Anwendung ausführt, muss auf dem Computer, auf dem SQL Server ausgeführt wird, über Systemadministrator Rechte verfügen.
- Das Dienst Konto, das auf dem Computer verwendet wird, auf dem SQL Server ausgeführt wird, muss Schreibzugriff auf den angegebenen Pfad der Ablauf Verfolgungs Datei

**F: kann ich Ablauf Verfolgungen für den gesamten Server oder nur für eine einzelne Datenbank erfassen?**

Mithilfe von DEA können Sie Ablauf Verfolgungen für alle Datenbanken auf dem Server oder für eine einzelne Datenbank erfassen.

**F: Ich habe einen Verbindungs Server in der Produktionsumgebung konfiguriert. Werden diese Abfragen in den Ablauf Verfolgungen angezeigt?**

Wenn Sie eine Ablauf Verfolgungs Erfassung für den gesamten Server ausführen, erfasst die Ablauf Verfolgung alle Abfragen, einschließlich der verknüpften Server Abfragen. Wenn Sie eine Ablauf Verfolgungs Erfassung für den gesamten Server ausführen möchten, lassen Sie das Feld **Datenbankname** unter **neue Erfassung** leer.

**F: wie hoch ist die empfohlene Zeit für die Ablauf Verfolgung für die Arbeitsauslastung?**

Es wird empfohlen, dass Sie eine Zeit auswählen, die die gesamte Arbeitsauslastung am besten repräsentiert. Auf diese Weise wird die Analyse für alle Abfragen in Ihrer Arbeitsauslastung ausgeführt.

**F: wie wichtig ist es, eine Datenbanksicherung zu erstellen, bevor Sie eine Ablauf Verfolgungs Erfassung startet?**

Bevor Sie eine Ablauf Verfolgungs Erfassung starten, müssen Sie sicherstellen, dass Sie alle Ihre Ziel Datenbanken sichern. Die erfasste Ablauf Verfolgung in Ziel 1 und Ziel 2 wird wiedergegeben. Wenn der Daten Bank Status nicht identisch ist, werden die Ergebnisse der Experimente verzerrt.

**F: kann ich xevents anstelle von Ablauf Verfolgungen erfassen, und kann ich xevents wiedergeben?**

Ja. "DEA" unterstützt xevents. Laden Sie die neueste Version von DEA herunter, und probieren Sie Sie aus.

## <a name="troubleshoot-trace-captures"></a>Problembehandlung bei Ablauf Verfolgungs Aufzeichnungen

Wenn beim Ausführen einer Ablauf Verfolgungs Erfassung ein Fehler angezeigt wird, bestätigen Sie Folgendes:

- Der Name des Computers, auf dem SQL Server ausgeführt wird, ist gültig. Versuchen Sie, eine Verbindung mit dem Computer herzustellen, auf dem SQL Server ausgeführt wird, indem Sie SQL Server Management Studio (SSMS) verwenden.
- Die Firewallkonfiguration blockiert keine Verbindungen mit dem Computer, auf dem SQL Server ausgeführt wird.
- Der Benutzer verfügt über die Berechtigungen, die in den häufig gestellten Fragen zur wieder [Gabe](https://docs.microsoft.com/sql/dea/database-experimentation-assistant-replay-trace?view=sql-server-ver15#frequently-asked-questions-about-trace-replay)aufgeführt sind.
- Der Ablauf Verfolgungs Name folgt nicht der standardrolloverkonvention (Erfassung \_ 1). Versuchen Sie stattdessen, Namen von Ablauf Verfolgungen wie z \_ . b. Capture 1A oder Capture1

Im folgenden finden Sie einige mögliche Fehler, die möglicherweise angezeigt werden, und Lösungen für deren Behebung:

|Mögliche Fehler|Lösung|  
|---|---|  
|Die Ablauf Verfolgung kann nicht auf dem Ziel SQL Server gestartet werden. Überprüfen Sie, ob Sie über die erforderlichen Berechtigungen verfügen und dass das SQL Server Konto Schreibzugriff auf den angegebenen Pfad für die Ablauf Verfolgungs Datei hat SQL-Fehler Code (53).|Der Benutzer, der das Tool "DEA" ausgeführt hat, muss Zugriff auf den Computer mit SQL Server haben. Dem Benutzer muss die sysadmin-Rolle zugewiesen werden.|  
|Die Ablauf Verfolgung kann nicht auf dem Ziel SQL Server gestartet werden. Überprüfen Sie, ob Sie über die erforderlichen Berechtigungen verfügen und dass das SQL Server Konto Schreibzugriff auf den angegebenen Pfad für die Ablauf Verfolgungs Datei hat SQL-Fehler Code (19062).|Der angegebene Ablauf Verfolgungs Pfad ist möglicherweise nicht vorhanden, oder der Ordner verfügt nicht über Schreibberechtigungen für das Konto, unter dem SQL Server-Dienste ausgeführt werden (z. b. Netzwerkdienst). Der Pfad muss vorhanden sein und muss über die erforderlichen Berechtigungen verfügen, damit die Ablauf Verfolgung gestartet werden kann.|  
|Auf dem Zielserver wird derzeit eine DEA-Ablauf Verfolgung ausgeführt.|Eine aktive Ablauf Verfolgung wird bereits auf dem Zielserver ausgeführt. Eine neue Ablauf Verfolgung kann nicht gestartet werden, wenn bereits eine Server weite Ablauf Verfolgung ausgeführt wird.|  
|Die angeforderte Datenbank kann nicht zum Erfassen der Ablauf Verfolgung geöffnet werden. Dieser Fehler kann durch einen falschen Datenbanknamen verursacht werden.|Die angegebene Datenbank ist nicht vorhanden, oder der aktuelle Benutzer ist nicht verfügbar. Verwenden Sie den richtigen Datenbanknamen.|  

Wenn Sie andere Fehler mit der Bezeichnung *SQL-Fehler Code*sehen, finden Sie unter [Datenbank-Engine Fehler](https://docs.microsoft.com/sql/relational-databases/errors-events/database-engine-events-and-errors) ausführliche Beschreibungen.

## <a name="see-also"></a>Weitere Informationen

- Informationen zum Konfigurieren der Distributed Replay Tools in SQL Server vor der Wiedergabe einer aufgezeichneten Ablauf Verfolgung finden Sie unter [configure Distributed Replay for Assistent für Datenbankexperimente](database-experimentation-assistant-configure-replay.md).
