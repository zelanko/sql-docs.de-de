---
title: Treiberverlauf für Microsoft SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 5/4/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daveng
manager: craigg
ms.openlocfilehash: 8862c6333673ddf69314f4a64c11c8b044484b69
ms.sourcegitcommit: 9ea11d738503223b46d2be5db6fed6af6265aecc
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 01/07/2019
ms.locfileid: "54069796"
---
# <a name="driver-history-for-microsoft-sql-server"></a>Treiberverlauf für Microsoft SQL Server

Auf dieser Seite werden die Technologien von Microsoft Daten zur Versionsgeschichte Verbindung für die Verbindung mit SQL Server.

## <a name="odbc"></a>ODBC

Es gibt drei verschiedene Generationen des Microsoft ODBC-Treiber für SQL Server. Der erste "SQL Server"-ODBC-Treiber wird weiterhin als Bestandteil von [Windows Data Access Components](#microsoft-or-windows-data-access-components). Es wird nicht empfohlen, diese Treiber für die neue Entwicklung zu verwenden. Ab SQL Server 2005, die [SQL Server Native Client](#sql-server-native-client) enthält eine ODBC-Schnittstelle und der ODBC-Treiber, die mit den im Lieferumfang von SQL Server 2005 über SQL Server 2012. Es wird nicht empfohlen, diese Treiber für die neue Entwicklung zu verwenden. Nach SQL Server 2012 die [Microsoft ODBC-Treiber für SQL Server](#microsoft-odbc-driver-for-sql-server) ist der Treiber, die mit den neuesten Serverfunktionen, die in Zukunft aktualisiert wird.

### <a name="sql-server-native-client"></a>SQL Server Native Client

SQL Server Native Client ist eine eigenständige Bibliothek, die für OLE DB und ODBC verwendet wird. SQL Server Native Client (häufig abgekürzt als SNAC) wurde in SQL Server 2005 bis 2012 enthalten. SQL Server Native Client kann für Anwendungen verwendet werden, die in SQL Server 2005 über SQL Server 2012 eingeführten neuen Funktionen nutzen müssen. (Microsoft/Windows Data Access Components sind für diese neuen Funktionen in SQL Server nicht aktualisiert.) Informationen zu neuen Funktionen über SQL Server 2012 wird SQL Server Native Client nicht aktualisiert werden. Wechseln Sie zum Microsoft ODBC Driver für SQL Server oder der Microsoft OLE DB-Treiber für SQL Server, wenn Sie neue SQL Server-Funktionen, die in Zukunft nutzen möchten.

Vollständige Dokumentation von SQL Server Native Client finden Sie in der [SQL Server Native Client Dokumentation](../relational-databases/native-client/sql-server-native-client-programming.md).

### <a name="microsoft-odbc-driver-for-sql-server"></a>Microsoft ODBC Driver for SQL Server

Nach SQL Server 2012 wurde die primäre ODBC-Treiber für SQL Server entwickelt und als Microsoft ODBC Driver für SQL Server veröffentlicht. Weitere Informationen finden Sie unter den [Microsoft ODBC-Treiber für SQL Server-Dokumentation](./odbc/microsoft-odbc-driver-for-sql-server.md).

## <a name="ole-db"></a>OLE DB

Es gibt drei verschiedene Generationen von Microsoft OLE DB-Anbieter für SQL Server. Der erste "Microsoft OLE DB-Anbieter für SQL Server" (SQLOLEDB) wird weiterhin als Bestandteil von [Windows Data Access Components](#microsoft-or-windows-data-access-components). Dieser Anbieter wird nicht mit den neuen Features aktualisiert werden, und es wird nicht empfohlen, diese Treiber für die neue Entwicklung zu verwenden. Ab SQL Server 2005, die [SQL Server Native Client](#sql-server-native-client) enthält eine OLE DB-Provider-Schnittstelle (SQLNCLI), und der OLE DB-Anbieter, die mit SQL Server 2005 über SQL Server 2017 geliefert wird. Es war [als im Jahr 2011 veraltet bekanntgegeben](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/) und es wird nicht empfohlen, diese Treiber für die neue Entwicklung zu verwenden. In 2017 OLE DB-datenzugriffstechnologie wurde anschließend [aufgehoben und ein neues geplantes Release wurde angekündigt](https://blogs.msdn.microsoft.com/sqlnativeclient/2017/10/06/announcing-the-new-release-of-ole-db-driver-for-sql-server/) für 2018. Neue OLE DB-Anbieters ist wird aufgerufen, die "Microsoft OLE DB-Treiber für SQL Server" (MSOLEDBSQL) und derzeit verwaltet und unterstützt.

## <a name="adonet"></a>ADO.NET

ADO.NET wurde eingeführt, mit dem Microsoft .NET Framework und weiterhin verbessert und verwaltet werden. Es ist eine Kernkomponente des Microsoft .NET Framework. Weitere Informationen finden Sie unter [Microsoft ADO.NET for SQL Server](ado-net/microsoft-ado-net-for-sql-server.md).

## <a name="jdbc"></a>JDBC

### <a name="microsoft-jdbc-driver-for-sql-server"></a>Microsoft JDBC-Treiber für SQL Server

In 2000 eingeführt wurde, wird weiterhin der Microsoft JDBC-Treiber für SQL Server verbessert und verwaltet werden. Es war, Open Source-2016. Die neuesten Informationen, einschließlich Informationen zum Herunterladen des Treibers, finden Sie unter [Überblick über den JDBC-Treiber](./jdbc/overview-of-the-jdbc-driver.md).

## <a name="php"></a>PHP

### <a name="microsoft-drivers-for-php-for-sql-server"></a>Microsoft-Treiber für PHP für SQL Server

Als Open-Source-Projekt in 2009 eingeführt wurde, weiterhin Microsoft Drivers for PHP for SQL Server verbessert und verwaltet werden. Die neuesten Informationen, einschließlich Informationen zum Herunterladen des PHP-Treibers finden Sie unter [Microsoft Drivers for PHP for SQL Server](./php/microsoft-php-driver-for-sql-server.md).

## <a name="nodejs"></a>Node.js

### <a name="microsoft-driver-for-nodejs-for-sql-server"></a>Microsoft Driver für Node.js für SQLServer

Das Microsoft Driver für Node.js für SQL Server können die Node.js-Anwendungen unter Microsoft Windows und Microsoft Windows Azure für Microsoft SQL Server und Microsoft Windows Azure SQL-Datenbank zugreifen. Entwicklungsprojekte sind nicht mehr auf diesen Treiber konzentriert werden. Es wird nicht empfohlen, um neue Anwendungen, die mithilfe von Microsoft Driver für Node.js für SQL Server zu erstellen.

Weitere Informationen zu Microsoft Driver für Node.js für SQL Server finden Sie unter [WindowsAzure / Knoten-Sqlserver](https://github.com/Azure/node-sqlserver).

### <a name="tedious"></a>Mühsam

Microsoft trägt zur aktuell und unterstützt die Open Source-Modul mühsame in Node.js für die Verbindung mit SQL Server mithilfe von JavaScript. Weitere Informationen finden Sie unter [Node.js-Treiber für SQL Server](./node-js/node-js-driver-for-sql-server.md).

## <a name="microsoft-or-windows-data-access-components"></a>Microsoft "oder" Windows Data Access Components

Microsoft/Windows Data Access Components (MDAC/WDAC) sind im Lieferumfang von Windows für die Anwendung Abwärtskompatibilität unterstützt und sind nicht Teil des aktuellen SQL Server-Technologie. Komponenten in MDAC/WDAC werden keine neuen Features hinzugefügt, und es wird nicht empfohlen, diese für die Entwicklung neuer Anwendungen verwenden.

Für die Zwecke dieses Dokuments werden soll können Sie den MDAC/WDAC-Stapel in die folgenden Komponenten, die basierend auf den Technologien und Produkte unterteilen:

* **ADO** (einschließlich ADOMD und ADOX)
* **OLE DB** (einschließlich OLE DB-Basisdienste, OLE DB Provider für SQL Server, Oracle OLE DB-Anbieter, OLE DB-Anbieter für ODBC-Treiber, Daten-Shape-Anbieter und Remote-Datenanbieter)
* **ODBC** (einschließlich ODBC-Treiber-Managers, ODBC-Treiber für SQL und Oracle ODBC-Treiber)

### <a name="mdacwdac-components"></a>MDAC/WDAC-Komponenten

MDAC/WDAC umfasst folgende Komponenten:

* **ODBC:** Die Microsoft Open Database Connectivity (ODBC)-Schnittstelle ist eine C-Programmiersprache-Schnittstelle, die Anwendungen auf Daten aus einer Vielzahl von Datenbank Datenbankverwaltungssystemen (DBMS) zugreifen kann. Anwendungen, die diese API verwenden, sind für den Zugriff auf relationale Datenquellen nur begrenzt.
* **OLE DB** OLE DB ist ein Satz von COM-Schnittstellen für den Zugriff auf Daten in einer Vielzahl von Datenspeichern. OLE DB-Anbieter vorhanden sein, für den Zugriff auf Daten in Datenbanken, Dateisysteme, Nachrichtenspeichern, Verzeichnisdienste, Workflow und Dokument speichert.
* **ADO** ActiveX Data Objects (ADO) bietet ein Programmiermodell, das auf hoher Ebene. Obwohl etwas weniger leistungsfähig als das Erstellen, OLEDB- oder ODBC direkt ADO einfach ist zu erlernen und zu verwenden. Es kann von Skriptsprachen, z. B. Microsoft Visual Basic Scripting Edition (VBScript) oder Microsoft JScript verwendet werden.
* **ADOMD:** ADO multidimensionales (ADOMD) ist mit mehrdimensionale Datenanbieter wie Microsoft OLAP-Anbieter, auch bekannt als Microsoft Analysis Services-Anbieter verwendet werden. Keine wichtigen haben, seit MDAC 2.0 wurden featureverbesserungen vorgenommen.
* **ADOX:** ADO-Erweiterungen für DDL-Befehle und Sicherheit (ADOX) ermöglichen die Erstellung und Änderung von Definitionen für eine Datenbank, Tabelle, Index oder gespeicherten Prozedur. Sie können mit jedem Anbieter ADOX verwenden. Microsoft Jet OLE DB-Anbieter bietet vollständige Unterstützung für ADOX, und der Microsoft SQL Server OLE DB-Anbieter nur eingeschränkt unterstützt.
* **Microsoft SQL Server-Netzwerkbibliotheken:** Die SQL Server-Netzwerkbibliotheken können SQLOLEDB und SQLODBC, für die Kommunikation mit SQL Server-Datenbank. Die folgenden SQL Server-Netzwerkbibliotheken sind veraltet in MDAC/WDAC-Versionen: Banyan Vines, AppleTalk, ServerNet, IPX/SPX, Giganet und RPC. TCP/IP und Named Pipes werden weiterhin unterstützt werden, und auf dem 64-Bit-Windows-Betriebssystem verfügbar sind.
* **MSDASQL:** Microsoft OLE DB-Anbieter für ODBC (MSDASQL) ermöglicht Anwendungen, die auf OLE DB und ADO (das OLE DB intern verwendet wird) den Zugriff auf Datenquellen über einen ODBC-Treiber integriert sind. MSDASQL ist ein OLE DB-Anbieter, der Verbindung mit ODBC, anstelle einer Datenbank. Es dient als Brücke von OLE DB eine ODBC-Treiber bei der keine direkten OLE DB-Anbieter für eine Datenquelle vorhanden ist. MSDASQL, die mit dem Betriebssystem Windows ausgeliefert wird, und Windows Server 2008 und Vista SP1 wurden, dass die ersten Windows releases, in denen eine 64-Bit-Version der Technologie enthalten.

### <a name="deprecated-mdacwdac-components"></a>Veraltete MDAC/WDAC-Komponenten

Diese Komponenten sind in der aktuellen Version von MDAC/WDAC weiterhin unterstützt, jedoch möglicherweise in zukünftigen Versionen entfernt werden. Wenn Sie neue Anwendungen entwickeln zu können, empfiehlt Microsoft, mithilfe dieser Komponenten vermeiden. Darüber hinaus beim Aktualisieren oder ändern Sie vorhandene Anwendungen, entfernen Sie alle Abhängigkeiten von diesen Komponenten.

* **SQLOLEDB:** Microsoft OLE DB-Anbieter für SQL Server (SQLOLEDB), die Zugriff auf Microsoft SQL Server unterstützt, ist veraltet. Die Konnektivität mit zukünftigen Versionen von SQL Server möglicherweise nicht unterstützt. Die Fähigkeit zum Verbinden mit Versionen vor SQL Server 7 nach Windows 7 aus dem Betriebssystem entfernt wird. Neue Anwendungen sollten der Microsoft OLE DB-Treiber für SQL Server (MSOLEDBSQL) verwenden, die neue SQL Server-Funktionen unterstützt. Vorhandene Anwendungen sollten auf der Microsoft OLE DB-Treiber für SQL Server als auch für eine bessere Leistung, Zuverlässigkeit und unterstützbarkeit migrieren. Weitere Informationen finden Sie unter [Aktualisieren einer Anwendung auf OLE DB-Treiber für SQL Server über MDAC](oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).
* **SQLODBC:** Die Microsoft SQL Server-ODBC-Treiber (SQLODBC), die Zugriff auf Microsoft SQL Server unterstützt, wurde als veraltet markiert. Die Konnektivität mit zukünftigen Versionen von SQL Server möglicherweise nicht unterstützt. Die Fähigkeit zum Verbinden mit Versionen vor SQL Server 7 nach Windows 7 aus dem Betriebssystem entfernt wird. Neue Anwendungen sollten den Microsoft ODBC Driver for SQL Server unter Windows, verwenden die neuen Features von SQL Server unterstützt. Vorhandene Anwendungen sollten auf der Microsoft ODBC Driver für SQL Server als auch für eine bessere Leistung, Zuverlässigkeit und unterstützbarkeit migrieren. Relevante Informationen finden Sie unter [Aktualisieren einer Anwendung von MDAC auf SQL Server Native Client](../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md).
* **Microsoft Jet-Datenbank-Engine 4.0:** Ab Version 2.6 enthält MDAC mehr Jet-Komponenten. Das heißt, MDAC 2.6, 2.7, 2.8 enthalten keine Microsoft Jet, Microsoft Jet OLE DB-Anbieter, die ODBC-Desktop-Datenbanktreiber oder Jet Datenzugriffsobjekte (DAO). 

  Es ist keine 64-Bit-Version des Jet-Datenbank-Engine, der Jet-OLEDB-Treiber, die Jet ODBC-Treiber oder Jet-DAO-verfügbar. Weitere Informationen finden Sie im Knowledge Base-Artikel [957570](https://support.microsoft.com/kb/957570). Bei 64-Bit-Versionen von Windows werden 32-Bit Jet unter Windows-WOW64-Subsystem ausgeführt. Weitere Informationen unter WOW64 finden Sie unter den [WOW64 für MSDN-Dokumentation](/windows/desktop/WinProg64/wow64-implementation-details). Systemeigene 64-Bit-Anwendungen können nicht mit der 32-Bit Jet-Treiber unter WOW64 kommunizieren.

  Anstelle von Microsoft Jet, Microsoft empfiehlt die Verwendung [Microsoft SQL Server Express Edition](https://www.microsoft.com/sql-server/sql-server-editions-express) beim Entwickeln von neuen, nicht Microsoft Access - Anwendungen, die einen relationalen Datenspeicher erfordern. Dieser neuen oder konvertierte Jet-Anwendungen können weiterhin Jet, die mit dem Ziel mithilfe von Microsoft Office 2003 und früheren Dateien ("mdb" und ".xls") nicht primären Datenspeicher verwenden. Allerdings sollten für diese Anwendungen sollen von Jet zu 2007 Office System-Treiber zu migrieren. Sie können [Herunterladen der 2007 Office System Driver](https://www.microsoft.com/downloads/details.aspx?displaylang=en&FamilyID=7554f536-8c28-4598-9b72-ef94e038c891), können Sie Lese- und Schreibzugriff auf bereits vorhandene Dateien in Office 2003 ("mdb" und ".xls") oder die Office 2007 (*.accdb, *.xlsm, *.xlsx und *.xlsb)-Dateiformate.

  > [!IMPORTANT]
  > Lesen Sie die 2007 Office System-Software-Lizenzbedingungen für bestimmte nutzungseinschränkungen.

  > [!NOTE]
  > SQL Server-Anwendungen können auch das 2007 Office System zugreifen und früheren Versionen Dateien heterogener Daten SQL Server-Konnektivität und Integration Services Funktionen auch über die 2007 Office System-Treiber. Darüber hinaus können 64-Bit SQL Server-Anwendungen mithilfe von 32-Bit SQL Server Integration Services (SSIS) auf 64-Bit-Windows 32-Bit Jet und 2007 Office System-Dateien zugreifen.

* **MSDADS:** Microsoft OLE DB-Anbieter für die Data Shaping (MSDADS) können Sie die hierarchische Beziehungen zwischen den Schlüssel, Felder oder Rowsets in einer Anwendung erstellen. Ohne wesentliche funktionale Erweiterungen wurden seit MDAC 2.1 vorgenommen. Dieser Anbieter ist veraltet. Microsoft empfiehlt die Verwendung von XML anstelle von MSDADS.
* **Oracle ODBC und Oracle OLE DB:** Bieten Zugriff auf Oracle-Datenbankserver, der Microsoft Oracle ODBC-Treiber (Oracle ODBC) und Microsoft OLE DB-Anbieter für Oracle (Oracle OLE DB). Sie werden mithilfe von Oracle aufrufen Schnittstelle (OCI) Version 7 erstellt und bieten vollständige Unterstützung für Oracle 7. Darüber hinaus verwendet Oracle 7-Emulation, um die eingeschränkten Unterstützung für Oracle 8-Datenbanken verfügbar. Oracle unterstützt nicht mehr Anwendungen, die Aufrufe der OCI-Version 7 verwenden. Diese Technologien sind veraltet. Wenn Sie Oracle-Datenquellen verwenden, sollten Sie Oracle bereitgestellte Treiber und Anbieter migrieren.
* **RDS:** Remote Data Services (RDS) ist eine proprietäre Microsoft-Mechanismus für den Zugriff auf remote-ADO-Recordset-Objekte über das Internet oder Intranet. RDS ist veraltet. ohne wesentliche funktionale Erweiterungen RDS seit MDAC 2.1 wurden. Microsoft stellt .NET Framework bietet umfangreiche Funktionen für SOAP und RDS-Komponenten ersetzt. Alle RDS-Server-Komponenten werden vom Betriebssystem nach Windows 7 entfernt.
* **JRO:** Jet-Replication-Objekte (JRO) ist veraltet. JRO wird innerhalb von ADO mit Jet verwendet (*.mdb) Datenbanken erstellen und Komprimieren der Jet-Datenbanken (.mdb) und Jet-Replikationsverwaltung auszuführen. MDAC 2.7 wird auf der letzten Version sein. JRO wird nicht auf dem 64-Bit-Windows-Betriebssystem verfügbar sein. JRO wird nicht unterstützt, in der Microsoft Access 2007-Dateiformat (*.accdb).
* **16-Bit-ODBC-Unterstützung:** Wenn Sie 16-Bit-Anwendungen verwenden, sollten Sie eine 32-Bit-Anwendung migrieren. 16-Bit-Funktionalität ist veraltet und wird von 64-Bit-Betriebssystemen entfernt. Weitere Informationen finden Sie im [Knowledge Base-Artikel 896458](https://support.microsoft.com/kb/896458).
* **Einfache OLE DB-Anbieter (MSDAOSP):** Einfache OLE DB-Anbieter bietet ein Framework zum schnellen Erstellen von OLE DB-Anbieter für einfache Daten. MSDAOSP ist veraltet.
* **ODBC-Cursorbibliothek** ODBC Cursor Library (ODBCCR32.dll) bietet begrenzte clientseitigen Datencursor. ODBC-Cursorbibliothek wurde als veraltet markiert; die Anwendung kann serverseitiger cursorimplementierungen als Ersatz verwenden.
* **OLE DB-Schnittstelle der Out-of-Process-Remoting:** OLE DB-Schnittstelle Remoting (msdaps.dll) wurde versucht, OLE DB-Anbieter außerhalb des Prozesses ausführen zu können. OLE DB-Schnittstelle der Out-of-Process-Remoting ist veraltet.
* **AppleTalk und Banyan Vines SQL-Netzwerkbibliotheken:** Die Netzwerkbibliotheken für Banyan Vines, AppleTalk, ServerNet, IPX/SPX, Giganet und RPC-SQL sind veraltet. Wenn Sie einer dieser Technologien verwenden, sollten Sie Ihre Anwendungen verwenden, z. B. TCP/IP und Named Pipe-Netzwerkbibliotheken, ändern.

### <a name="mdacwdac-releases"></a>MDAC/WDAC-Versionen

Hier ist eine Liste der Szenarien unterstützbarkeit von früheren Versionen von MDAC/WDAC, beginnend mit der frühesten.

* **MDAC 1.5, MDAC 2.0 und MDAC 2.1:** Diese Versionen von MDAC waren unabhängigen Versionen, die über das Microsoft Windows NT Option Pack, das Microsoft Windows-Plattform-SDK oder der MDAC-Website veröffentlicht wurden. Diese Versionen von MDAC werden nicht mehr unterstützt.
* **MDAC 2.5:** Diese Version von MDAC wurde mit dem Betriebssystem Windows 2000. Servicepacks von MDAC 2.5 wurden in entsprechende Windows 2000 Servicepacks enthalten.
* **MDAC 2.6:** MDAC 2.6 RTM, SP1 und SP2 waren in Microsoft SQL Server 2000 RTM, SP1 bzw. SP2 enthalten. Darüber hinaus wurden diese MDAC Servicepacks der MDAC-Website gemäß der Freigabezeitplan für den Microsoft SQL Server 2000 Service Pack-veröffentlicht. Sie können diese Version von MDAC und Servicepacks auf Windows 2000, Windows Millennium Edition, Windows NT, Windows 95 und Windows 98-Plattformen installieren. Diese Version von MDAC wird nicht mehr unterstützt.
* **MDAC 2.7:** Diese Version von MDAC ist in den Betriebssystemen Microsoft Windows XP RTM und SP1 enthalten. Sie können diese Version von MDAC und Servicepacks für Windows 2000, Windows Millennium, Windows NT und Windows 98-Plattformen installieren. Sie können diese Version auf der Windows XP-Plattform nur über das Betriebssystem oder die Service Packs installieren. Diese Version von MDAC wird nicht mehr unterstützt.
* **MDAC 2.8:** Diese Version von MDAC war inbegriffen; mit Windows Server 2003 und Windows XP SP2 und höher. Sie können diese Version von MDAC und Servicepacks auch unter Windows 2000 installieren.

  * Die 32-Bit-Version von MDAC 2.8 wurde auch der MDAC-Website zur gleichen Zeit veröffentlicht, die an den Kunden die Windows Server 2003 veröffentlicht wurde.
  * Die 64-Bit-Version von MDAC 2.8 wurde mit der 64-Bit-Version von Windows Server 2003 und Windows XP veröffentlicht.

* **Windows Data Access Components** MDAC wurde der Name in WDAC - "Windows Data Access Components" beginnend mit Windows Vista und Windows Server 2008 geändert. WDAC steht als Bestandteil des Betriebssystems und ist nicht für die weiterverteilung separat verfügbar. Wartbarkeit für WDAC unterliegt den Lebenszyklus des Betriebssystems ab.

  WDAC 32-Bit und 64-Bit-Versionen werden mit den 32-Bit und 64-Bit-Versionen der Windows-Betriebssysteme, veröffentlicht.

## <a name="obsolete-data-access-technologies"></a>Veraltete datenzugriffstechnologien

Veraltete-Technologien sind Technologien, die nicht erweitert oder aktualisiert wurden in mehrere Produktversionen und, die aus zukünftigen Produktversionen ausgeschlossen. Verwenden Sie diese Technologien nicht aus, wenn Sie neue Anwendungen schreiben. Wenn Sie vorhandene Anwendungen, die ändern mithilfe dieser Technologien geschrieben wurden, sollten Sie migrieren dieser Anwendungen zu ADO.NET oder einer anderen aktuellen Technologie.

Die folgenden Komponenten sind als veraltet eingestuft:

* **DB-Library:** DB-Library ist ein SQL Server-spezifische-Programmiermodell, der C-APIs enthält. Es wurden keine featureoptimierungen bereit, die DB-Library seit SQL Server 6.5. Der endgültigen Veröffentlichung wurde mit SQL Server 2000 und wird für das 64-Bit-Windows-Betriebssystem nicht portiert werden.
* **Embedded SQL (E-SQL):** E-SQL ist ein SQL Server-spezifische-Programmiermodell, mit der Transact-SQL-Anweisungen, die in Visual C#-Code eingebettet werden kann. Ohne funktionale Erweiterungen sind in der E-SQL seit SQL Server 6.5 erfolgt. Der endgültigen Veröffentlichung wurde mit SQL Server 2000 und wird für das 64-Bit-Windows-Betriebssystem nicht portiert werden.
* **Datenzugriffsobjekte (DAO):** DAO ermöglicht den Zugriff auf (Access)-JET-Datenbanken. Diese API kann von Microsoft Visual Basic, Microsoft Visual C++ und Skriptsprachen verwendet werden. Es wurde mit Microsoft Office 2000 und Office XP. DAO 3.6 ist die endgültige Version von dieser Technologie. Es wird nicht auf dem 64-Bit-Windows-Betriebssystem verfügbar sein.
* **Remote-Daten-Objekte (RDO):** RDO wurde speziell dazu entwickelt, den Zugriff auf remote-ODBC-relationale Datenquellen und ODBC verwenden, ohne komplexe Anwendungscode vereinfacht. Es wurde mit Microsoft Visual Basic-Versionen 4, 5 und 6. RDO-Version 2.0 war die endgültige Version von dieser Technologie.

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]