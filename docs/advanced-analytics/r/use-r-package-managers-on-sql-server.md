---
title: Installieren Sie neue R-Pakete auf SQL Server-Machine Learning-Services | Microsoft Docs
description: Hinzufügen von neuen R-Pakete auf SQL Server 2016 R Services oder SQL Server 2017 Machine Learning Services (Datenbankintern)
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/29/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 8f7b0ee2b623f6a208a92823948bf0295bae33f6
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34707498"
---
# <a name="use-r-package-managers-to-install-r-packages-on-sql-server"></a>Verwenden von R-Paket-Manager zum Installieren von R-Pakete auf SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Können Sie R-Standardtools um neue Pakete auf einer Instanz von SQL Server 2016 zu installieren oder SQL Server 2017 Bereitstellen des Computers verfügt über einen geöffneten Port 80, und Sie über Administratorrechte verfügen.

> [!IMPORTANT] 
> Achten Sie darauf, dass Pakete in der Standardbibliothek installieren, die der aktuellen Instanz zugeordnet ist. Installieren Sie Pakete niemals ein Verzeichnis des Benutzers.

Dieses Verfahren verwendet, "rgui.exe", jedoch können Sie RTerm oder eine beliebige andere R Befehlszeilentool, die mit erhöhten Rechten Datenzugriff unterstützt.

## <a name="install-a-package-using-rgui"></a>Installieren eines Pakets mithilfe von "rgui.exe"

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
>  Achten Sie darauf, dass Sie alle Abhängigkeiten analysieren und herunterladen **alle** benötigte Pakete **vor** mit der Installation beginnen. Wir empfehlen [MiniCRAN](https://mran.microsoft.com/package/miniCRAN) für diesen Prozess. Diese R-Paket kann es sich um eine Liste der Pakete, die Sie installieren möchten, Abhängigkeiten analysiert und ruft die ZIP-Dateien für Sie. MiniCRAN erstellt dann ein einzelnes Repository, das Sie in Server-Computer kopieren können. Weitere Informationen finden Sie unter [erstellen Sie ein lokales Paket-Repository mit MiniCRAN](create-a-local-package-repository-using-minicran.md)

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

## <a name="see-also"></a>Siehe auch

+ [Neue R-Pakete installieren](install-additional-r-packages-on-sql-server.md)
+ [Neue Python-Pakete installieren](../python/install-additional-python-packages-on-sql-server.md)
+ [Tutorials, Beispiele, Lösungen](../tutorials/machine-learning-services-tutorials.md)