---
title: T-SQL (Erstellen einer EXTERNEN Bibliothek) verwenden, um R-Pakete auf SQL Server-Machine Learning-Services zu installieren | Microsoft Docs
description: Hinzufügen von neuen R-Pakete in SQL Server 2017 Machine Learning Services (Datenbankintern)
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/20/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: bbc1adf4868cbfbd02afe5cae3a38fd6223e2d4d
ms.sourcegitcommit: b5ab9f3a55800b0ccd7e16997f4cd6184b4995f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2018
---
# <a name="use-t-sql-create-external-library-to-install-r-packages-on-sql-server-2017-machine-learning-services"></a>Verwenden Sie T-SQL (Erstellen einer EXTERNEN Bibliothek), um R-Pakete auf SQL Server 2017 Machine Learning Services installieren
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel beschreibt, wie neue R-Pakete mit einer Instanz von SQL Server installieren, Machine Learning aktiviert ist. Es gibt mehrere Ansätze zur Auswahl. Dieser Ansatz funktioniert am besten für Serveradministratoren, die mit r nicht vertraut sind.

**Gilt für:**  [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Die [externe Bibliothek erstellen](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) -Anweisung ist es möglich, ein Paket oder eine Reihe von Paketen zu einer Instanz oder eine bestimmte Datenbank hinzuzufügen, ohne Ausführen von R oder Python-code direkt. Diese Methode erfordert jedoch Paket Vorbereitung und zusätzliche Datenbankberechtigungen.

+ Alle Pakete als eine lokale ZIP-Datei verfügbar sein muss, anstatt bei Bedarf aus dem Internet heruntergeladen.

+ Alle Abhängigkeiten müssen nach Name und Version identifiziert, und in der Zipdatei enthalten. Die Anweisung schlägt fehl, wenn die erforderlichen Pakete stehen nicht zur Verfügung, einschließlich downstream-paketabhängigkeiten. 

+ Sie müssen die erforderlichen Berechtigungen für die Datenbank verfügen. Weitere Informationen finden Sie unter [externe Bibliothek erstellen](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

## <a name="download-packages-in-archive-format"></a>Herunterladen von Paketen im Archivformat

Wenn Sie ein einzelnes Paket installieren, wird herunterladen Sie das Paket im ZIP-Format.

Wenn das Paket andere Pakete erfordert, müssen Sie sicherstellen, dass die erforderlichen Pakete verfügbar sind. Sie können MiniCRAN analysieren Das Zielpaket und identifizieren alle abhängigen Elemente. Es wird empfohlen, [ **MiniCRAN** ](create-a-local-package-repository-using-minicran.md) oder [ **Igraph** ](http://igraph.org/r/) zum Analysieren von Paketen Abhängigkeiten. Installieren die falsche Version des Pakets oder paketabhängigkeit kann auch zum Fehlschlagen die Anweisung führen. 

## <a name="copy-the-file-to-a-local-folder"></a>Kopieren Sie die Datei in einen lokalen Ordner

Kopieren Sie die ZIP-Datei, die alle Pakete in einen lokalen Ordner auf dem Server enthält. Wenn Sie keinen Zugriff auf das Dateisystem auf dem Server haben, können Sie auch ein vollständiges Paket als Variable übergeben mit einem binary-Format. Weitere Informationen finden Sie unter [externe Bibliothek erstellen](../../t-sql/statements/create-external-library-transact-sql.md).

## <a name="run-the-statement-to-upload-packages"></a>Führen Sie die Anweisung aus, um Pakete hochladen

Öffnen einer **Abfrage** Fenster mit einem Konto mit Administratorrechten aus.

Führen Sie die T-SQL-Anweisung `CREATE EXTERNAL LIBRARY` zum Hochladen von ZIP-Paket-Auflistung in der Datenbank.

    For example, the following statement names as the package source a miniCRAN repository containing the **randomForest** package, together with its dependencies. 

    ```R
    CREATE EXTERNAL LIBRARY randomForest
    FROM (CONTENT = 'C:\Temp\Rpackages\randomForest_4.6-12.zip')
    WITH (LANGUAGE = 'R');
    ```

    You cannot use an arbitrary name; the external library name must have the same name that you expect to use when loading or calling the package.

## <a name="verify-package-installation"></a>Überprüfen Sie die Paketinstallation

Wenn die Bibliothek erfolgreich erstellt wurde, können Sie das Paket in SQL Server ausführen, indem sie innerhalb einer gespeicherten Prozedur aufgerufen wird.
    
    ```SQL
    EXEC sp_execute_external_script
    @language =N'R',
    @script=N'
    library(randomForest)'
    ```

