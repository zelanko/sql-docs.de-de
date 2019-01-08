---
title: 'Verwenden Sie T-SQL (CREATE EXTERNAL LIBRARY), um R-Pakete: SQL Server Machine Learning Services installieren'
description: Fügen Sie neue R-Pakete auf SQL Server 2016 R Services oder SQL Server 2017-Machine Learning Services (Datenbankintern) hinzu.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/30/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6e910f1c3b29522b11f1faa83db890d399bf3680
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53645049"
---
# <a name="use-t-sql-create-external-library-to-install-r-packages-on-sql-server"></a>Verwenden Sie T-SQL (CREATE EXTERNAL LIBRARY), um die Installation von R-Pakete auf SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird erläutert, wie Sie neue R-Pakete auf einer Instanz von SQL Server installieren, Machine Learning aktiviert ist. Es gibt mehrere Ansätze zur Auswahl. Mit T-SQL ist am besten geeignet für Server-Administratoren, die nicht mit r vertraut sind.

**Gilt für:**  [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Die [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) -Anweisung ist es möglich, ein Paket oder eine Gruppe von Paketen zu einer Instanz oder eine bestimmte Datenbank hinzuzufügen, ohne das Ausführen von R oder Python-code direkt. Allerdings erfordert diese Methode Paket zur Vorbereitung und zusätzliche Datenbankberechtigungen.

+ Alle Pakete müssen als eine lokale ZIP-Datei verfügbar, anstatt nach Bedarf aus dem Internet heruntergeladene sein.

+ Alle Abhängigkeiten müssen nach Name und Version gekennzeichnet sein und in der Zipdatei enthalten. Die Anweisung schlägt fehl, falls erforderlich, dass die Pakete nicht verfügbar, einschließlich downstream-paketabhängigkeiten sind. 

+ Sie müssen sein **Db_owner** oder über die CREATE EXTERNAL LIBRARY-Berechtigung in einer Datenbankrolle. Weitere Informationen finden Sie unter [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

## <a name="download-packages-in-archive-format"></a>Herunterladen von Paketen im Archivformat

Wenn Sie ein einzelnes Paket installieren, wird herunterladen Sie das Paket in komprimierten Format.

Es ist üblich, mehrere Pakete konnte aufgrund von paketabhängigkeiten zu installieren. Wenn ein Paket andere Pakete erfordert, müssen Sie sicherstellen, dass alle während der Installation erreichbar sind. Es wird empfohlen [Erstellen eines lokalen Repositorys](create-a-local-package-repository-using-minicran.md) mit [MiniCRAN](https://andrie.github.io/miniCRAN/) zusammenstellen eine vollständige Auflistung von Paketen, als auch [Igraph](https://igraph.org/r/) für das Analysieren der Abhängigkeiten von Paketen. Installieren die falsche Version eines Pakets oder eine paketabhängigkeit weglassen kann dazu führen, dass eine CREATE EXTERNAL LIBRARY-Anweisung fehlschlägt. 

## <a name="copy-the-file-to-a-local-folder"></a>Kopieren Sie die Datei in einen lokalen Ordner

Kopieren Sie die ZIP-Datei, die alle Pakete in einen lokalen Ordner auf dem Server enthält. Wenn Sie keinen Zugriff auf das Dateisystem auf dem Server haben, können Sie auch ein vollständiges Paket als Variable übergeben mit einem binären Format. Weitere Informationen finden Sie unter [CREATE EXTERNAL LIBRARY](../../t-sql/statements/create-external-library-transact-sql.md).

## <a name="run-the-statement-to-upload-packages"></a>Führen Sie die Anweisung zum Hochladen von Paketen

Öffnen einer **Abfrage** Fenster mit einem Konto mit Administratorrechten ausführen.

Führen Sie die T-SQL-Anweisung `CREATE EXTERNAL LIBRARY` zum Hochladen der ZIP-Paket-Auflistung in der Datenbank.

Die folgende Anweisung benennt beispielsweise als Paketquelle eine MiniCRAN-Repository mit den **RandomForest** -Paket sowie seine Abhängigkeiten. 

```sql
CREATE EXTERNAL LIBRARY randomForest
FROM (CONTENT = 'C:\Temp\Rpackages\randomForest_4.6-12.zip')
WITH (LANGUAGE = 'R');
```

Sie können keinen beliebigen Namen verwenden. den Namen der externen Bibliothek muss den gleichen Namen haben, den beim Laden oder das Paket Aufrufen verwendet werden sollen.

## <a name="verify-package-installation"></a>Überprüfen der Paketinstallation

Wenn die Bibliothek erfolgreich erstellt wurde, können Sie das Paket in SQL Server ausführen, indem sie innerhalb einer gespeicherten Prozedur aufgerufen wird.
    
```sql
EXEC sp_execute_external_script
@language =N'R',
@script=N'library(randomForest)'
```

## <a name="see-also"></a>Siehe auch

+ [Paketinformationen abrufen](determine-which-packages-are-installed-on-sql-server.md)
+ [R-tutorials](../tutorials/sql-server-r-tutorials.md)
+ [Anleitungen](sql-server-machine-learning-tasks.md)