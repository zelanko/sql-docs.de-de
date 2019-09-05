---
title: Installieren neuer R-Pakete mit sqlmlutils
description: Erfahren Sie, wie Sie sqlmlutils verwenden, um neue R-Pakete in einer Instanz von SQL Server Machine Learning Services oder SQL Server R Services zu installieren.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3b5a55ec16c7dfa2f16dbae62674a475fb39c5d7
ms.sourcegitcommit: 26715b4dbef95d99abf2ab7198a00e6e2c550243
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/04/2019
ms.locfileid: "70275675"
---
# <a name="install-new-r-packages-with-sqlmlutils"></a>Installieren neuer R-Pakete mit sqlmlutils

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel wird beschrieben, wie Sie Funktionen im [**sqlmlutils**](https://github.com/Microsoft/sqlmlutils) -Paket verwenden, um neue R-Pakete in einer Instanz von SQL Server Machine Learning Services oder SQL Server R Services zu installieren. Die von Ihnen installierten Pakete können in R-Skripts verwendet werden, die in-Database mit der [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) T-SQL-Anweisung ausgeführt werden.

> [!NOTE]
> Der Standard- `install.packages` R-Befehl wird nicht zum Hinzufügen von r-Paketen auf SQL Server empfohlen. Verwenden Sie stattdessen **sqlmlutils** , wie in diesem Artikel beschrieben.

## <a name="prerequisites"></a>Erforderliche Komponenten

- Installieren Sie [R](https://www.r-project.org) und [rstudio Desktop](https://www.rstudio.com/products/rstudio/download/) auf dem Client Computer, mit dem Sie eine Verbindung mit SQL Server herstellen. Sie können eine beliebige R-IDE zum Ausführen von Skripts verwenden, aber in diesem Artikel wird von rstudio ausgegangen.

- Installieren Sie [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/what-is) oder [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms) (SSMS) auf dem Client Computer, den Sie verwenden, um eine Verbindung mit SQL Server herzustellen. Sie können andere Daten Bank Verwaltungs-oder Abfrage Tools verwenden, aber in diesem Artikel wird davon ausgegangen, Azure Data Studio oder SSMS zu verwenden.

### <a name="other-considerations"></a>Andere Überlegungen

- R-Skript, das in SQL Server ausgeführt wird, kann nur Pakete verwenden, die in der standardinstanzbibliothek SQL Server können Pakete nicht aus externen Bibliotheken laden, auch wenn sich diese Bibliothek auf demselben Computer befindet. Dies umfasst auch R-Bibliotheken, die mit anderen Microsoft-Produkten installiert werden

- In einer SQL Server Umgebung mit verstärkter Sicherheit sollten Sie Folgendes vermeiden:
  - Pakete, für die Netzwerk Zugriff erforderlich ist
  - Pakete, für die ein erhöhter Dateisystem Zugriff erforderlich ist
  - Pakete, die für die Webentwicklung oder andere Aufgaben verwendet werden, die nicht von der Ausführung innerhalb SQL Server profitieren

## <a name="install-sqlmlutils-on-the-client-computer"></a>Installieren von sqlmlutils auf dem Client Computer

Um **sqlmlutils**verwenden zu können, müssen Sie es zuerst auf dem Client Computer installieren, mit dem Sie eine Verbindung mit SQL Server herstellen.

Das **sqlmlutils** -Paket ist von dem **rodbcext** -Paket abhängig, und **rodbcext** hängt von einer Reihe von anderen Paketen ab. In den folgenden Verfahren werden alle diese Pakete in der richtigen Reihenfolge installiert.

### <a name="install-sqlmlutils-online"></a>Installieren von sqlmlutils Online

Wenn der Client Computer über Internet Zugriff verfügt, können Sie **sqlmlutils** und die abhängigen Pakete Online herunterladen und installieren.

1. Laden Sie die aktuelle **sqlmlutils** -Zip https://github.com/Microsoft/sqlmlutils/tree/master/R/dist -Datei von auf den Client Computer herunter. Entzippen Sie die Datei nicht.

1. Öffnen Sie eine **Eingabeaufforderung** , und führen Sie die folgenden Befehle aus, um die Pakete **sqlmlutils** und **rodbcext**zu installieren. Ersetzen Sie den vollständigen Pfad der heruntergeladenen ZIP-Datei von **sqlmlutils** (in diesem Beispiel wird davon ausgegangen, dass sich die Datei im Ordner "Dokumente" befindet). Das **rodbcext** -Paket wurde Online und installiert gefunden.

   ```console
   R -e "install.packages('RODBCext', repos='https://cran.microsoft.com')"
   R CMD INSTALL %UserProfile%\Documents\sqlmlutils_0.7.1.zip
   ```

### <a name="install-sqlmlutils-offline"></a>Sqlmlutils Offline installieren

Wenn der Client Computer nicht über eine Internetverbindung verfügt, müssen Sie die Pakete **sqlmlutils** und **rodbcext** vorab mithilfe eines Computers herunterladen, der über Internet Zugriff verfügt. Anschließend können Sie die Dateien in einen Ordner auf dem Client Computer kopieren und die Pakete Offline installieren.

Das **rodbcext** -Paket verfügt über eine Reihe von abhängigen Paketen, und das Identifizieren aller Abhängigkeiten für ein Paket wird erschwert. Es wird empfohlen, [**minicran**](https://andrie.github.io/miniCRAN/) zu verwenden, um einen lokalen Repository-Ordner für das Paket zu erstellen, das alle abhängigen Pakete enthält.
Weitere Informationen finden Sie unter [Erstellen eines lokalen R-paketrepositorys mit minicran](create-a-local-package-repository-using-minicran.md).

Das **sqlmlutils** -Paket besteht aus einer einzelnen ZIP-Datei, die Sie auf den Client Computer kopieren und installieren können.

Auf einem Computer mit Internet Zugriff:

1. Installieren Sie **minicran**. Weitere Informationen finden Sie unter [install minicran](create-a-local-package-repository-using-minicran.md#install-minicran) .

1. Führen Sie in rstudio das folgende R-Skript aus, um ein lokales Repository des Pakets **rodbcext**zu erstellen. In diesem Beispiel wird das Repository im Ordner `c:\downloads\rodbcext`erstellt.

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

   Verwenden Sie als Wert die Version von R, die auf SQL Server installiert ist. `Rversion` Verwenden Sie den folgenden T-SQL-Befehl, um die installierte Version zu überprüfen.

   ```sql
   EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'print(R.version)'
   ```

1. Laden Sie die neueste ZIP-Datei von **sqlmlutils** aus https://github.com/Microsoft/sqlmlutils/tree/master/R/dist herunter (Entzippen Sie die Datei nicht). Laden Sie beispielsweise die Datei in `c:\downloads\sqlmlutils_0.7.1.zip`herunter.

1. Kopieren Sie den gesamten **rodbcext** -Repository`c:\downloads\rodbcext`-Ordner () und die **sqlmlutils** -ZIP-Datei (`c:\downloads\sqlmlutils_0.7.1.zip`) auf den Client Computer. Kopieren Sie diese z. b. in `c:\temp\packages` den Ordner auf dem Client Computer.

Öffnen Sie auf dem Client Computer, mit dem Sie eine Verbindung mit SQL Server herstellen, eine Eingabeaufforderung, und führen Sie die folgenden Befehle zum Installieren von **rodbcext** und dann **sqlmlutils**aus.

```console
R -e "install.packages('RODBCext', repos='c:\temp\packages\rodbcext')"
R CMD INSTALL c:\temp\packages\sqlmlutils_0.7.1.zip
```

## <a name="add-an-r-package-on-sql-server"></a>Hinzufügen eines R-Pakets auf SQL Server

Im folgenden Beispiel fügen Sie das- [**Installationspaket SQL Server**](https://cran.r-project.org/web/packages/glue/) hinzu.

### <a name="add-the-package-online"></a>Paket online hinzufügen

Wenn der Client Computer, mit dem Sie eine Verbindung mit SQL Server herstellen, über Internet Zugriff verfügt, können Sie mithilfe von **sqlmlutils** das **Klebe** Paket und alle Abhängigkeiten über das Internet suchen und das Paket dann Remote auf einer SQL Server Instanz installieren.

1. Öffnen Sie auf dem Client Computer rstudio, und erstellen Sie eine neue **R-Skript** Datei.

1. Verwenden Sie das folgende R-Skript, um **das Paket mit** **sqlmlutils**zu installieren. Ersetzen Sie Ihre eigenen SQL Server Daten bankverbindungs Informationen.

   ```R
   library(sqlmlutils)
   connection <- connectionInfo(
     server= "yourserver",
     database = "yourdatabase",
     uid = "yoursqluser",
     pwd = "yoursqlpassword")

   sql_install.packages(connectionString = connection, pkgs = "glue", verbose = TRUE, scope = "PUBLIC")
   ```

   > [!TIP]
   > Der **Bereich** kann entweder **öffentlich** oder **Privat**sein. Der öffentliche Bereich ist hilfreich für den Datenbankadministrator, um Pakete zu installieren, die von allen Benutzern verwendet werden können. Der private Bereich macht das Paket nur für den Benutzer verfügbar, der es installiert. Wenn Sie den Bereich nicht angeben, ist der Standardbereich **Privat**.

### <a name="add-the-package-offline"></a>Paket Offline hinzufügen

Wenn der Client Computer nicht über eine Internetverbindung verfügt, können Sie mit **minicran** **das Bindungs** Paket mithilfe eines Computers herunterladen, der über Internet Zugriff verfügt. Anschließend kopieren Sie das Paket auf den Client Computer, auf dem Sie das Paket Offline installieren können.
Weitere Informationen zum Installieren von **minicran**finden Sie unter [install minicran](create-a-local-package-repository-using-minicran.md#install-minicran) .

Auf einem Computer mit Internet Zugriff:

1. Führen Sie das folgende R-Skript aus, um ein lokales Repository für den **Kleber**zu erstellen. In diesem Beispiel wird der Repository- `c:\downloads\glue`Ordner in erstellt.

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


   Verwenden Sie als Wert die Version von R, die auf SQL Server installiert ist. `Rversion` Verwenden Sie den folgenden T-SQL-Befehl, um die installierte Version zu überprüfen.

   ```sql
   EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'print(R.version)'
   ```

1. Kopieren Sie den gesamten Ordner für den`c:\downloads\glue` **kleberepository** () auf den Client Computer. Kopieren Sie diese z. b. in `c:\temp\packages\glue`den Ordner.

Auf dem Client Computer:

1. Öffnen Sie rstudio, und erstellen Sie eine neue **R-Skript** Datei.

1. Verwenden Sie das folgende R-Skript, um **das Paket mit** **sqlmlutils**zu installieren. Ersetzen Sie Ihre eigenen SQL Server Daten bankverbindungs Informationen.

   ```R
   library(sqlmlutils)
   connection <- connectionInfo(
     server= "yourserver",
     database = "yourdatabase",
     uid = "yoursqluser",
     pwd = "yoursqlpassword")
   localRepo = "c:/temp/packages/glue"

   sql_install.packages(connectionString = connection, pkgs = "glue", verbose = TRUE, scope = "PUBLIC", repos=paste0("file:///",localRepo))
   ```

   > [!TIP]
   > Der **Bereich** kann entweder **öffentlich** oder **Privat**sein. Der öffentliche Bereich ist hilfreich für den Datenbankadministrator, um Pakete zu installieren, die von allen Benutzern verwendet werden können. Der private Bereich macht das Paket nur für den Benutzer verfügbar, der es installiert. Wenn Sie den Bereich nicht angeben, ist der Standardbereich **Privat**.

## <a name="use-the-package"></a>Verwenden des Pakets

Sobald das **Installationspaket installiert** ist, können Sie es in einem R-Skript in SQL Server mit dem T-SQL-Befehl " **sp_execute_external_script** " verwenden.

1. Öffnen Sie Azure Data Studio oder SSMS, und stellen Sie eine Verbindung mit Ihrer SQL Server Datenbank her.

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

## <a name="remove-the-package"></a>Entfernen des Pakets

Wenn Sie das **Klebe** Paket entfernen möchten, führen Sie das folgende R-Skript aus. Verwenden Sie dieselbe **Verbindungs** Variable, die Sie zuvor definiert haben.

```R
sql_remove.packages(connectionString = connection, pkgs = "glue", scope = "PUBLIC")
```

## <a name="next-steps"></a>Nächste Schritte

- Informationen zu installierten r-Paketen finden [Sie unter Get R Package Information](r-package-information.md) .
- Hilfe beim Arbeiten mit r-Paketen finden [Sie unter Tipps für die Verwendung von r-Paketen](tips-for-using-r-packages.md) .
- Weitere Informationen zum Installieren von Python-Paketen finden Sie unter [Installieren von Python-Paketen mit PIP](install-additional-python-packages-on-sql-server.md) .
- Weitere Informationen zum SQL Server Machine Learning Services finden Sie unter [Was ist SQL Server Machine Learning Services (python und R)?](../what-is-sql-server-machine-learning.md)
