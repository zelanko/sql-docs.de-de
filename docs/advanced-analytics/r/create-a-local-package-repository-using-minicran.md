---
title: Erstellen eines lokalen R-paketrepositorys mit minicran
description: Verwenden Sie minicran zum erkennen, zusammenstellen und Installieren von R-Paketabhängigkeiten in einem einzelnen konsolidierten Paket.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a2324ad662cad2c91bc6e002fd652fed73d8ab3d
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715763"
---
# <a name="create-a-local-r-package-repository-using-minicran"></a>Erstellen eines lokalen R-paketrepositorys mit minicran
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Das [minicran](https://cran.r-project.org/web/packages/miniCRAN/index.html) -Paket, das von [Andre de Vries](https://blog.revolutionanalytics.com/2016/05/minicran-sql-server.html)erstellt wurde, identifiziert Pakete und Abhängigkeiten in einem einzelnen Ordner, den Sie für die Offline Installation von R-Paketen auf andere Computer kopieren können.

Geben Sie als Eingabe mindestens ein Paket an. der **minicran** liest die Abhängigkeitsstruktur für diese Pakete rekursiv und lädt nur die aufgelisteten Pakete und ihre Abhängigkeiten von CRAN oder ähnlichen Depots herunter.

Als Ausgabe erstellt **minicran** ein intern konsistentes Repository, das aus den ausgewählten Paketen und allen erforderlichen Abhängigkeiten besteht. Anschließend können Sie dieses lokale Repository auf den Server verschieben und mit der Installation der Pakete ohne Internetverbindung fortfahren.

> [!NOTE]
> Erfahrene R-Benutzer suchen häufig nach der Liste der abhängigen Pakete in der Beschreibungsdatei für das heruntergeladene Paket. In **Imports** aufgelistete Pakete verfügen jedoch möglicherweise über Abhängigkeiten auf zweiter Ebene. Aus diesem Grund empfiehlt es sich, **minicran** für die Assemblierung der vollständigen Sammlung erforderlicher Pakete zu erhalten.

## <a name="why-create-a-local-repository"></a>Gründe für das Erstellen eines lokalen Repository

Das Ziel der Erstellung eines lokalen paketrepositorys besteht darin, einen einzelnen Speicherort bereitzustellen, der von einem Server Administrator oder anderen Benutzern in der Organisation verwendet werden kann, um neue R-Pakete auf einem Server zu installieren, insbesondere einen, der nicht über Internet Zugriff verfügt. Nachdem Sie das Repository erstellt haben, können Sie es ändern, indem Sie neue Pakete hinzufügen oder die Version vorhandener Pakete aktualisieren.

Paketrepositorys sind in folgenden Szenarien nützlich:

- **Sicherheit**: Viele r-Benutzer sind daran gewöhnt, neue r-Pakete auf der Grundlage von CRAN oder einer ihrer Spiegel Sites herunterzuladen und zu installieren. Aus Sicherheitsgründen verfügen Produktionsserver, auf denen [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ausgeführt wird, jedoch in der Regel nicht über Internet Konnektivität.

- **Einfachere Offline Installation**: Wenn Sie das Paket auf einem Offline Server installieren möchten, müssen Sie auch alle Paketabhängigkeiten herunterladen. mit minicran ist es einfacher, alle Abhängigkeiten im richtigen Format abzurufen.

    Durch die Verwendung von minicran können Sie Paket Abhängigkeitsfehler vermeiden, wenn Sie Pakete für die Installation mit der [Create externe Library](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) -Anweisung vorbereiten.

- **Verbesserte Versionsverwaltung**: In einer mehr Benutzerumgebung gibt es gute Gründe, eine uneingeschränkte Installation mehrerer Paketversionen auf dem Server zu vermeiden. Verwenden Sie ein lokales Repository, um einen konsistenten Satz von Paketen bereitzustellen, die von den Analysten verwendet werden können. 

> [!TIP]
> Sie können minicran auch verwenden, um Pakete für die Verwendung in Azure Machine Learning vorzubereiten. Weitere Informationen finden Sie in diesem Blog: [Verwenden von minicran in Azure ml von Michele usuelli](https://www.r-bloggers.com/using-minicran-in-azure-ml/) 

## <a name="install-minicran"></a>Installieren von minicran

Das **minicran** -Paket selbst ist von 18 anderen cran-Paketen abhängig. dabei handelt es sich um das **rcurl** -Paket, das eine System Abhängigkeit vom **curl-devel-** Paket aufweist. Ebenso hat Paket- **XML** eine Abhängigkeit von **libxml2-devel**. Um Abhängigkeiten aufzulösen, empfiehlt es sich, das lokale Repository zunächst auf einem Computer zu erstellen, der über Vollzugriff auf das Internet verfügt. 

Führen Sie die folgenden Befehle auf einem Computer mit Basis-r, r-Tools und Internetverbindung aus. Es wird davon ausgegangen, dass es sich hierbei *nicht* um Ihren SQL Server Computer handelt. Mit den folgenden Befehlen werden das **minicran** -Paket und das erforderliche **igraph** -Paket installiert. In diesem Beispiel wird überprüft, ob das Paket bereits installiert ist, aber Sie können die if-Anweisungen umgehen und die Pakete direkt installieren.

```R
if(!require("miniCRAN")) install.packages("miniCRAN") 
if(!require("igraph")) install.packages("igraph") 
library("miniCRAN")
```

## <a name="set-the-cran-mirror-and-mran-snapshot"></a>Festlegen des cran-Spiegels und der mran-Momentaufnahme

Geben Sie eine Spiegel Website an, die zum erhalten von Paketen verwendet wird. Beispielsweise können Sie die mran-Website oder eine beliebige andere Website in Ihrer Region verwenden, die die benötigten Pakete enthält. Wenn der Download fehlschlägt, probieren Sie eine andere Spiegel Website aus.

```R
CRAN_mirror <- c(CRAN = "https://mran.microsoft.com")
CRAN_mirror <- c(CRAN = "https://cran.cnr.berkeley.edu")
```

## <a name="create-a-local-folder"></a>Erstellen eines lokalen Ordners

Erstellen Sie einen lokalen Ordner, z `C:\mylocalrepo` . b. zum Speichern der gesammelten Pakete. Wenn Sie dies häufig wiederholen, sollten Sie einen aussagekräftigeren Namen, z. b. "minicranzoomopackages" oder "miniCRANMyRPackagev2", verwenden.

Geben Sie den Ordner als lokales Repository an. Die R-Syntax verwendet einen Schrägstrich für Pfadnamen, der gegen Windows-Konventionen steht.

```R
local_repo <- "C:/mylocalrepo"
```

## <a name="add-packages-to-the-local-repo"></a>Hinzufügen von Paketen zum lokalen Repository

Nachdem **minicran** installiert und geladen wurde, erstellen Sie eine Liste, in der die zusätzlichen Pakete angegeben sind, die Sie herunterladen möchten.

Fügen Sie dieser anfangs Liste **keine** Abhängigkeiten hinzu. Das **igraph** -Paket, das von **minicran** verwendet wird, generiert die Liste der Abhängigkeiten für Sie. Weitere Informationen zur Verwendung des generierten Abhängigkeits Diagramms finden Sie unter [Verwenden von minicran zur Identifizierung von Paketabhängigkeiten](https://cran.r-project.org/web/packages/miniCRAN/vignettes/miniCRAN-dependency-graph.html).

1. Hinzufügen von Ziel Paketen, "Zoo" und "Vorhersage" zu einer Variablen.

    ```R
    pkgs_needed <- c("zoo", "forecast")
    ```

2. Optional können Sie das Abhängigkeits Diagramm zeichnen, aber es kann informativ sein.
    
    ```R
    plot(makeDepGraph(pkgs_needed))
    ```

3. Erstellen Sie das lokale Repository. Stellen Sie sicher, dass Sie ggf. die R-Version in die Version ändern, die auf der SQL Server Instanz installiert ist Version 3.2.2 ist auf SQL Server 2016, Version 3,3, auf SQL Server 2017. Wenn Sie ein Komponenten Upgrade durchgeführt haben, kann die Version neuer sein. Weitere Informationen finden Sie unter [Informationen zu R-und Python-Paketen](../package-management/installed-package-information.md).

    ```R
    pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);
    makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.3");
    ```

   Aus diesen Informationen erstellt das minicran-Paket die Ordnerstruktur, die Sie benötigen, um die Pakete zu [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] einem späteren Zeitpunkt zu kopieren.

An diesem Punkt sollten Sie über einen Ordner verfügen, der die benötigten Pakete enthält, sowie alle zusätzlich erforderlichen Pakete. Der Pfad sollte in etwa wie im folgenden Beispiel aussehen: C:\mylocalrepo\bin\windows\contrib\3.3 und sollte eine Sammlung von ZIP-Paketen enthalten. Entpacken Sie die Pakete nicht, oder benennen Sie keine Dateien um.

Führen Sie optional den folgenden Code aus, um die Pakete aufzulisten, die im lokalen minicran-Repository enthalten sind.

```R
pdb <- as.data.frame(pkgAvail(local_repo, type = "win.binary", Rversion = "3.3"), stringsAsFactors = FALSE);
head(pdb);
pdb$Package;
pdb[, c("Package", "Version", "License")]
```

## <a name="add-packages-to-the-instance-library"></a>Hinzufügen von Paketen zur instanzbibliothek

Nachdem Sie über ein lokales Repository mit den Paketen verfügen, die Sie benötigen, verschieben Sie das Paketrepository auf den SQL Server Computer. Im folgenden Verfahren wird beschrieben, wie Sie die Pakete mithilfe von R Tools installieren.

1. Kopieren Sie den Ordner, der das minicran-Repository enthält, vollständig auf den Server, auf dem die Pakete installiert werden sollen. Der Ordner weist in der Regel die folgende Struktur auf: minicran root > bin > Windows > contrib > Version > Alle Pakete. In den folgenden Beispielen wird davon ausgegangen, dass es sich um einen Ordner vom Stamm Laufwerk handelt: 

2. Öffnen Sie ein R-Tool, das mit der Instanz verknüpft ist (z. b. können Sie "rgui. exe" verwenden). Klicken Sie mit der rechten Maustaste auf **als Administrator ausführen** , damit das Tool Updates an Ihrem System vornehmen kann.

    - Bei SQL Server 2017 lautet `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`der Speicherort für die rgui.

    - Bei SQL Server 2016 lautet `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`der Speicherort für die rgui.

3. Den Pfad für die instanzbibliothek erhalten und der Liste der Bibliothekspfade hinzufügen. Auf SQL Server 2017 ähnelt der Pfad dem folgenden Beispiel.

    ```R
    outputlib <- "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library"
    ```

4. Geben Sie den neuen Speicherort auf dem Server an, auf den Sie das **minicran** -Repository kopiert haben `server_repo`.

    In diesem Beispiel wird davon ausgegangen, dass Sie das Repository in einen temporären Ordner auf dem Server kopiert haben.

    ```R
    inputlib <- "C:/temp/mylocalrepo"
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

+ [Paketinformationen abrufen](../package-management/installed-package-information.md)
+ [R-Tutorials](../tutorials/sql-server-r-tutorials.md)
