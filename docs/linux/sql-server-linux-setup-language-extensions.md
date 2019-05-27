---
title: Installieren von SQL Server-Spracherweiterungen (Java) unter Linux | Microsoft-Dokumentation
description: Erfahren Sie, wie zum Installieren von SQL Server-Spracherweiterungen (Java) auf Red Hat, Ubuntu und SUSE.
author: dphansen
ms.author: davidph
manager: cgronlun
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: b694cde8784a1607c85ed9ab7dfcc4d770a6d938
ms.sourcegitcommit: 3b266dc0fdf1431fdca6b2ad34ae5fd38abe9f69
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66186805"
---
# <a name="install-sql-server-2019-language-extensions-java-on-linux"></a>Installieren von SQL Server 2019-Spracherweiterungen (Java) unter Linux

Es sind Spracherweiterungen ein Add-on für die Datenbank-Engine. Zwar Sie können [installieren Sie die Datenbank-Engine und Spracherweiterungen gleichzeitig](#install-all), es ist eine bewährte Methode zum Installieren und konfigurieren die SQL Server-Datenbank-Engine zuerst, damit Sie Probleme beheben können, bevor Sie weitere Komponenten hinzufügen. 

Führen Sie die Schritte in diesem Artikel zum Installieren der Erweiterung der Java-Sprache aus.

Speicherort des Pakets für die Java-Erweiterungen ist in den SQL Server Linux-Quell-Repositorys. Wenn Sie bereits über Quellcode-Repositorys für die Datenbank-Engine-Installation konfiguriert, können Sie Ausführen der **Mssql-Server-Erweiterbarkeit – Java** Paket Befehle zur Installation über die gleichen Repository-Registrierung.

Spracherweiterungen wird auch auf Linux-Container unterstützt. Wir bieten keine vorab erstellten Container mit Erweiterungen der Sprache, aber erstellen Sie einen aus der SQL Server-Containern unter Verwendung von [eine Beispielvorlage auf GitHub verfügbar](https://github.com/Microsoft/mssql-docker/tree/master/linux/preview/examples/mssql-mlservices).

## <a name="uninstall-previous-ctp"></a>Deinstallieren der vorherigen CTP-Version

Die Liste der Pakete hat sich über die letzten CTP-Version Versionen, was zu weniger Pakete geändert werden. Es wird empfohlen, deinstallieren CTP 2.x So entfernen Sie alle früheren Pakete vor der Installation der CTP-Version 3.0. Seite-an-Seite Installation mehrerer Versionen wird nicht unterstützt.

### <a name="1-confirm-package-installation"></a>1. Paketinstallation bestätigen

Sie möchten möglicherweise prüfen, ob das Vorhandensein einer früheren Installation als ersten Schritt. Die folgenden Dateien angeben eine vorhandene Installation: checkinstallextensibility.sh, Exthost, Launchpad.

```bash
ls /opt/microsoft/mssql/bin
```

### <a name="2-uninstall-previous-ctp-2x-packages"></a>2. Deinstallieren der vorherigen CTP-Version 2.x-Pakete

Deinstallieren Sie auf der untersten Paketebene. Alle abhängigen für ein Paket auf niedrigerer Ebene upstreampaket wird automatisch deinstalliert.

  + Entfernen Sie für die Java-Integration **Mssql-Server-Erweiterbarkeit – Java**

Befehle zum Löschen von Paketen, die in der folgenden Tabelle angezeigt werden.

| Platform  | Paket entfernen Befehle | 
|-----------|----------------------------|
| RHEL  | `sudo yum remove msssql-server-extensibility-java` |
| SLES  | `sudo zypper remove msssql-server-extensibility-java` |
| Ubuntu    | `sudo apt-get remove msssql-server-extensibility-java`|

### <a name="3-proceed-with-ctp-30-install"></a>3. CTP 3.0-Installation nicht fortsetzen

Auf der höchsten Paketebene, die mithilfe der Anweisungen in diesem Artikel für Ihr Betriebssystem installieren.

Für jeden Satz betriebssystemspezifischen Anweisungen zur Installation *höchsten Paketebene* ist entweder **Beispiel 1 – vollständige Installation** für den vollständigen Satz von Paketen oder **Beispiel 2: minimale Installation**  für die geringste Anzahl von Paketen, die für die kleinstmögliche Installation erforderlich.

1. Führen Sie Befehle zur Installation mit dem Paket-Manager und die Syntax für Ihre Linux-Distribution: 

   + [RedHat](#RHEL)
   + [Ubuntu](#ubuntu)
   + [SUSE](#suse)

## <a name="prerequisites"></a>Erforderliche Komponenten

+ Die Linux-Version muss [von SQL Server unterstützte](sql-server-linux-release-notes-2019.md#supported-platforms), aber nicht die Docker-Engine enthalten ist. Versionen werden unterstützt:

   + [Red Hat Enterprise Linux (RHEL)](quickstart-install-connect-red-hat.md)

   + [SUSE Enterprise Linux Server](quickstart-install-connect-suse.md)

   + [Ubuntu](quickstart-install-connect-ubuntu.md)

+ Sie sollten ein Tool zum Ausführen von T-SQL-Befehlen haben. Ein Abfrage-Editor ist für die Konfiguration nach der Installation und Überprüfung erforderlich. Es wird empfohlen [Studio für Azure Data](https://docs.microsoft.com/sql/azure-data-studio/download?view=sql-server-2017#get-azure-data-studio-for-linux), kostenloser Download, die unter Linux ausgeführt wird.

## <a name="package-list"></a>Liste der Pakete

Pakete sind auf einem Gerät Internetverbindung heruntergeladen und installiert, unabhängig von der Datenbank-Engine, die mit dem Paketinstaller für jedes Betriebssystem. Die folgende Tabelle beschreibt alle verfügbaren Pakete.

| Paketname | Applies-to | Description |
|--------------|----------|-------------|
|mssql-server-extensibility  | Alle Sprachen | Das Erweiterungsframework zum Ausführen der Java-Code verwendet. |
|mssql-server-extensibility-java | Java | Java-Erweiterung für das Laden einer Java-ausführungsumgebung. Es gibt keine zusätzliche Bibliotheken oder Pakete für Java. |

<a name="RHEL"></a>

## <a name="install-language-extensions"></a>Installieren von Spracherweiterungen

Sie können Spracherweiterungen und Java unter Linux installieren, durch die Installation von **Mssql-Server-Erweiterbarkeit – Java**. Bei der Installation **Mssql-Server-Erweiterbarkeit – Java**, das Paket automatisch JRE 8 installiert, wenn es nicht bereits installiert ist. Es wird eine Umgebungsvariable namens JRE_HOME auch die JVM-Pfad hinzufügen.

> [!Note]
> Bei einem Server mit Internetverbindung paketabhängigkeiten heruntergeladen und als Teil der Installation des Hauptpakets installiert. Wenn Ihr Server nicht mit dem Internet verbunden ist, finden Sie weitere Details in der [offlineeinrichtung](#offline-install).

### <a name="redhat-install-command"></a>Red hat-Befehl "Install"

Sie können die Spracherweiterungen für Java auf Red hat, die mit dem folgenden Befehl installieren.

> [!Tip]
> Führen Sie nach Möglichkeit `yum clean all` Pakete auf dem System vor der Installation zu aktualisieren.

```bash
# Install as root or sudo
sudo yum install mssql-server-extensibility-java
```

<a name="ubuntu"></a>

### <a name="ubuntu-install-command"></a>Befehl "Install" Ubuntu

Sie können die Spracherweiterungen für Java unter Ubuntu, die mit dem folgenden Befehl installieren.

> [!Tip]
> Führen Sie nach Möglichkeit `apt-get update` Pakete auf dem System vor der Installation zu aktualisieren. Darüber hinaus möglicherweise einige Docker-Images von Ubuntu nicht die Option "apt-Transport-Https". Verwenden sie zur Installation `apt-get install apt-transport-https`.

```bash
# Install as root or sudo
sudo apt-get install mssql-server-extensibility-java
```

<a name="suse"></a>

### <a name="suse-install-command"></a>SUSE-Befehl "Install"

Sie können die Spracherweiterungen für Java unter SUSE mit dem folgenden Befehl installieren.

```bash
# Install as root or sudo
sudo zypper install mssql-server-extensibility-java
```

## <a name="post-install-config-required"></a>Nach der Installation Config (erforderlich)

1. Erteilen von Berechtigungen für Linux

    Sie müssen diesen Schritt ausführen, wenn Sie externe Bibliotheken verwenden. Die empfohlene Vorgehensweise für arbeiten verwendet externe Bibliotheken zurückzugreifen. Hilfe zum Erstellen einer externen Bibliothek aus Ihrer JAR-Datei, finden Sie unter [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)

    Wenn Sie keine externe Bibliotheken verwenden, müssen Sie SQL Server mit Berechtigungen zum Ausführen der Java-Klassen in Ihrer JAR-Datei zur Verfügung.

    Zum Gewähren von Lese- und Ausführungsberechtigungen für eine JAR-Datei, führen Sie den folgenden **Chmod** Befehl die JAR-Datei. Es wird empfohlen, immer die Klassendateien in eine JAR-Datei einfügen, bei der Arbeit mit SQL Server. Hilfe, die eine JAR-Datei erstellen, finden Sie unter [Vorgehensweise: Erstellen Sie eine JAR-Datei](https://docs.microsoft.com/sql/language-extensions/how-to/create-a-java-jar-file-from-class-files).

    ```cmd
    chmod ug+rx <MyJarFile.jar>
    ```

    Sie müssen auch Mssql_satellite gewähren die JAR-Datei zum Lesen/ausführen.

    ```cmd
    chown mssql_satellite:mssql_satellite <MyJarFile.jar>
    ```

    Zusätzliche Konfiguration ist in erster Linie durch die [Mssql-Conf-Tool](sql-server-linux-configure-mssql-conf.md).

2. Fügen Sie der Mssql-Benutzerkonto zum Ausführen von SQL Server-Dienst hinzu. Dies ist erforderlich, wenn Sie das Setup nicht zuvor ausgeführt haben.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

3. Aktivieren Sie ausgehender Netzwerkzugriff. Ausgehender Netzwerkzugriff ist standardmäßig deaktiviert. Um ausgehende Anforderungen zu aktivieren, legen Sie die "Outboundnetworkaccess" boolesche Eigenschaft, die mit dem Mssql-Conf-Tool. Weitere Informationen finden Sie unter [Konfigurieren von SQL Server unter Linux mit Mssql-Conf](sql-server-linux-configure-mssql-conf.md#mlservices-outbound-access).

   ```bash
   # Run as SUDO or root
   # Enable outbound requests over the network
   sudo /opt/mssql/bin/mssql-conf set extensibility outboundnetworkaccess 1
   ```

4. Neustart der SQL Server Launchpad-Dienst und der Datenbank-Engine-Instanz, um die aktualisierten Werte aus der INI-Datei zu lesen. Eine Neustart-Nachricht daran erinnert Sie jedes Mal, wenn eine Erweiterbarkeit Einstellung geändert wird.  

   ```bash
   systemctl restart mssql-launchpadd

   systemctl restart mssql-server.service
   ```

5. Aktivieren Sie die Ausführung des externen Skripts mithilfe von Azure Data Studio oder einem anderen Tool wie SQL Server Management Studio (nur Windows), die Transact-SQL ausgeführt wird.

   ```bash
   EXEC sp_configure 'external scripts enabled', 1
   RECONFIGURE WITH OVERRIDE
   ```

6. Neustart der `mssql-launchpadd` -Dienst erneut.

7. Für jede Datenbank in-spracherweiterungen verwenden möchten, müssen Sie die externe Sprache mit registrieren [Erstellen externer Sprachen](https://docs.microsoft.com/sql/t-sql/statements/create-external-language-transact-sql).

## <a name="verify-installation"></a>Überprüfen der Installation

Integration der Java-Funktion enthält keine Bibliotheken, Sie können jedoch ausführen `grep -r JRE_HOME /etc` , bestätigen die JAVA_HOME-Umgebungsvariable erstellen.

Gespeicherte Prozedur, die Aufrufen von Java Überprüfen der Installation, zum Ausführen eines T-SQL-Skripts, das ein System ausgeführt wird. Für diese Aufgabe benötigen Sie ein Abfragetool. Azure Data Studio ist eine gute Wahl. Andere häufig verwendete Tools wie SQL Server Management Studio oder PowerShell sind nur für Windows. Wenn Sie einen Windows-Computer mit diesen Tools verfügen, verwenden Sie es für die Verbindung zu Ihrer Linux-Installation der Datenbank-Engine.

<a name="install-all"></a>

## <a name="full-install-of-sql-server-and-language-extensions"></a>Vollständige Installation von SQL Server und Spracherweiterungen

Sie können installieren und konfigurieren die Datenbank-Engine und Spracherweiterungen in eine Prozedur durch Anfügen von Java-Pakete und die Parameter für einen Befehl, der die Datenbank-Engine installiert.

1. Geben Sie eine Befehlszeile, die den Datenbank-Engine sowie die Sprachfeatures für die Erweiterung enthält.

  Sie können Java Installieren von Erweiterungen in einer Datenbank-Engine hinzufügen.

  ```bash
  sudo yum install -y mssql-server mssql-server-extensibility-java 
  ```

3. Zustimmen Sie Lizenzverträgen, und schließen Sie die Konfiguration nach der Installation. Verwenden der **Mssql-Conf** Tool für diese Aufgabe.

  ```bash
  sudo /opt/mssql/bin/mssql-conf setup
  ```

  Sie werden zum Akzeptieren des Lizenzvertrags für die Datenbank-Engine, wählen Sie eine Edition und Festlegen des Administratorkennworts aufgefordert werden. 

4. Starten Sie den Dienst neu, wenn Sie dazu aufgefordert werden.

  ```bash
  sudo systemctl restart mssql-server.service
  ```

## <a name="unattended-installation"></a>Für die unbeaufsichtigte installation

Mithilfe der [unbeaufsichtigte Installation](https://docs.microsoft.com/sql/linux/sql-server-linux-setup#unattended) für die Datenbank-Engine, fügen Sie die Pakete für die Mssql-Server-Erweiterbarkeit – Java.

<a name="offline-install"></a>


## <a name="offline-installation"></a>Offlineinstallation

Führen Sie die [Offline-Installation](sql-server-linux-setup.md#offline) Anweisungen für die Schritte zum Installieren der Pakete. Suchen Sie Ihre Download-Seite, und dann herunterladen Sie bestimmte Pakete, die mithilfe der folgenden Liste der Pakete.

> [!Tip]
> Einige der Paket-Tools bieten, dass Befehle, die Ihnen helfen können paketabhängigkeiten bestimmen. Verwenden Sie für Yum, `sudo yum deplist [package]`. Für Ubuntu verwenden `sudo apt-get install --reinstall --download-only [package name]` gefolgt von `dpkg -I [package name].deb`.

#### <a name="download-site"></a>Downloadsite

Sie können Pakete aus [ https://packages.microsoft.com/ ](https://packages.microsoft.com/). Alle Pakete für Java werden zusammen mit der Datenbank-Engine-Paket. 

#### <a name="redhat7-paths"></a>RedHat/7-Pfade

|||
|--|----|
| MSSQL/Erweiterbarkeit-Java-Pakete | [https://packages.microsoft.com/rhel/7/mssql-server-preview/](https://packages.microsoft.com/rhel/7/mssql-server-preview/) |

#### <a name="ubuntu1604-paths"></a>Ubuntu 16.04/Pfade

|||
|--|----|
| MSSQL/Erweiterbarkeit-Java-Pakete | [https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/) |

#### <a name="suse12-paths"></a>SUSE 12/Pfade

|||
|--|----|
| MSSQL/Erweiterbarkeit-Java-Pakete | [https://packages.microsoft.com/sles/12/mssql-server-preview/](https://packages.microsoft.com/sles/12/mssql-server-preview/) |

#### <a name="package-list"></a>Liste der Pakete

Je nachdem welche Erweiterungen möchten Sie verwenden, laden die Pakete, die für eine bestimmte Sprache erforderlich. Genauen Dateinamen Plattforminformationen in das Suffix einschließen sollten, aber die folgenden Dateinamen nahe genug, um zu bestimmen, welche Dateien erhalten Sie.

```
# Core packages 
mssql-server-15.0.1000
mssql-server-extensibility-15.0.1000

# Java
mssql-server-extensibility-java-15.0.1000
```

## <a name="limitations-in-ctp-releases"></a>Einschränkungen in der CTP-Versionen

Spracherweiterungen und Java-Erweiterbarkeit unter Linux ist immer noch in der aktiven Entwicklung. Die folgenden Features sind in der Vorschauversion noch nicht aktiviert.

+ Implizite Authentifizierung ist zu diesem Zeitpunkt an, was bedeutet, dass Sie sich an den Server aus Java in Bearbeitung, den Zugriff auf Daten oder andere Ressourcen verbinden können derzeit nicht unter Linux verfügbar.


### <a name="resource-governance"></a>Ressourcenkontrolle

Es gibt Parität zwischen Linux und Windows für [Ressourcenkontrolle](../t-sql/statements/create-external-resource-pool-transact-sql.md) für externe Ressourcenpools, aber die Statistiken für [sys.dm_resource_governor_external_resource_pools](../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md) derzeit andere Einheiten unter Linux. Einheiten werden in einer zukünftigen CTP-Version ausgerichtet.
 
| Spaltenname   | Description | Der Wert unter Linux | 
|---------------|--------------|---------------|
|peak_memory_kb | Die Höchstmenge an Arbeitsspeicher, die für den Ressourcenpool verwendet werden soll. | Unter Linux ist diese Statistik des Arbeitsspeichersubsystems CGroups, stammen, in denen der Wert memory.max_usage_in_bytes |
|write_io_count | Die Gesamtanzahl Schreibvorgänge seit dem Zurücksetzen der ressourcenkontrollenstatistiken wurden ausgegeben. | Unter Linux ist diese Statistik über das Subsystem für CGroups Blkio, stammt, in denen der Wert in der Zeile schreiben blkio.throttle.io_serviced | 
|read_io_count | Die Gesamtanzahl Lesevorgänge seit dem Zurücksetzen der ressourcenkontrollenstatistiken wurden ausgegeben. | Unter Linux ist diese Statistik über das Subsystem für CGroups Blkio, stammt, in dem Wert der Zeile lesen blkio.throttle.io_serviced | 
|total_cpu_kernel_ms | Die kumulierte CPU-Benutzer Kernelzeit in Millisekunden seit dem Zurücksetzen der ressourcenkontrollenstatistiken wurden. | Unter Linux ist diese Statistik über das Subsystem für CGroups Cpuacct, stammt, in denen der Wert für die Benutzerzeile cpuacct.stat |  
|total_cpu_user_ms | Die kumulierte CPU-Benutzerzeit in Millisekunden seit dem Zurücksetzen der ressourcenkontrollenstatistiken wurden.| Unter Linux ist diese Statistik über das Subsystem für CGroups Cpuacct, stammt, in denen der Wert auf den Wert der System-Zeile cpuacct.stat | 
|active_processes_count | Die Anzahl von externen Prozessen, die zum Zeitpunkt der Anforderung ausgeführt wird.| Unter Linux ist diese Statistik über das Subsystem für GGroups Pids, stammt, in denen der Wert pids.current | 

## <a name="next-steps"></a>Nächste Schritte

Java-Entwickler können mit einigen einfachen Beispielen beginnen, und die Grundlagen der Funktionsweise von Java mit SQL Server. Der nächste Schritt ist finden Sie in den folgenden Links:

+ [Tutorial: Reguläre Ausdrücke mit Java](../language-extensions/tutorials/search-for-string-using-regular-expressions-in-java.md)