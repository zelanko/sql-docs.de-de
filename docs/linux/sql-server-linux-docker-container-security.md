---
title: Sichern von SQL Server Docker-Containern
description: Informieren Sie sich über die verschiedenen Möglichkeiten zum Sichern von SQL Server Docker-Containern und darüber, wie Sie Container auf dem Host als ein anderer Benutzer als „root“ ausführen können.
author: vin-yu
ms.author: vinsonyu
ms.reviewer: vanto
ms.custom: contperfq1
ms.date: 09/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
moniker: '>= sql-server-linux-2017 || >= sql-server-2017 || =sqlallproducts-allversions'
ms.openlocfilehash: 10d2eb061a4ee6d9ff9c8d0594561667dd882dc9
ms.sourcegitcommit: 678f513b0c4846797ba82a3f921ac95f7a5ac863
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2020
ms.locfileid: "89511588"
---
# <a name="secure-sql-server-docker-containers"></a>Sichern von SQL Server Docker-Containern

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

SQL Server 2017-Container werden standardmäßig als Root-Benutzer gestartet. Dies kann zu Sicherheitsbedenken führen. In diesem Artikel werden die Sicherheitsoptionen beschrieben, die beim Ausführen von SQL Server Docker-Containern und beim Erstellen eines SQL Server-Containers als Nicht-root-Benutzer verfügbar sind.

## <a name="build-and-run-non-root-sql-server-2017-containers"></a><a id="buildnonrootcontainer"></a> Erstellen und Ausführen von SQL Server 2017-Containern ohne Root-Berechtigung

Führen Sie die folgenden Schritte aus, um einen SQL Server 2017-Container zu erstellen, der als `mssql`Nicht-Root-Benutzer gestartet wird.

> [!NOTE]
> SQL Server 2019-Container werden automatisch als Container ohne Root-Berechtigung gestartet, sodass die folgenden Schritte nur für SQL Server 2017-Container gelten, die standardmäßig mit Root-Berechtigung gestartet werden.

1. Laden Sie das [Beispiel-Dockerfile für SQL Server-Container ohne Root-Berechtigung](https://raw.githubusercontent.com/microsoft/mssql-docker/master/linux/preview/examples/mssql-server-linux-non-root/Dockerfile) herunter, und speichern Sie sie als `dockerfile`.

2. Führen Sie den folgenden Befehl im Kontext des dockerfile-Verzeichnisses aus, um den SQL Server-Container ohne Root-Berechtigung zu erstellen:

    ```bash
    cd <path to dockerfile>
    docker build -t 2017-latest-non-root .
    ```

3. Starten Sie den Container.

    ```bash
    docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyStrongPassword@" --cap-add SYS_PTRACE --name sql1 -p 1433:1433 -d 2017-latest-non-root
    ```

    > [!NOTE]
    > Das `--cap-add SYS_PTRACE`-Flag wird für SQL Server-Container ohne Root-Berechtigung benötigt, um Sicherungsdateien für die Problembehandlung zu erzeugen.

4. Überprüfen Sie, ob der Container als Nicht-Root-Benutzer ausgeführt wird:

    ```bash
    docker exec -it sql1 bash
    ```

    Führen Sie `whoami` aus, um den Benutzer zurückzugeben, der innerhalb des Containers ausgeführt wird.
    
    ```bash
    whoami
    ```

## <a name="run-container-as-a-different-non-root-user-on-the-host"></a><a id="nonrootuser"></a> Ausführen eines Containers als anderer Nicht-Root-Benutzer auf dem Host

Um den SQL Server-Container als anderer Nicht-Root-Benutzer auszuführen, fügen Sie dem Befehl „docker run“ das Flag „-u“ hinzu. Der Container ohne Root-Berechtigung hat die Einschränkung, dass er als Teil der Root-Gruppe ausgeführt werden muss, es sei denn, es wird ein Volume für `/var/opt/mssql` bereitgestellt, auf das der Nicht-Root-Benutzer zugreifen kann. Die Root-Gruppe gewährt dem Nicht-Root-Benutzer keine zusätzlichen Root-Berechtigungen.

#### <a name="run-as-a-user-with-a-uid-4000"></a>Ausführen als Benutzer mit einer UID 4000

Sie können SQL Server mit einer benutzerdefinierten UID starten. Der folgende Befehl startet beispielsweise SQL Server mit der UID 4000:

```bash
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyStrongPassword" --cap-add SYS_PTRACE -u 4000:0 -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-latest
```

> [!Warning]
> Stellen Sie sicher, dass der SQL Server-Container einen benannten Benutzer wie „mssql“ oder „root“ hat, denn anderenfalls kann SQLCMD nicht innerhalb des Containers ausgeführt werden. Sie können überprüfen, ob der SQL Server-Container als benannter Benutzer ausgeführt wird, indem Sie `whoami` innerhalb des Containers ausführen.

#### <a name="run-the-non-root-container-as-the-root-user"></a>Ausführen des Containers ohne Root-Berechtigung als Root-Benutzer

Sie können den Container ohne Root-Berechtigung als Root-Benutzer ausführen, wenn erforderlich. Dadurch würde der Container auch automatisch sämtliche Dateiberechtigungen erhalten, da er eine höhere Berechtigung hat.

```bash
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyStrongPassword" -u 0:0 -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-latest
```

#### <a name="run-as-a-user-on-your-host-machine"></a>Ausführen als Benutzer auf Ihrem Hostcomputer

Mit dem folgenden Befehl können Sie SQL Server mit einem vorhandenen Benutzer auf dem Hostcomputer starten:
```bash
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyStrongPassword" --cap-add SYS_PTRACE -u $(id -u myusername):0 -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-latest
```

#### <a name="run-as-a-different-user-and-group"></a>Ausführen als anderer Benutzer und Gruppe

Sie können SQL Server mit einem benutzerdefinierten Benutzer oder einer benutzerdefinierten Gruppe starten. In diesem Beispiel verfügt das bereitgestellte Volume über Berechtigungen, die für den Benutzer oder die Gruppe auf dem Hostcomputer konfiguriert sind.

```bash
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyStrongPassword" --cap-add SYS_PTRACE -u (id -u myusername):(id -g myusername) -v /path/to/mssql:/var/opt/mssql -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-latest
```

## <a name="configure-persistent-storage-permissions-for-non-root-containers"></a><a id="storagepermissions"></a> Konfigurieren von persistenten Speicherberechtigungen für Container ohne Root-Berechtigung

Um dem Nicht-Root-Benutzer den Zugriff auf Datenbankdateien zu ermöglichen, die sich auf bereitgestellten Volumes befinden, stellen Sie sicher, dass der Benutzer oder die Gruppe, unter der Sie den Container ausführen, Lese-/Schreibvorgänge im persistenten Dateispeicher ausführen kann.  

Mit diesem Befehl können Sie den aktuellen Besitzer der Datenbankdateien ermitteln.

```bash
ls -ll <database file dir>
```

Führen Sie einen der folgenden Befehle aus, wenn SQL Server keinen Zugriff auf persistente Datenbankdateien hat.

#### <a name="grant-the-root-group-rw-access-to-the-db-files"></a>Zuweisen der Berechtigungen für die Root-Gruppe zum Lesen und Schreiben der DB-Dateien

Erteilen Sie die Root-Gruppenberechtigungen für die folgenden Verzeichnisse, damit der SQL Server-Container ohne Root-Berechtigungen Zugriff auf Datenbankdateien hat.

```bash
chgrp -R 0 <database file dir>
chmod -R g=u <database file dir>
```

#### <a name="set-the-non-root-user-as-the-owner-of-the-files"></a>Festlegen des Nicht-Root-Benutzers als Besitzer der Dateien

Dies kann der standardmäßig festgelegte Nicht-Root-Benutzer oder ein anderer Nicht-Root-Benutzer sein, den Sie angeben möchten. In diesem Beispiel haben wir die UID 10001 als Nicht-Root-Benutzer festgelegt.

```bash
chown -R 10001:0 <database file dir>
```

## <a name="next-steps"></a>Nächste Schritte

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

- Der [Schnellstart](quickstart-install-connect-docker.md?view=sql-server-2017) erleichtert Ihnen den Einstieg in die Verwendung von SQL Server 2017-Containerimages in Docker.

::: moniker-end

<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

- Der [Schnellstart](quickstart-install-connect-docker.md?view=sql-server-ver15) erleichtert Ihnen den Einstieg in die Verwendung von SQL Server 2019-Containerimages in Docker.

::: moniker-end

- [Bereitstellen von und Herstellen einer Verbindung mit SQL Server Docker-Containern](sql-server-linux-docker-container-deployment.md)

- [Verweisen auf zusätzliche Konfiguration und Anpassung für Docker-Container](sql-server-linux-docker-container-configure.md)

- [Problembehandlung von SQL Server Docker-Containern](sql-server-linux-docker-container-troubleshooting.md)