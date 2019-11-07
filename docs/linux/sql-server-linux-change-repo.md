---
title: Konfigurieren von Linux-Repositorys für SQL Server 2017 und 2019
description: Überprüfen und konfigurieren Sie Quellrepositorys für SQL Server 2019 und SQL Server 2017 unter Linux. Das Quellrepository wirkt sich auf die Version von SQL Server aus, die während der Installation und beim Upgrade verwendet wird.
author: VanMSFT
ms.author: vanto
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
zone_pivot_groups: ld2-linux-distribution
ms.openlocfilehash: b71078e0d1d6af9bd35f248e8bbc324ac5c0e570
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73531329"
---
# <a name="configure-repositories-for-installing-and-upgrading-sql-server-on-linux"></a>Konfigurieren von Repositorys zum Installieren und Upgraden von SQL Server für Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

::: zone pivot="ld2-rhel"
In diesem Artikel wird beschrieben, wie das richtige Repository für die Installation und das Upgrade von SQL Server 2017 und SQL Server 2019 unter Linux konfiguriert wird. Ganz oben in Ihrer aktuellen Auswahl steht **Red Hat (RHEL)** .
::: zone-end

::: zone pivot="ld2-sles"
In diesem Artikel wird beschrieben, wie das richtige Repository für die Installation und das Upgrade von SQL Server 2017 und SQL Server 2019 unter Linux konfiguriert wird. Ganz oben in Ihrer aktuellen Auswahl steht **SUSE (SLES)** .
::: zone-end

::: zone pivot="ld2-ubuntu"
In diesem Artikel wird beschrieben, wie das richtige Repository für die Installation und das Upgrade von SQL Server 2017 und SQL Server 2019 unter Linux konfiguriert wird. Ganz oben in Ihrer aktuellen Auswahl steht **Ubuntu**.
::: zone-end

> [!TIP]
> SQL Server 2019 ist jetzt verfügbar. Wenn Sie es ausprobieren möchten, verwenden Sie diesen Artikel zum Konfigurieren des neuen **mssql-server-2019**-Repositorys. Führen Sie anschließend die Installation mithilfe der Anweisungen im [Installationshandbuch](sql-server-linux-setup.md) durch.

## <a id="repositories"></a> Repositorys

Wenn Sie SQL Server für Linux installieren, müssen Sie ein Microsoft-Repository konfigurieren. Dieses Repository dient zum Abrufen des Datenbank-Engine-Pakets **mssql-server** und der zugehörigen SQL Server-Pakete. Derzeit gibt es im Wesentlichen fünf Repositorys:

| Repository | Name | und Beschreibung |
|---|---|---|
| **2019** | **mssql-server-2019** | Repository zum kumulativen Update von SQL Server 2019 |
| **2019 GDR** | **mssql-server-2019-gdr** | Repository zur allgemeinen Vertriebsversion von SQL Server 2019, nur für kritische Updates |
| **2019 Preview** | **mssql-server-preview** | Repository zur Vorschauversion von SQL Server 2019 und RC |
| **2017** | **mssql-server-2017** | Repository zum kumulativen SQL Server 2017-Update (Cumulative Update, CU) |
| **2017 GDR** | **mssql-server-2017-gdr** | Repository zur allgemeinen Vertriebsversion (General Distribution Release, GDR) von SQL Server 2017, nur für kritische Updates |

## <a id="cuversusgdr"></a> Kumulatives Update und allgemeine Vertriebsversion im Vergleich

Beachten Sie, dass es für jede Vertriebsversion im Wesentlichen zwei Arten von Repositorys gibt:

- **Kumulative Updates (Cumulative Updates, CU)** : Das CU-Repository enthält Pakete für das SQL Server-Basisrelease sowie sämtliche Fehlerbehebungen und Verbesserungen seit diesem Release. Kumulative Updates gelten für eine bestimmte Releaseversion wie SQL Server 2019. Sie werden in regelmäßigen Abständen veröffentlicht.

- **Allgemeine Vertriebsversion (General Distribution Release, GDR)** Das GDR-Repository enthält Pakete für das SQL Server-Basisrelease sowie ausschließlich kritische Fixes und Sicherheitsupdates seit diesem Release. Mit diesen Updates wird auch das nächste CU-Release ergänzt.

Alle CU- und GDR-Releases enthalten das vollständige SQL Server-Paket sowie alle bisherigen Updates für das jeweilige Repository. Die Aktualisierung eines GDR-Releases auf ein CU-Release wird durch Ändern des konfigurierten Repositorys für SQL Server unterstützt. Ferner kann innerhalb einer Hauptversion auf ein beliebiges Release [herabgestuft](sql-server-linux-setup.md#rollback) werden (ab 2017).

> [!NOTE]
> Durch Ändern des Repositorys können Sie jederzeit von einem GDR-Release auf ein CU-Release aktualisieren. Die Aktualisierung von einem CU-Release auf ein GDR-Release wird dagegen nicht unterstützt.

## <a name="configure-repositories"></a>Konfigurieren von Repositorys

::: zone pivot="ld2-rhel"
Führen Sie die in den folgenden Abschnitten beschriebenen Schritte aus, um Repositorys unter Red Hat Enterprise Server (RHEL) zu konfigurieren.
::: zone-end

::: zone pivot="ld2-sles"
Führen Sie die in den folgenden Abschnitten beschriebenen Schritte aus, um Repositorys unter SUSE Linux Enterprise Server (SLES) zu konfigurieren.
::: zone-end

::: zone pivot="ld2-ubuntu"
Führen Sie die in den folgenden Abschnitten beschriebenen Schritte aus, um Repositorys unter Ubuntu zu konfigurieren.
::: zone-end

## <a name="check-for-previously-configured-repositories"></a>Prüfen, ob bereits konfigurierte Repositorys vorhanden sind

<!--RHEL-->
::: zone pivot="ld2-rhel"
Überprüfen Sie zunächst, ob Sie bereits ein SQL Server-Repository registriert haben.

1. Zeigen Sie hierzu die Dateien im Verzeichnis **/etc/yum.repos.d** mit folgendem Befehl an:

   ```bash
   sudo ls /etc/yum.repos.d
   ```

2. Suchen Sie nach einer Datei, mit der das SQL Server-Verzeichnis konfiguriert wird, z. B. **mssql-server.repo**.

3. Drucken Sie den Inhalt der Datei.

   ```bash
   sudo cat /etc/yum.repos.d/mssql-server.repo
   ```

4. Bei der Eigenschaft **name** handelt es sich um das konfigurierte Repository. Sie können es anhand der Tabelle im Abschnitt [Repositorys](#repositories) in diesem Artikel ausfindig machen.

::: zone-end

<!--SLES-->
::: zone pivot="ld2-sles"
Überprüfen Sie zunächst, ob Sie bereits ein SQL Server-Repository registriert haben.

1. Verwenden Sie **zypper info**, um Informationen zu einem zuvor konfigurierten Repository zu erhalten.

   ```bash
   sudo zypper info mssql-server
   ```

2. Bei der Eigenschaft **Repository** handelt es sich um das konfigurierte Repository. Sie können es anhand der Tabelle im Abschnitt [Repositorys](#repositories) in diesem Artikel ausfindig machen.

::: zone-end

<!--Ubuntu-->
::: zone pivot="ld2-ubuntu"
Überprüfen Sie zunächst, ob Sie bereits ein SQL Server-Repository registriert haben.

1. Zeigen Sie den Inhalt der Datei **/etc/apt/sources.list** an.

   ```bash
   sudo cat /etc/apt/sources.list
   ```

2. Überprüfen Sie die Paket-URL für mssql-server. Sie können es anhand der Tabelle im Abschnitt [Repositorys](#repositories) in diesem Artikel ausfindig machen.

::: zone-end

## <a name="remove-old-repository"></a>Entfernen eines alten Repositorys

<!--RHEL-->
::: zone pivot="ld2-rhel"
Entfernen Sie ggf. das alte Repository mit folgendem Befehl.

```bash
sudo rm -rf /etc/yum.repos.d/mssql-server.repo
```

Bei diesem Befehl wird davon ausgegangen, dass die im vorherigen Abschnitt ausfindig gemachte Datei den Namen **mssql-server.repo** hatte.

::: zone-end

<!--SLES-->
::: zone pivot="ld2-sles"
Entfernen Sie ggf. das alte Repository. Verwenden Sie je nach Typ des zuvor konfigurierten Repositorys einen der folgenden Befehle.

| Repository | Befehl zum Entfernen |
|---|---|
| **Vorschauversion (2019)** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-preview'` |
| **2019 CU** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2019'` |
| **2019 GDR** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2019-gdr'`|
| **2017 CU** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017'` |
| **2017 GDR** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017-gdr'`|

::: zone-end

<!--Ubuntu-->
::: zone pivot="ld2-ubuntu"
Entfernen Sie ggf. das alte Repository. Verwenden Sie je nach Typ des zuvor konfigurierten Repositorys einen der folgenden Befehle.

| Repository | Befehl zum Entfernen |
|---|---|
| **Vorschauversion (2019)** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview xenial main'` |
| **2019 CU** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019 xenial main'` | 
| **2019 GDR** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019-gdr xenial main'` |
| **2017 CU** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017 xenial main'` | 
| **2017 GDR** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr xenial main'` |

::: zone-end

## <a name="configure-new-repository"></a>Konfigurieren eines neuen Repositorys

<!--RHEL-->
::: zone pivot="ld2-rhel"
Konfigurieren Sie das neue Repository, das für Installationen und Upgrades von SQL Server verwendet werden soll. Verwenden Sie einen der folgenden Befehle, um das Repository Ihrer Wahl zu konfigurieren.

| Repository | Versionsoptionen | Befehl |
|---|---|---|
| **2019 CU** | 2019 | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2019.repo` |
| **2019 GDR** | 2019 | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2019-gdr.repo` |
| **2017 CU** | 2017 | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
| **2017 GDR** | 2017 | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |

::: zone-end

<!--SLES-->
::: zone pivot="ld2-sles"
Konfigurieren Sie das neue Repository, das für Installationen und Upgrades von SQL Server verwendet werden soll. Verwenden Sie einen der folgenden Befehle, um das Repository Ihrer Wahl zu konfigurieren.

| Repository | Versionsoptionen | Befehl |
|---|---|---|
| **2019 CU** | 2019 | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2019.repo` |
| **2019 GDR** | 2019 | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2019-gdr.repo` |
| **2017 CU** | 2017 | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo` |
| **2017 GDR** | 2017 | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017-gdr.repo` |

::: zone-end

<!--Ubuntu-->
::: zone pivot="ld2-ubuntu"
Konfigurieren Sie das neue Repository, das für Installationen und Upgrades von SQL Server verwendet werden soll.

1. Importieren Sie die öffentlichen GPG-Schlüssel des Repositorys.

   ```bash
   sudo curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Verwenden Sie einen der folgenden Befehle, um das Repository Ihrer Wahl zu konfigurieren.

   | Repository | Versionsoptionen | Befehl |
   |---|---|---|
   | **2019 CU** | 2019 | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2019.list)"` |
   | **2019 GDR** | 2019 | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2019-gdr.list)"` |
   | **2017 CU** | 2017 | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"` |
   | **2017 GDR** | 2017 | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017-gdr.list)"` |

3. Führen **apt-get update** aus.

   ```bash
   sudo apt-get update
   ```

::: zone-end

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie das richtige Repository konfiguriert haben, können Sie SQL Server und alle zugehörigen Paket aus dem neuen Repository [installieren](sql-server-linux-setup.md#platforms) oder [aktualisieren](sql-server-linux-setup.md#upgrade).

::: zone pivot="ld2-rhel"
> [!IMPORTANT]
> Wenn Sie sich für die Verwendung des [RHEL-Schnellstarts](quickstart-install-connect-red-hat.md) entscheiden, denken Sie daran, dass Sie das Zielrepository bereits konfiguriert haben. Wiederholen Sie diesen Schritt in den Tutorials nicht. Dies trifft vor allem dann zu, wenn Sie das GDR-Repository konfigurieren, da beim Schnellstart das CU-Repository verwendet wird.
::: zone-end

::: zone pivot="ld2-sles"
> [!IMPORTANT]
> Wenn Sie sich für die Verwendung des [SLES-Schnellstarts](quickstart-install-connect-suse.md) entscheiden, denken Sie daran, dass Sie das Zielrepository bereits konfiguriert haben. Wiederholen Sie diesen Schritt in den Tutorials nicht. Dies trifft vor allem dann zu, wenn Sie das GDR-Repository konfigurieren, da beim Schnellstart das CU-Repository verwendet wird.
::: zone-end

::: zone pivot="ld2-ubuntu"
> [!IMPORTANT]
> Wenn Sie sich für die Verwendung des [Ubuntu-Schnellstarts](quickstart-install-connect-ubuntu.md) entscheiden, denken Sie daran, dass Sie das Zielrepository bereits konfiguriert haben. Wiederholen Sie diesen Schritt in den Tutorials nicht. Dies trifft vor allem dann zu, wenn Sie das GDR-Repository konfigurieren, da beim Schnellstart das CU-Repository verwendet wird.
::: zone-end

Weitere Informationen zum Installieren von SQL Server 2017 unter Linux finden Sie unter [Leitfaden für die Installation von SQL Server für Linux](sql-server-linux-setup.md).
