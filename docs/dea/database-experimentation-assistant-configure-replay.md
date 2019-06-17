---
title: Konfigurieren von Replay im Datenbank-experimentieren-Assistenten für SQL Server-upgrades
description: Konfigurieren von Replay im Datenbank-experimentieren-Assistenten
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
ms.openlocfilehash: 8efef6f081395265f641197058b7920162cdde46
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66794484"
---
# <a name="configure-replay-in-database-experimentation-assistant"></a>Konfigurieren von Replay im Datenbank-experimentieren-Assistenten

Datenbank experimentieren-Assistenten (DEA) verwendet die Distributed Replay-Tools von SQL Server-Installation, um eine aufgezeichnete Ablaufverfolgung in einer aktualisierten testumgebung wiedergeben. Es wird empfohlen, einen Test ausführen, indem eine kleine Ablaufverfolgungsdatei davor eine vollständige Wiedergabe verwenden, um sicherzustellen, dass richtige Wiedergabe von Abfragen.

## <a name="distributed-replay-requirements"></a>Distributed Replay: Anforderungen

- 78 % zusätzlichen Festplatten-Speicherplatz ist erforderlich, um IRF Dateien auf dem Distributed Replay Controller-Computer zu erstellen.
- 200 MB oder 512 MB ist die ideale Ablaufverfolgung Rollover Größe zum Erfassen von ablaufverfolgungen für Produktions- oder Leistung.   
- Die Mindestanforderungen an die CPU- und Arbeitsspeicherressourcen für die Distributed Replay Controller und Client-Computer sind eine Single-Core-CPU mit 3,5 GB RAM.
- Die Wiedergabezeit dauert ca. 1,55 Mal länger als Zeitpunkt der Aufzeichnung da einen Controller und vier untergeordnete Computer verwendet werden, die Ablaufverfolgung für die Produktion wiedergegeben.
- Bei Verwendung unserer "veröffentlichten" Versionen der Produktions- und Definitionsdateien für Leistung und die Leistung Ablaufverfolgung Definition filtert die ablaufverfolgungen für eine Datenbank von Interesse Analyse zeigt, dass die **Leistung Ablaufverfolgung** beträgt 15-Mal größer als die **Produktion Ablaufverfolgung** Größe.

## <a name="set-up-a-virtual-network-or-domain"></a>Richten Sie ein virtuelles Netzwerk oder Domäne

Distributed Replay müssen Sie die allgemeine Konten zwischen Computern zu verwenden. Aufgrund dieser Anforderung, und aus Sicherheitsgründen wird empfohlen, Ausführen der Distributed Replay in einem virtuellen Netzwerk oder in einem Netzwerk Domäne gesteuert:

- Erstellen Sie die Controller- und Clientdienste Computer in der Umgebung.
- Stellen Sie sicher, dass die Controller- und Clientdienste Computer miteinander über das Netzwerk pingen können.
- Distributed Replay Client-Computer müssen mit dem Replay-Zielcomputer mit SQL Server verbunden.

## <a name="set-up-the-controller-service"></a>Richten Sie den Controller-Dienst

So richten den Controller-Dienst:

1. Installieren Sie die Distributed Replay-Controller mithilfe von SQL Server-Installationsprogramm. Wenn Sie den SQL Server-Installationsprogramm Schritt des Assistenten übersprungen, der den Distributed Replay-Controller konfiguriert haben, können Sie den Controller über die Konfigurationsdatei konfigurieren. In einer Standardinstallation befindet sich die Konfigurationsdatei unter C:\Program Files (x86) \Microsoft SQL Server\<Version\>\Tools\DReplayController\DReplayController.config.
1. Distributed Replay Controller-Protokolle befinden sich unter C:\Program Files (x86) \Microsoft SQL Server\<Version\>\Tools\DReplayController\Log.
1. Öffnen Sie "Services.msc", und fahren Sie mit der **SQL Server Distributed Replay Controller** Service.
1. Mit der rechten Maustaste auf den Dienst, und wählen Sie dann **Eigenschaften**. Festlegen des Dienstkontos mit einem Konto an, die für die Controller- und Clientdienste Computer im Netzwerk ist.
1. Wählen Sie **OK** schließen die **Eigenschaften** Fenster.
1. Neustart der **SQL Server Distributed Replay Controller** Dienst über "Services.msc". Sie können auch die folgenden Befehle in der Befehlszeile zum Neustart des Diensts ausführen:<br/>
   `NET STOP "SQL Server Distributed Replay Controller"`<br/>
   `NET START "SQL Server Distributed Replay Controller"`
1. Weitere Konfigurationsoptionen finden Sie unter [Konfigurieren von Distributed Replay](https://docs.microsoft.com/sql/tools/distributed-replay/configure-distributed-replay).

## <a name="configure-dcom"></a>Konfigurieren von DCOM

Diese Konfiguration ist nur auf dem Controllercomputer erforderlich.

1. Öffnen Sie dcomcnfg.exe ein.
1. Erweitern Sie **Komponentendienste** > **Computer** > **Arbeitsplatz** > **DCOM-Konfiguration**.
1. Klicken Sie unter **DCOM-Konfiguration**, mit der rechten Maustaste **DReplayController**, und wählen Sie dann **Eigenschaften**.
1. Wählen Sie die Registerkarte **Sicherheit** .
1. Klicken Sie unter **Start- und Aktivierungsberechtigungen**Option **anpassen**, und wählen Sie dann **bearbeiten**.
1. Hinzufügen des Benutzers, der die Wiedergabe gestartet wird. Erteilen Sie dem Benutzer die Berechtigungen lokaler Start "und" Lokale Aktivierung. Wenn der Benutzer plant, starten oder Remote aktivieren, können Sie Benutzer die Berechtigungen "Remotestart" und "Remoteaktivierung.
1. Wählen Sie **OK** committen der Änderungen und zum Zurückgeben der **Sicherheit** Registerkarte.
1. Klicken Sie unter **Zugriffsberechtigungen**Option **anpassen**, und wählen Sie dann **bearbeiten**.
1. Hinzufügen des Benutzers, der die Wiedergabe gestartet wird. Weisen Sie dem Benutzer Berechtigungen für den Lokalzugriff. Wenn der Benutzer plant, die Remotezugriff auf des Controller-Diensts, können Sie Benutzer RAS-Berechtigungen.
1. Wählen Sie **OK** committen der Änderungen und zum Zurückgeben der **Sicherheit** Registerkarte.
1. Wählen Sie **OK** um die Änderungen zu übernehmen.
1. Starten Sie den SQL Server Distributed Replay Controller-Dienst über "Services.msc" ein. Sie können auch die folgenden Befehle in der Befehlszeile zum Neustart des Diensts ausführen:<br/>
   `NET STOP "SQL Server Distributed Replay Controller"`<br/>
   `NET START "SQL Server Distributed Replay Controller"`

## <a name="set-up-the-client-service"></a>Richten Sie den Client-Dienst

Bevor Sie den Client-Dienst einrichten, verwenden Sie Netzwerke Tools wie Ping, stellen Sie sicher, dass die Controller und Client-Computer kommunizieren können.

1. Installieren Sie den Distributed Replay Client mithilfe von SQL Server-Installationsprogramm.
1. Öffnen Sie "Services.msc" aus, und wechseln Sie zu der SQL Server Distributed Replay Client-Dienst.
1. Mit der rechten Maustaste auf den Dienst, und wählen Sie dann **Eigenschaften**. Festlegen des Dienstkontos mit einem Konto an, die für den Controller und Client-Computer im Netzwerk ist.
1. Wählen Sie **OK** schließen die **Eigenschaften** Fenster. Wenn Sie die SQL Server-Installationsprogramm Assistentenschritt zum Konfigurieren des Distributed Replay Clients übersprungen haben, können Sie es über die Konfigurationsdatei konfigurieren. In einer Standardinstallation befindet sich die Konfigurationsdatei unter C:\Program Files (x86) \Microsoft SQL Server\<Version\>\Tools\DReplayClient\DReplayClient.config.
1. Stellen Sie sicher, dass die DReplayClient.config-Datei den Namen des Computers mit dem Domänencontroller als der Controller für die Registrierung enthält.
1.  Starten Sie den SQL Server Distributed Replay Client-Dienst über "Services.msc" ein. Sie können auch über die Befehlszeile zum Neustart des Diensts die folgenden Befehle ausführen:<br/>
    `NET STOP "SQL Server Distributed Replay Client"`<br/>
    `NET START "SQL Server Distributed Replay Client"`
1. Distributed Replay Controller-Protokolle befinden sich unter C:\Program Files (x86) \Microsoft SQL Server\<Version\>\Tools\DReplayClient\Log. Die Protokolle zeigen an, ob der Client mit dem Controller registriert werden kann.
1. Wenn die Konfiguration erfolgreich ist, zeigt das Protokoll die Meldung "mit dem Controller registriert < Name des Domänencontrollers\>".
1. Weitere Konfigurationsoptionen finden Sie unter [Konfigurieren von Distributed Replay](https://docs.microsoft.com/sql/tools/distributed-replay/configure-distributed-replay).

## <a name="set-up-distributed-replay-administration-tools"></a>Richten Sie Distributed Replay-Verwaltungstools

Sie können Distributed Replay-Verwaltungstools verwenden, schnell testen, ob die Distributed Replay in der Umgebung ordnungsgemäß funktioniert. Testen der Konfiguration, ist besonders hilfreich, in einer Umgebung, in denen mehrere Clientcomputer mit einem Controller registriert sind. Sie müssen möglicherweise SQL Server Management Studio (SSMS), rufen Sie die Verwaltungstools installieren.

1. Wechseln Sie in der SSMS-Installationsspeicherort aus, und suchen Sie nach der Distributed Replay Administration Tool dreplay.exe und ihrer abhängigen Komponenten.
1. Öffnen Sie ein Eingabeaufforderungsfenster, und führen `dreplay.exe status -f 1`.
1. Wenn alle vorherigen Schritte erfolgreich sind, gibt die Ausgabe der Konsole an, der Controller sehen kann, die Clients auf einem `READY` Zustand.

## <a name="configure-the-firewall-for-remote-distributed-replay-access"></a>Konfigurieren der Firewall für den Distributed Replay-Remotezugriff

Remotezugriff auf Distributed Replay erfordert das Öffnen von Ports, die innerhalb der Domäne oder dem virtuellen Netzwerk sichtbar sind.

1. Open **Windows-Firewall** mit **erweiterte Sicherheit**.
1. Wechseln Sie zu **Eingangsregeln**.
1. Erstellen Sie eine neue eingehende Firewallregel für Programm C:\Program Files (x86) \Microsoft SQL Server\<Version\>\Tools\DReplayController\DReplayController.exe.
1. Zugriff auf Domänenebene für alle Ports für DReplayController.exe Remote mit dem Controllerdienst kommunizieren können.
1. Speichern Sie die Regel an.

## <a name="set-up-target-computers"></a>Einrichten der Ziel-PCs

Zwei Wiedergaben sind erforderlich, um das Ausführen eines A / B-Tests oder ein Experiment. Das heißt, benötigen Sie möglicherweise zwei separate Instanzen von SQL Server-Installationen für ein Migrationsszenario. 

Sie können auch die beiden Versionen von SQL Server-Instanzen auf demselben Computer installieren. Ein Nachteil ist, um sicherzustellen, dass die Instanzen vollständig isoliert sind, wenn eine Wiedergabe ausgeführt wird.

Die folgenden Schritte müssen für die einzelnen Wiedergabe ausgeführt werden:

1. Stellen Sie die Sicherung der Datenbank.
1. Erteilen Sie Berechtigungen für die Benutzer Zugriff auf die Datenbanken unter SQL Server-Instanz für den Client des Dienstkontos. Berechtigungen sind erforderlich, für die Abfragen für SQL Server-Instanz ausgeführt werden.
1. Starten der Wiedergabe.

## <a name="next-steps"></a>Nächste Schritte

- Um zu erfahren, wie Sie eine aufgezeichnete Ablaufverfolgung in einer aktualisierten testumgebung wiedergeben, finden Sie unter [Wiedergabe der Ablaufverfolgung](database-experimentation-assistant-replay-trace.md).

- Für einen 19-minütige Einführung in DEA und Demonstrationen im folgenden Video:

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
