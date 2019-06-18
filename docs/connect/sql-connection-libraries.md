---
title: Verbindungsbibliotheken für Microsoft SQL-Datenbanken | Microsoft-Dokumentation
description: Bietet Downloadlinks für Module, die Verbindung mit Microsoft SQL Server und Azure SQL-Datenbank aus einer Vielzahl von clientprogrammiersprachen ermöglichen.
author: MightyPen
ms.prod: sql
ms.technology: ''
ms.custom: ''
ms.topic: article
ms.date: 06/18/2018
ms.author: genemi
ms.openlocfilehash: 7f759dbe9022cff557461d900a35b3ccc91d2c4b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62862419"
---
# <a name="connection-modules-for-microsoft-sql-databases"></a>Verbindungs-Modulen für Microsoft SQL-Datenbanken

Dieser Artikel enthält Links zum Herunterladen der Verbindung Modulen oder *Treiber* , die Ihre Clientprogramme verwenden können, für die Interaktion mit [Microsoft SQL Server](../relational-databases/database-features.md), und klicken Sie mit seinem zwilling in der Cloud [Azure SQL-Datenbank](https://docs.microsoft.com/azure/sql-database/). Treiber stehen für eine Vielzahl von Programmiersprachen, die unter den folgenden Betriebssystemen unterstützt:

- Linux
- macOS
- Windows

#### <a name="oop-to-relational-mismatch"></a>OOP zu relationalen Konflikt

*Relationale*: Clientprogramme, die häufig in einer objektorientierten Programmiersprache (OOP) Ihrer geschrieben werden, verwenden SQL-Treiber, die abgefragte Daten in einem Format zurückzugeben, die mehrere relationale, als objektorientierte ist. C# -Code mithilfe von ADO.NET ist ein Beispiel. Die relationalen-OOP-Format-Konflikt erschwert manchmal den OOP-Code zu schreiben und zu verstehen.

*ORM*: anderen Treibern oder Frameworks abgefragte Daten zurückgibt, in der OOP-Format, das den Konflikt zu vermeiden. Diese Treiber funktionieren wird erwartet, dass die Klassen entsprechend die Datenspalten der bestimmte SQL-Tabellen definiert wurden. Der Treiber führt dann die *objektrelationales Mapping* (ORM) als eine Instanz einer Klasse abgefragte Daten zurückgibt. Microsoft Entity Framework (EF) für C#-Code, und der Ruhezustand für Java, sind zwei Beispiele.

Diesem Artikel widmet getrennte Abschnitten, um diese beiden Arten von verbindungstreiber.

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

| Sprache | Den SQL-Treiber herunterladen |
| :------- | :---------------------- |
| C# | [ADO.NET](https://www.microsoft.com/net/download/)<br /><br />[.NET Core für Linux-Ubuntu](https://www.microsoft.com/net/core#Ubuntu)<br />[.NET Core für MacOS](https://www.microsoft.com/net/core#macos)<br />[.NET Core für Windows](https://www.microsoft.com/net/core) |
| C++ | [ODBC](./odbc/download-odbc-driver-for-sql-server.md)<br /><br />[OLE DB](./oledb/download-oledb-driver-for-sql-server.md) |
| Java | [JDBC](./jdbc/download-microsoft-jdbc-driver-for-sql-server.md) |
| Node.js | [Node.js-Treiber, installationsanweisungen](./node-js/step-1-configure-development-environment-for-node-js-development.md) |
| PHP | [PHP](./php/download-drivers-php-sql-server.md) |
| Python | [pyodbc, Installationsanweisungen](./python/pyodbc/step-1-configure-development-environment-for-pyodbc-python-development.md)<br />[Herunterladen von ODBC](./odbc/download-odbc-driver-for-sql-server.md) |
| Ruby | [Ruby-Treiber, installationsanweisungen](./ruby/step-1-configure-development-environment-for-ruby-development.md)<br />[Downloadseite für Ruby](https://rubyinstaller.org/downloads/) |
| &nbsp; | <br /> |

<a name="anchor-40-drivers-orm-access" />

## <a name="drivers-for-orm-access"></a>Treiber für ORM-Zugriff


Die folgende Tabelle enthält Beispiele für Object Relational Mapping (ORM)-Frameworks, mit denen Clientanwendungen eine Verbindung mit Microsoft SQL-Datenbanken herstellen.


| Sprache | ORM-Treiber-download |
| :------- | :------------------ |
| C# | [Entity Framework Core](https://docs.microsoft.com/ef/core/)<br />[Entitätsframework (6.x oder höher)](https://docs.microsoft.com/ef/) |
| Java | [Ruhezustand ORM](https://hibernate.org/orm)|
| PHP | [Seinen-ORM, eingeschlossen in Laravel-Installation](https://laravel.com/docs/) |
| Node.js | [Sequelize ORM](https://docs.sequelizejs.com) |
| Python | [Django](https://www.djangoproject.com/) |
| Ruby | [Ruby on Rails](https://rubyonrails.org/) |


<a name="anchor-60-build-an-app-webpages" />

## <a name="build-an-app-webpages"></a>Build-ein-app-Webseiten
[https://aka.ms/sqldev](https://aka.ms/sqldev) gelangen Sie auf einen Satz von *Build-ein-app* Webseiten. Die Webseiten Aufschluss darüber geben zahlreiche Kombinationen von Sprache, Betriebssystem und SQL-Verbindung-Treiber-Programmierung. Zwischen den Informationen, die von der Build-ein-app-Webseiten bereitgestellt werden Sie die folgenden Elemente:

- Details dazu, wie Sie von Anfang, für jede Kombination von Sprache, Betriebssystem und Treiber beginnen.
    - Anweisungen zum Installieren der aktuellen SQL-Verbindung-Treiber.
- Codebeispiele für jedes der folgenden Elemente:
    - Objektrelationale Codebeispiele.
    - ORM-Codebeispiele
    - Columnstore-Index-Demos für eine schnellere Leistung.

#### <a name="first-page-of-build-an-app-webpages"></a>Erste Seite des Build-ein-app-Webseiten
![Build-ein-app-Webseiten, erste Seite-screenshot][image-ref-163-buildanapp-webpages-first-page]

#### <a name="menu-for-java---ubuntu-of-build-an-app-webpages"></a>Menü für Java – Ubuntu von Build-ein-app-Webseiten
![Build-ein-app-Webseiten und Java-Ubuntu-Menü][image-ref-167-buildanapp-webpages-menu-java-ubuntu]

&nbsp;

## <a name="related-links"></a>Verwandte Links
- [Codebeispiele für die Verbindung mit Azure SQL-Datenbank in der Cloud, mit Java und anderen Sprachen](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java).

<!-- Image references -->

[image-ref-163-buildanapp-webpages-first-page]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-choose-language-g21.png
[image-ref-167-buildanapp-webpages-menu-java-ubuntu]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-java-ubuntu-c31.png
