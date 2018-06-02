---
title: T-SQL (Erstellen einer EXTERNEN Bibliothek) verwenden, um R-Pakete auf SQL Server-Machine Learning-Services zu installieren | Microsoft Docs
description: Hinzufügen von neuen R-Pakete in SQL Server 2017 Machine Learning Services (Datenbankintern)
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/30/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 7a5a0c394e9a26244661a4ae712d20583c1f1c99
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34585482"
---
# <a name="use-t-sql-create-external-library-to-install-r-packages-on-sql-server-2017-machine-learning-services"></a>Verwenden Sie T-SQL (Erstellen einer EXTERNEN Bibliothek), um R-Pakete auf SQL Server 2017 Machine Learning Services installieren
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel erläutert, wie neue R-Pakete auf einer Instanz von SQL Server installieren, Machine Learning aktiviert ist. Es gibt mehrere Ansätze zur Auswahl. Verwenden von T-SQL ist am besten geeignet für Serveradministratoren, die mit r nicht vertraut sind.

**Gilt für:**  [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Die [externe Bibliothek erstellen](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) -Anweisung ist es möglich, ein Paket oder eine Reihe von Paketen zu einer Instanz oder eine bestimmte Datenbank hinzuzufügen, ohne Ausführen von R oder Python-code direkt. Diese Methode erfordert jedoch Paket Vorbereitung und zusätzliche Datenbankberechtigungen.

+ Alle Pakete müssen als eine lokale ZIP-Datei verfügbar, anstatt bei Bedarf aus dem Internet heruntergeladene sein.

+ Alle Abhängigkeiten müssen nach Name und Version identifiziert, und in der Zipdatei enthalten. Die Anweisung schlägt fehl, wenn die erforderlichen Pakete stehen nicht zur Verfügung, einschließlich downstream-paketabhängigkeiten. 

+ Sie muss **Db_owner** oder berechtigt in einer Datenbankrolle, externe Bibliothek erstellen. Weitere Informationen finden Sie unter [externe Bibliothek erstellen](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

## <a name="download-packages-in-archive-format"></a>Herunterladen von Paketen im Archivformat

Wenn Sie ein einzelnes Paket installieren, wird herunterladen Sie das Paket im ZIP-Format.

Es ist eher üblich, mehrere Pakete konnte aufgrund von paketabhängigkeiten zu installieren. Wenn ein Paket andere Pakete erfordert, müssen Sie sicherstellen, dass alle miteinander während der Installation verfügbar sind. Es wird empfohlen [erstellen ein lokales Repository](create-a-local-package-repository-using-minicran.md) mit [MiniCRAN](http://andrie.github.io/miniCRAN/) um eine vollständige Auflistung von Paketen, assemblieren sowie [Igraph](http://igraph.org/r/) zum Analysieren von Paketen Abhängigkeiten. Installieren die falsche Version eines Pakets oder eine paketabhängigkeit auslassen kann dazu führen, dass eine externe Bibliothek erstellen-Anweisung fehl. 

## <a name="copy-the-file-to-a-local-folder"></a>Kopieren Sie die Datei in einen lokalen Ordner

Kopieren Sie die ZIP-Datei, die alle Pakete in einen lokalen Ordner auf dem Server enthält. Wenn Sie keinen Zugriff auf das Dateisystem auf dem Server haben, können Sie auch ein vollständiges Paket als Variable übergeben mit einem binary-Format. Weitere Informationen finden Sie unter [externe Bibliothek erstellen](../../t-sql/statements/create-external-library-transact-sql.md).

## <a name="run-the-statement-to-upload-packages"></a>Führen Sie die Anweisung aus, um Pakete hochladen

Öffnen einer **Abfrage** Fenster mit einem Konto mit Administratorrechten aus.

Führen Sie die T-SQL-Anweisung `CREATE EXTERNAL LIBRARY` zum Hochladen von ZIP-Paket-Auflistung in der Datenbank.

Die folgende Anweisung benennt beispielsweise als Paketquelle eine MiniCRAN "Repository" enthält die **RandomForest** -Paket, zusammen mit seiner Abhängigkeiten. 

```SQL
CREATE EXTERNAL LIBRARY randomForest
FROM (CONTENT = 'C:\Temp\Rpackages\randomForest_4.6-12.zip')
WITH (LANGUAGE = 'R');
```

Sie können keinen beliebigen Namen verwenden. den Namen der externen muss den gleichen Namen haben, den voraussichtlich verwenden, wenn beim Laden oder das Paket aufgerufen.

## <a name="verify-package-installation"></a>Überprüfen Sie die Paketinstallation

Wenn die Bibliothek erfolgreich erstellt wurde, können Sie das Paket in SQL Server ausführen, indem sie innerhalb einer gespeicherten Prozedur aufgerufen wird.
    
```SQL
EXEC sp_execute_external_script
@language =N'R',
@script=N'library(randomForest)'
```

## <a name="see-also"></a>Siehe auch

+ [Paketinformationen abrufen](determine-which-packages-are-installed-on-sql-server.md)
+ [R-Lernprogramme](../tutorials/sql-server-r-tutorials.md)
+ [Anleitungen](sql-server-machine-learning-tasks.md)