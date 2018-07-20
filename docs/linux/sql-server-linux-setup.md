---
title: Installationsanleitung für SQL Server 2017 unter Linux | Microsoft-Dokumentation
description: Installieren, aktualisieren und Deinstallieren von SQL Server unter Linux. In diesem Artikel werden online, offline und unbeaufsichtigte Szenarios behandelt.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/06/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 565156c3-7256-4e63-aaf0-884522ef2a52
ms.openlocfilehash: a2b725caa90ef277394637e4c65cfe5f241c1cc2
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39102428"
---
# <a name="installation-guidance-for-sql-server-on-linux"></a>Installationsanleitung für SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dieser Artikel enthält Anleitungen zum Installieren, aktualisieren und Deinstallieren von SQL Server 2017 unter Linux.

> [!TIP]
> Dieses Handbuch coves verschiedene Bereitstellungsszenarien. Wenn Sie nur ausführliche installationsanweisungen suchen, wechseln Sie auf einen der Schnellstarts:
> - [RHEL-Schnellstart](quickstart-install-connect-red-hat.md)
> - [SLES-Schnellstart](quickstart-install-connect-suse.md)
> - [Ubuntu-Schnellstart](quickstart-install-connect-ubuntu.md)
> - [Schnellstartanleitung für docker](quickstart-install-connect-docker.md)

Antworten auf häufig gestellte Fragen finden Sie unter den [SQL Server unter Linux – häufig gestellte Fragen](../linux/sql-server-linux-faq.md).

## <a id="supportedplatforms"></a> Unterstützte Plattformen

SQL Server 2017 wird unter Ubuntu, SUSE Linux Enterprise Server (SLES) und Red Hat Enterprise Linux (RHEL) unterstützt. Es wird auch als Docker-Image, unterstützt die Docker-Engine unter Linux oder Docker für Windows/Mac ausführen können

| Platform | Unterstützte Versionen | Herunterladen
|-----|-----|-----
| **Red Hat Enterprise Linux** | 7.3 oder 7.4 | [Abrufen von RHEL 7.4](http://access.redhat.com/products/red-hat-enterprise-linux/evaluation)
| **SUSE Linux Enterprise Server** | v12 SP2 | [SLES v12 SP2-Download](https://www.suse.com/products/server)
| **Ubuntu** | 16.04 | [Abrufen von Ubuntu 16.04](http://www.ubuntu.com/download/server)
| **Docker-Engine** | 1.8+ | [Docker abrufen](http://www.docker.com/products/overview)

Microsoft unterstützt auch bereitstellen und Verwalten von SQL Server-Containern mit OpenShift und Kubernetes.

> [!NOTE]
> SQL Server wird getestet und für die zuvor aufgeführten Distributionen unter Linux unterstützt. Wenn Sie SQL Server auf einem nicht unterstützten Betriebssystem installieren möchten, lesen Sie bitte die **Supportrichtlinie** im Abschnitt der [technischer Support-Richtlinie für Microsoft SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server) zu verstehen, die Unterstützung Auswirkungen auf.

## <a id="system"></a> Systemanforderungen

SQL Server 2017 hat die folgenden Systemanforderungen für Linux:

|||
|-----|-----|
| **Speicher** | 2 GB |
| **Dateisystem** | **XFS** oder **EXT4** (andere Dateisysteme, z. B. **BTRFS**, werden nicht unterstützt) |
| **Speicherplatz auf dem Datenträger** | 6 GB |
| **Prozessorgeschwindigkeit** | 2 GHz |
| **Prozessorkerne** | 2 Kerne |
| **Prozessortyp** | nur X64-kompatiblen |

Bei Verwendung von **Network File System (NFS)** Remotefreigaben in der Produktion, beachten Sie die folgenden Anforderungen:

- Verwenden Sie NFS-Version **4.2 oder höher**. Ältere Versionen von NFS unterstützen keine erforderlichen Features, wie z. B. Fallocate und Datei mit geringer Dichte erstellen, die für moderne Dateisysteme.
- Suchen Sie nur die **/var/opt/mssql** Verzeichnisse auf die NFS-Bereitstellung. Andere Dateien, z. B. die SQL Server-System-Binärdateien werden nicht unterstützt.
- Stellen Sie sicher, dass die NFS-Clients die Option "Nolock" verwenden, beim Einbinden der Freigabe auf des Remotecomputer.

## <a id="repositories"></a> Konfigurieren von Quellcode-Repositorys

Beim Installieren oder Aktualisieren von SQL Server, erhalten Sie die neueste Version von SQL Server 2017 aus dem Repository Ihrer konfigurierten Microsoft. Verwenden Sie die Schnellstarts der **kumulativen Update (CU)** Repository. Sie können aber stattdessen konfigurieren die **GDR** Repository. Weitere Informationen für Repositorys und deren Konfiguration finden Sie unter [Repositorys für SQL Server unter Linux konfigurieren](sql-server-linux-change-repo.md).

> [!IMPORTANT]
> Wenn Sie eine CTP-Version oder die RC-Version von SQL Server 2017 bereits installiert haben, müssen Sie entfernen das Repository für die Vorschau und registrieren eine allgemeine Verfügbarkeit (GA) eine. Weitere Informationen finden Sie unter [Repositorys für SQL Server unter Linux konfigurieren](sql-server-linux-change-repo.md).

## <a id="platforms"></a> Installieren von SQL Server

Sie können SQL Server unter Linux über die Befehlszeile installieren. Anweisungen hierzu finden Sie in einem der folgenden schnellstartanleitungen:

- [Installieren Sie unter Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installieren Sie unter SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installieren unter Ubuntu](quickstart-install-connect-ubuntu.md)
- [Führen unter Docker aus](quickstart-install-connect-docker.md)
- [Provision a SQL VM in Azure (Bereitstellen einer SQL-VM in Azure)](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

Sollten Sie nach der Installation zusätzliche konfigurationsänderungen für eine optimale Leistung aus. Weitere Informationen finden Sie unter [bewährte Methoden für Leistung und von Konfigurationsrichtlinien für das SQL Server unter Linux](sql-server-linux-performance-best-practices.md).

## <a id="upgrade"></a> Aktualisieren Sie SQLServer

Beim Aktualisieren der **Mssql-Server** Paket auf die neueste Version, verwenden Sie eine der folgenden Befehle basierend auf Ihrer Plattform:

| Platform | Paket-Update-Befehle |
|-----|-----|
| RHEL | `sudo yum update mssql-server` |
| SLES | `sudo zypper update mssql-server` |
| Ubuntu | `sudo apt-get update`<br/>`sudo apt-get install mssql-server` |

Diese Befehle Laden Sie das neueste Paket herunter, und Ersetzen Sie die Binärdateien befindet sich im `/opt/mssql/`. Der vom Benutzer generierte Datenbanken und Datenbanken sind von diesem Vorgang nicht betroffen.

## <a id="rollback"></a> Rollback-SQL-Server

Verwenden Sie zum Zurücksetzen oder Herabstufen von SQL Server auf einer früheren Version die folgenden Schritte aus:

1. Identifizieren Sie die Versionsnummer für das SQL Server-Paket, die, dem Sie auf herabstufen möchten. Eine Liste der Paket-Zahlen, finden Sie unter den [Anmerkungen zu dieser Version](sql-server-linux-release-notes.md).

1. Ein Downgrade durchführen Sie, um eine frühere Version von SQL Server. Ersetzen Sie in den folgenden Befehlen `<version_number>` mit der SQL Server-Versionsnummer, die Sie in Schritt 1 identifiziert haben.

   | Platform | Paket-Update-Befehle |
   |-----|-----|
   | RHEL | `sudo yum downgrade mssql-server-<version_number>.x86_64` |
   | SLES | `sudo zypper install --oldpackage mssql-server=<version_number>` |
   | Ubuntu | `sudo apt-get install mssql-server=<version_number>`<br/>`sudo systemctl start mssql-server` |

> [!NOTE]
> Es wird nur für ein Downgrade auf eine Version innerhalb derselben Hauptversion, z. B. SQL Server 2017 unterstützt.

## <a id="versioncheck"></a> Überprüfen Sie die installierte Version von SQL Server

Um Ihre aktuelle Version und Edition von SQL Server unter Linux zu überprüfen, verwenden Sie das folgende Verfahren aus:

1. Wenn noch nicht installiert, installieren Sie die [SQL Server-Befehlszeilentools](sql-server-linux-setup-tools.md).

1. Verwendung **Sqlcmd** einen Transact-SQL-Befehl aus, in dem die SQL Server-Version und Edition angezeigt.

   ```bash
   sqlcmd -S localhost -U SA -Q 'select @@VERSION'
   ```

## <a id="uninstall"></a> Deinstallieren von SQLServer

So entfernen Sie die **Mssql-Server** für Linux-Paket, verwenden Sie eine der folgenden Befehle basierend auf Ihrer Plattform:

| Platform | Paket entfernen Befehle |
|-----|-----|
| RHEL | `sudo yum remove mssql-server` |
| SLES | `sudo zypper remove mssql-server` |
| Ubuntu | `sudo apt-get remove mssql-server` |

Das Entfernen des Pakets werden die generierten Dateien nicht gelöscht werden. Wenn Sie die Datenbankdateien löschen möchten, verwenden Sie den folgenden Befehl aus:

```bash
sudo rm -rf /var/opt/mssql/
```

## <a id="unattended"></a> Unbeaufsichtigte Installation

Sie können eine unbeaufsichtigte Installation wie folgt ausführen:

- Führen Sie die ersten in Schritte der [Schnellstarts](#platforms) registrieren die Repositorys, und Installieren von SQL Server.
- Beim Ausführen von `mssql-conf setup`legen [Umgebungsvariablen](sql-server-linux-configure-environment-variables.md) und verwenden Sie die `-n` (keine Aufforderung) Option.

Im folgenden Beispiel wird die Developer-Edition von SQL Server mit der **MSSQL_PID** -Umgebungsvariablen angegeben. Außerdem akzeptiert den Endbenutzer-Lizenzvertrag (**ACCEPT_EULA**) und legt das Kennwort des SA-Benutzers (**MSSQL_SA_PASSWORD**). Die `-n` Parameter führt eine unangekündigte Installation, in denen die Konfigurationswerte werden aus den Umgebungsvariablen abgerufen.

```bash
sudo MSSQL_PID=Developer ACCEPT_EULA=Y MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' /opt/mssql/bin/mssql-conf -n setup
```

Sie können auch ein Skript erstellen, die andere Aktionen ausführt. Beispielsweise können Sie andere SQL Server-Pakete installieren.

Eine ausführlichere Beispielskript finden Sie unter den folgenden Beispielen:

- [Red Hat-Skript für die unbeaufsichtigte Installation](sample-unattended-install-redhat.md)
- [SUSE-Skript für die unbeaufsichtigte Installation](sample-unattended-install-suse.md)
- [Ubuntu Skript für die unbeaufsichtigte Installation](sample-unattended-install-ubuntu.md)

## <a id="offline"></a> Offline-Installation

Wenn Ihr Linux-Computer Zugriff auf die onlinerepositorys verwendet keinen der [Schnellstarts](#platforms), Sie können die Paketdateien direkt herunterladen. Diese Pakete befinden sich im Microsoft-Repository [ https://packages.microsoft.com ](https://packages.microsoft.com).

> [!TIP]
> Wenn Sie sich mit den Schritten in den Schnellstarts zum erfolgreich installiert, müssen Sie nicht herunterladen oder die SQL Server-Pakete manuell installieren. Dieser Abschnitt gilt nur für das Offlineszenario.

1. **Das Datenbank-Engine-Paket für Ihre Plattform herunterladen**. Finden Sie Links für Paketdownloads im Detailabschnitt des Pakets die [– Anmerkungen zu dieser](sql-server-linux-release-notes.md).

1. **Verschieben Sie das heruntergeladene Paket in Ihrem Linux-Computer**. Wenn Sie einen anderen Computer verwendet, um die Pakete herunterzuladen, ist eine Möglichkeit, verschieben Sie die Pakete auf Ihren Linux-Computer mit der **scp** Befehl.

1. **Installieren Sie das Datenbank-Engine-Paket**. Verwenden Sie eine der folgenden Befehle basierend auf der Plattform. Ersetzen Sie den Namen des Paket-Datei in diesem Beispiel, mit dem genauen Namen, die, den Sie heruntergeladen haben.

   | Platform | Befehl "Install Package" |
   |-----|-----|
   | RHEL | `sudo yum localinstall mssql-server_versionnumber.x86_64.rpm` |
   | SLES | `sudo zypper install mssql-server_versionnumber.x86_64.rpm` |
   | Ubuntu | `sudo dpkg -i mssql-server_versionnumber_amd64.deb` |

    > [!NOTE]
    > Sie können auch die RPM-Pakete (RHEL und SLES) installieren, mit der `rpm -ivh` -Befehl, aber die Befehle in der vorherigen Tabelle installieren Abhängigkeiten automatisch, wenn verfügbar, über Repositorys genehmigt.

1. **Beheben Sie fehlende Abhängigkeiten**: Sie müssen möglicherweise fehlende Abhängigkeiten an diesem Punkt. Wenn dies nicht der Fall ist, können Sie diesen Schritt überspringen. Unter Ubuntu, wenn Sie Zugriff auf genehmigte Repositorys, die mit diesen Abhängigkeiten, haben die einfachste Lösung ist die Verwendung der `apt-get -f install` Befehl. Dieser Befehl schließt auch die Installation von SQL Server. Um Abhängigkeiten manuell zu überprüfen, verwenden Sie die folgenden Befehle aus:

   | Platform | Abhängigkeiten auflisten (Befehl) |
   |-----|-----|
   | RHEL | `rpm -qpR mssql-server_versionnumber.x86_64.rpm` |
   | SLES | `rpm -qpR mssql-server_versionnumber.x86_64.rpm` |
   | Ubuntu | `dpkg -I mssql-server_versionnumber_amd64.deb` |

   Versuchen Sie nach dem Beheben der fehlenden Abhängigkeiten ein, um das Paket für die Mssql-Server erneut installieren.

1. **Führen Sie das SQL Server-Setup**. Verwendung **Mssql-Conf** um das SQL Server-Setup abzuschließen:

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

## <a name="optional-sql-server-features"></a>Optionale SQL Server-Funktionen

Nach der Installation können Sie auch installieren oder aktivieren Optionaler Features von SQL Server.

- [SQL Server-Befehlszeilentools](sql-server-linux-setup-tools.md)
- [SQL Server-Agent](sql-server-linux-setup-sql-agent.md)
- [SQL Server-Volltextsuche](sql-server-linux-setup-full-text-search.md)
- [SQL Server Integration Services (Ubuntu)](sql-server-linux-setup-ssis.md)

[!INCLUDE[Get Help Options](../includes/paragraph-content/get-help-options.md)]

> [!TIP]
> Antworten auf häufig gestellte Fragen finden Sie unter den [SQL Server unter Linux – häufig gestellte Fragen](sql-server-linux-faq.md).
