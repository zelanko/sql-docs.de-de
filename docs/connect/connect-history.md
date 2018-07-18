---
title: Treiberverlauf für Microsoft SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 5/4/2018
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: David-Engel
ms.author: v-daveng
manager: kenvh
ms.openlocfilehash: 2f2f4bafe48018da5c6f634b272a540021fd4ca2
ms.sourcegitcommit: 6fd8a193728abc0a00075f3e4766a7e2e2859139
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34236034"
---
# <a name="driver-history-for-microsoft-sql-server"></a>Treiberverlauf für Microsoft SQL Server

Diese Seite beschreibt Microsofts Verlaufsdaten Verbindung Technologien für die Verbindung mit SQL Server.

## <a name="odbc"></a>ODBC

Es gibt drei verschiedene Generationen der Microsoft ODBC-Treiber für SQL Server. Der erste "SQL Server" ODBC-Treiber weiterhin geliefert wird, im Rahmen des [Windows Data Access Components](#microsoft-or-windows-data-access-components). Es wird nicht empfohlen, diese Treiber für neue Entwicklungen verwenden. Ab SQL Server 2005, die [SQL Server Native Client](#sql-server-native-client) umfasst eine ODBC-Schnittstelle und der ODBC-Treiber, die mit den im Lieferumfang von SQL Server 2005 über SQL Server 2012. Es wird nicht empfohlen, diese Treiber für neue Entwicklungen verwenden. Nach SQL Server 2012 die [Microsoft ODBC Driver for SQL Server](#microsoft-odbc-driver-for-sql-server) ist der Treiber, die mit den neuesten Server-Funktionen, die zukünftig aktualisiert wird.

### <a name="sql-server-native-client"></a>SQL Server Native Client

SQL Server Native Client ist eine eigenständige Bibliothek, die für OLE DB und ODBC verwendet wird. SQL Server Native Client (SNAC häufig abgekürzt als) wurde in SQL Server 2005 bis 2012 enthalten. SQL Server Native Client kann für Anwendungen verwendet werden, die in SQL Server 2005 über SQL Server 2012 eingeführten neuen Funktionen nutzen müssen. (Microsoft/Windows Data Access Components sind für diese neuen Features in SQL Server nicht aktualisiert.) Informationen zu neuen Funktionen über SQL Server 2012 wird SQL Server Native Client nicht aktualisiert werden. Wechseln Sie zum Microsoft ODBC Driver für SQL Server oder der Microsoft OLE DB-Treiber für SQL Server, wenn Sie neue SQL Server-Funktionen, die zukünftig nutzen möchten.

Vollständige Dokumentation von SQL Server Native Client finden Sie unter der [SQL Server Native Client Dokumentation](../relational-databases/native-client/sql-server-native-client-programming.md).

### <a name="microsoft-odbc-driver-for-sql-server"></a>Microsoft ODBC Driver for SQL Server

Nach SQL Server 2012 wurde der primäre ODBC-Treiber für SQL Server entwickelt und als Microsoft ODBC Driver für SQL Server veröffentlicht. Weitere Informationen finden Sie unter der [Microsoft ODBC Driver for SQL Server-Dokumentation](./odbc/microsoft-odbc-driver-for-sql-server.md).

## <a name="ole-db"></a>OLE DB

Es gibt drei verschiedene Generationen von Microsoft OLE DB-Anbieter für SQL Server. Die erste "Microsoft OLE DB-Anbieter für SQL Server" (SQLOLEDB) noch geliefert wird, im Rahmen des [Windows Data Access Components](#microsoft-or-windows-data-access-components). Dieser Anbieter wird nicht mit neuen Funktionen aktualisiert werden, und es wird nicht empfohlen, diesen Treiber für neue Entwicklungen verwenden. Ab SQL Server 2005, die [SQL Server Native Client](#sql-server-native-client) enthält eine OLE DB-Provider-Schnittstelle (SQLNCLI), und die OLE DB-Anbieter, die mit SQL Server 2005 über SQL Server-2017 ausgeliefert wird. Es wurde [angekündigt, sobald in 2011 veraltet](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/) und es wird nicht empfohlen, diesen Treiber für neue Entwicklungen verwenden. 2017 OLE DB-datenzugriffstechnologie wurde anschließend [undeprecated und eine neue geplanten Version angekündigt wurde](https://blogs.msdn.microsoft.com/sqlnativeclient/2017/10/06/announcing-the-new-release-of-ole-db-driver-for-sql-server/) für 2018. Die neue OLE DB-Anbieter ist wird aufgerufen, die "Microsoft OLE DB-Treiber für SQL Server" (MSOLEDBSQL) und derzeit verwaltet und unterstützt.

## <a name="adonet"></a>ADO.NET

ADO.NET mit Microsoft .NET Framework eingeführt wurde und weiterhin verbessert und verwaltet werden. Es ist eine Kernkomponente der Microsoft .NET Framework. Weitere Informationen finden Sie unter [Microsoft ADO.NET for SQL Server](ado-net/microsoft-ado-net-for-sql-server.md).

## <a name="jdbc"></a>JDBC

### <a name="microsoft-jdbc-driver-for-sql-server"></a>Microsoft JDBC-Treiber für SQL Server

In 2000 eingeführt wurde, wird weiterhin Microsoft JDBC Driver für SQL Server verbessert und verwaltet werden. Open Source in 2016 war. Die neuesten Informationen, einschließlich Informationen zum Herunterladen des Treibers finden Sie unter [Überblick über die JDBC-Treiber](./jdbc/overview-of-the-jdbc-driver.md).

## <a name="php"></a>PHP

### <a name="microsoft-drivers-for-php-for-sql-server"></a>Microsoft-Treiber für PHP für SQL Server

Als Open-Source-Projekt in 2009 eingeführt wurde, weiterhin Microsoft Drivers for PHP for SQL Server verbessert und verwaltet werden. Die neuesten Informationen, einschließlich Informationen zum Herunterladen des PHP-Treibers finden Sie unter [Microsoft Drivers for PHP for SQL Server](./php/microsoft-php-driver-for-sql-server.md).

## <a name="nodejs"></a>Node.js

### <a name="microsoft-driver-for-nodejs-for-sql-server"></a>Microsoft-Treiber für Node.js für SQLServer

Microsoft Driver für Node.js für SQL Server ermöglicht Node.js-Anwendungen unter Microsoft Windows und Microsoft Windows Azure für den Zugriff auf Microsoft SQL Server und Microsoft Windows Azure SQL-Datenbank. Entwicklungsaufwand sind nicht mehr auf dieser Treiber zugeschnitten wird. Es wird nicht empfohlen, um neue Anwendungen mithilfe von Microsoft Driver für Node.js für SQL Server zu erstellen.

Weitere Informationen zu Microsoft Driver für Node.js für SQL Server, finden Sie unter [WindowsAzure / Knoten Sqlserver](https://github.com/Azure/node-sqlserver).

### <a name="tedious"></a>Mühsam

Microsoft ist derzeit trägt dazu bei, und unterstützt das mühsame Open-Source-Modul in Node.js für die Verbindung mit SQL Server, die mit JavaScript. Weitere Informationen finden Sie unter [Node.js-Treiber für SQL Server](./node-js/node-js-driver-for-sql-server.md).

## <a name="microsoft-or-windows-data-access-components"></a>Microsoft "oder" Windows Data Access Components

Microsoft/Windows Data Access Components (MDAC/WDAC) sind im Lieferumfang von Windows für die Anwendung der Abwärtskompatibilität unterstützt und sind nicht Teil der aktuellen SQL Server-Technologie. Komponenten in MDAC/WDAC werden keine neuen Funktionen hinzugefügt, und es wird nicht empfohlen, diese für die Entwicklung neuer verwenden.

Im Rahmen dieses Dokuments können Sie die MDAC/WDAC-Stapel in der folgenden Komponenten, basierend auf Technologie und Produkte unterteilen:

* **ADO** (einschließlich ADOMD und ADOX)
* **OLE DB-** (einschließlich OLE DB-Basisdienste, OLE DB-Anbieter für SQL Server, Oracle OLE DB-Anbieter, OLE DB-Anbieter für ODBC-Treiber, Data Shape-Anbieter und Remote-Datenanbieter)
* **ODBC** (einschließlich ODBC-Treiber-Managers, ODBC-Treiber für SQL und Oracle ODBC-Treiber)

### <a name="mdacwdac-components"></a>MDAC/WDAC-Komponenten

MDAC/WDAC umfasst folgende Komponenten:

* **ODBC:** Microsoft Open Database Connectivity (ODBC)-Schnittstelle ist eine C-Programmiersprache-Schnittstelle, die Clientanwendungen ermöglicht, Daten aus einer Vielzahl von Datenbank-Systeme (DBMS) zugreifen. Anwendungen, die diese API verwenden, sind für den Zugriff auf relationale Datenquellen nur beschränkt.
* **OLE DB:** OLE DB ist ein Satz von COM-Schnittstellen für den Zugriff auf Daten in einer Vielzahl von Datenspeichern. OLE DB-Anbieter, die für den Zugriff auf Daten in Datenbanken, Dateisystemen, Nachrichtenspeicher, Verzeichnisdienste, Workflow und Dokumentspeicher vorhanden sein.
* **ADO:** ActiveX Data Objects (ADO) stellt eine allgemeine Programmiermodell bereit. Obwohl etwas weniger leistungsfähiger als codieren, OLE DB- oder ODBC direkt, ADO einfach ist zu erlernen und zu verwenden. Es kann von Skriptsprachen, z. B. Microsoft Visual Basic Scripting Edition (VBScript) oder Microsoft JScript verwendet werden.
* **ADOMD:** ADO multidimensionales (ADOMD) wird mit mehrdimensionale Datenanbieter wie z. B. Microsoft OLAP-Anbieter, auch bekannt als Microsoft Analysis Services-Anbieter verwendet werden soll. Keine wichtigen Funktion haben, seit MDAC 2.0 wurden Verbesserungen vorgenommen.
* **ADOX:** ADO-Erweiterungen für DDL-Befehle und Sicherheit (ADOX) ermöglichen die Erstellung und Änderung von Definitionen einer Datenbank, Tabelle, Index oder gespeicherten Prozedur. Sie können mit jedem Anbieter ADOX verwenden. Der Microsoft Jet OLE DB-Anbieter bietet vollständige Unterstützung für ADOX, während Microsoft SQL Server OLE DB-Anbieter eingeschränkten Unterstützung bietet.
* **Microsoft SQL Server-Netzwerkbibliotheken:** die SQL Server-Netzwerkbibliotheken SQLOLEDB und SQLODBC für die Kommunikation mit SQL Server-Datenbank zu ermöglichen. Die folgenden SQL Server-Netzwerkbibliotheken sind veraltet in MDAC/WDAC-Versionen: Banyan Vines, AppleTalk, ServerNet, IPX/SPX, Giganet und RPC. TCP/IP und Named Pipes weiterhin unterstützt werden, und auf 64-Bit-Windows-Betriebssystems verfügbar sind.
* **MSDASQL:** Microsoft OLE DB-Anbieter für ODBC (MSDASQL) ermöglicht Anwendungen, die auf OLE DB und ADO (das OLE DB intern verwendet wird) den Zugriff auf Datenquellen über einen ODBC-Treiber integriert sind. MSDASQL ist ein OLE DB-Anbieter, der mit ODBC, statt einer Datenbank verbunden. Es ist vorgesehen als Brücke von OLE DB, ODBC-Treiber, wenn keine direkte OLE DB-Anbieter für eine Datenquelle vorhanden ist. MSDASQL im Lieferumfang von Windows-Betriebssystem sowie Windows Server 2008 und Vista SP1 wurden, dass der erste Windows frei, um eine 64-Bit-Version der Technologie einzuschließen.

### <a name="deprecated-mdacwdac-components"></a>Veraltete MDAC/WDAC-Komponenten

Diese Komponenten werden in der aktuellen Version von MDAC/WDAC weiterhin unterstützt, aber sie können in zukünftigen Versionen entfernt werden. Wenn Sie neue Anwendungen entwickeln, empfiehlt Microsoft, um vermeiden, verwenden diese Komponenten. Beim Aktualisieren oder ändern Sie vorhandene Anwendungen, entfernen Sie darüber hinaus eine Abhängigkeit von diesen Komponenten.

* **SQLOLEDB:** der Microsoft OLE DB-Anbieter für SQL Server (SQLOLEDB), die Zugriff auf Microsoft SQL Server unterstützt, ist veraltet. Die Verbindung auf zukünftige Versionen von SQL Server wird möglicherweise nicht unterstützt. Die Fähigkeit zum Herstellen einer Verbindung mit Versionen vor SQL Server 7 nach Windows 7 aus dem Betriebssystem entfernt wird. Neue Anwendungen sollten den Microsoft OLE DB-Treiber für SQL Server (MSOLEDBSQL) verwenden, die neue SQL Server-Funktionen unterstützt. Vorhandene Anwendungen sollten auf der Microsoft OLE DB-Treiber für SQL Server als auch für eine bessere Leistung, Zuverlässigkeit und unterstützbarkeit migrieren. Weitere Informationen finden Sie unter [Aktualisieren von einer Anwendung auf OLE DB-Treiber für SQL Server von MDAC](oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).
* **SQLODBC:** der Microsoft SQL Server-ODBC-Treiber (SQLODBC), die Zugriff auf Microsoft SQL Server unterstützt, ist veraltet. Die Verbindung auf zukünftige Versionen von SQL Server wird möglicherweise nicht unterstützt. Die Fähigkeit zum Herstellen einer Verbindung mit Versionen vor SQL Server 7 nach Windows 7 aus dem Betriebssystem entfernt wird. Neue Anwendungen sollten den Microsoft ODBC Driver für SQL Server unter Windows verwenden, die neue SQL Server-Funktionen unterstützt. Vorhandene Anwendungen sollten an den Microsoft ODBC Driver für SQL Server als auch für eine bessere Leistung, Zuverlässigkeit und unterstützbarkeit migrieren. Entsprechende Informationen finden Sie unter [Aktualisieren einer Anwendung von MDAC auf SQL Server Native Client](../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md).
* **Microsoft Jet 4.0-Datenbankmodul:** beginnend mit Version 2.6 enthält MDAC mehr Jet-Komponenten. Das heißt, MDAC 2.6, 2.7 und 2.8 enthalten keine Microsoft Jet, den Microsoft Jet OLE DB-Anbieter, die ODBC-Datenbanktreiber für Desktop oder Jet Datenzugriffsobjekte (DAO). Die Komponenten der Microsoft Jet-Datenbank-Engine 4.0 Status funktionale Veraltung eingegeben und durchgängig hoch, Engineering und Ebene featureverbesserungen nicht erhalten haben, da ein Teil von Microsoft Windows in Windows 2000.

  Es ist keine 64-Bit-Version des Jet-Datenbankmodul, der Jet OLE DB-Treiber, die Jet ODBC-Treiber oder Jet-DAO verfügbar. Weitere Informationen finden Sie unter [KB-Artikel 957570](http://support.microsoft.com/kb/957570). Wird ausgeführt auf 64-Bit-Versionen von Windows 32-Bit-Jet unter dem Windows-WOW64-Subsystem. Weitere Informationen unter WOW64 finden Sie unter der [WOW64 MSDN-Dokumentation](https://msdn.microsoft.com/library/windows/desktop/aa384274(v=vs.85).aspx). Systemeigene 64-Bit-Anwendungen können nicht mit der 32-Bit-Jet-Treiber unter WOW64 ausgeführt kommunizieren.

  Anstelle von Microsoft Jet, Microsoft empfiehlt die Verwendung [Microsoft SQL Server Express Edition](https://www.microsoft.com/sql-server/sql-server-editions-express) beim Entwickeln von neuen, Microsoft Access - Anwendungen, die einen relationalen Datenspeicher erfordert. Diese neue oder konvertierten Jet-Anwendungen können weiterhin Jet zu verwenden, Microsoft Office 2003 und früher-Dateien (.mdb und .xls) Nichtprimär-Datenspeicher verwendet. Allerdings sollten für diese Anwendungen Sie von Jet auf das 2007 Office System Driver migrieren möchten. Sie können [herunterladen das 2007 Office System Driver](https://www.microsoft.com/downloads/details.aspx?displaylang=en&FamilyID=7554f536-8c28-4598-9b72-ef94e038c891), können Sie Lese- und Schreibzugriff auf bereits vorhandene Dateien in Office 2003 (.mdb und xls) oder die Office 2007-Dateiformate (*.accdb, *.xlsm,.xlsx und.xlsb).

  > [!IMPORTANT]
  > Lesen Sie den 2007 Office System Endbenutzer-Lizenzvertrag für bestimmte nutzungseinschränkungen.

  > [!NOTE]
  > SQL Server-Anwendungen können auch das 2007 Office System zugreifen und früher Dateien aus SQL Server heterogener Datenkonnektivität und Integration Services Funktionen auch über das 2007 Office System Driver. Darüber hinaus können 64-Bit SQL Server-Anwendungen mithilfe von 32-Bit SQL Server Integration Services (SSIS) auf 64-Bit-Windows 32-Bit-Jet und 2007 Office System-Dateien zugreifen.

* **MSDADS:** mit dem Microsoft OLE DB-Anbieter für die Daten strukturieren (MSDADS), können Sie hierarchische Beziehungen zwischen den Schlüssel, Felder oder Rowsets in einer Anwendung erstellen. Seit MDAC 2.1 wurden keine wesentlichen Funktion Verbesserungen vorgenommen. Dieser Anbieter ist veraltet. Microsoft empfiehlt, XML, anstelle von MSDADS verwenden.
* **Oracle ODBC und Oracle OLE DB:** der Microsoft Oracle ODBC-Treiber (Oracle ODBC) und Microsoft OLE DB-Anbieter für Oracle (Oracle OLE DB) ermöglichen den Zugriff auf Oracle-Datenbankserver. Sie werden mithilfe von Oracle aufrufen Schnittstelle (OCI) Version 7 erstellt und bieten vollständige Unterstützung für Oracle 7. Es verwendet außerdem Oracle 7-Emulation eingeschränkten Unterstützung für Oracle 8-Datenbanken bereitstellen. Oracle unterstützt nicht mehr Anwendungen, die OCI Version 7 Aufrufe zu verwenden. Diese Technologien sind veraltet. Wenn Sie Oracle-Datenquellen verwenden, sollten Sie Oracle bereitgestellte Treiber und Anbieter migrieren.
* **RDS:** Remote Data Services (RDS) ist ein proprietäres Microsoft-Mechanismus für den Zugriff auf remote-ADO-Recordset-Objekte über das Internet oder Intranet. RDS ist veraltet. RDS wurden seit MDAC 2.1 keine wesentlichen Funktion-Verbesserungen vorgenommen. Microsoft hat es sich um .NET Framework veröffentlicht die verfügt über eine umfangreiche SOAP-Funktionen und RDS-Komponenten ersetzt. Alle RDS-Serverkomponenten werden vom Betriebssystem nach Windows 7 entfernt werden.
* **JRO:** Jet Replikationsobjekte (JRO) ist veraltet. JRO wird innerhalb von ADO mit Jet verwendet (*.mdb) zu erstellen und Komprimieren der Jet-Datenbanken (.mdb), und führen Sie die Verwaltung von Jet Datenbanken. MDAC 2.7 werden der letzten Version. JRO wird nicht auf 64-Bit-Windows-Betriebssystems verfügbar sein. JRO wird nicht unterstützt, in der Microsoft Access 2007-Dateiformat (*".accdb").
* **16-Bit-ODBC-Unterstützung:** bei Verwendung von 16-Bit-Anwendungen sollten Sie die Migration zu einer 32-Bit-Anwendung. 16-Bit-Funktionalität ist veraltet und wird von 64-Bit-Betriebssystemen entfernt wird. Weitere Informationen finden Sie unter [Knowledge Base-Artikel 896458](http://support.microsoft.com/kb/896458).
* **Einfache OLE DB-Anbieter (MSDAOSP):** einfache OLE DB-Anbieter bietet ein Framework zum schnellen Erstellen von OLE DB-Anbieter für einfache Daten. MSDAOSP ist veraltet.
* **ODBC-Cursorbibliothek:** ODBC Cursor Library (ODBCCR32.dll) bietet begrenzte Daten für die clientseitige Cursor. ODBC-Cursorbibliothek wurde als veraltet markiert; Ihre Anwendung kann als Ersatz serverseitigen cursorimplementierungen verwenden.
* **OLE DB-Out-of-Process-Schnittstelle Remoting:** Remoting für OLE DB-Schnittstelle (msdaps.dll) wurde versucht, OLE DB-Anbieter außerhalb des Prozesses ausgeführt ermöglichen. OLE DB-Schnittstelle der Out-of-Process-Remoting ist veraltet.
* **AppleTalk und Netzwerkbibliotheken für Banyan Vines SQL:** Netzwerkbibliotheken für die Netzwerkprotokolle Banyan Vines, AppleTalk, ServerNet, IPX/SPX, Giganet und RPC SQL sind veraltet. Wenn Sie eine dieser Technologien verwenden, sollten Sie Ihre Anwendungen verwenden, z. B. TCP/IP und Named Pipe-Netzwerkbibliotheken, ändern.

### <a name="mdacwdac-releases"></a>MDAC/WDAC-Versionen

Hier ist eine Liste der unterstützbarkeit-Szenarios mit früheren Versionen von MDAC/WDAC, beginnend mit der frühesten.

* **MDAC 1.5, MDAC 2.0 und 2.1 MDAC:** Versionen von MDAC wurden unabhängig Versionen, die über das Microsoft Windows NT Option Pack, das Microsoft Windows-Plattform-SDK oder der MDAC-Website veröffentlicht wurden. Diese Versionen von MDAC werden nicht mehr unterstützt.
* **MDAC 2.5:** diese Version von MDAC war mit dem Betriebssystem Windows 2000 enthalten. Servicepacks von MDAC 2.5 wurden mit den entsprechenden Windows 2000 Servicepacks enthalten.
* **MDAC 2.6:** MDAC 2.6 RTM, SP1 und SP2 wurden Lieferumfang von Microsoft SQL Server 2000 RTM, SP1 und SP2 bzw. Darüber hinaus wurden diese MDAC Servicepacks mit der MDAC-Website in Übereinstimmung mit der Freigabezeitplan für den Microsoft SQL Server 2000 Service Pack veröffentlicht. Sie können diese Version von MDAC und den zugehörigen Servicepacks auf Windows 2000, Windows Millenium Edition, Windows NT, Windows 95- und Windows 98-Plattformen installieren. Diese Version von MDAC wird nicht mehr unterstützt.
* **MDAC 2.7:** diese Version von MDAC war mit den Betriebssystemen Microsoft Windows XP RTM und SP1 enthalten. Sie können diese Version von MDAC und den zugehörigen Servicepacks für Windows 2000, Windows Millennium Edition, Windows NT und Windows 98-Plattformen installieren. Sie können diese Version auf der Windows XP-Plattform nur über das Betriebssystem oder die Service Packs installieren. Diese Version von MDAC wird nicht mehr unterstützt.
* **MDAC 2.8:** dieser Version von MDAC wurde Lieferumfang von Windows Server 2003 und Windows XP SP2 und höher. Sie können diese Version von MDAC und den zugehörigen Servicepacks auch unter Windows 2000 installieren.

  * Die 32-Bit-Version von MDAC 2.8 wurde auch der MDAC-Website zur gleichen Zeit veröffentlicht, die an den Kunden die Windows Server 2003 veröffentlicht wurden.
  * Die 64-Bit-Version von MDAC 2.8 wurde mit der 64-Bit-Version von Windows Server 2003 und Windows XP freigegeben.

* **Windows Data Access Components (WDAC):** MDAC seinen Namen in WDAC - "Windows Data Access Components" beginnend mit Windows Vista und Windows Server 2008 geändert. WDAC ist Bestandteil des Betriebssystems und ist nicht separat für die Verteilung verfügbar. Wartungsfreundlichkeit für WDAC unterliegt den Lebenszyklus des Betriebssystems ab.

  32-Bit und 64-Bit-Versionen von WDAC werden mit den 32-Bit und 64-Bit-Versionen von Windows-Betriebssysteme aufgehoben.

## <a name="obsolete-data-access-technologies"></a>Veraltete datenzugriffstechnologien

Veraltete Technologien sind Technologien, die nicht erweitert oder aktualisiert wurden in verschiedenen Produktversionen und, die aus zukünftigen Produktversionen ausgeschlossen. Verwenden Sie diese Technologien nicht verfügbar, wenn Sie neue Anwendungen schreiben. Wenn Sie vorhandene Anwendungen, die ändern mit diesen Technologien geschrieben werden, sollten Sie diese Anwendungen ADO.NET oder eine andere Technologie migrieren.

Die folgenden Komponenten werden als veraltet betrachtet:

* **DB-Library:** DB-Library-ist ein SQL Server-spezifische-Programmiermodell, die C-APIs enthält. Es wurden keine featureverbesserungen für die DB-Library seit SQL Server 6.5. Der endgültigen Version wurde mit SQL Server 2000 und wird auf 64-Bit-Windows-Betriebssystems nicht portiert werden.
* **Embedded SQL (E-SQL):** E SQL ist ein SQL Server-spezifische-Programmiermodell, mit der Transact-SQL-Anweisungen, die in Visual C#-Code eingebettet werden kann. In der E-SQL wurden seit SQL Server 6.5 keine Funktion Verbesserungen vorgenommen. Der endgültigen Version wurde mit SQL Server 2000 und wird auf 64-Bit-Windows-Betriebssystems nicht portiert werden.
* **Datenzugriffsobjekte (DAO):** DAO ermöglicht den Zugriff auf Datenbanken JET (Access). Diese API kann von Microsoft Visual Basic, Microsoft Visual C++ und Skriptsprachen verwendet werden. Es wurde mit Microsoft Office 2000 und Office XP. DAO 3.6 ist die endgültige Version dieser Technologie. Es wird nicht auf 64-Bit-Windows-Betriebssystems verfügbar sein.
* **Remote Data Objects (RDO):** RDO wurde speziell dazu entwickelt, den Zugriff auf remote relationalen ODBC-Datenquellen und ODBC verwenden, ohne komplexe Anwendungscode erleichtert. Es wurde in Microsoft Visual Basic-Versionen 4, 5 und 6 eingefügt. RDO-Version 2.0 wurde die endgültige Version dieser Technologie.