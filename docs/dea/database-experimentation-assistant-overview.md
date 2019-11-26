---
title: Übersicht über den Assistent für Datenbankexperimente
description: Übersicht über Assistent für Datenbankexperimente
ms.custom: seo-lt-2019
ms.date: 11/16/2019
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: jtoland
ms.reviewer: mathoma
ms.openlocfilehash: 79caf961208287e1482efe780d2d0e335bbdd16d
ms.sourcegitcommit: f018eb3caedabfcde553f9a5fc9c3e381c563f1a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2019
ms.locfileid: "74165550"
---
# <a name="overview-of-database-experimentation-assistant"></a>Übersicht über Assistent für Datenbankexperimente

Assistent für Datenbankexperimente (DEA) ist eine Experimentier Lösung für SQL Server Upgrades. Mithilfe von DEA können Sie eine Zielversion von SQL Server für eine bestimmte Arbeitsauslastung auswerten. Kunden, die ein Upgrade von früheren SQL Server Versionen (beginnend mit 2005) auf eine neuere Version von SQL Server durchführen können, können die analysemetriken verwenden, die das Tool bereitstellt.

Die Analyse Metriken von DEA umfassen:

- Abfragen mit Kompatibilitäts Fehlern
- Heruntergestufte Abfragen und Abfrage Pläne
- Weitere Vergleichsdaten für die Arbeitsauslastung

Vergleichsdaten können zu einem höheren Vertrauen und einem erfolgreichen Upgradevorgang führen.

## <a name="get-dea"></a>Erhalten von DEA

Zum Installieren von DEA [Laden Sie](https://www.microsoft.com/download/details.aspx?id=54090) die neueste Version des Tools herunter. Führen Sie dann die Datei **databaseexperimentationassistant. exe** aus.

## <a name="solution-architecture-for-comparing-workloads"></a>Lösungsarchitektur zum Vergleichen von Arbeits Auslastungen

Das folgende Diagramm zeigt die Lösungsarchitektur für einen workloadvergleich. Beim Vergleich der Arbeitsauslastung werden bei einem Upgrade von SQL Server 2008 auf SQL Server 2016 DEA und Distributed Replay verwendet.

![Lösungsarchitektur für workloadvergleich](./media/database-experimentation-assistant-overview/dea-overview-compare-solution-architecture.png)

## <a name="dea-prerequisites"></a>Erforderliche Komponenten für DEA

Es folgen einige Voraussetzungen für die Ausführung von DEA:

- Mindesthardwareanforderung: ein Single-Core-Computer mit 3,5 GB RAM.
- Ideale Hardware Anforderung: eine CPU mit 8 Kernen (mit mindestens 3,5 GB RAM). Prozessoren mit mehr als acht Kernen verbessern die DEA-Runtimes nicht.
- Zum Speichern der Datenbanken A, B und Report Analysis ist ein zusätzlicher Wert von 33% der Leistungs Ablauf Verfolgung erforderlich.

## <a name="configure-dea"></a>Konfigurieren von DEA

In der Architektur der Voraussetzungs Umgebung wird empfohlen, dass Sie *die ddea auf demselben Computer wie den Distributed Replay Controller*installieren. Durch diese Vorgehensweise werden Computer übergreifende Aufrufe vermieden und die Konfiguration vereinfacht.

### <a name="required-configuration-for-workload-comparison-using-dea"></a>Erforderliche Konfiguration für den workloadvergleich mithilfe von DEA

Mit der Windows-Authentifizierung stellt die DEA eine Verbindung mit Datenbankservern her Stellen Sie sicher, dass ein Benutzer, der DEA verwendet, mithilfe der Windows-Authentifizierung eine Verbindung mit Datenbankservern (Quelle, Ziel und Analyse) herstellen kann.

**Konfigurations Anforderungen erfassen**

Zum Aufzeichnen einer Ablauf Verfolgung ist Folgendes erforderlich:

- Der Benutzer, der DEA verwendet, kann mithilfe der Windows-Authentifizierung eine Verbindung mit dem Datenbankserver
- Der Benutzer, der "DEA" verwendet, hat Systemadministrator Rechte auf dem Quelldaten Bankserver.
- Das Dienst Konto, auf dem der Quelldaten Bankserver ausgeführt wird, verfügt über Schreibzugriff auf den Pfad des Verzeichnis

Weitere Informationen finden Sie unter [häufig gestellte Fragen zur Erfassung von](database-experimentation-assistant-capture-trace.md#frequently-asked-questions-about-trace-capture) Ablauf Verfolgungen.

**Anforderungen an die Wiedergabe Konfiguration**

Die Wiedergabe einer Ablauf Verfolgung erfordert Folgendes:

- Der Benutzer, der DEA verwendet, kann mithilfe der Windows-Authentifizierung eine Verbindung zum Ziel Datenbankserver
- Der Benutzer, der "DEA" verwendet, hat Systemadministrator Rechte auf dem Ziel Datenbankserver.
- Das Dienst Konto, auf dem die Ziel Datenbankserver ausgeführt werden, verfügt über Schreibzugriff auf den Pfad des Verzeichnis
- Das Dienst Konto, das Distributed Replay Clients ausgeführt wird, kann mithilfe der Windows-Authentifizierung eine Verbindung zum Ziel Datenbankserver
- TCP-Ports werden für eingehende Anforderungen auf dem Distributed Replay Controller geöffnet. Die Verwendung von "DEA" erfolgt über COM-Schnittstellen mit dem Distributed Replay Controller

Weitere Informationen finden Sie unter [häufig gestellte Fragen zur Wiedergabe](database-experimentation-assistant-replay-trace.md#frequently-asked-questions-about-trace-replay) der Ablauf Verfolgung.

**Anforderungen an die Analyse Konfiguration**

Zum Durchführen der Analyse ist Folgendes erforderlich:

- Der Benutzer, der "DEA" verwendet, kann mithilfe der Windows-Authentifizierung eine Verbindung mit dem Analysis
- Der Benutzer, der "DEA" verwendet, hat Systemadministrator Rechte auf dem Quelldaten Bankserver.

Weitere Informationen finden Sie unter [häufig gestellte Fragen zu Analyseberichten](database-experimentation-assistant-create-report.md#frequently-asked-questions-about-analysis-reports) .

## <a name="set-up-telemetry"></a>Einrichten von Telemetrie

Die Funktion "DEA" verfügt über ein internetfähiges Feature, mit dem Telemetriedaten an Microsoft gesendet werden können, um die Produktleistung zu verbessern. Die gesammelten Informationen werden auch auf Ihrem Computer für die lokale Überwachung gespeichert, sodass Sie immer sehen können, was erfasst wurde. Alle DEA-Protokolldateien werden im Ordner "% Temp%\\DEA" gespeichert.

Telemetriedaten können für vier Arten von Ereignissen erfasst werden:

- **TraceEvent**: Verwendungs Ereignisse für die Anwendung (z. b. "Auslösen der Erfassungs Erfassung").
- **Ausnahme**: Ausnahme bei der Anwendungs Verwendung.
- **Diagnosticevent**: ein Ereignisprotokoll zur Unterstützung der Diagnose, wenn Probleme auftreten (*nicht* an Microsoft gesendet).
- **Feedbackevent**: Benutzer Feedback, das über die Anwendung übermittelt wird.

Das erfassen und Senden von Telemetriedaten ist optional. Führen Sie die folgenden Schritte aus, um anzugeben, welche Ereignisse gesammelt werden und ob gesammelte Ereignisse an Microsoft gesendet werden:

1. Wechseln Sie zu dem Speicherort, an dem die DEA installiert ist (z. b. C:\\-Programmdateien (x86)\\Microsoft Corporation\\Assistent für Datenbankexperimente).
2. Öffnen und ändern Sie die config-Dateien " **Dea. exe. config** " (für die Anwendung) und " **deacmd. exe. config** " (für die CLI), um Ihr Szenario entsprechend zu beheben:
    - Legen Sie den Wert des *Ereignisses* (z. b. **TraceEvent**) auf **false**fest, um die Erfassung eines Ereignis Typs zu verhindern. Legen Sie den Wert auf " **true**" fest, um die erneute Erfassung des Ereignisses zu beginnen.
    - Legen Sie den Wert von **traceloggerfähig** auf **false**fest, um das Speichern von lokalen Kopien von Ereignissen zu verhindern. Legen Sie den Wert auf **true**fest, damit die lokalen Kopien erneut gespeichert werden.
    - Um das Senden von Ereignissen an Microsoft zu verhindern, legen Sie den Wert von **appinsightloggeraktiviauf** **false**fest. Legen Sie den Wert auf " **true**" fest, um erneut Ereignisse an Microsoft zu senden.

Die [Microsoft-Datenschutzbestimmungen unterliegen der Microsoft-Datenschutzerklärung](https://aka.ms/dea-privacy)

## <a name="see-also"></a>Siehe auch

[Übersicht über den Arbeits](database-experimentation-assistant-get-started.md)Auslastungs Vergleichsprozess, der den Prozess zum Vergleichen von Arbeits Auslastungen in zwei Umgebungen erläutert.
