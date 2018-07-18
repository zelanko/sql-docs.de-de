---
title: So verwenden Sie RevoScaleR-Funktionen zum Suchen, oder installieren Sie R-Paketen auf SQL Server | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: d92b3e993968ce48d7489b0c17d6bdba005809a3
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34707528"
---
# <a name="how-to-use-revoscaler-functions-to-find-or-install-r-packages-on-sql-server"></a>So verwenden Sie RevoScaleR-Funktionen zum Suchen, oder installieren R-Pakete auf SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

"Revoscaler" 9.0.1 und höher inklusive Funktionen für die Verwaltung der R-Paket einen SQL Server-computekontext. Diese Funktionen können remote, nicht-Administratoren verwendet werden, um Pakete auf SQL Server ohne direkten Zugriff auf den Server zu installieren.

SQL Server 2017 Machine Learning Services enthält bereits eine neuere Version von "revoscaler". SQL Server 2016-R-Services-Kunden müssen einen [Komponentenupdate](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md) RevoScaleR-Paket-Verwaltungsfunktionen abrufen. Anweisungen zum Abrufen von Version und des Inhalts zu verpacken, finden Sie unter [abrufen Paketinformationen](determine-which-packages-are-installed-on-sql-server.md).

## <a name="revoscaler-functions-for-package-management"></a>RevoScaleR-Funktionen für paketverwaltung

Die folgende Tabelle beschreibt die Funktionen für R-Paket-Installation und Verwaltung verwendet.

| Funktion | Description |
|----------|-------------|
| [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) | Ermitteln des Pfads der Instanz-Bibliothek auf dem SQL-Remoteserver. |
| [rxFindPackage](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxfindpackage) | Ruft den Pfad für ein oder mehrere Pakete auf dem SQL-Remoteserver. |
| [rxInstallPackages](https://docs.microsoft.com/en-us/machine-learning-server/r-reference/revoscaler/rxinstallpackages) | Mit dieser Funktion wird von einem Remoteclient "R" zum Installieren der Pakete in einer SQL Server-computekontext, entweder aus einem angegebenen Repository oder durch Lesen der komprimierten Pakete lokal gespeichert. Diese Funktion überprüft, ob Abhängigkeiten und stellt sicher, dass alle zugehörigen Pakete zu SQL Server, wie durch die Installation von R-Paket im lokalen rechenkontext installiert werden können. Um diese Option verwenden zu können, müssen Sie paketverwaltung auf dem Server und die Datenbank aktiviert haben. Client- und Server-Umgebungen müssen die gleiche Version von "revoscaler" haben. |
| [rxInstalledPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstalledpackages) | Ruft eine Liste der Pakete installiert, die in der angegebenen computekontext ab. |
| [rxSyncPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsyncpackages) | Kopieren Sie die Informationen zu einer Bibliothek Paket zwischen dem Dateisystem und die Datenbank, für die angegebene computekontext. |
| [rxRemovePackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxremovepackages) | Entfernt Pakete aus einer angegebenen computekontext. Außerdem Abhängigkeiten berechnet, und es wird sichergestellt, dass Pakete, die von anderen Paketen in SQL Server nicht mehr verwendet werden entfernt werden, um Ressourcen freizugeben. |

## <a name="prerequisites"></a>Erforderliche Komponenten

+ [Aktivieren der R-Paket Remoteverwaltung auf SQL Server](r-package-how-to-enable-or-disable.md)

+ "Revoscaler"-Versionen müssen auf dem Client und Server-Umgebungen entsprechen. Weitere Informationen finden Sie unter [abrufen Paketinformationen](determine-which-packages-are-installed-on-sql-server.md).

+ Berechtigung für die Verbindung mit dem Server und Ihrer Datenbank und R-Befehle auszuführen. Sie müssen ein Mitglied einer Datenbankrolle sein, die Ihnen ermöglicht, die Pakete auf die angegebene Instanz und die Datenbank zu installieren.

+ Pakete in **freigegebener Bereich** installiert werden, indem der Benutzer, die die `rpkgs-shared` Rolle in einer angegebenen Datenbank. Alle Benutzer in dieser Rolle können freigegebene Pakete zu deinstallieren.

+ Pakete in **privaten Bereich** kann installiert werden, von jedem Benutzer, die zu gehören die `rpkgs-private` Rolle in einer Datenbank. Allerdings können Benutzer sehen und nur ihre eigenen Pakete zu deinstallieren.

+ Datenbankbesitzer können freigegeben oder privat Pakete verwenden.

## <a name="client-connections"></a>Clientverbindungen

Kann von eine Clientarbeitsstation [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/install-on-windows) oder ein [Microsoft Machine Learning-Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) (Datenanalysten verwenden häufig die kostenlose Developer Edition) im selben Netzwerk.

Beim Aufrufen von Paket-Verwaltungsfunktionen von einem Remoteclient R müssen zuerst erstellen Sie eine Compute Context-Objekt, mit der [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) Funktion. Übergeben Sie für jede Paket-Management-Funktion, die Sie verwenden und danach computekontext als Argument.

Identität des Benutzers wird beim Festlegen des computekontexts in der Regel angegeben. Wenn Sie nicht angeben einen Benutzernamen und das Kennwort bei der Erstellung des computekontexts, dient die Identität des Benutzers, den R-Code ausführt.

1. Definieren Sie über eine Befehlszeile R eine Verbindungszeichenfolge für die Instanz und die Datenbank ein.
2. Verwenden der [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) Konstruktor, um einen SQL Server-computekontext, mithilfe der Verbindungszeichenfolge zu definieren.

    ```R
    sqlcc <- RxInSqlServer(connectionString = myConnString, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    ```
3. Erstellen Sie eine Liste der Pakete, die Sie verwenden möchten, installieren, und speichern Sie die Liste in einer Zeichenfolgenvariablen.

    ```R
    packageList <- c("e1071", "mice")
    ```

4. Rufen Sie [RxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) und übergeben des computekontexts und die Zeichenfolgenvariable, die mit den Paketnamen.

    ```R
    rxInstallPackages(pkgs = packageList, verbose = TRUE, computeContext = sqlcc)
    ```

    Wenn die abhängigen Programme erforderlich sind, werden sie auch installiert, vorausgesetzt, dass eine Internetverbindung auf dem Client verfügbar ist.
    
    Pakete werden mit den Anmeldeinformationen des Benutzers vornimmt, die Verbindung in den Standardbereich für diesen Benutzer installiert.

## <a name="call-package-management-functions-in-stored-procedures"></a>Rufen Sie die Paket-Verwaltungsfunktionen in gespeicherten Prozeduren

Cam führen Sie die Paket-Verwaltungsfunktionen in `sp_execute_external_script`. Wenn Sie dies tun, wird die Funktion mithilfe des Sicherheitskontexts des Aufrufers gespeicherte Prozedur ausgeführt.

## <a name="examples"></a>Beispiele

Dieser Abschnitt enthält Beispiele zur Verwendung dieser Funktionen von einem Remoteclient aus, bei der Verbindung mit einer SQL Server-Instanz oder Datenbank als computekontext.

Für alle Beispiele müssen Sie eine Verbindungszeichenfolge oder einen computekontext, wofür eine Verbindungszeichenfolge bereitstellen. In diesem Beispiel bietet eine Möglichkeit, einen computekontext für SQL Server zu erstellen:

```R
instance_name <- "computer-name/instance-name";
database_name <- "TestDB";
sqlWait= TRUE;
sqlConsoleOutput <- TRUE;
connString <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
sqlcc <- RxInSqlServer(connectionString = connString, wait = sqlWait, consoleOutput = sqlConsoleOutput, numTasks = 4);
```

Je nachdem, wo sich der Server befindet, und das Sicherheitsmodell müssen Sie eine Domäne und ein Subnetz-Spezifikation in der Verbindungszeichenfolge bereitstellen, oder verwenden Sie eine SQL-Anmeldung. Zum Beispiel:

```R
connStr <- "Driver=SQL Server;Server=myserver.financeweb.contoso.com;Database=Finance;Uid=RUser1;Pwd=RUserPassword"
```

### <a name="get-package-path-on-a-remote-sql-server-compute-context"></a>Abrufen von Paketpfad auf einen Remoteserver SQL Server-computekontext

In diesem Beispiel ruft den Pfad für die **"revoscaler"** Paket auf die computekontext `sqlcc`.

```R
sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlcc)
print(sqlPackagePaths)
```

**Ergebnisse**

"C: / Program Programme/Microsoft SQL Server/MSSQL14. MSSQLSERVER/R_SERVICES/Library / "revoscaler""

> [!TIP]
> Wenn Sie die Option aus, um die Ausgabe des SQL-Konsole finden Sie unter aktiviert haben, möglicherweise erhalten Sie statusmeldungen aus der Funktion, die vor der `print` Anweisung. Legen Sie Sie nach dem Testen von Code `consoleOutput` auf "false" in der Compute-Kontext-Konstruktor, um Nachrichten zu vermeiden.

### <a name="get-locations-for-multiple-packages"></a>Abrufen von Speicherorten für mehrere Pakete

Im folgende Beispiel ruft die Pfade für die **"revoscaler"** und **Vektorgitters** -Pakete, auf die computekontext `sqlcc`. Übergeben Sie zum Abrufen von Informationen über mehrere Pakete einen Zeichenfolge-Vektor mit den Paketnamen ein.

```R
packagePaths <- rxFindPackage(package = c("RevoScaleR", "lattice"), computeContext = sqlcc)
print(packagePaths)
```

### <a name="get-package-versions-on-a-remote-compute-context"></a>Abrufen von Paketversionen auf einem remote-computekontext.

Führen Sie diesen Befehl aus einer R-Konsole zum Abrufen der Build-Nummer und Versionsnummern für Pakete, die auf die computekontext installiert *SqlServer*.

```R
sqlPackages <- rxInstalledPackages(fields = c("Package", "Version", "Built"), computeContext = sqlServer)
```

**Ergebnisse**

```text
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library/RevoScaleR"

[2] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library/lattice"
```

### <a name="install-a-package-on-sql-server"></a>Installieren eines Pakets in SQL Server

In diesem Beispiel installiert die **prognostizieren** Paket und dessen Abhängigkeiten in der computekontext.

  ```R
  pkgs <- c("forecast")
  rxInstallPackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlcc)
  ```

### <a name="remove-a-package-from-sql-server"></a>Entfernen eines Pakets aus SQL Server

In diesem Beispiel wird die **prognostizieren** Paket und seine Abhängigkeiten aus dem computekontext.

  ```R
  pkgs <- c("forecast")
  rxRemovePackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlcc)
  ```

### <a name="synchronize-packages-between-database-and-file-system"></a>Synchronisieren Sie Pakete zwischen Datenbank und Dateisystem

Das folgende Beispiel überprüft die Datenbank **TestDB**, und bestimmt, ob alle Pakete im Dateisystem installiert werden. Wenn einige Pakete fehlen, werden sie im Dateisystem installiert.

```R
# Instantiate the compute context
connectionString <- "Driver=SQL Server;Server=myServer;Database=TestDB;Trusted_Connection=True;"
computeContext <- RxInSqlServer(connectionString = connectionString )

# Synchronize the packages in the file system for all scopes and users
rxSyncPackages(computeContext=computeContext, verbose=TRUE)
```

Paketsynchronisierung funktioniert auf einer pro Datenbank und pro Benutzer. Weitere Informationen finden Sie unter [R-Paket-Synchronisierung für SQL Server](../r/package-install-uninstall-and-sync.md).

### <a name="use-a-stored-procedure-to-list-packages-in-sql-server"></a>Verwenden einer gespeicherten Prozedur in der Liste von Paketen in SQL Server

Führen Sie diesen Befehl in Management Studio oder ein anderes Tool, das T-SQL, um eine Liste der installierten Pakete auf der aktuellen Instanz erhalten unterstützt mit `rxInstalledPackages` in einer gespeicherten Prozedur.

```SQL
EXEC sp_execute_external_script 
  @language=N'R', 
  @script=N'
    myPackages <- rxInstalledPackages();
    OutputDataSet <- as.data.frame(myPackages);
    '
```

Die `rxSqlLibPaths` -Funktion kann verwendet werden, um zu bestimmen, der aktiven Library von SQL Server-Machine Learning-Services verwendet. Dieses Skript kann nur den Pfad für den aktuellen Server zurückzugeben. 

```SQL
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