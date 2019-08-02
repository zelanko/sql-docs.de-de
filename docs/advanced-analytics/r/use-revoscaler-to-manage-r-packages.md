---
title: Verwenden von revoscaler-Funktionen zum Suchen oder Installieren von R-Paketen
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 8db20295c2e21b6499d4d935f9c99161983b588f
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715581"
---
# <a name="how-to-use-revoscaler-functions-to-find-or-install-r-packages-on-sql-server"></a>Verwenden von revoscaler-Funktionen zum Suchen oder Installieren von R-Paketen auf SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Revoscaler 9.0.1 und höher umfasst Funktionen für die R-Paketverwaltung a SQL Server computekontext. Diese Funktionen können von Remote-, nicht--Administratoren verwendet werden, um Pakete auf SQL Server ohne direkten Zugriff auf den-Server zu installieren.

SQL Server Machine Learning Services enthält bereits eine neuere Version von revoscaler. SQL Server 2016 R Services-Kunden müssen ein [Komponenten Upgrade](../install/upgrade-r-and-python.md) ausführen, um die revoscaler-Paketverwaltungsfunktionen zu erhalten. Anweisungen zum Abrufen der Paketversion und des Inhalts finden Sie unter Abrufen von [Paketinformationen](../package-management/installed-package-information.md).

## <a name="revoscaler-functions-for-package-management"></a>Revoscaler-Funktionen für die Paketverwaltung

In der folgenden Tabelle werden die für die Installation und Verwaltung von R-Paketen verwendeten Funktionen beschrieben.

| Funktion | Beschreibung |
|----------|-------------|
| [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) | Bestimmen Sie den Pfad der instanzbibliothek auf der Remote SQL Server. |
| [rxFindPackage](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxfindpackage) | Ruft den Pfad für ein oder mehrere Pakete auf dem Remote SQL Server ab. |
| [rxinstallpackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) | Diese Funktion kann von einem Remote-R-Client aufgerufen werden, um Pakete in einem SQL Server computekontext entweder aus einem angegebenen Repository oder durchlesen lokal gespeicherter gezippte Pakete zu installieren. Diese Funktion prüft auf Abhängigkeiten und stellt sicher, dass alle zugehörigen Pakete auf SQL Server installiert werden können, genau wie die R-Paketinstallation im lokalen computekontext. Um diese Option verwenden zu können, müssen Sie die Paketverwaltung auf dem Server und in der Datenbank aktiviert haben. Sowohl Client-als auch Serverumgebungen müssen die gleiche Version von revoscaler aufweisen. |
| [rxInstalledPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstalledpackages) | Ruft eine Liste der im angegebenen computekontext installierten Pakete ab. |
| [rxSyncPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsyncpackages) | Kopieren Sie Informationen zu einer paketbibliothek zwischen dem Dateisystem und der Datenbank für den angegebenen computekontext. |
| [rxRemovePackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxremovepackages) | Entfernt Pakete aus einem angegebenen computekontext. Außerdem werden Abhängigkeiten berechnet, und es wird sichergestellt, dass Pakete, die nicht mehr von anderen Paketen auf SQL Server verwendet werden, entfernt werden, um Ressourcen freizugeben. |

## <a name="prerequisites"></a>Vorraussetzungen

+ [Aktivieren der Remote-R-Paketverwaltung auf SQL Server](r-package-how-to-enable-or-disable.md)

+ Revoscaler-Versionen müssen in Client-und Serverumgebungen identisch sein. Weitere Informationen finden Sie unter [Get Package Information](../package-management/installed-package-information.md).

+ Berechtigung zum Herstellen einer Verbindung mit dem Server und einer Datenbank sowie zum Ausführen von R-Befehlen. Sie müssen Mitglied einer Daten Bank Rolle sein, die es Ihnen ermöglicht, Pakete auf der angegebenen Instanz und Datenbank zu installieren.

+ Pakete im frei **gegebenen Bereich** können von Benutzern installiert werden, die `rpkgs-shared` zur Rolle in einer angegebenen Datenbank gehören. Alle Benutzer mit dieser Rolle können freigegebene Pakete deinstallieren.

+ Pakete im **privaten Bereich** können von jedem Benutzer installiert werden, der `rpkgs-private` zur Rolle in einer Datenbank gehört. Benutzer können jedoch nur Ihre eigenen Pakete sehen und deinstallieren.

+ Datenbankbesitzer können mit freigegebenen oder privaten Paketen arbeiten.

## <a name="client-connections"></a>Client Verbindungen

Eine Client Arbeitsstation kann [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/install-on-windows) oder eine [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) (Datenanalysten verwenden häufig die kostenlose Developer Edition) im selben Netzwerk verwenden.

Beim Aufrufen von Paketverwaltungsfunktionen von einem Remote-R-Client aus müssen Sie zuerst mit der [rxinsqlserver](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) -Funktion ein computecontext-Objekt erstellen. Übergeben Sie anschließend für jede von Ihnen verwendete Paket Verwaltungsfunktion den computekontext als Argument.

Die Benutzeridentität wird in der Regel beim Festlegen des computekontexts angegeben. Wenn Sie beim Erstellen des computekontexts keinen Benutzernamen und kein Kennwort angeben, wird die Identität des Benutzers verwendet, der den R-Code ausgeführt hat.

1. Definieren Sie in einer R-Befehlszeile eine Verbindungs Zeichenfolge für die-Instanz und die-Datenbank.
2. Verwenden Sie den [rxinsqlserver](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) -Konstruktor, um mithilfe der Verbindungs Zeichenfolge einen SQL Server computekontext zu definieren.

    ```R
    sqlcc <- RxInSqlServer(connectionString = myConnString, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    ```
3. Erstellen Sie eine Liste der Pakete, die Sie installieren möchten, und speichern Sie die Liste in einer Zeichen folgen Variablen.

    ```R
    packageList <- c("e1071", "mice")
    ```

4. Ruft [rxinstallpackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) auf und übergibt den computekontext und die Zeichen folgen Variable, die die Paketnamen enthält.

    ```R
    rxInstallPackages(pkgs = packageList, verbose = TRUE, computeContext = sqlcc)
    ```

    Wenn abhängige Pakete erforderlich sind, werden Sie auch installiert, vorausgesetzt, dass eine Internetverbindung auf dem Client verfügbar ist.
    
    Pakete werden mit den Anmelde Informationen des Benutzers installiert, der die Verbindung hergestellt hat, im Standardbereich für diesen Benutzer.

## <a name="call-package-management-functions-in-stored-procedures"></a>Abrufen von Paketverwaltungsfunktionen in gespeicherten Prozeduren

Sie führen die Paketverwaltungsfunktionen in `sp_execute_external_script`aus. In diesem Fall wird die Funktion mithilfe des Sicherheits Kontexts des Aufrufers der gespeicherten Prozedur ausgeführt.

## <a name="examples"></a>Beispiele

Dieser Abschnitt enthält Beispiele für die Verwendung dieser Funktionen von einem Remote Client beim Herstellen einer Verbindung mit einer SQL Server-Instanz oder-Datenbank als computekontext.

Für alle Beispiele müssen Sie entweder eine Verbindungs Zeichenfolge oder einen computekontext angeben, für den eine Verbindungs Zeichenfolge erforderlich ist. Dieses Beispiel bietet eine Möglichkeit, einen computekontext für SQL Server zu erstellen:

```R
instance_name <- "computer-name/instance-name";
database_name <- "TestDB";
sqlWait= TRUE;
sqlConsoleOutput <- TRUE;
connString <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
sqlcc <- RxInSqlServer(connectionString = connString, wait = sqlWait, consoleOutput = sqlConsoleOutput, numTasks = 4);
```

Abhängig davon, wo sich der Server befindet, und dem Sicherheitsmodell müssen Sie möglicherweise eine Domänen-und Subnetzspezifikation in der Verbindungs Zeichenfolge angeben oder einen SQL-Anmelde Namen verwenden. Zum Beispiel:

```R
connStr <- "Driver=SQL Server;Server=myserver.financeweb.contoso.com;Database=Finance;Uid=RUser1;Pwd=RUserPassword"
```

### <a name="get-package-path-on-a-remote-sql-server-compute-context"></a>Get Package path on a Remote SQL Server Compute Context

In diesem Beispiel wird der Pfad für das **revoscaler** -Paket im computekontext `sqlcc`abgerufen.

```R
sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlcc)
print(sqlPackagePaths)
```

**Ergebnisse**

"C:/Program Files/Microsoft SQL Server/MSSQL14. MSSQLSERVER/R_SERVICES/Library/revoscaler "

> [!TIP]
> Wenn Sie die Option zum Anzeigen der Ausgabe der SQL-Konsole aktiviert haben, erhalten Sie möglicherweise Statusmeldungen von der Funktion `print` , die der Anweisung vorangestellt ist. Nachdem Sie den Code getestet haben, legen Sie `consoleOutput` im computecontext-Konstruktor auf false fest, um Nachrichten zu entfernen.

### <a name="get-locations-for-multiple-packages"></a>Abrufen von Speicherorten für mehrere Pakete

Im folgenden Beispiel werden die Pfade für die **revoscaler** -und die- **Gitter** Pakete im computekontext `sqlcc`abgerufen. Um Informationen über mehrere Pakete zu erhalten, übergeben Sie einen Zeichen folgen Vektor, der die Paketnamen enthält.

```R
packagePaths <- rxFindPackage(package = c("RevoScaleR", "lattice"), computeContext = sqlcc)
print(packagePaths)
```

### <a name="get-package-versions-on-a-remote-compute-context"></a>Paketversionen in einem remotecomputekontext erhalten

Führen Sie diesen Befehl in einer R-Konsole aus, um die Buildnummer und Versionsnummern für Pakete zu erhalten, die auf dem computekontext *SQLServer*installiert sind.

```R
sqlPackages <- rxInstalledPackages(fields = c("Package", "Version", "Built"), computeContext = sqlServer)
```

**Ergebnisse**

```text
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library/RevoScaleR"

[2] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library/lattice"
```

### <a name="install-a-package-on-sql-server"></a>Installieren eines Pakets in SQL Server

In diesem Beispiel werden das **Vorhersage** Paket und seine Abhängigkeiten im computekontext installiert.

  ```R
  pkgs <- c("forecast")
  rxInstallPackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlcc)
  ```

### <a name="remove-a-package-from-sql-server"></a>Entfernen eines Pakets aus SQL Server

In diesem Beispiel werden das **Vorhersage** Paket und seine Abhängigkeiten aus dem computekontext entfernt.

  ```R
  pkgs <- c("forecast")
  rxRemovePackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlcc)
  ```

### <a name="synchronize-packages-between-database-and-file-system"></a>Synchronisieren von Paketen zwischen Datenbank und Dateisystem

Im folgenden Beispiel wird die Datenbank **TestDB**überprüft und ermittelt, ob alle Pakete im Dateisystem installiert sind. Wenn einige Pakete fehlen, werden Sie im Dateisystem installiert.

```R
# Instantiate the compute context
connectionString <- "Driver=SQL Server;Server=myServer;Database=TestDB;Trusted_Connection=True;"
computeContext <- RxInSqlServer(connectionString = connectionString )

# Synchronize the packages in the file system for all scopes and users
rxSyncPackages(computeContext=computeContext, verbose=TRUE)
```

Die Paket Synchronisierung funktioniert pro Datenbank und pro Benutzer. Weitere Informationen finden Sie unter [R-Paket Synchronisierung für SQL Server](../r/package-install-uninstall-and-sync.md).

### <a name="use-a-stored-procedure-to-list-packages-in-sql-server"></a>Verwenden einer gespeicherten Prozedur zum Auflisten von Paketen in SQL Server

Führen Sie diesen Befehl in Management Studio oder einem anderen Tool aus, das T-SQL unterstützt, um eine Liste der installierten Pakete auf der `rxInstalledPackages` aktuellen Instanz zu erhalten, indem Sie in einer gespeicherten Prozedur verwenden.

```sql
EXEC sp_execute_external_script 
  @language=N'R', 
  @script=N'
    myPackages <- rxInstalledPackages();
    OutputDataSet <- as.data.frame(myPackages);
    '
```

Die `rxSqlLibPaths` -Funktion kann verwendet werden, um die von SQL Server Machine Learning Services verwendete aktive Bibliothek zu bestimmen. Dieses Skript kann nur den Bibliotheks Pfad für den aktuellen Server zurückgeben. 

```sql
declare @instance_name nvarchar(100) = @@SERVERNAME, @database_name nvarchar(128) = db_name();
exec sp_execute_external_script 
  @language = N'R',
  @script = N'
    connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
    .libPaths(rxSqlLibPaths(connStr));
    print(.libPaths());
  ', 
  @input_data_1 = N'', 
  @params = N'@instance_name nvarchar(100), @database_name nvarchar(128)',
  @instance_name = @instance_name, 
  @database_name = @database_name;
```

## <a name="see-also"></a>Siehe auch

+ [Remoteverwaltung für R-Pakete aktivieren](r-package-how-to-enable-or-disable.md)
+ [Synchronisieren von R-Paketen](package-install-uninstall-and-sync.md)
+ [Tipps zum Installieren von R-Paketen](packages-installed-in-user-libraries.md)
+ [Standardpakete](../package-management/default-packages.md)