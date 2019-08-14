---
title: Leitfaden für die Installation von SQL Server unter Linux
titleSuffix: SQL Server
description: Installieren, aktualisieren und deinstallieren Sie SQL Server unter Linux. In diesem Artikel erhalten Sie Informationen zu Online-, Offline- und unbeaufsichtigten Szenarios.
author: VanMSFT
ms.author: vanto
ms.date: 05/28/2019
ms.topic: conceptual
ms.prod: sql
ms.custom: sqlfreshmay19
ms.technology: linux
ms.assetid: 565156c3-7256-4e63-aaf0-884522ef2a52
ms.openlocfilehash: 7f4b2aa37b20cceaa3269527c95bfa97a2daa311
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68032433"
---
# <a name="installation-guidance-for-sql-server-on-linux"></a>Leitfaden für die Installation von SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Artikel erfahren Sie, wie Sie SQL Server 2017 und SQL Server 2019 (Vorschauversion) unter Linux installieren, aktualisieren und deinstallieren.

> [!TIP]
> Dieser Leitfaden umfasst mehrere Bereitstellungsszenarios. Eine ausführliche Installationsanleitung mit allen erforderlichen Schritten finden Sie in den jeweiligen Schnellstarts:
> - [RHEL-Schnellstart](quickstart-install-connect-red-hat.md)
> - [SLES-Schnellstart](quickstart-install-connect-suse.md)
> - [Ubuntu-Schnellstart](quickstart-install-connect-ubuntu.md)
> - [Docker-Schnellstart](quickstart-install-connect-docker.md)

Antworten auf häufig gestellte Fragen finden Sie unter [SQL Server on Linux FAQ (Häufig gestellte Fragen zu SQL Server unter Linux)](../linux/sql-server-linux-faq.md).

## <a id="supportedplatforms"></a> Unterstützte Plattformen

SQL Server 2017 wird auf Red Hat Enterprise Linux (RHEL), SUSE Linux Enterprise Server (SLES) und Ubuntu unterstützt. Es wird auch als Docker-Image unterstützt, das in der Docker-Engine unter Linux oder in Docker für Windows/Mac ausgeführt werden kann.

| Platform | Unterstützte Version(en) | Herunterladen
|-----|-----|-----
| **Red Hat Enterprise Linux** | 7.3, 7.4, 7.5, 7.6 | [RHEL 7.6 herunterladen](https://access.redhat.com/products/red-hat-enterprise-linux/evaluation)
| **SUSE Linux Enterprise Server** | v12 SP2 | [SLES v12 SP2 herunterladen](https://www.suse.com/products/server)
| **Ubuntu** | 16.04 | [Ubuntu 16.04 herunterladen](http://releases.ubuntu.com/xenial/)
| **Docker-Engine** | ab 1.8 | [Docker herunterladen](https://www.docker.com/get-started)

Microsoft unterstützt auch die Bereitstellung und Verwaltung von SQL Server-Containern mit OpenShift und Kubernetes.

> [!NOTE]
> SQL Server wird unter Linux für die oben aufgeführten Verteilungen getestet und unterstützt. Wenn Sie SQL Server unter einem nicht unterstützten Betriebssystem installieren möchten, finden Sie Informationen zu den Auswirkungen auf die Unterstützung unter [Technical support policy for Microsoft SQL Server (Richtlinie für den technischen Support für Microsoft SQL Server)](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server) im Abschnitt **Supportrichtlinie**.

## <a id="system"></a> Systemanforderungen

Für SQL Server 2017 gelten die folgenden Systemanforderungen unter Linux:

|||
|-----|-----|
| **Speicher** | 2 GB |
| **Dateisystem** | **XFS** oder **EXT4** (andere Dateisysteme wie z. B. **BTRFS** werden nicht unterstützt) |
| **Speicherplatz** | 6 GB |
| **Prozessorgeschwindigkeit** | 2 GHz |
| **Prozessorkerne** | 2 Kerne |
| **Prozessortyp** | Nur x64-kompatibel |

Wenn Sie **NFS-Remotefreigaben (Network File System)** in der Produktion verwenden, beachten Sie die folgenden Supportanforderungen:

- Verwenden Sie NFS in der Version **4.2 oder höher**. Ältere NFS-Versionen unterstützen nicht die erforderlichen Funktionen, wie das Erstellen von Fallocate- oder Sparsedateien, die häufig in modernen Dateisystemen enthalten sind.
- Verwenden Sie nur die Verzeichnisse vom Typ **/var/opt/mssql** in der NFS-Bereitstellung. Andere Dateien, wie z. B. die SQL Server-Systembinärdateien, werden nicht unterstützt.
- Stellen Sie sicher, dass NFS-Clients beim Einbinden der Remotefreigabe die Option „NOLOCK“ verwenden.

## <a id="repositories"></a> Konfigurieren von Quellrepositorys

Beim Installieren oder Aktualisieren von SQL Server erhalten Sie die aktuelle SQL Server-Version aus Ihrem konfigurierten Microsoft-Repository. In den Schnellstarts wird das **CU**-Repository mit dem kumulativen Update für SQL Server 2017 verwendet. Sie können stattdessen jedoch auch das **GDR**-Repository oder das **Preview (vNext)** -Repository konfigurieren. Weitere Informationen zu Repositorys und deren Konfiguration finden Sie unter [Configure repositories for SQL Server on Linux (Konfigurieren von Repository für SQL Server unter Linux)](sql-server-linux-change-repo.md).

## <a id="platforms"></a> Installieren von SQL Server 2017

Sie können SQL Server 2017 unter Linux über die Befehlszeile installieren. Eine ausführliche Anleitung mit den einzelnen Schritten finden Sie jeweils unter den folgenden Schnellstarts:

- [Installieren unter Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installieren unter SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installation unter Ubuntu](quickstart-install-connect-ubuntu.md)
- [Ausführen unter Docker](quickstart-install-connect-docker.md)
- [Provision a SQL VM in Azure (Bereitstellen einer SQL-VM in Azure)](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=/sql/toc/toc.json)

Nach der Installation sollten Sie zusätzliche Konfigurationsänderungen vornehmen, um eine optimale Leistung zu erzielen. Weitere Informationen finden Sie unter [Performance best practices and configuration guidelines for SQL Server on Linux (Bewährte Methoden für die Leistung und Konfigurationsrichtlinien für SQL Server unter Linux)](sql-server-linux-performance-best-practices.md).

## <a id="sqlvnext"></a> Installieren von SQL Server 2019 (Vorschauversion)

Sie können SQL Server 2019 (Vorschauversion) unter Linux ebenfalls über die Links zu den Schnellstarts im vorherigen Abschnitt installieren. Dabei müssen Sie jedoch anstelle des **CU**-Repositorys das **Preview (vNext)** -Repository registrieren. In den Schnellstarts finden Sie Anweisungen hierzu.  

## <a id="upgrade"></a> Aktualisieren von SQL Server

Wenn Sie das Paket **mssql-server** auf die neueste Version aktualisieren möchten, verwenden Sie je nach Plattform einen der folgenden Befehle:

| Platform | Befehl(e) für das Paketupdate |
|-----|-----|
| RHEL | `sudo yum update mssql-server` |
| SLES | `sudo zypper update mssql-server` |
| Ubuntu | `sudo apt-get update`<br/>`sudo apt-get install mssql-server` |

Mit diesen Befehlen laden Sie das neueste Paket herunter, und die Binärdateien unter `/opt/mssql/` werden ersetzt. Benutzergenerierte Datenbanken und Systemdatenbanken sind von diesem Vorgang nicht betroffen.

> [!TIP]
> Wenn Sie zuerst [Ihr konfiguriertes Repository ändern](sql-server-linux-change-repo.md), wird mit dem Befehl **update** möglicherweise Ihre SQL Server-Version aktualisiert. Dies ist jedoch nur möglich, wenn der Upgradepfad zwischen den Repositorys unterstützt wird.

## <a id="rollback"></a> Zurücksetzen von SQL Server

Wenn Sie SQL Server auf eine frühere Version zurücksetzen oder herabstufen möchten, führen Sie die folgenden Schritte aus:

1. Ermitteln Sie die Versionsnummer des SQL Server-Pakets, auf das Sie herabstufen möchten. Eine Liste der Paketnummern finden Sie in den [Versionshinweisen](../linux/sql-server-linux-release-notes.md).

1. Führen Sie ein Downgrade auf eine frühere Version von SQL Server aus. Ersetzen Sie `<version_number>` in den folgenden Befehlen durch die in Schritt 1 ermittelte Versionsnummer von SQL Server.

   | Platform | Befehl(e) für das Paketupdate |
   |-----|-----|
   | RHEL | `sudo yum downgrade mssql-server-<version_number>.x86_64` |
   | SLES | `sudo zypper install --oldpackage mssql-server=<version_number>` |
   | Ubuntu | `sudo apt-get install mssql-server=<version_number>`<br/>`sudo systemctl start mssql-server` |

> [!NOTE]
> Sie können SQL Server nur auf eine Version innerhalb derselben Hauptversion, wie z. B. SQL Server 2017, herabstufen.

## <a id="versioncheck"></a> Überprüfen der installierten Version von SQL Server

Gehen Sie zum Überprüfen Ihrer aktuellen Version und Edition von SQL Server unter Linux folgendermaßen vor:

1. Installieren Sie die [SQL Server-Befehlszeilentools](sql-server-linux-setup-tools.md), falls diese noch nicht installiert sind.

1. Führen Sie mit **sqlcmd** einen Transact-SQL-Befehl aus, der Ihre Version und Edition von SQL Server anzeigt.

   ```bash
   sqlcmd -S localhost -U SA -Q 'select @@VERSION'
   ```

## <a id="uninstall"></a> Deinstallieren von SQL Server

Wenn Sie das Paket **mssql-server** unter Linux entfernen möchten, verwenden Sie je nach Plattform einen der folgenden Befehle:

| Platform | Befehl(e) zum Entfernen des Pakets |
|-----|-----|
| RHEL | `sudo yum remove mssql-server` |
| SLES | `sudo zypper remove mssql-server` |
| Ubuntu | `sudo apt-get remove mssql-server` |

Durch Entfernen des Pakets werden die generierten Datenbankdateien nicht automatisch gelöscht. Wenn Sie die Datenbankdateien löschen möchten, verwenden Sie den folgenden Befehl:

```bash
sudo rm -rf /var/opt/mssql/
```

## <a id="unattended"></a> Unbeaufsichtigtes Installieren

Gehen Sie für eine unbeaufsichtigte Installation folgendermaßen vor:

- Führen Sie die ersten Schritte der [Schnellstarts](#platforms) aus, mit denen die Repositorys registriert und SQL Server installiert wird.
- Legen Sie beim Ausführen von `mssql-conf setup` [Umgebungsvariablen](sql-server-linux-configure-environment-variables.md) fest, und verwenden Sie die Option `-n` (keine Aufforderung).

Im folgenden Beispiel wird die Developer Edition von SQL Server mit der Umgebungsvariablen **MSSQL_PID** konfiguriert. Zudem werden die Lizenzbedingungen akzeptiert (**ACCEPT_EULA**) und das SA-Benutzerkennwort festgelegt (**MSSQL_SA_PASSWORD**). Mit dem Parameter `-n` wird eine unangekündigte Installation durchgeführt, bei der die Konfigurationswerte aus den Umgebungsvariablen abgerufen werden.

```bash
sudo MSSQL_PID=Developer ACCEPT_EULA=Y MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' /opt/mssql/bin/mssql-conf -n setup
```

Sie können auch ein Skript für weitere Aktionen erstellen. So können beispielsweise weitere SQL Server-Pakete installiert werden.

Ein ausführliches Beispielskript finden Sie in den folgenden Beispielen:

- [Red Hat unattended installation script (Skript für die unbeaufsichtigte Installation von Red Hat)](sample-unattended-install-redhat.md)
- [SUSE unattended installation script (Skript für die unbeaufsichtigte Installation von SUSE)](sample-unattended-install-suse.md)
- [Ubuntu unattended installation script (Skript für die unbeaufsichtigte Installation von Ubuntu)](sample-unattended-install-ubuntu.md)

## <a id="offline"></a> Offlineinstallation

Wenn Ihr Linux-Computer keinen Zugriff auf die Onlinerepositorys hat, die in den [Schnellstarts](#platforms) verwendet werden, können Sie die Paketdateien direkt herunterladen. Diese Pakete befinden sich im Microsoft-Repository [https://packages.microsoft.com](https://packages.microsoft.com).

> [!TIP]
> Wenn Sie die Installation mithilfe der Schritte in den Schnellstarts erfolgreich abgeschlossen haben, müssen Sie das oder die SQL Server-Pakete nicht herunterladen oder manuell installieren. Dieser Abschnitt betrifft nur das Offlineszenario.

1. **Laden Sie das Paket für die Datenbank-Engine für Ihre Plattform herunter**: Downloadlinks für die Pakete finden Sie in den [Versionshinweisen](../linux/sql-server-linux-release-notes.md) im Abschnitt zu den Paketdetails.

1. **Verschieben Sie das heruntergeladene Paket auf Ihren Linux-Computer**: Wenn Sie einen anderen Computer zum Herunterladen der Pakete verwendet haben, stellt der Befehl **scp** eine Möglichkeit dar, die Pakete auf Ihren Linux-Computer zu verschieben.

1. **Installieren Sie das Paket für die Datenbank-Engine**: Verwenden Sie je nach Plattform einen der folgenden Befehle. Ersetzen Sie den Dateinamen des Pakets in diesem Beispiel durch den genauen Namen des Pakets, das Sie heruntergeladen haben.

   | Platform | Befehl zur Paketinstallation |
   |-----|-----|
   | RHEL | `sudo yum localinstall mssql-server_versionnumber.x86_64.rpm` |
   | SLES | `sudo zypper install mssql-server_versionnumber.x86_64.rpm` |
   | Ubuntu | `sudo dpkg -i mssql-server_versionnumber_amd64.deb` |

    > [!NOTE]
    > Sie können zur Installation der RPM-Pakete (RHEL und SLES) auch den Befehl `rpm -ivh` verwenden. Mit den Befehlen in der vorherigen Tabelle werden jedoch automatisch Abhängigkeiten installiert, sofern sie in genehmigten Repositorys verfügbar sind.

1. **Lösen Sie fehlende Abhängigkeiten auf**: Zu diesem Zeitpunkt fehlen möglicherweise Abhängigkeiten. Falls nicht, können Sie diesen Schritt überspringen. Wenn Sie unter Ubuntu Zugriff auf genehmigte Repositorys mit diesen Abhängigkeiten haben, ist die einfachste Lösung die Verwendung des Befehls `apt-get -f install`. Mit diesem Befehl wird auch die Installation von SQL Server abgeschlossen. Verwenden Sie zum manuellen Überprüfen von Abhängigkeiten je nach Plattform einen der folgenden Befehle:

   | Platform | Befehl zum Auflisten von Abhängigkeiten |
   |-----|-----|
   | RHEL | `rpm -qpR mssql-server_versionnumber.x86_64.rpm` |
   | SLES | `rpm -qpR mssql-server_versionnumber.x86_64.rpm` |
   | Ubuntu | `dpkg -I mssql-server_versionnumber_amd64.deb` |

   Wenn Sie die fehlenden Abhängigkeiten aufgelöst haben, versuchen Sie erneut, das Paket „mssql-server“ zu installieren.

1. **Schließen Sie das Setup von SQL Server ab**: Verwenden Sie dazu den Befehl **mssql-conf**.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

## <a name="licensing-and-pricing"></a>Lizenzierung und Preise

Die SQL Server-Lizenzierung für Linux und Windows ist identisch. Weitere Informationen zur Lizenzierung und den Preisen von SQL Server finden Sie unter [Lizenzierung von SQL Server](https://www.microsoft.com/sql-server/sql-server-2017-pricing).

## <a name="optional-sql-server-features"></a>Optionale SQL Server-Funktionen

Nach der Installation können Sie optionale SQL Server-Funktionen installieren oder aktivieren, wie etwa:

- [SQL Server-Befehlszeilentools](sql-server-linux-setup-tools.md)
- [SQL Server-Agent](sql-server-linux-setup-sql-agent.md)
- [SQL Server-Volltextsuche](sql-server-linux-setup-full-text-search.md)
- [Machine Learning Services (R, Python)](sql-server-linux-setup-machine-learning.md)
- [SQL Server Integration Services](sql-server-linux-setup-ssis.md)

[!INCLUDE[Get Help Options](../includes/paragraph-content/get-help-options.md)]

> [!TIP]
> Antworten auf häufig gestellte Fragen finden Sie unter [SQL Server on Linux FAQ (Häufig gestellte Fragen zu SQL Server unter Linux)](sql-server-linux-faq.md).
