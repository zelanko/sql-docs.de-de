---
title: Verwenden des R-Paket-Managers
description: Verwenden Sie R-Standardbefehle wie install.packages, um neue R-Pakete zu SQL Server 2016 R Services oder SQL Server Machine Learning Services (datenbankintern) hinzuzufügen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 1f6d828a7267ab2b4b1def17f9d1c6bf4a6018dc
ms.sourcegitcommit: 632ff55084339f054d5934a81c63c77a93ede4ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "69633616"
---
# <a name="use-r-package-managers-to-install-r-packages-on-sql-server"></a>Verwenden von R-Paket-Managers zum Installieren von R-Paketen in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Mit den standardmäßigen R-Tools können Sie neue Pakete auf einer SQL Server 2016- oder SQL Server 2017-Instanz installieren, vorausgesetzt, der Port 80 auf dem Computer ist geöffnet und Sie verfügen über Administratorrechte.

> [!IMPORTANT] 
> Stellen Sie sicher, dass Sie Pakete in der Standardbibliothek installieren, die der aktuellen Instanz zugeordnet ist. Installieren Sie Pakete niemals in einem Benutzerverzeichnis.

In dieser Prozedur wird RGui verwendet, aber Sie können RTerm oder jedes andere Befehlszeilentool von R verwenden, das erhöhte Zugriffsrechte unterstützt.

## <a name="install-a-package-using-rgui"></a>Installieren eines Pakets mithilfe von RGui

1. [Ermitteln Sie den Speicherort der Instanzbibliothek](../package-management/r-package-information.md). Navigieren Sie zu dem Ordner, in dem die R-Tools installiert sind. Der Standardpfad für eine Standardinstanz von SQL Server 2017 lautet z. B. wie folgt: `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`

1. Klicken Sie mit der rechten Maustaste auf die Datei „RGui.exe“, und wählen Sie **Als Administrator ausführen** aus. Wenn Sie nicht über die erforderlichen Berechtigungen verfügen, wenden Sie sich an den Datenbankadministrator und geben Sie ihm eine Liste der benötigten Pakete.

1. Wenn Sie den Paketnamen kennen, können Sie in der Befehlszeile Folgendes eingeben: `install.packages("the_package-name")` Für den Namen des Pakets sind doppelte Anführungszeichen erforderlich.

1. Wenn Sie nach einer gespiegelten Site gefragt werden, wählen Sie eine beliebige Site aus, die für Ihren Standort zweckmäßig ist.

Wenn das Zielpaket von weiteren Paketen abhängig ist, werden die Abhängigkeiten vom R-Installationsprogramm automatisch heruntergeladen und installiert.

Bei mehreren SQL Server-Instanzen, wie z. B. parallelen Instanzen von SQL Server 2016 R Services und SQL Server Machine Learning Services, führen Sie die Installation für jede Instanz separat durch, wenn Sie das Paket in beiden Kontexten verwenden möchten. Pakete können nicht von mehreren Instanzen gemeinsam genutzt werden.

## <a name = "bkmk_offlineInstall"></a> Offlineinstallation mithilfe von R-Tools

Wenn der Server keinen Internetzugang hat, sind zusätzliche Schritte zur Vorbereitung der Pakete erforderlich. Zur Installation von R-Paketen auf einem Server, der keinen Internetzugang hat, gehen Sie wie folgt vor:

+ Analysieren Sie vorab die Abhängigkeiten.
+ Laden Sie das Zielpaket auf einen Computer mit Internetzugang herunter.
+ Laden Sie alle erforderlichen Pakete auf denselben Computer herunter, und platzieren Sie alle Pakete in einem einzelnen Paketarchiv.
+ Erstellen Sie eine ZIP-Datei aus dem Archiv, falls dieses noch nicht im ZIP-Format vorliegt.
+ Kopieren Sie das Paketarchiv in ein Verzeichnis auf dem Server.
+ Installieren Sie das Zielpaket, indem Sie die Archivdatei als Quelle angeben.

> [!IMPORTANT] 
>  Stellen Sie sicher, dass Sie alle Abhängigkeiten analysieren und **alle** benötigten Pakete herunterladen, **bevor** Sie mit der Installation beginnen. Für diesen Prozess wird [miniCRAN](https://mran.microsoft.com/package/miniCRAN) empfohlen. Dieses R-Paket übernimmt eine Liste der Pakete, die Sie installieren möchten, analysiert Abhängigkeiten und ruft alle ZIP-Dateien für Sie ab. Anschließend erstellt miniCRAN ein einzelnes Repository, das Sie dann auf den Servercomputer kopieren können. Weitere Informationen finden Sie im Artikel zum Thema [Erstellen eines lokalen Paketrepositorys mit miniCRAN](create-a-local-package-repository-using-minicran.md).

In dieser Prozedur wird davon ausgegangen, dass Sie alle benötigten Pakete im ZIP-Format vorbereitet haben und diese auf den Server kopieren können.

1. Kopieren Sie die ZIP-Datei des Pakets oder bei mehreren Paketen das komplette Repository mit allen Paketen im ZIP-Format an einen Speicherort, auf den der Server zugreifen kann.

2. Öffnen Sie den Ordner auf dem Server, auf dem die R-Tools für die Instanz installiert sind. Wenn Sie z. B. die Windows-Eingabeaufforderung auf einem System mit SQL Server 2016 R Services verwenden, wechseln Sie zu `C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`.

3. Klicken Sie mit der rechten Maustaste auf RGui oder RTerm, und wählen Sie **Als Administrator ausführen** aus.

4. Führen Sie den R-Befehl `install.packages` aus, und geben Sie den Paket- oder Repositorynamen und den Speicherort der ZIP-Dateien an.

    ```R
    install.packages("C:\\Temp\\Downloaded packages\\mynewpackage.zip", repos=NULL)
    ```

    Dieser Befehl extrahiert das R-Paket `mynewpackage` aus der lokalen ZIP-Datei, sofern Sie die Kopie im Verzeichnis `C:\Temp\Downloaded packages` gespeichert haben, und installiert das Paket auf dem lokalen Computer. Wenn das Paket Abhängigkeiten aufweist, prüft das Installationsprogramm, ob bereits Pakete in der Bibliothek vorhanden sind. Haben Sie ein Repository erstellt, das die Abhängigkeiten enthält, installiert das Installationsprogramm auch die erforderlichen Pakete.

    Wenn erforderliche Pakete nicht in der Instanzbibliothek vorhanden sind und nicht in den ZIP-Dateien gefunden werden, schlägt die Installation des Zielpakets fehl.

## <a name="see-also"></a>Siehe auch

+ [Neue R-Pakete installieren](install-additional-r-packages-on-sql-server.md)
+ [Neue Python-Pakete installieren](../python/install-additional-python-packages-on-sql-server.md)
+ [Tutorials, Beispiele, Lösungen](../tutorials/machine-learning-services-tutorials.md)
