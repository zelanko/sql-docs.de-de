---
title: Installieren neuer R-Pakete
description: Hier erfahren Sie, wie Sie mit sqlmlutils neue R-Pakete in einer Instanz von SQL Server Machine Learning Services oder SQL Server R Services installieren können.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 827e83a0d1b363d3b91477b9ae85fec156ee4fc9
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727498"
---
# <a name="install-new-r-packages-with-sqlmlutils"></a>Installieren von neuen R-Paketen mit sqlmlutils

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel wird beschrieben, wie Sie Funktionen im [**sqlmlutils**](https://github.com/Microsoft/sqlmlutils)-Paket verwenden, um neue R-Pakete in einer Instanz von SQL Server Machine Learning Services oder SQL Server R Services zu installieren. Die von Ihnen installierten Pakete können verwendet werden, um R-Skripts innerhalb einer Datenbank mithilfe der T-SQL-Anweisung [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) auszuführen.

> [!NOTE]
> Der R-Standardbefehl `install.packages` wird für das Hinzufügen von R-Paketen in SQL Server nicht empfohlen. Verwenden Sie stattdessen **sqlmlutils**, wie in diesem Artikel beschrieben.

## <a name="prerequisites"></a>Voraussetzungen

- Installieren Sie [R](https://www.r-project.org) und [RStudio Desktop](https://www.rstudio.com/products/rstudio/download/) auf dem Clientcomputer, den Sie mit SQL Server verbinden. Zum Ausführen von Skripts können Sie jede beliebige R-IDE verwenden. In diesem Artikel wird jedoch davon ausgegangen, dass Sie RStudio nutzen.

- Installieren Sie [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/what-is) oder [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms) (SSMS) auf dem Clientcomputer, den Sie zum Herstellen der Verbindung mit SQL Server verwenden. Sie können auch andere Datenbankverwaltungs- oder Abfragetools verwenden. In diesem Artikel wird jedoch davon ausgegangen, dass Sie Azure Data Studio oder SSMS nutzen.

### <a name="other-considerations"></a>Weitere Überlegungen

- Ein R-Skript, das in SQL Server ausgeführt wird, kann nur Pakete verwenden, die in der Standardinstanzbibliothek installiert sind. SQL Server kann auch dann keine Pakete aus externen Bibliotheken laden, wenn sich die entsprechenden Bibliotheken auf demselben Computer befinden. Das gilt auch für R-Bibliotheken, die in anderen Microsoft-Produkten installiert sind.

- In einer gesicherten SQL Server-Umgebung sollten Sie Folgendes vermeiden:
  - Pakete, für die Netzwerkzugriff erforderlich ist
  - Pakete, für die erhöhte Zugriffsrechte für das Dateisystem erforderlich sind
  - Pakete, die für die Webentwicklung oder andere Aufgaben verwendet werden und nicht von der Ausführung in SQL Server profitieren

## <a name="install-sqlmlutils-on-the-client-computer"></a>Installieren von sqlmlutils auf dem Clientcomputer

Zur Verwendung von **sqlmlutils** müssen Sie dies zunächst auf dem Clientcomputer installieren, den Sie mit SQL Server verbinden.

Welches **sqlmlutils**-Paket verwendet wird, hängt vom **RODBCext**-Paket ab. Und welches **RODBCext**-Paket verwendet wird, hängt von einigen anderen Paketen ab. Mithilfe der folgenden Verfahren werden alle Pakete in der richtigen Reihenfolge installiert.

### <a name="install-sqlmlutils-online"></a>Onlineinstallation von sqlmlutils

Wenn der Clientcomputer Internetzugriff hat, können Sie **sqlmlutils** und die abhängigen Pakete online herunterladen und installieren.

1. Laden Sie die neueste **sqlmlutils**-ZIP-Datei von https://github.com/Microsoft/sqlmlutils/tree/master/R/dist auf den Clientcomputer herunter. Entpacken Sie die Datei jedoch nicht.

1. Öffnen Sie eine **Eingabeaufforderung**, und führen Sie die folgenden Befehle aus, um die Pakete **sqlmlutils** und **RODBCext** zu installieren. Ersetzen Sie den vollständigen Pfad zur **sqlmlutils**-ZIP-Datei, die Sie heruntergeladen haben. (In diesem Beispiel wird davon ausgegangen, dass dies die Datei im Ordner „Dokumente“ ist.) Das Paket **RODBCext** können Sie online finden und installieren.

   ```console
   R -e "install.packages('RODBCext', repos='https://cran.microsoft.com')"
   R CMD INSTALL %UserProfile%\Documents\sqlmlutils_0.7.1.zip
   ```

### <a name="install-sqlmlutils-offline"></a>Offlineinstallation von sqlmlutils

Wenn der Clientcomputer keine Internetverbindung hat, müssen Sie die Pakete **sqlmlutils** und **RODBCext** vorab mithilfe eines Computers mit Internetzugang herunterladen. Anschließend können Sie die Dateien in einen Ordner auf dem Clientcomputer kopieren und die Pakete offline installieren.

Das **RODBCext**-Paket enthält zahlreiche abhängige Pakete, sodass sich die Identifizierung aller Abhängigkeiten für ein Paket schwierig gestaltet. Daher sollten Sie [**miniCRAN**](https://andrie.github.io/miniCRAN/) verwenden, um einen lokalen Repositoryordner für das Paket zu erstellen, das alle abhängigen Pakete enthält.
Weitere Informationen finden Sie im Artikel zum Thema [Erstellen eines lokalen R-Paketrepositorys mit miniCRAN](create-a-local-package-repository-using-minicran.md).

Das **sqlmlutils**-Paket besteht aus einer ZIP-Datei, die Sie auf den Clientcomputer kopieren und dort installieren können.

Auf einem Computer mit Internetzugriff:

1. Installieren Sie **miniCRAN**. Weitere Informationen finden Sie unter [Installieren von miniCRAN](create-a-local-package-repository-using-minicran.md#install-minicran).

1. Führen Sie in RStudio das folgende R-Skript aus, um ein lokales Repository für das Paket **RODBCext** zu erstellen. In diesem Beispiel wird das Repository im Ordner `c:\downloads\rodbcext` erstellt.

   ::: moniker range=">=sql-server-2016||=sqlallproducts-allversions"

   ```R
   CRAN_mirror <- c(CRAN = "https://cran.microsoft.com")
   local_repo <- "c:/downloads/rodbcext"
   pkgs_needed <- "RODBCext"
   pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);

   makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.5");
   ```

   ::: moniker-end

   ::: moniker range=">=sql-server-linux-ver15||=sqlallproducts-allversions"

   ```R
   CRAN_mirror <- c(CRAN = "https://cran.microsoft.com")
   local_repo <- "c:/downloads/rodbcext"
   pkgs_needed <- "RODBCext"
   pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);

   makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "source", Rversion = "3.5");
   ```

   ::: moniker-end

   Geben Sie für den `Rversion`-Wert die unter SQL Server installierte Version von R an. Um zu ermitteln, welche Version installiert ist, verwenden Sie den folgenden T-SQL-Befehl.

   ```sql
   EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'print(R.version)'
   ```

1. Laden Sie die neueste **sqlmlutils**-ZIP-Datei unter https://github.com/Microsoft/sqlmlutils/tree/master/R/dist herunter. (Entpacken Sie die Datei jedoch nicht.) Laden Sie die Datei beispielsweise in das Verzeichnis `c:\downloads\sqlmlutils_0.7.1.zip`.

1. Kopieren Sie den gesamten **RODBCext**-Repositoryordner (`c:\downloads\rodbcext`) und die **sqlmlutils**-ZIP-Datei (`c:\downloads\sqlmlutils_0.7.1.zip`) auf den Clientcomputer. Kopieren Sie beispielsweise beides in den Ordner `c:\temp\packages` auf dem Clientcomputer.

Öffnen Sie auf dem Clientcomputer, den Sie zum Herstellen einer Verbindung mit SQL Server verwenden, eine Eingabeaufforderung, und führen Sie die folgenden Befehle aus, um zuerst **RODBCext** und dann **sqlmlutils** zu installieren.

```console
R -e "install.packages('RODBCext', repos='c:\temp\packages\rodbcext')"
R CMD INSTALL c:\temp\packages\sqlmlutils_0.7.1.zip
```

## <a name="add-an-r-package-on-sql-server"></a>Hinzufügen eines R-Pakets in SQL Server

Im folgenden Beispiel fügen Sie in SQL Server das Paket [**glue**](https://cran.r-project.org/web/packages/glue/) hinzu.

### <a name="add-the-package-online"></a>Hinzufügen des Pakets über eine Internetverbindung

Wenn der Clientcomputer, mit dem Sie sich mit SQL Server verbinden, über einen Internetzugang verfügt, können Sie mit **sqlmlutils** das Paket **glue** und alle Abhängigkeiten über das Internet suchen. Anschließend können Sie das Paket per Remotezugriff in einer SQL Server-Instanz installieren.

1. Öffnen Sie auf dem Clientcomputer RStudio, und erstellen Sie eine neue **R-Skriptdatei**.

1. Verwenden Sie das folgende R-Skript zum Installieren des **glue**-Pakets mithilfe von **sqlmlutils**. Ersetzen Sie die eigenen Verbindungsdaten der SQL Server-Datenbank. (Wenn Sie keine Windows-Authentifizierung verwenden, fügen Sie die Parameter `uid` und `pwd` hinzu.)

   ```R
   library(sqlmlutils)
   connection <- connectionInfo(
     server= "yourserver",
     database = "yourdatabase")

   sql_install.packages(connectionString = connection, pkgs = "glue", verbose = TRUE, scope = "PUBLIC")
   ```

   > [!TIP]
   > Für **scope** kann **PUBLIC** oder **PRIVATE** angegeben werden. Ein öffentlicher Bereich (PUBLIC) ist für den Datenbankadministrator zum Installieren von Paketen nützlich, die von allen Benutzern verwendet werden. Pakete in einem privaten Bereich (PRIVATE) sind nur für den Benutzer verfügbar, der sie installiert. Wenn Sie keinen Bereich definieren, wird die Standardeinstellung **PRIVATE** verwendet.

### <a name="add-the-package-offline"></a>Hinzufügen des Pakets ohne Internetverbindung

Wenn der Clientcomputer keine Internetverbindung hat, können Sie das **glue**-Paket mit **miniCRAN** und einem Computer mit Internetzugang herunterladen. Anschließend kopieren Sie das Paket auf den Clientcomputer, auf dem Sie das Paket offline installieren können.
Informationen zum Installieren von **miniCRAN** finden Sie unter [Installieren von miniCRAN](create-a-local-package-repository-using-minicran.md#install-minicran).

Auf einem Computer mit Internetzugriff:

1. Führen Sie das folgende R-Skript aus, um ein lokales Repository für **glue** zu erstellen. In diesem Beispiel wird der Repositoryordner im Verzeichnis `c:\downloads\glue` erstellt.

   ::: moniker range=">=sql-server-2016||=sqlallproducts-allversions"

   ```R
   CRAN_mirror <- c(CRAN = "https://cran.microsoft.com")
   local_repo <- "c:/downloads/glue"
   pkgs_needed <- "glue"
   pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);

   makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.5");
   ```

   ::: moniker-end

   ::: moniker range=">=sql-server-linux-ver15||=sqlallproducts-allversions"

   ```R
   CRAN_mirror <- c(CRAN = "https://cran.microsoft.com")
   local_repo <- "c:/downloads/glue"
   pkgs_needed <- "glue"
   pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);

   makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "source", Rversion = "3.5");
   ```

   ::: moniker-end


   Geben Sie für den `Rversion`-Wert die unter SQL Server installierte Version von R an. Um zu ermitteln, welche Version installiert ist, verwenden Sie den folgenden T-SQL-Befehl.

   ```sql
   EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'print(R.version)'
   ```

1. Kopieren Sie den gesamten **glue**-Repositoryordner (`c:\downloads\glue`) auf den Clientcomputer. Kopieren Sie ihn beispielsweise in den Ordner `c:\temp\packages\glue`.

Auf dem Clientcomputer:

1. Öffnen Sie RStudio, und erstellen Sie eine neue **R-Skriptdatei**.

1. Verwenden Sie das folgende R-Skript zum Installieren des **glue**-Pakets mithilfe von **sqlmlutils**. Ersetzen Sie die eigenen Verbindungsdaten der SQL Server-Datenbank. (Wenn Sie keine Windows-Authentifizierung verwenden, fügen Sie die Parameter `uid` und `pwd` hinzu.)

   ```R
   library(sqlmlutils)
   connection <- connectionInfo(
     server= "yourserver",
     database = "yourdatabase")
   localRepo = "c:/temp/packages/glue"

   sql_install.packages(connectionString = connection, pkgs = "glue", verbose = TRUE, scope = "PUBLIC", repos=paste0("file:///",localRepo))
   ```

   > [!TIP]
   > Für **scope** kann **PUBLIC** oder **PRIVATE** angegeben werden. Ein öffentlicher Bereich (PUBLIC) ist für den Datenbankadministrator zum Installieren von Paketen nützlich, die von allen Benutzern verwendet werden. Pakete in einem privaten Bereich (PRIVATE) sind nur für den Benutzer verfügbar, der sie installiert. Wenn Sie keinen Bereich definieren, wird die Standardeinstellung **PRIVATE** verwendet.

## <a name="use-the-package"></a>Verwenden des Pakets

Nachdem Sie das **glue**-Paket installiert haben, können Sie es in einem R-Skript in SQL Server mit dem T-SQL-Befehl **sp_execute_external_script** verwenden.

1. Öffnen Sie Azure Data Studio oder SSMS, und stellen Sie eine Verbindung mit Ihrer SQL Server-Datenbank her.

1. Führen Sie den folgenden Befehl aus:

   ```sql
   EXECUTE sp_execute_external_script @language = N'R'
       , @script = N'
   library(glue)

   name <- "Fred"
   birthday <- as.Date("2020-06-14")
   text <- glue(''My name is {name} '',
   ''and my birthday is {format(birthday, "%A, %B %d, %Y")}.'')

   print(text)
         ';
   ```

    **Ergebnisse**

    ```text
    My name is Fred and my birthday is Sunday, June 14, 2020.
    ```

## <a name="remove-the-package"></a>Entfernen des Programms

Wenn Sie das **glue**-Paket entfernen möchten, führen Sie das folgende R-Skript aus. Verwenden Sie die zuvor definierte **Verbindungsvariable**.

```R
sql_remove.packages(connectionString = connection, pkgs = "glue", scope = "PUBLIC")
```

## <a name="next-steps"></a>Nächste Schritte

- Informationen zu installierten R-Paketen finden Sie unter [Abrufen von Paketinformationen für R](r-package-information.md).
- Unterstützung bei der Verwendung von R-Paketen finden Sie unter [Tipps für die Verwendung von R-Paketen](tips-for-using-r-packages.md).
- Informationen zum Installieren von Python-Paketen finden Sie unter [Installieren von Python-Paketen mit pip](install-additional-python-packages-on-sql-server.md).
- Weitere Informationen zu SQL Server Machine Learning Services finden Sie unter [Was ist SQL Server Machine Learning Services (Python und R)?](../what-is-sql-server-machine-learning.md)
