---
title: Verbindungs Bibliotheken für Microsoft SQL-Datenbanken | Microsoft-Dokumentation
description: Bietet Download Links für Module, die die Verbindung mit Microsoft SQL Server und Azure SQL-Datenbank über eine Vielzahl von Client Programmiersprachen ermöglichen.
author: MightyPen
ms.prod: sql
ms.technology: ''
ms.custom: ''
ms.topic: article
ms.date: 06/18/2018
ms.author: genemi
ms.openlocfilehash: 71254b937c4c0173af9e1549efb98a0b42f65e02
ms.sourcegitcommit: 66dbc3b740f4174f3364ba6b68bc8df1e941050f
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2019
ms.locfileid: "73632818"
---
# <a name="connection-modules-for-microsoft-sql-databases"></a>Verbindungs Module für Microsoft SQL-Datenbanken

Dieser Artikel bietet Download Links zu Verbindungs Modulen oder *Treibern* , die von Ihren Client Programmen für die Interaktion mit [Microsoft SQL Server](../relational-databases/database-features.md)und mit dem zugehörigen Zwilling in der [Azure SQL](https://docs.microsoft.com/azure/sql-database/)-Cloud-Cloud verwendet werden können. Treiber sind für eine Vielzahl von Programmiersprachen verfügbar, die unter den folgenden Betriebssystemen ausgeführt werden:

- Linux
- macOS
- Windows

#### <a name="oop-to-relational-mismatch"></a>Nicht übereinstimmender OOP-zu-relationaler Konflikt

*Relational*: Client Programme, die in einer OOP-Sprache (Object-Oriented Programming) geschrieben wurden, verwenden häufig SQL-Treiber, die abgefragte Daten in einem Format zurückgeben, das mehr relationaler als objektorientiert ist. C#die Verwendung von ADO.net ist ein Beispiel. Der Konflikt zwischen OOP-relationalem Format ist manchmal schwerer zu schreiben und zu verstehen.

*ORM*: andere Treiber oder Frameworks geben abgefragte Daten im OOP-Format zurück, sodass keine Übereinstimmung gefunden wird. Diese Treiber funktionieren, indem Sie erwarten, dass Klassen so definiert wurden, dass Sie den Datenspalten bestimmter SQL-Tabellen entsprechen. Der Treiber führt dann die *Objekt relationale Zuordnung* (ORM) aus, um abgefragte Daten als eine Instanz einer Klasse zurückzugeben. Die Microsoft-Entity Framework (EF) C#for und Hibernate für Java sind zwei Beispiele.

Im vorliegenden Artikel werden die beiden Arten von Verbindungs Treibern in separaten Abschnitten beschrieben.

<a name="anchor-20-drivers-relational-access" />

## <a name="drivers-for-relational-access"></a>Treiber für relationalen Zugriff


<!--
Each given Microsoft Download Center page should be enhanced
with a link to the next NEWER version page, on the day that the
original page is no longer the latest because the newer page is being added.
But this policy is not agreed on or observed,
putting the links in the following table at risk for being outdated.

PHP driver in Github.com also uses this FWLink:  https://go.microsoft.com/fwlink/?LinkID=518036 ,
although the FWLink is less precise than is https://github.com/Microsoft/msphpsql/tree/dev#install-unix .
-->

| Sprache | Herunterladen des SQL-Treibers |
| :------- | :---------------------- |
| C# | [ADO.NET](https://www.microsoft.com/net/download/)<br />[Microsoft.Data.SqlClient](https://www.nuget.org/packages/Microsoft.Data.SqlClient/)<br /><br />[.Net Core, für Linux-Ubuntu](https://www.microsoft.com/net/core#Ubuntu)<br />[.Net Core für MacOS](https://www.microsoft.com/net/core#macos)<br />[.Net Core, für Windows](https://www.microsoft.com/net/core) |
| C++ | [ODBC](./odbc/download-odbc-driver-for-sql-server.md)<br /><br />[OLE DB](./oledb/download-oledb-driver-for-sql-server.md) |
| Java | [JDBC](./jdbc/download-microsoft-jdbc-driver-for-sql-server.md) |
| Node.js | [Node. js-Treiber, Installationsanweisungen](./node-js/step-1-configure-development-environment-for-node-js-development.md) |
| PHP | [PHP](./php/download-drivers-php-sql-server.md) |
| Python | [pyodbc, Installationsanweisungen](./python/pyodbc/step-1-configure-development-environment-for-pyodbc-python-development.md)<br />[Herunterladen von ODBC](./odbc/download-odbc-driver-for-sql-server.md) |
| Ruby | [Ruby-Treiber, Installationsanweisungen](./ruby/step-1-configure-development-environment-for-ruby-development.md)<br />[Ruby-Downloadseite](https://rubyinstaller.org/downloads/) |
| &nbsp; | <br /> |

<a name="anchor-40-drivers-orm-access" />

## <a name="drivers-for-orm-access"></a>Treiber für den ORM-Zugriff


In der folgenden Tabelle sind Beispiele für ORM-Frameworks (Object Relational Mapping) aufgelistet, die Client Anwendungen zum Herstellen einer Verbindung mit Microsoft SQL-Datenbanken verwenden.


| Sprache | ORM-Treiber Download |
| :------- | :------------------ |
| C# | [Entity Framework Core](https://docs.microsoft.com/ef/core/)<br />[Entity Framework (6. x oder höher)](https://docs.microsoft.com/ef/) |
| Java | [Hibernate ORM](https://hibernate.org/orm)|
| PHP | [Eloquentes ORM, in laravel install enthalten](https://laravel.com/docs/) |
| Node.js | [Sequelize ORM](https://docs.sequelizejs.com) |
| Python | [Django](https://www.djangoproject.com/) |
| Ruby | [Ruby on Rails](https://rubyonrails.org/) |


<a name="anchor-60-build-an-app-webpages" />

## <a name="build-an-app-webpages"></a>Build-an-App-Webseiten
[https://aka.ms/sqldev](https://aka.ms/sqldev) gelangen Sie zu einer Gruppe von *Build-an-App-* Webseiten. Die Webseiten enthalten Informationen zu zahlreichen Kombinationen aus Programmiersprache, Betriebssystem und SQL-Verbindungs Treiber. Zu den Informationen, die von den Webseiten Build-an-App bereitgestellt werden, zählen die folgenden Elemente:

- Details zu den ersten Schritten von Anfang an für jede Kombination aus Sprache + Betriebssystem und Treiber.
    - Anweisungen zum Installieren der aktuellen SQL-Verbindungs Treiber.
- Code Beispiele für jedes der folgenden Elemente:
    - Objekt relationale Codebeispiele.
    - ORM-Codebeispiele
    - Columnstore-Index Demonstrationen für eine wesentlich schnellere Leistung.

#### <a name="first-page-of-build-an-app-webpages"></a>Erste Seite, von Build-an-App-Webseiten
![Build-a-app-Webseiten, Screenshot der ersten Seite][image-ref-163-buildanapp-webpages-first-page]

#### <a name="menu-for-java---ubuntu-of-build-an-app-webpages"></a>Menü für Java-Ubuntu von Build-an-App-Webseiten
![Build-an-App-Webseiten, Menü Java Ubuntu][image-ref-167-buildanapp-webpages-menu-java-ubuntu]

&nbsp;

## <a name="related-links"></a>Verwandte Links
- [Code Beispiele für das Herstellen einer Verbindung mit Azure SQL-Datenbank in der Cloud mit Java und anderen Sprachen](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java).

<!-- Image references -->

[image-ref-163-buildanapp-webpages-first-page]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-choose-language-g21.png
[image-ref-167-buildanapp-webpages-menu-java-ubuntu]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-java-ubuntu-c31.png
