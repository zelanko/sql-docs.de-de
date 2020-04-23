---
title: Microsoft OLE DB-Treiber für SQL Server | Microsoft-Dokumentation
description: Der Microsoft OLE DB-Treiber für SQL Server ermöglicht Konnektivität mit SQL Server und Azure SQL-Datenbank über standardmäßige OLE DB-APIs.
ms.custom: ''
ms.date: 02/12/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- MSOLEDBSQL, about OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server, about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server
- MSOLEDBSQL
- native data access [OLE DB Driver for SQL Server]
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 52877846ab573b146c148dab681cd45aec0a083c
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488510"
---
# <a name="microsoft-ole-db-driver-for-sql-server"></a>Microsoft OLE DB-Treiber für SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

Der OLE DB-Treiber für SQL Server ist eine eigenständige Datenzugriffs-API (Application Programming Interface), die für OLE DB verwendet wird und in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] eingeführt wurde. Der OLE DB-Treiber für SQL Server stellt den SQL OLE DB-Treiber in einer Dynamic Link Library (DLL) bereit. Sie stellt auch neue Funktionen bereit, die weit über die von Windows Data Access Components (Windows DAC, früher Microsoft Data Access Components oder MDAC genannt) bereitgestellten Funktionalität hinausgehen. Der OLE DB-Treiber für SQL Server kann zur Erstellung neuer Anwendungen oder zur Erweiterung vorhandener Anwendungen verwendet werden, die in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] neu eingeführte Funktionen nutzen müssen, wie Multiple Active Result Sets (MARS), benutzerdefinierte Datentypen (UDT), Abfragebenachrichtigungen, Momentaufnahmenisolation und Unterstützung für XML-Datentypen.  
  
> [!NOTE]  
> Eine Liste der Unterschiede zwischen dem OLE DB-Treiber für SQL Server und Windows DAC sowie Informationen zu Problemen, die vor der Aktualisierung einer Windows DAC-Anwendung auf den OLE DB-Treiber zu berücksichtigen sind, finden Sie unter [Aktualisieren einer Anwendung auf den OLE DB-Treiber für SQL Server über MDAC](../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).  

> [!IMPORTANT]
> Der vorherige [Microsoft OLE DB-Anbieter für SQL Server](../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) (SQLOLEDB) und [SQL Server Native Client OLE DB](../../relational-databases/native-client/sql-server-native-client.md)-Anbieter (SQLNCLI) bleiben als veraltet markiert und sollten nicht mehr für neue Bereitstellungen verwendet werden.
  
 Der OLE DB-Treiber für SQL Server kann in Verbindung mit den OLE DB-Basisdiensten von Windows DAC verwendet werden, dies wird jedoch nicht vorausgesetzt. Ob die Basisdienste verwendet werden oder nicht, hängt von den Anforderungen der jeweiligen Anwendung ab (beispielsweise wenn Verbindungspooling erforderlich ist).  
  
 ADO (ActiveX Data Object)-Anwendungen können den OLE DB-Treiber für SQL Server verwenden. Es wird allerdings empfohlen, ADO in Verbindung mit dem Schlüsselwort für **DataTypeCompatibility**-Verbindungszeichenfolgen (bzw. der zugehörigen **DataSource**-Eigenschaft) zu verwenden. Beim Einsatz des OLE DB-Treibers für SQL Server können ADO-Anwendungen die neuen Funktionen nutzen, die in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] eingeführt wurden und für den OLE DB-Treiber für SQL Server über die Verbindungszeichenfolgen-Schlüsselwörter, OLE DB-Eigenschaften oder [!INCLUDE[tsql](../../includes/tsql-md.md)] verfügbar sind. Weitere Informationen zur Verwendung dieser Funktionen mit ADO finden Sie unter [Verwenden von ADO mit dem OLE DB-Treiber für SQL Server](../oledb/applications/using-ado-with-oledb-driver-for-sql-server.md).  
  
 Der OLE DB-Treiber für SQL Server wurde entwickelt, um eine einfache Methode für den nativen Datenzugriff auf SQL Server über OLE DB zur Verfügung zu stellen. Er bietet eine Möglichkeit, Datenzugriffsfunktionen zu optimieren und weiterzuentwickeln, ohne die aktuellen Windows DAC-Komponenten zu ändern, die jetzt Teil der Microsoft Windows-Plattform sind.  
  
 Der OLE DB-Treiber für SQL Server verwendet zwar Komponenten von Windows DAC, ist jedoch nicht ausdrücklich von einer bestimmten Version von Windows DAC abhängig. Sie können den OLE DB-Treiber für SQL Server mit der Version von Windows DAC verwenden, die zusammen mit dem vom OLE DB-Treiber für SQL Server unterstützten Betriebssystem installiert wird.  

 ## <a name="different-generations-of-ole-db-drivers"></a>Verschiedene Generationen des OLE DB-Treibers

Es gibt drei verschiedene Generationen von Microsoft OLE DB-Anbietern für SQL Server.

### <a name="1-microsoft-ole-db-provider-for-sql-server-sqloledb"></a>1. Microsoft OLE DB-Anbieter für SQL Server (SQLOLEDB)
Der [Microsoft OLE DB-Anbieter für SQL Server](../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) (SQLOLEDB) ist weiterhin als Teil von [Windows Data Access Components](https://msdn.microsoft.com/library/ms692897.aspx) erhältlich. Er ist jedoch veraltet, und es wird nicht empfohlen, diesen Treiber für neue Bereitstellungen zu verwenden.

### <a name="2-sql-server-native-client-snac"></a>2. SQL Server Native Client (SNAC)
Ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] umfasst der [SQL Server Native Client (SNAC)](../../relational-databases/native-client/sql-server-native-client.md) eine OLE DB-Anbieterschnittstelle (SQLNCLI) und ist der im Lieferumfang von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] über [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] bereitgestellte OLE DB-Anbieter.

[Seit 2011 gilt dieser jedoch als veraltet](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/), und es wird nicht empfohlen, diesen Treiber für neue Bereitstellungen zu verwenden. Weitere Informationen zum SNAC-Lebenszyklus und den verfügbaren Downloads finden Sie im Blog [SNAC lifecycle explained](https://blogs.msdn.microsoft.com/sqlreleaseservices/snac-lifecycle-explained/) (Erklärung des SNAC-Lebenszyklus).

### <a name="3-microsoft-ole-db-driver-for-sql-server-msoledbsql"></a>3. Microsoft OLE DB-Treiber für SQL Server (MSOLEDBSQL)
OLE DB wurde 2018 [als nicht mehr veraltet](https://blogs.msdn.microsoft.com/sqlnativeclient/2017/10/06/announcing-the-new-release-of-ole-db-driver-for-sql-server/) gekennzeichnet und freigegeben.

Der neue OLE DB-Anbieter wird als Microsoft OLE DB-Treiber für SQL Server (MSOLEDBSQL) bezeichnet. In Zukunft wird der neue Anbieter mit den neuesten Serverfunktionen aktualisiert.

> [!NOTE]
> Wenn Sie den neuen Microsoft OLE DB-Treiber für SQL Server in vorhandenen Anwendungen verwenden möchten, sollten Sie Ihre Verbindungszeichenfolgen von SQLOLEDB oder SQLNCLI zu MSOLEDBSQL konvertieren.
  
## <a name="in-this-section"></a>In diesem Abschnitt  
[Verwendung des OLE DB-Treibers für SQL Server](../oledb/when-to-use-oledb-driver-for-sql-server.md)  
 In diesem Artikel wird erläutert, welche Rolle der OLE DB-Treiber für SQL Server unter den Datenzugriffstechnologien von Microsoft spielt und welche Unterschiede gegenüber Windows DAC und ADO.NET bestehen. Sie erhalten Entscheidungshilfen für die Auswahl einer Datenzugriffstechnologie.  
  
 [Features des OLE DB-Treibers für SQL Server](../oledb/features/oledb-driver-for-sql-server-features.md )  
 Beschreibt die vom OLE DB-Treiber für SQL Server unterstützten Funktionen.  
  
 [Erstellen von Anwendungen mit dem OLE DB-Treiber für SQL Server](../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
 Außerdem erhalten Sie einen Überblick über die Entwicklung von OLE DB-Treiber für SQL Server sowie die Unterschiede gegenüber Windows DAC, die verwendeten Komponenten und darüber, wie ADO in Verbindung damit verwendet werden kann.  
  
 In diesem Abschnitt wird auch die Installation und die Bereitstellung des OLE DB-Treibers für SQL Server sowie die Weiterverteilung der Bibliothek des OLE DB-Treibers für SQL Server erläutert.  
  
 [Systemanforderungen für den OLE DB-Treiber für SQL Server](../oledb/system-requirements-for-oledb-driver-for-sql-server.md)  
 Erläutert die zur Nutzung des OLE DB-Treibers für SQL Server erforderlichen Systemressourcen.  
  
 [OLE DB-Treiber für SQL Server-Programmierung](../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
 Bietet Informationen zur Verwendung des OLE DB-Treibers für SQL Server.  
  
 [Weitere Informationen zum OLE DB-Treiber für SQL Server](../oledb/finding-more-oledb-driver-for-sql-server-information.md)  
 Stellt zusätzliche Ressourcen über den OLE DB-Treiber für SQL Server bereit, einschließlich Links zu externen Ressourcen und zum Abrufen weiterer Hilfe.  
  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aktualisieren einer Anwendung von SQL Server 2005 Native Client](../oledb/applications/updating-an-application-from-sql-server-2005-native-client.md)    
 [Vorgehensweisen für OLE DB](../oledb/ole-db-how-to/ole-db-how-to-topics.md)  
  
  
