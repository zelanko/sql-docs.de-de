---
title: Übersicht über den Arbeits Auslastungs Vergleichsprozess
description: Assistent für Datenbankexperimente (DEA) ist eine A/B-Testlösung für Änderungen in SQL Server Umgebungen, z. B. Upgrades oder neue Indizes.
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
ms.custom: seo-lt-2019
ms.openlocfilehash: 18cba7abf0d73197c248a62283d52126873169a3
ms.sourcegitcommit: f018eb3caedabfcde553f9a5fc9c3e381c563f1a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2019
ms.locfileid: "74165749"
---
# <a name="overview-of-the-workload-comparison-process"></a>Übersicht über den Arbeits Auslastungs Vergleichsprozess

Mit Assistent für Datenbankexperimente (DEA) können Sie bewerten, wie die Arbeitsauslastung auf dem Quell Server (in Ihrer aktuellen Umgebung) in der neuen Umgebung durchgeführt wird. In der folgenden Anleitung werden Sie durch die Ausführung eines A/B-Tests geführt.

- Erfassen einer Arbeits Auslastungs Ablauf Verfolgung auf dem Quell Server.
- Wiedergeben der aufgezeichneten workloadverfolgung auf Ziel 1 und Ziel 2.
- Analysieren der wiedergegebenen workloadüberwachungen, die von Ziel 1 und Ziel 2 erfasst wurden.

Dieser Artikel bietet eine Übersicht über diesen Prozess.

## <a name="capturing-a-workload-trace"></a>Erfassen einer workloadverfolgung

Die erste Phase SQL Server a/B-Tests besteht darin, eine Ablauf Verfolgung auf dem Quell Server zu erfassen. Der Quell Server ist normalerweise der Produktionsserver. Ablauf Verfolgungs Dateien erfassen die gesamte Arbeitsauslastung der Abfrage auf diesem Server, einschließlich Zeitstempel.

Weitere Überlegungen:

- Stellen Sie sicher, dass Sie die Datenbanken sichern, von denen Sie die Ablauf Verfolgung erfassen, bevor Sie mit dem Erfassen der workloadverfolgung beginnen.
- Ein DEA-Benutzer muss konfiguriert werden, um mithilfe der Windows-Authentifizierung eine Verbindung mit der Datenbank herzustellen.
- Ein SQL Server-Dienst Konto erfordert Zugriff auf den Pfad der Quelldatei für die Ablauf Verfolgungs Datei.
- Damit von DEA bestimmt wird, ob die Leistung einer Abfrage verbessert oder beeinträchtigt wird, muss diese Abfrage mindestens 15 Mal während des Erfassungs Zeitraums ausgeführt werden.

## <a name="replaying-a-workload-trace"></a>Wiedergeben einer workloadverfolgung

Die zweite Phase SQL Server A/B-Tests ist die Wiedergabe der Ablauf Verfolgungs Datei, die Sie auf zwei Ziel Servern aufgezeichnet haben:

Ziel 1, das das Quell Server Ziel 2 imitiert, das Ihre vorgeschlagene Zielumgebung imitiert.

Die Hardware Konfigurationen von Ziel 1 und Ziel 2 sollten so ähnlich wie möglich sein, damit SQL Server die Leistungs Auswirkung ihrer vorgeschlagenen Änderungen genau analysieren kann.

Weitere Überlegungen:

- Um eine Ablauf Verfolgungs Ablauf Verfolgung wiederzugeben, müssen die Computer so eingerichtet werden, dass Sie Distributed Replay (dreplay)-Ablauf Verfolgungen ausführen.
- Stellen Sie sicher, dass Sie die Datenbanken auf ihren Ziel Servern wiederherstellen, indem Sie die Sicherung vom Quell Server verwenden.
- Es wird empfohlen, den SQL Server-Dienst (MSSQLSERVER) in der Dienste-Anwendung neu zu starten, um die Konsistenz der Bewertungsergebnisse zu verbessern. Das Zwischenspeichern von Abfragen in SQL Server kann die Auswertungs Ergebnisse beeinflussen.

## <a name="analyzing-the-replayed-workload-traces"></a>Analysieren der wiedergegebenen workloadüberwachungen

Die letzte Phase des Prozesses besteht darin, einen Analysebericht mithilfe der Wiedergabe Ablauf Verfolgungen zu generieren. Anschließend können Sie den Analysebericht überprüfen, um Einblicke in die potenziellen Auswirkungen auf die Leistung der vorgeschlagenen Änderung zu erhalten.

Weitere Überlegungen:

- Wenn eine oder mehrere Komponenten fehlen, wird eine Seite mit Links zu Downloads angezeigt, die angezeigt wird, wenn Sie versuchen, einen neuen Analysebericht zu generieren (Internetverbindung erforderlich).
- Um einen Bericht anzuzeigen, der in einer früheren Version des Tools generiert wurde, müssen Sie zuerst das Schema aktualisieren.

## <a name="see-also"></a>Siehe auch

- Informationen zum Erstellen einer Ablauf Verfolgungs Datei mit einem Protokoll von Ereignissen, die auf einem Server auftreten, finden Sie unter [Capture Trace](database-experimentation-assistant-capture-trace.md).
