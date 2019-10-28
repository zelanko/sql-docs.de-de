---
title: Startseite für die SQL-Client Programmierung | Microsoft-Dokumentation
description: Eine Hub-Seite mit mit Anmerkungen versehene Links zu Downloads und Dokumentation für zahlreiche Kombinationen von Sprachen und Betriebssystemen für die Verbindung mit SQL Server oder Azure SQL-Datenbank.
author: MightyPen
ms.date: 11/07/2018
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
ms.reviewer: v-daveng
ms.author: genemi
ms.openlocfilehash: 6961f8c23b4acfd787958cc9a160faf88362b54c
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72451849"
---
# <a name="homepage-for-client-programming-to-microsoft-sql-server"></a>Startseite für die Clientprogrammierung in Microsoft SQL Server


Willkommen bei unserer Homepage zur Client Programmierung für die Interaktion mit Microsoft SQL Server und Azure SQL-Datenbank in der Cloud. Dieser Artikel bietet die folgenden Informationen:

- Listet die verfügbaren Kombinationen aus Sprache und Treiber auf und beschreibt diese.
    - Informationen werden für die Betriebssysteme von Linux (Ubuntu und andere), MacOS und Windows angegeben.
- Enthält Links zu der detaillierten Dokumentation für jede Kombination.
- Zeigt die Bereiche und Unterbereiche der hierarchischen Dokumentation für bestimmte Sprachen an, wenn dies angebracht ist.


#### <a name="azure-sql-database"></a>Azure SQL-Datenbank

In jeder beliebigen Sprache ist der Code, der eine Verbindung mit SQL Server herstellt, fast identisch mit dem Code für die Verbindung mit Azure SQL-Datenbank.

Ausführliche Informationen zu den Verbindungs Zeichenfolgen für das Herstellen einer Verbindung mit Azure SQL-Datenbank finden Sie unter:

- [Verwenden Sie .net CoreC#(), um eine Azure SQL-Datenbank abzufragen](/azure/sql-database/sql-database-connect-query-dotnet-core).
- Weitere Azure SQL-Datenbanken, die sich in der Nähe des vorangehenden Artikels im Inhaltsverzeichnis befinden, zu anderen Sprachen. Informationen zum Beispiel finden [Sie unter Verwenden von PHP zum Abfragen einer Azure SQL-Datenbank](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-php).


#### <a name="build-an-app-webpages"></a>Build-an-App-Webseiten

Unsere Webseiten von *Build-a-app* enthalten Codebeispiele sowie Konfigurationsinformationen in einem alternativen Format. Weitere Informationen finden Sie weiter unten in diesem Artikel im [Abschnitt mit der Bezeichnung *Build-an-App-Website*](#an-204-aka-ms-sqldev).



<a name="an-050-languages-clients" />

## <a name="languages-and-drivers-for-client-programs"></a>Sprachen und Treiber für Client Programme


In der folgenden Tabelle ist jedes sprach Image ein Link zu Details zur Verwendung der Sprache mit SQL Server. Jeder Link springt zu einem späteren Abschnitt in diesem Artikel.

| &nbsp; | &nbsp; | &nbsp; |
| :-- | :-- | :-- |
| &nbsp; [![C# Logo][image-ref-320-csharp]](#an-110-ado-net-docu) | &nbsp; [![ORM Entity Framework von .NET Framework][image-ref-333-ef]](#an-116-csharp-ef-orm) | &nbsp; [![Java-Logo][image-ref-330-java]](#an-130-jdbc-docu) |
| &nbsp; [![Node. js-Logo][image-ref-340-node]](#an-140-node-js-docu) | &nbsp; [ **`ODBC for C++`** ](#an-160-odbc-cpp-docu)<br/>[![cpp-big-plus][image-ref-322-cpp]](#an-160-odbc-cpp-docu) | &nbsp; [![PHP Logo][image-ref-360-php]](#an-170-php-docu) |
| &nbsp; [![Python-Logo][image-ref-370-python]](#an-180-python-docu) | &nbsp; [![Ruby Logo][image-ref-380-ruby]](#an-190-ruby-docu) | &nbsp; ... |
| &nbsp; | &nbsp; | <br />|


#### <a name="downloads-and-installs"></a>Downloads und Installationen

Der folgende Artikel dient zum herunterladen und Installieren verschiedener SQL-Verbindungs Treiber für die Verwendung durch Programmiersprachen:

- [SQL Server-Treiber](sql-server-drivers.md)



<a name="an-110-ado-net-docu" />

## <a name="c-logoimage-ref-320-csharp-c-using-adonet"></a>![C#Logo][image-ref-320-csharp] C#Verwenden von ADO.net

Die verwalteten .net C# -Sprachen, wie z. b. und Visual Basic, sind die gängigsten Benutzer von ADO.net. *ADO.net* ist ein zufälliger Name für eine Teilmenge von .NET Framework-Klassen.

#### <a name="code-examples"></a>Codebeispiele

|||
| :-- | :-- |
| [Proof of concept connecting to SQL using ADO.NET (Proof of Concept für Verbindungen mit SQL mithilfe von ADO.NET)](./ado-net/step-3-connect-sql-ado-net.md) | Ein kleines Codebeispiel konzentriert sich auf das verbinden und Abfragen von SQL Server. |
| [Connect resiliently to SQL with ADO.NET (Herstellen stabiler SQL-Verbindungen mit ADO.NET)](./ado-net/step-4-connect-resiliently-sql-ado-net.md) | Wiederholungs Logik in einem Codebeispiel, da bei Verbindungen gelegentlich Verbindungs Verluste auftreten können.<br /><br />Die Wiederholungs Logik gilt auch für Verbindungen, die über das Internet in beliebige clouddatenbanken wie Azure SQL-Datenbank verwaltet werden. |
| [Azure SQL-Datenbank: Demonstration der Verwendung von .net Core unter Windows/Linux/macOS zum Erstellen eines C# Programms, zum Herstellen einer Verbindung und Abfragen](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-dotnet-core) | Beispiel für eine Azure SQL-Datenbank. |
| [Build-an-App: C#, ADO.net, Windows](https://www.microsoft.com/sql-server/developer-get-started/csharp/win/) | Konfigurationsinformationen, zusammen mit Codebeispielen. |
| &nbsp; | <br /> |

#### <a name="documentation"></a>Dokumentation

|||
| :-- | :-- |
| [C#Verwenden von ADO.net](./ado-net/index.md)| Der Stamm der Dokumentation. |
| [Namespace: System. Data](https://docs.microsoft.com/dotnet/api/system.data) | Eine Reihe von Klassen, die für ADO.NET verwendet werden. |
| [Namespace: System.Data.SqlClient](https://docs.microsoft.com/dotnet/api/system.data.SqlClient) | Der Satz von Klassen, die am meisten direkt den Mittelpunkt von ADO.net haben. |
| &nbsp; | <br /> |



<a name="an-116-csharp-ef-orm" />

## <a name="entity-framework-logoimage-ref-333-ef-entity-framework-ef-with-cx23"></a>![Entity Framework-Logo][image-ref-333-ef] Entity Framework (EF) mit C&#x23;

Entity Framework (EF) stellt eine Objekt relationale Zuordnung (ORM) bereit. ORM vereinfacht den OOP-Quellcode (Object-Oriented Programming) zum Bearbeiten von Daten, die aus einer relationalen SQL-Datenbank abgerufen wurden.

EF hat direkte oder indirekte Beziehungen zu den folgenden Technologien:

- .NET Framework
- [LINQ to SQL](https://docs.microsoft.com/dotnet/framework/data/adonet/sql/linq/)oder [LINQ to Entities](https://docs.microsoft.com/dotnet/framework/data/adonet/ef/language-reference/linq-to-entities)
- Verbesserungen der Sprachsyntax, z. b C#. der **=>** Operator in.
- Praktische Programme, die Quellcode für Klassen generieren, die den Tabellen in der SQL-Datenbank zugeordnet sind. Beispielsweise " [EdmGen. exe](https://docs.microsoft.com/dotnet/framework/data/adonet/ef/edm-generator-edmgen-exe)".


#### <a name="original-ef-and-new-ef"></a>Ursprüngliches EF und neues EF

Die [Startseite für Entity Framework](https://docs.microsoft.com/ef/) führt EF mit einer Beschreibung ein, die der folgenden ähnelt:

- Entity Framework ist eine Objekt relationale Zuordnung (Object-Relational Mapper, O/RM), die .NET-Entwicklern die Arbeit mit einer Datenbank mithilfe von .NET-Objekten ermöglicht. Dadurch entfällt der größte Teil des Datenzugriffs Quellcodes, den Entwickler in der Regel schreiben müssen.

*Entity Framework* ist ein Name, der von zwei separaten Quell Code Verzweigungen gemeinsam verwendet wird. Eine EF-Verzweigung ist älter, und ihr Quellcode kann nun von der öffentlichen verwaltet werden. Der andere EF ist neu. Die beiden EFS werden im folgenden beschrieben:

|     |     |
| :-- | :-- |
| [EF 6.x](https://docs.microsoft.com/ef/ef6/) | Microsoft hat zuerst EF im August 2008 veröffentlicht. Im März 2015 hat Microsoft angekündigt, dass EF 6. x die endgültige Version ist, die Microsoft entwickeln würde. Microsoft hat den Quellcode in der öffentlichen Domäne veröffentlicht.<br /><br />Zunächst war EF Teil .NET Framework. EF 6. x wurde jedoch aus .NET Framework entfernt.<br /><br />[EF 6. x-Quellcode auf GitHub im Repository *ASPNET/EntityFramework6*](https://github.com/aspnet/EntityFramework6) |
| [EF Core](https://docs.microsoft.com/ef/core/) | Microsoft hat die neu entwickelte EF Core im Juni 2016 veröffentlicht. EF Core ist für eine bessere Flexibilität und Portabilität konzipiert. EF Core können auf Betriebssystemen außerhalb von Microsoft Windows ausgeführt werden. Und EF Core können über Microsoft SQL Server und andere relationale Datenbanken hinaus mit Datenbanken interagieren.<br /><br />**C&#x23; -Codebeispiele:**<br />[Erste Schritte mit Entity Framework Core](https://docs.microsoft.com/ef/core/get-started/index)<br />[Die ersten Schritte mit EF Core auf .NET Framework mit einer vorhandenen Datenbank](https://docs.microsoft.com/ef/core/get-started/full-dotnet/existing-db) |
| &nbsp; | <br /> |

EF und verwandte Technologien sind leistungsstark und für den Entwickler, der den gesamten Bereich beherrschen möchte, sehr viel zu erlernen.

&nbsp;



<a name="an-130-jdbc-docu" />

## <a name="java-logoimage-ref-330-java-java-and-jdbc"></a>![Java-Logo][image-ref-330-java] Java und JDBC

Microsoft stellt einen JDBC-Treiber (Java Database Connectivity) für die Verwendung mit SQL Server (oder mit Azure SQL-Datenbank) bereit. Dabei handelt es sich um einen JDBC-Treiber vom Typ 4, der über die Standardanwendungsprogrammierschnittstellen für JDBC Database Connectivity zur Verfügung stellt.

#### <a name="code-examples"></a>Codebeispiele

|||
| :-- | :-- |
| [Codebeispiele](./jdbc/code-samples/index.md) | Code Beispiele, die Informationen zu Datentypen, Resultsets und großen Datenmengen vermitteln. |
| [Verbindungs-URL – Beispiel](./jdbc/connection-url-sample.md) | Beschreibt die Verwendung einer Verbindungs-URL zum Herstellen einer Verbindung mit SQL Server. Verwenden Sie diese dann, um eine SQL-Anweisung zum Abrufen von Daten zu verwenden. |
| [Beispiel für Datenquellen](./jdbc/data-source-sample.md) | Beschreibt, wie eine Datenquelle verwendet wird, um eine Verbindung mit SQL Server herzustellen. Verwenden Sie dann eine gespeicherte Prozedur, um Daten abzurufen. |
| [Abfragen einer Azure SQL-Datenbank mithilfe von Java](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java) | Beispiel für eine Azure SQL-Datenbank. |
| [Erstellen von Java-Apps mithilfe von SQL Server unter Ubuntu](https://www.microsoft.com/sql-server/developer-get-started/java/ubuntu/) | Konfigurationsinformationen, zusammen mit Codebeispielen. |
| &nbsp; | <br /> |

#### <a name="documentation"></a>Dokumentation

Die JDBC-Dokumentation enthält die folgenden Hauptbereiche:

|||
| :-- | :-- |
| [Java Database Connectivity (JDBC)](./jdbc/index.md) | Stamm der JDBC-Dokumentation. |
| [Referenz](./jdbc/reference/index.md) | Schnittstellen, Klassen und Member. |
| [Programmierhandbuch für den JDBC-SQL-Treiber](./jdbc/programming-guide-for-jdbc-sql-driver.md) | Konfigurationsinformationen, zusammen mit Codebeispielen. |
| &nbsp; | <br /> |



<a name="an-140-node-js-docu" />

## <a name="nodejs-logoimage-ref-340-node-nodejs"></a>![Node. js-Logo][image-ref-340-node] Node.js

Mit Node. js können Sie eine Verbindung mit SQL Server von Windows, Linux oder Mac herstellen. Der Stamm der Node. js-Dokumentation finden Sie [hier](./node-js/index.md).

Der Node. js-Verbindungs Treiber für SQL Server wird in JavaScript implementiert. Der Treiber verwendet das TDS-Protokoll, das von allen modernen Versionen von SQL Server unterstützt wird. Der Treiber ist ein Open Source-Projekt, das [auf GitHub verfügbar](https://tediousjs.github.io/tedious/)ist.

#### <a name="code-examples"></a>Codebeispiele

|||
| :-- | :-- |
| [Proof of concept connecting to SQL using Node.js (Proof of Concept für Verbindungen mit SQL mithilfe von Node.js)](./node-js/step-3-proof-of-concept-connecting-to-sql-using-node-js.md) | Der Quellcode für das Herstellen einer Verbindung mit SQL Server und das Ausführen einer Abfrage. |
| [Azure SQL-Datenbank: Verwenden von Node. js zum Abfragen](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-nodejs) | Beispiel für Azure SQL-Datenbank in der Cloud. |
| [Erstellen von Node. js-Apps für die Verwendung von SQL Server unter macOS](https://www.microsoft.com/sql-server/developer-get-started/node/mac/) | Konfigurationsinformationen, zusammen mit Codebeispielen. |
| &nbsp; | <br /> |



<a name="an-160-odbc-cpp-docu" />

## <a name="odbc-for-c"></a>ODBC für C++ 

![ODBC-Logo][image-ref-350-odbc] ![cpp-big-plus][image-ref-322-cpp]

ODBC (Open Database Connectivity) wurde in den 90er Jahren entwickelt, und es werden .NET Framework vorausgeht. ODBC ist unabhängig von einem bestimmten Datenbanksystem und unabhängig vom Betriebssystem.

Im Laufe der Jahre wurden zahlreiche ODBC-Treiber von Gruppen innerhalb und außerhalb von Microsoft erstellt und freigegeben. Der Bereich der Treiber umfasst mehrere Client Programmiersprachen. Die Liste der Datenziele geht weit über die SQL Server hinaus.

Einige andere konnektivitätstreiber verwenden ODBC intern.

#### <a name="code-example"></a>Codebeispiel

- [C++-Codebeispiel unter Verwendung von ODBC](../odbc/reference/sample-odbc-program.md)

#### <a name="documentation-outline"></a>Dokumentations Gliederung

Der ODBC-Inhalt in diesem Abschnitt konzentriert sich auf den Zugriff auf SQL Server oder Azure SQL C++-Datenbank, von. In der folgenden Tabelle wird ein ungefähre Umriss der Haupt Dokumentation für ODBC aufgelistet.


| Bereich | Unterbereich | und Beschreibung |
| :--- | :------ | :---------- |
| [ODBC für C++](./odbc/index.md) | Der Stamm der Dokumentation. |
| [Linux-Mac](./odbc/linux-mac/index.md) | &nbsp; | Informationen zur Verwendung von ODBC unter den Linux-oder MacOS-Betriebssystemen. |
| [Windows](./odbc/windows/index.md)     | &nbsp; | Informationen zur Verwendung von ODBC unter dem Windows-Betriebssystem. |
| [Verwaltung](../odbc/admin/index.md) | &nbsp; | Das Verwaltungs Tool zum Verwalten von ODBC-Datenquellen. |
| [Microsoft](../odbc/microsoft/index.md)  | &nbsp; | Verschiedene ODBC-Treiber, die von Microsoft erstellt und bereitgestellt werden. |
| [Konzeptionell und Verweis](../odbc/reference/index.md) | &nbsp; | Konzeptionelle Informationen zur ODBC-Schnittstelle, zusätzlich zur herkömmlichen Referenz. |
| &nbsp; " | [Anhänge](../odbc/reference/appendixes/index.md)    | Zustands Übergangs Tabellen, ODBC-Cursor Bibliothek und mehr. |
| &nbsp; " | [Entwickeln der APP](../odbc/reference/develop-app/index.md)  | Funktionen, Handles und vieles mehr. |
| &nbsp; " | [Entwickeln von Treibern](../odbc/reference/develop-driver/index.md) | Erfahren Sie, wie Sie einen eigenen ODBC-Treiber entwickeln, wenn Sie über eine spezialisierte Datenquelle verfügen. |
| &nbsp; " | [Installieren](../odbc/reference/install/index.md) | ODBC-Installation, Unterschlüssel und mehr. |
| &nbsp; " | [Syntax](../odbc/reference/syntax/index.md)   | APIs für Setup, Installer, Übersetzung und Datenzugriff. |
| &nbsp; | &nbsp; | <br /> |



<a name="an-170-php-docu" />

## <a name="php-logoimage-ref-360-php-php"></a>![PHP-Logo][image-ref-360-php] PHP

Sie können PHP verwenden, um mit SQL Server zu interagieren. Den Stamm der PHP-Dokumentation finden Sie [hier](./php/index.md).

#### <a name="code-examples"></a>Codebeispiele

|||
| :-- | :-- |
| [Proof of concept connecting to SQL using PHP (Proof of Concept für Verbindungen mit SQL mithilfe von PHP)](./php/step-3-proof-of-concept-connecting-to-sql-using-php.md) | Ein kleines Codebeispiel konzentriert sich auf das verbinden und Abfragen von SQL Server. |
| [Connect resiliently to SQL with PHP (Herstellen stabiler SQL-Verbindungen mit PHP)](./php/step-4-connect-resiliently-to-sql-with-php.md) | Wiederholungs Logik in einem Codebeispiel, da bei Verbindungen über das Internet und die Cloud gelegentlich Zeit-und konnektivitätsverluste auftreten können. |
| [Azure SQL-Datenbank: Verwenden von PHP zum Abfragen](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-php) | Beispiel für eine Azure SQL-Datenbank. |
| [Erstellen von PHP-Apps für die Verwendung von SQL Server für RHEL](https://www.microsoft.com/sql-server/developer-get-started/php/rhel/) | Konfigurationsinformationen, zusammen mit Codebeispielen. |
| &nbsp; | <br /> |



<a name="an-180-python-docu" />

## <a name="python-logoimage-ref-370-python-python"></a>![Python-Logo][image-ref-370-python] Python


Sie können python verwenden, um mit SQL Server zu interagieren.

#### <a name="code-examples"></a>Codebeispiele

|||
| :-- | :-- |
| [Proof of Concept für das Herstellen einer Verbindung mit SQL mit python mithilfe von pyodbc](./python/pyodbc/step-3-proof-of-concept-connecting-to-sql-using-pyodbc.md) | Ein kleines Codebeispiel konzentriert sich auf das verbinden und Abfragen von SQL Server. |
| [Azure SQL-Datenbank: Verwenden von python zum Abfragen](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-python) | Beispiel für eine Azure SQL-Datenbank. |
| [Erstellen von PHP-Apps für die Verwendung von SQL Server in SLES](https://www.microsoft.com/sql-server/developer-get-started/python/sles/) | Konfigurationsinformationen, zusammen mit Codebeispielen. |
| &nbsp; | <br /> |

#### <a name="documentation"></a>Dokumentation

| Bereich | und Beschreibung |
| :--- | :---------- |
| [Python zu SQL Server](./python/index.md) | Der Stamm der Dokumentation. |
| [pymssql-Treiber](./python/pymssql/index.md) | Microsoft verwaltet oder testet den pymssql-Treiber nicht.<br /><br />Der pymssql-Verbindungs Treiber ist eine einfache Schnittstelle zu SQL-Datenbanken, die in Python-Programmen verwendet werden können. Pymssql baut auf freetds auf, um eine Python DB-API-Schnittstelle (PEP-249) für Microsoft SQL Server bereitzustellen. |
| [pyodbc-Treiber](./python/pyodbc/index.md)   | Der pyodbc-Verbindungs Treiber ist ein Open-Source-Python-Modul, das den Zugriff auf ODBC-Datenbanken vereinfacht. Es implementiert die Spezifikation der DB-API 2,0, bietet jedoch noch mehr Pythonic-Unterstützung. |
| &nbsp; | <br /> |


<a name="an-190-ruby-docu" />

## <a name="ruby-logoimage-ref-380-ruby-ruby"></a>![Ruby-Logo][image-ref-380-ruby] Ruby

Sie können Ruby verwenden, um mit SQL Server zu interagieren. Das Stammverzeichnis unserer Ruby-Dokumentation finden Sie [hier](./ruby/index.md).

#### <a name="code-examples"></a>Codebeispiele

|||
| :-- | :-- |
| [Proof of Concept für Verbindungen mit SQL mithilfe von PHP](./ruby/step-3-proof-of-concept-connecting-to-sql-using-ruby.md) | Ein kleines Codebeispiel konzentriert sich auf das verbinden und Abfragen von SQL Server. |
| [Azure SQL-Datenbank: Verwenden von Ruby zum Abfragen](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-ruby) | Beispiel für eine Azure SQL-Datenbank. |
| [Erstellen von Ruby-Apps für die Verwendung von SQL Server unter MacOS](https://www.microsoft.com/sql-server/developer-get-started/ruby/mac/) | Konfigurationsinformationen, zusammen mit Codebeispielen. |
| &nbsp; | <br /> |



<a name="an-204-aka-ms-sqldev" />

## <a name="build-an-app-website-for-sql-client-developmenthttpswwwmicrosoftcomsql-serverdeveloper-get-started"></a>[Build-an-App-Website für die SQL-Client Entwicklung](https://www.microsoft.com/sql-server/developer-get-started/)


Auf unseren Webseiten [*Build-an-App*](https://www.microsoft.com/sql-server/developer-get-started/) können Sie aus einer langen Liste von Programmiersprachen auswählen, um eine Verbindung mit SQL Server herzustellen. Und das Client Programm kann eine Vielzahl von Betriebssystemen ausführen.

*Build-a-app* betont Einfachheit und Vollständigkeit für den Entwickler, der gerade erst gestartet wird. In den folgenden Schritten werden die folgenden Aufgaben erläutert:

1. Installieren von Microsoft SQL Server
2. Hier erfahren Sie, wie Sie Tools und Treiber herunterladen und installieren.
3. So nehmen Sie ggf. erforderliche Konfigurationen für Ihr ausgewähltes Betriebssystem vor.
4. Kompilieren des bereitgestellten Quellcodes.
5. Ausführen des Programms.

Im nächsten Abschnitt werden einige ungefähre Details der auf der Website bereitgestellten Details aufgeführt:

#### <a name="java-on-ubuntu"></a>Java unter Ubuntu:

1. Einrichten Ihrer Umgebung
    - Schritt 1.1: Installieren von SQL Server
    - Schritt 1,2 Installieren von Java
    - Schritt 1,3 Installieren des Java Development Kit (JDK)
    - Schritt 1,4 Installieren von Maven
2. Erstellen einer Java-Anwendung mit SQL Server
    - Schritt 2,1 Erstellen einer Java-App, die eine Verbindung mit SQL Server herstellt und Abfragen ausführt
    - Schritt 2,2 Erstellen einer Java-App, die eine Verbindung zu SQL Server mithilfe des beliebten Framework-Ruhe Zustands herstellt
3. Machen Sie Ihre Java-App bis zu 100-mal schneller
    - Schritt 3,1 Erstellen einer Java-App zur Veranschaulichung von columnstore-Indizes

#### <a name="python-on-windows"></a>Python unter Windows:

1. Einrichten Ihrer Umgebung
    - Schritt 1.1: Installieren von SQL Server
    - Schritt 1,2 Installieren von python
    - Schritt 1,3 installieren Sie den ODBC-Treiber und das SQL-Befehlszeilen-Hilfsprogramm für SQL Server
2. Erstellen einer python-Anwendung mit SQL Server
    - Schritt 2,1 Installieren des python-Treibers für SQL Server
    - Schritt 2,2 Erstellen einer Datenbank für Ihre Anwendung
    - Schritt 2,3 Erstellen einer python-APP, die eine Verbindung mit SQL Server herstellt und Abfragen ausführt
3. Machen Sie Ihre python-app bis zu 100-mal schneller
    - Schritt 3,1 Erstellen einer neuen Tabelle mit 5 Millionen mithilfe von "sqlcmd"
    - Schritt 3,2 Erstellen Sie eine python-APP, die diese Tabelle abfragt und die benötigte Zeit misst.
    - Schritt 3,3 Messen, wie lange die Abfrage ausgeführt wird
    - Schritt 3,4 fügen Sie der Tabelle einen columnstore--Index hinzu.
    - Schritt 3,5 Messen, wie lange es dauert, bis die Abfrage mit einem columnstore--Index ausgeführt wird

Die folgenden Screenshots zeigen Ihnen, wie die Website zur SQL-Entwicklungsdokumentation aussieht.

#### <a name="choose-a-language"></a>Wählen Sie eine Sprache aus:

![SQL dev-Website, Einstieg][image-ref-390-aka-ms-sqldev-choose-language]

&nbsp;

#### <a name="choose-an-operating-system"></a>Auswählen eines Betriebssystems:

![SQL dev-Website, Java Ubuntu][image-ref-400-aka-ms-sqldev-java-ubuntu]

&nbsp;



## <a name="other-development"></a>Andere Entwicklung


Dieser Abschnitt enthält Links zu anderen Entwicklungsoptionen. Dazu gehört die Verwendung derselben Sprachen für die Azure-Entwicklung im Allgemeinen. Die Informationen gehen über die Zielsetzung der Azure SQL-Datenbank und der Microsoft SQL Server hinaus.

#### <a name="developer-hub-for-azure"></a>Developer Hub für Azure

- [Developer Hub für Azure](https://docs.microsoft.com/azure/)
- [Azure für .NET-Entwickler](https://docs.microsoft.com/dotnet/azure/)
- [Azure für Java-Entwickler](https://docs.microsoft.com/java/azure/)
- [Azure für Node. js-Entwickler](https://docs.microsoft.com/nodejs/azure/)
- [Azure für python-Entwickler](https://docs.microsoft.com/python/azure/)
- [Erstellen einer PHP-Web-App in Azure](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-php)

#### <a name="other-languages"></a>Andere Sprachen

- [Erstellen von Go-Apps mithilfe von SQL Server unter Windows](https://www.microsoft.com/sql-server/developer-get-started/go/windows/)



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

