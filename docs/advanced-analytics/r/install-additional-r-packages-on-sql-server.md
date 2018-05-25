---
title: Installieren Sie neue R-Pakete auf SQL Server-Machine Learning-Services | Microsoft Docs
description: Hinzufügen von neuen R-Pakete auf SQL Server 2016 R Services oder SQL Server 2017 Machine Learning Services (Datenbankintern)
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/10/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 20ef7181c5ab8c0494f73b205dddcdf1ac0a620e
ms.sourcegitcommit: b5ab9f3a55800b0ccd7e16997f4cd6184b4995f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2018
---
# <a name="install-new-r-packages-on-sql-server"></a>Installieren Sie neue R-Pakete unter SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel beschreibt, wie neue R-Pakete mit einer Instanz von SQL Server installieren, Machine Learning aktiviert ist. Es gibt mehrere Methoden für die Installation von neuen R-Pakete, je nach von Ihnen installierten Version von SQL Server, und gibt an, ob der Server über eine Internetverbindung verfügt. Die folgenden Ansätze für die Neuinstallation des Pakets sind möglich.

| Vorgehensweise                           | Berechtigungen  | Remote/Local |
|------------------------------------|---------------------------|-------|
| [Verwenden Sie herkömmliche R-Paket-Manager](#bkmk_rInstall)  | Admin | Lokal |
| [Verwenden von RevoScaleR](use-revoscaler-to-manage-r-packages.md) | Admin | Lokal |
| [Verwenden von T-SQL (externe Bibliothek erstellen)](install-r-packages-tsql.md) | Administratorrechte verfügen, um Setup danach Datenbankrollen | both 
| [Verwenden Sie eine MiniCRAN, um ein lokales Repository erstellt werden.](create-a-local-package-repository-using-minicran.md) | Administratorrechte verfügen, um Setup danach Datenbankrollen | both |

## <a name="bkmk_rInstall"></a> Installieren von R-Pakete über eine Internetverbindung

Können Sie R-Standardtools um neue Pakete auf einer Instanz von SQL Server 2016 zu installieren oder SQL Server 2017 Bereitstellen des Computers verfügt über einen geöffneten Port 80, und Sie über Administratorrechte verfügen.

> [!IMPORTANT] 
> Achten Sie darauf, dass Pakete in der Standardbibliothek installieren, die der aktuellen Instanz zugeordnet ist. Installieren Sie Pakete niemals ein Verzeichnis des Benutzers.

Dieses Verfahren verwendet, "rgui.exe", jedoch können Sie RTerm oder eine beliebige andere R Befehlszeilentool, die mit erhöhten Rechten Datenzugriff unterstützt.

### <a name="install-a-package-using-rgui"></a>Installieren eines Pakets mithilfe von "rgui.exe"

1. [Bestimmen Sie den Speicherort der Bibliothek Instanz](installing-and-managing-r-packages.md). Navigieren Sie zu dem Ordner, in dem die R-Tools installiert sind. Beispielsweise lautet der Standardpfad für eine Standardinstanz von SQL Server-2017 wie folgt ein: `C:\Program Files\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`

1. RGui.exe Maustaste, und wählen **als Administrator ausführen**. Wenn Sie nicht über die erforderlichen Berechtigungen verfügen, wenden Sie sich an den Datenbankadministrator, und geben Sie eine Liste der Pakete, die Sie benötigen.

1. Über die Befehlszeile, wenn Sie wissen, dass der Paketname können Sie eingeben: `install.packages("the_package-name")` doppelte Anführungszeichen für den Paketnamen erforderlich sind.

1. Wenn Sie nach einer gespiegelten Site gefragt werden, wählen Sie einen Standort, der für Ihren Standort zweckmäßig ist.

Wenn das Zielpaket von weiteren Paketen abhängig ist, die R-Installationsprogramm automatisch die Abhängigkeiten für herunter und installiert sie Sie.

Wenn Sie mehrere Instanzen von SQL Server, z. B. Seite-an-Seite-Instanzen von SQL Server 2016 R Services und SQL Server 2017 Machine Learning Services haben führen Sie Installation separat für jede Instanz, wenn Sie das Paket in beiden Kontexten verwenden möchten. Pakete können nicht über Instanzen freigegeben werden.

## <a name = "bkmk_offlineInstall"></a> Offline-Installation mithilfe von R-tools

Wenn der Server nicht über Internetzugriff verfügt, sind zusätzliche Schritte erforderlich, um die Pakete vorzubereiten. Um die R-Pakete auf einem Server installieren, die nicht über Internetzugriff verfügt, müssen Sie folgende Aktionen ausführen:

+ Analysieren Sie die Abhängigkeiten im voraus.
+ Das Zielpaket auf einem Computer mit Internetzugriff herunterladen.
+ Herunterladen Sie alle erforderlichen Pakete auf dem gleichen Computer, und fügen Sie alle Pakete in ein einzelnes Paket-Archiv.
+ ZIP-Archiv, ist er nicht bereits im ZIP-Format.
+ Kopieren Sie das Archiv Paket an einen Speicherort auf dem Server.
+ Installieren Sie das Zielpaket, das die Archivdatei als Quelle angeben.

> [!IMPORTANT] 
> > Achten Sie darauf, dass Sie alle Abhängigkeiten analysieren und herunterladen **alle** benötigte Pakete **vor** mit der Installation beginnen. Wir empfehlen [MiniCRAN](https://mran.microsoft.com/package/miniCRAN) für diesen Prozess. Diese R-Paket kann es sich um eine Liste der Pakete, die Sie installieren möchten, Abhängigkeiten analysiert und ruft die ZIP-Dateien für Sie. MiniCRAN erstellt dann ein einzelnes Repository, das Sie in Server-Computer kopieren können.
> 
> Weitere Informationen finden Sie unter [erstellen Sie ein lokales Paket-Repository mit MiniCRAN](create-a-local-package-repository-using-minicran.md)

Dieses Verfahren setzt voraus, dass Sie alle Pakete vorbereitet haben, im ZIP-Format müssen und sind bereit, die sie auf den Server kopiert.

1. Kopieren Sie das Paket ZIP-Datei, oder für mehrere Pakete vollständige Repository, enthält alle Pakete im ZIP-Format an einen Speicherort, den auf der Server zugreifen kann.

2. Öffnen Sie den Ordner auf dem Server, auf dem die R-Tools für die Instanz installiert werden. Wenn Sie die Windows-Eingabeaufforderung auf einem System mit SQL Server 2016-R-Services verwenden, z. B. Wechseln Sie zur `C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`.

3. Mit der rechten Maustaste auf "rgui.exe" oder RTerm und wählen Sie **als Administrator ausführen**.

4. Führen Sie den Befehl R `install.packages` , und geben Sie das Paket oder Namen und den Speicherort der ZIP-Dateien.

    ```R
    install.packages("C:\\Temp\\Downloaded packages\\mynewpackage.zip", repos=NULL)
    ```

    Dieser Befehl extrahiert das R-Paket `mynewpackage` aus der lokalen ZIP-Datei, sofern Sie die Kopie im Verzeichnis gespeichert ist `C:\Temp\Downloaded packages`, und das Paket auf dem lokalen Computer installiert. Wenn das Paket keine Abhängigkeiten enthält, überprüft das Installationsprogramm für vorhandene Pakete in der Bibliothek. Wenn Sie ein Repository, die die Abhängigkeiten enthält erstellt haben, installiert das Installationsprogramm die erforderlichen Pakete auch an.

    Wenn alle erforderlichen Pakete in der Bibliothek für die Instanz nicht vorhanden sind und können nicht in die ZIP-Dateien gefunden werden, schlägt fehl, die Installation des Ziel-Pakets.

## <a name="tips-for-package-installation"></a>Tipps für die Paketinstallation

Dieser Abschnitt enthält verschiedene Tipps und häufig gestellte Fragen im Zusammenhang mit der Installation von R-Paket für SQL Server.

###  <a name="packageVersion"></a> Rufen Sie die richtige Paketversion und format

Es gibt mehrere Quellen für R-Pakete, z. B. CRAN und Bioconductor. Die offizielle Website für die Sprache "R" (<https://www.r-project.org/>) sind viele dieser Ressourcen aufgeführt. Viele Pakete werden in GitHub veröffentlicht, in dem Sie den Quellcode erhalten können. Schließlich, Sie können R-Pakete, die von einer Person in Ihrem Unternehmen entwickelt wurden angegeben wurde, oder Sie haben ein benutzerdefiniertes Paket an dem von das Ihnen geschriebenen.

Stellen Sie unabhängig von der Quelle bevor Sie versuchen, die zum Installieren des Pakets sicher, dass Sie mit das binary-Format für die Windows-Plattform erhalten haben. 

### <a name="bkmk_zipPreparation"></a> Das Paket als ZIP-Datei herunterladen

Für die Installation auf einem Server ohne Internetzugriff müssen Sie eine Kopie des Pakets in das Format einer ZIP-Datei für die Offlineinstallation herunterladen. **Entzippen Sie das Paket nicht.**

Z. B. das folgende Verfahren beschreibt jetzt, um die richtige Version von den [FISHalyseR](http://bioconductor.org/packages/release/bioc/html/FISHalyseR.html) Paket von Bioconductor, vorausgesetzt, der Computer über Internetzugriff verfügt.

1.  Suchen Sie in der Liste der **Paketarchive** die **Windows-Binärdateiversion** .

2.  Mit der rechten Maustaste des Links, um die. ZIP-Datei, und wählen **Ziel speichern unter**.

3.  Navigieren Sie zu den lokalen Ordner, in dem komprimierten Pakete gespeichert sind, und klicken Sie auf **speichern**.

    Dieser Vorgang erstellt eine lokale Kopie des Pakets. 

4. Wenn Sie einen Download-Fehler erhalten, versuchen Sie eine andere gespiegelte Site aus.

5. Nachdem das Archiv Paket heruntergeladen wurde, können Sie installieren Sie das Paket oder kopieren das ZIP-Paket auf einen Server, die über keinen Zugriff auf das Internet.

> [!TIP]
> Wenn versehentlich des Pakets installieren anstelle eines Downloads von Binärdateien wird eine Kopie der heruntergeladene ZIP-Datei auch auf Ihrem Computer gespeichert. Beobachten Sie die statusmeldungen aus, während das Paket installiert wird, um den Dateispeicherort zu bestimmen. Sie können diese ZIP-Datei an den Server kopieren, die über keinen Zugriff auf das Internet.
> 
> Wenn Sie Pakete, die mit dieser Methode abgerufen haben, sind die Abhängigkeiten nicht enthalten. 

### <a name="bkmk_packageDependencies"></a> Abrufen der erforderlichen Pakete

R-Pakete hängen häufig mehrere andere Pakete, von die einige möglicherweise nicht verfügbar in der Standardeinstellung R-Bibliothek, die von der Instanz verwendet. In einigen Fällen erfordert ein Paket eine andere Version von ein abhängiges Paket, das bereits installiert ist.

Wenn Sie müssen zum Installieren mehrerer Pakete, oder möchten, stellen Sie sicher, dass jeder einzelne in Ihrem Unternehmen die richtigen Pakettyp und Version erhält, wir empfehlen die Verwendung der [MiniCRAN](https://mran.microsoft.com/package/miniCRAN) Paket, um die vollständige Abhängigkeitskette zu analysieren. MinicRAN erstellt ein lokales Repository, das für mehrere Benutzer oder Computer freigegeben werden kann. Weitere Informationen finden Sie unter [erstellen Sie ein lokales Paket-Repository mit MiniCRAN](create-a-local-package-repository-using-minicran.md).


### <a name="know-which-library-you-are-installing-to-and-which-packages-are-already-installed"></a>Wissen, welche Bibliothek, die Sie zum Installieren und die Pakete sind bereits installiert.

Wenn Sie vor der Installation von alles zuvor die R-Umgebung auf dem Computer geändert haben, halten Sie einen Moment, und stellen Sie sicher, dass die R-Umgebungsvariable `.libPath` nur ein Pfad verwendet.

Dieser Pfad sollte auf den Ordner R_SERVICES für die Instanz verweisen. Weitere Informationen, einschließlich Informationen zum bestimmen, welche Pakete bereits installiert sind, finden Sie unter [R-Pakete, die mit SQL Server installierten](installing-and-managing-r-packages.md).

### <a name="side-by-side-installation-with-standalone-r-or-python-servers"></a>Seite-an-Seite-Installation mit Standalone R oder Python-Servern

Wenn Sie SQL Server 2017 Microsoft Machine Learning-Server (eigenständig) oder SQL Server 2016 R Server (eigenständig) zusätzlich zu den in der Datenbank Analytics (SQL Server 2017 Machine Learning Services und SQL Server 2016 R Services) installiert haben, sind für Ihren computer Installationen von R für die einzelnen Duplikate aller R-Tools und Bibliotheken zu trennen.

Pakete, die in der Bibliothek R_SERVER installiert sind, werden nur von einem eigenständigen Server verwendet und können nicht zugegriffen werden, indem Sie eine Instanz von SQL Server (In-Database). Verwenden Sie immer die `R_SERVICES` Bibliothek Installieren von Paketen, die Sie in der Datenbank auf SQL Server verwenden möchten.
