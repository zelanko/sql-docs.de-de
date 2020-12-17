---
title: Detailliertes RevoScaleR-Tutorial
description: In dieser Tutorialreihe erfahren Sie, wie Sie RevoScaleR-Funktionen mithilfe der R-Integration von SQL Server Machine Learning Services aufrufen.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15'
ms.openlocfilehash: 9d7300acb587dd25c294918fe5ae3a6d6a90ddbc
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97470571"
---
# <a name="tutorial-use-revoscaler-r-functions-with-sql-server-data"></a>Tutorial: Verwenden von RevoScaleR-Funktionen für R mit SQL Server-Daten
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

In diesem mehrteiligen Tutorialreihe lernen Sie einige **RevoScaleR**-Funktionen für Data Science-Aufgaben kennen. Dabei erfahren Sie, wie Sie einen Remotecomputekontext erstellen, Daten zwischen einem lokalen und einem Remotecomputekontext verschieben und R-Code auf einer Remoteinstanz von SQL Server ausführen. Außerdem lernen Sie, wie Sie Daten lokal und auf einem Remoteserver analysieren und zeichnen sowie wie Sie Modelle erstellen und bereitstellen.

[RevoScaleR](/machine-learning-server/r-reference/revoscaler/revoscaler) ist ein R-Paket von Microsoft, das die verteilte und parallele Verarbeitung für Data Science- und Machine Learning-Workloads bereitstellt. Für die R-Entwicklung in SQL Server stellt **RevoScaleR** eines der wichtigsten integrierten Pakete dar. Es enthält Funktionen zum Erstellen von Datenquellenobjekten, zum Einrichten eines Computekontexts, zum Verwalten von Paketen und vor allem zur End-to-End-Verarbeitung von Daten, vom Import über die Visualisierung bis hin zur Analyse. Machine Learning-Algorithmen in SQL Server weisen eine Abhängigkeit von **RevoScaleR**-Datenquellen auf. Angesichts dieses Stellenwerts ist es also wichtig zu wissen, wann und wie **RevoScaleR**-Funktionen aufgerufen werden. 

## <a name="prerequisites"></a>Voraussetzungen

+ [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) mit der R-Funktion oder [SQL Server R Services (datenbankintern)](../install/sql-r-services-windows-install.md)
  
+ [Datenbankberechtigungen](../security/user-permission.md) und eine Benutzeranmeldung für SQL Server-Datenbank

+ [SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md)

+ Eine IDE wie z. B. RStudio oder das in R enthaltene integrierte RGUI-Tool

Sie benötigen zwei Systeme, damit Sie zwischen dem lokalen und dem Remotecomputekontext hin- und herwechseln können. Das lokale System ist in der Regel eine Entwicklungsarbeitsstation mit ausreichender Leistung für Data Science-Workloads. Den Remotekontext stellt in diesem Fall SQL Server mit aktivierter R-Funktion dar. 

Das Wechseln zwischen den Computekontexten ist nur möglich, wenn auf dem lokalen und dem Remotesystem dieselbe Version von **RevoScaleR** ausgeführt wird. Auf einer lokalen Arbeitsstation erhalten Sie die **RevoScaleR**-Pakete und zugehörigen Anbieter, indem Sie Microsoft R Client installieren.

Befinden sich Client und Server notwendigerweise auf demselben Computer, müssen Sie einen zweiten Satz Microsoft R-Bibliotheken installieren, um R-Skripts von einem Remoteclient senden zu können. Verwenden Sie nicht die R-Bibliotheken, die in der SQL Server-Instanz unter „Programme“ installiert sind. Insbesondere, wenn Sie nur einen Computer verwenden, benötigen Sie die **RevoScaleR**-Bibliothek an beiden der folgenden Speicherorten, um Client- und Servervorgänge zu unterstützen:

+ C:\Programme\Microsoft\R Client\R_SERVER\library\RevoScaleR 
+ C:\Programme\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\RevoScaleR

Anweisungen zur Clientkonfiguration finden Sie unter [Einrichten eines Data Science-Clients für die Entwicklung in R](../r/set-up-a-data-science-client.md).


## <a name="r-development-tools"></a>R-Entwicklungstools

R-Entwickler verwenden zum Schreiben und Debuggen von R-Code in der Regel IDEs. Hier einige Vorschläge:

- **R-Tools für Visual Studio (RTVS)** ist ein kostenloses Plug-In, das IntelliSense, Debugging sowie Unterstützung für Microsoft R bietet. Sie können es sowohl mit R Server als auch mit SQL Server Machine Learning Services verwenden. Gehen Sie unter [R Tools for Visual Studio](https://marketplace.visualstudio.com/items?itemName=MikhailArkhipov007.RTVS2019)(R-Tools für Visual Studio), um es herunterzuladen.

- **RStudio** ist eine der beliebtesten Umgebungen für die Entwicklung von R. Weitere Informationen finden Sie unter [https://www.rstudio.com/products/RStudio/](https://www.rstudio.com/products/RStudio/).

- Grundlegende R-Tools (R.exe, RTerm.exe, RScripts.exe) werden auch standardmäßig bei der Installation von R in SQL Server oder R Client installiert. Wenn Sie keine IDE installieren möchten, können Sie mit integrierten R-Tools den Code in diesem Tutorial ausführen.

Denken Sie daran, dass Sie **RevoScaleR** auf dem lokalen und dem Remotecomputer ausführen müssen. Sie können dieses Tutorial nicht mit einer generischen Installation von RStudio oder einer anderen Umgebung ohne Microsoft R-Bibliotheken durchführen. Weitere Informationen finden Sie unter [Einrichten eines Data Science-Clients](../r/set-up-a-data-science-client.md).

## <a name="summary-of-tasks"></a>Zusammenfassung der Aufgaben

+ Zuerst werden die Daten aus CSV-Dateien oder XDF-Dateien abgerufen. Die Daten werden mithilfe der Funktionen im **RevoScaleR**-Paket in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] importiert.
+ Das Trainieren und Bewerten des Modells erfolgt mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Computekontexts. 
+ Sie erstellen neue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabellen mithilfe der **RevoScaleR**-Funktionen, um die Bewertungsergebnisse zu speichern.
+ Sie erstellen Zeichnungen auf dem Server und im lokalen Computekontext.
+ Sie trainieren ein Modell mit Daten der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank, und führen R in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz aus.
+ Sie extrahieren eine Teilmenge der Daten und speichern sie als XDF-Datei für die erneute Verwendung bei der Analyse auf Ihrer lokalen Arbeitsstation.
+ Sie erhalten neue Daten für die Bewertung, indem Sie eine ODBC-Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank herstellen. Die Bewertung wird auf der lokalen Arbeitsstation ausgeführt.
+ Sie erstellen eine benutzerdefinierte R-Funktion und führen sie im Computekontext des Servers aus, um eine Simulation durchzuführen.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Tutorial 1: Erstellen einer Datenbank und von Berechtigungen](deepdive-work-with-sql-server-data-using-r.md)