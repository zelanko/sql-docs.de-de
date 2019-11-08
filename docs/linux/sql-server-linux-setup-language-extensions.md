---
title: Installieren von SQL Server-Spracherweiterungen (Java) unter Linux
description: Erfahren Sie, wie Sie SQL Server-Spracherweiterungen (Java) unter Red Hat, Ubuntu und SUSE installieren können.
author: dphansen
ms.author: davidph
ms.reviewer: vanto
manager: cgronlun
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3e86da652231a06cd28318096ada3ae3aed7526e
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73531231"
---
# <a name="install-sql-server-2019-language-extensions-java-on-linux"></a>Installieren von SQL Server 2019-Spracherweiterungen (Java) unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Spracherweiterungen stellen ein Add-On für die Datenbank-Engine dar. Obwohl Sie die [Datenbank-Engine und Spracherweiterungen gleichzeitig installieren](#install-all) können, empfiehlt es sich, zuerst die SQL Server-Datenbank-Engine zu installieren und zu konfigurieren, damit Sie eventuelle Probleme beheben können, bevor Sie weitere Komponenten hinzufügen. 

Führen Sie die in diesem Artikel beschriebenen Schritte aus, um die Java-Spracherweiterung zu installieren.

Erweiterungspakete für Java werden unter Linux in den Quellrepositorys für SQL Server gespeichert. Wenn Sie für die Installation der Datenbank-Engine bereits Quellrepositorys konfiguriert haben, können Sie die **mssql-server-extensibility-java**-Befehle für die Paketinstallation unter Verwendung derselben Repositorregistrierung ausführen.

Spracherweiterungen werden auch in Linux-Containern unterstützt. Wir stellen keine vorgefertigten Container mit Spracherweiterungen bereit. Sie können jedoch [mithilfe einer in GitHub verfügbaren Vorlage](https://github.com/Microsoft/mssql-docker/tree/master/linux/preview/examples/mssql-mlservices) einen Container aus den SQL Server-Containern erstellen.

Spracherweiterungen und [Machine Learning Services](../advanced-analytics/index.yml) werden standardmäßig auf Big Data-Clustern für SQL Server installiert. Wenn Sie Big Data-Cluster verwenden, müssen Sie die Schritte in diesem Artikel nicht ausführen. Weitere Informationen finden Sie unter [Verwenden von Machine Learning Services (Python und R) in Big Data-Clustern](../big-data-cluster/machine-learning-services.md).

## <a name="uninstall-preview-version"></a>Deinstallieren einer Vorschauversion

Wenn Sie eine Vorschauversion (Community Technology Preview (CTP) oder Release Candidate (RC)) installiert haben, empfehlen wir, diese Version zu deinstallieren, um vor der Installation von SQL Server 2019 alle vorherigen Pakete zu entfernen. Die parallele Installation mehrerer Versionen wird nicht unterstützt, und die Paketliste wurde im Laufe der letzten Vorschauversionen (CTP/RC) geändert.

### <a name="1-confirm-package-installation"></a>1. Bestätigen der Paketinstallation

Sie sollten in einem ersten Schritt überprüfen, ob eine frühere Version installiert ist. Die folgenden Dateien sind Zeichen dafür, dass bereits eine Installation durchgeführt wurde: „checkinstallextensibility.sh“, „exthost“ und „launchpad“.

```bash
ls /opt/microsoft/mssql/bin
```

### <a name="2-uninstall-previous-ctprc-packages"></a>2. Deinstallieren früherer CTP- und RC-Pakete

Führen Sie die Deinstallation auf der niedrigsten Paketebene durch. Alle Upstreampakete, die von einem Paket auf einer niedrigeren Ebene abhängig sind, werden automatisch deinstalliert.

  + Entfernen Sie für die Java-Integration **mssql-server-extensibility-java**.

Die Befehle zum Entfernen von Paketen können Sie der folgenden Tabelle entnehmen.

| Platform  | Befehl(e) zum Entfernen eines Pakets | 
|-----------|----------------------------|
| RHEL  | `sudo yum remove msssql-server-extensibility-java` |
| SLES  | `sudo zypper remove msssql-server-extensibility-java` |
| Ubuntu    | `sudo apt-get remove msssql-server-extensibility-java`|

### <a name="3-install-sql-server-2019"></a>3. Installieren von SQL Server 2019

Führen Sie die Installation gemäß den in diesem Artikel beschriebenen Anweisungen für Ihr Betriebssystem auf der höchsten Paketebene durch.

Für sämtliche betriebssystemspezifischen Installationsanweisungen ist die *höchste Paketebene* entweder **Beispiel 1: vollständige Installation** für alle Pakete oder **Beispiel 2: minimale Installation** für die geringste Anzahl von Paketen, die für eine verwendbare Installation erforderlich sind.

1. Führen Sie Installationsbefehle mithilfe des Paket-Managers und der Syntax für Ihre Linux-Distribution aus: 

   + [Red Hat](#RHEL)
   + [Ubuntu](#ubuntu)
   + [SUSE](#suse)

## <a name="prerequisites"></a>Voraussetzungen

+ Die Linux-Version muss [von SQL Server unterstützt](sql-server-linux-release-notes-2019.md#supported-platforms) werden, muss aber nicht die Docker-Engine enthalten. Folgende Versionen werden unterstützt:

   + [Red Hat Enterprise Linux (RHEL)](quickstart-install-connect-red-hat.md)

   + [SUSE Enterprise Linux Server](quickstart-install-connect-suse.md)

   + [Ubuntu](quickstart-install-connect-ubuntu.md)

+ Sie sollten über ein Tool zum Ausführen von T-SQL-Befehlen verfügen. Sie benötigen einen Abfrage-Editor für die Konfiguration und Validierung nach der Installation. Es wird empfohlen, [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download?view=sql-server-2017#get-azure-data-studio-for-linux) zu verwenden. Dabei handelt es sich um ein kostenloses Tools, dass unter Linux verwendet werden kann.

## <a name="package-list"></a>Paketliste

Auf einem mit dem Internet verbundenen Gerät werden Pakete unabhängig von der Datenbank-Engine mithilfe des Paketinstallationsprogramms für das betreffende Betriebssystem heruntergeladen und installiert. Die folgende Tabelle enthält alle verfügbaren Pakete.

| Paketname | Gilt für | und Beschreibung |
|--------------|----------|-------------|
|mssql-server-extensibility  | Alle Sprachen | Verwendetes Erweiterbarkeitsframework für die Java-Spracherweiterung |
|mssql-server-extensibility-java | Java | Verwendetes Erweiterbarkeitsframework für die Java-Spracherweiterung, enthält außerdem eine unterstützte Java-Runtime |

<a name="RHEL"></a>

## <a name="install-language-extensions"></a>Installieren von Spracherweiterungen

Sie können Spracherweiterungen und Java unter Linux über das Paket **mssql-server-extensibility-java** installieren. Wenn Sie das Paket **mssql-server-extensibility-java** installieren, wird auch automatisch JRE 11 installiert, sofern nicht bereits geschehen. Außerdem wird der JVM-Pfad einer Umgebungsvariablen mit dem Namen „JRE_HOME“ hinzugefügt.

> [!Note]
> Auf einem mit dem Internet verbundenen Server werden Paketabhängigkeiten im Rahmen der Hauptpaketinstallation heruntergeladen und installiert. Wenn Ihr Server nicht mit dem Internet verbunden ist, finden Sie weitere Informationen unter [Offlineeinrichtung](#offline-install).

### <a name="redhat-install-command"></a>Red Hat-Installationsbefehl

Mithilfe des folgenden Befehls können Sie Spracherweiterungen für Java unter Red Hat installieren.

> [!Tip]
> Führen Sie nach Möglichkeit `yum clean all` aus, um vor der Installation Pakete auf dem System zu aktualisieren.

```bash
# Install as root or sudo
sudo yum install mssql-server-extensibility-java
```

<a name="ubuntu"></a>

### <a name="ubuntu-install-command"></a>Ubuntu-Installationsbefehl

Mithilfe des folgenden Befehls können Sie Spracherweiterungen für Java unter Ubuntu installieren.

> [!Tip]
> Führen Sie nach Möglichkeit `apt-get update` aus, um vor der Installation Pakete auf dem System zu aktualisieren. Außerdem verfügen einige Docker-Images von Ubuntu möglicherweise nicht über die HTTPS-Transportoption „apt“. Verwenden Sie `apt-get install apt-transport-https`, um diese zu installieren.

```bash
# Install as root or sudo
sudo apt-get install mssql-server-extensibility-java
```

<a name="suse"></a>

### <a name="suse-install-command"></a>SUSE-Installationsbefehl

Mithilfe des folgenden Befehls können Sie Spracherweiterungen für Java unter SUSE installieren.

```bash
# Install as root or sudo
sudo zypper install mssql-server-extensibility-java
```

## <a name="post-install-config-required"></a>Konfigurieren nach der Installation (erforderlich)

1. Erteilen Sie Berechtigungen unter Linux.

    Wenn Sie externe Bibliotheken verwenden, müssen Sie diesen Schritt nicht ausführen. Es wird empfohlen, externe Bibliotheken für die Arbeit zu verwenden. Informationen zum Erstellen einer externen Bibliothek aus der JAR-Datei finden Sie unter [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

    Wenn Sie keine externen Bibliotheken verwenden, müssen Sie SQL Server Berechtigungen zum Ausführen der Java-Klassen in Ihrer JAR-Datei erteilen.

    Sie können einer JAR-Datei Lese-und Ausführungszugriff gewähren, indem Sie den folgenden **chmod**-Befehl auf diese ausführen. Wenn Sie mit SQL Server arbeiten, empfiehlt es sich, die Klassendateien immer in eine JAR-Datei zu speichern. Informationen zum Erstellen einer JAR-Datei finden Sie unter [Erstellen einer JAR-Datei](https://docs.microsoft.com/sql/language-extensions/how-to/create-a-java-jar-file-from-class-files).

    ```cmd
    chmod ug+rx <MyJarFile.jar>
    ```

    Außerdem müssen Sie „mssql_satellite“ Berechtigungen erteilen, um die JAR-Datei zu lesen oder auszuführen.

    ```cmd
    chown mssql_satellite:mssql_satellite <MyJarFile.jar>
    ```

    Die zusätzliche Konfiguration erfolgt in erster Linie über das Tool [mssql-conf](sql-server-linux-configure-mssql-conf.md).

2. Fügen Sie das MSSQL-Benutzerkonto hinzu, um den SQL Server-Dienst auszuführen. Dies ist erforderlich, wenn Sie das Setup vorher noch nicht ausgeführt haben.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

3. Aktivieren Sie den Zugriff auf ausgehenden Netzwerkdatenverkehr. Der Zugriff auf ausgehenden Netzwerkdatenverkehr ist standardmäßig deaktiviert. Sie können mithilfe des Tools mssql-conf die boolesche Eigenschaft „outboundnetworkaccess“ festlegen, um ausgehende Anforderungen zu aktivieren. Weitere Informationen finden Sie unter [Konfigurieren von SQL Server für Linux mithilfe von mssql-conf](sql-server-linux-configure-mssql-conf.md#mlservices-outbound-access).

   ```bash
   # Run as SUDO or root
   # Enable outbound requests over the network
   sudo /opt/mssql/bin/mssql-conf set extensibility outboundnetworkaccess 1
   ```

4. Starten Sie anschließend das SQL Server-Launchpad und die Datenbank-Engine-Instanz neu, um die aktualisierten Werte aus der INI-Datei zu lesen. Wenn eine Erweiterbarkeitseinstellung geändert wird, werden Sie in einer Neustartmeldung darauf hingewiesen.  

   ```bash
   systemctl restart mssql-launchpadd

   systemctl restart mssql-server.service
   ```

5. Aktivieren Sie die externe Skriptausführung mithilfe von Azure Data Studio oder einem anderen Tool wie SQL Server Management Studio (nur unter Windows), das Transact-SQL ausführt.

   ```bash
   EXEC sp_configure 'external scripts enabled', 1
   RECONFIGURE WITH OVERRIDE
   ```

6. Starten Sie den Dienst `mssql-launchpadd` neu.

7. Für jede Datenbank, in der Sie Spracherweiterungen verwenden möchten, müssen Sie die externe Sprache über den Befehl [CREATE EXTERNAL LANGUAGE](https://docs.microsoft.com/sql/t-sql/statements/create-external-language-transact-sql) registrieren.

## <a name="register-external-language"></a>Registrieren einer externen Sprache

Für jede Datenbank, in der Sie Spracherweiterungen verwenden möchten, müssen Sie die externe Sprache über den Befehl [CREATE EXTERNAL LANGUAGE](https://docs.microsoft.com/sql/t-sql/statements/create-external-language-transact-sql) registrieren.

Im folgenden Beispiel wird die externe Sprache mit dem Namen Java zu einer Datenbank unter SQL Server für Linux hinzugefügt.

```SQL
CREATE EXTERNAL LANGUAGE Java
FROM (CONTENT = N'<path-to-tar.gz>', FILE_NAME = 'javaextension.so');
GO
```

Weitere Informationen finden Sie unter [CREATE EXTERNAL LANGUAGE](https://docs.microsoft.com/sql/t-sql/statements/create-external-language-transact-sql).

## <a name="verify-installation"></a>Überprüfen der Installation

Die Integration von Java-Funktionen umfasst keine Bibliotheken, aber Sie können `grep -r JRE_HOME /etc` ausführen, um die Erstellung der Umgebungsvariablen JAVA_HOME zu bestätigen.

Sie können die Installation überprüfen, indem Sie ein T-SQL-Skript ausführen, das eine gespeicherte Systemprozedur ausführt, die Java aufruft. Für diese Aufgabe benötigen Sie ein Abfragetool. Azure Data Studio ist eine gute Wahl. Andere häufig verwendete Tools wie SQL Server Management Studio oder PowerShell können nur unter Windows verwendet werden. Wenn Sie über einen Windows-Computer mit diesen Tools verfügen, verwenden Sie diesen, um eine Verbindung mit Ihrer Linux-Installation der Datenbank-Engine herzustellen.

<a name="install-all"></a>

## <a name="full-install-of-sql-server-and-language-extensions"></a>Vollständige Installation von SQL Server und Spracherweiterungen

Sie können die Datenbank-Engine und die Spracherweiterungen zusammen installieren und konfigurieren, indem Sie Java-Pakete und -Parameter an einen Befehl anfügen, der wiederum die Datenbank-Engine installiert.

1. Geben Sie eine Befehlszeile an, die die Datenbank-Engine sowie Spracherweiterungsfeatures enthält.

  Sie können Java-Erweiterbarkeit zur Installation einer Datenbank-Engine hinzufügen.

  ```bash
  sudo yum install -y mssql-server mssql-server-extensibility-java 
  ```

3. Akzeptieren Sie die Lizenzbedingungen, und schließen Sie die Konfiguration im Anschluss an die Installation ab. Verwenden Sie hierfür das Tool **mssql-conf**.

  ```bash
  sudo /opt/mssql/bin/mssql-conf setup
  ```

  Sie werden dann aufgefordert, die Lizenzbedingungen für die Datenbank-Engine zu akzeptieren, eine Edition auszuwählen und das Administratorkennwort festzulegen. 

4. Starten Sie den Dienst neu, wenn Sie dazu aufgefordert werden.

  ```bash
  sudo systemctl restart mssql-server.service
  ```

## <a name="unattended-installation"></a>Unbeaufsichtigte Installation

Fügen Sie die Pakete für „mssql-server-extensibility-java“ der Datenbank-Engine über eine [unbeaufsichtigte Installation](https://docs.microsoft.com/sql/linux/sql-server-linux-setup#unattended) hinzu.

<a name="offline-install"></a>


## <a name="offline-installation"></a>Offlineinstallation

Befolgen Sie die Anweisungen zur [Offlineinstallation](sql-server-linux-setup.md#offline), um die Pakete zu installieren. Der nachfolgenden Liste können Sie entnehmen, auf welchen Websites Sie jeweils entsprechende Downloads finden. Laden Sie dann alle nötigen Pakete herunter.

> [!Tip]
> Einige der Paketverwaltungstools umfassen Befehle, mit denen Sie Paketabhängigkeiten ermitteln können. Verwenden Sie für yum `sudo yum deplist [package]`. Verwenden Sie für Ubuntu erst `sudo apt-get install --reinstall --download-only [package name]` und dann `dpkg -I [package name].deb`.

#### <a name="download-site"></a>Downloadsite

Sie können die Pakete unter [https://packages.microsoft.com/](https://packages.microsoft.com/) herunterladen. Alle Pakete für Java werden zusammen mit dem Datenbank-Engine-Paket bereitgestellt. 

#### <a name="redhat7-paths"></a>Red Hat/7-Pfade

|||
|--|----|
| mssql/extensibility-java-Pakete | [https://packages.microsoft.com/rhel/7/mssql-server-preview/](https://packages.microsoft.com/rhel/7/mssql-server-preview/) |

#### <a name="ubuntu1604-paths"></a>Ubuntu/16.04-Pfade

|||
|--|----|
| mssql/extensibility-java-Pakete | [https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/) |

#### <a name="suse12-paths"></a>SUSE/12-Pfade

|||
|--|----|
| mssql/extensibility-java-Pakete | [https://packages.microsoft.com/sles/12/mssql-server-preview/](https://packages.microsoft.com/sles/12/mssql-server-preview/) |

#### <a name="package-list"></a>Paketliste

Je nachdem, welche Erweiterungen Sie verwenden möchten, müssen Sie die für die jeweilige Sprache erforderlichen Pakete herunterladen. Genaue Dateinamen enthalten Plattforminformationen im Suffix, aber die unten aufgeführten Dateinamen sollten genau genug sein, damit Sie herausfinden können, welche Dateien Sie benötigen.

```
# Core packages 
mssql-server-15.0.1000
mssql-server-extensibility-15.0.1000

# Java
mssql-server-extensibility-java-15.0.1000
```

## <a name="limitations"></a>Einschränkungen

+ Die implizite Authentifizierung ist zurzeit nicht unter Linux verfügbar. Das bedeutet, dass Sie über Java-Code, der zu diesem Zeitpunkt ausgeführt wird, keine erneute Verbindung mit dem Server herstellen können, um auf Daten oder andere Ressourcen zuzugreifen.

### <a name="resource-governance"></a>Ressourcengovernance

In Bezug auf die [Ressourcengovernance](../t-sql/statements/create-external-resource-pool-transact-sql.md) besteht zwar zwischen Linux und Windows Parität für externe Ressourcenpools, aber die Statistiken für [sys.dm_resource_governor_external_resource_pools](../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md) haben derzeit unterschiedliche Einheiten unter Linux. 
 
| Spaltenname   | und Beschreibung | Wert unter Linux | 
|---------------|--------------|---------------|
|peak_memory_kb | Der maximale Speicher, der für den Ressourcenpool verwendet wird. | Unter Linux wird diese Statistik dem CGroups-Speichersubsystem entnommen. Dabei lautet der Wert „memory.max_usage_in_bytes“. |
|write_io_count | Die Gesamtanzahl der E/A-Schreibvorgänge, die seit dem Zurücksetzen der Resource Governor-Statistiken ausgegeben wurden. | Unter Linux wird diese Statistik dem CGroups-Speichersubsystem „blkio“ entnommen. Dabei lautet der Wert der Zeile für die Schreibvorgänge „blkio.throttle.io_serviced“. | 
|read_io_count | Die Gesamtanzahl der E/A-Lesevorgänge, die seit dem Zurücksetzen der Resource Governor-Statistiken ausgegeben wurden. | Unter Linux wird diese Statistik dem CGroups-Speichersubsystem „blkio“ entnommen. Dabei lautet der Wert der Zeile für die Lesevorgänge „blkio.throttle.io_serviced“. | 
|total_cpu_kernel_ms | Die kumulierte CPU-Benutzerkernelzeit in Millisekunden, seitdem die Resource Governor-Statistiken zurückgesetzt wurden. | Unter Linux wird diese Statistik dem CGroups-Speichersubsystem „cpuacct“ entnommen. Dabei lautet der Wert der Zeile für den Benutzer „cpuacct.stat“. |  
|total_cpu_user_ms | Die kumulierte CPU-Benutzerzeit in Millisekunden, seitdem die Resource Governor-Statistiken zurückgesetzt wurden.| Unter Linux wird diese Statistik dem CGroups-Speichersubsystem „cpuacct“ entnommen. Dabei lautet der Systemzeilenwert „cpuacct.stat“. | 
|active_processes_count | Die Anzahl externer Prozesse, die zum Zeitpunkt der Anforderung ausgeführt werden.| Unter Linux wird diese Statistik dem CGroups-Speichersubsystem „pids“ entnommen. Dabei lautet der Wert „pids.current“. | 

## <a name="next-steps"></a>Nächste Schritte

Java-Entwickler können mit einigen einfachen Beispielen loslegen und die Grundlagen der Funktionen von Java unter SQL Server kennenlernen. Informationen zu den nächsten Schritten finden Sie unter den folgenden Links:

+ [Tutorial: Reguläre Ausdrücke in Java](../language-extensions/tutorials/search-for-string-using-regular-expressions-in-java.md)