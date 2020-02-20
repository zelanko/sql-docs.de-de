---
title: Verwenden des OLE DB-Treibers für SQL Server-Header- und -Bibliotheksdateien | Microsoft-Dokumentation
description: Verwenden des OLE DB-Treibers für SQL Server-Header- und -Bibliotheksdateien
ms.custom: ''
ms.date: 02/12/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- header files [OLE DB Driver for SQL Server]
- MSOLEDBSQL, header files
- OLE DB, header files
- library files [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, header files
- data access [OLE DB Driver for SQL Server], header files
- data access [OLE DB Driver for SQL Server], library files
- OLE DB Driver for SQL Server, library files
- MSOLEDBSQL, library files
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 93b906a0604772fe224b1e63eaf6eed9eb8af983
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67989236"
---
# <a name="using-the-ole-db-driver-for-sql-server-header-and-library-files"></a>Verwenden des OLE DB-Treibers für SQL Server-Header- und -Bibliotheksdateien
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Die Header- und Bibliotheksdateien des OLE DB-Treibers für SQL Server werden installiert, wenn die Option „OLE DB-Treiber für SQL Server“ während des Installationsprozesses ausgewählt wird. Es ist wichtig, beim Entwickeln von Anwendungen alle für die Entwicklung erforderlichen Dateien in die Entwicklungsumgebung zu kopieren. Weitere Informationen zum Installieren und erneuten Verteilen des OLE DB-Treibers für SQL Server finden Sie unter [Installieren des OLE DB-Treibers für SQL Server](../../oledb/applications/installing-oledb-driver-for-sql-server.md).  
  
 Die Header- und Bibliotheksdateien des OLE DB-Treibers für SQL Server werden am folgenden Speicherort installiert:  
  
 *%PROGRAMME%* \Microsoft SQL Server\Client SDK\OLEDB\182\SDK  
  
 Die Headerdatei für den OLE DB-Treiber für SQL Server (msoledbsql.h) kann verwendet werden, um Ihren benutzerdefinierten Anwendungen die Datenzugriffsfunktionalität des OLE DB-Treibers für SQL Server hinzuzufügen. Die Headerdatei des OLE DB-Treibers für SQL Server enthält alle Definitionen, Attribute, Eigenschaften und Schnittstellen, damit Sie die neuen, in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] eingeführten Funktionen nutzen können.  
  
 Zusätzlich zur Headerdatei für den OLE DB-Treiber für SQL Server gibt es auch eine msoledbsql.lib-Bibliotheksdatei, die die Exportbibliothek für die [OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)-Funktionalität ist.  
  
 Die Headerdatei des OLE DB-Treibers für SQL Server ist abwärtskompatibel mit der mit Microsoft Data Access Components (MDAC) verwendeten Headerdatei „sqloledb.h“, enthält aber weder die CLSIDs für SQLOLEDB (den in MDAC enthaltenen OLE DB-Anbieter für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]) noch die Symbole für die XML-Funktionalität. Letztere wird nicht vom OLE DB-Treiber für SQL Server unterstützt.    
  
 OLE DB-Anwendungen, die den OLE DB-Treiber für SQL Server verwenden, müssen nur auf „msoledbsql.h“ verweisen. Wenn eine Anwendung MDAC (SQLOLEDB) und den OLE DB-Treiber für SQL Server verwendet, kann sowohl auf „sqloledb.h“ als auch auf „msoledbsql.h“ verwiesen werden, unter der Voraussetzung, dass „sqloledb.h“ zuerst angegeben wird.  
  
## <a name="using-the-ole-db-driver-for-sql-server-header-file"></a>Verwenden der Headerdatei des OLE DB-Treibers für SQL Server  
 Zum Verwenden der Headerdatei des OLE DB-Treibers für SQL Server müssen Sie eine **include**-Anweisung in Ihrem C-/C++-Programmcode angeben. In den folgenden Abschnitten wird dies für OLE DB-Anwendungen beschrieben.  
  
> [!NOTE]  
>  Die Header- und Bibliotheksdateien des OLE DB-Treibers für SQL Server können nur mithilfe von Visual Studio C++ 2012 oder höher kompiliert werden.  
  
### <a name="ole-db"></a>OLE DB  
 Zum Verwenden der Headerdatei des OLE DB-Treibers für SQL Server in einer OLE DB-Anwendung geben Sie den folgenden Programmiercode ein:  
  
```    
include "msoledbsql.h";  
```  
  
> [!NOTE]  
>  Wenn die Anwendung eine **include**-Anweisung für „sqloledb.h“ aufweist, sollte die **include**-Anweisung für „msoledbsql.h“ nach der Anweisung für „sqloledb.h“ stehen.  
  
 Verwenden Sie zum Herstellen einer Verbindung mit einer Datenquelle über den OLE DB-Treiber für SQL Server die Zeichenfolge „MSOLEDBSQL“ als Anbieternamen-Zeichenfolge.  

  
## <a name="component-names-and-properties-by-version"></a>Komponentennamen und Eigenschaften nach Version  

|Eigenschaft|OLE DB-Treiber für SQL Server|MDAC|  
|--------|----------------------------|----|   
|OLE DB PROGID|MSOLEDBSQL|SQLOLEDB|  
|OLE DB-Headerdateiname|msoledbsql.h|Sqloledb.h|  
|OLE DB-Anbieter-DLL|msoledbsql.dll|Sqloledb.dll| 
  
  
## <a name="static-linking-and-bcp-functions"></a>Statische Verknüpfung und BCP-Funktionen  
 Wenn eine Anwendung BCP-Funktionen verwendet, muss in der Verbindungszeichenfolge der Treiber mit derselben Version angegeben werden, die mit der für die Anwendungskompilierung verwendeten Headerdatei und Bibliothek ausgeliefert wurde.  
  
 Weitere Informationen finden Sie unter [Durchführen von Massenkopiervorgängen](../../oledb/features/performing-bulk-copy-operations.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Anwendungen mit dem OLE DB-Treiber für SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
  
  
