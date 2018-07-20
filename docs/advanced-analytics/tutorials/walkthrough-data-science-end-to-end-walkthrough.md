---
title: End-to-End-Data Science Walkthrough für R und SQL Server | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 3d4f38fd424c881392d48b0a6a24feb7f7e27ee0
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39086502"
---
# <a name="end-to-end-data-science-walkthrough-for-r-and-sql-server"></a>End-to-End-Data Science Walkthrough für R und SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In dieser exemplarischen Vorgehensweise entwickeln Sie eine End-to-End-Lösung für die vorhersagemodellierung basierend auf der Unterstützung von R-Funktionen in SQL Server 2016 oder SQL Server 2017.

Diese exemplarische Vorgehensweise basiert auf einem bekannten öffentlichen Dataset, dem Dataset New York City-Taxi. Sie verwenden eine Kombination aus R-Code [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Daten und benutzerdefinierten SQL-Funktionen ein klassifizierungsmodells des Typs zu erstellen, der die Wahrscheinlichkeit angibt, dass der Treiber ein Trinkgeld für eine bestimmte taxifahrt erhalten kann. Sie wird auch Ihr R-Modell zum Bereitstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Server-Daten zum Generieren von Bewertungen auf Grundlage des Modells verwenden.

In diesem Beispiel kann auf alle möglichen realen Probleme, z. B. Vorhersagen der Kundenreaktionen auf Verkaufsaktionen oder die Vorhersage der Ausgaben oder die Teilnahme an Ereignisse erweitert werden. Da das Modell aus einer gespeicherten Prozedur aufgerufen werden kann, können Sie einfach in eine Anwendung einbetten.

Die exemplarische Vorgehensweise ist darauf ausgelegt, R-Entwicklern eine Einführung [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], R wird verwendet, wo immer dies möglich. Dies bedeutet jedoch nicht, dass R unbedingt das beste Tool für jede Aufgabe ist. In vielen Fällen stellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine bessere Leistung bereit, besonders für Aufgaben wie Datenaggregation und Featureentwicklung.  Solche Aufgaben profitieren besonders von neuen Funktionen in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], wie z.B. von speicheroptimierten Columnstore-Indizes. Wir versuchen, nebenbei auf mögliche Optimierungen hinweisen.

## <a name="target-audience"></a>Zielgruppe

Diese exemplarische Vorgehensweise ist für R- oder SQL-Entwickler vorgesehen. Sie bietet eine Einführung in die Integration von R in Unternehmensworkflows mithilfe von [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].  Sie sollten mit der Datenbankvorgänge, z. B. das Erstellen von Datenbanken und Tabellen, Importieren von Daten und Ausführen von Abfragen vertraut sein.

+ Alle SQL und R-Skripts sind enthalten.
+ Sie müssen möglicherweise Zeichenfolgen in den Skripts zum Ausführen in Ihrer Umgebung zu ändern. Hierzu können Sie mit einem beliebigen Codeeditor, z. B. [Visual Studio Code](https://code.visualstudio.com/Download).

## <a name="prerequisites"></a>Erforderliche Komponenten

Es wird empfohlen, dass Sie in dieser exemplarischen Vorgehensweise auf einem Laptop oder einem anderen Computer, die die Microsoft R-Bibliotheken, die installiert werden. Sie müssen möglicherweise, sich im selben Netzwerk, eine Verbindung mit einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Computer mit SQL Server und die R-Sprache aktiviert.

Sie können die exemplarische Vorgehensweise ausführen, auf einem Computer, die beides aufweist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und ein R-Entwicklungsumgebung, aber es wird nicht empfohlen, diese Konfiguration für eine produktionsumgebung.

Wenn Sie R-Befehle von einem Remotecomputer, z.B. einem Laptop oder einem anderen Computer im Netzwerk ausführen möchten, müssen Sie die Microsoft R Open-Bibliotheken installieren. Sie können entweder Microsoft R Client oder Microsoft R Server installieren. Der Remotecomputer muss in der Lage, Herstellen einer Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz.

Wenn Sie Client und Server auf demselben Computer platzieren möchten, achten Sie darauf, dass Sie einen separaten Satz von Microsoft R-Bibliotheken für die Verwendung beim Senden von R-Skript von einem "remote" Client installieren. Verwenden Sie nicht die R-Bibliotheken, die installiert werden für die Verwendung von SQL Server-Instanz für diesen Zweck.

## <a name="add-r-to-sql-server"></a>Hinzufügen von R mit SQLServer

Sie benötigen Zugriff auf eine Instanz von SQL Server mit Unterstützung für R installiert. In dieser exemplarischen Vorgehensweise wurde ursprünglich für SQL Server 2016 entwickelt und auf 2017 getestet werden, damit Sie eine der folgenden SQL Server-Versionen verwenden können sollen. (Es gibt einige geringfügige Unterschiede in der RevoScaleR-Funktionen zwischen den Versionen.)

+ [Installieren von SQL Server 2017-Machine-Learning-Dienste](../install/sql-machine-learning-services-windows-install.md)
+ [Installieren von SQL Server 2016 R Services](../install/sql-r-services-windows-install.md).

## <a name="install-an-r-development-environment"></a>Installieren einer R-Entwicklungsumgebung

In dieser exemplarischen Vorgehensweise wird empfohlen, dass Sie eine R-Entwicklungsumgebung verwenden. Hier sind einige Vorschläge:

- **R Tools für Visual Studio** (RTVS) ist ein kostenloses plug-in, bietet Intellisense, debugging und die Unterstützung für Microsoft r Sie es mit R Server und SQL Server-Machine Learning-Dienste verwenden können. Gehen Sie unter [R Tools for Visual Studio](https://www.visualstudio.com/vs/rtvs/)(R-Tools für Visual Studio), um es herunterzuladen.

- **Microsoft R Client** ist ein schlankes Entwicklungstool, die Entwicklung in R mithilfe der RevoScaleR-Paket unterstützt. Unter [Erste Schritte mit Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)können Sie es herunterladen.

- **RStudio** ist eine der beliebtesten Umgebungen für die Entwicklung von R. Weitere Informationen finden Sie unter [ https://www.rstudio.com/products/RStudio/ ](https://www.rstudio.com/products/RStudio/).

    Sie können nicht in diesem Tutorial mit einer generischen Installation von RStudio oder einer anderen Umgebung abschließen; Sie müssen auch die R-Pakete und verbindungsbibliotheken für Microsoft R Open installieren. Weitere Informationen finden Sie unter [Einrichten eines Data Science-Clients](../r/set-up-a-data-science-client.md).

- Grundlegende R-Tools (R.exe, RTerm.exe, RScripts.exe) werden auch standardmäßig installiert, bei der Installation von R in SQL Server oder R Client. Wenn Sie keine IDE installieren möchten, können Sie diese Tools verwenden.

## <a name="get-permissions-on-the-sql-server-instance-and-database"></a>Abrufen von Berechtigungen für die SQL Server-Instanz und Datenbank

Für die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zum Ausführen von Skripts und Daten hochzuladen, müssen Sie einen gültigen Anmeldenamen haben, auf dem Datenbankserver.  Sie können entweder einen SQL-Anmeldenamen oder die integrierte Windows-Authentifizierung verwenden. Bitten Sie den Datenbankadministrator so konfigurieren Sie die folgenden Berechtigungen für das Konto in der Datenbank, in dem Sie r verwenden

- Erstellen von Datenbanken, Tabellen, Funktionen und gespeicherten Prozeduren
- Schreiben von Daten in Tabellen
- Möglichkeit zum Ausführen von R-Skript (`GRANT EXECUTE ANY EXTERNAL SCRIPT to <user>`)

In dieser exemplarischen Vorgehensweise haben wir die SQL-Anmeldung verwendet **RTestUser**. Im Allgemeinen wird empfohlen, dass Sie die integrierte Windows-Authentifizierung verwenden, mit der SQL-Anmeldung ist jedoch einfacher für einige Demozwecke zu nutzen.

## <a name="next-steps"></a>Nächste Schritte

[Vorbereiten der Daten mithilfe von PowerShell](walkthrough-prepare-the-data.md)
