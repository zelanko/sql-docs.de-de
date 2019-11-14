---
title: Wiedergabe für SQL Server Upgrades konfigurieren
description: Wiedergabe in Assistent für Datenbankexperimente konfigurieren
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
ms.openlocfilehash: b58233e40e27908f0bc8b03a95455216de2c119c
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056723"
---
# <a name="configure-replay-in-database-experimentation-assistant"></a>Wiedergabe in Assistent für Datenbankexperimente konfigurieren

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

1. Installieren Sie den Distributed Replay Controller, indem Sie den SQL Server Installer verwenden. Wenn Sie den Schritt SQL Server Installer-Assistent übersprungen haben, mit dem der Distributed Replay Controller konfiguriert wird, können Sie den Controller über die Konfigurationsdatei konfigurieren. Bei einer typischen Installation befindet sich die Konfigurationsdatei unter "c:\Programme (x86) \Microsoft SQL Server\<Version\>\tools\dreplaycontroller\dreplaycontroller.config.
1. Distributed Replay Controller Protokolle befinden sich unter "c:\Programme (x86) \Microsoft SQL Server\<Version\>\tools\dreplaycontroller\log".
1. Öffnen Sie "Services. msc", und wechseln Sie zum **SQL Server Distributed Replay Controller** -Dienst.
1. Klicken Sie mit der rechten Maustaste auf den Dienst, und wählen Sie dann **Eigenschaften**aus. Legen Sie das Dienst Konto auf ein Konto fest, das dem Controller und den Client Computern im Netzwerk gemeinsam ist.
1. Wählen Sie **OK** aus, um das **Eigenschaften** Fenster zu schließen.
1. Starten Sie den **SQL Server Distributed Replay Controller** -Dienst über "Services. msc" neu. Sie können auch die folgenden Befehle in der Befehlszeile ausführen, um den Dienst neu zu starten:<br/>
   `NET STOP "SQL Server Distributed Replay Controller"`<br/>
   `NET START "SQL Server Distributed Replay Controller"`
1. Weitere Konfigurationsoptionen finden Sie unter [Konfigurieren von Distributed Replay](https://docs.microsoft.com/sql/tools/distributed-replay/configure-distributed-replay).

## <a name="configure-dcom"></a>Konfigurieren von DCOM

Diese Konfiguration ist nur auf dem Controller Computer erforderlich.

1. Öffnen Sie DCOMCNFG. exe.
1. Erweitern Sie **Komponenten Dienste** > **Computer** > **Arbeitsplatz** > **DCOM-Konfiguration**.
1. Klicken Sie unter **DCOM-Konfiguration**mit der rechten Maustaste auf **dreplaycontroller**, und wählen Sie dann **Eigenschaften**aus.
1. Wählen Sie die Registerkarte **Sicherheit** .
1. Wählen Sie unter **Start-und Aktivierungs Berechtigungen**die Option **Anpassen**aus, und klicken Sie dann auf **Bearbeiten**.
1. Fügen Sie den Benutzer hinzu, der die Wiedergabe startet. Hiermit werden dem Benutzer lokale Start-und lokale Aktivierungs Berechtigungen erteilt. Wenn der Benutzer plant, Remote zu starten oder zu aktivieren, müssen Sie den Benutzern die Berechtigungen Remote Start und Remote Aktivierung erteilt haben.
1. Wählen Sie **OK** aus, um die Änderungen zu übertragen und zur Registerkarte **Sicherheit** zurückzukehren.
1. Wählen Sie unter **Zugriffsberechtigungen**die Option **Anpassen**aus, und klicken Sie dann auf **Bearbeiten**.
1. Fügen Sie den Benutzer hinzu, der die Wiedergabe startet. Erteilt dem Benutzer lokale Zugriffsberechtigungen. Wenn der Benutzer einen Remote Zugriff auf den Controller Dienst plant, sollten Sie dem Benutzer Remote Zugriffsberechtigungen einräumen.
1. Wählen Sie **OK** aus, um die Änderungen zu übertragen und zur Registerkarte **Sicherheit** zurückzukehren.
1. Wählen Sie **OK** aus, um die Änderungen zu übertragen.
1. Starten Sie den SQL Server Distributed Replay Controller-Dienst über "Services. msc" neu. Sie können auch die folgenden Befehle in der Befehlszeile ausführen, um den Dienst neu zu starten:<br/>
   `NET STOP "SQL Server Distributed Replay Controller"`<br/>
   `NET START "SQL Server Distributed Replay Controller"`

## <a name="set-up-the-client-service"></a>Einrichten des Client Dienstanbieter

Verwenden Sie vor dem Einrichten des-Client Dienstanbieter Netzwerk Tools wie Ping, um zu überprüfen, ob die Controller-und Client Computer kommunizieren können.

1. Installieren Sie den Distributed Replay Client, indem Sie den SQL Server Installer verwenden.
1. Öffnen Sie "Services. msc", und wechseln Sie zum SQL Server Distributed Replay-Client Dienst.
1. Klicken Sie mit der rechten Maustaste auf den Dienst, und wählen Sie dann **Eigenschaften**aus. Legen Sie das Dienst Konto auf ein Konto fest, das sowohl dem Controller als auch den Client Computern im Netzwerk gemeinsam ist.
1. Wählen Sie **OK** aus, um das **Eigenschaften** Fenster zu schließen. Wenn Sie den Schritt SQL Server Installer-Assistent übersprungen haben, um den Distributed Replay-Client zu konfigurieren, können Sie ihn über die Konfigurationsdatei konfigurieren. Bei einer typischen Installation befindet sich die Konfigurationsdatei unter "c:\Programme (x86) \Microsoft SQL Server\<Version\>\tools\dreplayclient\dreplayclient.config".
1. Stellen Sie sicher, dass die Datei dreplayclient. config den Namen des Controller Computers als Controller für die Registrierung enthält.
1.  Starten Sie den SQL Server Distributed Replay-Client Dienst über "Services. msc" neu. Sie können auch die folgenden Befehle in der Befehlszeile ausführen, um den Dienst neu zu starten:<br/>
    `NET STOP "SQL Server Distributed Replay Client"`<br/>
    `NET START "SQL Server Distributed Replay Client"`
1. Distributed Replay Controller Protokolle befinden sich unter c:\Programme (x86) \Microsoft SQL Server\<Version\>\tools\dreplayclient\log. Die Protokolle geben an, ob sich der Client selbst beim Controller registrieren kann.
1. Wenn die Konfiguration erfolgreich ist, wird im Protokoll die Meldung "registriert bei Controller < Controller Name\>" angezeigt.
1. Weitere Konfigurationsoptionen finden Sie unter [Konfigurieren von Distributed Replay](https://docs.microsoft.com/sql/tools/distributed-replay/configure-distributed-replay).

## <a name="set-up-distributed-replay-administration-tools"></a>Einrichten Distributed Replay Verwaltungs Tools

Mit Distributed Replay-Verwaltungs Tools können Sie schnell überprüfen, ob Distributed Replay in der Umgebung ordnungsgemäß funktioniert. Das Testen der Konfiguration kann insbesondere in einer Umgebung hilfreich sein, in der mehrere Client Computer bei einem Controller registriert sind. Möglicherweise müssen Sie SQL Server Management Studio (SSMS) installieren, um die Verwaltungs Tools zu erhalten.

1. Wechseln Sie zum Speicherort der SSMS-Installation, und suchen Sie nach dem Distributed Replay Verwaltungs Tool dreplay. exe und seinen abhängigen Komponenten.
1. Öffnen Sie ein Eingabe Aufforderungs Fenster, und führen Sie `dreplay.exe status -f 1`aus.
1. Wenn alle vorherigen Schritte erfolgreich ausgeführt wurden, gibt die Konsolenausgabe an, dass der Controller seine Clients in einem `READY` Zustand sehen kann.

## <a name="configure-the-firewall-for-remote-distributed-replay-access"></a>Konfigurieren der Firewall für den Remote Distributed Replay Zugriff

Für den Remote Zugriff auf Distributed Replay müssen Ports geöffnet werden, die innerhalb der Domäne oder des virtuellen Netzwerks sichtbar sind.

1. Öffnen Sie **Windows-Firewall** mit erweiterter **Sicherheit**.
1. Wechseln Sie zu **Eingehende Regeln**.
1. Erstellen Sie eine neue eingehende Firewallregel für das Programm c:\Program Files (x86) \Microsoft SQL Server\<Version\>\tools\dreplaycontroller\dreplaycontroller.exe.
1. Hiermit wird der Zugriff auf Domänen Ebene auf alle Ports für dreplaycontroller. exe zugelassen, damit die Kommunikation mit dem Controller Dienst Remote möglich ist.
1. Speichern Sie die Regel.

## <a name="set-up-target-computers"></a>Einrichten von Ziel Computern

Zum Ausführen eines A/B-Tests oder eines Experiments sind zwei Wiederholungen erforderlich. Das heißt, Sie benötigen möglicherweise zwei separate Instanzen von SQL Server Installationen für ein Migrations Szenario. 

Sie können auch die beiden Versionen SQL Server Instanzen auf demselben Computer installieren. Ein Nachteil besteht darin, sicherzustellen, dass die Instanzen vollständig isoliert sind, wenn eine Wiedergabe ausgeführt wird.

Die folgenden Schritte müssen für jede Wiedergabe ausgeführt werden:

1. Stellen Sie die Sicherung der Datenbank wieder her.
1. Erteilen von Berechtigungen für den Benutzer des Client Dienst Kontos für den Zugriff auf die Datenbanken unter der SQL Server Instanz. Berechtigungen sind erforderlich, damit die Abfragen für die SQL Server Instanz ausgeführt werden.
1. Starten Sie die Wiedergabe.

## <a name="next-steps"></a>Nächste Schritte

- Informationen dazu, wie Sie eine aufgezeichnete Ablauf Verfolgung in einer aktualisierten Testumgebung wiedergeben, finden Sie unter [Wiedergabe Verfolgung](database-experimentation-assistant-replay-trace.md).

- Sehen Sie sich das folgende Video an, um die Einführung von DEA und Demo in 19 Minuten zu demonstrieren:

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
