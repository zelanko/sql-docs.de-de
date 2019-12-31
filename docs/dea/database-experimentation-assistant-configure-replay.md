---
title: Wiedergabe für SQL Server Upgrades konfigurieren
description: Konfigurieren von Distributed Replay für Assistent für Datenbankexperimente
ms.custom: seo-lt-2019
ms.date: 11/21/2019
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: jtoland
ms.reviewer: mathoma
ms.openlocfilehash: 2ef570f531bcd37a2a5f7be1f3a900c4b8a4c112
ms.sourcegitcommit: 9e026cfd9f2300f106af929d88a9b43301f5edc2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74317729"
---
# <a name="configure-distributed-replay-for-database-experimentation-assistant"></a>Konfigurieren von Distributed Replay für Assistent für Datenbankexperimente

Assistent für Datenbankexperimente (DEA) verwendet die Distributed Replay Tools aus der SQL Server-Installation, um eine aufgezeichnete Ablauf Verfolgung in einer aktualisierten Testumgebung wiederzugeben. Es wird empfohlen, einen Testlauf mithilfe einer kleinen Ablauf Verfolgungs Datei auszuführen, bevor Sie eine vollständige Wiedergabe ausführen

## <a name="distributed-replay-requirements"></a>Distributed Replay Anforderungen

- Zum Erstellen von auf dem Distributed Replay Controller-Computer sind zusätzliche 78% des Festplatten Speicherplatzes erforderlich.
- 200 MB oder 512 MB ist die ideale ablaufverfolgungsrollovergröße zum Erfassen von Produktions-oder Leistungs Ablauf Verfolgungen.
- Die Mindestanforderungen an die CPU-und RAM-Anforderungen für die Distributed Replay Controller-und Client Computer sind eine Einzel Kern-CPU mit 3,5 GB RAM.
- Die Wiedergabezeit dauert ungefähr 1,55 mal länger als die Erfassungs Zeit, da ein Controller und vier untergeordnete Computer verwendet werden, um die Produktionsablauf Verfolgung wiederzugeben.
- Wenn Sie unsere "veröffentlichten" Versionen der Definitions Dateien für die Produktions-und Leistungsüberwachung verwenden und die Leistungs Ablauf Verfolgungs Definition die Ablauf Verfolgungen für eine relevante Datenbank herausfiltert, zeigt die Analyse, dass die **Leistung der Leistungs** Ablauf Verfolgung ungefähr 15 Mal größer ist als die Größe der **Produktions** Ablauf Verfolgung.

## <a name="set-up-a-virtual-network-or-domain"></a>Einrichten eines virtuellen Netzwerks oder einer Domäne

Distributed Replay erfordert, dass Sie gemeinsame Konten zwischen Computern verwenden. Aufgrund dieser Anforderung und aus Sicherheitsgründen wird empfohlen, Distributed Replay in einem virtuellen Netzwerk oder in einem domänengesteuerten Netzwerk zu ausführen:

- Erstellen Sie den Controller und die Client Computer in der Umgebung.
- Stellen Sie sicher, dass die Controller-und Client Computer sich gegenseitig über das Netzwerk pingen können.
- Distributed Replay-Client Computern muss eine Verbindung mit dem Wiedergabe Zielcomputer bestehen, auf dem SQL Server ausgeführt wird.

## <a name="set-up-the-controller-service"></a>Einrichten des Controller Dienstanbieter

So richten Sie den Controller Dienst ein:

1. Installieren Sie den Distributed Replay Controller, indem Sie den SQL Server Installer verwenden. Wenn Sie den Schritt SQL Server Installer-Assistent übersprungen haben, mit dem der Distributed Replay Controller konfiguriert wird, können Sie den Controller über die Konfigurationsdatei konfigurieren. Bei einer typischen Installation befindet sich die Konfigurationsdatei unter "c:\Programme (x86) \Microsoft SQL Server\<Version\>\tools\dreplaycontroller\dreplaycontroller.config".
2. Distributed Replay Controller Protokolle befinden sich unter c:\Programme (x86) \Microsoft SQL Server\<Version\>\tools\dreplaycontroller\log.
3. Öffnen Sie "Services. msc", und wechseln Sie zum **SQL Server Distributed Replay Controller** -Dienst.
4. Klicken Sie mit der rechten Maustaste auf den Dienst, und wählen Sie dann **Eigenschaften**aus. Legen Sie das Dienst Konto auf ein Konto fest, das dem Controller und den Client Computern im Netzwerk gemeinsam ist.
5. Wählen Sie **OK** aus, um das **Eigenschaften** Fenster zu schließen.
6. Starten Sie den **SQL Server Distributed Replay Controller** -Dienst über "Services. msc" neu. Sie können auch die folgenden Befehle in der Befehlszeile ausführen, um den Dienst neu zu starten:<br/>
   `NET STOP "SQL Server Distributed Replay Controller"`<br/>
   `NET START "SQL Server Distributed Replay Controller"`
7. Weitere Konfigurationsoptionen finden Sie unter [Konfigurieren von Distributed Replay](https://docs.microsoft.com/sql/tools/distributed-replay/configure-distributed-replay).

## <a name="configure-dcom"></a>Konfigurieren von DCOM

Diese Konfiguration ist nur auf dem Controller Computer erforderlich.

1. Öffnen Sie DCOMCNFG. exe.
2. Erweitern Sie **Komponenten Dienste** > **Computer** > **Arbeitsplatz** > **DCOM-Konfiguration**.
3. Klicken Sie unter **DCOM-Konfiguration**mit der rechten Maustaste auf **dreplaycontroller**, und wählen Sie dann **Eigenschaften**aus.
4. Wählen Sie die Registerkarte **Sicherheit** aus.
5. Wählen Sie unter **Start-und Aktivierungs Berechtigungen**die Option **Anpassen**aus, und klicken Sie dann auf **Bearbeiten**.
6. Fügen Sie den Benutzer hinzu, der die Wiedergabe startet. Hiermit werden dem Benutzer lokale Start-und lokale Aktivierungs Berechtigungen erteilt. Wenn der Benutzer plant, Remote zu starten oder zu aktivieren, müssen Sie den Benutzern die Berechtigungen Remote Start und Remote Aktivierung erteilt haben.
7. Wählen Sie **OK** aus, um die Änderungen zu übertragen und zur Registerkarte **Sicherheit** zurückzukehren.
8. Wählen Sie unter **Zugriffsberechtigungen**die Option **Anpassen**aus, und klicken Sie dann auf **Bearbeiten**.
9. Fügen Sie den Benutzer hinzu, der die Wiedergabe startet. Erteilt dem Benutzer lokale Zugriffsberechtigungen. Wenn der Benutzer einen Remote Zugriff auf den Controller Dienst plant, sollten Sie dem Benutzer Remote Zugriffsberechtigungen einräumen.
10. Wählen Sie **OK** aus, um die Änderungen zu übertragen und zur Registerkarte **Sicherheit** zurückzukehren.
11. Wählen Sie **OK** aus, um die Änderungen zu übertragen.
12. Starten Sie den SQL Server Distributed Replay Controller-Dienst über "Services. msc" neu. Sie können auch die folgenden Befehle in der Befehlszeile ausführen, um den Dienst neu zu starten:<br/>
   `NET STOP "SQL Server Distributed Replay Controller"`<br/>
   `NET START "SQL Server Distributed Replay Controller"`

## <a name="set-up-the-client-service"></a>Einrichten des Client Dienstanbieter

Verwenden Sie vor dem Einrichten des-Client Dienstanbieter Netzwerk Tools wie Ping, um zu überprüfen, ob die Controller-und Client Computer kommunizieren können.

1. Installieren Sie den Distributed Replay Client, indem Sie den SQL Server Installer verwenden.
2. Öffnen Sie "Services. msc", und wechseln Sie zum SQL Server Distributed Replay-Client Dienst.
3. Klicken Sie mit der rechten Maustaste auf den Dienst, und wählen Sie dann **Eigenschaften**aus. Legen Sie das Dienst Konto auf ein Konto fest, das sowohl dem Controller als auch den Client Computern im Netzwerk gemeinsam ist.
4. Wählen Sie **OK** aus, um das **Eigenschaften** Fenster zu schließen. Wenn Sie den Schritt SQL Server Installer-Assistent übersprungen haben, um den Distributed Replay-Client zu konfigurieren, können Sie ihn über die Konfigurationsdatei konfigurieren. Bei einer typischen Installation befindet sich die Konfigurationsdatei unter "c:\Programme (x86) \Microsoft SQL Server\<Version\>\tools\dreplayclient\dreplayclient.config".
5. Stellen Sie sicher, dass die Datei dreplayclient. config den Namen des Controller Computers als Controller für die Registrierung enthält.
6. Starten Sie den SQL Server Distributed Replay-Client Dienst über "Services. msc" neu. Sie können auch die folgenden Befehle in der Befehlszeile ausführen, um den Dienst neu zu starten:<br/>
    `NET STOP "SQL Server Distributed Replay Client"`<br/>
    `NET START "SQL Server Distributed Replay Client"`
7. Distributed Replay Controller Protokolle befinden sich unter "c:\Programme (x86) \Microsoft SQL Server\<Version\>\tools\dreplayclient\log". Die Protokolle geben an, ob sich der Client selbst beim Controller registrieren kann.
8. Wenn die Konfiguration erfolgreich ist, wird im Protokoll die Meldung "bei Controller <Controller Name\>registriert" angezeigt.
9. Weitere Konfigurationsoptionen finden Sie unter [Konfigurieren von Distributed Replay](https://docs.microsoft.com/sql/tools/distributed-replay/configure-distributed-replay).

## <a name="set-up-distributed-replay-administration-tools"></a>Einrichten Distributed Replay Verwaltungs Tools

Mit Distributed Replay-Verwaltungs Tools können Sie schnell überprüfen, ob Distributed Replay in der Umgebung ordnungsgemäß funktioniert. Das Testen der Konfiguration kann insbesondere in einer Umgebung hilfreich sein, in der mehrere Client Computer bei einem Controller registriert sind. Möglicherweise müssen Sie SQL Server Management Studio (SSMS) installieren, um die Verwaltungs Tools zu erhalten.

1. Wechseln Sie zum Speicherort der SSMS-Installation, und suchen Sie nach dem Distributed Replay Verwaltungs Tool dreplay. exe und seinen abhängigen Komponenten.
2. Führen `dreplay.exe status -f 1`Sie an einer Eingabeaufforderung aus.

Wenn die vorangehenden Schritte erfolgreich ausgeführt wurden, gibt die Konsolenausgabe an, dass der Controller seine Clients `READY` in einem Zustand sehen kann.

## <a name="configure-the-firewall-for-remote-distributed-replay-access"></a>Konfigurieren der Firewall für den Remote Distributed Replay Zugriff

Für den Remote Zugriff auf Distributed Replay müssen Ports geöffnet werden, die innerhalb der Domäne oder des virtuellen Netzwerks sichtbar sind.

1. Öffnen Sie **Windows-Firewall** mit erweiterter **Sicherheit**.
2. Wechseln Sie zu **Eingehende Regeln**.
3. Erstellen Sie eine neue eingehende Firewallregel für das Programm c:\Programme (x86)\<\Microsoft SQL Server Version\>\tools\dreplaycontroller\dreplaycontroller.exe.
4. Hiermit wird der Zugriff auf Domänen Ebene auf alle Ports für dreplaycontroller. exe zugelassen, damit die Kommunikation mit dem Controller Dienst Remote möglich ist.
5. Speichern Sie die Regel.

## <a name="set-up-target-computers"></a>Einrichten von Ziel Computern

Zum Ausführen eines A/B-Tests oder eines Experiments sind zwei Wiederholungen erforderlich. Das heißt, Sie benötigen möglicherweise zwei separate Instanzen von SQL Server Installationen für ein Migrations Szenario.

Sie können auch die beiden Versionen SQL Server Instanzen auf demselben Computer installieren. Ein Nachteil besteht darin, sicherzustellen, dass die Instanzen isoliert sind, wenn eine Wiedergabe ausgeführt wird.

Die folgenden Schritte müssen für jede Wiedergabe ausgeführt werden:

1. Stellen Sie die Sicherung der Datenbank wieder her.
2. Erteilen von Berechtigungen für den Benutzer des Client Dienst Kontos für den Zugriff auf die Datenbanken unter der SQL Server Instanz. Berechtigungen sind erforderlich, damit die Abfragen für die SQL Server Instanz ausgeführt werden.
3. Starten Sie die Wiedergabe.

## <a name="see-also"></a>Siehe auch

- Informationen dazu, wie Sie eine aufgezeichnete Ablauf Verfolgung in einer aktualisierten Testumgebung wiedergeben, finden Sie unter Wiedergeben [einer Ablauf Verfolgung in Assistent für Datenbankexperimente](database-experimentation-assistant-replay-trace.md).
