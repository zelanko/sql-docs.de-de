---
title: Beginnen Sie mit SQL Server Linux-Containern in docker
titleSuffix: SQL Server
description: In dieser Schnellstartanleitung erfahren Sie, wie Sie docker verwenden, um die Container Images SQL Server 2017 und 2019 auszuführen. Anschließend erstellen Sie mit dem Hilfsprogramm „sqlcmd“ eine Datenbank und fragen diese ab.
author: vin-yu
ms.author: vinsonyu
ms.reviewer: vanto
ms.date: 05/14/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.custom: sqlfreshmay19
ms.prod_service: linux
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
moniker: '>= sql-server-linux-2017 || >= sql-server-2017 || =sqlallproducts-allversions'
zone_pivot_groups: cs1-command-shell
ms.openlocfilehash: addb8d43a48247206a59d90bac94b998d5b29a81
ms.sourcegitcommit: 73dc08bd16f433dfb2e8406883763aabed8d8727
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68329250"
---
# <a name="quickstart-run-sql-server-container-images-with-docker"></a>Schnellstart: Ausführen SQL Server Container Images mit docker

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

In diesem Schnellstart wird Docker verwendet, um das SQL Server 2017-Containerimage [mssql-server-linux](https://hub.docker.com/_/microsoft-mssql-server) mithilfe von Pull zu übertragen und auszuführen. Stellen Sie anschließend eine Verbindung mit **sqlcmd** her, um Ihre erste Datenbank zu erstellen und Abfragen auszuführen.

> [!TIP]
> Wenn Sie das SQL Server 2019 Preview-Image testen möchten, lesen Sie die [Vorschauversion SQL Server 2019 dieses Artikels](quickstart-install-connect-docker.md?view=sql-server-linux-ver15).

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

In dieser Schnellstartanleitung verwenden Sie Docker, um das SQL Server 2019-Vorschau Container Image, [MSSQL-Server](https://hub.docker.com/r/microsoft/mssql-server), abzurufen und auszuführen. Stellen Sie anschließend eine Verbindung mit **sqlcmd** her, um Ihre erste Datenbank zu erstellen und Abfragen auszuführen.

> [!TIP]
> In dieser Schnellstartanleitung werden SQL Server 2019-Vorschau Container erstellt. Wenn Sie SQL Server 2017-Container erstellen möchten, sehen Sie sich die [SQL Server 2017-Version dieses Artikels](quickstart-install-connect-docker.md?view=sql-server-linux-2017)an.
::: moniker-end

Dieses Image enthält SQL Server für Linux (basierend auf Ubuntu 16.04). Es kann unter Linux mit der Docker-Engine 1.8 und höher und in Docker für Mac bzw. Windows verwendet werden. Diese Schnellstartanleitung konzentriert sich speziell auf die Verwendung der SQL Server unter **Linux** -Image. Das Windows-Image wird hier zwar nicht behandelt, aber auf der [Docker-Hubseite zu „mssql-server-windows-developer“](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/) erhalten Sie weitere Informationen.

## <a id="requirements"></a> Erforderliche Komponenten

- Docker-Engine 1.8 und höher auf unterstütztem Linux-Betriebssystem oder Docker für Mac bzw. Windows. Weitere Informationen finden Sie unter [Install Docker (Installieren von Docker)](https://docs.docker.com/engine/installation/).
- Docker **Overlay2** Speicher Treiber. Dies ist die Standardeinstellung für die meisten Benutzer. Wenn Sie feststellen, dass Sie diesen Speicher Anbieter nicht verwenden und sich ändern müssen, lesen Sie die Anweisungen und Warnungen in der [docker-Dokumentation zum Konfigurieren von Overlay2](https://docs.docker.com/storage/storagedriver/overlayfs-driver/#configure-docker-with-the-overlay-or-overlay2-storage-driver).
- Mindestens 2 GB Speicherplatz.
- Mindestens 2 GB RAM.
- [Systemanforderungen von SQL Server unter Linux](sql-server-linux-setup.md#system)

<!--The following H2 is versioned for 2017 and 2019. Much of the content is duplicated, so
any changes to one section should be duplicated in the other-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="pullandrun2017"></a>Abrufen und Ausführen des Container Images

Bevor Sie die folgenden Schritte ausführen, stellen Sie sicher, dass Sie am Anfang dieses Artikels Ihre bevorzugte Shell (bash, PowerShell oder cmd) ausgewählt haben.

1. Ziehen Sie das SQL Server 2017 Linux-Container Image von Microsoft Container Registry.

   ::: zone pivot="cs1-bash"
   ```bash
   sudo docker pull mcr.microsoft.com/mssql/server:2017-latest
   ```
   ::: zone-end

   ::: zone pivot="cs1-powershell"
   ```PowerShell
   docker pull mcr.microsoft.com/mssql/server:2017-latest
   ```
   ::: zone-end

   ::: zone pivot="cs1-cmd"
   ```cmd
   docker pull mcr.microsoft.com/mssql/server:2017-latest
   ```
   ::: zone-end

   > [!TIP]
   > Wenn Sie das SQL Server 2019 Preview-Image testen möchten, lesen Sie die [Vorschauversion SQL Server 2019 dieses Artikels](quickstart-install-connect-docker.md?view=sql-server-linux-ver15#pullandrun2019).

   Mit dem obenstehenden Befehl wird das neueste Containerimage von SQL Server 2017 mithilfe von Pull übertragen. Wenn Sie ein bestimmtes Image übertragen möchten, fügen Sie einen Doppelpunkt und den Tagnamen hinzu (z.B. `mcr.microsoft.com/mssql/server:2017-GA-ubuntu`). Alle verfügbaren Images finden Sie auf [der MSSQL-Server-docker-Hub-Seite](https://hub.docker.com/r/microsoft/mssql-server).

   ::: zone pivot="cs1-bash"
   Für die bash-Befehle in diesem Artikel `sudo` wird verwendet. Unter MacOS ist `sudo` möglicherweise nicht erforderlich. Wenn Sie unter Linux nicht zum Ausführen von Docker `sudo` verwenden möchten, können Sie eine **docker** -Gruppe konfigurieren und dieser Gruppe Benutzer hinzufügen. Weitere Informationen finden Sie unter [Schritte nach der Installation für Linux](https://docs.docker.com/install/linux/linux-postinstall/).
   ::: zone-end

2. Zum Ausführen des Containerimages in Docker können Sie eine Bash-Shell (Linux bzw. macOS) oder eine PowerShell-Eingabeaufforderung mit erhöhten Rechten verwenden. Nachfolgend finden Sie den dafür benötigten Befehl:

   ::: zone pivot="cs1-bash"
   ```bash
   sudo docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=<YourStrong!Passw0rd>" \
      -p 1433:1433 --name sql1 \
      -d mcr.microsoft.com/mssql/server:2017-latest
   ```
   ::: zone-end

   ::: zone pivot="cs1-powershell"
   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=<YourStrong!Passw0rd>" `
      -p 1433:1433 --name sql1 `
      -d mcr.microsoft.com/mssql/server:2017-latest
   ```
   ::: zone-end

   ::: zone pivot="cs1-cmd"
   ```cmd
   docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=<YourStrong!Passw0rd>" `
      -p 1433:1433 --name sql1 `
      -d mcr.microsoft.com/mssql/server:2017-latest
   ```
   ::: zone-end

   > [!NOTE]
   > Das Kennwort sollte der Standardrichtlinie für SQL Server-Kennwörter entsprechen. Ist dies nicht der Fall, kann der Container SQL Server nicht einrichten und funktioniert nicht mehr. Standardmäßig muss das Kennwort mindestens 8 Zeichen lang sein und Zeichen aus drei der folgenden vier Sätze enthalten: Großbuchstaben, Kleinbuchstaben, Ziffern und Symbole. Mit dem Befehl [docker logs](https://docs.docker.com/engine/reference/commandline/logs/) können Sie das Fehlerprotokoll untersuchen.

   > [!NOTE]
   > Standardmäßig wird dabei ein Container erstellt, der die Developer Edition von SQL Server 2017 enthält. Die Vorgehensweise zum Ausführen von Produktionseditionen in Containern weicht hiervon minimal ab. Weitere Informationen finden Sie unter [Run production container images (Ausführen von Containerimages für Produktionsumgebungen)](sql-server-linux-configure-docker.md#production).

   In der folgenden Tabelle finden Sie Beschreibungen der Parameter des vorangegangenen Beispiels für `docker run`:

   | Parameter | Beschreibung |
   |-----|-----|
   | **-e "ACCEPT_EULA = Y"** |  Legen Sie für die Variable **ACCEPT_EULA** einen beliebigen Wert fest, um Ihre Zustimmung zum [End-User Licensing Agreement (Benutzerlizenzvertrag)](https://go.microsoft.com/fwlink/?LinkId=746388) zu geben. Diese Einstellung ist für das SQL Server-Image zwingend erforderlich. |
   | **-e ' SA_PASSWORD =\<yourstrong! Passw0rd\>'** | Geben Sie ein starkes Kennwort ein, das aus mindestens acht Zeichen besteht und den [Kennwortanforderungen von SQL Server](../relational-databases/security/password-policy.md) entspricht. Diese Einstellung ist für das SQL Server-Image zwingend erforderlich. |
   | **-p 1433:1433** | Ordnen Sie einen TCP-Port in der Hostumgebung (erster Wert) einem TCP-Port im Container zu (zweiter Wert). In diesem Beispiel lauscht SQL Server an TCP 1433 im Container und ist für den Port 1433 auf dem Host verfügbar. |
   | **--name sql1** | Geben Sie dem Container selbst einen Namen, anstatt einen willkürlich generierten zu verwenden. Wenn Sie mehrere Container ausführen, können Sie nicht denselben Namen mehrfach verwenden. |
   | **mcr.microsoft.com/mssql/server:2017-latest** | Das Linux-Containerimage von SQL Server 2017 |

3. Verwenden Sie den Befehl `docker ps`, um Ihre Docker-Container anzeigen zu lassen.


   ::: zone pivot="cs1-bash"
   ```bash
   sudo docker ps -a
   ```
   ::: zone-end

   ::: zone pivot="cs1-powershell"
   ```PowerShell
   docker ps -a
   ```
   ::: zone-end

   ::: zone pivot="cs1-cmd"
   ```cmd
   docker ps -a
   ```
   ::: zone-end

   Die Ausgabe sollte dann ähnlich wie in diesem Screenshot sein:

   ![Ausgabe des Befehls „docker ps“](./media/sql-server-linux-setup-docker/docker-ps-command.png)

4. Wenn in der Spalte **STATUS** **Up** (Aktiv) eingetragen ist, wird SQL Server im Container ausgeführt und überwacht den Port, der in der Spalte **PORTS** angegeben ist. Wenn in der Spalte **STATUS** Ihres SQL Server-Containers **Exited** (Beendet) steht, lesen Sie bitte im [Abschnitt „Problembehebung“ im Konfigurationshandbuch](sql-server-linux-configure-docker.md#troubleshooting) nach.

Der Parameter `-h` (Hostname) ist ebenfalls nützlich, wird der Einfachheit halber jedoch in diesem Tutorial nicht verwendet. Mit ihm lässt sich der interne Name eines Containers in einen benutzerdefinierten Wert ändern. Dieser Name wird in der folgenden Transact-SQL-Abfrage zurückgegeben:

```sql
SELECT @@SERVERNAME,
    SERVERPROPERTY('ComputerNamePhysicalNetBIOS'),
    SERVERPROPERTY('MachineName'),
    SERVERPROPERTY('ServerName')
```

Wenn Sie für `-h` und `--name` denselben Wert festlegen, kann der Zielcontainer ganz einfach ermittelt werden.

::: moniker-end
<!--End of 2017 "Pull and run" section-->

<!--This is the 2019 version of the "Pull and run" section-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="pullandrun2019"></a>Abrufen und Ausführen des Container Images

Bevor Sie die folgenden Schritte ausführen, stellen Sie sicher, dass Sie am Anfang dieses Artikels Ihre bevorzugte Shell (bash, PowerShell oder cmd) ausgewählt haben.

1. Ziehen Sie das SQL Server 2019-Vorschau-Linux-Container Image von Docker Hub.

   ::: zone pivot="cs1-bash"
   ```bash
   sudo docker pull mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
   ```
   ::: zone-end

   ::: zone pivot="cs1-powershell"
   ```PowerShell
   docker pull mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
   ```
   ::: zone-end

   ::: zone pivot="cs1-cmd"
   ```cmd
   docker pull mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
   ```
   ::: zone-end

   > [!TIP]
   > In dieser Schnellstartanleitung wird das docker-Image SQL Server 2019 Preview verwendet. Wenn Sie das SQL Server 2017-Abbild ausführen möchten, finden Sie weitere Informationen in der [SQL Server 2017-Version dieses Artikels](quickstart-install-connect-docker.md?view=sql-server-linux-2017#pullandrun2017).

   Mit dem vorherigen Befehl wird das SQL Server 2019-Vorschau Container Image basierend auf Ubuntu abgerufen. Informationen dazu, wie Sie Container Images verwenden, die auf RedHat basieren, finden Sie unter [Ausführen von RHEL-basierten Container Images](sql-server-linux-configure-docker.md#rhel). Informationen zu allen verfügbaren Images finden Sie auf der [Docker-Hubseite zu „mssql-server-linux“](https://hub.docker.com/_/microsoft-mssql-server).

   ::: zone pivot="cs1-bash"
   Für die bash-Befehle in diesem Artikel `sudo` wird verwendet. Unter MacOS ist `sudo` möglicherweise nicht erforderlich. Wenn Sie unter Linux nicht zum Ausführen von Docker `sudo` verwenden möchten, können Sie eine **docker** -Gruppe konfigurieren und dieser Gruppe Benutzer hinzufügen. Weitere Informationen finden Sie unter [Schritte nach der Installation für Linux](https://docs.docker.com/install/linux/linux-postinstall/).
   ::: zone-end

2. Zum Ausführen des Containerimages in Docker können Sie eine Bash-Shell (Linux bzw. macOS) oder eine PowerShell-Eingabeaufforderung mit erhöhten Rechten verwenden. Nachfolgend finden Sie den dafür benötigten Befehl:

   ::: zone pivot="cs1-bash"
   ```bash
   sudo docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=<YourStrong!Passw0rd>" \
      -p 1433:1433 --name sql1 \
      -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
   ```
   ::: zone-end

   ::: zone pivot="cs1-powershell"
   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=<YourStrong!Passw0rd>" `
      -p 1433:1433 --name sql1 `
      -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
   ```
   ::: zone-end

   ::: zone pivot="cs1-cmd"
   ```cmd
   docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=<YourStrong!Passw0rd>" `
      -p 1433:1433 --name sql1 `
      -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
   ```
   ::: zone-end

   > [!NOTE]
   > Das Kennwort sollte der Standardrichtlinie für SQL Server-Kennwörter entsprechen. Ist dies nicht der Fall, kann der Container SQL Server nicht einrichten und funktioniert nicht mehr. Standardmäßig muss das Kennwort mindestens 8 Zeichen lang sein und Zeichen aus drei der folgenden vier Sätze enthalten: Großbuchstaben, Kleinbuchstaben, Ziffern und Symbole. Mit dem Befehl [docker logs](https://docs.docker.com/engine/reference/commandline/logs/) können Sie das Fehlerprotokoll untersuchen.

   > [!NOTE]
   > Standardmäßig wird dadurch ein Container mit der Developer Edition von SQL Server 2019 Preview erstellt.

   In der folgenden Tabelle finden Sie Beschreibungen der Parameter des vorangegangenen Beispiels für `docker run`:

   | Parameter | Beschreibung |
   |-----|-----|
   | **-e "ACCEPT_EULA = Y"** |  Legen Sie für die Variable **ACCEPT_EULA** einen beliebigen Wert fest, um Ihre Zustimmung zum [End-User Licensing Agreement (Benutzerlizenzvertrag)](https://go.microsoft.com/fwlink/?LinkId=746388) zu geben. Diese Einstellung ist für das SQL Server-Image zwingend erforderlich. |
   | **-e ' SA_PASSWORD =\<yourstrong! Passw0rd\>'** | Geben Sie ein starkes Kennwort ein, das aus mindestens acht Zeichen besteht und den [Kennwortanforderungen von SQL Server](../relational-databases/security/password-policy.md) entspricht. Diese Einstellung ist für das SQL Server-Image zwingend erforderlich. |
   | **-p 1433:1433** | Ordnen Sie einen TCP-Port in der Hostumgebung (erster Wert) einem TCP-Port im Container zu (zweiter Wert). In diesem Beispiel lauscht SQL Server an TCP 1433 im Container und ist für den Port 1433 auf dem Host verfügbar. |
   | **--name sql1** | Geben Sie dem Container selbst einen Namen, anstatt einen willkürlich generierten zu verwenden. Wenn Sie mehrere Container ausführen, können Sie nicht denselben Namen mehrfach verwenden. |
   | **mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu** | Das SQL Server 2019 CTP 3.1 Linux-Container Image. |

3. Verwenden Sie den Befehl `docker ps`, um Ihre Docker-Container anzeigen zu lassen.

   ::: zone pivot="cs1-bash"
   ```bash
   sudo docker ps -a
   ```
   ::: zone-end

   ::: zone pivot="cs1-powershell"
   ```PowerShell
   docker ps -a
   ```
   ::: zone-end

   ::: zone pivot="cs1-cmd"
   ```cmd
   docker ps -a
   ```
   ::: zone-end

   Die Ausgabe sollte dann ähnlich wie in diesem Screenshot sein:

   ![Ausgabe des Befehls „docker ps“](./media/sql-server-linux-setup-docker/docker-ps-command.png)

4. Wenn in der Spalte **STATUS** **Up** (Aktiv) eingetragen ist, wird SQL Server im Container ausgeführt und überwacht den Port, der in der Spalte **PORTS** angegeben ist. Wenn in der Spalte **STATUS** Ihres SQL Server-Containers **Exited** (Beendet) steht, lesen Sie bitte im [Abschnitt „Problembehebung“ im Konfigurationshandbuch](sql-server-linux-configure-docker.md#troubleshooting) nach.

Der Parameter `-h` (Hostname) ist ebenfalls nützlich, wird der Einfachheit halber jedoch in diesem Tutorial nicht verwendet. Mit ihm lässt sich der interne Name eines Containers in einen benutzerdefinierten Wert ändern. Dieser Name wird in der folgenden Transact-SQL-Abfrage zurückgegeben:

```sql
SELECT @@SERVERNAME,
    SERVERPROPERTY('ComputerNamePhysicalNetBIOS'),
    SERVERPROPERTY('MachineName'),
    SERVERPROPERTY('ServerName')
```

Wenn Sie für `-h` und `--name` denselben Wert festlegen, kann der Zielcontainer ganz einfach ermittelt werden.

::: moniker-end
<!--End of 2019 "Pull and run" section-->

## <a id="sapassword"></a>Ändern des SA-Kennworts

<!-- This section was pasted in from includes/sql-server-linux-change-docker-password.md, to better support zone pivots. 2019/02/11 -->

Das **SA**-Konto ist ein Systemadministrator auf der SQL Server-Instanz, der beim Setup erstellt wird. Nach dem Erstellen Ihres SQL Server-Containers wird die von Ihnen festgelegte `MSSQL_SA_PASSWORD` Umgebungsvariable sichtbar, wenn Sie sie in dem Container ausführen`echo $MSSQL_SA_PASSWORD`. Ändern Sie aus Sicherheitsgründen ihr SA-Kennwort.

1. Wählen Sie ein sicheres Kennwort für den SA-Benutzer aus.

1. Verwenden Sie `docker exec` in Transact-SQL **sqlcmd** zum Ausführen und Ändern des Kennworts. Ersetzen Sie im folgenden Beispiel das alte Kennwort `<YourStrong!Passw0rd>`, und das neue `<YourNewStrong!Passw0rd>`Kennwort mit ihren eigenen Kenn Wort Werten.

   ::: zone pivot="cs1-bash"
   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P "<YourStrong!Passw0rd>" \
      -Q 'ALTER LOGIN SA WITH PASSWORD="<YourNewStrong!Passw0rd>"'
   ```
   ::: zone-end

   ::: zone pivot="cs1-powershell"
   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourStrong!Passw0rd>" `
      -Q "ALTER LOGIN SA WITH PASSWORD='<YourNewStrong!Passw0rd>'"
   ```
   ::: zone-end

   ::: zone pivot="cs1-cmd"
   ```cmd
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourStrong!Passw0rd>" `
      -Q "ALTER LOGIN SA WITH PASSWORD='<YourNewStrong!Passw0rd>'"
   ```
   ::: zone-end

## <a name="connect-to-sql-server"></a>Verbindung mit SQL Server herstellen

In den folgenden Schritten wird im Container das SQL Server-Befehlszeilentool **sqlcmd** genutzt, um eine Verbindung mit SQL Server herzustellen.

1. Verwenden Sie den Befehl `docker exec -it`, um in Ihrem laufenden Container eine interaktive Bash-Shell zu starten. Im folgenden Beispiel steht `sql1` für den Namen, den Sie bei der Erstellung des Containers mit dem Parameter `--name` angegeben haben.

   ::: zone pivot="cs1-bash"
   ```bash
   sudo docker exec -it sql1 "bash"
   ```
   ::: zone-end

   ::: zone pivot="cs1-powershell"
   ```PowerShell
   docker exec -it sql1 "bash"
   ```
   ::: zone-end

   ::: zone pivot="cs1-cmd"
   ```cmd
   docker exec -it sql1 "bash"
   ```
   ::: zone-end

2. Stellen Sie eine lokale Verbindung mit „sqlcmd“ her. „Sqlcmd“ verwendet nicht automatisch den richtigen Pfad. Sie müssen daher selbst den vollständigen Pfand angeben.

   ```bash
   /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P "<YourNewStrong!Passw0rd>"
   ```

   > [!TIP]
   > Sie können das Kennwort in der Befehlszeile auslassen, damit Sie aufgefordert werden, es einzugeben.

3. Wenn dies erfolgreich war, sollten zu einer **sqlcmd** Eingabeaufforderung: `1>` gelangen.

## <a name="create-and-query-data"></a>Erstellen und Abfragen von Daten

Die folgenden Abschnitte führen Sie durch die Verwendung von **sqlcmd** und Transact-SQL, um eine neue Datenbank zu erstellen, Daten hinzuzufügen und eine einfache Abfrage auszuführen.

### <a name="create-a-new-database"></a>Erstellen einer neuen Datenbank

Mit den folgenden Schritten wird eine neue Datenbank mit dem Namen `TestDB` erstellt.

1. Fügen Sie aus der **sqlcmd**-Eingabeaufforderung den folgenden Transact-SQL-Befehl zur Erstellung einer Testdatenbank ein:

   ```sql
   CREATE DATABASE TestDB
   ```

2. Schreiben Sie in der nächsten Zeile eine Abfrage, um den Namen all Ihrer Datenbanken auf Ihrem Server zurückzugeben:

   ```sql
   SELECT Name from sys.Databases
   ```

3. Die vorherigen beiden Befehle wurden nicht sofort ausgeführt. Sie müssen `GO` in einer neuen Zeile eingeben, um die zuvor eingegebenen Befehle auszuführen:

   ```sql
   GO
   ```

### <a name="insert-data"></a>Einfügen von Daten

Erstellen Sie als Nächstes eine neue Tabelle, `Inventory`, und fügen Sie zwei neue Zeilen ein.

1. Wechseln Sie den Kontext aus der **sqlcmd**-Eingabeaufforderung zur neuen `TestDB`-Datenbank:

   ```sql
   USE TestDB
   ```

2. Erstellen Sie eine neue Tabelle mit dem Namen `Inventory`:

   ```sql
   CREATE TABLE Inventory (id INT, name NVARCHAR(50), quantity INT)
   ```

3. Fügen Sie Daten in die neue Tabelle ein:

   ```sql
   INSERT INTO Inventory VALUES (1, 'banana', 150); INSERT INTO Inventory VALUES (2, 'orange', 154);
   ```

4. Geben Sie `GO` ein, um die zuvor eingegebenen Befehle auszuführen:

   ```sql
   GO
   ```

### <a name="select-data"></a>Auswählen von Daten

Führen Sie nun eine Abfrage zum Zurückgeben von Daten aus der `Inventory`-Tabelle aus.

1. Geben Sie aus der **sqlcmd**-Eingabeaufforderung eine Abfrage ein, die Reihen aus der `Inventory`-Tabelle zurückgibt, bei denen die Menge größer als 152 ist:

   ```sql
   SELECT * FROM Inventory WHERE quantity > 152;
   ```

2. Führen Sie den Befehl aus:

   ```sql
   GO
   ```

### <a name="exit-the-sqlcmd-command-prompt"></a>Beenden der sqlcmd-Eingabeaufforderung

1. Zum Beenden der **sqlcmd**-Sitzung, geben Sie `QUIT` ein:

   ```sql
   QUIT
   ```

2. Geben Sie `exit` ein, um die interaktive Befehlszeile in Ihrem Container zu beenden. Der Container wird auch nach dem Beenden der interaktiven Bash-Shell weiter ausgeführt.

## <a id="connectexternal"></a> Herstellen einer Verbindung von außerhalb des Containers

Sie können auch über jedes externe Linux-, Windows- oder macOS-Tool, das SQL-Verbindungen unterstützt, eine Verbindung mit der SQL Server-Instanz auf Ihrem Docker-Computer herstellen.

Mithilfe der folgenden Schritte stellen Sie über **sqlcmd** von außerhalb Ihres Containers eine Verbindung mit SQL Server im Container her. Voraussetzung ist, dass Sie außerhalb Ihres Containers bereits SQL Server-Befehlszeilentools installiert haben. Die gleichen Prinzipien gelten für die Verwendung anderer Tools, aber der Verbindungsvorgang ist für jedes Tool eindeutig.

1. Ermitteln Sie die IP-Adresse des Computers, der Ihren Container hostet. Verwenden Sie dazu unter Linux **Ifconfig** oder **ip addr**. Verwenden Sie unter Windows **ipconfig**.

1. Installieren Sie in diesem Beispiel das **sqlcmd** -Tool auf dem Client Computer. Weitere Informationen finden Sie unter [Installieren von sqlcmd unter Windows](../tools/sqlcmd-utility.md) oder [Installieren von sqlcmd unter Linux](sql-server-linux-setup-tools.md).

1. Führen Sie „sqlcmd“ aus. Geben Sie dabei die IP-Adresse und den Port an, der dem Port 1433 Ihres Containers zugeordnet ist. In diesem Beispiel entspricht dies dem Port 1433 auf dem Host Computer. Wenn Sie einen anderen zugeordneten Port auf dem Host Computer angegeben haben, verwenden Sie ihn hier.

   ::: zone pivot="cs1-bash"
   ```bash
   sqlcmd -S <ip_address>,1433 -U SA -P "<YourNewStrong!Passw0rd>"
   ```
   ::: zone-end

   ::: zone pivot="cs1-powershell"
   ```PowerShell
   sqlcmd -S <ip_address>,1433 -U SA -P "<YourNewStrong!Passw0rd>"
   ```
   ::: zone-end

   ::: zone pivot="cs1-cmd"
   ```cmd
   sqlcmd -S <ip_address>,1433 -U SA -P "<YourNewStrong!Passw0rd>"
   ```
   ::: zone-end

1. Führen Sie Transact-SQL-Befehle aus. Wenn Sie fertig sind, geben Sie `QUIT` ein.

Für eine Verbindung mit SQL Server werden häufig auch folgende Tools verwendet:

- [Visual Studio Code](sql-server-linux-develop-use-vscode.md)
- [SQL Server Management Studio (SSMS) unter Windows](sql-server-linux-manage-ssms.md)
- [Azure Data Studio](../azure-data-studio/what-is.md)
- [mssql-cli (Vorschauversion)](https://github.com/dbcli/mssql-cli/blob/master/doc/usage_guide.md)
- [PowerShell-Kern](sql-server-linux-manage-powershell-core.md)

## <a name="remove-your-container"></a>Entfernen Ihres Containers

Wenn Sie den in diesem Tutorial verwendeten SQL Server-Container entfernen möchten, führen Sie die folgenden Befehle aus:

::: zone pivot="cs1-bash"
```bash
sudo docker stop sql1
sudo docker rm sql1
```
::: zone-end

::: zone pivot="cs1-powershell"
```PowerShell
docker stop sql1
docker rm sql1
```
::: zone-end

::: zone pivot="cs1-cmd"
```cmd
docker stop sql1
docker rm sql1
```
::: zone-end

> [!WARNING]
> Wenn Sie einen Container beenden oder entfernen, werden die SQL Server-Daten dauerhaft aus diesem Container gelöscht. Wenn Sie Ihre Daten weiterhin benötigen, [erstellen Sie eine Sicherungskopie des Containers](tutorial-restore-backup-in-sql-server-container.md), oder nutzen Sie für die Containerdaten eine [Methode zur Datenpersistenz](sql-server-linux-configure-docker.md#persist).

## <a name="docker-demo"></a>Docker-Demo

Nachdem Sie nun das SQL Server-Containerimage für Docker getestet haben, sollten Sie auch wissen, welche Vorteile Ihnen Docker beim Entwickeln und Testen bringt. Im folgenden Video sehen Sie, wie sich Docker in einem Continuous Integration-Szenario bzw. einem Continuous Deployment-Szenario verwenden lässt.

> [!VIDEO https://channel9.msdn.com/Events/Connect/2017/T152/player]

## <a name="next-steps"></a>Nächste Schritte

Ein Tutorial zum Wiederherstellen von Sicherungskopien von Datenbanken in einem Container finden Sie unter [Restore a SQL Server database in a Linux Docker container (Wiederherstellen einer SQL Server-Datenbank in einem Docker-Container unter Linux)](tutorial-restore-backup-in-sql-server-container.md). Weitere Szenarios, z. b. das Ausführen mehrerer Container, die Daten Persistenz und die Problembehandlung, finden Sie unter [Konfigurieren von SQL Server Container Images in docker](sql-server-linux-configure-docker.md).

Ressourcen, Feedback und Informationen über bekannte Probleme finden Sie im [GitHub-Repository „mssql-docker“](https://github.com/Microsoft/mssql-docker).
