---
title: Verwenden von T-SQL (externe Bibliothek erstellen) zum Installieren von R-Paketen
description: Fügen Sie SQL Server 2016 r Services oder SQL Server Machine Learning Services (in-Database) neue R-Pakete hinzu.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/12/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 1acaae39d71abd1cbd68781c0edec76308b85760
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715731"
---
# <a name="use-t-sql-create-external-library-to-install-r-packages-on-sql-server"></a>Verwenden von T-SQL (externe Bibliothek erstellen) zum Installieren von R-Paketen auf SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel wird erläutert, wie Sie neue R-Pakete auf einer Instanz von SQL Server installieren, auf der Machine Learning aktiviert ist. Es gibt mehrere Ansätze, aus denen Sie auswählen können. Die Verwendung von T-SQL funktioniert am besten für Server Administratoren, die mit R nicht vertraut sind.

**Gilt für:** [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)]  [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Die Anweisung [Create externe Library](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) ermöglicht das Hinzufügen eines Pakets oder einer Gruppe von Paketen zu einer Instanz oder einer bestimmten Datenbank, ohne dass R-oder python-Code direkt ausgeführt werden muss. Diese Methode erfordert jedoch Paket Vorbereitung und zusätzliche Daten Bank Berechtigungen.

+ Alle Pakete müssen als lokale ZIP-Datei verfügbar sein und nicht Bedarfs gesteuert aus dem Internet heruntergeladen werden.

+ Alle Abhängigkeiten müssen anhand des Namens und der Version identifiziert und in der ZIP-Datei enthalten sein. Die-Anweisung schlägt fehl, wenn erforderliche Pakete nicht verfügbar sind, einschließlich von downstreampaketabhängigkeiten. 

+ Sie müssen über **db_owner** verfügen oder über die Berechtigung externe Bibliothek erstellen in einer Daten Bank Rolle verfügen. Weitere Informationen finden Sie unter [Erstellen einer externen Bibliothek](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

## <a name="download-packages-in-archive-format"></a>Pakete im Archivformat herunterladen

Wenn Sie ein einzelnes Paket installieren, laden Sie das Paket im ZIP-Format herunter.

Es ist häufiger üblich, aufgrund von Paketabhängigkeiten mehrere Pakete zu installieren. Wenn für ein Paket Andere Pakete erforderlich sind, müssen Sie überprüfen, ob während der Installation alle verfügbar sind. Wir empfehlen die [Erstellung eines lokalen Repository](create-a-local-package-repository-using-minicran.md) mithilfe von [minicran](https://andrie.github.io/miniCRAN/) , um eine vollständige Sammlung von Paketen zusammenzustellen, sowie [igraph](https://igraph.org/r/) zum Analysieren von Paketabhängigkeiten. Wenn Sie die falsche Version eines Pakets installieren oder eine Paketabhängigkeit weglassen, kann dies dazu führen, dass eine CREATE externe Library-Anweisung fehlschlägt. 

## <a name="copy-the-file-to-a-local-folder"></a>Kopieren Sie die Datei in einen lokalen Ordner.

Kopieren Sie die ZIP-Datei mit allen Paketen in einen lokalen Ordner auf dem Server. Wenn Sie keinen Zugriff auf das Dateisystem auf dem Server haben, können Sie auch ein umfassendes Paket als Variable übergeben, indem Sie ein Binärformat verwenden. Weitere Informationen finden Sie unter [Erstellen einer externen Bibliothek](../../t-sql/statements/create-external-library-transact-sql.md).

## <a name="run-the-statement-to-upload-packages"></a>Ausführen der Anweisung zum Hochladen von Paketen

Öffnen Sie ein **Abfrage** Fenster, und verwenden Sie ein Konto mit Administratorrechten.

Führen Sie die T-SQL `CREATE EXTERNAL LIBRARY` -Anweisung aus, um die komprimierte Paket Sammlung in die-Datenbank hochzuladen.

Beispielsweise ist die folgende Anweisung als Paketquelle ein minicran-Repository, das das Paket **randomforest** enthält, sowie die zugehörigen Abhängigkeiten. 

```sql
CREATE EXTERNAL LIBRARY randomForest
FROM (CONTENT = 'C:\Temp\Rpackages\randomForest_4.6-12.zip')
WITH (LANGUAGE = 'R');
```

Sie können keinen beliebigen Namen verwenden. der Name der externen Bibliothek muss den gleichen Namen aufweisen, den Sie beim Laden oder Aufrufen des Pakets verwenden.

## <a name="verify-package-installation"></a>Überprüfen der Paketinstallation

Wenn die Bibliothek erfolgreich erstellt wurde, können Sie das Paket in SQL Server ausführen, indem Sie es in einer gespeicherten Prozedur aufrufen.
    
```sql
EXEC sp_execute_external_script
@language =N'R',
@script=N'library(randomForest)'
```

## <a name="see-also"></a>Siehe auch

+ [Paketinformationen abrufen](../package-management/installed-package-information.md)
+ [R-Tutorials](../tutorials/sql-server-r-tutorials.md)
