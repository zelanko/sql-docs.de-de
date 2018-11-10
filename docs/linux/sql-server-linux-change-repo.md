---
title: Konfigurieren von Linux-Repositorys für SQL Server 2017 und 2019 | Microsoft-Dokumentation
description: Überprüfen Sie, und konfigurieren Sie des Quellcode-Repositorys für 2019 für SQL Server und SQL Server 2017 unter Linux. Das Quellrepository wirkt sich auf die Version von SQL Server, die während der Installation und Upgrade angewendet wird.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/14/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 9b5d9e27db92ba048f0b6400c00313e81a1899f7
ms.sourcegitcommit: a2be75158491535c9a59583c51890e3457dc75d6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2018
ms.locfileid: "51269445"
---
# <a name="configure-repositories-for-installing-and-upgrading-sql-server-on-linux"></a>Konfigurieren von Repositorys zum Installieren und Aktualisieren von SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dieser Artikel beschreibt, wie Sie die richtige Repository für SQL Server 2017 und 2019 für SQL Server-Installationen und Upgrades unter Linux konfigurieren.

> [!TIP]
> SQL Server-2019 Preview ist jetzt verfügbar! Um dies auszuprobieren, verwenden Sie diesen Artikel zum Konfigurieren der neuen **Mssql-Server-Preview** Repository. Installieren Sie dann mithilfe der Anweisungen in der [Installationshandbuch](sql-server-linux-setup.md).

## <a id="repositories"></a> Repositorys

Wenn Sie SQL Server unter Linux installieren, müssen Sie ein Microsoft-Repository konfigurieren. Dieses Repository dient zum Abrufen der Datenbank-Engine-Paket, **Mssql-Server**, und SQL Server-Pakete. Es gibt derzeit drei wichtigsten Repositorys:

| Repository | Name | Description |
|---|---|---|
| **Vorschauversion (2017)** | **mssql-server** | SQL Server 2017 CTP und RC-Repository (nicht mehr unterstützt). |
| **Vorschau (2019)** | **MSSQL-Server-preview** | Vorschau der SQL Server-2019 und RC-Repository. |
| **CU** | **mssql-server-2017** | SQL Server 2017 kumulativen Update (CU)-Repository. |
| **GDR** | **mssql-server-2017-gdr** | SQL Server 2017-GDR-Repository für nur kritische Updates. |

## <a id="cuversusgdr"></a> Kumulatives Update im Vergleich zu GDR

Es ist wichtig zu beachten, dass es zwei Haupttypen von Repositorys für jede Verteilung gibt:

- **Kumulative Updates (CU)**: Repository für das kumulative Update (CU) enthält die Pakete für die grundlegenden SQL Server-Version und alle Fehler behoben oder Verbesserungen seit diesem Release. Kumulative Updates sind spezifisch für ein Releaseversion, z. B. SQL Server 2017. Sie werden in regelmäßigen Abständen veröffentlicht.

- **GDR**: das GDR-Repository enthält Pakete für die grundlegenden SQL Server-Version und nur wichtige Updates und Sicherheitsupdates seit diesem Release. Diese Updates werden auch die nächste CU-Version hinzugefügt.

Jede CU und GDR-Version enthält die vollständige SQL Server-Pakets und aller früheren Updates für das Repository. Beim Aktualisieren einer GDR-Version auf eine CU-Version wird durch die Änderung der Ihre konfigurierte Repositorys für SQL Server unterstützt. Sie können auch [downgrade](sql-server-linux-setup.md#rollback) für jede Version in Ihrer Hauptversion (Beispiel: 2017).

> [!NOTE]
> Sie können ein GDR-Version aktualisieren, um CU zu einem beliebigen Zeitpunkt durch Ändern der Repositorys freizugeben. Aktualisieren von einer CU-Version mit einer GDR-Version wird nicht unterstützt. 

## <a id="configure"></a> Konfigurieren Sie ein repository

In den folgenden Abschnitten wird beschrieben, wie Sie überprüfen und konfigurieren ein Repository für die folgenden unterstützten Plattformen:

- [Red Hat Enterprise Server](#rhel)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#sles)

## <a id="rhel"></a> Konfigurieren von virtuellen RHEL-Repositorys
Verwenden Sie die folgenden Schritte aus, um Repositorys auf Red Hat Enterprise Server (RHEL) konfigurieren.

### <a name="check-for-previously-configured-repositories-rhel"></a>Überprüfen Sie für Repositorys, die zuvor konfigurierten (RHEL)
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

### <a name="remove-old-repository-rhel"></a>Entfernen Sie alte Repository (RHEL)
Entfernen Sie ggf. das alte-Repository mit den folgenden Befehl aus.

```bash
sudo rm -rf /etc/yum.repos.d/mssql-server.repo
```

Mit diesem Befehl wird davon ausgegangen, dass die Datei, die im vorherigen Abschnitt angegeben hatte **Mssql-server.repo**.

### <a name="configure-new-repository-rhel"></a>Konfigurieren Sie neues Repository (RHEL)
Konfigurieren Sie das neue Repository für SQL Server-Installationen und Upgrades verwendet. Verwenden Sie einen der folgenden Befehle aus, um das Repository Ihrer Wahl zu konfigurieren.

| Repository | Version | Befehl |
|---|---|---|
| **Vorschau (2019)** | 2019 | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-preview.repo` |
| **CU** | 2017 | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
| **GDR** | 2017 | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |

## <a id="sles"></a> Konfigurieren von SLES-Repositorys
Verwenden Sie die folgenden Schritte aus, um Repositorys auf SLES konfigurieren.

### <a name="check-for-previously-configured-repositories-sles"></a>Überprüfen Sie für Repositorys, die zuvor konfigurierten (SLES)
Zuerst stellen Sie sicher, ob Sie bereits ein SQL Server-Repository registriert haben.

1. Verwendung **Zypper Informationen** zum Abrufen von Informationen über alle zuvor konfigurierten Repository.

   ```bash
   sudo zypper info mssql-server
   ```

2. Die **Repository** -Eigenschaft ist das Repository konfiguriert. Sie können sie ermitteln, mit der Tabelle in der [Repositorys](#repositories) Abschnitt dieses Artikels.

### <a name="remove-old-repository-sles"></a>Entfernen Sie alte Repository (SLES)
Entfernen Sie ggf. das alte Repository. Verwenden Sie eine der folgenden Befehle basierend auf den Typ des zuvor konfigurierten Repositorys.

| Repository | Befehl zum Entfernen |
|---|---|
| **Vorschauversion (2017)** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server'` |
| **Vorschau (2019)** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-preview'` |
| **CU** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017'` |
| **GDR** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017-gdr'`|

### <a name="configure-new-repository-sles"></a>Neues Repository (SLES) konfigurieren
Konfigurieren Sie das neue Repository für SQL Server-Installationen und Upgrades verwendet. Verwenden Sie einen der folgenden Befehle aus, um das Repository Ihrer Wahl zu konfigurieren.

| Repository | Version | Befehl |
|---|---|---|
| **Vorschau (2019)** | 2019 | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-preview.repo` |
| **CU** | 2017 | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo` |
| **GDR** | 2017 | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017-gdr.repo` |

## <a id="ubuntu"></a> Konfigurieren von Repositorys von Ubuntu
Verwenden Sie die folgenden Schritte aus, um Repositorys unter Ubuntu konfigurieren.

### <a name="check-for-previously-configured-repositories-ubuntu"></a>Überprüfen Sie für Repositorys, die zuvor konfigurierten (Ubuntu)
Zuerst stellen Sie sicher, ob Sie bereits ein SQL Server-Repository registriert haben.

1. Anzeigen des Inhalts der **/etc/apt/sources.list** Datei.

   ```bash
   sudo cat /etc/apt/sources.list
   ```

2. Überprüfen Sie die Paket-URL für Mssql-Server. Sie können sie ermitteln, mit der Tabelle in der [Repositorys](#repositories) Abschnitt dieses Artikels.

### <a name="remove-old-repository-ubuntu"></a>Entfernen Sie alte Repository (Ubuntu)
Entfernen Sie ggf. das alte Repository. Verwenden Sie eine der folgenden Befehle basierend auf den Typ des zuvor konfigurierten Repositorys.

| Repository | Befehl zum Entfernen |
|---|---|
| **Vorschauversion (2017)** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server xenial main'` |
| **Vorschau (2019)** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview xenial main'` |
| **CU** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017 xenial main'` | 
| **GDR** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr xenial main'` |

### <a name="configure-new-repository-ubuntu"></a>Konfigurieren Sie neues Repository (Ubuntu)
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

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie die richtige Repository konfiguriert haben, können Sie zum Fortfahren [installieren](sql-server-linux-setup.md#platforms) oder [aktualisieren](sql-server-linux-setup.md#upgrade) SQL Server und der verbundenen Pakete aus dem Repository neue.

> [!IMPORTANT]
> An diesem Punkt, wenn Sie den Installations-Artikeln, wie z. B. Verwenden der [Schnellstarts](sql-server-linux-setup.md#platforms), denken Sie daran, dass Sie die Ziel-Repository bereits konfiguriert haben. Wiederholen Sie diesen Schritt nicht in den Tutorials ein. Dies ist insbesondere dann, wenn Sie das GDR-Repository konfigurieren, da die Schnellstarts der CU-Repository verwenden.

Weitere Informationen zum Installieren von SQL Server 2017 unter Linux finden Sie unter [zur Installation von SQL Server unter Linux](sql-server-linux-setup.md).
