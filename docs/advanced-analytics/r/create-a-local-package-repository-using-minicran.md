---
title: Erstellen eines lokalen R-paketrepositorys mit minicran
description: Erfahren Sie, wie Sie R-Pakete Offline installieren, indem Sie das minicran-Paket verwenden, um ein lokales Repository von Paketen und Abhängigkeiten zu erstellen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 68f86d673b944a029c7bd0f74c9594692bd579f4
ms.sourcegitcommit: 632ff55084339f054d5934a81c63c77a93ede4ce
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "69634172"
---
# <a name="create-a-local-r-package-repository-using-minicran"></a>Erstellen eines lokalen R-paketrepositorys mit minicran
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel wird beschrieben, wie Sie R-Pakete mithilfe von [minicran](https://cran.r-project.org/web/packages/miniCRAN/index.html) Offline installieren, um ein lokales Repository von Paketen und Abhängigkeiten zu erstellen. **minicran** identifiziert Pakete und Abhängigkeiten in einem einzelnen Ordner, den Sie für die Offline Installation von R-Paketen auf andere Computer kopieren, und lädt Sie herunter.

Sie können ein oder mehrere Pakete angeben. der **minicran** -Code liest die Abhängigkeitsstruktur für diese Pakete rekursiv. Anschließend werden nur die aufgelisteten Pakete und ihre Abhängigkeiten von CRAN oder ähnlichen Depots heruntergeladen.

Wenn dies der Fall ist, erstellt **minicran** ein intern konsistentes Repository, das aus den ausgewählten Paketen und allen erforderlichen Abhängigkeiten besteht. Sie können dieses lokale Repository auf den Server verschieben und mit der Installation der Pakete ohne Internetverbindung fortfahren.

Erfahrene R-Benutzer suchen häufig nach der Liste der abhängigen Pakete in der Beschreibungsdatei eines heruntergeladenen Pakets. In **Imports** aufgelistete Pakete verfügen jedoch möglicherweise über Abhängigkeiten auf zweiter Ebene. Aus diesem Grund empfiehlt es sich, **minicran** für die Assemblierung der vollständigen Sammlung erforderlicher Pakete zu erhalten.

## <a name="why-create-a-local-repository"></a>Gründe für das Erstellen eines lokalen Repository

Das Ziel der Erstellung eines lokalen paketrepositorys besteht darin, einen einzelnen Speicherort bereitzustellen, der von einem Server Administrator oder anderen Benutzern in der Organisation verwendet werden kann, um neue R-Pakete auf einem Server zu installieren, insbesondere einen, der nicht über Internet Zugriff verfügt. Nachdem Sie das Repository erstellt haben, können Sie es ändern, indem Sie neue Pakete hinzufügen oder die Version vorhandener Pakete aktualisieren.

Paketrepositorys sind in folgenden Szenarien nützlich:

- **Sicherheit**: Viele r-Benutzer sind daran gewöhnt, neue r-Pakete auf der Grundlage von CRAN oder einer ihrer Spiegel Sites herunterzuladen und zu installieren. Aus Sicherheitsgründen verfügen Produktionsserver, auf denen [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ausgeführt wird, jedoch in der Regel nicht über Internet Konnektivität.

- **Einfachere Offline Installation**: Zum Installieren eines Pakets auf einem Offline Server müssen Sie auch alle Paketabhängigkeiten herunterladen. Die Verwendung von minicran vereinfacht das erzielen aller Abhängigkeiten im richtigen Format. Durch die Verwendung von minicran können Sie Paket Abhängigkeitsfehler vermeiden, wenn Sie Pakete für die Installation mit der [Create externe Library](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) -Anweisung vorbereiten.

- **Verbesserte Versionsverwaltung**: In einer mehr Benutzerumgebung gibt es gute Gründe, eine uneingeschränkte Installation mehrerer Paketversionen auf dem Server zu vermeiden. Verwenden Sie ein lokales Repository, um einen konsistenten Satz von Paketen für Ihre Benutzer bereitzustellen.

## <a name="install-minicran"></a>Installieren von minicran

Das **minicran** -Paket selbst ist von 18 anderen cran-Paketen abhängig. dabei handelt es sich um das **rcurl** -Paket, das eine System Abhängigkeit vom **curl-devel-** Paket aufweist. Ebenso hat Paket- **XML** eine Abhängigkeit von **libxml2-devel**. Um Abhängigkeiten aufzulösen, empfiehlt es sich, das lokale Repository zunächst auf einem Computer zu erstellen, der über Vollzugriff auf das Internet verfügt.

Führen Sie die folgenden Befehle auf einem Computer mit Basis-r, r-Tools und Internetverbindung aus. Es wird davon ausgegangen, dass es sich hierbei nicht um Ihren SQL Server Computer handelt. Mit den folgenden Befehlen werden das **minicran** -Paket und das **igraph** -Paket installiert. In diesem Beispiel wird überprüft, ob das Paket bereits installiert ist, aber Sie `if` können die-Anweisungen umgehen und die Pakete direkt installieren.

```R
if(!require("miniCRAN")) install.packages("miniCRAN") 
if(!require("igraph")) install.packages("igraph") 
library("miniCRAN")
```

## <a name="set-the-cran-mirror-and-mran-snapshot"></a>Festlegen des cran-Spiegels und der mran-Momentaufnahme

Geben Sie eine Spiegel Website an, die zum erhalten von Paketen verwendet wird. Beispielsweise können Sie die mran-Website oder eine beliebige andere Website in Ihrer Region verwenden, die die benötigten Pakete enthält. Wenn ein Download fehlschlägt, versuchen Sie es mit einer anderen Spiegel Website.

```R
CRAN_mirror <- c(CRAN = "https://cran.cnr.berkeley.edu")
```

## <a name="create-a-local-folder"></a>Erstellen eines lokalen Ordners

Erstellen Sie einen lokalen Ordner, in dem die gesammelten Pakete gespeichert werden sollen. Wenn Sie dies häufig wiederholen, empfiehlt es sich, einen beschreibenden Namen zu verwenden, z. b. "minicranzoomopackages" oder "miniCRANMyRPackageV2".

Geben Sie den Ordner als lokales Repository an. Die R-Syntax verwendet einen Schrägstrich für Pfadnamen, der gegen Windows-Konventionen steht.

```R
local_repo <- "C:/miniCRANZooPackages"
```

## <a name="add-packages-to-the-local-repo"></a>Hinzufügen von Paketen zum lokalen Repository

Nachdem **minicran** installiert und geladen wurde, erstellen Sie eine Liste, in der die zusätzlichen Pakete angegeben sind, die Sie herunterladen möchten.

Fügen Sie dieser anfangs Liste **keine** Abhängigkeiten hinzu. Das **igraph** -Paket, das von **minicran** verwendet wird, generiert automatisch die Liste der Abhängigkeiten. Weitere Informationen zur Verwendung des generierten Abhängigkeits Diagramms finden Sie unter [Verwenden von minicran zur Identifizierung von Paketabhängigkeiten](https://cran.r-project.org/web/packages/miniCRAN/vignettes/miniCRAN-dependency-graph.html).

1. Fügen Sie den Ziel Paketen ' Zoo ' und ' Forecast ' einer Variablen hinzu.

    ```R
    pkgs_needed <- c("zoo", "forecast")
    ```

2. Optional können Sie das Abhängigkeits Diagramm zeichnen. Dies ist nicht erforderlich, kann aber informativ sein.

    ```R
    plot(makeDepGraph(pkgs_needed))
    ```

3. Erstellen Sie das lokale Repository. Stellen Sie sicher, dass Sie ggf. die R-Version in die Version ändern, die auf der SQL Server-Instanz installiert ist. Wenn Sie ein Komponenten Upgrade durchgeführt haben, ist die Version möglicherweise neuer als die ursprüngliche Version. Weitere Informationen finden Sie unter [Get R Package Information](../package-management/r-package-information.md).

    ```R
    pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);
    makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.3");
    ```

   Aus diesen Informationen erstellt das minicran-Paket die Ordnerstruktur, die Sie benötigen, um die Pakete zu [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] einem späteren Zeitpunkt zu kopieren.

An diesem Punkt sollten Sie über einen Ordner mit den benötigten Paketen und zusätzlichen erforderlichen Paketen verfügen. Der Ordner sollte eine Auflistung gezippte Pakete enthalten. Entpacken Sie die Pakete nicht, oder benennen Sie keine Dateien um.

Führen Sie optional den folgenden Code aus, um die Pakete aufzulisten, die im lokalen minicran-Repository enthalten sind.

```R
pdb <- as.data.frame(pkgAvail(local_repo, type = "win.binary", Rversion = "3.3"), stringsAsFactors = FALSE);
head(pdb);
pdb$Package;
pdb[, c("Package", "Version", "License")]
```

## <a name="add-packages-to-the-instance-library"></a>Hinzufügen von Paketen zur instanzbibliothek

Nachdem Sie über ein lokales Repository mit den Paketen verfügen, die Sie benötigen, verschieben Sie das Paketrepository auf den SQL Server Computer. Im folgenden Verfahren wird beschrieben, wie Sie die Pakete mithilfe von R Tools installieren.

1. Kopieren Sie den Ordner, der das minicran-Repository enthält, vollständig auf den Server, auf dem die Pakete installiert werden sollen. Der Ordner weist in der Regel die folgende Struktur auf: 

   `<miniCRAN root>/bin/windows/contrib/version/<all packages>`

   In diesem Verfahren wird davon ausgegangen, dass es sich um einen Ordner vom Stamm Laufwerk handelt.

2. Öffnen Sie ein R-Tool, das mit der Instanz verknüpft ist (z. b. können Sie "rgui. exe" verwenden). Klicken Sie mit der rechten Maustaste, und wählen Sie **als Administrator ausführen** aus, damit das Tool Updates an Ihrem System vornehmen kann.

   ::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
   - Der Standard Speicherort für die rgui lautet `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`beispielsweise.
   ::: moniker-end

   ::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
   - Der Speicherort für die rgui lautet `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`beispielsweise.
   ::: moniker-end

   ::: moniker range=">sql-server-2017||=sqlallproducts-allversions"
   - Der Speicherort für die rgui lautet `C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\R_SERVICES\bin\x64`beispielsweise.
   ::: moniker-end

3. Den Pfad für die instanzbibliothek erhalten und der Liste der Bibliothekspfade hinzufügen.

   ::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
   Ein auf ein Objekt angewendeter

   ```R
   outputlib <- "C:/Program Files/Microsoft SQL Server/MSSQL13.MSSQLSERVER/R_SERVICES/library"
   ```

   ::: moniker-end

   ::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
   Ein auf ein Objekt angewendeter

   ```R
   outputlib <- "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library"
   ```

   ::: moniker-end

   ::: moniker range=">sql-server-2017||=sqlallproducts-allversions"
   Ein auf ein Objekt angewendeter

   ```R
   outputlib <- "C:/Program Files/Microsoft SQL Server/MSSQL15.MSSQLSERVER/R_SERVICES/library"
   ```

   ::: moniker-end

4. Geben Sie den neuen Speicherort auf dem Server an, auf den Sie das **minicran** -Repository `server_repo`kopiert haben.

    In diesem Beispiel wird davon ausgegangen, dass Sie das Repository in einen temporären Ordner auf dem Server kopiert haben.

    ```R
    inputlib <- "C:/miniCRANZooPackages"
    ```

5. Da Sie in einem neuen R-Arbeitsbereich auf dem Server arbeiten, müssen Sie auch die Liste der zu installierenden Pakete bereitstellen.

    ```R
    mypackages <- c("zoo", "forecast")
    ```

6. Installieren Sie die Pakete, und geben Sie den Pfad zur lokalen Kopie des minicran-Repository an.

    ```R
    install.packages(mypackages, repos = file.path("file://", normalizePath(inputlib, winslash = "/")), lib = outputlib, type = "win.binary", dependencies = TRUE);
    ```

7. In der instanzbibliothek können Sie die installierten Pakete mit einem Befehl wie dem folgenden anzeigen:

    ```R
    installed.packages()
    ```

## <a name="see-also"></a>Siehe auch

+ [R-Paketinformationen erhalten](../package-management/r-package-information.md)
+ [R-Tutorials](../tutorials/sql-server-r-tutorials.md)
