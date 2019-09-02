---
title: Treiber Verlauf für Microsoft SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/04/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c0fcc2172cca192c8c7580450ab50b4416f9ec2d
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70154183"
---
# <a name="driver-history-for-microsoft-sql-server"></a>Treiber Verlauf für Microsoft SQL Server

Auf dieser Seite werden die Daten Verbindungstechnologien von Microsoft zum Herstellen einer Verbindung mit SQL Server beschrieben.

## <a name="odbc"></a>ODBC

Es gibt drei Generationen von Microsoft ODBC-Treibern für SQL Server. Der erste ODBC-Treiber "SQL Server" wird weiterhin als Teil der [Windows-Datenzugriffs Komponenten](#microsoft-or-windows-data-access-components)ausgeliefert. Es wird nicht empfohlen, diesen Treiber für die neue Entwicklung zu verwenden. Ab SQL Server 2005 umfasst das [SQL Server Native Client](#sql-server-native-client) eine ODBC-Schnittstelle und ist der ODBC-Treiber, der mit SQL Server 2005 bis SQL Server 2012 ausgeliefert wurde. Es wird nicht empfohlen, diesen Treiber für die neue Entwicklung zu verwenden. Nach SQL Server 2012 ist der [Microsoft ODBC Driver for SQL Server](#microsoft-odbc-driver-for-sql-server) der Treiber, der mit den neuesten Server Funktionen aktualisiert wird.

### <a name="sql-server-native-client"></a>SQL Server Native Client

SQL Server Native Client ist eine eigenständige Bibliothek, die sowohl für OLE DB als auch für ODBC verwendet wird. SQL Server Native Client (häufig abgekürzte SNAC) war in SQL Server 2005 bis 2012 enthalten. SQL Server Native Client können für Anwendungen verwendet werden, die die neuen Features nutzen müssen, die in SQL Server 2005 bis SQL Server 2012 eingeführt wurden. (Die Microsoft/Windows-Datenzugriffs Komponenten werden für diese neuen Features in SQL Server nicht aktualisiert.) Für neue Features über SQL Server 2012 hinaus werden SQL Server Native Client nicht aktualisiert. Wechseln Sie zum Microsoft ODBC Driver for SQL Server oder Microsoft OLE DB-Treiber für SQL Server, wenn Sie die neuen SQL Server Features nutzen möchten.

Eine umfassende Dokumentation der SQL Server Native Client finden Sie in der [Dokumentation zu SQL Server Native Client](../relational-databases/native-client/sql-server-native-client-programming.md).

### <a name="microsoft-odbc-driver-for-sql-server"></a>Microsoft ODBC Driver for SQL Server

Nach SQL Server 2012 wurde der primäre ODBC-Treiber für SQL Server als Microsoft ODBC Driver for SQL Server entwickelt und freigegeben. Weitere Informationen finden Sie in der [Microsoft ODBC Driver for SQL Server-Dokumentation](./odbc/microsoft-odbc-driver-for-sql-server.md).

## <a name="ole-db"></a>OLE DB

Es gibt drei verschiedene Generationen von Microsoft OLE DB-Anbietern für SQL Server. Die erste „Microsoft OLE DB-Anbieter für SQL Server“ (SQLOLEDB) ist weiterhin als Teil von [Windows Data Access Components](#microsoft-or-windows-data-access-components) erhältlich. Dieser Anbieter wird nicht mit neuen Features aktualisiert, und es wird nicht empfohlen, diesen Treiber für die neue Entwicklung zu verwenden. Ab SQL Server 2005 enthält die [SQL Server Native Client](#sql-server-native-client) eine OLE DB Provider-Schnittstelle (SQLNCLI) und ist der OLE DB Anbieter, der mit SQL Server 2005 bis SQL Server 2017 ausgeliefert wurde. [Seit 2011 gilt dieser jedoch als veraltet](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/), und es wird nicht empfohlen, diesen Treiber für neue Bereitstellungen zu verwenden. In 2017 wurde die Datenzugriffs Technologie nachfolgend nicht mehr als veraltet markiert OLE DB, und für 2018 [wurde eine neue geplante Version angekündigt](https://blogs.msdn.microsoft.com/sqlnativeclient/2017/10/06/announcing-the-new-release-of-ole-db-driver-for-sql-server/) . Der neue OLE DB Anbieter heißt "Microsoft OLE DB Driver for SQL Server" (msoledbsql) und wird zurzeit verwaltet und unterstützt.

## <a name="adonet"></a>ADO.NET

ADO.net wurde mit dem Microsoft .NET Framework eingeführt und wird weiterhin verbessert und gewartet. Es ist eine Kernkomponente des Microsoft .NET-Frameworks. Weitere Informationen finden Sie unter [Microsoft ADO.net for SQL Server](ado-net/microsoft-ado-net-for-sql-server.md).

## <a name="jdbc"></a>JDBC

### <a name="microsoft-jdbc-driver-for-sql-server"></a>Microsoft JDBC-Treiber für SQL Server

Der Microsoft JDBC-Treiber für SQL Server wurde in 2000 eingeführt und wird weiterhin verbessert und gewartet. Es war in 2016 Open Source. Die neuesten Informationen, einschließlich Informationen zum Herunterladen des Treibers, finden Sie unter [Übersicht über den JDBC-Treiber](./jdbc/overview-of-the-jdbc-driver.md).

## <a name="php"></a>PHP

### <a name="microsoft-drivers-for-php-for-sql-server"></a>Microsoft-Treiber für PHP für SQL Server

Die Microsoft-Treiber für PHP für SQL Server werden in 2009 als Open-Source-Projekt eingeführt und werden weiterhin verbessert und gewartet. Die neuesten Informationen, einschließlich des Downloads des PHP-Treibers, finden Sie unter [Microsoft Drivers for PHP for SQL Server](./php/microsoft-php-driver-for-sql-server.md).

## <a name="nodejs"></a>Node.js

### <a name="microsoft-driver-for-nodejs-for-sql-server"></a>Microsoft-Treiber für Node. js für SQL Server

Mit dem Microsoft-Treiber für Node. js für SQL Server können Node. js-Anwendungen in Microsoft Windows und Microsoft Azure auf Microsoft SQL Server und Microsoft Azure SQL-Datenbank zugreifen. Der Schwerpunkt des Entwicklungsaufwands liegt nicht mehr auf diesem Treiber. Es wird nicht empfohlen, neue Anwendungen zu erstellen, indem Sie den Microsoft-Treiber für Node. js für SQL Server verwenden.

Weitere Informationen zum Microsoft-Treiber für Node. js für SQL Server finden Sie unter [WindowsAzure/Node-SQLServer](https://github.com/Azure/node-sqlserver).

### <a name="tedious"></a>Langwei

Microsoft trägt derzeit zu und unterstützt das mühsame Open Source-Modul in Node. js für die Konnektivität mit SQL Server mithilfe von JavaScript. Weitere Informationen finden Sie unter [node. js-Treiber für SQL Server](./node-js/node-js-driver-for-sql-server.md).

## <a name="microsoft-or-windows-data-access-components"></a>Microsoft-oder Windows-Datenzugriffs Komponenten

Microsoft/Windows Data Access Components (MDAC/WDac) werden von Windows für die Anwendungs Abwärtskompatibilität ausgeliefert und unterstützt und sind nicht Teil des aktuellen SQL Server-Technologie Stapels. Komponenten in MDAC/WDac werden keine neuen Features hinzugefügt, und es wird nicht empfohlen, Sie für die Entwicklung neuer Anwendungen zu verwenden.

Im Rahmen dieses Dokuments können Sie den MDAC/WDac-Stapel auf der Grundlage von Technologie und Produkten in die folgenden Komponenten aufteilen:

* **ADO** (einschließlich ADOMD und ADOX)
* **OLE DB** (einschließlich OLE DB Kerndienste, SQL Server OLE DB-Anbieter, Oracle OLE DB-Anbieter, OLE DB Anbieter für ODBC-Treiber, datenshape-Anbieter und Remote Datenanbieter)
* **ODBC** (einschließlich ODBC-Treiber-Manager, SQL ODBC-Treiber und Oracle ODBC-Treiber)

### <a name="mdacwdac-components"></a>MDAC/WDac-Komponenten

MDAC/WDac umfasst folgende Komponenten:

* **ODBC:** Die Schnittstelle von Microsoft Open Database Connectivity (ODBC) ist eine Programmiersprache der C-Programmiersprache, die Anwendungen den Zugriff auf Daten von einer Vielzahl von Datenbank-Management Systemen (DBMS) ermöglicht. Anwendungen, die diese API verwenden, sind nur auf den Zugriff auf relationale Datenquellen beschränkt.
* **OLE DB:** OLE DB ist ein Satz von COM-Schnittstellen für den Zugriff auf Daten in einer Vielzahl von Daten speichern. OLE DB Anbieter sind für den Zugriff auf Daten in Datenbanken, Dateisystemen, Nachrichten speichern, Verzeichnisdiensten, Workflows und Dokument speichern vorhanden.
* **ADO:** ActiveX Data Objects (ADO) stellt ein allgemeines Programmiermodell bereit. Obwohl es etwas weniger leistungsfähiger ist als das direkte Programmieren in OLE DB oder ODBC, ist ADO einfach zu erlernen und zu verwenden. Sie kann in Skriptsprachen wie Microsoft Visual Basic Scripting Edition (VBScript) oder Microsoft JScript verwendet werden.
* **ADOMD:** ADO Alem (ADOMD) ist für die Verwendung mit mehrdimensionalen Datenanbietern wie Microsoft OLAP Provider, auch bekannt als Microsoft Analysis Services Provider. Seit MDAC 2,0 wurden keine wesentlichen Verbesserungen an Features vorgenommen.
* **ADOX:** ADO-Erweiterungen für DDL und Security (ADOX) ermöglichen das Erstellen und Ändern von Definitionen einer Datenbank, Tabelle, eines Indexes oder einer gespeicherten Prozedur. Sie können ADOX mit beliebigen Anbietern verwenden. Der Anbieter von Microsoft Jet OLE DB bietet vollständige Unterstützung für ADOX, während der Microsoft SQL Server OLE DB-Anbieter eingeschränkte Unterstützung bietet.
* **Microsoft SQL Server Netzwerk Bibliotheken:** Mit den SQL Server Netzwerk Bibliotheken können SQLOLEDB und SQLODBC mit der SQL Server Datenbank kommunizieren. Die folgenden SQL Server Netzwerk Bibliotheken sind in MDAC/WDac-Releases veraltet: Banyan Vines, AppleTalk, ServerNet, IPX/SPX, Giganet und RPC. TCP/IP und Named Pipes werden weiterhin unterstützt und sind auf dem 64-Bit-Windows-Betriebssystem verfügbar.
* **MSDASQL:** Der Microsoft OLE DB-Anbieter für ODBC (MSDASQL) ermöglicht Anwendungen, die auf OLE DB und ADO basieren (die intern OLEDB verwenden), den Zugriff auf Datenquellen über einen ODBC-Treiber. Bei MSDASQL handelt es sich um einen OLE DB-Anbieter, der anstelle einer Datenbank eine Verbindung mit ODBC herstellt. Er ist als Brücke von OLE DB zu einem ODBC-Treiber gedacht, wenn für eine Datenquelle kein direkter OLE DB Anbieter vorhanden ist. Msdasql ist im Lieferumfang des Windows-Betriebssystems enthalten, und Windows Server 2008 und Vista SP1 waren die ersten Windows-Releases, die eine 64-Bit-Version der Technologie enthalten.

### <a name="deprecated-mdacwdac-components"></a>Als veraltet markierte MDAC/WDac-Komponenten

Diese Komponenten werden in der aktuellen Version von MDAC/WDac weiterhin unterstützt, aber in zukünftigen Versionen möglicherweise entfernt. Wenn Sie neue Anwendungen entwickeln, empfiehlt Microsoft, die Verwendung dieser Komponenten zu vermeiden. Entfernen Sie außerdem alle Abhängigkeiten dieser Komponenten, wenn Sie vorhandene Anwendungen aktualisieren oder ändern.

* **SQLOLEDB:** Der Microsoft OLE DB-Anbieter für SQL Server (SQLOLEDB), der den Zugriff auf Microsoft SQL Server unterstützt, ist veraltet. Die Konnektivität mit zukünftigen Versionen von SQL Server wird möglicherweise nicht unterstützt. Die Möglichkeit, eine Verbindung mit früheren Versionen als SQL Server 7 herzustellen, wird nach Windows 7 aus dem Betriebssystem entfernt. Neue Anwendungen sollten den Microsoft OLE DB-Treiber für SQL Server (msoledbsql) verwenden, der neue SQL Server Features unterstützt. Vorhandene Anwendungen sollten auch zum Microsoft OLE DB-Treiber für SQL Server migrieren, um die Leistung, Zuverlässigkeit und unter Stütz barkeit zu verbessern. Weitere Informationen finden Sie unter [Aktualisieren einer Anwendung auf OLE DB Treiber für SQL Server von MDAC](oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).
* **SQLODBC:** Der Microsoft SQL Server ODBC-Treiber (SQLODBC), der den Zugriff auf Microsoft SQL Server unterstützt, ist veraltet. Die Konnektivität mit zukünftigen Versionen von SQL Server wird möglicherweise nicht unterstützt. Die Möglichkeit, eine Verbindung mit früheren Versionen als SQL Server 7 herzustellen, wird nach Windows 7 aus dem Betriebssystem entfernt. Neue Anwendungen sollten das Microsoft ODBC Driver for SQL Server unter Windows verwenden, das neue SQL Server Features unterstützt. Vorhandene Anwendungen sollten auch zum Microsoft ODBC Driver for SQL Server migrieren, um die Leistung, die Zuverlässigkeit und die unter Stütz barkeit zu verbessern. Relevante Informationen finden Sie unter [Aktualisieren einer Anwendung in SQL Server Native Client von MDAC](../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md).
* **Microsoft Jet Datenbank-Engine 4,0:** Ab Version 2,6 enthält MDAC keine Jet-Komponenten mehr. Anders ausgedrückt: MDAC 2,6, 2,7 und 2,8 enthalten nicht Microsoft Jet, den Microsoft Jet OLE DB-Anbieter, die ODBC Desktop-Datenbanktreiber oder die Jet Data Access Objects (DAO). 

  Es gibt keine 64-Bit-Version des Jet-Datenbank-Engine, des Jet-OLEDB-Treibers, der Jet-ODBC-Treiber oder Jet DAO verfügbar. Weitere Informationen finden Sie im Knowledge Base-Artikel [957570](https://support.microsoft.com/kb/957570). Auf 64-Bit-Versionen von Windows wird 32-Bit Jet unter dem Windows WOW64-Subsystem ausgeführt. Weitere Informationen zu WOW64 finden Sie in der [MSDN WOW64-Dokumentation](/windows/desktop/WinProg64/wow64-implementation-details). Native 64-Bit-Anwendungen können nicht mit den 32-Bit-Jet-Treibern kommunizieren, die in WOW64 ausgeführt werden.

  Anstelle von Microsoft Jet empfiehlt Microsoft die Verwendung von [Microsoft SQL Server Express Edition](https://www.microsoft.com/sql-server/sql-server-editions-express) bei der Entwicklung neuer, nicht von Microsoft basierenden Access-Anwendungen, die einen relationalen Datenspeicher erfordern. Diese neuen oder konvertierten Jet-Anwendungen können Jet weiterhin mit der Verwendung von Microsoft Office 2003 und früheren Dateien (MDB und XLS) für nicht primäre Datenspeicherung verwenden. Allerdings sollten Sie für diese Anwendungen die Migration von Jet zum Microsoft Access Datenbank-Engine planen. Sie können [den Microsoft Access Datenbank-Engine herunterladen](https://www.microsoft.com/download/details.aspx?id=54920), der es Ihnen ermöglicht, aus bereits vorhandenen Dateien in den Dateiformaten Office 2003 (MDB und XLS) oder Office 2007 (*. accdb, *. xlsm, *. xlsx und *. xlsb) zu lesen und in diese zu schreiben.

  > [!IMPORTANT]
  > Lesen Sie den 2007 Office System-Endbenutzer-Lizenzvertrag für bestimmte Nutzungsbeschränkungen.

  > [!NOTE]
  > SQL Server Anwendungen können auch über den 2007 Office System-Treiber auf das 2007 Office-System und frühere Versionen von SQL Server heterogenen Datenkonnektivitäts-und Integrationen Services-Funktionen zugreifen. Darüber hinaus können 64-Bit-SQL Server Anwendungen auf 32-Bit-Jet-und 2007 Office-System Dateien mithilfe von 32-Bit-SQL Server Integration Services (SSIS) auf 64-Bit-Windows zugreifen.

* **Msdads:** Mit dem Microsoft OLE DB-Anbieter für die Daten Strukturierung (msdads) können Sie hierarchische Beziehungen zwischen Schlüsseln, Feldern oder Rowsets in einer Anwendung erstellen. Seit MDAC 2,1 wurden keine größeren Features Verbesserungen vorgenommen. Dieser Anbieter ist veraltet. Microsoft empfiehlt, anstelle von msdads XML zu verwenden.
* **Oracle ODBC-und Oracle-OLE DB:** Der Microsoft Oracle ODBC-Treiber (Oracle ODBC) und Microsoft OLE DB-Anbieter für Oracle (Oracle OLE DB) ermöglichen den Zugriff auf Oracle-Datenbankserver. Sie werden mithilfe von OCI (Oracle callinterface) Version 7 erstellt und bieten vollständige Unterstützung für Oracle 7. Außerdem wird die Oracle 7-Emulation verwendet, um eine eingeschränkte Unterstützung für Oracle 8-Datenbanken bereitzustellen. Oracle unterstützt keine Anwendungen mehr, die OCI-Aufrufe der Version 7 verwenden. Diese Technologien sind veraltet. Wenn Sie Oracle-Datenquellen verwenden, sollten Sie zu den von Oracle bereitgestellten Treibern und Anbietern migrieren.
* **RDS:** Remote Data Services (RDS) ist ein proprietärer Microsoft-Mechanismus für den Zugriff auf remoterecordsetobjekte über das Internet oder ein Intranet. RDS ist veraltet. seit MDAC 2,1 wurden keine größeren Funktions Verbesserungen an RDS vorgenommen. Microsoft hat den .NET Framework veröffentlicht, der über umfangreiche SOAP-Funktionen verfügt und RDS-Komponenten ersetzt. Alle RDS-Serverkomponenten werden nach Windows 7 aus dem Betriebssystem entfernt.
* **JRO:** Jet Replication Objects (JRO) ist veraltet. JRO wird in ADO mit Jet-Daten*Banken (. mdb) verwendet, um Jet-Datenbanken (. mdb) zu erstellen und zu komprimieren und die Jet-Replikations Verwaltung auszuführen. MDAC 2,7 ist die letzte Version. JRO ist auf dem 64-Bit-Windows-Betriebssystem nicht verfügbar. JRO wird im Microsoft Access 2007-Dateiformat (* . accdb) nicht unterstützt.
* **Unterstützung für 16-Bit-ODBC:** Wenn Sie 16-Bit-Anwendungen verwenden, sollten Sie zu einer 32-Bit-Anwendung migrieren. die 16-Bit-Funktionalität ist veraltet und wird aus 64-Bit-Betriebssystemen entfernt. Weitere Informationen finden Sie im [Knowledge Base-Artikel 896458](https://support.microsoft.com/kb/896458).
* **OleDb Simple Provider (msdaosp):** Der einfache OLEDB-Anbieter bietet ein Framework für das schnelle Entwickeln von OLE DB Anbietern über einfache Daten. Msdaosp ist veraltet.
* **ODBC-Cursor Bibliothek:** Die ODBC-Cursor Bibliothek (ODBCCR32. dll) stellt eingeschränkte Client seitige Daten Cursor bereit. Die ODBC-Cursor Bibliothek ist veraltet. in Ihrer Anwendung können serverseitige Cursor Implementierungen als Ersatz verwendet werden.
* **OLE DB out-of-Process Interface Remoting:** OLEDB Interface Remoting (msdaps. dll) war ein Versuch, OLE DB Anbietern die Ausführung außerhalb des Prozesses zu ermöglichen. OLEDB-Remoting für Out-of-Process-Schnittstelle ist veraltet.
* **SQL-Netzwerk Bibliotheken von AppleTalk und Banyan Vines:** Die SQL-Netzwerk Bibliotheken Banyan Vines, AppleTalk, ServerNet, IPX/SPX, Giganet und RPC sind veraltet. Wenn Sie eine dieser Technologien verwenden, sollten Sie Ihre Anwendungen so ändern, dass Sie eine der anderen Netzwerk Bibliotheken verwenden, z. b. TCP/IP und Named Pipe.

### <a name="mdacwdac-releases"></a>MDAC/WDac-Releases

Im folgenden finden Sie eine Liste der Szenarien für die unter Stütz barkeit früherer MDAC/WDac-Releases, beginnend mit der frühesten Version.

* **MDAC 1,5, MDAC 2,0 und MDAC 2,1:** Diese Versionen von MDAC waren unabhängige Releases, die über das Microsoft Windows NT-Optionspaket, das Microsoft Windows-Plattform-SDK oder die MDAC-Website veröffentlicht wurden. Diese Versionen von MDAC werden nicht mehr unterstützt.
* **MDAC 2,5:** Diese MDAC-Version ist im Betriebssystem Windows 2000 enthalten. Service Packs von MDAC 2,5 waren in den entsprechenden Windows 2000 Service Packs enthalten.
* **MDAC 2.6:** MDAC 2.6 RTM, SP1 und SP2 wurden in Microsoft SQL Server 2000-RTM, SP1 und SP2 enthalten bzw. Außerdem wurden diese MDAC-Service Packs gemäß dem Microsoft SQL Server 2000 Service Pack-releasezeitplan auf der MDAC-Website veröffentlicht. Sie können diese Version von MDAC und der zugehörigen Service Packs auf den Plattformen Windows 2000, Windows Millennium Edition, Windows NT, Windows 95 und Windows 98 installieren. Diese MDAC-Version wird nicht mehr unterstützt.
* **MDAC 2,7:** Diese MDAC-Version ist in den Betriebssystemen Microsoft Windows XP RTM und SP1 enthalten. Sie können diese Version von MDAC und der zugehörigen Service Packs auf den Plattformen Windows 2000, Windows Millennium, Windows NT und Windows 98 installieren. Sie können diese Version nur über das Betriebssystem oder die zugehörigen Service Packs auf der Windows XP-Plattform installieren. Diese MDAC-Version wird nicht mehr unterstützt.
* **MDAC 2,8:** Diese MDAC-Version ist in Windows Server 2003 und Windows XP SP2 und höher enthalten. Sie können diese Version von MDAC und die zugehörigen Service Packs auch unter Windows 2000 installieren.

  * Die 32-Bit-Version von MDAC 2,8 wurde auch auf der MDAC-Website zur gleichen Zeit freigegeben, als Windows Server 2003 für den Kunden freigegeben wurde.
  * Die 64-Bit-Version von MDAC 2,8 wurde mit der 64-Bit-Version von Windows Server 2003 und Windows XP veröffentlicht.

* **Windows Data Access Components (WDac):** Der Name der MDAC wurde in WDac geändert: "Windows Data Access Components", beginnend mit Windows Vista und Windows Server 2008. WDac ist als Teil des Betriebssystems enthalten und ist für die erneute Verteilung nicht separat verfügbar. Die Serviceability für WDac unterliegt dem Lebenszyklus des Betriebssystems.

  32-Bit-und 64-Bit-Versionen von WDac werden mit den 32-Bit-und 64-Bit-Versionen der Windows-Betriebssysteme veröffentlicht.

## <a name="obsolete-data-access-technologies"></a>Veraltete Datenzugriffs Technologien

Bei veralteten Technologien handelt es sich um Technologien, die in mehreren Produkt Releases nicht erweitert oder aktualisiert wurden und die von zukünftigen Produkt Releases ausgeschlossen werden. Verwenden Sie diese Technologien nicht, wenn Sie neue Anwendungen schreiben. Wenn Sie vorhandene Anwendungen ändern, die mithilfe dieser Technologien geschrieben wurden, sollten Sie die Migration dieser Anwendungen zu ADO.net oder einer anderen aktuellen Technologie in Erwägung gezogen.

Die folgenden Komponenten gelten als veraltet:

* **DB-Library:** DB-Library ist ein SQL Server spezifisches Programmiermodell, das C-APIs umfasst. Es wurden seit SQL Server 6,5 keine Features Erweiterungen für die DB-Library vorgenommen. Die endgültige Version war mit SQL Server 2000 und wird nicht auf das Windows-Betriebssystem 64-Bit portiert.
* **Eingebettetes SQL (E-SQL):** E-SQL ist ein SQL Server spezifisches Programmiermodell, das es ermöglicht, Transact-SQL-Anweisungen in Visual C-Code zu integrieren. An E-SQL wurden seit SQL Server 6,5 keine Features Verbesserungen vorgenommen. Die endgültige Version war mit SQL Server 2000 und wird nicht auf das Windows-Betriebssystem 64-Bit portiert.
* **Data Access Objects (DAO):** DAO ermöglicht den Zugriff auf Jet-Datenbanken (Access). Diese API kann von Microsoft Visual Basic, Microsoft Visual C++und Skriptsprachen verwendet werden. Es war in Microsoft Office 2000 und Office XP enthalten. DAO 3,6 ist die endgültige Version dieser Technologie. Es ist nicht auf dem 64-Bit-Windows-Betriebssystem verfügbar.
* **Remote Datenobjekte (RDO):** RDO wurde speziell für den Zugriff auf relationale ODBC-Datenquellen konzipiert und erleichtert die Verwendung von ODBC ohne komplexen Anwendungscode. Es ist in den Microsoft Visual Basic-Versionen 4, 5 und 6 enthalten. RDO Version 2,0 war die endgültige Version dieser Technologie.

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]
