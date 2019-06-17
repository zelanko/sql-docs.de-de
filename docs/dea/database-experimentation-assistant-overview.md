---
title: Übersicht über die der Datenbank-experimentieren-Assistenten für SQL Server-Lösung wird aktualisiert
description: Übersicht über die für Datenbankexperimente
ms.custom: ''
ms.date: 01/08/2019
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
ms.openlocfilehash: 25b5d051f6241919f34a60a42582e8a101052290
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66794460"
---
# <a name="overview-of-database-experimentation-assistant"></a>Übersicht über die für Datenbankexperimente

Datenbank experimentieren-Assistenten (DEA) ist eine experimentieren-Lösung für die SQL Server-Upgrades. DEA können Sie die Zielversion von SQL Server für eine bestimmte Arbeitslast zu bewerten. Kunden, die von SQL Server-Vorgängerversionen (2005 ab) auf eine neuere Version von SQL Server aktualisieren, können die Metriken für die Analyse, die das Tool bietet. 

Beispiele für DEA Analysis Metriken:
- Abfragen mit Kompatibilitätsfehler
- Beeinträchtigten Abfragen und Abfragepläne
- Andere Workloads Vergleichsdaten

Vergleichsdaten können höhere Zuverlässigkeit und einem erfolgreichen Upgradevorgang führen.

Für einen 19-minütige Einführung in DEA sowie eine Demonstration im folgenden Video:

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]

## <a name="get-dea"></a>DEA abrufen

Zum Installieren von DEA [herunterladen](https://www.microsoft.com/download/details.aspx?id=54090) die neueste Version des Tools. Führen Sie dann die **DatabaseExperimentationAssistant.exe** Datei.

## <a name="solution-architecture-for-comparing-workloads"></a>Architektur der Lösung für den Vergleich von workloads

Das folgende Diagramm zeigt die Lösungsarchitektur für einen Vergleich der arbeitsauslastung. Der Vergleich der Workload verwendet DEA "und" Distributed Replay während eines Upgrades von SQL Server 2008 auf SQL Server 2016.

![Workload-Vergleich Lösungsarchitektur](./media/database-experimentation-assistant-overview/dea-overview-compare-solution-architecture.png)

## <a name="dea-prerequisites"></a>DEA-Voraussetzungen

Es folgen einige erforderliche Komponenten für die Ausführung von DEA:
- Minimale hardwareanforderungen: Ein Single-Core-Computer mit 3,5 GB RAM.
- Ideale hardwareanforderungen: Eine 8-Kern-CPU (mit 3,5 GB RAM oder mehr). DEA Laufzeiten nicht Prozessoren, die mehr als acht Kerne verbessert werden.
- Weitere 33 % der Leistung Ablaufverfolgung Größe ist für die Store A, B und Analysedatenbanken Berichts benötigt.

## <a name="configure-dea"></a>DEA konfigurieren

Architektur der erforderlichen Umgebung empfehlen wir die Installation von DEA *auf dem gleichen Computer wie den Distributed Replay Controller*. Diese Vorgehensweise verhindert computerübergreifende Aufrufe und vereinfacht die Konfiguration.

### <a name="required-configuration-for-workload-comparison-by-using-dea"></a>Erforderliche Konfiguration für den Vergleich der Workload mit DEA

DEA eine Verbindung mit Datenbank-Server mithilfe der Windows-Authentifizierung herstellt. Achten Sie darauf, dass ein Benutzer ausführt DEA mithilfe der Windows-Authentifizierung eine Verbindung zu Datenbank-Servern (Quelle, Ziel und Analyse) herstellen kann.

**Erfassen von Anforderungen an die**:

*   Benutzer, der ausführt DEA kann mithilfe der Windows-Authentifizierung auf dem Quellserver für die Datenbank verbinden.
*   Benutzer, die mit DEA hat Sysadmin-Rechte auf dem Quellserver für die Datenbank an.
*   Dienstkonto mit dem Quellserver für die Datenbank verfügt über Schreibzugriff auf den Ordnerpfad für die Ablaufverfolgung.

Weitere Informationen finden Sie unter den [erfassen – häufig gestellte Fragen](database-experimentation-assistant-capture-trace.md#frequently-asked-questions-about-trace-capture)

**Anforderungen für die Konfiguration die Wiedergabe**: 

*   Benutzer, der ausführt DEA kann mithilfe der Windows-Authentifizierung auf dem Zielserver für die Datenbank verbinden.
*   Benutzer, die mit DEA hat Sysadmin-Rechte auf dem Zielserver für die Datenbank an.
*   Dienstkonto zur Ausführung der Zielserver für die Datenbank verfügt über Schreibzugriff auf den Ordnerpfad für die Ablaufverfolgung.
*   Dienstkonto zur Ausführung von Distributed Replay-Clients kann mithilfe der Windows-Authentifizierung auf dem Zielserver für die Datenbank verbinden.
*   DEA kommuniziert mit dem Distributed Replay-Controller über COM-Schnittstellen. Stellen Sie sicher, dass TCP-Ports für eingehende Anforderungen für den Distributed Replay Controller geöffnet werden.

Weitere Informationen finden Sie unter den [wiedergeben – häufig gestellte Fragen](database-experimentation-assistant-replay-trace.md#frequently-asked-questions-about-trace-replay)

**Anforderungen an die Analyse**: 

*   Benutzer, der ausführt DEA kann mithilfe der Windows-Authentifizierung an den Analysis-Server-Datenbank verbinden.
*   Benutzer, die mit DEA hat Sysadmin-Rechte auf dem Quellserver für die Datenbank an.

Weitere Informationen finden Sie unter den [Analyse – häufig gestellte Fragen](database-experimentation-assistant-create-report.md#frequently-asked-questions-about-analysis-reports)

## <a name="set-up-telemetry"></a>Einrichten der Telemetrie

DEA verfügt über eine Internet-fähigen-Funktion, die Telemetriedaten an Microsoft senden können. Microsoft erfasst Telemetriedaten, um das Produkt zu verbessern. Telemetrie ist optional. Die Informationen, die gesammelt werden, wird auch auf Ihrem Computer für die lokale Überwachung gespeichert. Sie können immer sehen, was gesammelt wird. Alle Protokolldateien aus DEA werden gespeichert, in der "% Temp%"\\DEA-Ordner.

Sie können entscheiden, welche Ereignisse gesammelt werden. Auch entscheiden Sie, ob die gesammelten Ereignisse an Microsoft gesendet werden. Es gibt vier Arten von Ereignissen:

*   **TraceEvent**: Verwendung-Ereignisse für die Anwendung (z. B. "Aufzeichnung ausgelösten beenden").
*   **Ausnahme**: Bei Anwendungsverwendung ausgelöste Ausnahme.
*   **DiagnosticEvent**: Ein Ereignisprotokoll zur Unterstützung bei der Diagnose, wenn Probleme auftreten (*nicht* an Microsoft gesendet).
*   **FeedbackEvent**: Benutzerfeedback, die durch die Anwendung übermittelt werden.

Diese Schritte zeigen, wie Sie auswählen, welche Ereignisse gesammelt werden und gibt an, ob die Ereignisse an Microsoft gesendet werden:

1.  Wechseln Sie zu dem Speicherort, in denen DEA installiert ist (z. B. "c:"\\Programmdateien (x86)\\Microsoft Corporation\\Database experimentieren Assistant).
2.  Öffnen Sie die beiden .config-Dateien: DEA.exe.config (für die Anwendung) und DEACmd.exe.config (für die Azure CLI).
3.  Um einen Typ von Ereignis erfassen zu beenden, legen Sie den Wert der *Ereignis* (z. B. **TraceEvent**) zu **"false"** . Um erfassen das Ereignis erneut zu starten, legen Sie den Wert auf **"true"** .
4.  Um lokale Kopien der Ereignisse zu beenden, legen Sie den Wert der **TraceLoggerEnabled** zu **"false"** . Um lokale Kopien Speichervorgang zu starten, legen Sie den Wert auf **"true"** .
5.  Zum Senden von Ereignissen an Microsoft zu beenden, legen Sie den Wert der **AppInsightsLoggerEnabled** zu **"false"** . Um für das Senden von Ereignissen an Microsoft ist es noch Mal zu starten, legen Sie den Wert auf **"true"** .

DEA unterliegt der [Microsoft Privacy Statement](https://aka.ms/dea-privacy).

## <a name="next-steps"></a>Nächste Schritte

[Erste Schritte](database-experimentation-assistant-get-started.md) führt Sie durch die erforderlichen Schritte zum Erfassen und wiedergeben eine Ablaufverfolgung analysieren.
