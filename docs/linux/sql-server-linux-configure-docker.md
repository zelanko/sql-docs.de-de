---
title: Konfigurationsoptionen für SQL Server unter Docker | Microsoft-Dokumentation
description: Entdecken Sie Möglichkeiten der Verwendung von und Interaktion mit SQL Server 2017 und 2019 Vorschau-containerimages in Docker. Dies schließt dauerhafte Speichern von Daten, Kopieren von Dateien und zur Problembehandlung.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 01/17/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
ms.custom: sql-linux
moniker: '>= sql-server-linux-2017 || >= sql-server-2017 || =sqlallproducts-allversions'
ms.openlocfilehash: 328c73efd2230a09ad838ab375335bdb01f046aa
ms.sourcegitcommit: 56fb7b648adae2c7b81bd969de067af1a2b54180
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57227372"
---
# <a name="configure-sql-server-container-images-on-docker"></a>Konfigurieren von SQL Server-Container-Images in Docker

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dieser Artikel erläutert das Konfigurieren und Verwenden der [Mssql-Server-Linux-Container-Abbild](https://hub.docker.com/r/microsoft/mssql-server-linux/) mit Docker. Dieses Image enthält SQL Server für Linux (basierend auf Ubuntu 16.04). Es kann unter Linux mit der Docker-Engine 1.8 und höher und in Docker für Mac bzw. Windows verwendet werden.

> [!NOTE]
> In diesem Artikel wird speziell mit der Mssql-Server-Linux-Image. Das Windows-Abbild wird nicht behandelt, aber mehr darüber erfahren Sie auf die [Mssql-Server-Windows-Docker-Hubseite](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/).

## <a name="pull-and-run-the-container-image"></a>Übertragen mithilfe von Pull und Ausführen von Containerimages

Führen Sie zum Abrufen, und führen Sie die Docker-Container-Images für SQL Server 2017 und SQL Server-2019 Preview, die Voraussetzungen und Schritte in den folgenden Schnellstart aus:

- [Ausführen des SQL Server 2017-containerimages mit Docker](quickstart-install-connect-docker.md?view=sql-server-2017)
- [Ausführen des SQL Server-2019 Vorschau-containerimages mit Docker](quickstart-install-connect-docker.md?view=sql-server-ver15)

In diesem Artikel für die Konfiguration enthält Szenarien für die weitere Verwendung in den folgenden Abschnitten.

<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="rhel"></a> Führen Sie die RHEL-basierte containerimages

Gesamte Dokumentation zu SQL Server Linux-containerimages zeigen Sie auf der Ubuntu-basierte Container. Ab SQL Server-2019 Preview können Sie Container basierend auf Red Hat Enterprise Linux (RHEL) verwenden. Ändern Sie das containerrepository von **mcr.microsoft.com/mssql/server:2019-CTP2.3-ubuntu** zu **mcr.microsoft.com/mssql/rhel/server:2019-CTP2.3** in all Ihre Docker-Befehle.

Beispielsweise ruft der folgende Befehl aus der neuesten SQL Server-2019-Vorschau-Container, der RHEL verwendet:

```bash
sudo docker pull mcr.microsoft.com/mssql/rhel/server:2019-CTP2.3
```

```PowerShell
docker pull mcr.microsoft.com/mssql/rhel/server:2019-CTP2.3
```

::: moniker-end

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="production"></a> Ausführen von produktionscontainerimages

Der schnellstartanleitung im vorherigen Abschnitt wird die kostenlose Developer-Edition von SQL Server ausgeführt, von Docker Hub. Die meisten Informationen weiterhin gilt, wenn es sich bei produktionsumgebungen containerimages, z. B. Web, Standard oder Enterprise Edition ausgeführt werden soll. Es gibt jedoch einige Unterschiede, die im folgenden beschrieben werden.

- Sie können nur SQL Server in einer produktionsumgebung verwenden, wenn Sie eine gültige Lizenz haben. Sie erhalten eine kostenlose Lizenz für SQL Server Express Produktion [hier](https://go.microsoft.com/fwlink/?linkid=857693). SQL Server Standard und Enterprise Edition-Lizenzen stehen über [Microsoft Volume Licensing](https://www.microsoft.com/licensing/default.aspx).


- Das containerimage Entwickler kann zum Ausführen oder der Editions für die Produktion konfiguriert werden. Verwenden Sie die folgenden Schritte aus, um produktionseditionen ausführen:

Überprüfen Sie die Anforderungen und Prozeduren ausführen, der [Schnellstart](quickstart-install-connect-docker.md). Sie müssen angeben, dass Ihre Produktions-Edition, mit der **MSSQL_PID** -Umgebungsvariablen angegeben. Das folgende Beispiel zeigt, wie Sie das neueste containerimage von SQL Server 2017 für die Enterprise Edition ausführen:

      ```bash
      docker run --name sqlenterprise \
         -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
         -e 'MSSQL_PID=Enterprise' -p 1433:1433 \
         -d store/microsoft/mssql-server-linux:2017-latest
      ```

      ```PowerShell
      docker run --name sqlenterprise `
         -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
         -e "MSSQL_PID=Enterprise" -p 1433:1433 `
         -d "store/microsoft/mssql-server-linux:2017-latest"
      ```

      > [!IMPORTANT]
      > By passing the value **Y** to the environment variable **ACCEPT_EULA** and an edition value to **MSSQL_PID**, you are expressing that you have a valid and existing license for the edition and version of SQL Server that you intend to use. You also agree that your use of SQL Server software running in a Docker container image will be governed by the terms of your SQL Server license.

      > [!NOTE]
      > For a full list of possible values for **MSSQL_PID**, see [Configure SQL Server settings with environment variables on Linux](sql-server-linux-configure-environment-variables.md).

::: moniker-end

## <a name="connect-and-query"></a>Verbinden und Abfragen

Sie können eine Verbindung herstellen und Abfragen von SQL Server in einem Container entweder außerhalb des Containers aus oder innerhalb des Containers. Den folgenden Abschnitten werden beide Szenarien. 

### <a name="tools-outside-the-container"></a>Tools, die außerhalb des Containers

Sie können mit SQL Server-Instanz auf Ihrem Docker-Computer über jedes externe Linux-, Windows oder MacOS-Tool verbinden, die SQL-Verbindungen unterstützt. Einige häufig verwendete Tools gehören:

- [sqlcmd](sql-server-linux-setup-tools.md)
- [Visual Studio Code](sql-server-linux-develop-use-vscode.md)
- [SQL Server Management Studio (SSMS) unter Windows](sql-server-linux-manage-ssms.md)

Im folgenden Beispiel wird **Sqlcmd** zur Verbindung mit SQL Server in einem Docker-Container ausgeführt. Die IP-Adresse in der Verbindungszeichenfolge ist die IP-Adresse des Hostcomputers, die der Container ausgeführt wird.

```bash
sqlcmd -S 10.3.2.4 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4 -U SA -P "<YourPassword>"
```

Wenn Sie einen hostPort zugeordnet, die nicht die Standardeinstellung **1433**, fügen Sie diesen Port auf die Verbindungszeichenfolge hinzu. Angenommen, Sie angegeben haben `-p 1400:1433` in Ihre `docker run` und dann verbinden, indem explizit Port 1400 angeben.

```bash
sqlcmd -S 10.3.2.4,1400 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1400 -U SA -P "<YourPassword>"
```

### <a name="tools-inside-the-container"></a>Tools, die innerhalb des Containers

Ab SQL Server 2017 Preview, die [SQL Server-Befehlszeilentools](sql-server-linux-setup-tools.md) im containerimage enthalten sind. Wenn Sie das Image mit einer interaktiven Eingabeaufforderung anfügen, können Sie die Tools lokal ausführen.

1. Verwenden Sie den Befehl `docker exec -it`, um in Ihrem laufenden Container eine interaktive Bash-Shell zu starten. Im folgenden Beispiel `e69e056c702d` ist die Container-ID.

    ```bash
    docker exec -it e69e056c702d "bash"
    ```

    > [!TIP]
    > Sie müssen nicht immer die gesamte Container-Id angeben. Sie müssen nur genügend Zeichen zur eindeutigen Identifizierung angeben. In diesem Beispiel ist es ausreichend, um Sie verwenden u. u. `e6` oder `e69` anstatt die vollständige Id.

2. Stellen Sie eine lokale Verbindung mit „sqlcmd“ her. Beachten Sie, dass diese Sqlcmd wird nicht im Pfad in der Standardeinstellung ist, müssen Sie den vollständigen Pfad angeben.

    ```bash
    /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '<YourPassword>'
    ```

3. Geben Sie abschließend mit Sqlcmd `exit`.

4. Geben Sie abschließend mit der interaktiven Eingabeaufforderung `exit`. Der Container wird auch nach dem Beenden der interaktiven Bash-Shell weiter ausgeführt.

## <a name="run-multiple-sql-server-containers"></a>Führen Sie mehrere SQL Server-Container

Docker bietet eine Möglichkeit, mehrere SQL Server-Container auf demselben Hostcomputer ausgeführt wird. Dies ist der Ansatz für Szenarien, in denen mehrere Instanzen von SQL Server auf demselben Host zu müssen. Jeder Container muss sich auf einem anderen Port verfügbar machen.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

Im folgende Beispiel werden zwei SQL Server 2017-Container erstellt und ordnet sie Ports **1401** und **1402** auf dem Hostcomputer.

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d mcr.microsoft.com/mssql/server:2017-latest
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1402:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d mcr.microsoft.com/mssql/server:2017-latest
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1402:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

Im folgende Beispiel werden zwei SQL Server-2019 Vorschau-Container erstellt und ordnet sie Ports **1401** und **1402** auf dem Hostcomputer.

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-CTP2.3-ubuntu
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1402:1433 -d mcr.microsoft.com/mssql/server:2019-CTP2.3-ubuntu
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-CTP2.3-ubuntu
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1402:1433 -d mcr.microsoft.com/mssql/server:2019-CTP2.3-ubuntu
```

::: moniker-end

Es gibt jetzt zwei Instanzen von SQL Server in einem separaten Container ausgeführt wird. Clients können mit jeder SQL Server-Instanz verbinden, mit der IP-Adresse des Docker-Hosts und die Portnummer für den Container verwendet wird.

```bash
sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
sqlcmd -S 10.3.2.4,1402 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
sqlcmd -S 10.3.2.4,1402 -U SA -P "<YourPassword>"
```

## <a id="customcontainer"></a> Erstellen Sie einen angepassten container

Es ist möglich, Ihre eigenen erstellen [dockerfile-Datei](https://docs.docker.com/engine/reference/builder/#usage) zum Erstellen eines benutzerdefinierten SQL Server-Containers. Weitere Informationen finden Sie unter [eine Demo, die SQL Server und einer Node-Anwendung kombiniert](https://github.com/twright-msft/mssql-node-docker-demo-app). Wenn Sie eigene dockerfile-Datei erstellen, achten Sie die Vordergrundprozess ausgeführt, da dieser Prozess die Lebensdauer des Containers steuert. Wenn es beendet wird, wird der Container heruntergefahren. Beispielsweise sollten Sie ein Skript ausführen, starten Sie SQL Server, und stellen Sie sicher, dass ist die SQL Server-Prozess, der am weitesten rechts befindlichen-Befehl. Alle anderen Befehle werden im Hintergrund ausgeführt. Dies wird in den folgenden Befehl in einer dockerfile-Datei veranschaulicht:

```bash
/usr/src/app/do-my-sql-commands.sh & /opt/mssql/bin/sqlservr
```

Wenn Sie die Befehle im vorherigen Beispiel storniert, würde der Container Herunterfahren bei Abschluss des Skripts führen-my-Sql-commands.sh.

## <a id="persist"></a> Speichern Sie Ihre Daten

Ihre Änderungen an der Konfiguration von SQL Server und die Datenbankdateien in den Container beibehalten werden, selbst wenn Sie neu starten, den Container mit `docker stop` und `docker start`. Aber wenn Sie den Container mit entfernen `docker rm`, alles, was im Container gelöscht wird, einschließlich SQL Server und Ihre Datenbanken. Im folgende Abschnitt wird erläutert, wie Sie mit **Datenvolumes** die Datenbankdateien beibehalten, auch wenn die zugehörigen Container gelöscht werden.

> [!IMPORTANT]
> Für SQL Server ist es wichtig, dass Sie verstehen, dass die Datenpersistenz in Docker. Neben der Beschreibung in diesem Abschnitt finden Sie in der Docker-Dokumentation auf [so verwalten Sie Daten in Docker-Containern](https://docs.docker.com/engine/tutorials/dockervolumes/).

### <a name="mount-a-host-directory-as-data-volume"></a>Ein Host-Verzeichnis als Datenvolumen bereitstellen

Die erste Option ist ein Verzeichnis auf dem Host als ein Volumen für Daten in Ihrem Container bereitgestellt. Zu diesem Zweck verwenden Sie die `docker run` -Befehl mit der `-v <host directory>:/var/opt/mssql` Flag. Dadurch werden die Daten zwischen den Ausführungen der Container wiederhergestellt werden.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP2.3-ubuntu
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP2.3-ubuntu
```

::: moniker-end

Dieser Technik können auch zum Freigeben und zeigen Sie die Dateien auf dem Docker-Host.

> [!IMPORTANT]
> Host-volumezuordnung für Docker auf dem Mac mit dem SQL Server auf Linux-Image wird zu diesem Zeitpunkt nicht unterstützt. Verwenden Sie stattdessen datenvolumecontainer. Diese Einschränkung bezieht sich auf die `/var/opt/mssql` Verzeichnis. Lesen aus der eine bereitgestellte Verzeichnis funktioniert gut. Sie können z. B. mithilfe von - V auf einem Mac-Hostverzeichnis bereitzustellen und die Wiederherstellung einer Sicherung von einer bak-Datei, die auf dem Host befindet.

### <a name="use-data-volume-containers"></a>Datenvolumecontainer verwenden

Die zweite Option ist die Verwendung ein volumecontainers Daten. Sie können einen volumecontainer für die Daten erstellen, indem Sie einen Volumenamen anstelle eines Host-Verzeichnisses mit Angabe der `-v` Parameter. Das folgende Beispiel erstellt eine freigegebene Datenvolume mit dem Namen **Sqlvolume**.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v sqlvolume:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v sqlvolume:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v sqlvolume:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP2.3-ubuntu
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v sqlvolume:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP2.3-ubuntu
```
::: moniker-end

> [!NOTE]
> Dieses Verfahren zum Erstellen von ein Datenvolume implizit in den Befehl "run" funktioniert nicht mit älteren Versionen von Docker. In diesem Fall verwenden Sie die expliziten Schritte in der Dokumentation zum Docker [erstellen und Bereitstellen eines volumecontainers Daten](https://docs.docker.com/engine/tutorials/dockervolumes/#creating-and-mounting-a-data-volume-container).

Auch wenn Sie zu beenden und entfernen diesen Container, behält das Datenvolumen auf. Sie können ihn mit Anzeigen der `docker volume ls` Befehl.

```bash
docker volume ls
```

Wenn Sie einen anderen Container klicken Sie dann mit dem gleichen Volumenamen erstellen, verwendet der neue Container die gleichen SQL Server-Daten enthalten sind, auf dem Volume.

Um einen volumecontainer für die Daten zu entfernen, verwenden die `docker volume rm` Befehl.

> [!WARNING]
> Wenn Sie den datenvolumecontainer löschen, werden SQL Server-Daten im Container *dauerhaft* gelöscht.

### <a name="backup-and-restore"></a>Sichern und Wiederherstellen

Zusätzlich zu diesen Funktionen und Container Techniken können Sie auch die Verwendung der standardmäßigen SQL Server-Sicherung und Wiederherstellungsverfahren. Sie können die Sicherungsdateien zum Schutz Ihrer Daten oder zum Verschieben der Daten in eine andere SQL Server-Instanz verwenden. Weitere Informationen finden Sie unter [Sicherungs- und SQL Server-Datenbanken unter Linux](sql-server-linux-backup-and-restore-database.md).

> [!WARNING]
> Wenn Sie Sicherungen erstellen, stellen Sie sicher, dass zum Erstellen oder kopieren Sie die Sicherungsdateien außerhalb des Containers. Andernfalls, wenn der Container entfernt wird, werden die Sicherungsdateien ebenfalls gelöscht.

## <a name="execute-commands-in-a-container"></a>Führen Sie Befehle in einem container

Wenn Sie einen aktiven Container verfügen, können Sie Befehle innerhalb des Containers von einem Host, die Terminalserver ausführen.

So führe Sie die Container-ID zu erhalten:

```bash
docker ps
```

So starten Sie ein Bash-terminal in den Container ausführen:

```bash
docker exec -ti <Container ID> /bin/bash
```

Jetzt können Sie Befehle ausführen, als ob sie am Terminal innerhalb des Containers ausführen. Wenn Sie fertig sind, geben Sie `exit` ein. Dies in der interaktiven befehlssitzung beendet wird, aber Ihren Container wird weiterhin ausgeführt.

## <a name="copy-files-from-a-container"></a>Kopieren von Dateien aus einem container

Um eine Datei aus dem Container zu kopieren, verwenden Sie den folgenden Befehl aus:

```bash
docker cp <Container ID>:<Container path> <host path>
```

**Beispiel:**

```bash
docker cp d6b75213ef80:/var/opt/mssql/log/errorlog /tmp/errorlog
```

```PowerShell
docker cp d6b75213ef80:/var/opt/mssql/log/errorlog C:\Temp\errorlog
```

## <a name="copy-files-into-a-container"></a>Kopieren von Dateien in einem container

Um eine Datei in den Container zu kopieren, verwenden Sie den folgenden Befehl aus:

```bash
docker cp <Host path> <Container ID>:<Container path>
```

**Beispiel:**

```bash
docker cp /tmp/mydb.mdf d6b75213ef80:/var/opt/mssql/data
```

```PowerShell
docker cp C:\Temp\mydb.mdf d6b75213ef80:/var/opt/mssql/data
```
## <a id="tz"></a> Konfigurieren Sie die Zeitzone

Führen Sie SQL Server in einem Linux-Container mit einer bestimmten Zeitzone konfigurieren die **TZ** -Umgebungsvariablen angegeben. Führen Sie zum Ermitteln der richtigen Timezone-Werts der **Tzselect** einer Linux-Bash-Eingabeaufforderung den Befehl:

```bash
tzselect
```

Nach der Auswahl der Zeitzone **Tzselect** zeigt eine Ausgabe ähnlich der folgenden:

```bash
The following information has been given:

        United States
        Pacific

Therefore TZ='America/Los_Angeles' will be used.
```

Sie können diese Informationen verwenden, auf die gleiche Umgebungsvariable in Ihrer Linux-Container festgelegt. Das folgende Beispiel zeigt, wie Sie zum Ausführen von SQL Server in einem Container in der `Americas/Los_Angeles` Zeitzone:

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

```bash
sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
   -p 1433:1433 --name sql1 \
   -e 'TZ=America/Los_Angeles'\
   -d mcr.microsoft.com/mssql/server:2017-latest 
```

```PowerShell
sudo docker run -e 'ACCEPT_EULA=Y' -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
   -p 1433:1433 --name sql1 `
   -e "TZ=America/Los_Angeles" `
   -d mcr.microsoft.com/mssql/server:2017-latest 
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

```bash
sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
   -p 1433:1433 --name sql1 \
   -e 'TZ=America/Los_Angeles'\
   -d mcr.microsoft.com/mssql/server:2019-CTP2.3-ubuntu
```

```PowerShell
sudo docker run -e 'ACCEPT_EULA=Y' -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
   -p 1433:1433 --name sql1 `
   -e "TZ=America/Los_Angeles" `
   -d mcr.microsoft.com/mssql/server:2019-CTP2.3-ubuntu
```
::: moniker-end

## <a id="tags"></a> Ausführen eines bestimmten SQL Server-containerimages

Es gibt Szenarien, in denen Sie nicht das neueste containerimage von SQL Server verwenden sollten. Führen Sie eine bestimmte SQL Server-Container-Images verwenden Sie die folgenden Schritte aus:

1. Identifizieren Sie die Docker **Tag** für die Version, die Sie verwenden möchten. Um die verfügbaren Tags anzuzeigen, finden Sie unter [der Mssql-Server-Linux-Docker-Hubseite](https://hub.docker.com/r/microsoft/mssql-server-linux/tags/).

2. Ziehen Sie das SQL Server-containerimage mit dem Tag. Um der RC1-Image per Pull abzurufen, ersetzen Sie z. B. `<image_tag>` in den folgenden Befehl mit `rc1`.

   ```bash
   docker pull mcr.microsoft.com/mssql/server:<image_tag>
   ```

3. Um einen neuen Container mit diesem Image auszuführen, geben Sie den Namen des Tags in der `docker run` Befehl. Ersetzen Sie in den folgenden Befehl `<image_tag>` mit der Version, die Sie ausführen möchten.

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d mcr.microsoft.com/mssql/server:<image_tag>
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d mcr.microsoft.com/mssql/server:<image_tag>
   ```

Diese Schritte können auch einen vorhandenen Container herabgestuft verwendet werden. Beispielsweise können Sie zurücksetzen möchten oder ein downgrade von einem ausgeführten Container für die Problembehandlung oder zu testen. Ein Downgrade ein ausgeführtes Containers müssen Sie eine Technik, die Persistenz für den Datenordner verwenden. Befolgen Sie die gleichen Schritte der [Aktualisierungsabschnitt](#upgrade), aber der Tagname der älteren Version angeben, wenn Sie den neuen Container ausführen.

## <a id="version"></a> Überprüfen Sie die containerversion

Wenn Sie die Version von SQL Server in einem ausgeführten Docker-Container wissen möchten, führen Sie den folgenden Befehl aus, um es anzuzeigen. Ersetzen Sie dies `<Container ID or name>` mit dem Ziel-Container-ID oder Name. Ersetzen Sie dies `<YourStrong!Passw0rd>` mit dem SQL Server-Kennwort für das SA-Anmeldung.

```bash
sudo docker exec -it <Container ID or name> /opt/mssql-tools/bin/sqlcmd \
   -S localhost -U SA -P '<YourStrong!Passw0rd>' \
   -Q 'SELECT @@VERSION'
```

```PowerShell
docker exec -it <Container ID or name> /opt/mssql-tools/bin/sqlcmd `
   -S localhost -U SA -P "<YourStrong!Passw0rd>" `
   -Q 'SELECT @@VERSION'
```

Sie können auch ermitteln von SQL Server-Version und Buildnummer für ein Ziel-Docker-containerimage. Der folgende Befehl zeigt die Informationen der SQL Server Versions- und Buildinformationen für die **Microsoft/Mssql-Server-Linux:2017-neueste** Image. Dies geschieht durch einen neuen Container mit einer Umgebungsvariablen mit **PAL_PROGRAM_INFO = 1**. Der resultierende Container sofort beendet wird, und die `docker rm` Befehl entfernt.

```bash
sudo docker run -e PAL_PROGRAM_INFO=1 --name sqlver \
   -ti mcr.microsoft.com/mssql/server:2017-latest && \
   sudo docker rm sqlver
```

```PowerShell
docker run -e PAL_PROGRAM_INFO=1 --name sqlver `
   -ti mcr.microsoft.com/mssql/server:2017-latest; `
   docker rm sqlver
```

Die zuvor eingegebenen Befehle anzeigen von Versionsinformationen, die ähnlich wie die folgende Ausgabe:

```Text
sqlservr
  Version 14.0.3029.16
  Build ID ee3d3882f1c48a7a7e590a620153012eaedc2f37143d485df945a079b9d4eeea
  Build Type release
  Git Version 65d42c4
  Built at Sat Jun 16 01:20:11 GMT 2018

PAL
  Build ID 60cfcb134bbae96d311f6a4f56aeb5a685b3809de80bcb61ec587a8f58b555eb
  Build Type release
  Git Version 21a4c11
  Built at Sat Jun 16 01:18:53 GMT 2018

Packages
  system.sfp                    6.2.9200.1,21a4c1178,
  system.common.sfp             10.0.15063.540
  system.certificates.sfp       6.2.9200.1,21a4c1178,
  system.netfx.sfp              4.6.1590.0
  secforwarderxplat.sfp         14.0.3029.16
  sqlservr.sfp                  14.0.3029.16
  sqlagent.sfp                  14.0.3029.16
```

## <a id="upgrade"></a> Upgrade von SQL Server in Containern

Um das containerimage mit Docker zu aktualisieren, müssen identifizieren Sie das Tag für die Version für das Upgrade zunächst. Rufen Sie diese Version aus der Registrierung mit dem `docker pull` Befehl:

```bash
docker pull mcr.microsoft.com/mssql/server:<image_tag>
```

Aktualisiert die SQL Server-Images für alle neuen Container, die Sie erstellen, aber SQL Server auf alle aktuell ausgeführten Container wird nicht aktualisiert. Zu diesem Zweck müssen Sie einen neuen Container mit dem aktuellen SQL Server-Container-Image Erstellen und migrieren Sie Ihre Daten in diesen neuen Container.

1. Stellen Sie sicher, dass Sie eines der [Data Persistence-Techniken](#persist) für Ihre vorhandenen SQL Server-Container. Dadurch können Sie einen neuen Container mit denselben Daten zu starten.

1. Beenden Sie den SQL Server-Container mit dem `docker stop` Befehl.

1. Erstellt einen neuen SQL Server-Container mit `docker run` , und geben Sie ein Hostverzeichnis zugeordneten oder einen volumecontainer für Daten. Stellen Sie sicher, dass die bestimmte Tag für das SQL Server-Upgrade zu verwenden. Der neue Container verwendet jetzt eine neue Version von SQL Server mit Ihren vorhandenen SQL Server-Daten.

   > [!IMPORTANT]
   > Upgrade wird nur zu diesem Zeitpunkt zwischen RC1 und RC2 bei allgemeiner Verfügbarkeit unterstützt.

1. Überprüfen Sie Ihre Datenbanken und die Daten in den neuen Container.

1. Entfernen Sie optional den alten Container mit `docker rm`.

## <a id="troubleshooting"></a> Problembehandlung

Die folgenden Abschnitte enthalten Vorschläge zur Problembehandlung für die Ausführung von SQL Server in Containern.

### <a name="docker-command-errors"></a>Fehler der Docker-Befehl

Wenn Sie für einen Fehler erhalten `docker` Befehle, stellen Sie sicher, dass der Docker-Dienst ausgeführt wird, und versuchen Sie es mit erweiterten Berechtigungen ausführen.

Beispielsweise unter Linux erhalten Sie möglicherweise die folgende Fehlermeldung beim Ausführen `docker` Befehle:

```
Cannot connect to the Docker daemon. Is the docker daemon running on this host?
```

Wenn Sie diesen Fehler unter Linux erhalten, führen Sie die gleichen Befehle, die mit dem Präfix `sudo`. Wenn dies fehlschlägt, überprüfen Sie der Docker-Dienst ausgeführt wird, und starten Sie ihn bei Bedarf.

```bash
sudo systemctl status docker
sudo systemctl start docker
```

Auf Windows stellen Sie sicher, dass Sie PowerShell oder der Eingabeaufforderung als Administrator starten.

### <a name="sql-server-container-startup-errors"></a>SQL Server-Container-Startfehlern

Wenn der SQL Server-Container nicht ausgeführt werden, versuchen Sie die folgenden Tests:

- Wenn Sie eine Fehlermeldung, wie z. B. erhalten **"Fehler beim Erstellen des Endpunkts CONTAINER_NAME auf Netzwerk-Bridge. Fehler beim Starten Proxy: Lauschen Tcp 0.0.0.0:1433 Bind: Adresse wird bereits verwendet. "** , und Sie versuchen, den Container-Port 1433 an einen Port zuzuordnen, die bereits verwendet wird. Dies kann vorkommen, wenn Sie SQL Server lokal auf dem Hostcomputer ausführen. Es kann auch vorkommen, wenn Sie zwei SQL Server-Container starten, und versuchen, die beide den gleichen hostPort zugeordnet sind. In diesem Fall verwenden die `-p` Parameter, um den Container-Port 1433 an einen anderen Host-Port zugeordnet. Zum Beispiel: 

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

    ```bash
    docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1400:1433 -d mcr.microsoft.com/mssql/server:2017-latest`.
    ```

    ```PowerShell
    docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1400:1433 -d mcr.microsoft.com/mssql/server:2017-latest`.
    ```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

    ```bash
    docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1400:1433 -d mcr.microsoft.com/mssql/server:2019-CTP2.3-ubuntu`.
    ```

    ```PowerShell
    docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1400:1433 -d mcr.microsoft.com/mssql/server:2019-CTP2.3-ubuntu`.
    ```

::: moniker-end

- Überprüfen Sie, wenn alle Fehlermeldungen aus Container vorhanden sind.

    ```bash
    docker logs e69e056c702d
    ```

- Stellen Sie sicher, dass Sie den Arbeitsspeicher und Datenträger im angegebenen Mindestanforderungen der [Anforderungen](#requirements) Abschnitt dieses Artikels.

- Wenn Sie einer Container-Management-Software verwenden, stellen Sie sicher, dass sie als Root-Benutzer ausgeführten containerprozesse unterstützt. Der Sqlservr-Prozess in den Container, die als Root-Benutzer ausgeführt wird.

- Überprüfen Sie die [Setup und SQL Server-Fehlerprotokolle](#errorlogs).

### <a name="enable-dump-captures"></a>Aktivieren Sie Dump Erfassungen

Wenn SQL Server-Prozess innerhalb des Containers ein Fehler auftritt, erstellen Sie einen neuen Container mit **SYS_PTRACE** aktiviert. Dadurch werden die Linux-Funktion für die Ablaufverfolgung von eines Prozess, der zum Erstellen einer Dumpdatei einer Ausnahme erforderlich ist. Die Speicherabbilddatei kann vom Support verwendet werden, um das Problem zu beheben. Diese Funktion wird von folgende Ausführungsbefehl von Docker ermöglicht.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

```bash
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -e "MSSQL_PID=Developer" --cap-add SYS_PTRACE -p 1401:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

```bash
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -e "MSSQL_PID=Developer" --cap-add SYS_PTRACE -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-CTP2.3-ubuntu
```

::: moniker-end

### <a name="sql-server-connection-failures"></a>SQL Server-Verbindungsfehler

Wenn Sie mit SQL Server-Instanz ausgeführt wird, in Ihrem Container herstellen können, probieren Sie die folgenden Tests:

- Stellen Sie sicher, dass der SQL Server-Container ausgeführt wird, anhand der **STATUS** Spalte die `docker ps -a` Ausgabe. Wenn nicht der Fall, verwenden Sie `docker start <Container ID>` zu starten.

- Wenn Sie mit einem nicht standardmäßigen hostPort (nicht Port 1433) zugeordnet sind, stellen Sie sicher, dass Sie den Port in der Verbindungszeichenfolge angeben. Sehen Sie die portzuordnung in der **PORTS** Spalte die `docker ps -a` Ausgabe. Der folgende Befehl verbindet z. B. Sqlcmd in einen Container, der über Port 1401 lauscht:

    ```bash
    sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
    ```

    ```PowerShell
    sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
    ```

- Wenn Sie verwendet `docker run` mit einem vorhandenen zugeordneten Datenvolumen oder der datenvolumecontainer ignoriert SQL Server den Wert der `MSSQL_SA_PASSWORD`. Stattdessen wird das vorkonfiguriert, dass SA-Kennwort für Benutzer von den SQL Server-Daten in das Volumen für Daten oder datenvolumecontainer verwendet. Stellen Sie sicher, dass Sie das SA-Kennwort, das die Daten, die Sie zum Anfügen, verwenden.

- Überprüfen Sie die [Setup und SQL Server-Fehlerprotokolle](#errorlogs).

### <a name="sql-server-availability-groups"></a>SQL Server-Verfügbarkeitsgruppen

Wenn Sie Docker mit SQL Server-Verfügbarkeitsgruppen verwenden, sind zwei zusätzliche Anforderungen.

- Ordnen Sie den Port, der für die Replikat-Kommunikation (Standard 5022) verwendet wird. Geben Sie z. B. `-p 5022:5022` als Teil Ihrer `docker run` Befehl.

- Legen Sie explizit den Hostnamen des Containers durch die `-h YOURHOSTNAME` Parameter der `docker run` Befehl. Dieser Hostname wird verwendet, wenn Sie Ihre Verfügbarkeitsgruppe konfigurieren. Wenn Sie nicht mit angeben `-h`, wird standardmäßig die Container-ID.

### <a id="errorlogs"></a> Setup und SQL Server-Fehlerprotokolle

Sehen Sie sich die SQL Server-Setup und Fehlerprotokolle **/var/opt/mssql/log**. Wenn der Container nicht ausgeführt wird, starten Sie zunächst den Container. Anschließend verwenden Sie eine interaktive Eingabeaufforderung, um die Protokolle zu überprüfen.

```bash
docker start e69e056c702d
docker exec -it e69e056c702d "bash"
```

Führen Sie in der Bash-Sitzung in Ihrem Container die folgenden Befehle aus:

```bash
cd /var/opt/mssql/log
cat setup*.log
cat errorlog
```

> [!TIP]
> Wenn Sie ein Hostverzeichnis zum bereitgestellt **/var/opt/mssql** bei der Erstellung Ihres Containers stattdessen finden Sie auf die **Log** Unterverzeichnis auf dem zugeordneten Pfad auf dem Host.

## <a name="next-steps"></a>Nächste Schritte

Erste Schritte mit SQL Server 2017-containerimages unter Docker durchlaufen die [Schnellstart](quickstart-install-connect-docker.md).

Sehen Sie sich auch die [Mssql-Docker-GitHub-Repository](https://github.com/Microsoft/mssql-docker) für Ressourcen, Feedback und bekannte Probleme.

[Erkunden Sie hochverfügbarkeit für SQL Server-Container](sql-server-linux-container-ha-overview.md)
