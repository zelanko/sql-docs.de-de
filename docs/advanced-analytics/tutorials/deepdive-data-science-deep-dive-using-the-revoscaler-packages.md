---
title: Revoscaler-Funktion Deep-Dive-Tutorial-SQL Server Machine Learning
description: In diesem Tutorial erfahren Sie, wie Sie mit SQL Server Machine Learning R-Integration revoscaler-Funktionen aufzurufen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4db5debf4ba71f29a8870c8674a5422e9ffd334a
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714883"
---
# <a name="tutorial-use-revoscaler-r-functions-with-sql-server-data"></a>Tutorial: Verwenden von revoscaler R-Funktionen mit SQL Server Daten
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[Revoscaler](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) ist ein Microsoft R-Paket, das verteilte und parallele Verarbeitung für Data Science-und Machine Learning-Workloads bereitstellt. Bei der R-Entwicklung in SQL Server ist **revoscaler** eines der integrierten Kernpakete mit Funktionen zum Erstellen von Datenquellen Objekten, zum Einrichten eines computekontexts, zum Verwalten von Paketen und zu den wichtigsten Aufgaben: End-to-End-arbeiten mit Daten, vom Import bis zum Visualisierung und Analyse. Machine Learning Algorithmen in SQL Server eine Abhängigkeit von **revoscaler** -Datenquellen haben. Angesichts der Wichtigkeit von **revoscaler**ist es wichtig, zu wissen, wann und wie seine Funktionen aufgerufen werden. 

In diesem mehrteiligen Tutorial haben Sie eine Reihe von **revoscaler** -Funktionen für Aufgaben eingeführt, die Data Science zugeordnet sind. Im Verfahren erfahren Sie, wie Sie einen remotecomputekontext erstellen, Daten zwischen lokalen und remotecomputekontexten verschieben und R-Code auf einem Remote SQL Server ausführen. Außerdem erfahren Sie, wie Sie Daten sowohl lokal als auch auf dem Remote Server analysieren und darstellen und wie Sie Modelle erstellen und bereitstellen.

## <a name="prerequisites"></a>Vorraussetzungen

+ [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) mit der R-Funktion oder [SQL Server R Services (in-Database)](../install/sql-r-services-windows-install.md)
  
+ [Daten Bank Berechtigungen](../security/user-permission.md) und eine SQL Server Datenbank-Benutzeranmeldung

+ [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)

+ Eine IDE wie rstudio oder das integrierte rgui-Tool, das in R enthalten ist

Um zwischen lokalen und remotecomputekontexten hin-und herwechseln zu können, benötigen Sie zwei Systeme. Local ist in der Regel eine Entwicklungs Arbeitsstation mit einer suffitze Stromversorgung für Data Science Arbeits Auslastungen. Remote ist in diesem Fall SQL Server, wenn die R-Funktion aktiviert ist. 

Das Umschalten von computekontexten ist darauf ausgerichtet, dass die gleiche-Version- **revoscaler** auf lokalen Systemen und Remote Systemen vorhanden ist. Auf einer lokalen Arbeitsstation können Sie die **revoscaler** -Pakete und die zugehörigen Anbieter abrufen, indem Sie Microsoft R Client installieren.

Wenn Sie Client und Server auf demselben Computer platzieren müssen, achten Sie darauf, dass Sie einen zweiten Satz von Microsoft r-Bibliotheken zum Senden eines R-Skripts von einem Remote Client installieren. Verwenden Sie die R-Bibliotheken nicht, die in den Programmdateien der SQL Server Instanz installiert sind. Insbesondere, wenn Sie einen Computer verwenden, benötigen Sie die **revoscaler** -Bibliothek an beiden Speicherorten, um Client-und Server Vorgänge zu unterstützen.

+ C:\programme\microsoft\r Client\R_SERVER\library\RevoScaleR 
+ C:\Programme\Microsoft SQL server\mssql14. MSSQLSERVER\R_SERVICES\library\RevoScaleR

Anweisungen zur Client Konfiguration finden Sie unter [Einrichten eines Data Science Clients für die R-Entwicklung](../r/set-up-a-data-science-client.md).


## <a name="r-development-tools"></a>R-Entwicklungs Tools

R-Entwickler verwenden normalerweise IDES zum Schreiben und Debuggen von R-Code. Hier einige Vorschläge:

- **R Tools für Visual Studio** (Rtvs) ist ein kostenloses Plug-in, das IntelliSense, Debuggen und Unterstützung für Microsoft R bereitstellt. Sie können Sie mit R Server und SQL Server Machine Learning Services verwenden. Gehen Sie unter [R Tools for Visual Studio](https://www.visualstudio.com/vs/rtvs/)(R-Tools für Visual Studio), um es herunterzuladen.

- **RStudio** ist eine der beliebtesten Umgebungen für die Entwicklung von R. Weitere Informationen finden [https://www.rstudio.com/products/RStudio/](https://www.rstudio.com/products/RStudio/)Sie unter.

- Grundlegende r-Tools (r. exe, RTERM. exe, rscripts. exe) werden standardmäßig auch installiert, wenn Sie r in SQL Server oder r-Client installieren. Wenn Sie keine IDE installieren möchten, können Sie die integrierten R-Tools verwenden, um den Code in diesem Tutorial auszuführen.

Beachten Sie, dass **revoscaler** auf lokalen Computern und Remote Computern erforderlich ist. Sie können dieses Tutorial nicht mit einer generischen Installation von rstudio oder einer anderen Umgebung durchführen, in der die Microsoft R-Bibliotheken fehlen. Weitere Informationen finden Sie unter [Einrichten eines Data Science-Clients](../r/set-up-a-data-science-client.md).

## <a name="summary-of-tasks"></a>Zusammenfassung der Tasks

+ Zuerst werden die Daten aus CSV-Dateien oder XDF-Dateien abgerufen. Sie importieren die Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe der Funktionen im **revoscaler** -Paket.
+ Modell Training und-Bewertung werden mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computekontexts ausgeführt. 
+ Verwenden Sie die **revoscaler** -Funktionen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , um neue Tabellen zum Speichern der Bewertungsergebnisse zu erstellen.
+ Erstellen Sie Plots sowohl auf dem Server als auch im lokalen computekontext.
+ Trainieren eines Modells für Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der Datenbank, wobei R in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der-Instanz ausgeführt wird.
+ Extrahieren Sie eine Teilmenge der Daten, und speichern Sie Sie als Xdf-Datei für die erneute Verwendung in der Analyse auf der lokalen Arbeitsstation.
+ Sie erhalten neue Daten für die Bewertung, indem Sie eine ODBC- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verbindung mit der-Datenbank öffnen. Die Bewertung erfolgt auf der lokalen Arbeitsstation.
+ Erstellen Sie eine benutzerdefinierte R-Funktion, und führen Sie Sie im Server-computekontext aus, um eine Simulation auszuführen.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Lektion 1: Create Database und Berechtigungen](deepdive-work-with-sql-server-data-using-r.md)