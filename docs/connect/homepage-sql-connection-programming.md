---
title: Homepage für SQL-Client-Programmierung | Microsoft-Dokumentation
description: Hub-Seite mit Anmerkungen versehene Links zu Downloads und Dokumentation für zahlreiche Kombinationen aus den Sprachen und Betriebssysteme, für die Verbindung mit SQL Server oder Azure SQL-Datenbank.
author: MightyPen
ms.date: 04/16/2018
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
ms.reviewer: meetb
ms.author: genemi
ms.openlocfilehash: e2c3da2ba71661602f69f85f5eb79ba6d550be9b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47633798"
---
# <a name="homepage-for-client-programming-to-microsoft-sql-server"></a>Homepage für den Client für Microsoft SQL Server-Programmierung


Willkommen Sie auf unserer Homepage zur Clientprogrammierung für die Interaktion mit Microsoft SQL Server, und klicken Sie mit Azure SQL-Datenbank in der Cloud. Dieser Artikel enthält die folgende Informationen an:

- Aufgelistet und beschrieben die verfügbaren Kombinationen von Sprache und -Treiber.
    - Informationen für die Betriebssysteme von Windows, MacOS und Linux (Ubuntu und andere) angegeben werden.
- Enthält Links zur ausführlichen Dokumentation für jede Kombination aus.
- Gegebenenfalls der Bereiche und Unterbereiche der hierarchischen Dokumentation für bestimmte Sprachen angezeigt werden soll.


#### <a name="azure-sql-database"></a>Azure SQL-Datenbank

In jeder angegebenen Sprache ist der Code für der Verbindung mit SQL Server fast identisch, mit dem Code für die Verbindung mit Azure SQL-Datenbank.

Weitere Informationen zu den für die Verbindung mit Azure SQL-Datenbank-Verbindungszeichenfolgen finden Sie unter:

- [Mithilfe von .NET Core (c#) zum Abfragen einer Azure SQL-Datenbank](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-dotnet-core).
- Andere Azure-SQL-Datenbank, die in der Nähe der vorherigen Artikel in der Tabelle von Inhalt, zu anderen Sprachen sind. Beispielsweise finden Sie unter [Verwenden von PHP zum Abfragen einer Azure SQL-Datenbank](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-php).


#### <a name="build-an-app-webpages"></a>Build-ein-app-Webseiten

Unsere *Build-ein-app* Webseiten Codebeispiele, zusammen mit Informationen zu Konfigurationen in ein alternatives Format vorhanden. Weitere Informationen finden Sie weiter unten in diesem Artikel die [Abschnitt mit der Bezeichnung *Build-ein-app-Website*](#an-204-aka-ms-sqldev).



<a name="an-050-languages-clients" />

## <a name="languages-and-drivers-for-client-programs"></a>Sprachen und Treiber für Clientprogramme


In der folgenden Tabelle wird jedes Bild Sprache einen Link zu Informationen zur Verwendung der Sprache mit SQL Server. Jeder Link führt zu einem späteren Abschnitt in diesem Artikel.

| &nbsp; | &nbsp; | &nbsp; |
| :-- | :-- | :-- |
| &nbsp; [![C#-logo][image-ref-320-csharp]](#an-110-ado-net-docu) | &nbsp; [![ORM-Entitätsframework von .NET Framework][image-ref-333-ef]](#an-116-csharp-ef-orm) | &nbsp; [![Java-Logo][image-ref-330-java]](#an-130-jdbc-docu) |
| &nbsp; [![Node.js-logo][image-ref-340-node]](#an-140-node-js-docu) | &nbsp; [**`ODBC for C++`**](#an-160-odbc-cpp-docu)<br/>[![Cpp-big-plus][image-ref-322-cpp]](#an-160-odbc-cpp-docu) | &nbsp; [![PHP-logo][image-ref-360-php]](#an-170-php-docu) |
| &nbsp; [![Python-logo][image-ref-370-python]](#an-180-python-docu) | &nbsp; [![Ruby-logo][image-ref-380-ruby]](#an-190-ruby-docu) | &nbsp; ... |
| &nbsp; | &nbsp; | <br />|


#### <a name="downloads-and-installs"></a>Heruntergeladen und installiert wird

Im folgende Artikel geht es um das Herunterladen und Installieren von verschiedenen SQL-Verbindung-Treiber, für die Verwendung von den Programmiersprachen:

- [SQL Server-Treiber](sql-server-drivers.md)



<a name="an-110-ado-net-docu" />

## <a name="c-logoimage-ref-320-csharp-c-using-adonet"></a>![C#-logo][image-ref-320-csharp] C# -Code mithilfe von ADO.NET

Der auf .NET-Basis verwalteten Sprachen wie c# und Visual Basic, sind die am häufigsten verwendeten Benutzer von ADO.NET. *ADO.NET* ist eine ungezwungene Name für eine Teilmenge der .NET Framework-Klassen.

#### <a name="code-examples"></a>Codebeispiele

|||
| :-- | :-- |
| [Proof of concept connecting to SQL using ADO.NET (Proof of Concept für Verbindungen mit SQL mithilfe von ADO.NET)](./ado-net/step-3-proof-of-concept-connecting-to-sql-using-ado-net.md) | Ein kleines Codebeispiel konzentriert sich auf eine Verbindung herstellen und Abfragen von SQL Server. |
| [Connect resiliently to SQL with ADO.NET (Herstellen stabiler SQL-Verbindungen mit ADO.NET)](./ado-net/step-4-connect-resiliently-to-sql-with-ado-net.md) | Wiederholen Sie die Logik in ein Codebeispiel, da Verbindungen Momente von verbindungsunterbrechung gelegentlich auftreten können.<br /><br />Wiederholungslogik gilt auch für Verbindungen, die über das Internet wie z. B. mit Azure SQL-Datenbank in eine beliebige Clouddatenbank verwaltet. |
| [Azure SQL-Datenbank: Demonstration der Verwendung von .NET Core unter Windows/Linux/MacOS ein C#-Programm erstellen, zum Verbinden und Abfragen](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-dotnet-core) | Beispiel für Azure SQL-Datenbank. |
| [Erstellen einer app: C#, ADO.NET, Windows](http://www.microsoft.com/sql-server/developer-get-started/csharp/win/) | Konfigurationsinformationen sowie Codebeispiele. |
| &nbsp; | <br /> |

#### <a name="documentation"></a>Dokumentation

|||
| :-- | :-- |
| [C# -Code mithilfe von ADO.NET](./ado-net/index.md)| Der Stamm der Dokumentation. |
| [Namespace: "System.Data"](http://docs.microsoft.com/dotnet/api/system.data) | Ein Satz von Klassen, die für ADO.NET. |
| [Namespace: System.Data.SqlClient](http://docs.microsoft.com/dotnet/api/system.data.SqlClient) | Der Satz von Klassen, die unmittelbar Center von ADO.NET. |
| &nbsp; | <br /> |



<a name="an-116-csharp-ef-orm" />

## <a name="entity-framework-logoimage-ref-333-ef-entity-framework-ef-with-cx23"></a>![Entity Framework-Logo][image-ref-333-ef] Entitätsframework (EF) mit C#&#x23;

Entity Framework (EF) bietet Object-Relational Mapping (ORM). ORM erleichtert es für Ihren Quellcode gehaltene, objektorientierte Programmierung (OOP), um Daten zu bearbeiten, die aus einer relationalen SQL-Datenbank abgerufen wurden.

EF hat es sich um direkte oder indirekte Beziehungen mit den folgenden Technologien:

- .NET Framework
- [LINQ to SQL](http://docs.microsoft.com/dotnet/framework/data/adonet/sql/linq/), oder [LINQ to Entities](http://docs.microsoft.com/dotnet/framework/data/adonet/ef/language-reference/linq-to-entities)
- Verbesserungen der Sprache-Syntax, wie z. B. die **=>** -Operator in c#.
- Nützliche Programme, die Quellcode für Klassen zu generieren, die für die Tabellen in der SQL-Datenbank zugeordnet sind. Z. B. [EdmGen.exe](http://docs.microsoft.com/dotnet/framework/data/adonet/ef/edm-generator-edmgen-exe).


#### <a name="original-ef-and-new-ef"></a>Ursprüngliche EF und neue EF

Die [für Entity Framework-Startseite](http://docs.microsoft.com/ef/) EF eingeführt, mit einer Beschreibung, die etwa wie folgt:

- Entitätsframework ist ein Objektrelationaler Mapper (O/RM), der .NET Entwicklern die Arbeit mit einer Datenbank mithilfe von .NET-Objekten ermöglicht. Es nicht erforderlich, die für den Großteil der Datenzugriffs-Quellcode, den Entwickler in der Regel schreiben müssen.

*Entitätsframework* ist ein Name, der von zwei separaten Quellcodefenster codeverzweigungen gemeinsam verwendet werden. Ein EF-Branch ist älter und der Quellcode kann jetzt von der öffentlichen verwaltet werden. Die andere EF ist neu. Nachfolgend werden die zwei EFs beschrieben:

|     |     |
| :-- | :-- |
| [EF 6.x](http://docs.microsoft.com/ef/ef6/) | Microsoft hat EF zuerst im August 2008 veröffentlicht. Seit März 2015 Microsoft hat angekündigt, die EF 6.x war die endgültige Version, die Microsoft entwickeln würden. Microsoft hat den Quellcode in der öffentlichen Domäne veröffentlicht.<br /><br />EF war ursprünglich Teil von .NET Framework. Aber EF 6.x von .NET Framework entfernt wurde.<br /><br />[EF 6.x-Quellcode auf Github im Repository *Aspnet/EntityFramework6*](http://github.com/aspnet/EntityFramework6) |
| [EF Core](http://docs.microsoft.com/ef/core/) | Microsoft hat die neu entwickelte EF Core im Juni 2016 veröffentlicht. EF Core ist für eine größere Flexibilität und Portabilität konzipiert. EF Core kann auf über nur Microsoft-Windows-Betriebssystemen ausführen. Und EF Core mit über nur Microsoft SQL Server-Datenbanken und anderen relationalen Datenbanken interagieren können.<br /><br />**C&#x23; Codebeispiele:**<br />[Erste Schritte mit Entity Framework Core](https://docs.microsoft.com/ef/core/get-started/index)<br />[Erste Schritte mit EF Core in .NET Framework mit einer vorhandenen Datenbank](https://docs.microsoft.com/ef/core/get-started/full-dotnet/existing-db) |
| &nbsp; | <br /> |

Entity Framework und verwandte Technologien sind leistungsstarke, und einige Dinge zu für den Entwickler, der den gesamten Bereich meistern möchte.

&nbsp;



<a name="an-130-jdbc-docu" />

## <a name="java-logoimage-ref-330-java-java-and-jdbc"></a>![Java-Logo][image-ref-330-java] Java- und JDBC

Microsoft bietet einen Java Database Connectivity (JDBC)-Treiber für die Verwendung mit SQL Server (oder mit Azure SQL-Datenbank, natürlich) ein. Dabei handelt es sich um einen JDBC-Treiber vom Typ 4, der über die Standardanwendungsprogrammierschnittstellen für JDBC Database Connectivity zur Verfügung stellt.

#### <a name="code-examples"></a>Codebeispiele

|||
| :-- | :-- |
| [Codebeispiele](./jdbc/code-samples/index.md) | Codebeispiele, die Informationen zu Datentypen, Resultsets und großer Datenmengen zu vermitteln. |
| [Verbindungs-URL – Beispiel](./jdbc/connection-url-sample.md) | Beschreibt, wie eine Verbindungs-URL für die Verbindung mit SQL Server verwenden. Können Sie damit dann eine SQL-Anweisung verwenden, um Daten abzurufen. |
| [Beispiel für Datenquellen](./jdbc/data-source-sample.md) | Beschreibt, wie eine Datenquelle zu verwenden, um die Verbindung mit SQL Server. Klicken Sie dann verwenden Sie eine gespeicherte Prozedur, um Daten abzurufen. |
| [Abfragen einer Azure SQL-Datenbank mithilfe von Java](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java) | Beispiel für Azure SQL-Datenbank. |
| [Erstellen Sie Java-apps, die mit SQL Server unter Ubuntu](http://www.microsoft.com/sql-server/developer-get-started/java/ubuntu/) | Konfigurationsinformationen sowie Codebeispiele. |
| &nbsp; | <br /> |

#### <a name="documentation"></a>Dokumentation

Die JDBC-Dokumentation umfasst die folgenden Hauptbereiche:

|||
| :-- | :-- |
| [Java Database Connectivity (JDBC)](./jdbc/index.md) | Stamm der JDBC-Dokumentation. |
| [Referenz](./jdbc/reference/index.md) | Schnittstellen, Klassen und Member. |
| [Programmierhandbuch für den JDBC-SQL-Treiber](./jdbc/programming-guide-for-jdbc-sql-driver.md) | Konfigurationsinformationen sowie Codebeispiele. |
| &nbsp; | <br /> |



<a name="an-140-node-js-docu" />

## <a name="nodejs-logoimage-ref-340-node-nodejs"></a>![Node.js-logo][image-ref-340-node] Node.js

Mit Node.js können Sie mit SQL Server von Windows, Linux oder Mac verbinden Der Stamm der Node.js-Dokumentation ist [hier](./node-js/index.md).

Die Node.js-Verbindung-Treiber für SQL Server wird in JavaScript implementiert. Der Treiber verwendet die TDS-Protokolls, das von allen modernen SQL Server-Versionen unterstützt wird. Der Treiber ist ein open-Source-Projekt, [auf Github verfügbar](http://tediousjs.github.io/tedious/).

#### <a name="code-examples"></a>Codebeispiele

|||
| :-- | :-- |
| [Proof of concept connecting to SQL using Node.js (Proof of Concept für Verbindungen mit SQL mithilfe von Node.js)](./node-js/step-3-proof-of-concept-connecting-to-sql-using-node-js.md) | Texten Quellcode für eine Verbindung mit SQL Server herstellen und Ausführen einer Abfrage an. |
| [Azure SQL-Datenbank: Verwenden von Node.js zum Abfrage](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-nodejs) | Beispiel für Azure SQL-Datenbank in der Cloud. |
| [Erstellen von Node.js-apps zur Verwendung von SQL Server unter macOS](http://www.microsoft.com/sql-server/developer-get-started/node/mac/) | Konfigurationsinformationen sowie Codebeispiele. |
| &nbsp; | <br /> |



<a name="an-160-odbc-cpp-docu" />

## <a name="odbc-for-c"></a>ODBC für C++ 

![ODBC-logo][image-ref-350-odbc] ![Cpp-big-plus][image-ref-322-cpp]

Open Database Connectivity (ODBC) in den 1990er Jahren entwickelt wurde, und es empfiehlt es sich um .NET Framework. ODBC ist unabhängig von jedem System bestimmten Datenbank und unabhängig vom Betriebssystem werden soll.

Im Laufe der Jahre wurden viele ODBC-Treiber erstellt und von Gruppen innerhalb und außerhalb von Microsoft veröffentlicht. Der Bereich der Treiber umfassen verschiedene Client-Programmiersprachen. Die Liste der Datenziele geht weit über die SQL Server.

Einige andere Connectivity-Treiber verwenden intern von ODBC.

#### <a name="code-example"></a>Codebeispiel

- [C++-Codebeispiel, mithilfe von ODBC](../odbc/reference/sample-odbc-program.md)

#### <a name="documentation-outline"></a>Übersicht über die Dokumentation

Der ODBC-Inhalt in diesem Abschnitt konzentriert sich auf den Zugriff auf SQL Server oder Azure SQL-Datenbank von C++. Die folgende Tabelle enthält die ungefähren Überblick über die wesentliche Dokumentation für ODBC.


| Bereich | Unterbereichs | und Beschreibung |
| :--- | :------ | :---------- |
| [ODBC für C++](./odbc/index.md) | Der Stamm der Dokumentation. |
| [Linux-Mac](./odbc/linux-mac/index.md) | &nbsp; | Informationen zur Verwendung von ODBC unter den Betriebssystemen Linux oder MacOS. |
| [Windows](./odbc/windows/index.md)     | &nbsp; | Informationen zur Verwendung von ODBC auf dem Windows-Betriebssystem. |
| [Verwaltung](../odbc/admin/index.md) | &nbsp; | Das administrative Tool für die Verwaltung von ODBC-Datenquellen. |
| [Microsoft](../odbc/microsoft/index.md)  | &nbsp; | Verschiedene ODBC-Treiber, die erstellt und von Microsoft bereitgestellt werden. |
| [Konzept- und](../odbc/reference/index.md) | &nbsp; | Grundlegende Informationen über die ODBC-Schnittstelle, zusätzlich zu der herkömmlichen Verweis. |
| &nbsp; " | [Anhänge](../odbc/reference/appendixes/index.md)    | Zustandsübergang Tabellen, ODBC-Cursorbibliothek und vieles mehr. |
| &nbsp; " | [Entwickeln der app](../odbc/reference/develop-app/index.md)  | Funktionen, Handles und vieles mehr. |
| &nbsp; " | [Entwickeln Sie Treiber](../odbc/reference/develop-driver/index.md) | Wie Sie eigene ODBC-Treiber zu entwickeln, wenn Sie eine speziellen Datenquelle verfügen. |
| &nbsp; " | [Installieren](../odbc/reference/install/index.md) | ODBC-Installation, Unterschlüssel und vieles mehr. |
| &nbsp; " | [Syntax](../odbc/reference/syntax/index.md)   | APIs für Setup, Installer, Übersetzung und Daten zugreifen. |
| &nbsp; | &nbsp; | <br /> |



<a name="an-170-php-docu" />

## <a name="php-logoimage-ref-360-php-php"></a>![PHP-logo][image-ref-360-php] PHP

Sie können PHP verwenden, um die Interaktion mit SQL Server. Der Stamm der PHP-Dokumentation ist [hier](./php/index.md).

#### <a name="code-examples"></a>Codebeispiele

|||
| :-- | :-- |
| [Proof of concept connecting to SQL using PHP (Proof of Concept für Verbindungen mit SQL mithilfe von PHP)](./php/step-3-proof-of-concept-connecting-to-sql-using-php.md) | Ein kleines Codebeispiel konzentriert sich auf eine Verbindung herstellen und Abfragen von SQL Server. |
| [Connect resiliently to SQL with PHP (Herstellen stabiler SQL-Verbindungen mit PHP)](./php/step-4-connect-resiliently-to-sql-with-php.md) | Wiederholen Sie die Logik in ein Codebeispiel, da Verbindungen über das Internet und der Cloud Momente von verbindungsunterbrechung gelegentlich auftreten können. |
| [Azure SQL-Datenbank: Verwenden von PHP zum Abfrage](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-php) | Beispiel für Azure SQL-Datenbank. |
| [Erstellen von PHP-apps zur Verwendung von SQL Server unter RHEL](http://www.microsoft.com/sql-server/developer-get-started/php/rhel/) | Konfigurationsinformationen sowie Codebeispiele. |
| &nbsp; | <br /> |



<a name="an-180-python-docu" />

## <a name="python-logoimage-ref-370-python-python"></a>![Python-logo][image-ref-370-python] Python


Sie können Python verwenden, um die Interaktion mit SQL Server.

#### <a name="code-examples"></a>Codebeispiele

|||
| :-- | :-- |
| [Proof of Concept für Verbindungen mit SQL mit Python mithilfe von pyodbc](./python/pyodbc/step-3-proof-of-concept-connecting-to-sql-using-pyodbc.md) | Ein kleines Codebeispiel konzentriert sich auf eine Verbindung herstellen und Abfragen von SQL Server. |
| [Azure SQL-Datenbank: Verwenden von Python zum Abfrage](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-python) | Beispiel für Azure SQL-Datenbank. |
| [Erstellen von PHP-apps zur Verwendung von SQL Server unter SLES](http://www.microsoft.com/sql-server/developer-get-started/python/sles/) | Konfigurationsinformationen sowie Codebeispiele. |
| &nbsp; | <br /> |

#### <a name="documentation"></a>Dokumentation

| Bereich | und Beschreibung |
| :--- | :---------- |
| [Python mit SQLServer](./python/index.md) | Der Stamm der Dokumentation. |
| [Pymssql-Treiber](./python/pymssql/index.md) | Microsoft nicht beibehält oder testen Sie den Pymssql-Treiber.<br /><br />Der Pymssql-Treiber-Verbindung ist eine einfache Schnittstelle für die SQL-Datenbanken, für die Verwendung in Python-Programmen. Pymssql baut auf FreeTDS zum Bereitstellen einer Python (PEP-249) für die DB-API-Oberfläche für Microsoft SQL Server. |
| [pyodbc-Treiber](./python/pyodbc/index.md)   | Die Treiber für die Pyodbc-Connection ist ein open-Source-Python-Modul, das Zugriff auf ODBC-Datenbanken auf einfache Weise. Es implementiert die DB API 2.0-Spezifikation, aber der Einfachheit halber auch weitere Python-Ähnlichere enthält. |
| &nbsp; | <br /> |


<a name="an-190-ruby-docu" />

## <a name="ruby-logoimage-ref-380-ruby-ruby"></a>![Ruby-logo][image-ref-380-ruby] Ruby

Sie können unter Verwendung von Ruby für die Interaktion mit SQL Server. Der Stamm der Ruby-Dokumentation ist [hier](./ruby/index.md).

#### <a name="code-examples"></a>Codebeispiele

|||
| :-- | :-- |
| [Proof of Concept für Verbindungen mit SQL mithilfe von PHP](./ruby/step-3-proof-of-concept-connecting-to-sql-using-ruby.md) | Ein kleines Codebeispiel konzentriert sich auf eine Verbindung herstellen und Abfragen von SQL Server. |
| [Azure SQL-Datenbank: Verwenden von Ruby zum Abfrage](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-ruby) | Beispiel für Azure SQL-Datenbank. |
| [Erstellen Sie Ruby-apps zur Verwendung von SQL Server unter MacOS](http://www.microsoft.com/sql-server/developer-get-started/ruby/mac/) | Konfigurationsinformationen sowie Codebeispiele. |
| &nbsp; | <br /> |



<a name="an-204-aka-ms-sqldev" />

## <a name="build-an-app-website-for-sql-client-developmenthttpwwwmicrosoftcomsql-serverdeveloper-get-started"></a>[Build-ein-app-Website für SQL-Client-Entwicklung](http://www.microsoft.com/sql-server/developer-get-started/)


Auf unserer [ *Build-ein-app* ](https://www.microsoft.com/sql-server/developer-get-started/) Webseiten Sie über eine lange Liste von Programmiersprachen zu vergleichen, die für die Verbindung mit SQL Server können. Und das Clientprogramm kann eine Vielzahl von Betriebssystemen ausgeführt.

*Build-ein-app* betont Einfachheit und Vollständigkeit für Entwickler, die erst der Anfang ist. Die Schritte erläutern die folgenden Aufgaben:

1. Vorgehensweise: Installieren von Microsoft SQL Server
2. Informationen zum Herunterladen und Installieren von Tools und Treiber.
3. So stellen Sie alle erforderlichen Konfigurationen, je nach ausgewählten Betriebssystem.
4. Informationen zum Kompilieren des Codes für die bereitgestellte Quelle.
5. Wie das Programm ausgeführt werden.

Als Nächstes werden einige ungefähre zeigt die Details auf der Website bereitgestellt:

#### <a name="java-on-ubuntu"></a>Java unter Ubuntu:

1. Einrichten der Umgebung
    - Schritt 1.1: Installieren von SQL Server
    - Schritt 1.2 installieren Java
    - Schritt 1.3 installieren Sie das Java Development Kit (JDK)
    - Schritt 1.4 installieren Sie Maven
2. Erstellen Sie Java-Anwendung mit SQL Server
    - Schritt 2.1: Erstellen einer Java-app, die eine Verbindung mit SQL Server her und führt Abfragen
    - Schritt 2.2: Erstellen einer Java-app, die Verbindung mit SQL Server mithilfe des beliebten Frameworks Ruhezustand
3. Machen Sie Ihre Java-app bis zu 100-Mal schneller
    - Schritt 3.1: Erstellen einer Java-app zur Veranschaulichung der columnstore-Indizes

#### <a name="python-on-windows"></a>Python unter Windows:

1. Einrichten der Umgebung
    - Schritt 1.1: Installieren von SQL Server
    - Schritt 1.2 Installieren von Python
    - Schritt 1.3 Installieren von ODBC-Treiber und SQL-Befehlszeilen-Hilfsprogramm für SQLServer
2. Erstellen von Python-Anwendung mit SQL Server
    - Schritt 2.1 installieren den Python-Treiber für SQL Server
    - Schritt 2.2: Erstellen einer Datenbank für Ihre Anwendung
    - Schritt 2.3: Erstellen einer Python-app, die eine Verbindung mit SQL Server her und führt Abfragen
3. Machen Sie Ihre Python-app bis zu 100-Mal schneller
    - Schritt 3.1: Erstellen einer neuen Tabelle mit 5 Millionen mithilfe von sqlcmd
    - Schritt 3.2: Erstellen einer Python-app, die Abfragen in dieser Tabelle und misst die Zeit
    - Schritt 3.3 zu messen, wie lange es dauert, um die Abfrage auszuführen
    - Schritt 3.4 hinzufügen einen columnstore-Index zu einer Tabelle
    - Schritt 3.5 zu messen, wie lange es dauert, zum Ausführen der Abfrage mit einem columnstore-index

Die folgenden Screenshots bieten Ihnen einen Überblick darüber, wie unsere SQL-Entwicklung-Dokumentationswebsite aussieht.

#### <a name="choose-a-language"></a>Wählen Sie eine Sprache aus:

![SQL-Entwickler-Website, erste Schritte][image-ref-390-aka-ms-sqldev-choose-language]

&nbsp;

#### <a name="choose-an-operating-system"></a>Wählen Sie ein Betriebssystem installiert ist:

![SQL-Entwickler Java-Ubuntu-website][image-ref-400-aka-ms-sqldev-java-ubuntu]

&nbsp;



## <a name="other-development"></a>Andere Entwicklung


Dieser Abschnitt enthält Links zu anderen Entwicklungsoptionen. Dazu gehören, verwenden diese dieselben Sprachen für Azure-Entwicklung im Allgemeinen. Hinausgeht, dass die Informationen auf die nur Azure SQL-Datenbank und Microsoft SQL Server.

#### <a name="developer-hub-for-azure"></a>Entwickler-Hub für Azure

- [Entwickler-Hub für Azure](http://docs.microsoft.com/azure/)
- [Azure für .NET-Entwickler](http://docs.microsoft.com/dotnet/azure/)
- [Azure für Java-Entwickler](http://docs.microsoft.com/java/azure/)
- [Azure für Node.js-Entwickler](http://docs.microsoft.com/nodejs/azure/)
- [Azure für Python-Entwickler](http://docs.microsoft.com/python/azure/)
- [Erstellen einer PHP-Web-app in Azure](http://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-php)

#### <a name="other-languages"></a>Andere Sprachen

- [Erstellen von Go-apps, die mit SQL Server unter Windows](http://www.microsoft.com/sql-server/developer-get-started/go/windows/)



<!-- Image references. -->

[image-ref-322-cpp]: ./media/homepage-sql-connection-drivers/gm-cpp-4point-p61f.png
[image-ref-320-csharp]: ./media/homepage-sql-connection-drivers/gm-csharp-c10c.png
[image-ref-333-ef]: ./media/homepage-sql-connection-drivers/gm-entity-framework-ef20d.png
[image-ref-330-java]: ./media/homepage-sql-connection-drivers/gm-java-j18c.png
[image-ref-340-node]: ./media/homepage-sql-connection-drivers/gm-node-n30.png
[image-ref-350-odbc]: ./media/homepage-sql-connection-drivers/gm-odbc-ic55826-o35.png
[image-ref-360-php]: ./media/homepage-sql-connection-drivers/gm-php-php60.png
[image-ref-370-python]: ./media/homepage-sql-connection-drivers/gm-python-py72.png
[image-ref-380-ruby]: ./media/homepage-sql-connection-drivers/gm-ruby-un-r82.png
[image-ref-390-aka-ms-sqldev-choose-language]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-choose-language-g21.png
[image-ref-400-aka-ms-sqldev-java-ubuntu]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-java-ubuntu-c31.png

