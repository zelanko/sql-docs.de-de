---
title: R-Paket Synchronisierung aus dem Dateisystem
description: Aktualisieren Sie R-Bibliotheken auf SQL Server mit neueren Versionen, die auf dem Dateisystem installiert sind.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4e0b6133bcecc553934cd657785ea9ee765c6fd9
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715073"
---
# <a name="r-package-synchronization-for-sql-server"></a>R-Paket Synchronisierung für SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Die in SQL Server 2017 enthaltene Version von revoscaler bietet die Möglichkeit, Sammlungen von R-Paketen zwischen dem Dateisystem und der Instanz und Datenbank zu synchronisieren, in der Pakete verwendet werden.

Diese Funktion wurde bereitgestellt, um das Sichern von R-Paket Auflistungen, die SQL Server Datenbanken zugeordnet sind, zu vereinfachen. Mit diesem Feature kann ein Administrator nicht nur die Datenbank, sondern auch alle R-Pakete wiederherstellen, die von Datenanalysten verwendet wurden, die in dieser Datenbank arbeiten.

In diesem Artikel wird die Paket Synchronisierungs Funktion beschrieben und erläutert, wie Sie die Funktion [rxsyncpackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsyncpackages) verwenden, um die folgenden Aufgaben auszuführen:

+ Synchronisieren einer Liste von Paketen für eine gesamte SQL Server Datenbank

+ Synchronisieren von Paketen, die von einem einzelnen Benutzer oder einer Benutzergruppe verwendet werden

+ Wenn ein Benutzer zu einer anderen SQL Server wechselt, können Sie eine Sicherung der Arbeits Datenbank des Benutzers erstellen und diese auf dem neuen Server wiederherstellen, und die Pakete für den Benutzer werden im Dateisystem auf dem neuen Server installiert, wie von R erforderlich.

Beispielsweise können Sie die Paket Synchronisierung in folgenden Szenarien verwenden:

+ Der Datenbankadministrator hat eine Instanz von SQL Server auf einem neuen Computer wieder hergestellt und fordert die Benutzer auf, von ihren R `rxSyncPackages` -Clients eine Verbindung herzustellen und auszuführen, um die Pakete zu aktualisieren und wiederherzustellen.

+ Sie sind der Ansicht, dass ein R-Paket im Dateisystem beschädigt `rxSyncPackages` ist, sodass Sie auf dem SQL Server ausführen.

## <a name="requirements"></a>Anforderungen

Bevor Sie die Paket Synchronisierung verwenden können, müssen Sie über die entsprechende Version von Microsoft R oder Machine Learning Server verfügen. Diese Funktion wird in Microsoft R Version 9.1.0 oder höher bereitgestellt. 

Außerdem müssen Sie das [Paket Verwaltungs Feature](r-package-how-to-enable-or-disable.md) auf dem Server aktivieren.

### <a name="determine-whether-your-server-supports-package-management"></a>Bestimmen, ob der Server die Paketverwaltung unterstützt

Diese Funktion ist in SQL Server 2017 CTP 2 oder höher verfügbar.

Sie können diese Funktion einer Instanz von SQL Server 2016 hinzufügen, indem Sie die-Instanz so aktualisieren, dass Sie die neueste Version von Microsoft R verwendet. Weitere Informationen finden [Sie unter Verwenden von sqlbindr. exe zum Aktualisieren von SQL Server R Services](../install/upgrade-r-and-python.md).

### <a name="enable-the-package-management-feature"></a>Aktivieren der Paket Verwaltungsfunktion

Damit die Paket Synchronisierung verwendet werden kann, muss das neue Paket Verwaltungs Feature für die SQL Server-Instanz und für einzelne Datenbanken aktiviert werden. Weitere Informationen finden Sie unter [Aktivieren oder Deaktivieren der Paketverwaltung für SQL Server](r-package-how-to-enable-or-disable.md).

1. Der Server Administrator aktiviert das Feature für die SQL Server Instanz.
2. Der Administrator erteilt einzelnen Benutzern mithilfe von Daten bankrollen die Möglichkeit, R-Pakete mithilfe von Daten bankrollen zu installieren oder freizugeben.

Wenn dies der Fall ist, können Sie mithilfe von revoscaler-Funktionen (z. [b. rxinstallpackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) ) Pakete in einer-Datenbank installieren.  Informationen zu Benutzern und den Paketen, die Sie verwenden können, werden in der SQL Server Instanz gespeichert. 

Wenn Sie ein neues Paket mit den Paketverwaltungsfunktionen hinzufügen, werden sowohl die Datensätze in SQL Server als auch das Dateisystem aktualisiert. Diese Informationen können verwendet werden, um Paketinformationen für die gesamte Datenbank wiederherzustellen.

### <a name="permissions"></a>Berechtigungen

+ Die Person, die die Paket Synchronisierungs Funktion ausführt, muss ein Sicherheits Prinzipal auf der SQL Server Instanz und der Datenbank sein, die die Pakete enthält.

+ Der Aufrufer der Funktion muss Mitglied einer dieser Paket Verwaltungs Rollen sein: **rpkgs-Shared** oder **rpkgs-private**.

+ Zum Synchronisieren von als frei **gegeben**markierten Paketen muss die Person, die die Funktion ausgeführt hat, Mitglied der **rpkgs-Shared-** Rolle sein, und die Pakete, die verschoben werden, müssen in einer freigegebenen Bereichs Bibliothek installiert sein.

+ Zum Synchronisieren von als **Privat**markierten Paketen muss entweder der Besitzer des Pakets oder der Administrator die Funktion ausführen, und die Pakete müssen privat sein.

+ Um Pakete im Namen anderer Benutzer zu synchronisieren, muss der Besitzer Mitglied der Daten Bank Rolle **db_owner** sein.

## <a name="how-package-synchronization-works"></a>Funktionsweise der Paket Synchronisierung

Rufen Sie zum Verwenden der Paket Synchronisierung [rxsyncpackages](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsyncpackages)auf, bei dem es sich um eine neue Funktion in [revoscaler](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)handelt. 

Für jeden-Rückruf `rxSyncPackages`müssen Sie eine SQL Server Instanz und eine-Datenbank angeben. Listen Sie dann entweder die zu synchronisierenden Pakete auf, oder geben Sie den Paketbereich an.

1. Erstellen Sie den SQL Server computekontext mithilfe der `RxInSqlServer` -Funktion. Wenn Sie keinen computekontext angeben, wird der aktuelle computekontext verwendet.

2. Geben Sie den Namen einer Datenbank auf der Instanz im angegebenen computekontext an. Pakete werden pro Datenbank synchronisiert.

3. Geben Sie die zu synchronisierenden Pakete mithilfe des Bereichs Arguments an.

    Wenn Sie den **privaten** Bereich verwenden, werden nur Pakete synchronisiert, die dem angegebenen Besitzer gehören. Wenn Sie den frei **gegebenen** Bereich angeben, werden alle nicht privaten Pakete in der Datenbank synchronisiert. 
    
    Wenn Sie die Funktion ausführen, ohne entweder einen **privaten** oder einen frei **gegebenen** Bereich anzugeben, werden alle Pakete synchronisiert.

4. Wenn der Befehl erfolgreich ausgeführt wird, werden der Datenbank vorhandene Pakete im Dateisystem mit dem angegebenen Gültigkeitsbereich und Besitzer hinzugefügt.

    Wenn das Dateisystem beschädigt ist, werden die Pakete auf der Grundlage der in der Datenbank verwalteten Liste wieder hergestellt.

    Wenn das Paket Verwaltungs Feature in der Zieldatenbank nicht verfügbar ist, wird ein Fehler ausgelöst: "Die Paket Verwaltungsfunktion ist entweder auf dem SQL Server nicht aktiviert, oder die Version ist zu alt".

### <a name="example-1-synchronize-all-package-by-database"></a>Beispiel 1. Alle Pakete nach Datenbank synchronisieren

In diesem Beispiel werden alle neuen Pakete aus dem lokalen Dateisystem abgerufen, und die Pakete werden in der-Datenbank [TestDB] installiert. Da kein Besitzer spezifisch ist, enthält die Liste alle Pakete, die für private und freigegebene Bereiche installiert wurden.

```R
connectionString <- "Driver=SQL Server;Server=myServer;Database=TestDB;Trusted_Connection=True;"
computeContext <- RxInSqlServer(connectionString = connectionString )
rxSyncPackages(computeContext=computeContext, verbose=TRUE)
```

### <a name="example-2-restrict-synchronized-packages-by-scope"></a>Beispiel 2. Synchronisierte Pakete nach Gültigkeitsbereich einschränken

In den folgenden Beispielen werden nur die Pakete im angegebenen Bereich synchronisiert.

```R
#Shared scope
rxSyncPackages(computeContext=computeContext, scope="shared", verbose=TRUE)

#Private scope
rxSyncPackages(computeContext=computeContext, scope="private", verbose=TRUE)
```

### <a name="example-3-restrict-synchronized-packages-by-owner"></a>Beispiel 3: Synchronisierte Pakete nach Besitzer einschränken

Im folgenden Beispiel wird veranschaulicht, wie nur die Pakete synchronisiert werden, die für einen bestimmten Benutzer installiert wurden. In diesem Beispiel wird der Benutzer durch den SQL-Anmelde Namen *User1*identifiziert.

```R
rxSyncPackages(computeContext=computeContext, scope="private", owner = "user1", verbose=TRUE))
```

## <a name="related-resources"></a>Verwandte Ressourcen

[R-Paketverwaltung für SQL Server](install-additional-r-packages-on-sql-server.md)
