---
title: Verwenden des R-Paket-Managers
description: Verwenden Sie Standard-r-Befehle wie install. Packages zum Hinzufügen neuer r-Pakete zu SQL Server 2016 R Services oder SQL Server 2017 Machine Learning Services (in-Database).
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 1977e616b8f5ac41f533d49fab684db146cdb204
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469875"
---
# <a name="use-r-package-managers-to-install-r-packages-on-sql-server"></a>Verwenden Sie r-Paket-Manager zum Installieren von r-Paketen auf SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Sie können Standard-R-Tools verwenden, um neue Pakete auf einer Instanz von SQL Server 2016 oder SQL Server 2017 zu installieren, wobei der Computer über einen geöffneten Port 80 verfügt und Sie über Administratorrechte verfügen.

> [!IMPORTANT] 
> Stellen Sie sicher, dass Sie Pakete in der Standardbibliothek installieren, die der aktuellen Instanz zugeordnet ist. Installieren Sie Pakete niemals in einem Benutzerverzeichnis.

In diesem Verfahren wird rgui verwendet, aber Sie können RTERM oder ein beliebiges anderes R-Befehlszeilen Tool verwenden, das erhöhten Zugriff unterstützt.

## <a name="install-a-package-using-rgui"></a>Installieren eines Pakets mithilfe von rgui

1. [Bestimmen Sie den Speicherort der instanzbibliothek](../package-management/default-packages.md). Navigieren Sie zu dem Ordner, in dem die R-Tools installiert sind. Der Standardpfad für eine Standard Instanz von SQL Server 2017 lautet z. b. wie folgt:`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`

1. Klicken Sie mit der rechten Maustaste auf rgui. exe, und wählen Sie **als Administrator ausführen**aus. Wenn Sie nicht über die erforderlichen Berechtigungen verfügen, wenden Sie sich an den Datenbankadministrator, und geben Sie eine Liste der Pakete an, die Sie benötigen.

1. Wenn Sie den Paketnamen kennen, können Sie in der Befehlszeile Folgendes eingeben: `install.packages("the_package-name")`Für den Paketnamen sind doppelte Anführungszeichen erforderlich.

1. Wenn Sie nach einer Spiegel Website gefragt werden, wählen Sie eine beliebige Site aus, die für Ihren Standort geeignet ist.

Wenn das Zielpaket von weiteren Paketen abhängig ist, lädt das R-Installationsprogramm die Abhängigkeiten automatisch herunter und installiert Sie für Sie.

Wenn Sie über mehrere Instanzen von SQL Server verfügen, z. b. parallele Instanzen von SQL Server 2016 R Services und SQL Server 2017 Machine Learning Services, führen Sie die Installation für jede Instanz separat aus, wenn Sie das Paket in beiden Kontexten verwenden möchten. Pakete können nicht über mehrere Instanzen hinweg freigegeben werden.

## <a name = "bkmk_offlineInstall"></a>Offline Installation mithilfe von R-Tools

Wenn der Server nicht über Internet Zugriff verfügt, sind zusätzliche Schritte erforderlich, um die Pakete vorzubereiten. Zum Installieren von R-Paketen auf einem Server, der nicht über Internet Zugriff verfügt, müssen Sie folgende Schritte ausführen:

+ Analysieren Sie Abhängigkeiten im voraus.
+ Laden Sie das Zielpaket auf einen Computer mit Internet Zugriff herunter.
+ Laden Sie alle erforderlichen Pakete auf denselben Computer herunter, und platzieren Sie alle Pakete in einem einzelnen Paketarchiv.
+ Zippen Sie das Archiv, wenn es nicht bereits in einem komprimierten Format vorliegt.
+ Kopieren Sie das Paketarchiv an einen Speicherort auf dem Server.
+ Installieren Sie das Zielpaket, das die Archivdatei als Quelle angibt.

> [!IMPORTANT] 
>  Stellen Sie sicher, dass Sie alle Abhängigkeiten analysieren und **alle** erforderlichen Pakete herunterladen, **bevor** Sie mit der Installation beginnen. Wir empfehlen [minicran](https://mran.microsoft.com/package/miniCRAN) für diesen Prozess. Dieses R-Paket übernimmt eine Liste der Pakete, die Sie installieren möchten, analysiert Abhängigkeiten und ruft alle ZIP-Dateien für Sie ab. der minicran erstellt dann ein einzelnes Repository, das Sie auf den Server Computer kopieren können. Weitere Informationen finden [Sie unter Erstellen eines lokalen paketrepositorys mit minicran](create-a-local-package-repository-using-minicran.md) .

Bei diesem Verfahren wird davon ausgegangen, dass Sie alle Pakete, die Sie benötigen, in komprimierten Formaten vorbereitet haben und bereit sind, Sie auf den Server zu kopieren.

1. Kopieren Sie die ZIP-Datei des Pakets oder für mehrere Pakete das vollständige Repository, das alle Pakete im ZIP-Format enthält, an einen Speicherort, auf den der Server zugreifen kann.

2. Öffnen Sie den Ordner auf dem Server, auf dem die R-Tools für die-Instanz installiert sind. Wenn Sie z. b. die Windows-Eingabeaufforderung auf einem System mit SQL Server 2016 R-Diensten verwenden, `C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`wechseln Sie zu.

3. Klicken Sie mit der rechten Maustaste auf rgui oder RTERM, und wählen Sie **als Administrator ausführen**aus.

4. Führen Sie den R `install.packages` -Befehl aus, und geben Sie den Paket-oder Repository-Namen und den Speicherort der ZIP-Dateien an.

    ```R
    install.packages("C:\\Temp\\Downloaded packages\\mynewpackage.zip", repos=NULL)
    ```

    Dieser Befehl extrahiert das R- `mynewpackage` Paket aus der lokalen ZIP-Datei, wobei angenommen wird, dass Sie die `C:\Temp\Downloaded packages`Kopie im Verzeichnis gespeichert haben, und installiert das Paket auf dem lokalen Computer. Wenn das Paketabhängigkeiten aufweist, prüft das Installationsprogramm, ob vorhandene Pakete in der Bibliothek vorhanden sind. Wenn Sie ein Repository erstellt haben, das die Abhängigkeiten enthält, installiert das Installationsprogramm auch die erforderlichen Pakete.

    Wenn erforderliche Pakete nicht in der instanzbibliothek vorhanden sind und in den ZIP-Dateien nicht gefunden werden können, tritt bei der Installation des Ziel Pakets ein Fehler auf.

## <a name="see-also"></a>Siehe auch

+ [Neue R-Pakete installieren](install-additional-r-packages-on-sql-server.md)
+ [Neue Python-Pakete installieren](../python/install-additional-python-packages-on-sql-server.md)
+ [Tutorials, Beispiele, Lösungen](../tutorials/machine-learning-services-tutorials.md)
