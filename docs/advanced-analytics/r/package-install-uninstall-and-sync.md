---
title: Synchronisierung von R-Paket aus dem Dateisystem – SQL Server Machine Learning Services
description: Aktualisieren Sie auf SQL Server R-Bibliotheken durch neuere Versionen, die im Dateisystem installiert.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 5b7141e1fe6256c7a7e21056d82f2d8fc4ad4faf
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2018
ms.locfileid: "53431817"
---
# <a name="r-package-synchronization-for-sql-server"></a>Synchronisierung von R-Paket für SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Die Version von RevoScaleR in SQL Server 2017 enthalten umfasst die Möglichkeit, synchronisieren Sammlungen von R-Pakete zwischen dem Dateisystem und die Instanz und Datenbank, in denen Pakete verwendet werden.

Dieses Feature wurde angegeben, um zu vereinfachen, um R-Paket-Sammlungen, die zugeordneten SQL Server-Datenbanken zu sichern. Mit diesem Feature kann Administrator wiederherstellen, nicht nur die Datenbank, sondern alle R-Pakete, die von Datenanalysten, die Arbeit in dieser Datenbank verwendet wurden.

Dieser Artikel beschreibt das Synchronisierungsfeature Paket, und wie Sie mit der [RxSyncPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsyncpackages) Funktion, um die folgenden Aufgaben ausführen:

+ Eine Liste der Pakete für eine gesamte SQL Server-Datenbank zu synchronisieren

+ Synchronisieren Sie die Pakete, die durch einen einzelnen Benutzer oder eine Gruppe von Benutzern verwendet.

+ Wenn ein Benutzer auf einen anderen SQL Server verschoben wird, können Sie eine Sicherung des Arbeitsdatenbank des Benutzers und in den neuen Server wiederhergestellt werden kann, und die Pakete für den Benutzer in das Dateisystem auf dem neuen Server, nach Bedarf von r installiert werden

Sie können z. B. paketsynchronisierung in diesen Szenarien verwenden:

+ Der Datenbankadministrator eine Instanz von SQL Server zu einem neuen Computer wiederhergestellt hat und bittet die Benutzer eine Verbindung aus ihrer R-Clients, und führen `rxSyncPackages` aktualisiert, und stellen ihre Pakete wieder her.

+ Sie denken, ein R-Paket im Dateisystem ist beschädigt. Führen Sie Sie `rxSyncPackages` auf dem SQL Server.

## <a name="requirements"></a>Anforderungen

Bevor Sie die paketsynchronisierung verwenden können, müssen Sie die entsprechende Version von Microsoft R oder Machine Learning Server verfügen. Diese Funktion wird in Microsoft R Version 9.1.0 oder höher bereitgestellt werden. 

Außerdem müssen Sie aktivieren die [paketverwaltungsfunktion](r-package-how-to-enable-or-disable.md) auf dem Server.

### <a name="determine-whether-your-server-supports-package-management"></a>Bestimmen Sie, ob der Server, paketverwaltung unterstützt

Dieses Feature ist in SQL Server 2017 CTP 2 oder höher verfügbar.

Sie können dieses Feature mit einer Instanz von SQL Server 2016 hinzufügen, indem Sie ein Upgrade der Instanz um die neueste Version von Microsoft R. verwenden Weitere Informationen finden Sie unter [Verwenden von SqlBindR.exe zum Aktualisieren von SQL Server R Services](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

### <a name="enable-the-package-management-feature"></a>Aktivieren Sie die paketverwaltungsfunktion

Verwendung der paketsynchronisierung erfordert, dass die neue paketverwaltungsfunktion auf SQL Server-Instanz, und klicken Sie auf einzelne Datenbanken aktiviert werden. Weitere Informationen finden Sie unter [aktivieren oder Deaktivieren der paketverwaltung für SQL Server](r-package-how-to-enable-or-disable.md).

1. Der Server-Administrator können die Funktion für SQL Server-Instanz.
2. Für jede Datenbank erteilt der Administrator einzelne Benutzer die Möglichkeit zum Installieren oder Teilen Sie R-Pakete mithilfe von Datenbankrollen.

Wenn dies abgeschlossen ist, können Sie RevoScaleR-Funktionen, z. B. [RxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) zum Installieren der Pakete in einer Datenbank.  Informationen zu Benutzern und die Pakete, die sie verwenden können, ist in SQL Server-Instanz gespeichert. 

Wenn Sie ein neues Paket, das mithilfe der Paket-Management-Funktionen hinzufügen, werden sowohl die Datensätze in SQL Server und dem Dateisystem aktualisiert. Diese Informationen kann verwendet werden, die Paketinformationen für die gesamte Datenbank wiederherstellen.

### <a name="permissions"></a>Berechtigungen

+ Die Person, die die Paket-Synchronisierung-Funktion führt muss einem Sicherheitsprinzipal auf dem SQL Server-Instanz und die Datenbank, die dem Pakete gespeichert sind.

+ Der Aufrufer der Funktion muss ein Mitglied einer dieser Paket-Management-Rollen: **Rpkgs-shared** oder **Rpkgs-Private**.

+ Synchronisieren von Paketen, die als **freigegebenen**, muss die Person, die die Funktion ausgeführt wird die Mitgliedschaft in der **Rpkgs-shared** Rolle und die Pakete, die verschoben werden müssen installiert wurde an einen freigegebenen Scope-Bibliothek.

+ Synchronisieren von Paketen, die als **private**, entweder der Besitzer des Pakets oder der Administrator muss die Funktion ausgeführt, und die Pakete müssen privat sein.

+ Um Pakete im Namen anderer Benutzer zu synchronisieren, muss der Besitzer Bhe ein Mitglied der **Db_owner** -Datenbankrolle.

## <a name="how-package-synchronization-works"></a>Funktionsweise der paketsynchronisierung

Rufen Sie zum Verwenden der paketsynchronisierung [RxSyncPackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsyncpackages), dies ist eine neue Funktion in [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler). 

Für jeden Aufruf von `rxSyncPackages`, müssen Sie eine SQL Server-Instanz und Datenbank angeben. Entweder Sie dann die Liste der Pakete zum Synchronisieren, oder geben Sie Paketbereich.

1. Erstellen Sie den SQL Server-computekontext mithilfe der `RxInSqlServer` Funktion. Wenn Sie einen computekontext nicht angeben, wird der aktuellen computekontext verwendet.

2. Geben Sie den Namen einer Datenbank, auf die Instanz im angegebenen rechenkontext. Pakete werden pro Datenbank synchronisiert.

3. Angegeben Sie die Pakete zu synchronisieren, indem Sie mit dem Scope-Argument.

    Bei Verwendung von **private** Bereich nur Pakete, die im Besitz von dem angegebenen Besitzer werden synchronisiert. Bei Angabe von **freigegebenen** Bereich alle nicht-privaten Pakete in der Datenbank synchronisiert werden. 
    
    Wenn Sie die Funktion ausführen, ohne dass eine **private** oder **freigegebenen** Bereich alle Pakete werden synchronisiert.

4. Wenn der Befehl erfolgreich ist, werden vorhandene Pakete im Dateisystem mit dem angegebenen Bereich und der Besitzer der Datenbank hinzugefügt.

    Wenn das Dateisystem beschädigt ist, werden die Pakete wiederhergestellt, basierend auf der Liste, die in der Datenbank verwaltet.

    Wenn die paketverwaltungsfunktion nicht in der Zieldatenbank verfügbar ist, wird ein Fehler ausgelöst: "Die paketverwaltungsfunktion ist entweder nicht auf dem SQL Server aktiviert, oder die Version ist veraltet"

### <a name="example-1-synchronize-all-package-by-database"></a>Beispiel 1. Alle Paket von der Datenbank zu synchronisieren.

In diesem Beispiel ruft alle neuen Pakete aus dem lokalen Dateisystem und die Pakete werden in der Datenbank [TestDB] installiert. Da kein Besitzer spezifisch ist, enthält die Liste aller Pakete, die für private und gemeinsam genutzte Bereiche installiert wurden.

```R
connectionString <- "Driver=SQL Server;Server=myServer;Database=TestDB;Trusted_Connection=True;"
computeContext <- RxInSqlServer(connectionString = connectionString )
rxSyncPackages(computeContext=computeContext, verbose=TRUE)
```

### <a name="example-2-restrict-synchronized-packages-by-scope"></a>Beispiel 2. Synchronisierte Pakete durch den Bereich einschränken

In den folgenden Beispielen synchronisieren nur die Pakete im angegebenen Bereich.

```R
#Shared scope
rxSyncPackages(computeContext=computeContext, scope="shared", verbose=TRUE)

#Private scope
rxSyncPackages(computeContext=computeContext, scope="private", verbose=TRUE)
```

### <a name="example-3-restrict-synchronized-packages-by-owner"></a>Beispiel 3. Synchronisierte Pakete vom Besitzer zu beschränken

Im folgenden Beispiel wird veranschaulicht, wie nur die Pakete, die für einen bestimmten Benutzer installiert wurden, synchronisiert wird. In diesem Beispiel wird der Benutzer durch den SQL-Anmeldenamen, identifiziert *"user1"*.

```R
rxSyncPackages(computeContext=computeContext, scope="private", owner = "user1", verbose=TRUE))
```

## <a name="related-resources"></a>Verwandte Ressourcen

[R-Paketverwaltung für SQL Server](install-additional-r-packages-on-sql-server.md)
