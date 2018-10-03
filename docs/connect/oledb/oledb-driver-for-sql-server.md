---
title: Microsoft OLE DB-Treiber für SQL Server | Microsoft-Dokumentation
description: Microsoft OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/14/2018
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
manager: craigg
ms.openlocfilehash: befcc84662b2273f81faaded76045d4d44b03e98
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47687868"
---
# <a name="microsoft-ole-db-driver-for-sql-server"></a>Microsoft OLE DB-Treiber für SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

  OLE DB-Treiber für SQL Server ist eine eigenständige Data Access Application programming Interface (API), verwendet für OLE DB, das in eingeführte [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. OLE DB-Treiber für SQL Server bietet es sich um den SQL OLE DB-Treiber in einer Dynamic Link Library (DLL). Sie stellt auch neue Funktionen bereit, die weit über die von Windows Data Access Components (Windows DAC, früher Microsoft Data Access Components oder MDAC genannt) bereitgestellten Funktionalität hinausgehen. Der OLE DB-Treiber für SQL Server kann zur Erstellung neuer Anwendungen oder zur Erweiterung vorhandener Anwendungen verwendet werden, die in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] neu eingeführte Funktionen nutzen müssen, wie Multiple Active Result Sets (MARS), benutzerdefinierte Datentypen (UDT), Abfragebenachrichtigungen, Momentaufnahmenisolation und Unterstützung für XML-Datentypen.  
  
> [!NOTE]  
>  Eine Liste der Unterschiede zwischen der OLE DB-Treiber für SQL Server und Windows DAC sowie Informationen zu Problemen zu berücksichtigen, bevor Sie eine Windows-DAC-Anwendung auf OLE DB-Treiber für SQL Server aktualisieren, finden Sie unter [Aktualisieren von einer Anwendung auf OLE DB-Treiber für SQL Server über MDAC](../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).  
  
 Der OLE DB-Treiber für SQL Server kann in Verbindung mit den OLE DB-Basisdiensten von Windows DAC verwendet werden, dies wird jedoch nicht vorausgesetzt. Ob die Basisdienste verwendet werden oder nicht, hängt von den Anforderungen der jeweiligen Anwendung ab (beispielsweise wenn Verbindungspooling erforderlich ist).  
  
 ActiveX Data Object (ADO)-Anwendungen können den OLE DB-Treiber für SQL Server verwenden, aber es wird empfohlen, das Verwenden von ADO in Verbindung mit der **DataTypeCompatibility** Schlüsselwort für Verbindungszeichenfolgen (bzw. der zugehörigen  **DataSource** Eigenschaft). Wenn der OLE DB-Treiber für SQL Server verwenden, ADO-Anwendungen nutzen, die diese neuen Funktionen in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , die über die OLE DB-Treiber für SQL Server über die Verbindungszeichenfolgen-Schlüsselwörter oder OLE DB-Eigenschaften verfügbar sind oder [!INCLUDE[tsql](../../includes/tsql-md.md)]. Weitere Informationen zur Verwendung dieser Funktionen mit ADO finden Sie unter [mithilfe von ADO mit OLE DB-Treiber für SQL Server](../oledb/applications/using-ado-with-oledb-driver-for-sql-server.md).  
  
 Der OLE DB-Treiber für SQL Server wurde entwickelt, um eine einfache Methode für den nativen Datenzugriff auf SQL Server über OLE DB zur Verfügung zu stellen. Es bietet eine Möglichkeit, Innovationen und neue Datenzugriffsfunktionen weiterentwickeln, ohne die aktuellen Windows DAC-Komponenten, die jetzt Teil der Microsoft Windows-Plattform sind.  
  
 Der OLE DB-Treber für SQL Server verwendet zwar Komponenten von Windows DAC, ist jedoch nicht ausdrücklich von einer bestimmten Version von Windows DAC abhängig. Sie können den OLE DB-Treiber für SQL Server mit der Version von Windows DAC verwenden, die mit einem beliebigen von OLE DB-Treiber für SQL Server unterstützten Betriebssystem installiert ist.  

 ## <a name="different-generations-of-ole-db-drivers"></a>Verschiedene Generationen von OLE DB-Treiber

Es gibt drei verschiedene Generationen von Microsoft OLE DB-Anbieter für SQL Server.

### <a name="1-microsoft-ole-db-provider-for-sql-server-sqloledb"></a>1. Microsoft OLE DB-Anbieter für SQL Server (SQLOLEDB)
Die [Microsoft OLE DB-Anbieter für SQL Server](../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) (SQLOLEDB) wird weiterhin als Bestandteil von [Windows Data Access Components](https://msdn.microsoft.com/library/ms692897.aspx). Es wird nicht mehr verwaltet, und es wird nicht empfohlen, diese Treiber für die neue Entwicklung zu verwenden.

### <a name="2-sql-server-native-client-snac"></a>2. SQL Server Native Client (SNAC)
Ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [SQL Server Native Client (SNAC)](../../relational-databases/native-client/sql-server-native-client.md) enthält eine OLE DB-Provider-Schnittstelle (SQLNCLI) und OLE DB-Anbieter, die im Lieferumfang [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] über [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].

Es war [als im Jahr 2011 veraltet bekanntgegeben](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/) und es wird nicht empfohlen, diese Treiber für die neue Entwicklung zu verwenden. Weitere Informationen zu den SNAC-Lebenszyklus und die verfügbaren Downloads, finden Sie unter [SNAC-Lebenszyklus erklärt](https://blogs.msdn.microsoft.com/sqlreleaseservices/snac-lifecycle-explained/).

### <a name="3-microsoft-ole-db-driver-for-sql-server-msoledbsql"></a>3. Microsoft OLE DB-Treiber für SQL Server (MSOLEDBSQL)
OLE DB wurde [aufgehoben](https://blogs.msdn.microsoft.com/sqlnativeclient/2017/10/06/announcing-the-new-release-of-ole-db-driver-for-sql-server/) und 2018 veröffentlicht.

Die neue OLE DB-Anbieter wird der Microsoft OLE DB-Treiber für SQL Server (MSOLEDBSQL) aufgerufen. Der neue Anbieter wird mit den neuesten Serverfunktionen, die in Zukunft aktualisiert werden.

> [!NOTE]
> Um der neuen Microsoft OLE DB-Treiber für SQL Server in vorhandene Anwendungen zu verwenden, sollten Sie planen, um die Verbindungszeichenfolgen von SQLOLEDB oder SQLNCLI, in MSOLEDBSQL zu konvertieren.
  
## <a name="in-this-section"></a>In diesem Abschnitt  
[Verwendung des OLE DB-Treibers für SQL Server](../oledb/when-to-use-oledb-driver-for-sql-server.md)  
 In diesem Artikel wird erläutert, welche Rolle der OLE DB-Treiber für SQL Server unter den Datenzugriffstechnologien von Microsoft spielt und welche Unterschiede gegenüber Windows DAC und ADO.NET bestehen. Sie erhalten Entscheidungshilfen für die Auswahl einer Datenzugriffstechnologie.  
  
 [OLE DB-Treiber für SQL Server-Features](../oledb/features/oledb-driver-for-sql-server-features.md )  
 Beschreibt die Funktionen von OLE DB-Treiber für SQL Server unterstützt.  
  
 [Erstellen von Anwendungen mit dem OLE DB-Treiber für SQL Server](../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
 Außerdem erhalten Sie einen Überblick über die Entwicklung von OLE DB-Treiber für SQL Server sowie die Unterschiede gegenüber Windows DAC, die verwendeten Komponenten und darüber, wie ADO in Verbindung damit verwendet werden kann.  
  
 Dieser Abschnitt beschreibt auch die OLE DB-Treiber für SQL Server-Installation und Bereitstellung, einschließlich der weiterverteilung der OLE DB-Treiber für SQL Server-Bibliothek.  
  
 [Systemanforderungen für den OLE DB-Treiber für SQL Server](../oledb/system-requirements-for-oledb-driver-for-sql-server.md)  
 Erläutert die Systemressourcen für die Verwendung von OLE DB-Treiber für SQL Server erforderlich sind.  
  
 [OLE DB-Treiber für SQL Server-Programmierung](../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
 Enthält Informationen zur Verwendung der OLE DB-Treiber für SQL Server.  
  
 [Weitere Informationen zum OLE DB-Treiber für SQL Server](../oledb/finding-more-oledb-driver-for-sql-server-information.md)  
 Stellt zusätzliche Ressourcen zu OLE DB-Treiber für SQL Server, einschließlich Links zu externen Ressourcen und zum Abrufen weiterer Hilfe bereit.  
  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Aktualisieren einer Anwendung von SQL Server 2005 Native Client](../oledb/applications/updating-an-application-from-sql-server-2005-native-client.md)    
 [Vorgehensweisen für OLE DB](../oledb/ole-db-how-to/ole-db-how-to-topics.md)  
  
  
