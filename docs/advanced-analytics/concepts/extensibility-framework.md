---
title: Erweiterbarkeits Architektur für R-Sprache und Python-Skript
description: Unterstützung externer Code für die SQL Server-Datenbank-Engine mit doppelter Architektur zum Ausführen von R-und python-Skripts für relationale Daten.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/30/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 49c45fa39cd271140ba78c2b1b32ee8a2f9c1a7a
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715252"
---
# <a name="extensibility-architecture-in-sql-server-machine-learning-services"></a>Erweiterbarkeits Architektur in SQL Server Machine Learning Services 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

SQL Server verfügt über ein Erweiterbarkeits Framework zum Ausführen externer Skripts, z. b. R oder python, auf dem Server. Skripts werden in einer Language Runtime-Umgebung als Erweiterung der Kerndatenbank-Engine ausgeführt. 

## <a name="background"></a>Hintergrund

Das Erweiterbarkeit Framework wurde in SQL Server 2016 eingeführt, um die R-Laufzeit zu unterstützen. SQL Server 2017 und höher unterstützt python.

Der Zweck des Erweiterbarkeits-Frameworks besteht darin, eine Schnittstelle zwischen SQL Server und Data Science Sprachen wie R und python bereitzustellen, die beim verlagern Data Science Lösungen in die Produktion und beim Schützen von Daten, die während der Entwicklung verfügbar gemacht werden, zu reduzieren. ESS. Durch Ausführen einer vertrauenswürdigen Skriptsprache innerhalb eines von SQL Server verwalteten sicheren Frameworks können Datenbankadministratoren die Sicherheit aufrechterhalten, während Datenanalysten Zugriff auf Unternehmensdaten erhalten.

Im folgenden Diagramm werden die Möglichkeiten und Vorteile der erweiterbaren Architektur visuell beschrieben.

  ![Ziele der Integration in SQL Server](../media/ml-service-value-add.png "Machine Learning Services Wert hinzufügen")

Alle R-oder python-Skripts können durch Aufrufen einer gespeicherten Prozedur ausgeführt werden, und die Ergebnisse werden als tabellarische Ergebnisse direkt an SQL Server zurückgegeben. dadurch ist es einfach, Machine Learning aus jeder Anwendung zu generieren oder zu nutzen, die eine SQL-Abfrage senden und die Ergebnisse verarbeiten kann.

+ Die Ausführung externer Skripts unterliegt SQL Server Datensicherheit, in der ein Benutzer, der externe Skripts ausführen, nur auf Daten zugreifen kann, die gleichzeitig in einer SQL-Abfrage verfügbar sind. Wenn eine Abfrage aufgrund unzureichender Berechtigungen fehlschlägt, kann das Skript, das vom gleichen Benutzer ausgeführt wird, aus demselben Grund auch fehlschlagen. SQL Server Sicherheit wird auf der Ebene der Tabelle, Datenbank und Instanz erzwungen. Datenbankadministratoren können den Benutzer Zugriff, die von externen Skripts verwendeten Ressourcen und externe Codebibliotheken verwalten, die dem Server hinzugefügt werden.  

+ Skalierungs-und Optimierungsmöglichkeiten haben einen doppelten Grund: Vorteile der Daten Bank Plattform (columnstore-Indizes, [Ressourcen](../../advanced-analytics/r/resource-governance-for-r-services.md)Kontrolle) und Erweiterungs spezifischen Vorteilen, wenn Microsoft-Bibliotheken für R und python für Data Science Modelle verwendet werden. Bei R handelt es sich um einen Single Thread, revoscaler-Funktionen sind Multithreadfunktionen, die eine Arbeitsauslastung über mehrere Kerne verteilen können.

+ Bereitstellung verwendet SQL Server Methodologien: gespeicherte Prozeduren, die externe Skripts, eingebettete SQL-oder T-SQL-Abfragen zum Aufrufen von Funktionen wie Vorhersagen umschreiben, um Ergebnisse von Vorhersagemodellen zurückzugeben

+ R-und Python-Entwickler mit bewährten Kenntnissen in bestimmten Tools und IDES können Code in diese Tools schreiben und dann Code zum SQL Server portieren.

## <a name="architecture-diagram"></a>Architektur Diagramm

Die Architektur ist so konzipiert, dass externe Skripts in einem separaten Prozess von SQL Server ausgeführt werden, jedoch mit Komponenten, die intern die Kette von Anforderungen für Daten und Vorgänge auf SQL Server verwalten. Abhängig von der SQL Server Version enthalten unterstützte Spracherweiterungen R und python. 

  ![Komponentenarchitektur](../media/generic-architecture.png "Komponentenarchitektur")

Zu den Komponenten gehören ein **Launchpad** -Dienst, mit dem sprachspezifische Launcher (R oder python), sprach-und Bibliotheks spezifische Logik zum Laden von Interpretern und Bibliotheken aufgerufen werden. Das Start Programm lädt eine Sprachlaufzeit sowie alle proprietären Module. Wenn Ihr Code z. b. revoscaler-Funktionen enthält, würde ein revoscaler-Interpreter geladen werden. **Bxlserver** und **SQL-Satellit** verwalten Kommunikation und Datenübertragung mit SQL Server.

<a name="launchpad"></a>

## <a name="launchpad"></a>Launchpad

Bei [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] handelt es sich um einen Dienst, der externe Skripts verwaltet und ausführt, ähnlich der Art, in der die Volltextindizierung und der Abfragedienst einen separaten Host zum Verarbeiten von voll Text Abfragen starten. Der Launchpad-Dienst kann nur vertrauenswürdige Launcher starten, die von Microsoft veröffentlicht wurden oder die von Microsoft als Erfüllung der Anforderungen an die Leistung und Ressourcenverwaltung zertifiziert wurden.

| Vertrauenswürdige Launcher | Erweiterung | SQL Server Versionen |
|-------------------|-----------|---------------------|
| "Rlauncher. dll" für die Sprache "R" | [R-Erweiterung](extension-r.md) | SQL Server 2016 und höher |
| Pythonlauncher. dll für python 3,5 | [Python-Erweiterung](extension-python.md) | SQL Server 2017 und höher |

Der [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]-Dienst wird unter dem eigenen Benutzerkonto ausgeführt. Wenn Sie das Konto ändern, mit dem Launchpad ausgeführt wird, stellen Sie sicher, dass dies mit SQL Server-Konfigurations-Manager erfolgt, um sicherzustellen, dass Änderungen in verwandte Dateien geschrieben werden.

Für jede [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] Instanz der Datenbank-Engine, der Sie SQL Server Machine Learning Services hinzugefügt haben, wird ein separater Dienst erstellt. Es gibt einen Launchpad-Dienst für jede Instanz der Datenbank-Engine. Wenn Sie also über mehrere Instanzen mit externer Skriptunterstützung verfügen, verfügen Sie jeweils über einen Launchpad-Dienst. Eine Datenbank-Engine-Instanz ist an den für Sie erstellten Launchpad-Dienst gebunden. Alle Aufrufe externer Skripts in einer gespeicherten Prozedur oder in T-SQL führen dazu, dass der SQL Server Dienst den für die gleiche Instanz erstellten Launchpad-Dienst aufruft.

Zum Ausführen von Aufgaben in einer bestimmten unterstützten Sprache erhält das Launchpad ein gesichertes Workerkonto aus dem Pool und startet einen Satelliten Prozess zum Verwalten der externen Laufzeit. Jeder Satelliten Prozess erbt das Benutzerkonto des Launchpad und verwendet dieses Workerkonto für die Dauer der Skriptausführung. Wenn Skripts parallele Prozesse verwenden, werden Sie unter demselben einzelworkerkonto erstellt.

## <a name="bxlserver-and-sql-satellite"></a>Bxlserver und SQL-Satellit

**Bxlserver** ist eine ausführbare Datei, die von Microsoft bereitgestellt wird, die die Kommunikation zwischen SQL Server und Python oder R verwaltet. Er erstellt die Windows-Auftrags Objekte, die verwendet werden, um externe Skript Sitzungen zu enthalten, stellt sichere Arbeitsordner für jeden externen Skript Auftrag bereit und verwendet SQL-Satelliten, um die Datenübertragung zwischen der externen Laufzeit und der SQL Server zu verwalten. Wenn Sie den [Prozess-Explorer](https://technet.microsoft.com/sysinternals/processexplorer.aspx) ausführen, während ein Auftrag ausgeführt wird, wird möglicherweise eine oder mehrere Instanzen von bxlserver angezeigt.

Bxlserver ist in der Tat ein Begleit Verfahren für eine Sprachlaufzeit-Umgebung, die mit SQL Server zum Übertragen von Daten und Verwalten von Aufgaben arbeitet. BXL steht für binäre Austausch Sprache und bezieht sich auf das Datenformat, das zum effizienten Verschieben von Daten zwischen SQL Server und externen Prozessen verwendet wird. Bxlserver ist auch ein wichtiger Bestandteil verwandter Produkte wie Microsoft R Client und Microsoft R Server.

Der **SQL-Satellit** ist eine Erweiterbarkeits-API, die in der Datenbank-Engine enthalten ist, die externen Code oder externe Laufzeiten C++unterstützt, die mithilfe von C oder implementiert werden.

BxlServer verwendet den SQL-Satelliten für die folgenden Aufgaben:.

+ Lesen von Eingabedaten
+ Schreiben von Ausgabedaten
+ Abrufen von Eingabeargumenten
+ Schreiben von Ausgabeargumenten
+ Fehlerbehandlung
+ STDOUT und STDERR zurück auf den Client schreiben

Der SQL-Satellit verwendet ein benutzerdefiniertes Datenformat, das für die schnelle Datenübertragung zwischen SQL Server und externen Skriptsprachen optimiert ist. Sie führt Typkonvertierungen aus und definiert die Schemas der Eingabe-und Ausgabe Datasets während der Kommunikation zwischen SQL Server und der externen Skript Laufzeit.

Der SQL-Satellit kann mithilfe von erweiterten Windows-Ereignissen (xevents) überwacht werden. Weitere Informationen finden Sie unter [Erweiterte Ereignisse für R](../../advanced-analytics/r/extended-events-for-sql-server-r-services.md) und [Erweiterte Ereignisse für python](../../advanced-analytics/python/extended-events-for-python.md).

## <a name="communication-channels-between-components"></a>Kommunikationskanäle zwischen Komponenten

Die Kommunikationsprotokolle zwischen Komponenten und Daten Plattformen werden in diesem Abschnitt beschrieben.

+ **TCP/IP**

  Standardmäßig verwenden die interne Kommunikation zwischen SQL Server und dem SQL-Satelliten TCP/IP.

+ **Named Pipes**

  Der interne Datentransport zwischen dem bxlserver und dem SQL Server über den SQL-Satelliten verwendet ein proprietäres, komprimiertes Datenformat zur Leistungssteigerung. Daten werden zwischen den sprach Laufzeiten und bxlserver im BXL-Format mithilfe von Named Pipes ausgetauscht.

+ **ODBC**

  Bei der Kommunikation zwischen externen Data Science Clients und einer Remote SQL Server Instanz wird ODBC verwendet. Das Konto, das die Skript Aufträge an SQL Server sendet, muss über beide Berechtigungen zum Herstellen einer Verbindung mit der Instanz und zum Ausführen externer Skripts verfügen.

  Außerdem benötigt das Konto abhängig von der Aufgabe möglicherweise die folgenden Berechtigungen:

  + Lesen von Daten, die vom Auftrag verwendet werden
  + Schreiben von Daten in Tabellen: z. b. beim Speichern von Ergebnissen in einer Tabelle
  + Erstellen von Datenbankobjekten, z. b. Wenn Sie ein externes Skript als Teil einer neuen gespeicherten Prozedur speichern.

  Wenn SQL Server als computekontext für Skripts verwendet wird, die von einem Remote Client ausgeführt werden, und die ausführbare Datei Daten aus einer externen Quelle abrufen muss, wird ODBC für das Rück schreiben verwendet. SQL Server ordnet die Identität des Benutzers, der den Remote Befehl ausgibt, der Identität des Benutzers auf der aktuellen Instanz zu und führt den ODBC-Befehl mit den Anmelde Informationen des Benutzers aus. Die Verbindungszeichenfolge, die zum Durchführen dieses ODBC-Aufruf erforderlich ist, wird vom Clientcode abgerufen.

+ **Rodbc (nur R)** 

  Zusätzliche ODBC-Aufrufe können innerhalb des Skripts mithilfe von **RODBC** erfolgen. Rodbc ist ein beliebtes R-Paket, mit dem auf Daten in relationalen Datenbanken zugegriffen werden kann. die Leistung ist jedoch im Allgemeinen langsamer als vergleichbare Anbieter, die von SQL Server verwendet werden. Viele R-Skripts verwenden eingebettete Aufrufe auf RODBC als eine Möglichkeit, „sekundäre“ Datasets für den Gebrauch in Analysen abzurufen. Beispielsweise kann die gespeicherte Prozedur, die ein Modell trainiert, möglicherweise eine SQL-Abfrage definieren, um die Daten für das Trainieren eines Modells abzurufen, aber einen eingebetteten RODBC-Aufruf zum Abrufen zusätzlicher Faktoren verwenden, um Lookups auszuführen oder um neue Daten aus externen Quellen zu erhalten, z.B. Textdateien oder Excel.

  Der folgende Code zeigt einen RODBC-Aufruf, der in einem R-Skript eingebettet ist:

    ```R
    library(RODBC);
    connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
    dbhandle <- odbcDriverConnect(connStr)
    OutputDataSet <- sqlQuery(dbhandle, "select * from table_name");
    ```

+ **Andere Protokolle**

  Prozesse, die möglicherweise in "Blöcken" arbeiten oder Daten zurück an einen Remote Client übertragen müssen, können auch das [Xdf-Dateiformat](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-xdf)verwenden. Die tatsächliche Datenübertragung erfolgt über codierte blobdaten.

## <a name="see-also"></a>Siehe auch

+ [R-Erweiterung in SQL Server](extension-r.md)
+ [Python-Erweiterung in SQL Server](extension-python.md)