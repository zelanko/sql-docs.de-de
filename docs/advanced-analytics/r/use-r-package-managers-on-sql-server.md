---
title: Verwenden von R-Paket-Manager - SQL Server Machine Learning Services
description: Verwenden Sie R-Standardbefehle wie install.packages, um neue R-Pakete auf SQL Server 2016 R Services oder SQL Server 2017-Machine Learning Services (Datenbankintern) hinzuzufügen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 2582d519893fac3a49ce997674980d2d58d5cf32
ms.sourcegitcommit: a91c3f4fe2587d474cd4d470bda93239ba2693bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/14/2019
ms.locfileid: "67140778"
---
# <a name="use-r-package-managers-to-install-r-packages-on-sql-server"></a>Verwenden von R-Paket-Manager zum Installieren von R-Pakete auf SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Können Sie R-Standardtools zum Installieren neuer Pakete in einer Instanz von SQL Server 2016 oder SQL Server 2017 Bereitstellen des Computers verfügt über einen geöffneten Port 80, und Sie über Administratorrechte verfügen.

> [!IMPORTANT] 
> Achten Sie darauf, zum Installieren von Paketen in der Standardbibliothek, der mit der aktuellen Instanz zugeordnet ist. Installieren Sie Pakete nicht auf ein Benutzerverzeichnis.

Diese Prozedur verwendet RGui, jedoch können RTerm oder ein anderes R Befehlszeilen Tool, die mit erhöhten Rechten Datenzugriff unterstützt.

## <a name="install-a-package-using-rgui"></a>Installieren eines Pakets mit RGui

1. [Bestimmen Sie den Speicherort der Instanz-Bibliothek](../package-management/default-packages.md). Navigieren Sie zu dem Ordner, in dem die R-Tools installiert sind. Beispielsweise lautet der standardmäßige Pfad für eine Standardinstanz von SQL Server 2017: `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`

1. Mit der rechten Maustaste RGui.exe, und wählen **als Administrator ausführen**. Wenn Sie nicht über die erforderlichen Berechtigungen verfügen, wenden Sie sich an den Datenbankadministrator, und geben Sie eine Liste der Pakete, die Sie benötigen.

1. Über die Befehlszeile Wenn Sie wissen, dass der Paketname, können Sie eingeben: `install.packages("the_package-name")` Doppelte Anführungszeichen sind erforderlich, für den Paketnamen ein.

1. Wenn nach einer gespiegelten Site gefragt werden, wählen Sie einen Standort, der für Ihren Standort zweckmäßig ist.

Wenn das Zielpaket von weiteren Paketen abhängig ist, werden von R-Installationsprogramm automatisch die Abhängigkeiten heruntergeladen und installiert sie für Sie.

Wenn Sie mehrere Instanzen von SQL Server, z. B. Seite-an-Seite-Instanzen von SQL Server 2016 R Services und SQL Server 2017 Machine Learning Services verwenden führen Sie die Installation separat für jede Instanz, wenn Sie das Paket in beiden Kontexten verwenden möchten. Pakete können nicht zwischen Instanzen freigegeben werden.

## <a name = "bkmk_offlineInstall"></a> Offline-Installation mit R-tools

Wenn der Server nicht über Internetzugriff verfügt, sind zusätzliche Schritte erforderlich, um die Pakete vorzubereiten. Um R-Pakete auf einem Server installieren, die nicht über Internetzugriff verfügt, müssen Sie folgende Aktionen ausführen:

+ Analysieren von Abhängigkeiten im voraus.
+ Laden Sie das Zielpaket auf einem Computer mit Internetzugriff herunter.
+ Herunterladen Sie alle erforderlichen Pakete auf dem gleichen Computer, und platzieren Sie alle Pakete in einem einzelnen Paket-Archiv.
+ ZIP-Archiv ist dies nicht bereits im komprimierten Format.
+ Kopieren Sie das Archiv Paket an einem Speicherort auf dem Server.
+ Installieren Sie das Zielpaket die Archivdatei als Quelle angeben.

> [!IMPORTANT] 
>  Achten Sie darauf, dass Sie alle Abhängigkeiten analysieren und Herunterladen von **alle** erforderlichen Pakete **vor** mit der Installation beginnen. Es wird empfohlen [MiniCRAN](https://mran.microsoft.com/package/miniCRAN) für diesen Prozess. Dieses R-Paket kann es sich um eine Liste von Paketen, die Sie installieren möchten, Abhängigkeiten analysiert und ruft alle ZIP-Dateien für Sie. MiniCRAN erstellt dann ein einzelnes Repository, das Sie zum Server-Computer kopieren können. Weitere Informationen finden Sie unter [erstellen ein lokalen paketrepositorys mit MiniCRAN](create-a-local-package-repository-using-minicran.md)

Dieses Verfahren setzt voraus, dass Sie alle Pakete vorbereitet haben, dass Sie, im ZIP-Format benötigen und sie auf dem Server zu kopieren können.

1. Kopieren des Pakets ZIP-Datei, oder für mehrere Pakete des vollständigen Repositorys mit der alle Pakete in komprimierten ZIP-Format, an einem Speicherort an, dem auf der Server zugreifen kann.

2. Öffnen Sie den Ordner auf dem Server, auf dem die R-Tools für die Instanz installiert sind. Z. B. Wenn Sie die Windows-Eingabeaufforderung auf einem System mit SQL Server 2016 R Services verwenden, wechseln Sie zum `C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`.

3. Mit der rechten Maustaste auf RGui oder RTerm, und wählen **als Administrator ausführen**.

4. Führen Sie den R-Befehl `install.packages` , und geben Sie das Paket oder Name des Repositorys und den Speicherort der ZIP-Dateien.

    ```R
    install.packages("C:\\Temp\\Downloaded packages\\mynewpackage.zip", repos=NULL)
    ```

    Dieser Befehl extrahiert das R-Paket `mynewpackage` aus der lokalen ZIP-Datei, sofern Sie die Kopie im Verzeichnis gespeichert `C:\Temp\Downloaded packages`, und das Paket auf dem lokalen Computer installiert. Wenn das Paket, Abhängigkeiten aufweist, prüft das Installationsprogramm für vorhandene Pakete in der Bibliothek. Wenn Sie ein Repository, die die Abhängigkeiten enthält erstellt haben, installiert das Installationsprogramm die erforderlichen Pakete auch an.

    Wenn alle erforderlichen Pakete in der Bibliothek für die Instanz nicht vorhanden sind und können nicht in die ZIP-Dateien gefunden werden, schlägt die Installation des Zielpakets fehl.

## <a name="see-also"></a>Siehe auch

+ [Neue R-Pakete installieren](install-additional-r-packages-on-sql-server.md)
+ [Neue Python-Pakete installieren](../python/install-additional-python-packages-on-sql-server.md)
+ [Tutorials, Beispiele, Lösungen](../tutorials/machine-learning-services-tutorials.md)
