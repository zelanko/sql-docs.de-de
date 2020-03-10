---
title: Konfigurationsoptionen für SQL Server auf Docker
description: Entdecken Sie verschiedene Möglichkeiten zur Verwendung von und Interaktion mit SQL Server 2017- und SQL Server 2019-Containerimages in Docker. Diese umfassen das Beibehalten von Daten, das Kopieren von Dateien und das Beheben von Problemen.
author: vin-yu
ms.author: vinsonyu
ms.reviewer: vanto
ms.date: 01/08/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
moniker: '>= sql-server-linux-2017 || >= sql-server-2017 || =sqlallproducts-allversions'
ms.openlocfilehash: e97f535dedd2b6ee25abfc886d1f08272697c549
ms.sourcegitcommit: ff1bd69a8335ad656b220e78acb37dbef86bc78a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78340402"
---
# <a name="configure-sql-server-container-images-on-docker"></a>Konfigurieren von SQL Server-Containerimages in Docker

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Artikel wird erläutert, wie Sie das [mssql-server-linux-Containerimage](https://hub.docker.com/_/microsoft-mssql-server) mit Docker konfigurieren und verwenden. 

Informationen zu weiteren Bereitstellungsszenarios finden Sie unter:

- [Windows](../database-engine/install-windows/install-sql-server.md)
- [Linux](../linux/sql-server-linux-setup.md)
- [Kubernetes: Big Data-Cluster](../big-data-cluster/deploy-get-started.md)

Dieses Image enthält SQL Server für Linux (basierend auf Ubuntu 16.04). Es kann unter Linux mit der Docker-Engine 1.8 und höher und in Docker für Mac bzw. Windows verwendet werden.

> [!NOTE]
> In diesem Artikel liegt der Fokus auf dem Image „mssql-sever-linux“. Das Windows-Image wird hier zwar nicht behandelt, aber auf der [Docker Hub-Seite zu „mssql-server-windows“](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/) erhalten Sie weitere Informationen.

> [!IMPORTANT]
> Bevor Sie sich für die Ausführung eines SQL Server-Containers für Anwendungsfälle in der Produktion entscheiden, lesen Sie unsere [Richtlinie zur Unterstützung von SQL Server-Containern](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server), um sicherzustellen, dass Sie mit einer unterstützten Konfiguration arbeiten.

Dieses 6-minütige Video enthält eine Einführung in die Ausführung von SQL Server in Containern:

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2019-in-Containers/player?WT.mc_id=dataexposed-c9-niner]


## <a name="pull-and-run-the-container-image"></a>Übertragen mithilfe von Pull und Ausführen von Containerimages

Wenn Sie Docker-Containerimages für SQL Server 2017 und SQL Server 2019 herunterladen und ausführen möchten, sollten Sie zunächst die im folgenden Schnellstart beschriebenen Voraussetzungen schaffen und die Schritte ausführen:

- [Ausführen des SQL Server 2017-Containerimages mit Docker](quickstart-install-connect-docker.md?view=sql-server-2017)
- [Ausführen des SQL Server 2019-Containerimages mit Docker](quickstart-install-connect-docker.md?view=sql-server-ver15)

In diesem Artikel zur Konfiguration werden zusätzliche Anwendungsfälle beschrieben.

<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="rhel"></a> Ausführen von RHEL-basierten Containerimages

Die Dokumentation für SQL Server-Containerimages für Linux bezieht sich auf Ubuntu-basierte Container. Ab SQL Server 2019 können Sie auch RHEL-basierte Container (Red Hat Enterprise Linux) verwenden. Ändern Sie das Containerrepository in allen Docker-Befehlen von **mcr.microsoft.com/mssql/server:2019-GA-ubuntu-16.04** in **mcr.microsoft.com/mssql/rhel/server:2019-CU1-rhel-8**.

Der folgende Befehl ruft beispielsweise das kumulative Update 1 für SQL Server 2019 ab, für das RHEL 8 verwendet wird:

```bash
sudo docker pull mcr.microsoft.com/mssql/rhel/server:2019-CU1-rhel-8
```

```PowerShell
docker pull mcr.microsoft.com/mssql/rhel/server:2019-CU1-rhel-8
```

::: moniker-end

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="production"></a> Ausführen von Produktionscontainerimages

Im Schnellstart im vorherigen Abschnitt wird die kostenlose Developer Edition von SQL Server über Docker Hub ausgeführt. Die meisten Angaben gelten weiterhin, wenn Sie Produktionscontainerimages wie für die Enterprise-, Standard- und Web-Edition ausführen möchten. Es gibt jedoch einige Unterschiede, die im Folgenden erläutert werden.

- Sie können SQL Server nur in einer Produktionsumgebung verwenden, wenn Sie über eine gültige Lizenz verfügen. Sie können eine [kostenlose SQL Server Express-Lizenz](https://go.microsoft.com/fwlink/?linkid=857693) für die Produktion erwerben. Lizenzen für SQL Server Standard und SQL Server Enterprise sind über die [Microsoft-Volumenlizenzierung](https://www.microsoft.com/licensing/default.aspx) verfügbar.


- Das Developer-Containerimage kann so konfiguriert werden, dass auch die Produktionseditionen ausgeführt werden können. Führen Sie Folgendes durch, um Produktionseditionen auszuführen:

Machen Sie sich im [Schnellstart](quickstart-install-connect-docker.md) mit den Voraussetzungen vertraut, und führen Sie die dort aufgeführten Befehle aus. Sie müssen Ihre Produktionsedition mit der Umgebungsvariable **MSSQL_PID** angeben. Im folgenden Beispiel wird die Ausführung des neuesten SQL Server 2017-Containerimages für die Enterprise Edition veranschaulicht:

```bash
docker run --name sqlenterprise \
      -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
      -e 'MSSQL_PID=Enterprise' -p 1433:1433 \
      -d mcr.microsoft.com/mssql/server:2017-latest
```

```PowerShell
docker run --name sqlenterprise `
      -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
      -e "MSSQL_PID=Enterprise" -p 1433:1433 `
      -d "mcr.microsoft.com/mssql/server:2017-latest"
```

> [!IMPORTANT]
> Indem Sie den Wert **Y** an die Umgebungsvariable **ACCEPT_EULA** und einen Editionswert an **MSSQL_PID** übergeben, bestätigen Sie, dass Sie eine gültige und vorhandene Lizenz für die Edition und Version von SQL Server besitzen, die Sie verwenden möchten. Außerdem stimmen Sie den Nutzungsbedingungen für Ihre SQL Server-Lizenz zu, die für die Verwendung von SQL Server-Software gilt, die in einem Docker-Containerimage ausgeführt wird.

> [!NOTE]
> Eine vollständige Liste der möglichen Werte für **MSSQL_PID** finden Sie unter [Konfigurieren von SQL Server-Einstellungen mit Umgebungsvariablen unter Linux](sql-server-linux-configure-environment-variables.md).

::: moniker-end

## <a name="connect-and-query"></a>Herstellen einer Verbindung und Ausführen von Abfragen

Sie können von innerhalb oder außerhalb des Containers eine Verbindung mit einer SQL Server-Instanz herstellen, die in einem Container ausgeführt wird, und Abfragen an diese senden. In den folgenden Abschnitten werden beide Szenarios erläutert. 

### <a name="tools-outside-the-container"></a>Tools außerhalb des Containers

Sie können über jedes externe Linux-, Windows- oder macOS-Tool, das SQL-Verbindungen unterstützt, eine Verbindung mit der SQL Server-Instanz auf Ihrem Docker-Computer herstellen. Folgende Tools werden häufig verwendet:

- [sqlcmd](sql-server-linux-setup-tools.md)
- [Visual Studio Code](sql-server-linux-develop-use-vscode.md)
- [SQL Server Management Studio (SSMS) unter Windows](sql-server-linux-manage-ssms.md)

Im folgenden Beispiel wird **sqlcmd** verwendet, um eine Verbindung mit einer SQL Server-Instanz herzustellen, die in einem Docker-Container ausgeführt wird. Die IP-Adresse in der Verbindungszeichenfolge ist die IP-Adresse des Hostcomputers, auf dem der Container ausgeführt wird.

```bash
sqlcmd -S 10.3.2.4 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4 -U SA -P "<YourPassword>"
```

Wenn Sie eine Hostport zugeordnet haben, der nicht dem Standardport **1433** entspricht, fügen Sie diesen Port zur Verbindungszeichenfolge hinzu. Wenn Sie beispielsweise `-p 1400:1433` in Ihrem `docker run`-Befehl angegeben haben, stellen Sie die Verbindung her, indem Sie explizit Port 1400 angeben.

```bash
sqlcmd -S 10.3.2.4,1400 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1400 -U SA -P "<YourPassword>"
```

### <a name="tools-inside-the-container"></a>Tools innerhalb des Containers

Ab SQL Server 2017 sind die [SQL Server-Befehlszeilentools](sql-server-linux-setup-tools.md) im Containerimage enthalten. Wenn Sie diese mit einer interaktiven Befehlszeile an das Image anfügen, können Sie die Tools lokal ausführen.

1. Verwenden Sie den Befehl `docker exec -it`, um in Ihrem laufenden Container eine interaktive Bash-Shell zu starten. Im folgenden Beispiel entspricht `e69e056c702d` der Container-ID.

    ```bash
    docker exec -it e69e056c702d "bash"
    ```

    > [!TIP]
    > Sie müssen nicht immer die gesamte Container-ID angeben. Sie müssen nur ausreichend Zeichen angeben, um diese eindeutig zu identifizieren. In diesem Beispiel reicht es aus, `e6` oder `e69` anstelle der vollständigen ID zu verwenden.

2. Stellen Sie eine lokale Verbindung mit „sqlcmd“ her. Beachten Sie, dass sqlcmd nicht automatisch im Pfad vorhanden ist. Sie müssen daher selbst den vollständigen Pfand angeben.

    ```bash
    /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '<YourPassword>'
    ```

3. Wenn Sie mit sqlcmd fertig sind, geben Sie `exit` ein.

4. Wenn Sie mit der interaktiven Eingabeaufforderung fertig sind, geben Sie `exit` ein. Der Container wird auch nach dem Beenden der interaktiven Bash-Shell weiter ausgeführt.

## <a name="run-multiple-sql-server-containers"></a>Ausführen mehrerer SQL Server-Container

Docker ermöglicht die Ausführung mehrerer SQL Server-Container auf demselben Hostcomputer. Verwenden Sie diesen Ansatz, wenn mehrere SQL Server-Instanzen auf demselben Host benötigt werden. Jeder Container muss sich an einem anderen Port verfügbar machen.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

Im folgenden Beispiel werden zwei SQL Server 2017-Container erstellt und den Ports **1401** und **1402** auf dem Hostcomputer zugeordnet.

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

Im folgenden Beispiel werden zwei SQL Server 2019-Container erstellt und den Ports **1401** und **1402** auf dem Hostcomputer zugeordnet.

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-GA-ubuntu-16.04
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1402:1433 -d mcr.microsoft.com/mssql/server:2019-GA-ubuntu-16.04
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-GA-ubuntu-16.04
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1402:1433 -d mcr.microsoft.com/mssql/server:2019-GA-ubuntu-16.04
```

::: moniker-end

Nun gibt es zwei Instanzen von SQL Server, die in separaten Containern ausgeführt werden. Clients können eine Verbindung mit der jeweiligen SQL Server-Instanz herstellen, indem sie die IP-Adresse des Docker-Hosts und die Portnummer für den Container verwenden.

```bash
sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
sqlcmd -S 10.3.2.4,1402 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
sqlcmd -S 10.3.2.4,1402 -U SA -P "<YourPassword>"
```

## <a id="customcontainer"></a> Erstellen eines benutzerdefinierten Containers

Sie können ein eigenes [Dockerfile](https://docs.docker.com/engine/reference/builder/#usage) erstellen, um einen benutzerdefinierten SQL Server-Container zu erstellen. Weitere Informationen finden Sie in [dieser Demo, in der SQL Server und eine Node-Anwendung kombiniert werden](https://github.com/twright-msft/mssql-node-docker-demo-app). Wenn Sie ein eigenes Dockerfile erstellen, sollten Sie auf den Vordergrundprozess achten, da dieser die Lebensdauer des Containers bestimmt. Wenn dieser beendet wird, wird der Container heruntergefahren. Wenn Sie beispielsweise ein Skript ausführen und SQL Server starten möchten, sollten Sie sicherstellen, dass der SQL Server-Prozess der Befehl ganz rechts ist. Alle anderen Befehle werden im Hintergrund ausgeführt. Dies wird mit dem folgenden Befehl in einem Dockerfile veranschaulicht:

```bash
/usr/src/app/do-my-sql-commands.sh & /opt/mssql/bin/sqlservr
```

Wenn Sie die Befehle im vorherigen Beispiel rückgängig gemacht haben, wird der Container heruntergefahren, wenn das Skript „do-my-sql-commands.sh“ abgeschlossen wird.

## <a id="persist"></a> Beibehalten von Daten

Die SQL Server-Konfigurationsänderungen und -Datenbankdateien werden im Container beibehalten, auch wenn Sie den Container mit `docker stop` und `docker start` neu starten. Wenn Sie den Container jedoch mit `docker rm` entfernen, werden sämtliche Inhalte des Containers gelöscht, einschließlich SQL Server und Ihrer Datenbanken. Im folgenden Abschnitt wird erläutert, wie **Datenvolumes** verwendet werden, um Ihre Datenbankdateien beizubehalten, auch wenn die zugeordneten Container gelöscht werden.

> [!IMPORTANT]
> Für SQL Server ist es wichtig, sich mit der Datenpersistenz in Docker auseinanderzusetzen. Weitere Informationen finden Sie in der Docker-Dokumentation unter [Verwalten von Daten in Docker-Containern](https://docs.docker.com/engine/tutorials/dockervolumes/).

### <a name="mount-a-host-directory-as-data-volume"></a>Einbinden eines Hostverzeichnisses als Datenvolume

Die erste Option besteht darin, ein Verzeichnis auf dem Host als Datenvolume in Ihrem Container einzubinden. Verwenden Sie hierzu den Befehl `docker run` mit dem Flag `-v <host directory>:/var/opt/mssql`. Dadurch können die Daten zwischen den Containerausführungen wiederhergestellt werden.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>/data:/var/opt/mssql/data -v <host directory>/log:/var/opt/mssql/log -v <host directory>/secrets:/var/opt/mssql/secrets -d mcr.microsoft.com/mssql/server:2017-latest
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>/data:/var/opt/mssql/data -v <host directory>/log:/var/opt/mssql/log -v <host directory>/secrets:/var/opt/mssql/secrets -d mcr.microsoft.com/mssql/server:2017-latest
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>/data:/var/opt/mssql/data -v <host directory>/log:/var/opt/mssql/log -v <host directory>/secrets:/var/opt/mssql/secrets -d mcr.microsoft.com/mssql/server:2019-GA-ubuntu-16.04
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>/data:/var/opt/mssql/data -v <host directory>/log:/var/opt/mssql/log -v <host directory>/secrets:/var/opt/mssql/secrets -d mcr.microsoft.com/mssql/server:2019-GA-ubuntu-16.04
```

::: moniker-end

Mit dieser Methode können Sie die Dateien auch außerhalb von Docker auf dem Host freigeben und anzeigen.

> [!IMPORTANT]
> Die Hostvolumezuordnung für **Docker unter Windows** unterstützt derzeit nicht die Zuordnung des kompletten `/var/opt/mssql`-Verzeichnisses. Sie können dem Hostcomputer jedoch ein Unterverzeichnis wie `/var/opt/mssql/data` zuordnen.

> [!IMPORTANT]
> Die Hostvolumezuordnung für **Docker unter Mac** mit dem SQL Server für Linux-Image wird derzeit nicht unterstützt. Verwenden Sie stattdessen Datenvolumecontainer. Diese Einschränkung gilt nur für das Verzeichnis `/var/opt/mssql`. Das Lesen aus einem bereitgestellten Verzeichnis funktioniert ordnungsgemäß. Sie können beispielsweise ein Hostverzeichnis mithilfe von-v auf einem Mac einbinden und eine Sicherung aus einer BAK-Datei wiederherstellen, die sich auf dem Host befindet.

### <a name="use-data-volume-containers"></a>Verwenden von Datenvolumecontainern

Die zweite Option besteht in der Verwendung eines Datenvolumecontainers. Sie können einen Datenvolumecontainer erstellen, indem Sie mit dem Parameter `-v` einen Volumenamen anstelle eines Hostverzeichnisses angeben. Im folgenden Beispiel wird ein freigegebenes Datenvolume mit dem Namen **sqlvolume** erstellt.

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
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v sqlvolume:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-GA-ubuntu-16.04
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v sqlvolume:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-GA-ubuntu-16.04
```
::: moniker-end

> [!NOTE]
> Dieses Verfahren zum impliziten Erstellen eines Datenvolumes im run-Befehl funktioniert nicht mit älteren Docker-Versionen. Wenden Sie in diesem Fall die expliziten Schritte an, die in der Docker-Dokumentation zum [Erstellen und Einbinden eines Datenvolumecontainers](https://docs.docker.com/engine/tutorials/dockervolumes/#creating-and-mounting-a-data-volume-container) beschrieben werden.

Auch wenn Sie diesen Container anhalten und entfernen, bleibt das Datenvolume erhalten. Sie können es mit dem Befehl `docker volume ls` anzeigen.

```bash
docker volume ls
```

Wenn Sie dann einen weiteren Container mit dem gleichen Volumenamen erstellen, verwendet der neue Container die gleichen SQL Server-Daten, die auch im Volume enthalten sind.

Verwenden Sie den Befehl `docker volume rm`, um einen Datenvolumecontainer zu entfernen.

> [!WARNING]
> Wenn Sie den Datenvolumecontainer löschen, werden alle SQL Server-Daten im Container *dauerhaft* gelöscht.

### <a name="backup-and-restore"></a>Sichern und Wiederherstellen

Zusätzlich zu diesen Containerverfahren können Sie auch SQL Server-Standardverfahren für die Sicherung und Wiederherstellung anwenden. Sie können Sicherungsdateien verwenden, um Ihre Daten zu schützen oder die Daten auf eine andere SQL Server-Instanz zu verschieben. Weitere Informationen finden Sie unter [Sichern und Wiederherstellen von SQL Server-Datenbanken unter Linux](sql-server-linux-backup-and-restore-database.md).

> [!WARNING]
> Wenn Sie Sicherungen erstellen, stellen Sie sicher, dass die Sicherungsdateien außerhalb des Containers erstellt oder kopiert werden. Andernfalls werden die Sicherungsdateien gelöscht, wenn der Container entfernt wird.

## <a name="execute-commands-in-a-container"></a>Ausführen von Befehlen in einem Container

Wenn Sie bereits einen Container ausführen, können Sie über ein Hostterminal Befehle innerhalb des Containers ausführen.

So rufen Sie die Container-ID ab:

```bash
docker ps
```

So starten Sie ein Bash-Terminal in der Containerausführung:

```bash
docker exec -it <Container ID> /bin/bash
```

Nun können Sie Befehle wie über das Terminal innerhalb des Containers ausführen. Wenn Sie fertig sind, geben Sie `exit` ein. Dadurch wird die interaktive Befehlssitzung beendet, aber der Container wird weiter ausgeführt.

## <a name="copy-files-from-a-container"></a>Kopieren von Dateien aus einem Container

Verwenden Sie den folgenden Befehl, um eine Datei aus dem Container zu kopieren:

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

## <a name="copy-files-into-a-container"></a>Kopieren von Dateien in einen Container

Verwenden Sie den folgenden Befehl, um eine Datei in den Container zu kopieren:

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
## <a id="tz"></a> Konfigurieren der Zeitzone

Konfigurieren Sie die Umgebungsvariable `TZ`, um SQL Server mit einer bestimmten Zeitzone in einem Linux-Container auszuführen. Führen Sie den Befehl `tzselect` über eine Linux-Bash-Eingabeaufforderung aus, um den richtigen Zeitzonenwert zu ermitteln:

```bash
tzselect
```

Nachdem Sie eine Zeitzone ausgewählt haben, zeigt `tzselect` in etwa folgende Ausgabe an:

```bash
The following information has been given:

        United States
        Pacific

Therefore TZ='America/Los_Angeles' will be used.
```

Sie können diese Informationen verwenden, um die gleiche Umgebungsvariable in Ihrem Linux-Container festzulegen. Im folgenden Beispiel wird veranschaulicht, wie SQL Server in einem Container in der Zeitzone `Americas/Los_Angeles` ausgeführt wird:

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
   -d mcr.microsoft.com/mssql/server:2019-GA-ubuntu-16.04
```

```PowerShell
sudo docker run -e 'ACCEPT_EULA=Y' -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
   -p 1433:1433 --name sql1 `
   -e "TZ=America/Los_Angeles" `
   -d mcr.microsoft.com/mssql/server:2019-GA-ubuntu-16.04
```
::: moniker-end

## <a id="tags"></a> Ausführen eines bestimmten SQL Server-Containerimages

In manchen Fällen möchten Sie nicht das neueste SQL Server-Containerimage verwenden. Mithilfe der folgenden Schritte können Sie ein bestimmtes SQL Server-Containerimage ausführen:

1. Ermitteln Sie das **Docker-Tag** für das Release, das Sie verwenden möchten. Die verfügbaren Tags finden Sie auf der [Docker Hub-Seite zu „mssql-server-linux“](https://hub.docker.com/_/microsoft-mssql-server).

2. Laden Sie das SQL Server-Containerimage mit diesem Tag herunter. Wenn Sie das RC1-Image herunterladen möchten, ersetzen Sie `<image_tag>` im folgenden Befehl durch `rc1`.

   ```bash
   docker pull mcr.microsoft.com/mssql/server:<image_tag>
   ```

3. Wenn Sie einen neuen Container mit diesem Image ausführen möchten, geben Sie den Tagnamen im Befehl `docker run` an. Ersetzen Sie im folgenden Befehl `<image_tag>` durch die Version, die Sie ausführen möchten.

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d mcr.microsoft.com/mssql/server:<image_tag>
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d mcr.microsoft.com/mssql/server:<image_tag>
   ```

Diese Schritte können auch zum Herabstufen eines vorhandenen Containers verwendet werden. Sie können beispielsweise einen Rollback oder ein Downgrade für einen Container ausführen, um Probleme zu beheben oder Tests durchzuführen. Zum Herabstufen eines ausgeführten Containers müssen Sie eine Persistenzmethode für den Datenordner verwenden. Führen Sie die Schritte durch, die im [Abschnitt zu Upgrades](#upgrade) beschrieben werden, aber geben Sie den Tagnamen der älteren Version an, wenn Sie den neuen Container ausführen.

## <a id="version"></a> Überprüfen der Containerversion

Führen Sie folgenden Befehl aus, um die SQL Server-Version in einem ausgeführten Docker-Container zu ermitteln. Ersetzen Sie `<Container ID or name>` durch die Zielcontainer-ID oder den Namen. Ersetzen Sie `<YourStrong!Passw0rd>` durch das SQL Server-Kennwort für die SA-Anmeldung.

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

Sie können auch die SQL Server-Version und die Buildnummer für ein Docker-Zielcontainerimage ermitteln. Der folgende Befehl zeigt die SQL Server-Version und die Buildinformationen für das Image **mcr.microsoft.com/mssql/server:2017-latest** an. Hierfür wird ein neuer Container mit der Umgebungsvariable **PAL_PROGRAM_INFO=1** ausgeführt. Der daraus resultierende Container wird sofort beendet und durch den Befehl `docker rm` entfernt.

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

In den vorherigen Befehlen werden Versionsinformationen angezeigt, die der folgenden Ausgabe ähneln:

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

## <a id="upgrade"></a> Aktualisieren von SQL Server in Containern

Wenn Sie das Containerimage mit Docker aktualisieren möchten, müssen Sie zunächst das Tag für das Release des Upgrades ermitteln. Rufen Sie diese Version mit dem Befehl `docker pull` aus der Registrierung ab:

```bash
docker pull mcr.microsoft.com/mssql/server:<image_tag>
```

Dadurch wird das SQL Server-Image für neu erstellte Container aktualisiert. SQL Server wird jedoch nicht in ausgeführten Containern aktualisiert. Zu diesem Zweck müssen Sie einen neuen Container mit dem neuesten SQL Server-Containerimage erstellen und die Daten in diesen neuen Container migrieren.

1. Stellen Sie sicher, dass Sie eine der [Datenpersistenzmethoden](#persist) für Ihren vorhandenen SQL Server-Container verwenden. So können Sie einen neuen Container mit den gleichen Daten starten.

1. Halten Sie den SQL Server-Container mit dem Befehl `docker stop` an.

1. Erstellen Sie mit `docker run` einen neuen SQL Server-Container, und geben Sie entweder ein zugeordnetes Hostverzeichnis oder einen Datenvolumecontainer an. Verwenden Sie das jeweilige Tag für Ihr SQL Server-Upgrade. Der neue Container verwendet nun eine neue Version von SQL Server mit Ihren vorhandenen SQL Server-Daten.

   > [!IMPORTANT]
   > Upgrades werden derzeit nur zwischen RC1, RC2 und der allgemein verfügbaren Version unterstützt.

1. Überprüfen Sie Ihre Datenbanken und Daten im neuen Container.

1. Entfernen Sie den alten Container optional mit `docker rm`.

## <a id="buildnonrootcontainer"></a> Erstellen und Ausführen von SQL Server 2017-Containern ohne Root-Berechtigung

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

„docker exec“ in den Container.
```bash
docker exec -it sql1 bash
```

Führen Sie `whoami` aus, um den Benutzer zurückzugeben, der innerhalb des Containers ausgeführt wird.

```bash
whoami
```

## <a id="nonrootuser"></a> Ausführen eines Containers als anderer Nicht-Root-Benutzer auf dem Host

Um den SQL Server-Container als anderer Nicht-Root-Benutzer auszuführen, fügen Sie dem Befehl „docker run“ das Flag „-u“ hinzu. Der Container ohne Root-Berechtigung hat die Einschränkung, dass er als Teil der Root-Gruppe ausgeführt werden muss, es sei denn, es wird ein Volume für „/var/opt/mssql“ bereitgestellt, auf das der Nicht-Root-Benutzer zugreifen kann. Die Root-Gruppe gewährt dem Nicht-Root-Benutzer keine zusätzlichen Root-Berechtigungen.

**Ausführen als Benutzer mit einer UID 4000**

Sie können SQL Server mit einer benutzerdefinierten UID starten. Der folgende Befehl startet beispielsweise SQL Server mit der UID 4000:
```bash
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyStrongPassword" --cap-add SYS_PTRACE -u 4000:0 -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-latest
```

> [!Warning]
> Stellen Sie sicher, dass der SQL Server-Container einen benannten Benutzer wie „mssql“ oder „root“ hat, denn anderenfalls kann SQLCMD nicht innerhalb des Containers ausgeführt werden. Sie können überprüfen, ob der SQL Server-Container als benannter Benutzer ausgeführt wird, indem Sie `whoami` innerhalb des Containers ausführen.

**Ausführen des Containers ohne Root-Berechtigung als Root-Benutzer**

Sie können den Container ohne Root-Berechtigung ggf. als Root-Benutzer ausführen. Dadurch würde der Container auch automatisch sämtliche Dateiberechtigungen erhalten, da er eine höhere Berechtigung hat.

```bash
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyStrongPassword" -u 0:0 -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-latest
```

**Ausführen als Benutzer auf Ihrem Hostcomputer**

Mit dem folgenden Befehl können Sie SQL Server mit einem vorhandenen Benutzer auf dem Hostcomputer starten:
```bash
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyStrongPassword" --cap-add SYS_PTRACE -u $(id -u myusername):0 -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-latest
```

**Ausführen als anderer Benutzer und Gruppe**

Sie können SQL Server mit einem benutzerdefinierten Benutzer oder einer benutzerdefinierten Gruppe starten. In diesem Beispiel verfügt das bereitgestellte Volume über Berechtigungen, die für den Benutzer oder die Gruppe auf dem Hostcomputer konfiguriert sind.

```bash
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyStrongPassword" --cap-add SYS_PTRACE -u (id -u myusername):(id -g myusername) -v /path/to/mssql:/var/opt/mssql -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-latest
```

## <a id="storagepermissions"></a> Konfigurieren von persistenten Speicherberechtigungen für Container ohne Root-Berechtigung

Um dem Nicht-Root-Benutzer den Zugriff auf DB-Dateien zu ermöglichen, die sich auf bereitgestellten Volumes befinden, stellen Sie sicher, dass der Benutzer bzw. die Gruppe, unter der Sie den Container ausführen, auf den persistenten Dateispeicher zugreifen kann.  

Mit diesem Befehl können Sie den aktuellen Besitzer der Datenbankdateien ermitteln.

```bash
ls -ll <database file dir>
```

Führen Sie einen der folgenden Befehle aus, wenn SQL Server keinen Zugriff auf persistente Datenbankdateien hat.

**Zuweisen der Berechtigungen für die Root-Gruppe zum Lesen und Schreiben der DB-Dateien**

Erteilen Sie die Root-Gruppenberechtigungen für die folgenden Verzeichnisse, damit der SQL Server-Container ohne Root-Berechtigungen Zugriff auf Datenbankdateien hat.

```bash
chgrp -R 0 <database file dir>
chmod -R g=u <database file dir>
```

**Festlegen des Nicht-Root-Benutzers als Besitzer der Dateien**

Dies kann der standardmäßig festgelegte Nicht-Root-Benutzer oder ein anderer Nicht-Root-Benutzer sein, den Sie angeben möchten. In diesem Beispiel haben wir die UID 10001 als Nicht-Root-Benutzer festgelegt.

```bash
chown -R 10001:0 <database file dir>
```

## <a id="changefilelocation"></a> Ändern des Standardspeicherorts der Datei

Fügen Sie die Variable `MSSQL_DATA_DIR` hinzu, um Ihr Datenverzeichnis in Ihrem `docker run`-Befehl zu ändern, und stellen Sie dann ein Volume an dem Speicherort bereit, auf den der Benutzer Ihres Containers Zugriff hat.

```bash
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyStrongPassword" -e "MSSQL_DATA_DIR=/my/file/path" -v /my/host/path:/my/file/path -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-latest
```

## <a id="troubleshooting"></a> Problembehandlung

In den folgenden Abschnitten finden Sie Vorschläge zur Problembehandlung bei der Ausführung von SQL Server in Containern.

### <a name="docker-command-errors"></a>Fehler bei Docker-Befehlen

Wenn Fehler bei `docker`-Befehlen auftreten, sollten Sie sicherstellen, dass der Docker-Dienst ausgeführt wird und versuchen, diesen mit erhöhten Berechtigungen auszuführen.

Unter Linux kann beispielsweise folgender Fehler auftreten, wenn Sie `docker`-Befehle ausführen:

```
Cannot connect to the Docker daemon. Is the docker daemon running on this host?
```

Wenn dieser Fehler unter Linux auftritt, versuchen Sie, diese Befehle mit `sudo` auszuführen. Wenn dieser Versuch fehlschlägt, sollten Sie überprüfen, ob der Docker-Dienst ausgeführt wird und diesen ggf. starten.

```bash
sudo systemctl status docker
sudo systemctl start docker
```

Vergewissern Sie sich unter Windows, dass Sie PowerShell oder die Eingabeaufforderung als Administrator starten.

### <a name="sql-server-container-startup-errors"></a>Startfehler bei SQL Server-Containern

Wenn der SQL Server-Container nicht ausgeführt werden kann, versuchen Sie Folgendes:

- Wenn ein Fehler wie **failed to create endpoint CONTAINER_NAME on network bridge. Error starting proxy: listen tcp 0.0.0.0:1433 bind: address already in use.** (Der Endpunkt CONTAINERNAME konnte auf der Netzwerkbrücke nicht erstellt werden. Fehler beim Starten des Proxy: listen tcp 0.0.0.0:1433 bind: Adresse wird bereits verwendet.) auftritt, liegt das daran, dass Sie versuchen, den Containerport 1433 einem Port zuzuordnen, der bereits verwendet wird. Dieser Fall kann eintreten, wenn Sie SQL Server lokal auf dem Hostcomputer ausführen. Dieser Fall kann außerdem eintreten, wenn Sie zwei SQL Server-Container starten und versuchen, diese demselben Hostport zuzuordnen. Verwenden Sie in diesem Fall den Parameter `-p`, um den Containerport 1433 einem anderen Hostport zuzuordnen. Beispiel: 

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
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1400:1433 -d mcr.microsoft.com/mssql/server:2019-GA-ubuntu-16.04`.
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1400:1433 -d mcr.microsoft.com/mssql/server:2019-GA-ubuntu-16.04`.
```

::: moniker-end

- Wenn beispielsweise eine Fehlermeldung wie **Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get http://%2Fvar%2Frun%2Fdocker.sock/v1.30tdout=1&tail=all: dial unix /var/run/docker.sock: connect: permission denied** (Berechtigung während des Verbindungsversuchs mit dem Docker-Daemonsocket unter unix:///var/run/docker.sock verweigert: Get http://%2Fvar%2Frun%2Fdocker.sock/v1.30tdout=1&tail=all: dial unix /var/run/docker.sock: connect: Berechtigung verweigert.) angezeigt wird, wenn Sie versuchen, einen Container zu starten, sollten Sie Ihren Benutzer zur Docker-Gruppe in Ubuntu hinzufügen. Melden Sie sich ab und wieder an, da sich diese Änderung auf neue Sitzungen auswirkt. 

   ```bash
    usermod -aG docker $USER
   ```
- Überprüfen Sie, ob Fehlermeldungen in Bezug auf den Container vorhanden sind.

    ```bash
    docker logs e69e056c702d
    ```

- Stellen Sie sicher, dass die Mindestanforderungen für den Arbeitsspeicher und den Datenträger erfüllt werden, die im Abschnitt [Voraussetzungen](quickstart-install-connect-docker.md#requirements) des Schnellstartartikels aufgelistet werden.

- Wenn Sie Containerverwaltungssoftware verwenden, müssen Sie sicherstellen, dass diese die Ausführung von Containerprozessen als Root unterstützt. Der Prozess „sqlservr“ im Container wird als Root ausgeführt.

- Überprüfen Sie die [Setup- und Fehlerprotokolle für SQL Server](#errorlogs).

### <a name="enable-dump-captures"></a>Aktivieren der Sicherungserfassung

Wenn der SQL Server-Prozess innerhalb des Containers fehlschlägt, sollten Sie einen neuen Container erstellen, bei dem **SYS_PTRACE** aktiviert ist. Dadurch kann die Linux-Funktion zur Nachverfolgung eines Prozesses genutzt werden, die für das Erstellen einer Sicherungsdatei für eine Ausnahme erforderlich ist. Die Sicherungsdatei kann vom Support genutzt werden, um das Problem zu beheben. Die Funktion wird mit folgendem docker run-Befehl aktiviert.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

```bash
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -e "MSSQL_PID=Developer" --cap-add SYS_PTRACE -p 1401:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

```bash
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -e "MSSQL_PID=Developer" --cap-add SYS_PTRACE -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-GA-ubuntu-16.04
```

::: moniker-end

### <a name="sql-server-connection-failures"></a>SQL Server-Verbindungsfehler

Wenn Sie keine Verbindung mit der SQL Server-Instanz herstellen können, die in Ihrem Container ausgeführt wird, versuchen Sie Folgendes:

- Stellen Sie sicher, dass Ihr SQL Server-Container ausgeführt wird, indem Sie die Spalte **STATUS** der Ausgabe von `docker ps -a` überprüfen. Starten Sie ihn andernfalls mit `docker start <Container ID>`.

- Wenn Sie den Container nicht dem Standardhostport 1433 zugeordnet haben, müssen Sie den Port in der Verbindungszeichenfolge angeben. Die Portzuordnung ist in der Spalte **PORTS** der Ausgabe von `docker ps -a` ersichtlich. Folgender Befehl verbindet sqlcmd beispielsweise mit einem Container, der Port 1401 lauscht:

    ```bash
    sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
    ```

    ```PowerShell
    sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
    ```

- Wenn Sie `docker run` mit einem vorhandenen zugeordneten Datenvolume oder Datenvolumecontainer verwendet haben, ignoriert SQL Server den Wert von `MSSQL_SA_PASSWORD`. Stattdessen wird das vorkonfigurierte SA-Benutzerkennwort aus den SQL Server-Daten im Datenvolume oder Datenvolumecontainer verwendet. Vergewissern Sie sich, dass Sie das SA-Kennwort verwenden, das den Daten zugeordnet ist, an die Sie anfügen.

- Überprüfen Sie die [Setup- und Fehlerprotokolle für SQL Server](#errorlogs).

### <a name="sql-server-availability-groups"></a>SQL Server-Verfügbarkeitsgruppen

Wenn Sie Docker mit SQL Server-Verfügbarkeitsgruppen verwenden, gibt es zwei zusätzliche Voraussetzungen.

- Ordnen Sie den Port zu, der für die Replikatkommunikation verwendet wird (standardmäßig 5022). Geben Sie in Ihrem `docker run`-Befehl beispielsweise `-p 5022:5022` an.

- Legen Sie den Containerhostnamen mit dem Parameter `-h YOURHOSTNAME` des Befehls `docker run` explizit fest. Dieser Hostname wird verwendet, wenn Sie die Verfügbarkeitsgruppe konfigurieren. Wenn Sie ihn nicht mit `-h` angeben, wird standardmäßig die Container-ID verwendet.

### <a id="errorlogs"></a> Setup- und Fehlerprotokolle für SQL Server

Sie finden Sie Setup- und Fehlerprotokolle für SQL Server unter **/var/opt/mssql/log**. Wenn der Container nicht ausgeführt wird, starten Sie diesen zunächst. Verwenden Sie dann eine interaktive Eingabeaufforderung, um die Protokolle zu überprüfen.

```bash
docker start e69e056c702d
docker exec -it e69e056c702d "bash"
```

Führen Sie folgende Befehle über die Bash-Sitzung in Ihrem Container aus:

```bash
cd /var/opt/mssql/log
cat setup*.log
cat errorlog
```

> [!TIP]
> Wenn Sie bei der Erstellung des Containers ein Hostverzeichnis in **/var/opt/mssql** eingebunden haben, können Sie stattdessen im Unterverzeichnis **log** des auf dem Host zugeordneten Pfads suchen.

## <a name="next-steps"></a>Nächste Schritte

Der [Schnellstart](quickstart-install-connect-docker.md) erleichtert Ihnen den Einstieg in die Verwendung von SQL Server 2017-Containerimages in Docker.

Ressourcen, Feedback und Informationen über bekannte Probleme finden Sie im [GitHub-Repository „mssql-docker“](https://github.com/Microsoft/mssql-docker).

[Hochverfügbarkeit für SQL Server-Container](sql-server-linux-container-ha-overview.md)
