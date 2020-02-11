---
title: Übersicht über den Arbeits Auslastungs Vergleichsprozess
description: Assistent für Datenbankexperimente (DEA) ist eine A/B-Testlösung für Änderungen in SQL Server Umgebungen, z. B. Upgrades oder neue Indizes.
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
ms.custom: seo-lt-2019
ms.openlocfilehash: 36e36060e16ff85ba2b1fa58d9d900231cf6581f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "75258525"
---
# <a name="overview-of-the-workload-comparison-process"></a>Übersicht über den Arbeits Auslastungs Vergleichsprozess

Mit Assistent für Datenbankexperimente (DEA) können Sie bewerten, wie die Arbeitsauslastung auf dem Quell Server (in Ihrer aktuellen Umgebung) in der neuen Umgebung durchgeführt wird. In der folgenden Anleitung werden Sie durch die Ausführung eines A/B-Tests geführt.

- Erfassen einer Arbeits Auslastungs Ablauf Verfolgung auf dem Quell Server.
- Wiedergeben der aufgezeichneten workloadverfolgung auf Ziel 1 und Ziel 2.
- Analysieren der wiedergegebenen workloadüberwachungen, die von Ziel 1 und Ziel 2 erfasst wurden.

Dieser Artikel bietet eine Übersicht über diesen Prozess.

## <a name="capturing-a-workload-trace"></a>Erfassen einer workloadverfolgung

Die erste Phase SQL Server a/B-Tests besteht darin, eine Ablauf Verfolgung auf dem Quell Server zu erfassen. Der Quellserver ist normalerweise der Produktionsserver. Ablauf Verfolgungs Dateien erfassen die gesamte Arbeitsauslastung der Abfrage auf diesem Server, einschließlich Zeitstempel.

Überlegungen:

- Bevor Sie beginnen, müssen Sie sicherstellen, dass Sie die Datenbanken sichern, von denen Sie die Ablauf Verfolgung erfassen.
- Der DEA-Benutzer muss in der Lage sein, mithilfe der Windows-Authentifizierung eine Verbindung mit der Datenbank herzustellen.
- Ein SQL Server-Dienst Konto muss auf den Pfad der Quelldatei für die Ablauf Verfolgung zugreifen können.
- Damit von DEA bestimmt wird, ob die Leistung einer Abfrage verbessert oder beeinträchtigt wird, muss diese Abfrage mindestens 15 Mal während des Erfassungs Zeitraums ausgeführt werden.

## <a name="replaying-a-workload-trace"></a>Wiedergeben einer workloadverfolgung

Die zweite Phase SQL Server A/B-Tests ist die Wiedergabe der Ablauf Verfolgungs Datei, die Sie auf zwei Ziel Servern aufgezeichnet haben:

Ziel 1, das das Quell Server Ziel 2 imitiert, das Ihre vorgeschlagene Zielumgebung imitiert.

Die Hardware Konfigurationen von Ziel 1 und Ziel 2 sollten so ähnlich wie möglich sein, damit SQL Server die Leistungs Auswirkung ihrer vorgeschlagenen Änderungen genau analysieren kann.

Überlegungen:

- Um eine Ablauf Verfolgungs Ablauf Verfolgung wiederzugeben, müssen die Computer so eingerichtet werden, dass Sie Distributed Replay (dreplay)-Ablauf Verfolgungen ausführen.
- Stellen Sie sicher, dass Sie die Datenbanken auf ihren Ziel Servern wiederherstellen, indem Sie die Sicherung vom Quell Server verwenden.
- Es wird empfohlen, den SQL Server-Dienst (MSSQLSERVER) in der Dienste-Anwendung neu zu starten, um die Konsistenz der Bewertungsergebnisse zu verbessern. Das Zwischenspeichern von Abfragen in SQL Server kann die Auswertungs Ergebnisse beeinflussen.

## <a name="analyzing-the-replayed-workload-traces"></a>Analysieren der wiedergegebenen workloadüberwachungen

Die letzte Phase des Prozesses besteht darin, einen Analysebericht mithilfe der Wiedergabe Ablauf Verfolgungen zu generieren und den Bericht zu überprüfen, um Einblicke in die potenziellen Auswirkungen der vorgeschlagenen Änderung auf die Leistung zu erhalten.

Überlegungen:

- Wenn eine oder mehrere Komponenten fehlen, wird eine Seite mit Links zu Downloads angezeigt, die angezeigt wird, wenn Sie versuchen, einen neuen Analysebericht zu generieren (Internet Verbindung erforderlich).
- Um einen Bericht anzuzeigen, der in einer früheren Version des Tools generiert wurde, müssen Sie zuerst das Schema aktualisieren.

## <a name="see-also"></a>Weitere Informationen

- Informationen zum Erstellen einer Ablauf Verfolgungs Datei mit einem Protokoll von Ereignissen, die auf einem Server auftreten, finden Sie im Artikel aufzeichnen [einer Ablauf Verfolgung in Assistent für Datenbankexperimente](database-experimentation-assistant-capture-trace.md).