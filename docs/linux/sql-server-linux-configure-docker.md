---
title: Konfigurationsoptionen für SQL Server auf docker
description: Entdecken Sie verschiedene Möglichkeiten der Verwendung von und Interaktion mit SQL Server 2017-und 2019-Vorschau Container Images in Docker. Dies umfasst das Beibehalten von Daten, das Kopieren von Dateien und das Beheben von Problemen.
author: vin-yu
ms.author: vinsonyu
ms.reviewer: vanto
ms.date: 01/17/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
moniker: '>= sql-server-linux-2017 || >= sql-server-2017 || =sqlallproducts-allversions'
ms.openlocfilehash: d24bb3566195c71a3b62d16fab867ab5085404b7
ms.sourcegitcommit: d667fa9d6f1c8035f15fdb861882bd514be020d9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68388381"
---
# <a name="configure-sql-server-container-images-on-docker"></a>Konfigurieren von SQL Server Container Images in docker

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Artikel wird erläutert, wie Sie das [Container Image MSSQL-Server-Linux](https://hub.docker.com/_/microsoft-mssql-server) mit docker konfigurieren und verwenden. Dieses Image enthält SQL Server für Linux (basierend auf Ubuntu 16.04). Es kann unter Linux mit der Docker-Engine 1.8 und höher und in Docker für Mac bzw. Windows verwendet werden.

> [!NOTE]
> Dieser Artikel konzentriert sich speziell auf die Verwendung des MSSQL-Server-Linux-Images. Das Windows-Abbild wird nicht abgedeckt, Sie können sich jedoch auf der [Seite MSSQL-Server-Windows docker Hub](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)ausführlicher darüber informieren.

## <a name="pull-and-run-the-container-image"></a>Übertragen mithilfe von Pull und Ausführen von Containerimages

Um die Docker-Container Images für SQL Server 2017 und SQL Server 2019 Preview abzurufen und auszuführen, befolgen Sie die Voraussetzungen und Schritte in der folgenden Schnellstartanleitung:

- [Ausführen des SQL Server 2017-Container Images mit docker](quickstart-install-connect-docker.md?view=sql-server-2017)
- [Ausführen des SQL Server 2019-Vorschau Container Images mit docker](quickstart-install-connect-docker.md?view=sql-server-ver15)

Dieser Konfigurations Artikel enthält zusätzliche Verwendungs Szenarien in den folgenden Abschnitten.

<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="rhel"></a>Ausführen von RHEL-basierten Container Images

Die gesamte Dokumentation zu SQL Server Linux-Container Images verweist auf Ubuntu-basierte Container. Ab SQL Server 2019 Preview können Sie Container basierend auf Red Hat Enterprise Linux (RHEL) verwenden. Ändern Sie in all ihren docker-Befehlen das containerrepository von **MCR.Microsoft.com/MSSQL/Server:2019-CTP3.1-Ubuntu** in **MCR.Microsoft.com/MSSQL/RHEL/Server:2019-CTP3.1** .

Der folgende Befehl ruft beispielsweise den neuesten SQL Server 2019-Vorschau Container ab, der RHEL verwendet:

```bash
sudo docker pull mcr.microsoft.com/mssql/rhel/server:2019-CTP3.1
```

```PowerShell
docker pull mcr.microsoft.com/mssql/rhel/server:2019-CTP3.1
```

::: moniker-end

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="production"></a>Ausführen von Produktions Container Images

Der Schnellstart im vorherigen Abschnitt führt die kostenlose Developer Edition von SQL Server von Docker Hub aus. Die meisten Informationen gelten weiterhin, wenn Sie Produktions Container Images ausführen möchten, z. b. Enterprise, Standard oder Web Edition. Es gibt jedoch einige Unterschiede, die hier beschrieben werden.

- Sie können SQL Server nur in einer Produktionsumgebung verwenden, wenn Sie über eine gültige Lizenz verfügen. Sie können [hier](https://go.microsoft.com/fwlink/?linkid=857693)eine kostenlose SQL Server Express Produktionslizenz erwerben. SQL Server Standard-und Enterprise Edition-Lizenzen sind über die [Microsoft-Volumen Lizenzierung](https://www.microsoft.com/licensing/default.aspx)verfügbar.


- Das Entwickler Container Image kann auch so konfiguriert werden, dass die Produktions Editionen ausgeführt werden. Führen Sie die folgenden Schritte aus, um die Produktions Editionen auszuführen:

Überprüfen Sie die Anforderungen und die Prozeduren in der [Schnellstart](quickstart-install-connect-docker.md)Anleitung. Sie müssen die Production Edition mit der **MSSQL_PID** -Umgebungsvariablen angeben. Im folgenden Beispiel wird gezeigt, wie das neueste SQL Server 2017-Container Image für die Enterprise Edition ausgeführt wird:

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
> Wenn Sie den Wert **Y** an die Umgebungsvariable **ACCEPT_EULA** und einen Editions Wert an **MSSQL_PID**übergeben, legen Sie fest, dass Sie über eine gültige und vorhandene Lizenz für die Edition und die Version von SQL Server verfügen, die Sie verwenden möchten. Außerdem erklären Sie, dass die Verwendung von SQL Server Software, die in einem docker-Container Image ausgeführt wird, den Bedingungen Ihrer SQL Server Lizenz unterliegt.

> [!NOTE]
> Eine vollständige Liste der möglichen Werte für **MSSQL_PID**finden Sie unter [Konfigurieren von SQL Server Einstellungen mit Umgebungsvariablen unter Linux](sql-server-linux-configure-environment-variables.md).

::: moniker-end

## <a name="connect-and-query"></a>Verbinden und Abfragen

Sie können SQL Server in einem Container entweder außerhalb des Containers oder innerhalb des Containers verbinden und Abfragen. In den folgenden Abschnitten werden beide Szenarien erläutert. 

### <a name="tools-outside-the-container"></a>Tools außerhalb des Containers

Sie können von jedem externen Linux-, Windows-oder macOS-Tool, das SQL-Verbindungen unterstützt, eine Verbindung mit der SQL Server Instanz auf dem docker-Computer herstellen. Einige gängige Tools sind:

- [sqlcmd](sql-server-linux-setup-tools.md)
- [Visual Studio Code](sql-server-linux-develop-use-vscode.md)
- [SQL Server Management Studio (SSMS) unter Windows](sql-server-linux-manage-ssms.md)

Im folgenden Beispiel wird **sqlcmd** verwendet, um eine Verbindung mit SQL Server herzustellen, die in einem docker-Container ausgeführt wird. Die IP-Adresse in der Verbindungs Zeichenfolge ist die IP-Adresse des Host Computers, auf dem der Container ausgeführt wird.

```bash
sqlcmd -S 10.3.2.4 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4 -U SA -P "<YourPassword>"
```

Wenn Sie einen hostport zugeordnet haben, der nicht der Standard- **1433**ist, fügen Sie diesen Port der Verbindungs Zeichenfolge hinzu. Wenn Sie z. b. `-p 1400:1433` in Ihrem `docker run` Befehl festgelegt haben, stellen Sie die Verbindung durch explizites angeben von Port 1400

```bash
sqlcmd -S 10.3.2.4,1400 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1400 -U SA -P "<YourPassword>"
```

### <a name="tools-inside-the-container"></a>Tools innerhalb des Containers

Ab SQL Server 2017 Preview sind die [SQL Server Befehlszeilen Tools](sql-server-linux-setup-tools.md) im Container Image enthalten. Wenn Sie eine interaktive Eingabeaufforderung an das Image anfügen, können Sie die Tools lokal ausführen.

1. Verwenden Sie den Befehl `docker exec -it`, um in Ihrem laufenden Container eine interaktive Bash-Shell zu starten. Im folgenden Beispiel `e69e056c702d` ist die Container-ID.

    ```bash
    docker exec -it e69e056c702d "bash"
    ```

    > [!TIP]
    > Sie müssen nicht immer die gesamte Container-ID angeben. Sie müssen nur ausreichend Zeichen angeben, um Sie eindeutig zu identifizieren. In diesem Beispiel reicht es aus, oder `e6` `e69` anstelle der vollständigen ID zu verwenden.

2. Stellen Sie eine lokale Verbindung mit „sqlcmd“ her. Beachten Sie, dass sqlcmd nicht standardmäßig im Pfad vorhanden ist. Daher müssen Sie den vollständigen Pfad angeben.

    ```bash
    /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '<YourPassword>'
    ```

3. Wenn Sie mit sqlcmd fertig sind `exit`, geben Sie ein.

4. Wenn Sie mit der interaktiven Eingabeaufforderung fertig sind, `exit`geben Sie ein. Der Container wird auch nach dem Beenden der interaktiven Bash-Shell weiter ausgeführt.

## <a name="run-multiple-sql-server-containers"></a>Mehrere SQL Server Container ausführen

Docker bietet eine Möglichkeit, mehrere SQL Server Container auf demselben Host Computer auszuführen. Dies ist der Ansatz für Szenarien, die mehrere Instanzen von SQL Server auf demselben Host erfordern. Jeder Container muss sich selbst an einem anderen Port verfügbar machen.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

Im folgenden Beispiel werden zwei SQL Server 2017-Container erstellt und den Ports **1401** und **1402** auf dem Host Computer zugeordnet.

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

Im folgenden Beispiel werden zwei SQL Server 2019-Vorschau Container erstellt und den Ports **1401** und **1402** auf dem Host Computer zugeordnet.

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1402:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1402:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

::: moniker-end

Nun gibt es zwei Instanzen von SQL Server in separaten Containern ausgeführt wird. Clients können eine Verbindung mit jeder SQL Server Instanz herstellen, indem Sie die IP-Adresse des docker-Hosts und die Portnummer für den Container verwenden.

```bash
sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
sqlcmd -S 10.3.2.4,1402 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
sqlcmd -S 10.3.2.4,1402 -U SA -P "<YourPassword>"
```

## <a id="customcontainer"></a>Erstellen eines angepassten Containers

Es ist möglich, eine eigene [dockerfile-Datei](https://docs.docker.com/engine/reference/builder/#usage) zu erstellen, um einen benutzerdefinierten SQL Server Container zu erstellen. Weitere Informationen finden Sie in [einer Demo, in der SQL Server und eine Node-Anwendung kombiniert](https://github.com/twright-msft/mssql-node-docker-demo-app)werden. Wenn Sie eine eigene dockerfile-Datei erstellen, achten Sie auf den Vordergrund Prozess, da dieser Prozess die Lebensdauer des Containers steuert. Wenn Sie beendet wird, wird der Container heruntergefahren. Wenn Sie z. b. ein Skript ausführen und SQL Server starten möchten, stellen Sie sicher, dass der SQL Server Prozess der Rechte Befehl ist. Alle anderen Befehle werden im Hintergrund ausgeführt. Dies wird im folgenden Befehl in einer dockerfile-Datei veranschaulicht:

```bash
/usr/src/app/do-my-sql-commands.sh & /opt/mssql/bin/sqlservr
```

Wenn Sie die Befehle im vorherigen Beispiel zurückgesetzt haben, wird der Container heruntergefahren, wenn das Do-My-SQL-Commands.sh-Skript abgeschlossen wird.

## <a id="persist"></a>Beibehalten von Daten

Die SQL Server Konfigurationsänderungen und Datenbankdateien werden im Container beibehalten, auch wenn Sie den Container mit `docker stop` und `docker start`neu starten. Wenn Sie jedoch den Container mit `docker rm`entfernen, wird alles im Container gelöscht, einschließlich SQL Server und der Datenbanken. Im folgenden Abschnitt wird erläutert, wie **Datenvolumes** verwendet werden, um Ihre Datenbankdateien beizubehalten, auch wenn die zugeordneten Container gelöscht werden.

> [!IMPORTANT]
> Für SQL Server ist es wichtig, dass Sie die Daten Persistenz in docker verstehen. Zusätzlich zur Erörterung dieses Abschnitts finden Sie in der Docker-Dokumentation Informationen zum [Verwalten von Daten in docker-Containern](https://docs.docker.com/engine/tutorials/dockervolumes/).

### <a name="mount-a-host-directory-as-data-volume"></a>Einbinden eines Host Verzeichnisses als Daten Volume

Die erste Option besteht darin, ein Verzeichnis auf dem Host als Daten Volume in Ihrem Container zu einbinden. Verwenden Sie hierzu den `docker run` Befehl mit dem `-v <host directory>:/var/opt/mssql` -Flag. Dadurch können die Daten zwischen den Container Ausführungen wieder hergestellt werden.

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
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

::: moniker-end

Mit dieser Technik können Sie auch die Dateien auf dem Host außerhalb von Docker freigeben und anzeigen.

> [!IMPORTANT]
> Die hostvolumezuordnung für docker unter Mac mit dem SQL Server für Linux Abbild wird zurzeit nicht unterstützt. Verwenden Sie stattdessen datenvolumecontainer. Diese Einschränkung ist spezifisch für das `/var/opt/mssql` Verzeichnis. Das Lesen aus einem bereitgestellten Verzeichnis funktioniert einwandfrei. Beispielsweise können Sie ein Host Verzeichnis mithilfe von-v auf einem Mac einbinden und eine Sicherung aus einer BAK-Datei wiederherstellen, die sich auf dem Host befindet.

### <a name="use-data-volume-containers"></a>Verwenden von datenvolumecontainern

Die zweite Option ist die Verwendung eines datenvolumecontainers. Sie können einen datenvolumecontainer erstellen, indem Sie anstelle eines Host Verzeichnisses mit dem `-v` -Parameter einen Volumenamen angeben. Im folgenden Beispiel wird ein frei gegebenes Daten Volume mit dem Namen **sqlvolume**erstellt.

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
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v sqlvolume:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v sqlvolume:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```
::: moniker-end

> [!NOTE]
> Dieses Verfahren zum impliziten Erstellen eines Datenvolumens im Befehl "ausführen" funktioniert nicht mit älteren Versionen von Docker. Verwenden Sie in diesem Fall die expliziten Schritte, die in der Docker-Dokumentation beschrieben sind, [und erstellen und Einbinden eines datenvolumecontainers](https://docs.docker.com/engine/tutorials/dockervolumes/#creating-and-mounting-a-data-volume-container).

Auch wenn Sie diesen Container anhalten und entfernen, bleibt das Daten Volume erhalten. Sie können Sie mit dem `docker volume ls` Befehl anzeigen.

```bash
docker volume ls
```

Wenn Sie dann einen weiteren Container mit dem gleichen Volumenamen erstellen, verwendet der neue Container die gleichen SQL Server Daten, die im Volume enthalten sind.

Um einen datenvolumecontainer zu entfernen, `docker volume rm` verwenden Sie den Befehl.

> [!WARNING]
> Wenn Sie den datenvolumecontainer löschen, werden alle SQL Server Daten im Container *dauerhaft* gelöscht.

### <a name="backup-and-restore"></a>Sichern und Wiederherstellen

Zusätzlich zu diesen Container Techniken können Sie auch Standard SQL Server Sicherungs-und Wiederherstellungsverfahren verwenden. Sie können Sicherungsdateien verwenden, um Ihre Daten zu schützen oder die Daten auf eine andere SQL Server Instanz zu verschieben. Weitere Informationen finden Sie unter [Sichern und Wiederherstellen SQL Server-Datenbanken unter Linux](sql-server-linux-backup-and-restore-database.md).

> [!WARNING]
> Wenn Sie Sicherungen erstellen, stellen Sie sicher, dass die Sicherungsdateien außerhalb des Containers erstellt oder kopiert werden. Andernfalls werden die Sicherungsdateien auch gelöscht, wenn der Container entfernt wird.

## <a name="execute-commands-in-a-container"></a>Ausführen von Befehlen in einem Container

Wenn Sie einen ausgelaufenden Container haben, können Sie Befehle innerhalb des Containers von einem Host Terminal ausführen.

So erhalten Sie die Container-ID:

```bash
docker ps
```

Zum Starten eines bash-Terminals im Container führen Sie Folgendes aus:

```bash
docker exec -it <Container ID> /bin/bash
```

Nun können Sie Befehle ausführen, als ob Sie Sie am Terminal innerhalb des Containers ausführen. Wenn Sie fertig sind, geben Sie `exit` ein. Dies wird in der interaktiven Befehls Sitzung beendet, der Container wird jedoch weiterhin ausgeführt.

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
## <a id="tz"></a>Konfigurieren der Zeitzone

Um SQL Server in einem Linux-Container mit einer bestimmten Zeitzone auszuführen, konfigurieren Sie die **TZ** -Umgebungsvariable. Um den richtigen Zeit Zonen Wert zu ermitteln, führen **Sie den Befehl tzselect** an einer Linux bash-Eingabeaufforderung aus:

```bash
tzselect
```

Nach dem Auswählen der Zeitzone zeigt **tzselect** eine Ausgabe ähnlich der folgenden an:

```bash
The following information has been given:

        United States
        Pacific

Therefore TZ='America/Los_Angeles' will be used.
```

Sie können diese Informationen verwenden, um die gleiche Umgebungsvariable in Ihrem Linux-Container festzulegen. Im folgenden Beispiel wird gezeigt, wie SQL Server in einem Container in der `Americas/Los_Angeles` Zeitzone ausgeführt wird:

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
   -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

```PowerShell
sudo docker run -e 'ACCEPT_EULA=Y' -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
   -p 1433:1433 --name sql1 `
   -e "TZ=America/Los_Angeles" `
   -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```
::: moniker-end

## <a id="tags"></a>Ausführen eines bestimmten SQL Server Container Images

Es gibt Szenarien, in denen Sie möglicherweise nicht das neueste SQL Server Container Image verwenden möchten. Führen Sie die folgenden Schritte aus, um ein bestimmtes SQL Server Container Image auszuführen:

1. Identifizieren Sie das docker- **Tag** für das Release, das Sie verwenden möchten. Informationen zu den verfügbaren Tags finden Sie auf [der Docker Hub-Seite für MSSQL-Server-Linux](https://hub.docker.com/_/microsoft-mssql-server).

2. Ziehen Sie das SQL Server Container Image mit dem-Tag. Wenn Sie z. b. das RC1-Bild `<image_tag>` per Pull abrufen möchten, `rc1`ersetzen Sie im folgenden Befehl durch.

   ```bash
   docker pull mcr.microsoft.com/mssql/server:<image_tag>
   ```

3. Wenn Sie einen neuen Container mit diesem Image ausführen möchten, geben Sie den Tagnamen im `docker run` Befehl an. Ersetzen `<image_tag>` Sie im folgenden Befehl durch die Version, die Sie ausführen möchten.

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d mcr.microsoft.com/mssql/server:<image_tag>
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d mcr.microsoft.com/mssql/server:<image_tag>
   ```

Diese Schritte können auch zum Herabstufen eines vorhandenen Containers verwendet werden. Beispielsweise können Sie einen Rollback oder Downgrade für einen Container ausführen, um Probleme zu beheben oder zu testen. Zum Herabstufen eines laufenden Containers müssen Sie eine persistenztechnik für den Datenordner verwenden. Führen Sie dieselben Schritte aus, die im [Abschnitt Upgrade](#upgrade)beschrieben werden, aber geben Sie den Tagnamen der älteren Version an, wenn Sie den neuen Container ausführen.

## <a id="version"></a>Überprüfen Sie die Container Version.

Wenn Sie die Version von SQL Server in einem ausgelaufenden docker-Container kennen möchten, führen Sie den folgenden Befehl aus, um ihn anzuzeigen. Ersetzen `<Container ID or name>` Sie dies durch die Zielcontainer-ID oder den Namen. Ersetzen `<YourStrong!Passw0rd>` Sie dies durch das SQL Server Kennwort für die sa-Anmeldung.

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

Sie können auch die SQL Server Version und Buildnummer für ein Ziel-docker-Container Image ermitteln. Der folgende Befehl zeigt die SQL Server Version und Buildinformationen für das Image " **Microsoft/MSSQL-Server-Linux: 2017-Latest** " an. Dies geschieht durch Ausführen eines neuen Containers mit der Umgebungsvariablen **PAL_PROGRAM_INFO = 1**. Der resultierende Container wird sofort beendet, und `docker rm` der Befehl entfernt ihn.

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

## <a id="upgrade"></a>SQL Server in Containern aktualisieren

Um das Container Image mit Docker zu aktualisieren, müssen Sie zuerst das Tag für das Release für das Upgrade ermitteln. Rufen Sie diese Version mit dem `docker pull` folgenden Befehl aus der Registrierung ab:

```bash
docker pull mcr.microsoft.com/mssql/server:<image_tag>
```

Dadurch wird das SQL Server Abbild für alle neu erstellten Container aktualisiert, aber SQL Server in Containern, die ausgeführt werden, werden nicht aktualisiert. Zu diesem Zweck müssen Sie einen neuen Container mit dem neuesten SQL Server Container Image erstellen und die Daten zu diesem neuen Container migrieren.

1. Stellen Sie sicher, dass Sie eine der [Daten persistenztechniken](#persist) für Ihren vorhandenen SQL Server-Container verwenden. Dies ermöglicht es Ihnen, einen neuen Container mit denselben Daten zu starten.

1. Beendet den SQL Server-Container mit `docker stop` dem Befehl.

1. Erstellen Sie einen neuen SQL Server Container `docker run` mit, und geben Sie entweder ein zugeordnetes Host Verzeichnis oder einen datenvolumecontainer an. Stellen Sie sicher, dass Sie das jeweilige Tag für das SQL Server Upgrade verwenden. Der neue Container verwendet nun eine neue Version von SQL Server mit Ihren vorhandenen SQL Server Daten.

   > [!IMPORTANT]
   > Das Upgrade wird zurzeit nur zwischen RC1, RC2 und GA unterstützt.

1. Überprüfen Sie Ihre Datenbanken und Daten im neuen Container.

1. Entfernen Sie optional den alten Container mit `docker rm`.

## <a id="troubleshooting"></a> Problembehandlung

In den folgenden Abschnitten finden Sie Vorschläge zur Problembehandlung beim Ausführen von SQL Server in Containern.

### <a name="docker-command-errors"></a>Docker-Befehls Fehler

Wenn Sie für `docker` Befehle Fehler erhalten, stellen Sie sicher, dass der Docker-Dienst ausgeführt wird, und versuchen Sie, mit erhöhten Berechtigungen auszuführen.

Unter Linux wird z. b. beim Ausführen `docker` von Befehlen möglicherweise der folgende Fehler angezeigt:

```
Cannot connect to the Docker daemon. Is the docker daemon running on this host?
```

Wenn Sie diesen Fehler unter Linux erhalten, führen Sie die gleichen Befehle aus, die `sudo`mit vorangestellt sind. Wenn dies fehlschlägt, überprüfen Sie, ob der Docker-Dienst ausgeführt wird, und starten Sie ihn bei Bedarf.

```bash
sudo systemctl status docker
sudo systemctl start docker
```

Vergewissern Sie sich unter Windows, dass Sie PowerShell oder die Eingabeaufforderung als Administrator starten.

### <a name="sql-server-container-startup-errors"></a>Fehler beim Starten des SQL Server Containers.

Wenn der SQL Server-Container nicht ausgeführt werden kann, versuchen Sie es mit den folgenden Tests:

- Wenn eine Fehlermeldung wie z **. b. "Fehler beim Erstellen des Endpunkt CONTAINER_NAME auf der Netzwerk Brücke" angezeigt wird. Fehler beim Starten des Proxys: lauschen Sie TCP 0.0.0.0:1433 BIND: die Adresse wird bereits verwendet. "** , versuchen Sie, den containerport 1433 einem bereits verwendeten Port zuzuordnen. Dies kann vorkommen, wenn Sie SQL Server lokal auf dem Host Computer ausführen. Dies kann auch vorkommen, wenn Sie zwei SQL Server Container starten und versuchen, beide dem gleichen hostport zuzuordnen. Wenn dies der Fall ist, `-p` verwenden Sie den-Parameter, um den containerport 1433 einem anderen hostport zuzuordnen. Zum Beispiel: 

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
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1400:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu`.
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1400:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu`.
```

::: moniker-end

- Wenn beim Versuch, eine Verbindung mit **dem docker-daemonsocket bei Unix:///var/run/Docker.sock herzustellen, eine Fehlermeldung wie "Get-Berechtigung verweigert" angezeigt wird: Wählen Sie beim Versuch, einen Container zu starten,** die Berechtigung UNIX/var/run/Docker.sock: Connect: Berechtigung verweigert "aus, und fügen Sie dann Ihren Benutzer der Docker-Gruppe in Ubuntu hinzu. http://%2Fvar%2Frun%2Fdocker.sock/v1.30tdout=1&tail=all: Melden Sie sich ab und wieder an, da sich diese Änderung auf neue Sitzungen auswirkt. 

   ```bash
    usermod -aG docker $USER
    ```
- Überprüfen Sie, ob Fehlermeldungen aus dem Container vorhanden sind.

    ```bash
    docker logs e69e056c702d
    ```

- Stellen Sie sicher, dass Sie die minimalen Arbeitsspeicher-und Datenträger Anforderungen erfüllen, die im Abschnitt " [Voraussetzungen](quickstart-install-connect-docker.md#requirements) " des Schnellstart Artikels angegeben sind

- Wenn Sie eine beliebige Container Verwaltungssoftware verwenden, stellen Sie sicher, dass Container Prozesse unterstützt werden, die als root ausgeführt werden. Der sqlservr-Prozess im Container wird als root-Prozess ausgeführt.

- Überprüfen Sie die [SQL Server Setup-und Fehlerprotokolle](#errorlogs).

### <a name="enable-dump-captures"></a>Aktivieren von dumperfassungen

Wenn der SQL Server Prozess innerhalb des Containers fehlschlägt, sollten Sie einen neuen Container mit aktiviertem **SYS_PTRACE** erstellen. Dadurch wird die Linux-Funktion hinzugefügt, um einen Prozess zu verfolgen, der zum Erstellen einer Dumpdatei bei einer Ausnahme erforderlich ist. Die Dumpdatei kann von der-Unterstützung verwendet werden, um das Problem zu beheben. Mit dem folgenden docker Run-Befehl wird diese Funktion aktiviert.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

```bash
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -e "MSSQL_PID=Developer" --cap-add SYS_PTRACE -p 1401:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

```bash
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -e "MSSQL_PID=Developer" --cap-add SYS_PTRACE -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

::: moniker-end

### <a name="sql-server-connection-failures"></a>SQL Server Verbindungsfehler

Wenn Sie keine Verbindung mit der SQL Server Instanz herstellen können, die in Ihrem Container ausgeführt wird, testen Sie die folgenden Tests:

- Stellen Sie sicher, dass Ihr SQL Server Container ausgeführt wird, indem  Sie die Spalte Status `docker ps -a` der Ausgabe überprüfen. Wenn nicht, verwenden `docker start <Container ID>` Sie, um es zu starten.

- Stellen Sie sicher, dass Sie den Port in der Verbindungs Zeichenfolge angeben, wenn Sie einen nicht standardmäßigen hostport (nicht 1433) zugeordnet haben. Sie können die Port Zuordnung in der Spalte **Ports** der `docker ps -a` Ausgabe sehen. Mit dem folgenden Befehl wird z. b. sqlcmd mit einem Container verbunden, der an Port 1401 lauscht:

    ```bash
    sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
    ```

    ```PowerShell
    sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
    ```

- Wenn Sie mit `docker run` einem vorhandenen zugeordneten Daten Volume oder datenvolumecontainer verwendet haben, SQL Server den `MSSQL_SA_PASSWORD`Wert von ignoriert. Stattdessen wird das vorkonfigurierte SA-Benutzer Kennwort aus den SQL Server Daten im datenvolumecontainer oder Daten volumecontainer verwendet. Vergewissern Sie sich, dass Sie das SA-Kennwort verwenden, das den Daten zugeordnet ist, an die Sie anhängen.

- Überprüfen Sie die [SQL Server Setup-und Fehlerprotokolle](#errorlogs).

### <a name="sql-server-availability-groups"></a>SQL Server Verfügbarkeits Gruppen

Wenn Sie docker mit SQL Server Verfügbarkeits Gruppen verwenden, gibt es zwei zusätzliche Anforderungen.

- Ordnen Sie den Port zu, der für die Replikat Kommunikation verwendet wird (Standard 5022). Geben `-p 5022:5022` Sie`docker run` z. b. als Teil des Befehls an.

- Legen Sie den Container Hostnamen explizit mit `-h YOURHOSTNAME` dem-Parameter `docker run` des-Befehls fest. Dieser Hostname wird verwendet, wenn Sie die Verfügbarkeits Gruppe konfigurieren. Wenn Sie ihn nicht mit `-h`angeben, wird standardmäßig die Container-ID verwendet.

### <a id="errorlogs"></a>SQL Server Setup-und Fehlerprotokolle

Sie können sich die SQL Server Setup-und Fehlerprotokolle in **/var/opt/MSSQL/Log**ansehen. Wenn der Container nicht ausgeführt wird, starten Sie zuerst den Container. Verwenden Sie dann eine interaktive Eingabeaufforderung, um die Protokolle zu überprüfen.

```bash
docker start e69e056c702d
docker exec -it e69e056c702d "bash"
```

Führen Sie aus der bash-Sitzung in Ihrem Container die folgenden Befehle aus:

```bash
cd /var/opt/mssql/log
cat setup*.log
cat errorlog
```

> [!TIP]
> Wenn Sie beim Erstellen des Containers ein Host Verzeichnis in **/var/opt/MSSQL** eingebunden haben, können Sie stattdessen im **Protokoll** Unterverzeichnis auf dem zugeordneten Pfad auf dem Host suchen.

## <a name="next-steps"></a>Nächste Schritte

Erste Schritte mit SQL Server 2017-Container Images in Docker, indem Sie den [Schnellstart](quickstart-install-connect-docker.md)durchlaufen.

Weitere Informationen finden Sie unter [MSSQL-docker GitHub-Repository](https://github.com/Microsoft/mssql-docker) für Ressourcen, Feedback und bekannte Probleme.

[Erkunden der Hochverfügbarkeit für SQL Server Container](sql-server-linux-container-ha-overview.md)
