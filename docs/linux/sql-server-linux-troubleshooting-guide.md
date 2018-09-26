---
title: Problembehandlung bei SQLServer unter Linux | Microsoft-Dokumentation
description: Bietet Tipps zur Problembehandlung für die Verwendung von SQL Server unter Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/30/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 99636ee8-2ba6-4316-88e0-121988eebcf9S
ms.openlocfilehash: b49506bc7a2ba4e88b4c6551d45dce24e2873f7e
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2018
ms.locfileid: "46712462"
---
# <a name="troubleshoot-sql-server-on-linux"></a>Problembehandlung bei SQLServer unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dieses Dokument beschreibt, wie Sie die Problembehandlung für Microsoft SQL Server unter Linux oder in einem Docker-Container ausgeführt wird. Bei der Problembehandlung SQL Server unter Linux, denken Sie daran, überprüfen die unterstützten Funktionen und bekannte Einschränkungen in der [SQL Server on Linux Release Notes](sql-server-linux-release-notes.md).

> [!TIP]
> Antworten auf häufig gestellte Fragen finden Sie unter den [SQL Server unter Linux – häufig gestellte Fragen](sql-server-linux-faq.md).

## <a id="connection"></a> Problembehandlung bei Verbindungsfehlern
Wenn beim Herstellen einer Verbindung mit dem Linux-SQL-Server Probleme auftreten, sind einige Punkte zu überprüfen. 

- Stellen Sie sicher, dass der Servername oder IP-Adresse von Ihrem Clientcomputer erreichbar ist.

   > [!TIP]
   > Um die IP-Adresse Ihrem Ubuntu-Computer zu suchen, können Sie den Befehl "Ifconfig", wie im folgenden Beispiel ausführen:
   >
   >   ```bash
   >   sudo ifconfig eth0 | grep 'inet addr'
   >   ```
   > Für Red Hat können Sie die IP-Adresse wie im folgenden Beispiel gezeigt:
   >
   >   ```bash
   >   sudo ip addr show eth0 | grep "inet"
   >   ```
   > Eine Ausnahme aus, um dieses Verfahren bezieht sich auf virtuellen Azure-Computern. Für Azure-VMs [finden Sie die öffentliche IP-Adresse für den virtuellen Computer im Azure-Portal](https://docs.microsoft.com/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine#connect).

- Falls zutreffend, überprüfen Sie, dass Sie SQL Server-Port (Standardport: 1433) in der Firewall geöffnet haben.

- Für Azure-VMs, überprüfen Sie, ob eine [netzwerksicherheitsgruppen-Regel für den SQL Server-Standardport](https://docs.microsoft.com/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine#remote).

- Stellen Sie sicher, dass der Benutzername und das Kennwort keine Schreibfehler oder zusätzlichen Leerzeichen oder falsche Groß-/Kleinschreibung enthalten.

- Versuchen Sie es explizit auf die Anzahl Protokoll und Port mit dem Namen des Servers wie im folgenden Beispiel festlegen: **Tcp:servername, 1433**.

- Probleme mit der Netzwerkkonnektivität können auch Verbindungsfehlern und zeitüberschreitungen führen. Nachdem Sie überprüft haben, die Verbindungsinformationen und die Netzwerkkonnektivität, versuchen Sie es erneut, die Verbindung.

## <a name="manage-the-sql-server-service"></a>Verwalten von SQL Server-Diensts

Die folgenden Abschnitte zeigen, wie Sie starten, beenden, Neustarten und überprüfen Sie den Status des SQL Server-Diensts. 

### <a name="manage-the-mssql-server-service-in-red-hat-enterprise-linux-rhel-and-ubuntu"></a>Verwalten des Diensts Mssql-Server, Red Hat Enterprise Linux (RHEL) und Ubuntu 

Überprüfen Sie den Status des SQL Server-Dienst mit dem folgenden Befehl ein:

   ```bash
   sudo systemctl status mssql-server
   ```

Sie können zu beenden, starten oder Neustarten von SQL Server-Diensts, je nach Bedarf mit den folgenden Befehlen:

   ```bash
   sudo systemctl stop mssql-server
   sudo systemctl start mssql-server
   sudo systemctl restart mssql-server
   ```

### <a name="manage-the-execution-of-the-mssql-docker-container"></a>Die Ausführung von der Mssql-Docker-Container verwalten

Sie können den Status und Container-ID, von der zuletzt erstellte SQL Server-Docker-Container abrufen, indem Sie den folgenden Befehl ausführen (die ID ist unter den **CONTAINER-ID** Spalte):

   ```bash
   sudo docker ps -l
   ```
   
Sie beenden oder starten Sie SQL Server-Dienst nach Bedarf mit den folgenden Befehlen neu:
   
   ```bash
   sudo docker stop <container ID>
   sudo docker restart <container ID>
   ```

> [!TIP]
> Weitere Problembehandlungstipps für Docker finden Sie unter [zur Problembehandlung von SQL Server-Docker-Containern](sql-server-linux-configure-docker.md#troubleshooting).

## <a name="access-the-log-files"></a>Zugriff auf die Protokolldateien
   
Der SQL Server-Engine protokolliert in die Datei /var/opt/mssql/log/errorlog in Linux- und Docker-Installationen. Sie müssen im Modus "Superuser", dieses Verzeichnis zu durchsuchen.

Der Installer protokolliert hier: / Var/opt/Mssql/Setup-< Zeitstempel, der Zeitpunkt der Installation darstellt > können Sie die Errorlog-Dateien mit einem beliebigen kompatible UTF-16-Tool wie 'Vim' Durchsuchen, oder "cat" wie folgt aus: 

   ```bash
   sudo cat errorlog
   ```

Falls gewünscht, können Sie auch die Dateien in UTF-8 mit eingelesen konvertieren "more" oder "kleiner", mit dem folgenden Befehl:
   
   ```bash
   sudo iconv –f UTF-16LE –t UTF-8 <errorlog> -o <output errorlog file>
   ```
## <a name="extended-events"></a>Erweiterte Ereignisse

Erweiterte Ereignisse können über einen SQL‑Befehl abgefragt werden.  Weitere Informationen zu erweiterten Ereignissen finden [hier](https://technet.microsoft.com/library/bb630282.aspx):

## <a name="crash-dumps"></a>Absturzabbilder 

Suchen Sie nach der Absturzabbilder in das Protokollverzeichnis unter Linux. Überprüfen Sie, ob unter dem Verzeichnis /var/opt/mssql/log Speicherabbilder von Linux-Core (. tar.gz2-Erweiterung) oder SQL-Minidumps (Durchwahl .mdmp)

Für kernspeicherabbilder 
   ```bash
   sudo ls /var/opt/mssql/log | grep .tar.gz2 
   ```

Für SQL-dumps 
   ```bash
   sudo ls /var/opt/mssql/log | grep .mdmp 
   ```
   
## <a name="start-sql-server-in-minimal-configuration-or-in-single-user-mode"></a>Starten Sie SQLServer in der Minimalkonfiguration oder im Einzelbenutzermodus

### <a name="start-sql-server-in-minimal-configuration-mode"></a>Starten Sie SQLServer im Modus der Minimalkonfiguration
Dies ist hilfreich, wenn der Server aufgrund der Einstellung eines Konfigurationswerts (z. B. aufgrund von Arbeitsspeichermangel) nicht gestartet werden kann.
  
   ```bash
   sudo -u mssql /opt/mssql/bin/sqlservr -f
   ```

### <a name="start-sql-server-in-single-user-mode"></a>Starten Sie SQLServer im Einzelbenutzermodus
Unter bestimmten Umständen müssen Sie möglicherweise zu einer Instanz von SQL Server im Einzelbenutzermodus mithilfe der Startoption-m. Dies ist z. B. der Fall, wenn Sie Serverkonfigurationsoptionen ändern oder eine beschädigte master-Datenbank oder andere Systemdatenbanken wiederherstellen möchten. Beispielsweise sollten Sie Serverkonfigurationsoptionen ändern oder eine beschädigte master-Datenbank oder andere Systemdatenbanken Wiederherstellen von   

Starten Sie SQLServer im Einzelbenutzermodus
   ```bash
   sudo -u mssql /opt/mssql/bin/sqlservr -m
   ```

Starten Sie SQLServer im Einzelbenutzermodus mit SQLCMD
   ```bash
   sudo -u mssql /opt/mssql/bin/sqlservr -m SQLCMD
   ```
  
> [!WARNING]  
>  Starten Sie SQL Server unter Linux mit dem Benutzer „MSSQL“, um zukünftige Startprobleme zu vermeiden. Beispiel „sudo-u mssql /opt/mssql/bin/sqlservr [STARTOPTIONEN]“ 

Wenn Sie SQL Server mit einem anderen Benutzer versehentlich begonnen haben, müssen Sie den Besitz der SQL Server-Datenbankdateien zurück an den Benutzer "Mssql" vor dem Starten von SQL Server mit "systemd" ändern. Führen Sie z. B. den folgenden Befehl zum Ändern des Besitzes aller Datenbankdateien unter /var/opt/mssql für den Benutzer "Mssql"

   ```bash
   chown -R mssql:mssql /var/opt/mssql/
   ```

## <a name="rebuild-system-databases"></a>Neuerstellen von Systemdatenbanken
Als letzten Ausweg können Sie zum Neuerstellen des Masters und Model-Datenbanken sichern, um Standardversionen aus.

> [!WARNING]
> Mit diesen Schritten werden **Löschen aller Daten von SQL Server-System** , die Sie konfiguriert haben. Dies umfasst Informationen über die Benutzerdatenbanken (aber nicht die Benutzerdatenbanken sich selbst). Es werden auch andere Informationen gespeichert, die in den Systemdatenbanken, einschließlich der folgenden gelöscht: Master Key-Informationen, alle Zertifikate in Master, das Kennwort des Anmeldenamens "SA", projektbezogenen Informationen aus Msdb, DB E-Mail-Informationen aus Msdb "und" Sp_configure-Optionen geladen. Verwenden Sie nur, wenn Sie die Auswirkungen kennen!

1. Beenden Sie SqlServer.

   ```bash
   sudo systemctl stop mssql-server
   ```

1. Führen Sie **Sqlservr** mit der **-Force-Setup** Parameter. 

   ```bash
   sudo -u mssql /opt/mssql/bin/sqlservr --force-setup
   ```
   
   > [!WARNING]
   > Siehe die vorherige Warnung! Sie müssen außerdem Ausführen als die **Mssql** Benutzer wie hier gezeigt.

1. Nachdem der Meldung "Wiederherstellung ist abgeschlossen" angezeigt wird, drücken Sie STRG + C. Dieser wird Computer mit SQL Server heruntergefahren

1. Konfigurieren Sie das SA-Kennwort ein.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set-sa-password
   ```
   
1. Starten Sie SQL Server und konfigurieren Sie den Server neu. Dies schließt wiederherstellen oder erneuten Anfügen einer beliebigen Benutzerdatenbank.

   ```bash
   sudo systemctl start mssql-server
   ```

## <a name="improve-performance"></a>Verbessern der Leistung

Es gibt viele Faktoren, die Leistung zu erzielen, einschließlich Datenbankentwurf, Hardware- und arbeitsauslastungsanforderungen zu beeinflussen. Wenn Sie zur Verbesserung der Leistung möchten, zunächst die bewährten Methoden im Artikel [bewährte Methoden für Leistung und von Konfigurationsrichtlinien für das SQL Server unter Linux](sql-server-linux-performance-best-practices.md). Anschließend lernen Sie einige der Tools die Berechtigung für die Behandlung von Leistungsproblemen.

- [Abfragespeicher](../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)
- [Dynamische Verwaltungssichten (DMVs) für System](../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)
- [Leistungsdashboard in SQL Server Management Studio](https://blogs.msdn.microsoft.com/sql_server_team/new-in-ssms-performance-dashboard-built-in/)

## <a name="common-issues"></a>Häufige Probleme

1. Sie können nicht mit Ihrer SQL Server-Remoteinstanz verbinden.

   Finden Sie im Abschnitt zur Problembehandlung im Artikel [Herstellen einer Verbindung mit SQL Server unter Linux](#connection).

2. Fehler: Die Hostnamen muss sein 15 Zeichen oder weniger.

   Dies ist eine bekannte Problem, das ausgeführt wird, wenn der Name des Computers, der versucht, installieren das Debian-Paket von SQLServer mehr als 15 Zeichen ist. Es gibt derzeit keine problemumgehungen als den Namen des Computers ändern. Eine Möglichkeit, dies zu erreichen, ist durch Bearbeiten der Hostname-Datei und Neustarten des Computers. Die folgenden [Website Handbuch](http://www.cyberciti.biz/faq/ubuntu-change-hostname-command/) wird dies ausführlich erläutert.

3. Das System-Verwaltung (SA)-Kennwort zurücksetzen.

   Wenn Sie das Systemadministratorkennwort (SA vergessen haben) oder einem anderen Grund zurücksetzen müssen, gehen Sie wie folgt vor.

   > [!NOTE]
   > Die folgenden Schritte aus, beendet SQL Server-Dienst vorübergehend.

   Melden Sie sich das Host-Terminal, führen Sie die folgenden Befehle aus, und befolgen Sie die Anweisungen zum Zurücksetzen des SA-Kennworts:

   ```bash
   sudo systemctl stop mssql-server
   sudo /opt/mssql/bin/mssql-conf setup
   ```

4. Verwenden Sonderzeichen im Kennwort an.

   Wenn Sie einige Zeichen in das Anmeldekennwort für SQL Server verwenden, müssen Sie sie mit einem umgekehrten Schrägstrich als Escapezeichen, bei Verwendung in einem Linux-Befehl im Terminal. Beispielsweise müssen Sie mit Escapezeichen versehen das Dollarzeichen ($) jedes Mal, wenn Sie sie verwenden in einem terminal Befehls-Shell-Skript:

   Ist nicht geeignet:

   ```bash
   sudo sqlcmd -S myserver -U sa -P Test$$
   ```

   Funktioniert:

   ```bash
   sqlcmd -S myserver -U sa -P Test\$\$
   ```

   Ressourcen: [Sonderzeichen](http://tldp.org/LDP/abs/html/special-chars.html)
   [Escaping](http://tldp.org/LDP/abs/html/escapingsection.html)

[!INCLUDE[Get Help Options](../includes/paragraph-content/get-help-options.md)]
