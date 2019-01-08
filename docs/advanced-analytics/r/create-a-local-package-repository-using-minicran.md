---
title: Erstellen eines lokalen R-paketrepositorys mit MiniCRAN - SQL Server Machine Learning Services
description: Können Sie erkennen, assemblieren und Installieren von R-paketabhängigkeiten in einem einzelnen konsolidierten Paket MiniCran zu.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/29/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 7dc2e286e6eb80fe1eef3e8b86ed1002a6344cfb
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2018
ms.locfileid: "53431753"
---
# <a name="create-a-local-r-package-repository-using-minicran"></a>Erstellen Sie eine lokale R-paketrepositorys mit miniCRAN
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[MiniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html) vom erstellte Paket [Andre de Vries](https://blog.revolutionanalytics.com/2016/05/minicran-sql-server.html), identifiziert und downloads, Pakete und Abhängigkeiten in einem Ordner, die Sie mit anderen Computern für eine Offlineinstallation von R-Paket kopieren können.

Geben Sie als Eingabe ein oder mehrere Pakete. **MiniCRAN** rekursiv liest die Abhängigkeitsstruktur für diese Pakete und lädt nur die aufgelisteten Pakete und ihre Abhängigkeiten über CRAN oder ähnliche Repositorys.

Als Ausgabe **MiniCRAN** ein intern konsistent Repository bestehend aus der ausgewählten Pakete und alle erforderlichen Abhängigkeiten erstellt. Sie können dann Verschieben dieses lokale Repository auf den Server, und führen die Pakete ohne Internetverbindung zu installieren.

> [!NOTE]
> Erfahrene R-Benutzer suchen häufig nach der Liste der abhängigen Pakete in der DESCRIPTION-Datei für das heruntergeladene Paket verwendet werden. Allerdings Pakete aufgeführt, **Importe** möglicherweise zweiten Ebene Abhängigkeiten. Aus diesem Grund empfehlen wir **MiniCRAN** für das Zusammenstellen der vollständigen Sammlung der erforderlichen Pakete.

## <a name="why-create-a-local-repository"></a>Warum Erstellen eines lokalen Repositorys

Das Ziel der Erstellung eines lokalen paketrepositorys ist an einem zentralen Ort zu erhalten, ein Serveradministrator oder andere Benutzer in der Organisation verwenden können, um neue R-Pakete auf einem Server, insbesondere wenn er zu installieren, die keinen Zugriff auf das Internet. Nach dem Erstellen des Repositorys können Sie es ändern, indem neue Pakete hinzufügen oder Aktualisieren der Version der vorhandenen Pakete.

Package-Repositorys sind in diesen Szenarien nützlich:

- **Sicherheit**: Viele R-Benutzer sind es gewöhnt, zum Herunterladen und Installieren neuer R-Pakete werden von CRAN oder einer der gespiegelten Sites. Jedoch aus Sicherheitsgründen Produktionsservern ausgeführt [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] haben für gewöhnlich keine Internetverbindung.

- **Einfacher offline-Installation**: Zum Installieren des Pakets mit einem offline-Server erfordert, dass Sie auch alle paketabhängigkeiten herunterladen Using MiniCRAN erleichtert es, alle Abhängigkeiten im richtigen Format zu erhalten.

    Sie können mithilfe der MiniCRAN Paket abhängigkeitsfehler vermeiden, bei der Vorbereitung der Pakete für die Installation mit der [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) Anweisung.

- **Verbesserte versionsverwaltung**: In einer mehrbenutzerumgebung gibt es gute Gründe für die uneingeschränkte Installation von mehreren Versionen des Pakets auf dem Server zu vermeiden. Verwenden Sie ein lokales Repository, um einen konsistenten Satz von Paketen für die Verwendung durch Ihre Analytiker bereitzustellen. 

> [!TIP]
> Sie können auch MiniCRAN verwenden, um Pakete für die Verwendung in Azure Machine Learning vorbereiten. Weitere Informationen finden Sie in diesem Blog: [Verwenden in Azure ML von Michele Usuelli miniCRAN](https://www.r-bloggers.com/using-minicran-in-azure-ml/) 

## <a name="install-minicran"></a>Installieren von miniCRAN

Die **MiniCRAN** Paket selbst ist abhängig von 18 CRAN-Paketen für die die **RCurl** -Paket, das System abhängig ist auf die **Curl-Entwickler** Paket. Auf ähnliche Weise Paket **XML** weist eine Abhängigkeit **libxml2-entwickl**. Um Abhängigkeiten zu beheben, empfehlen wir, dass Sie Ihr lokale Repository zunächst auf einem Computer mit vollständigen Zugriff auf das Internet zu erstellen. 

Führen die folgenden Befehle auf einem Computer mit einer Basis-R, R-Tools und dem Internet verbunden. Es wird angenommen, dies ist *nicht* SQL Server-Computers. Die folgenden Befehle installieren die **MiniCRAN** Paket und die erforderlichen **Igraph** Paket. In diesem Beispiel wird überprüft, ob das Paket bereits installiert ist, jedoch können Sie umgehen, die bei Anweisungen, und installieren Sie die Pakete direkt.

```R
if(!require("miniCRAN")) install.packages("miniCRAN") 
if(!require("igraph")) install.packages("igraph") 
library("miniCRAN")
```

## <a name="set-the-cran-mirror-and-mran-snapshot"></a>Legen Sie die CRAN-Spiegel und MRAN-Momentaufnahme

Geben Sie eine gespiegelte Site beim Abrufen der Pakete verwenden. Z. B. können die MRAN-Website oder einen anderen Standort in Ihrer Region Sie, die die Pakete enthält, die Sie benötigen. Wenn der Download fehlschlägt, versuchen Sie eine andere gespiegelte Site aus.

```R
CRAN_mirror <- c(CRAN = "https://mran.microsoft.com")
CRAN_mirror <- c(CRAN = "https://cran.cnr.berkeley.edu")
```

## <a name="create-a-local-folder"></a>Erstellen Sie einen lokalen Ordner

Erstellen Sie einen lokalen Ordner, z. B. `C:\mylocalrepo` in dem Sie die gesammelten Pakete zu speichern. Wenn Sie dies oft wiederholen, sollten Sie wahrscheinlich einen aussagekräftigeren Namen, z. B. "MiniCRANZooPackages" oder "miniCRANMyRPackagev2" verwenden.

Geben Sie den Ordner, wie das lokale Repository. R-Syntax verwendet, einen Schrägstrich für Pfadnamen, die entgegengesetzten wird von Windows-Konventionen.

```R
local_repo <- "C:/mylocalrepo"
```

## <a name="add-packages-to-the-local-repo"></a>Hinzufügen von Paketen zum lokalen Repository

Nach dem **MiniCRAN** wird installiert und geladen, erstellen Sie eine Liste, der angibt, die zusätzlichen Pakete herunterladen möchten.

Führen Sie **nicht** Abhängigkeiten zu dieser anfänglichen Liste hinzufügen. Die **Igraph** Paket ein, die **MiniCRAN** generiert die Liste der Abhängigkeiten für Sie. Weitere Informationen zur Verwendung des generierten Abhängigkeitsdiagramms finden Sie unter [mit MiniCRAN zum Identifizieren von paketabhängigkeiten](https://cran.r-project.org/web/packages/miniCRAN/vignettes/miniCRAN-dependency-graph.html).

1. Fügen Sie die Zielpakete, "Zoo" und "Prognose", um eine Variable hinzu.

    ```R
    pkgs_needed <- c("zoo", "forecast")
    ```

2. Zeichnen das Abhängigkeitsdiagramm optional, jedoch kann es informativ sein.
    
    ```R
    plot(makeDepGraph(pkgs_needed))
    ```

3. Erstellen Sie das lokale Repository. Achten Sie darauf, dass die R-Version, die auf Ihrer SQL Server-Instanz installierte Version ggf. geändert werden. Version 3.2.2 ist auf SQL Server 2016, Version 3.3 ist auf SQL Server 2017. Wenn Sie eine Komponentenupgrade ausgeführt haben, kann Ihre Version höher sein. Weitere Informationen finden Sie unter [erhalten R- und Python-Paketinformationen](determine-which-packages-are-installed-on-sql-server.md).

    ```R
    pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);
    makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.3");
    ```

   Anhand dieser Informationen erstellt das MiniCRAN-Paket die Ordnerstruktur, die Sie benötigen, kopieren Sie die Pakete für die [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] später noch mal.

An diesem Punkt müssen Sie einen Ordner, in dem Sie die benötigten Pakete, und alle zusätzlichen Pakete, die erforderlich waren. Der Pfad sollte etwa wie folgt lauten: C:\mylocalrepo\bin\windows\contrib\3.3 und es sollte eine Auflistung von komprimierten Paketen enthalten. Entzippen Sie die Pakete nicht, und benennen Sie alle Dateien.

Führen Sie optional den folgenden Code zum Auflisten der Pakete in das lokale MiniCRAN-Repository enthalten sind.

```R
pdb <- as.data.frame(pkgAvail(local_repo, type = "win.binary", Rversion = "3.3"), stringsAsFactors = FALSE);
head(pdb);
pdb$Package;
pdb[, c("Package", "Version", "License")]
```

## <a name="add-packages-to-the-instance-library"></a>Hinzufügen von Paketen in der Instanz-Bibliothek

Nachdem Sie ein lokales Repository mit den Paketen, die Sie benötigen haben, verschieben Sie den paketrepository auf den SQL Server-Computer. Das folgende Verfahren beschreibt die Pakete, die mit R-Tools zu installieren.

1. Kopieren Sie den Ordner mit der MiniCRAN-Repository, in seiner Gesamtheit und an den Server, in dem Sie die Pakete installieren möchten. Der Ordner in der Regel weist die folgende Struktur: MiniCRAN-Stamm > "bin" > Windows > Contrib > Version > alle Pakete. In den folgenden Beispielen wird davon ausgegangen einen Ordner aus dem Stammlaufwerk: 

2. Öffnen Sie ein R-Tool, mit der Instanz verknüpft ist (z. B. können Rgui.exe). Mit der rechten Maustaste **als Administrator ausführen** um das Tool zum Erstellen von Updates auf Ihr System zu ermöglichen.

    - Für SQL Server 2017 wird der Dateispeicherort für RGUI `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`.

    - Für SQL Server 2016, He-Dateispeicherort für RGUI ist `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`.

3. Rufen Sie den Pfad für die Instanz-Bibliothek, und fügen Sie es der Liste der Library-Pfade hinzu. Auf SQL Server 2017 ist der Pfad im folgenden Beispiel ähnelt.

    ```R
    outputlib <- "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library"
    ```

4. Geben Sie den neuen Speicherort auf dem Server, in denen Sie kopiert, die **MiniCRAN** -Repository als `server_repo`.

    In diesem Beispiel wird davon ausgegangen, dass Sie das Repository in einen temporären Ordner auf dem Server kopiert haben.

    ```R
    inputlib <- "C:/temp/mylocalrepo"
    ```

5. Da Sie in einem neuen R-Arbeitsbereich auf dem Server arbeiten, müssen Sie auch die Liste der zu installierenden Paketen Dokumentationselement.

    ```R
    mypackages <- c("zoo", "forecast")
    ```

6. Installieren Sie die Pakete, die den Pfad zu der lokalen Kopie der MiniCRAN-Repository bereitgestellt.

    ```R
    install.packages(mypackages, repos = file.path("file://", normalizePath(inputlib, winslash = "/")), lib = outputlib, type = "win.binary", dependencies = TRUE);
    ```

7. Aus der Bibliothek Instanz können Sie die installierten Pakete, die mit einem Befehl wie folgt anzeigen:

    ```R
    installed.packages()
    ```

## <a name="see-also"></a>Siehe auch

+ [Paketinformationen abrufen](determine-which-packages-are-installed-on-sql-server.md)
+ [R-tutorials](../tutorials/sql-server-r-tutorials.md)
+ [Anleitungen](sql-server-machine-learning-tasks.md)


