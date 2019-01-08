---
title: 'RevoScaleR-Funktion – ausführliche Tutorial: SQL Server-Machine Learning'
description: Erfahren Sie in diesem Tutorial, wie RevoScaleR-Funktionen, die mithilfe der SQL Server Machine Learning-R-Integration aufgerufen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 4ce2eea1638c301f85741dc22f7541af0cf7e5d6
ms.sourcegitcommit: 33712a0587c1cdc90de6dada88d727f8623efd11
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2018
ms.locfileid: "53596621"
---
# <a name="tutorial-use-revoscaler-r-functions-with-sql-server-data"></a>Lernprogramm: Verwenden der RevoScaleR-R-Funktionen mit SQL Server-Daten
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) ist eine verteilte Bereitstellung von Microsoft R-Paket und die parallele Verarbeitung für Data Science und Machine learning-Workloads. Für die Entwicklung von R in SQL Server **RevoScaleR** ist eine der wichtigsten integrierten Pakete mit Funktionen zum Erstellen von Datenquellenobjekten, Festlegen des computekontexts, Verwalten von Paketen, und noch wichtiger: Arbeiten mit Daten End-to-End von in die Visualisierung und Analyse importieren. Machine Learning-Algorithmen in SQL Server verfügen über eine Abhängigkeit auf **RevoScaleR** -Datenquellen. Angesichts der Bedeutung von **RevoScaleR**, herauszufinden, wann und wie Sie ihre Funktionen aufrufen sind von entscheidender Bedeutung. 

In diesem mehrteiligen Tutorial haben Sie eine Einführung in einen Bereich von **RevoScaleR** Funktionen für Aufgaben im Zusammenhang mit Data Science. Klicken Sie im Prozess erfahren Sie, wie zum Erstellen von eines remotecomputekontext, Verschieben von Daten zwischen lokalen und remote computekontexte, und führen Sie R-Code auf einem Remotecomputer mit SQL Server. Außerdem erfahren Sie, wie Sie die Analyse und Darstellung von Daten sowohl lokal als auch auf dem Remoteserver, und das Erstellen und Bereitstellen von Modellen.

## <a name="prerequisites"></a>Erforderliche Komponenten

+ [SQL Server 2017-Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) mit der R-Funktion oder [SQL Server 2016 R Services (Datenbankintern)](../install/sql-r-services-windows-install.md)
  
+ [Datenbankberechtigungen](../security/user-permission.md) und eine SQL Server-Datenbank-Benutzeranmeldung

+ [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)

+ Eine IDE wie RStudio oder des integrierten RGUI-Tools, die in R enthalten ist

Um zwischen lokalen und remote computekontexte hin und her zu wechseln, benötigen Sie zwei Systeme. Local ist in der Regel eine Arbeitsstation mit ausreichend Leistung für Data Science-Workloads. Remote ist in diesem Fall SQL Server 2017 oder SQL Server 2016 mit aktivierter R-Funktion. 

Wechseln von computekontexten beruht darauf, dass Sie mit der gleichen-Version **RevoScaleR** auf lokale und remote-Systemen. Sie können auf einer lokalen Arbeitsstation Abrufen der **RevoScaleR** Pakete und die zugehörigen Anbieter durch die Installation von Microsoft R Client.

Wenn Sie Client und Server auf demselben Computer platzieren möchten, achten Sie darauf, dass Sie einen zweiten Satz von Microsoft R-Bibliotheken für das Senden von R-Skript von einem "remote" Client installieren. Verwenden Sie nicht die R-Bibliotheken, die in die Programmdateien des SQL Server-Instanz installiert sind. Insbesondere wenn Sie einen Computer verwenden, müssen Sie die **RevoScaleR** Bibliothek in beiden der folgenden Speicherorte auf Client- und Servervorgänge zu unterstützen.

+ C:\Programme\Microsoft Files\Microsoft\R Client\R_SERVER\library\RevoScaleR 
+ C:\Programme\Microsoft c:\Programme\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES\library\RevoScaleR

Anweisungen zur Clientkonfiguration von, finden Sie unter [richten Sie eine Data Science-Client für R-Entwicklungstools](../r/set-up-a-data-science-client.md).


## <a name="r-development-tools"></a>R-Entwicklungstools

R-Entwickler verwenden die IDEs in der Regel zum Schreiben und Debuggen von R-Code. Hier einige Vorschläge:

- **R Tools für Visual Studio** (RTVS) ist ein kostenloses plug-in, bietet Intellisense, debugging und Unterstützung für Microsoft-R. Sie können es mit R Server und SQL Server-Machine Learning-Dienste verwenden. Gehen Sie unter [R Tools for Visual Studio](https://www.visualstudio.com/vs/rtvs/)(R-Tools für Visual Studio), um es herunterzuladen.

- **RStudio** ist eine der beliebtesten Umgebungen für die Entwicklung von R. Weitere Informationen finden Sie unter [ https://www.rstudio.com/products/RStudio/ ](https://www.rstudio.com/products/RStudio/).

- Grundlegende R-Tools (R.exe, RTerm.exe, RScripts.exe) werden auch standardmäßig installiert, bei der Installation von R in SQL Server oder R Client. Wenn Sie keine IDE installieren möchten, können Sie integrierte R-Tools, um den Code in diesem Tutorial auszuführen.

Zur Erinnerung: **RevoScaleR** ist auf lokalen und Remotecomputern erforderlich. Sie können nicht in diesem Tutorial mit einer generischen Installation von RStudio oder einer anderen Umgebung, auf denen die Microsoft R-Bibliotheken fehlt, ist abgeschlossen. Weitere Informationen finden Sie unter [Einrichten eines Data Science-Clients](../r/set-up-a-data-science-client.md).

## <a name="summary-of-tasks"></a>Zusammenfassung der Aufgaben

+ Zuerst werden die Daten aus CSV-Dateien oder XDF-Dateien abgerufen. Importieren von Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit den Funktionen in der **RevoScaleR** Paket.
+ Das Modelltraining und Bewertung erfolgt über die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] compute Context verwenden. 
+ Verwendung **RevoScaleR** Funktionen zum Erstellen von neuen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabellen, um die Bewertungsergebnisse zu speichern.
+ Erstellen von Plots auf dem Server, und im lokalen computekontext.
+ Trainieren eines Modells für Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank, die Ausführung von R in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz.
+ Extrahieren Sie eine Teilmenge der Daten zu, und speichern Sie sie als XDF-Datei für die erneute Verwendung bei der Analyse auf Ihrer lokalen Arbeitsstation.
+ Abrufen von neuen Daten für die Bewertung, durch Öffnen des ODBC-Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank. Bewertung erfolgt auf der lokalen Arbeitsstation.
+ Erstellen Sie eine benutzerdefinierte R-Funktion, und führen Sie sie auf dem Server-computekontext zum Ausführen einer Simulations.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Lektion 1: Erstellen von Datenbanken und Berechtigungen](deepdive-work-with-sql-server-data-using-r.md)