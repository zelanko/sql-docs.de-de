---
title: Erweiterbarkeitsarchitektur
description: In diesem Artikel wird die Architektur des Erweiterbarkeitsframeworks zum Ausführen eines externen Skripts wie R oder Python auf SQL Server beschrieben.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/04/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: fcdb92f92ffb8239a6cf20b0f39dfb8f546b521a
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727689"
---
# <a name="extensibility-architecture-in-sql-server-machine-learning-services"></a>Erweiterbarkeitsarchitektur in SQL Server-Machine Learning Services 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

SQL Server verfügt über ein Erweiterungsframework zum Ausführen eines externes Skripts wie R oder Python auf dem Server. Das Skript wird in einer Language Runtime-Umgebung als Erweiterung der Haupt-Datenbank-Engine ausgeführt.

## <a name="background"></a>Hintergrund

Das Erweiterbarkeitsframework wurde in SQL Server 2016 zur Unterstützung der R-Runtime eingeführt. Python wird von SQL Server 2017 und höher unterstützt.

Der Zweck des Erweiterbarkeitsframeworks besteht darin, eine Schnittstelle zwischen SQL Server und Data Science-Sprachen wie R und Python bereitzustellen. Ziel dabei ist es, eine möglichst reibungslose Migration von Data-Science-Lösungen in die Produktion zu gewährleisten und die während des Entwicklungsprozesses verfügbar gemachten Daten zu schützen. Durch Ausführen einer vertrauenswürdigen Skriptsprache innerhalb eines von SQL Server verwalteten sicheren Frameworks können Datenbankadministratoren die Sicherheit aufrechterhalten und gleichzeitig Datenanalysten den Zugriff auf Unternehmensdaten ermöglichen.

Im folgenden Diagramm werden die Möglichkeiten und Vorteile der erweiterbaren Architektur visuell beschrieben.

  ![Ziele der Integration in SQL Server](../media/ml-service-value-add.png "Mehrwert durch Machine Learning Services")

Ein externes Skript kann durch Aufrufen einer gespeicherten Prozedur ausgeführt werden, und die Ergebnisse werden als tabellarische Ergebnisse direkt an SQL Server zurückgegeben. Dies vereinfacht das Generieren oder Verwenden von Machine Learning aus einer beliebigen Anwendung, die eine SQL-Abfrage senden und die Ergebnisse verarbeiten kann.

+ Die Ausführung externer Skripts unterliegt der Datensicherheit von SQL Server. Ein Benutzer, der ein externes Skript ausführt, kann nur auf Daten zugreifen, die gleichzeitig in einer SQL-Abfrage verfügbar sind. Wenn eine Abfrage aufgrund unzureichender Berechtigungen fehlschlägt, kann ein Skript, das vom gleichen Benutzer ausgeführt wird, aus demselben Grund ebenfalls fehlschlagen. Die SQL Server-Sicherheit wird auf der Ebene der Tabelle, Datenbank und Instanz erzwungen. Datenbankadministratoren können den Benutzerzugriff, die von externen Skripts verwendeten Ressourcen und die dem Server hinzugefügten externen Codebibliotheken verwalten.  

+ Skalierungs-und Optimierungsmöglichkeiten bieten Vorteile in zweierlei Hinsicht: Vorteile durch die Datenbankplattform (ColumnStore-Indizes, [Ressourcenkontrolle](../../advanced-analytics/r/resource-governance-for-r-services.md)) und erweiterungsspezifische Vorteile, z. B. bei Verwendung von Microsoft-Bibliotheken für R und Python für Data-Science- Modelle. Bei R handelt es sich um einen einzelnen Thread. RevoScaleR-Funktionen werden hingegen mit mehreren Threads ausgeführt und können eine Workload über mehrere Kerne verteilen.

+ Für die Bereitstellung werden SQL Server-Methoden verwendet. Dies können gespeicherte Prozeduren sein, die ein externes Skript oder eingebettete SQL- bzw. T-SQL-Abfragen zum Aufrufen von Funktionen wie PREDICT umfassen, um Ergebnisse von auf dem Server verbliebenen Prognosemodellen zurückzugeben.

+ Entwickler mit fundierten Kenntnissen in bestimmten Tools und IDEs können Code in diese Tools schreiben und den Code dann in SQL Server portieren.

## <a name="architecture-diagram"></a>Architekturdiagramm

Die Architektur ist so konzipiert, dass externe Skripts in einem separaten Prozess von SQL Server ausgeführt werden, jedoch mit Komponenten, die intern die Kette von Anforderungen für Daten und Vorgänge auf SQL Server verwalten. Abhängig von der Version von SQL Server enthalten die unterstützten Spracherweiterungen [R](extension-r.md), [Python](extension-python.md) und Sprachen von Drittanbietern wie Java und .NET.

  ***Komponentenarchitektur in Windows:***
  
  ![Windows-Komponentenarchitektur](../media/generic-architecture-windows.png "Komponentenarchitektur")
  
  ***Komponentenarchitektur in Linux:***

  ![Linux-Komponentenarchitektur](../media/generic-architecture-linux.png "Komponentenarchitektur")
  
Zu den Komponenten gehören ein **Launchpaddienst**, der zum Aufrufen externer Runtimes und bibliotheksspezifischer Logik zum Laden von Interpretern und Bibliotheken verwendet wird. Das Startprogramm lädt eine Language Runtime sowie alle proprietären Module. Wenn der Code z. B. RevoScaleR-Funktionen enthält, wird ein RevoScaleR-Interpreter geladen. **BxlServer** und **SQL Satellite** verwalten die Kommunikation mit SQL Server und die Datenübertragung. 

Unter Linux verwendet SQL einen **launchpadd**-Dienst, um mit einem separaten Launchpad-Prozess für jeden Benutzer zu kommunizieren.

<a name="launchpad"></a>

## <a name="launchpad"></a>Launchpad

[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] ist ein Dienst, der die Ausführung externer Skripts verwaltet und unterstützt, ganz ähnlich wie die Volltextindizierung und der Abfragedienst einen separaten Host für die Verarbeitung von Volltextabfragen starten. Der Launchpaddienst startet nur vertrauenswürdige Startprogramme, die von Microsoft veröffentlicht wurden oder die durch Microsoft zertifiziert wurden, da sie die Anforderungen für Leistung und Ressourcenverwaltung erfüllen.

| Vertrauenswürdige Startprogramme | Erweiterung | SQL Server-Versionen |
|-------------------|-----------|---------------------|
| „RLauncher.dll“ für die R-Sprache für Windows | [R-Erweiterung](extension-r.md) | SQL Server 2016 und höher |
| „Pythonlauncher.dll“ für Python 3.5 für Windows | [Python-Erweiterung](extension-python.md) | SQL Server 2017 und höher |
| „RLauncher.so“ für die R-Sprache für Linux | [R-Erweiterung](extension-r.md) | SQL Server 2019 und höher |
| „Pythonlauncher.so“ für Python 3.5 für Linux | [Python-Erweiterung](extension-python.md) | SQL Server 2019 und höher |

Der [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]-Dienst wird unter dem eigenen Benutzerkonto ausgeführt. Wenn Sie das Konto ändern, mit dem Launchpad ausgeführt wird, stellen Sie sicher, dass dies mit dem SQL Server-Konfigurations-Manager erfolgt, um sicherzustellen, dass Änderungen in die zugehörigen Dateien geschrieben werden.

In Windows wird für jede Instanz der Datenbank-Engine, der Sie SQL Server-Machine Learning Services hinzugefügt haben, ein separater [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]-Dienst erstellt. Es gibt einen Launchpaddienst für jede Instanz der Datenbank-Engine. Wenn Sie also über mehrere Instanzen mit externer Skriptunterstützung verfügen, haben Sie für jede einen Launchpaddienst. Eine Instanz der Datenbank-Engine ist an den für sie erstellten Launchpaddienst gebunden. Alle Aufrufe externer Skripts in einer gespeicherten Prozedur oder in T-SQL führen dazu, dass der SQL Server-Dienst den für dieselbe Instanz erstellten Launchpaddienst aufruft.

Zum Ausführen von Aufgaben in einer bestimmten unterstützten Sprache erhält das Launchpad ein gesichertes Workerkonto aus dem Pool und startet einen Satellitenprozess zum Verwalten der externen Runtime. Jeder Satellitenprozess erbt das Benutzerkonto des Launchpads und verwendet dieses Workerkonto für die Dauer der Skriptausführung. Wenn Skripts parallele Prozesse verwenden, werden sie unter demselben Einzelworkerkonto erstellt.

Unter Linux wird nur eine Instanz der Datenbank-Engine unterstützt, und es ist ein launchpadd-Dienst an die Instanz gebunden. Wenn ein Skript ausgeführt wird, startet der launchpadd-Dienst einen separaten Launchpadprozess mit dem **mssql_satellite**-Benutzerkonto mit geringen Berechtigungen. Jeder Satellitenprozess erbt das mssql_satellite-Benutzerkonto des Launchpads und verwendet dieses für die Dauer der Skriptausführung.

## <a name="bxlserver-and-sql-satellite"></a>BxlServer und SQL Satellite

**BxlServer** ist eine ausführbare Datei, die von Microsoft bereitgestellt wird und die die Kommunikation zwischen SQL Server und der Language Runtime verwaltet. Sie erstellt die Windows-Auftragsobjekte für Windows oder die Namespaces für Linux, die zur Bereitstellung externer Skriptsitzungen verwendet werden. Außerdem stellt sie für jeden externen Skriptauftrag sichere Arbeitsordner bereit und verwendet SQL Satellite, um die Datenübertragung zwischen der externen Runtime und SQL Server zu verwalten. Wenn Sie während der Ausführung eines Auftrags [Prozess-Explorer](https://technet.microsoft.com/sysinternals/processexplorer.aspx) verwenden, wird möglicherweise eine oder mehrere Instanzen von BxlServer angezeigt.

Im Grunde genommen ist BxlServer ein begleitendes Verfahren zu einer Language Runtime-Umgebung, das in Verbindung mit SQL Server für die Übertragung und Verwaltung von Aufgaben eingesetzt werden kann. BXL steht für „Binary Exchange Language“ und verweist auf das Datenformat, das zum effektiven Verschieben von Daten zwischen SQL Server und externen Prozessen verwendet wird. Darüber hinaus ist BxlServer ein wichtiger Bestandteil verwandter Produkte wie Microsoft R Client und Microsoft R Server.

**SQL Satellite** ist eine in der Datenbank-Engine enthaltene Erweiterbarkeits-API, um externen Code oder externe Runtimes, die mithilfe von C oder C++ implementiert wurden, zu unterstützen.

BxlServer verwendet den SQL-Satelliten für die folgenden Aufgaben:.

+ Lesen von Eingabedaten
+ Schreiben von Ausgabedaten
+ Abrufen von Eingabeargumenten
+ Schreiben von Ausgabeargumenten
+ Fehlerbehandlung
+ STDOUT und STDERR zurück auf den Client schreiben

SQL Satellite verwendet ein benutzerdefiniertes Datenformat, das für die schnelle Datenübertragung zwischen SQL Server und externen Skriptsprachen optimiert ist. Er führt Typumwandlungen durch und definiert die Schemas der Eingabe- und Ausgabedatasets während der Kommunikation zwischen SQL Server und der externen Skriptruntime.

SQL Satellite kann mithilfe von erweiterten Windows-Ereignissen (xEvents) überwacht werden. Weitere Informationen finden Sie unter [Erweiterte Ereignisse für R](../../advanced-analytics/r/extended-events-for-sql-server-r-services.md) und [Erweiterte Ereignisse für Python](../../advanced-analytics/python/extended-events-for-python.md).

## <a name="communication-channels-between-components"></a>Kommunikationskanäle zwischen Komponenten

Im folgenden Abschnitt werden die Kommunikationsprotokolle zwischen Komponenten und Datenplattformen beschrieben.

+ **TCP/IP**

  Standardmäßig wird für die interne Kommunikation zwischen SQL Server und SQL Satellite TCP/IP verwendet.

+ **Named Pipes**

  Für den interne Datentransport zwischen BxlServer und SQL Server über SQL Satellite wird zur Leistungssteigerung ein proprietäres, komprimiertes Datenformat verwendet. Der Datenaustausch zwischen den Language Runtimes und BxlServer erfolgt im BXL-Format mithilfe von Named Pipes.

+ **ODBC**

  Für die Kommunikation zwischen externen Data Science-Clients und einer SQL Server-Remoteinstanz wird ODBC verwendet. Das Konto, das Skriptaufträge an SQL Server übermittelt, muss über beide Berechtigungen zum Herstellen einer Verbindung mit der Instanz und zum Ausführen externer Skripts verfügen.

  Außerdem benötigt das Konto abhängig von der Aufgabe möglicherweise die folgenden Berechtigungen zum:

  + Lesen der vom Auftrag verwendeten Daten
  + Schreiben von Daten in Tabellen, z. B. beim Speichern von Ergebnissen in einer Tabelle
  + Erstellen von Datenbankobjekten, z. B. beim Speichern eines externen Skripts als Teil einer neuen gespeicherten Prozedur

  Wenn SQL Server als Computekontext für Skripts verwendet wird, die von einem Remoteclient ausgeführt werden, und die ausführbare Datei Daten aus einer externen Quelle abrufen muss, wird ODBC für den Rückschreibevorgang verwendet. SQL Server ordnet die Identität des Benutzers, der den Remotebefehl ausgibt, der Identität des Benutzers auf der aktuellen Instanz zu und führt den ODBC-Befehl mit den Anmeldeinformationen dieses Benutzers aus. Die Verbindungszeichenfolge, die zum Durchführen dieses ODBC-Aufruf erforderlich ist, wird vom Clientcode abgerufen.

+ **RODBC (nur R)** 

  Zusätzliche ODBC-Aufrufe können innerhalb des Skripts mithilfe von **RODBC** erfolgen. RODBC ist ein beliebtes R-Paket, das für den Zugriff auf Daten in relationalen Datenbanken verwendet wird. Die Leistung ist jedoch im Allgemeinen langsamer als die von vergleichbaren Anbietern, die von SQL Server verwendet werden. Viele R-Skripts verwenden eingebettete Aufrufe auf RODBC als eine Möglichkeit, „sekundäre“ Datasets für den Gebrauch in Analysen abzurufen. Beispielsweise kann die gespeicherte Prozedur, die ein Modell trainiert, möglicherweise eine SQL-Abfrage definieren, um die Daten für das Trainieren eines Modells abzurufen, aber einen eingebetteten RODBC-Aufruf zum Abrufen zusätzlicher Faktoren verwenden, um Lookups auszuführen oder um neue Daten aus externen Quellen zu erhalten, z.B. Textdateien oder Excel.

  Der folgende Code zeigt einen RODBC-Aufruf, der in einem R-Skript eingebettet ist:

    ```R
    library(RODBC);
    connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
    dbhandle <- odbcDriverConnect(connStr)
    OutputDataSet <- sqlQuery(dbhandle, "select * from table_name");
    ```

+ **Weitere Protokolle**

  Prozesse, die möglicherweise in „Blöcken“ arbeiten oder Daten zurück an einen Remoteclient übertragen müssen, können auch das [XDF-Dateiformat](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-xdf) verwenden. Die tatsächliche Datenübertragung erfolgt über codierte Blobs.

## <a name="see-also"></a>Weitere Informationen

+ [R-Erweiterung in SQL Server](extension-r.md)
+ [Python-Erweiterung in SQL Server](extension-python.md)