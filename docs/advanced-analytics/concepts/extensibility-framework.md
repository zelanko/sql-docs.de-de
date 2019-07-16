---
title: Architektur für die Sprache R und Python-Skript – SQL Server-Machine Learning-Erweiterbarkeit
description: Unterstützung für externen Code für die SQL Server-Datenbank-Engine, mit der Architektur mit zwei für die Ausführung von R und Python-Skript auf relationalen Daten.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 3d4d8108fda500d48425abfb52fd9f72c6faa147
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67963059"
---
# <a name="extensibility-architecture-in-sql-server-machine-learning-services"></a>Architektur der Erweiterbarkeit in SQL Server Machine Learning Services 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server bietet ein Erweiterungsframework für die Ausführung externer Skripts, z. B. R oder Python auf dem Server. Skript wird in einer Laufzeitumgebung Language als Erweiterung der Kerndatenbank-Engine ausgeführt. 

## <a name="background"></a>Hintergrund

Das Extensibility Framework wurde in SQL Server 2016 zur Unterstützung der R-Laufzeit eingeführt. SQL Server 2017 bietet Unterstützung für Python

Die dem Extensibility Framework dient zum bieten eine Schnittstelle zwischen SQL Server und Data Science-Sprachen wie R und Python reibungslosere benutzereinladung, wenn Gleitender Data Science-Lösungen in der Produktion und den Schutz von Daten während der Entwicklung verfügbar gemacht. der Prozess. Durch Ausführen von einer vertrauenswürdigen Skriptsprache in eine sichere Basis von SQL Server verwaltet werden, können Datenbankadministratoren Sicherheit zu gewährleisten und gleichzeitig Datenanalysten den Zugriff auf Unternehmensdaten.

Das folgende Diagramm beschreibt visuellen Möglichkeiten und Vorteile der erweiterbaren Architektur.

  ![Ziele der Integration in SQL Server](../media/ml-service-value-add.png "Machine Learning Services Wert hinzufügen")

Alle R oder Python-Skript kann durch Aufrufen einer gespeicherten Prozedur ausgeführt werden, und die Ergebnisse werden als tabellarische Ergebnisse direkt in SQL Server, zu generieren, oder nutzen jede Anwendung, die eine SQL-Abfrage senden und Verarbeiten der Ergebnisse kann Machine Learning vereinfachen zurückgegeben.

+ Ausführung des externen Skripts unterliegt den SQL Server Data-Sicherheit, in denen ein Benutzer ausführen externen Skripts können nur den Zugriff auf Daten, die in einer SQL-Abfrage gleichermaßen verfügbar ist. Wenn eine Abfrage aufgrund von unzureichenden Berechtigungen ein Fehler auftritt, würde Skript, das vom gleichen Benutzer auch aus demselben Grund fehlschlagen. SQL Server-Sicherheit wird auf die Tabelle, Datenbank und Instanzebene erzwungen. Datenbankadministratoren können Benutzer den Zugriff von externen Skripts verwendeten Ressourcen und externer Codebibliotheken, die dem Server hinzugefügt verwalten.  

+ Skalierung und Optimierung Möglichkeiten haben eine duale-Basis: Gewinne über die Datenbankplattform (columnstore-Indizes, [Ressourcenkontrolle](../../advanced-analytics/r/resource-governance-for-r-services.md)), und Gewinne spezifisch, wenn Microsoft-Bibliotheken für R und Python für Daten verwendet werden Science-Modelle. Während R Singlethread ist, sind die RevoScaleR-Funktionen mit mehreren Threads, der eine arbeitsauslastung über mehrere Kerne verteilen kann.

+ Bereitstellung verwendet SQL Server-Methoden: gespeicherte Prozeduren umschließen externen Skripts, eingebettete SQL oder T-SQL-Abfragen aufrufende Funktionen wie PREDICT zurückzugebenden Ergebnisse forecasting-Modellen, die auf dem Server persistent gespeichert.

+ R und Python-Entwickler mit eingerichtet Fähigkeiten in speziellen Tools und IDEs schreiben Sie Code in diese Tools und klicken Sie dann Code in SQL Server-port können.

## <a name="architecture-diagram"></a>Architekturdiagramm

Die Architektur ist so entworfen, dass externe Skripts in einem separaten Prozess ausführen, von SQL Server, jedoch mit Komponenten, die intern die Kette der Anforderungen für Daten und Vorgängen auf SQL Server zu verwalten. Abhängig von der Version von SQL Server enthalten die unterstützten spracherweiterungen R- und Python. 

  ![Komponentenarchitektur](../media/generic-architecture.png "Komponentenarchitektur")

Komponenten einer **Launchpad** Service verwendet, um sprachspezifische Startprogramme (R oder Python),-Sprache und Bibliothek-spezifische Logik für das Laden von Interpretern und-Bibliotheken aufzurufen. Das Startprogramm lädt zeilenweise Sprache ausführen, sowie alle proprietäre Module. Wenn Ihr Code die RevoScaleR-Funktionen enthält, z. B. lädt ein RevoScaleR-Interpreter. **BxlServer** und **SQL-Satellit** Übertragung von Daten und Kommunikation mit SQL Server verwaltet.

<a name="launchpad"></a>

## <a name="launchpad"></a>Launchpad

Die [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] ist ein Dienst, der verwaltet und externer Skripts, ähnlich wie die, dass der Volltextsuchdienst indizierungs- und einen separaten Host startet, für die Verarbeitung von Volltextabfragen ausführt. Der Launchpad-Dienst starten nur vertrauenswürdige Startprogramme, die von Microsoft veröffentlicht werden, oder, die von Microsoft als Anforderungen für Leistung und ressourcenverwaltung erfüllen zertifiziert wurden.

| Vertrauenswürdige Startprogramme | Erweiterung | SQL Server-Versionen |
|-------------------|-----------|---------------------|
| Datei "rlauncher.dll" für die Sprache R | [R-Erweiterung](extension-r.md) | SQLServer 2016, SqlServer 2017 |
| PythonLauncher.dll für Python 3.5 | [Python-Erweiterung](extension-python.md) | SQL Server 2017 |

Der [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]-Dienst wird unter dem eigenen Benutzerkonto ausgeführt. Wenn Sie das Konto, das Launchpad ausgeführt wird ändern, achten Sie darauf, dass Sie zu diesem Zweck verwenden SQL Server-Konfigurations-Manager, um sicherzustellen, dass Änderungen in geschrieben werden Dateien im Zusammenhang.

Eine Separate [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] Dienst erstellt und für jede Instanz der Datenbank-Engine zu dem Sie SQL Server-Machine Learning-Dienste hinzugefügt haben. Es wird eine Launchpad für jede Datenbank-Engine-Instanz, also wenn Sie mehrere Instanzen mit der Unterstützung externer Skripts verfügen, Sie einen Launchpad-Dienst für jeden einzelnen Dienst. Eine Instanz der Datenbank-Engine wird an den Launchpad-Dienst erstellt gebunden. Alle Aufrufe von externen Skripts in einer gespeicherten Prozedur oder ein Ergebnis von T-SQL in SQL Server-Dienst den Launchpad-Dienst erstellt für dieselbe Instanz aufgerufen.

Zum Ausführen von Aufgaben in einer bestimmten unterstützten Sprache, das Launchpad Ruft eine gesicherte workerkonto aus dem Pool, und startet einen satellitenprozess zum Verwalten der externen Runtime. Jeder satellitenprozess erbt das Benutzerkonto des LaunchPads und verwendet dieses workerkonto für die Dauer der Ausführung des Skripts. Wenn Skripts parallele Prozessen verwendet wird, werden sie unter dem workerkonto dieselbe, einzelne erstellt.

## <a name="bxlserver-and-sql-satellite"></a>BxlServer und SQL-Satellit

**BxlServer** ist eine ausführbare Datei, die von Microsoft, die Kommunikation zwischen SQL Server und Python oder r verwaltet bereitgestellt werden Er erstellt die Windows-Auftragsobjekte, die werden verwendet, um externen Skript-Sitzungen, stellt sichere Arbeitsordner für jeden Auftrag externes Skript enthalten, und SQL-Satellit zum Verwalten der Datenübertragung zwischen der externen Common Language Runtime und SQL Server verwendet. Wenn das Ausführen [Process Explorer](https://technet.microsoft.com/sysinternals/processexplorer.aspx) während ein Auftrag ausgeführt wird, können Sie sehen, dass eine oder mehrere Instanzen von BxlServer.

BxlServer ist eine begleitende in eine Sprache, das Time-Umgebung, das zusammen mit SQL Server zum Übertragen von Daten und Verwalten von Aufgaben ausführen. BXL steht für Binary Exchange Language und bezieht sich auf das Datenformat, das zum Verschieben von Daten effizient zwischen SQL Server und externen Prozessen verwendet. BxlServer ist auch ein wichtiger Bestandteil der verwandte Produkte wie Microsoft R Client und Microsoft R Server.

**SQL-Satellit** ist eine Erweiterbarkeits-API, die in der Datenbank-Engine, beginnend mit SQL Server 2016, die von externem Code unterstützt enthalten oder externe Laufzeiten, die mithilfe von C oder C++ implementiert.

BxlServer verwendet den SQL-Satelliten für die folgenden Aufgaben:.

+ Lesen von Eingabedaten
+ Schreiben von Ausgabedaten
+ Abrufen von Eingabeargumenten
+ Schreiben von Ausgabeargumenten
+ Fehlerbehandlung
+ STDOUT und STDERR zurück auf den Client schreiben

SQL-Satellit verwendet ein benutzerdefiniertes Datenformat, das optimiert ist, für die schnelle Datenübertragung zwischen SQL Server und externen Skriptsprachen. Er führt Typumwandlungen und die Schemas der Eingabe- und ausgabedatasets während der Kommunikation zwischen SQL Server und externen Skript-Runtime definiert.

Der SQL-Satellit kann mithilfe von Windows, die erweiterte Ereignisse (xEvents) überwacht werden. Weitere Informationen finden Sie unter [erweiterte Ereignisse bei R](../../advanced-analytics/r/extended-events-for-sql-server-r-services.md) und [Extended Events für Python](../../advanced-analytics/python/extended-events-for-python.md).

## <a name="communication-channels-between-components"></a>Kommunikationskanäle zwischen Komponenten

In diesem Abschnitt werden die Kommunikationsprotokolle zwischen Komponenten und der datenplattformen beschrieben.

+ **TCP/IP**

  Interne Kommunikation zwischen SQL Server und der SQL-Satellit verwenden standardmäßig TCP/IP.

+ **Named Pipes**

  Interne Datentransport zwischen BxlServer und SQL Server über SQL-Satellit verwendet ein proprietäres, komprimiertes Datenformat, um die Leistung zu verbessern. Daten werden im BXL-Format, die mithilfe von Named Pipes zwischen den Zeiten von Sprache, die ausgeführt und BxlServer ausgetauscht.

+ **ODBC**

  Kommunikation zwischen externen Data Science-Clients und einer SQL Server-Remoteinstanz Verwenden von ODBC. Das Konto, das die Skripts für Aufträge an SQL Server sendet, müssen beide Berechtigungen für die Verbindung mit der Instanz sowie zum Ausführen externer Skripts.

  Abhängig von der Aufgabe ist benötigen das Konto darüber hinaus Mitgliedsrechte:

  + Lesen von Daten, die vom Auftrag verwendeten
  + Schreiben von Daten in Tabellen: führt z. B. beim Speichern in einer Tabelle
  + Erstellen von Datenbankobjekten: Angenommen, externes Skript als Teil einer neuen gespeicherten Prozedur zu speichern.

  Wenn SQL Server als Compute Context verwendet wird, für die skriptausführung über ein Remoteclient und die ausführbare Datei müssen Daten aus einer externen Quelle abrufen, wird ODBC für das Rückschreiben verwendet. SQL Server ordnet die Identität des Benutzers den Remotebefehl auf die Identität des Benutzers in der aktuellen Instanz ausgibt, und führt den ODBC-Befehl mit Anmeldeinformationen des Benutzers. Die Verbindungszeichenfolge, die zum Durchführen dieses ODBC-Aufruf erforderlich ist, wird vom Clientcode abgerufen.

+ **RODBC (nur R)** 

  Zusätzliche ODBC-Aufrufe können innerhalb des Skripts mithilfe von **RODBC** erfolgen. RODBC ist eine beliebte R-Paket, das Zugriff auf Daten in relationalen Datenbanken verwendet. Es ist jedoch die Leistung in der Regel langsamer als die vergleichbaren Anbietern, die von SQL Server verwendet. Viele R-Skripts verwenden eingebettete Aufrufe auf RODBC als eine Möglichkeit, „sekundäre“ Datasets für den Gebrauch in Analysen abzurufen. Beispielsweise kann die gespeicherte Prozedur, die ein Modell trainiert, möglicherweise eine SQL-Abfrage definieren, um die Daten für das Trainieren eines Modells abzurufen, aber einen eingebetteten RODBC-Aufruf zum Abrufen zusätzlicher Faktoren verwenden, um Lookups auszuführen oder um neue Daten aus externen Quellen zu erhalten, z.B. Textdateien oder Excel.

  Der folgende Code zeigt einen RODBC-Aufruf, der in einem R-Skript eingebettet ist:

    ```R
    library(RODBC);
    connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
    dbhandle <- odbcDriverConnect(connStr)
    OutputDataSet <- sqlQuery(dbhandle, "select * from table_name");
    ```

+ **Andere Protokolle**

  Prozesse, die in "Blöcken" Geschäfts-, Schul- oder Daten an einen Remoteclient übertragen müssen möglicherweise können Sie auch die [XDF-Datei-Format](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-xdf). Tatsächliche Datenübertragung geschieht über codierte Blobs.

## <a name="see-also"></a>Siehe auch

+ [R-Erweiterung in SQL Server](extension-r.md)
+ [Python-Erweiterung in SQL Server](extension-python.md)