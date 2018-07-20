---
title: Tutorial zu RevoScaleR-Funktionen mit SQL Server Machine Learning | Microsoft-Dokumentation
description: Erfahren Sie in diesem Tutorial, wie RevoScaleR-Funktion in SQL Server-Machine Learning mit R unterstützt aktiviert aufrufen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: ac7345e2e4f71db13801e2813ea77aa88f5cdc69
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39084673"
---
# <a name="tutorial-use-revoscaler-r-functions-with-sql-server-data"></a>Tutorial: RevoScaleR die R-Funktionen mit SQL Server-Daten
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

RevoScaleR ist ein Microsoft-R-Paket, verteilte und parallele Verarbeitung für Data Science und Machine learning-Workloads bereitstellen. Für die Entwicklung von R in SQL Server, RevoScaleR ist eine integrierte Core-Paket, mit Funktionen zum Festlegen des computekontexts, Verwalten von Paketen, und noch wichtiger: Arbeiten mit Daten End-to-End, aus der in der Visualisierung und Analyse importieren. Machine Learning-Algorithmen in SQL Server über eine Abhängigkeit für RevoScaleR-Datenquellen verfügen. Die Bedeutung von RevoScaleR ist zu wissen, wann und wie Sie ihre Funktionen aufrufen zu den wesentlichen Qualifikationen. 

Erfahren Sie in diesem Tutorial, wie zum Erstellen von eines remotecomputekontext, Verschieben von Daten zwischen lokalen und remote computekontexte, und führen Sie R-Code auf einem Remotecomputer mit SQL Server. Außerdem erfahren Sie, wie Sie die Analyse und Darstellung von Daten sowohl lokal als auch auf dem Remoteserver, und das Erstellen und Bereitstellen von Modellen.

+ Zuerst werden die Daten aus CSV-Dateien oder XDF-Dateien abgerufen. Importieren von Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe der Funktionen im RevoScaleR-Paket.
+ Das Modelltraining und Bewertung erfolgt über die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] compute Context verwenden. 
+ Verwenden der RevoScaleR-Funktionen zum Erstellen von neuen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabellen, um die Bewertungsergebnisse zu speichern.
+ Erstellen von Plots auf dem Server, und im lokalen computekontext.
+ Trainieren eines Modells für Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank, die Ausführung von R in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz.
+ Extrahieren Sie eine Teilmenge der Daten zu, und speichern Sie sie als XDF-Datei für die erneute Verwendung bei der Analyse auf Ihrer lokalen Arbeitsstation.
+ Abrufen von neuen Daten für die Bewertung, durch Öffnen des ODBC-Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank. Bewertung erfolgt auf der lokalen Arbeitsstation.
+ Erstellen Sie eine benutzerdefinierte R-Funktion, und führen Sie sie auf dem Server-computekontext zum Ausführen einer Simulations.

## <a name="target-audience"></a>Zielgruppe

Dieses Tutorial richtet sich an Datenanalysten oder für Personen, die bereits mit R und Data Science-Aufgaben wie z. B. Übersichten und Modellerstellung vertraut sind. Allerdings wird der gesamte Code bereitgestellt, selbst wenn Sie keine Erfahrung mit R sind, führen Sie den Code und folgen zu können, vorausgesetzt, dass Sie die erforderlichen Server- und Clientumgebungen verfügen.

Sie sollten auch mit vertraut sein [!INCLUDE[tsql](../../includes/tsql-md.md)] Syntax und wissen, wie Sie den Zugriff auf eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank mithilfe von Tools wie diese:

+ [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 
+ Datenbanktools in Visual Studio 
+ Die kostenlose [Mssql-Erweiterung für Visual Studio Code](https://docs.microsoft.com/sql/linux/sql-server-linux-develop-use-vscode).
  
> [!TIP]
> Speichern Sie Ihren R-Arbeitsbereich zwischen den Lektionen, sodass Sie nach einer Unterbrechung problemlos weitermachen können.

## <a name="prerequisites"></a>Erforderliche Komponenten

- **SQL Server mit Unterstützung für R**
  
    Installieren Sie [SQL Server 2017-Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) mit der R-Funktion, oder installieren Sie [SQL Server 2016 R Services (Datenbankintern)](../install/sql-r-services-windows-install.md).

    Stellen Sie sicher, externe Skripts aktiviert sind, Launchpad-Dienst ausgeführt wird und, dass Sie Zugriff auf den Dienst berechtigt.
  
-  **Datenbankberechtigungen**
  
    Für die Durchführung der Abfragen zum Trainieren des Modells benötigen Sie **db_datareader** -Berechtigungen für die Datenbank, in der die Daten gespeichert ist. Um R auszuführen, muss der Benutzer die Berechtigung EXECUTE ANY EXTERNAL SCRIPT haben.

-   **Data Science-Entwicklungscomputer**
  
    Um zwischen lokalen und remote computekontexte hin und her zu wechseln, benötigen Sie zwei Systeme. Local ist in der Regel eine Arbeitsstation mit ausreichend Leistung für Data Science-Workloads. Remote ist in diesem Fall SQL Server 2017 oder SQL Server 2016 mit aktivierter R-Funktion. 
    
    Wechseln von computekontexten beruht darauf, dass die gleiche Version RevoScaleR auf lokale und remote-Systemen mit. Auf einer lokalen Arbeitsstation verwenden, können Sie die RevoScaleR-Pakete und die zugehörigen Anbieter abrufen, indem installieren oder verwenden eine der folgenden: [Data Science-VM in Azure](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/overview), [(kostenlos) mit Microsoft R Client](https://docs.microsoft.com/en-us/machine-learning-server/r-client/what-is-microsoft-r-client), oder [ Microsoft Machine Learning Server (eigenständig)](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-install). Installieren Sie für die Option eigenständigen Server kostenlose Developer Edition wird mit Linux- oder Windows Installer. Sie können auch SQL Server-Setup verwenden, um einem eigenständigen Server installieren.
      
-   **Zusätzliche R-Pakete**
  
    In diesem Tutorial haben Sie die folgenden Pakete installieren: **Dplyr**, **"ggplot2"**, **Ggthemes**, **reshape2**, und **e1071** . Anweisungen sind im Tutorial enthalten.
  
    Alle Pakete müssen an zwei Orten installiert werden: auf der Arbeitsstation für die Entwicklung von R-Lösungen verwendet, und klicken Sie auf dem SQL Server-Computer, auf dem R-Skripts ausgeführt werden. Wenn Sie nicht über die Berechtigung zum Installieren von Paketen auf dem Servercomputer verfügen, bitten Sie einen Administrator. 
    
    **Installieren Sie die Pakete nicht in einer Benutzerbibliothek.** In der R-paketbibliothek, die von der SQL Server-Instanz verwendet wird, müssen die Pakete installiert werden.

## <a name="r-development-tools"></a>R-Entwicklungstools

R-Entwickler verwenden die IDEs in der Regel zum Schreiben und Debuggen von R-Code. Hier sind einige Vorschläge:

- **R Tools für Visual Studio** (RTVS) ist ein kostenloses plug-in, bietet Intellisense, debugging und die Unterstützung für Microsoft r Sie es mit R Server und SQL Server-Machine Learning-Dienste verwenden können. Gehen Sie unter [R Tools for Visual Studio](https://www.visualstudio.com/vs/rtvs/)(R-Tools für Visual Studio), um es herunterzuladen.

- **RStudio** ist eine der beliebtesten Umgebungen für die Entwicklung von R. Weitere Informationen finden Sie unter [ https://www.rstudio.com/products/RStudio/ ](https://www.rstudio.com/products/RStudio/).

- Grundlegende R-Tools (R.exe, RTerm.exe, RScripts.exe) werden auch standardmäßig installiert, bei der Installation von R in SQL Server oder R Client. Wenn Sie keine IDE installieren möchten, können Sie integrierte R-Tools, um den Code in diesem Tutorial auszuführen.

Denken Sie daran, dass RevoScaleR auf lokalen und Remotecomputern erforderlich ist. Sie können nicht in diesem Tutorial mit einer generischen Installation von RStudio oder einer anderen Umgebung, auf denen die Microsoft R-Bibliotheken fehlt, ist abgeschlossen. Weitere Informationen finden Sie unter [Einrichten eines Data Science-Clients](../r/set-up-a-data-science-client.md).

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Lektion 1: Erstellen Sie,-Datenbank und Berechtigungen](deepdive-work-with-sql-server-data-using-r.md)

