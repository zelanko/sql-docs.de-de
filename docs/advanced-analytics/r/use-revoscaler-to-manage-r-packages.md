---
title: 'Gewusst wie: Verwenden der RevoScaleR-Funktionen zum Suchen oder installieren R-Pakete: SQL Server Machine Learning Services'
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 64f930a72dbb7f8c6aff8338f22dd3e9b7cc7bbe
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53645359"
---
# <a name="how-to-use-revoscaler-functions-to-find-or-install-r-packages-on-sql-server"></a>Gewusst wie: Verwenden von RevoScaleR-Funktionen zum Suchen oder installieren R-Pakete auf SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

RevoScaleR 9.0.1 und höher schließt Funktionen für R-paketverwaltung für einen SQL Server-computekontext. Diese Funktionen können von remote nicht-Administratoren verwendet werden, um Pakete auf SQL Server ohne direkten Zugriff auf den Server zu installieren.

SQL Server 2017-Machine Learning Services enthält bereits eine neuere Version von RevoScaleR. SQL Server 2016 R Services-Kunden müssen eine [Upgrade von Integrationskomponenten](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md) um RevoScaleR-Paket-Management-Funktionen zu erhalten. Anweisungen zum Abrufen von Version und Inhalt Verpacken, finden Sie unter [Abrufen von Paketinformationen](determine-which-packages-are-installed-on-sql-server.md).

## <a name="revoscaler-functions-for-package-management"></a>RevoScaleR-Funktionen für die paketverwaltung

Die folgende Tabelle beschreibt die Funktionen zur Installation von R-Paket und die Verwaltung verwendet.

| Funktion | Description |
|----------|-------------|
| [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) | Ermitteln des Pfads der Instanz-Bibliothek auf dem Remotecomputer mit SQL Server. |
| [rxFindPackage](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxfindpackage) | Ruft den Pfad für eine oder mehrere Pakete auf dem SQL-Remoteserver. |
| [rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) | Mit dieser Funktion wird von einem Remoteclient-R zum Installieren von Paketen in einem SQL Server-rechenkontext, entweder aus einem angegebenen Repository oder durch Lesen von lokal gespeicherten ZIP-Archivpaketen. Diese Funktion überprüft, ob Abhängigkeiten und stellt sicher, dass alle zugehörigen Pakete in SQL Server – genau wie durch die Installation von R-Paket im lokalen computekontext installiert werden können. Um diese Option verwenden zu können, müssen Sie die Verwaltung von Paketen auf dem Server und die Datenbank aktiviert haben. Client und Server-Umgebungen müssen die gleiche Version von RevoScaleR. |
| [rxInstalledPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstalledpackages) | Ruft eine Liste der im angegebenen rechenkontext installierten Pakete. |
| [rxSyncPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsyncpackages) | Kopieren Sie die Informationen über eine paketbibliothek zwischen dem Dateisystem und die Datenbank, für den angegebenen rechenkontext. |
| [rxRemovePackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxremovepackages) | Entfernt Pakete aus einem angegebenen rechenkontext. Außerdem Abhängigkeiten berechnet und stellt sicher, dass Pakete, die von anderen Paketen in SQL Server nicht mehr verwendet werden entfernt werden, um Ressourcen freizugeben. |

## <a name="prerequisites"></a>Erforderliche Komponenten

+ [Aktivieren von remote R-paketverwaltung für SQL Server](r-package-how-to-enable-or-disable.md)

+ RevoScaleR-Versionen müssen auf Client und Server-Umgebungen identisch sein. Weitere Informationen finden Sie unter [Abrufen von Paketinformationen](determine-which-packages-are-installed-on-sql-server.md).

+ Berechtigung zur Verbindung mit dem Server und einer Datenbank, und klicken Sie zum Ausführen von R-Befehlen. Sie müssen ein Mitglied einer Datenbankrolle sein, die Sie zum Installieren der Pakete für die angegebene Instanz und die Datenbank ermöglicht.

+ Pakete in **freigegebener Bereich** installiert werden, indem Benutzern der `rpkgs-shared` Rolle in einer angegebenen Datenbank. Alle Benutzer in dieser Rolle können freigegebene Pakete deinstallieren.

+ Pakete in **privater Bereich** kann installiert werden, von einem Benutzer gehören zu den `rpkgs-private` Rolle in einer Datenbank. Benutzer können jedoch sehen und nur ihre eigenen Pakete deinstallieren.

+ Datenbankbesitzer können freigegeben oder privat Pakete angewendet werden.

## <a name="client-connections"></a>Clientverbindungen

Eine Clientarbeitsstation möglich [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/install-on-windows) oder [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) (Datenanalysten verwenden häufig die kostenlose Developer Edition) im selben Netzwerk.

Beim Aufruf von Paketverwaltungsfunktionen aus einem R-Remoteclient, müssen zuerst erstellen Sie einen computekontext-Objekt, mit der [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) Funktion. Übergeben Sie den computekontext danach für jedes Paket-Management-Funktion, die Sie verwenden, als Argument.

Identität des Benutzers wird in der Regel angegeben, wenn Sie den computekontext festlegen. Wenn Sie nicht angeben einen Benutzernamen und Kennwort beim Erstellen des computekontexts, dient die Identität des Benutzers, den R-Code ausführt.

1. Definieren Sie eine Verbindungszeichenfolge aus einer R-Befehlszeile mit der Instanz und Datenbank.
2. Verwenden der [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) Konstruktor, um eine SQL Server-computekontext, mithilfe der Verbindungszeichenfolge zu definieren.

    ```R
    sqlcc <- RxInSqlServer(connectionString = myConnString, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    ```
3. Erstellen Sie eine Liste der Pakete, die Sie verwenden möchten, installieren, und speichern Sie die Liste in einer Zeichenfolgenvariablen.

    ```R
    packageList <- c("e1071", "mice")
    ```

4. Rufen Sie [RxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) und übergeben Sie den computekontext und die Zeichenfolgenvariable, die den Namen der Pakete enthält.

    ```R
    rxInstallPackages(pkgs = packageList, verbose = TRUE, computeContext = sqlcc)
    ```

    Wenn die abhängigen Pakete erforderlich sind, werden sie auch installiert, vorausgesetzt, dass eine Internetverbindung auf dem Client verfügbar ist.
    
    Pakete werden mit den Anmeldeinformationen des Benutzers an, die Verbindung in den Standardbereich für diesen Benutzer installiert.

## <a name="call-package-management-functions-in-stored-procedures"></a>Rufen Sie die Paket-Management-Funktionen in gespeicherten Prozeduren

Cam ausführen Paketverwaltungsfunktionen in `sp_execute_external_script`. Wenn Sie dies tun, wird die Funktion mithilfe des Sicherheitskontexts des Aufrufers gespeicherte Prozedur ausgeführt.

## <a name="examples"></a>Beispiele

Dieser Abschnitt enthält Beispiele dafür, wie Sie diese Funktionen von einem Remoteclient aus zu verwenden, bei der Verbindung mit einer SQL Server-Instanz oder die Datenbank als den computekontext.

Alle Beispiele müssen Sie angeben, entweder eine Verbindungszeichenfolge oder einen computekontext, der eine Verbindungszeichenfolge erforderlich ist. In diesem Beispiel bietet eine Möglichkeit, einen computekontext für SQL Server zu erstellen:

```R
instance_name <- "computer-name/instance-name";
database_name <- "TestDB";
sqlWait= TRUE;
sqlConsoleOutput <- TRUE;
connString <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
sqlcc <- RxInSqlServer(connectionString = connString, wait = sqlWait, consoleOutput = sqlConsoleOutput, numTasks = 4);
```

Je nachdem, wo sich der Server befindet, und das Sicherheitsmodell müssen Sie eine Domäne und das Subnetz-Spezifikation in der Verbindungszeichenfolge angeben, oder verwenden Sie eine SQL-Anmeldung. Zum Beispiel:

```R
connStr <- "Driver=SQL Server;Server=myserver.financeweb.contoso.com;Database=Finance;Uid=RUser1;Pwd=RUserPassword"
```

### <a name="get-package-path-on-a-remote-sql-server-compute-context"></a>Abrufen von Paketpfad auf einen Remoteserver SQL Server-computekontext

In diesem Beispiel ruft den Pfad für die **RevoScaleR** Paket auf den computekontext `sqlcc`.

```R
sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlcc)
print(sqlPackagePaths)
```

**Ergebnisse**

"C: / Program Programme/Microsoft SQL Server/MSSQL14. MSSQLSERVER/R_SERVICES/Library/RevoScaleR"

> [!TIP]
> Wenn Sie die Option aus, um die Ausgabe der SQL-Konsole finden Sie unter aktiviert haben, erhalten Sie möglicherweise statusmeldungen aus der Funktion, die vor der `print` Anweisung. Wenn Sie das Testen Ihres Codes abgeschlossen haben, legen Sie `consoleOutput` auf "false" in der Compute-Kontext-Konstruktor, um Meldungen zu deaktivieren.

### <a name="get-locations-for-multiple-packages"></a>Abrufen von Speicherorten für mehrere Pakete

Im folgenden Beispiel wird die Pfade für die **RevoScaleR** und **Lattice** -Pakete, auf den computekontext `sqlcc`. Übergeben Sie einen Zeichenfolgenvektor, die den Namen der Pakete enthält, rufen Sie Informationen über mehrere Pakete.

```R
packagePaths <- rxFindPackage(package = c("RevoScaleR", "lattice"), computeContext = sqlcc)
print(packagePaths)
```

### <a name="get-package-versions-on-a-remote-compute-context"></a>Abrufen von Paketversionen in einem remotecomputekontext

Führen Sie diesen Befehl aus einer R-Konsole, um die Build- und Versionsnummern auf im rechenkontext installierten Paketen erhalten *SqlServer*.

```R
sqlPackages <- rxInstalledPackages(fields = c("Package", "Version", "Built"), computeContext = sqlServer)
```

**Ergebnisse**

```text
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library/RevoScaleR"

[2] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library/lattice"
```

### <a name="install-a-package-on-sql-server"></a>Installieren eines Pakets in SQL Server

In diesem Beispiel installiert das **prognostizieren** Paket und seine Abhängigkeiten im rechenkontext.

  ```R
  pkgs <- c("forecast")
  rxInstallPackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlcc)
  ```

### <a name="remove-a-package-from-sql-server"></a>Entfernen eines Pakets aus SQL Server

In diesem Beispiel wird die **prognostizieren** Paket und seine Abhängigkeiten aus dem rechenkontext.

  ```R
  pkgs <- c("forecast")
  rxRemovePackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlcc)
  ```

### <a name="synchronize-packages-between-database-and-file-system"></a>Synchronisieren der Pakete zwischen Datenbank und Dateisystem

Das folgende Beispiel überprüft die Datenbank **TestDB**, und bestimmt, ob alle Pakete im Dateisystem installiert sind. Wenn einige Pakete fehlen, werden sie im Dateisystem installiert.

```R
# Instantiate the compute context
connectionString <- "Driver=SQL Server;Server=myServer;Database=TestDB;Trusted_Connection=True;"
computeContext <- RxInSqlServer(connectionString = connectionString )

# Synchronize the packages in the file system for all scopes and users
rxSyncPackages(computeContext=computeContext, verbose=TRUE)
```

Paket funktioniert auf eine pro Datenbank und pro Benutzer. Weitere Informationen finden Sie unter [für SQL Server R-paketsynchronisierung](../r/package-install-uninstall-and-sync.md).

### <a name="use-a-stored-procedure-to-list-packages-in-sql-server"></a>Verwenden Sie eine gespeicherte Prozedur zum Auflisten der Pakete in SQL Server

Führen Sie diesen Befehl in Management Studio oder ein anderes Tool, das T-SQL, um eine Liste der installierten Pakete auf der aktuellen Instanz ist, erhalten unterstützt mit `rxInstalledPackages` in einer gespeicherten Prozedur.

```sql
EXEC sp_execute_external_script 
  @language=N'R', 
  @script=N'
    myPackages <- rxInstalledPackages();
    OutputDataSet <- as.data.frame(myPackages);
    '
```

Die `rxSqlLibPaths` Funktion kann verwendet werden, um zu bestimmen, die active-Bibliothek, die von SQL Server-Machine Learning-Dienste verwendet. Dieses Skript kann nur den Bibliothekspfad für den aktuellen Server zurück. 

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
+ [Tipps für die Installation von R-Pakete](packages-installed-in-user-libraries.md)
+ [Standardpakete](installing-and-managing-r-packages.md)