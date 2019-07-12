---
title: Konfigurieren von Linux-Repositorys für SQL Server 2017 und 2019
description: Überprüfen Sie, und konfigurieren Sie des Quellcode-Repositorys für 2019 für SQL Server und SQL Server 2017 unter Linux. Das Quellrepository wirkt sich auf die Version von SQL Server, die während der Installation und Upgrade angewendet wird.
author: VanMSFT
ms.author: vanto
manager: jroth
ms.date: 02/11/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
zone_pivot_groups: ld2-linux-distribution
ms.openlocfilehash: 05299a2efd374dc7d58b5e32fcdea918b12fc1d3
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67834086"
---
# <a name="configure-repositories-for-installing-and-upgrading-sql-server-on-linux"></a>Konfigurieren von Repositorys zum Installieren und Aktualisieren von SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

::: zone pivot="ld2-rhel"
Dieser Artikel beschreibt, wie Sie die richtige Repository für SQL Server 2017 und 2019 für SQL Server-Installationen und Upgrades unter Linux konfigurieren. Im oberen Bereich die aktuelle Auswahl ist **Red Hat (RHEL)** .
::: zone-end

::: zone pivot="ld2-sles"
Dieser Artikel beschreibt, wie Sie die richtige Repository für SQL Server 2017 und 2019 für SQL Server-Installationen und Upgrades unter Linux konfigurieren. Im oberen Bereich die aktuelle Auswahl ist **SUSE (SLES)** .
::: zone-end

::: zone pivot="ld2-ubuntu"
Dieser Artikel beschreibt, wie Sie die richtige Repository für SQL Server 2017 und 2019 für SQL Server-Installationen und Upgrades unter Linux konfigurieren. Im oberen Bereich die aktuelle Auswahl ist **Ubuntu**.
::: zone-end

> [!TIP]
> SQL Server-2019 Preview ist jetzt verfügbar! Um dies auszuprobieren, verwenden Sie diesen Artikel zum Konfigurieren der neuen **Mssql-Server-Preview** Repository. Installieren Sie dann mithilfe der Anweisungen in der [Installationshandbuch](sql-server-linux-setup.md).

## <a id="repositories"></a> Repositorys

Wenn Sie SQL Server unter Linux installieren, müssen Sie ein Microsoft-Repository konfigurieren. Dieses Repository dient zum Abrufen der Datenbank-Engine-Paket, **Mssql-Server**, und SQL Server-Pakete. Es gibt derzeit drei wichtigsten Repositorys:

| Repository | Name | Beschreibung |
|---|---|---|
| **Vorschauversion (2017)** | **mssql-server** | SQL Server 2017 CTP und RC-Repository (nicht mehr unterstützt). |
| **Vorschau (2019)** | **mssql-server-preview** | Vorschau der SQL Server-2019 und RC-Repository. |
| **CU** | **mssql-server-2017** | SQL Server 2017 kumulativen Update (CU)-Repository. |
| **GDR** | **mssql-server-2017-gdr** | SQL Server 2017-GDR-Repository für nur kritische Updates. |

## <a id="cuversusgdr"></a> Kumulatives Update im Vergleich zu GDR

Es ist wichtig zu beachten, dass es zwei Haupttypen von Repositorys für jede Verteilung gibt:

- **Kumulative Updates (CU)** : Das kumulative Update (CU)-Repository enthält Pakete für die grundlegenden SQL Server-Version und alle Fehler behoben oder Verbesserungen seit diesem Release. Kumulative Updates sind spezifisch für ein Releaseversion, z. B. SQL Server 2017. Sie werden in regelmäßigen Abständen veröffentlicht.

- **GDR**: Das GDR-Repository enthält Pakete für die grundlegenden SQL Server-Version und nur wichtige Updates und Sicherheitsupdates seit diesem Release. Diese Updates werden auch die nächste CU-Version hinzugefügt.

Jede CU und GDR-Version enthält die vollständige SQL Server-Pakets und aller früheren Updates für das Repository. Beim Aktualisieren einer GDR-Version auf eine CU-Version wird durch die Änderung der Ihre konfigurierte Repositorys für SQL Server unterstützt. Sie können auch [downgrade](sql-server-linux-setup.md#rollback) für jede Version in Ihrer Hauptversion (Beispiel: 2017).

> [!NOTE]
> Sie können ein GDR-Version aktualisieren, um CU zu einem beliebigen Zeitpunkt durch Ändern der Repositorys freizugeben. Aktualisieren von einer CU-Version mit einer GDR-Version wird nicht unterstützt.

## <a name="configure-repositories"></a>Konfigurieren von Repositorys

::: zone pivot="ld2-rhel"
Verwenden Sie die Schritte in den folgenden Abschnitten, um Repositorys auf Red Hat Enterprise Server (RHEL) konfigurieren.
::: zone-end

::: zone pivot="ld2-sles"
Verwenden Sie die Schritte in den folgenden Abschnitten, um Repositorys auf SUSE Linux Enterprise Server (SLES) konfigurieren.
::: zone-end

::: zone pivot="ld2-ubuntu"
Verwenden Sie die Schritte in den folgenden Abschnitten zum Konfigurieren von Repositorys auf Ubuntu.
::: zone-end

## <a name="check-for-previously-configured-repositories"></a>Kontrollkästchen für Repositorys, die zuvor konfigurierten

<!--RHEL-->
::: zone pivot="ld2-rhel"
Zuerst stellen Sie sicher, ob Sie bereits ein SQL Server-Repository registriert haben.

1. Zeigen Sie die Dateien der **/etc/yum.repos.d** Verzeichnis mit dem folgenden Befehl:

   ```bash
   sudo ls /etc/yum.repos.d
   ```

2. Suchen Sie nach einer Datei, die der SQL Server gespeichert, z. B. konfiguriert **Mssql-server.repo**.

3. Druckt den Inhalt der Datei.

   ```bash
   sudo cat /etc/yum.repos.d/mssql-server.repo
   ```

4. Die **Namen** -Eigenschaft ist das Repository konfiguriert. Sie können sie ermitteln, mit der Tabelle in der [Repositorys](#repositories) Abschnitt dieses Artikels.

::: zone-end

<!--SLES-->
::: zone pivot="ld2-sles"
Zuerst stellen Sie sicher, ob Sie bereits ein SQL Server-Repository registriert haben.

1. Verwendung **Zypper Informationen** zum Abrufen von Informationen über alle zuvor konfigurierten Repository.

   ```bash
   sudo zypper info mssql-server
   ```

2. Die **Repository** -Eigenschaft ist das Repository konfiguriert. Sie können sie ermitteln, mit der Tabelle in der [Repositorys](#repositories) Abschnitt dieses Artikels.

::: zone-end

<!--Ubuntu-->
::: zone pivot="ld2-ubuntu"
Zuerst stellen Sie sicher, ob Sie bereits ein SQL Server-Repository registriert haben.

1. Anzeigen des Inhalts der **/etc/apt/sources.list** Datei.

   ```bash
   sudo cat /etc/apt/sources.list
   ```

2. Überprüfen Sie die Paket-URL für Mssql-Server. Sie können sie ermitteln, mit der Tabelle in der [Repositorys](#repositories) Abschnitt dieses Artikels.

::: zone-end

## <a name="remove-old-repository"></a>Entfernen Sie alte repository

<!--RHEL-->
::: zone pivot="ld2-rhel"
Entfernen Sie ggf. das alte-Repository mit den folgenden Befehl aus.

```bash
sudo rm -rf /etc/yum.repos.d/mssql-server.repo
```

Mit diesem Befehl wird davon ausgegangen, dass die Datei, die im vorherigen Abschnitt angegeben hatte **Mssql-server.repo**.

::: zone-end

<!--SLES-->
::: zone pivot="ld2-sles"
Entfernen Sie ggf. das alte Repository. Verwenden Sie eine der folgenden Befehle basierend auf den Typ des zuvor konfigurierten Repositorys.

| Repository | Befehl zum Entfernen |
|---|---|
| **Vorschauversion (2017)** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server'` |
| **Vorschau (2019)** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-preview'` |
| **CU** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017'` |
| **GDR** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017-gdr'`|

::: zone-end

<!--Ubuntu-->
::: zone pivot="ld2-ubuntu"
Entfernen Sie ggf. das alte Repository. Verwenden Sie eine der folgenden Befehle basierend auf den Typ des zuvor konfigurierten Repositorys.

| Repository | Befehl zum Entfernen |
|---|---|
| **Vorschauversion (2017)** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server xenial main'` |
| **Vorschau (2019)** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview xenial main'` |
| **CU** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017 xenial main'` | 
| **GDR** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr xenial main'` |

::: zone-end

## <a name="configure-new-repository"></a>Neues Repository konfigurieren

<!--RHEL-->
::: zone pivot="ld2-rhel"
Konfigurieren Sie das neue Repository für SQL Server-Installationen und Upgrades verwendet. Verwenden Sie einen der folgenden Befehle aus, um das Repository Ihrer Wahl zu konfigurieren.

| Repository | Version | Befehl |
|---|---|---|
| **Vorschau (2019)** | 2019 | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-preview.repo` |
| **CU** | 2017 | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
| **GDR** | 2017 | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |

::: zone-end

<!--SLES-->
::: zone pivot="ld2-sles"
Konfigurieren Sie das neue Repository für SQL Server-Installationen und Upgrades verwendet. Verwenden Sie einen der folgenden Befehle aus, um das Repository Ihrer Wahl zu konfigurieren.

| Repository | Version | Befehl |
|---|---|---|
| **Vorschau (2019)** | 2019 | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-preview.repo` |
| **CU** | 2017 | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo` |
| **GDR** | 2017 | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017-gdr.repo` |

::: zone-end

<!--Ubuntu-->
::: zone pivot="ld2-ubuntu"
Konfigurieren Sie das neue Repository für SQL Server-Installationen und Upgrades verwendet.

1. Importieren Sie die öffentlichen Repository GPG-Schlüssel.

   ```bash
   sudo curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Verwenden Sie einen der folgenden Befehle aus, um das Repository Ihrer Wahl zu konfigurieren.

   | Repository | Version | Befehl |
   |---|---|---|
   | **Vorschau (2019)** | 2019 | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-preview.list)"` |
   | **CU** | 2017 | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"` |
   | **GDR** | 2017 | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017-gdr.list)"` |

3. Führen Sie **apt-Get-Update**.

   ```bash
   sudo apt-get update
   ```

::: zone-end

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie die richtige Repository konfiguriert haben, können Sie zum Fortfahren [installieren](sql-server-linux-setup.md#platforms) oder [aktualisieren](sql-server-linux-setup.md#upgrade) SQL Server und der verbundenen Pakete aus dem Repository neue.

::: zone pivot="ld2-rhel"
> [!IMPORTANT]
> An diesem Punkt möchten Sie verwenden die [RHEL-Schnellstart](quickstart-install-connect-red-hat.md), denken Sie daran, dass Sie die Ziel-Repository bereits konfiguriert haben. Wiederholen Sie diesen Schritt nicht in den Tutorials ein. Dies ist insbesondere dann, wenn Sie das GDR-Repository konfigurieren, da der Schnellstart das CU-Repository verwendet.
::: zone-end

::: zone pivot="ld2-sles"
> [!IMPORTANT]
> An diesem Punkt möchten Sie verwenden die [SLES Schnellstart](quickstart-install-connect-suse.md), denken Sie daran, dass Sie die Ziel-Repository bereits konfiguriert haben. Wiederholen Sie diesen Schritt nicht in den Tutorials ein. Dies ist insbesondere dann, wenn Sie das GDR-Repository konfigurieren, da der Schnellstart das CU-Repository verwendet.
::: zone-end

::: zone pivot="ld2-ubuntu"
> [!IMPORTANT]
> An diesem Punkt möchten Sie verwenden die [Ubuntu Schnellstart](quickstart-install-connect-ubuntu.md), denken Sie daran, dass Sie die Ziel-Repository bereits konfiguriert haben. Wiederholen Sie diesen Schritt nicht in den Tutorials ein. Dies ist insbesondere dann, wenn Sie das GDR-Repository konfigurieren, da der Schnellstart das CU-Repository verwendet.
::: zone-end

Weitere Informationen zum Installieren von SQL Server 2017 unter Linux finden Sie unter [zur Installation von SQL Server unter Linux](sql-server-linux-setup.md).
