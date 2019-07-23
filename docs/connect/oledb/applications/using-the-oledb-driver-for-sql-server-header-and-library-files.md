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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989236"
---
# <a name="using-the-ole-db-driver-for-sql-server-header-and-library-files"></a>Verwenden des OLE DB-Treibers für SQL Server-Header- und -Bibliotheksdateien
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB Treiber für SQL Server Header-und Bibliotheksdateien werden installiert, wenn während des Installationsvorgangs die Option OLE DB Treiber für SQL Server SDK ausgewählt wird. Es ist wichtig, beim Entwickeln von Anwendungen alle für die Entwicklung erforderlichen Dateien in die Entwicklungsumgebung zu kopieren. Weitere Informationen zum Installieren und erneuten verteilen OLE DB Treibers für SQL Server finden Sie unter [Installieren OLE DB Treibers für SQL Server](../../oledb/applications/installing-oledb-driver-for-sql-server.md).  
  
 Der OLE DB Treiber für SQL Server Header-und Bibliotheksdateien werden an folgendem Speicherort installiert:  
  
 *% Program Files%* \Microsoft SQL server\client sdk\oledb\182 \SDK  
  
 Der OLE DB Treiber für SQL Server Header Datei (msoledbsql. h) kann verwendet werden, um Ihren benutzerdefinierten Anwendungen OLE DB Treiber für SQL Server Datenzugriffs Funktionalität hinzuzufügen. Die Headerdatei des OLE DB-Treibers für SQL Server enthält alle Definitionen, Attribute, Eigenschaften und Schnittstellen, damit Sie die neuen, in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] eingeführten Funktionen nutzen können.  
  
 Zusätzlich zum OLE DB Treiber für SQL Server Header Datei gibt es auch eine msoledbsql. lib-Bibliotheksdatei, die die Export Bibliothek für die [OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md) -Funktionalität ist.  
  
 Die Headerdatei des OLE DB-Treibers für SQL Server ist abwärtskompatibel mit der mit Microsoft Data Access Components (MDAC) verwendeten Headerdatei „sqloledb.h“, enthält aber weder die CLSIDs für SQLOLEDB (den in MDAC enthaltenen OLE DB-Anbieter für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]) noch die Symbole für die XML-Funktionalität. Letztere wird nicht vom OLE DB-Treiber für SQL Server unterstützt.    
  
 OLE DB Anwendungen, für die der OLE DB-Treiber für SQL Server verwendet wird, muss nur auf msoledbsql. h verwiesen werden. Wenn eine Anwendung MDAC (SQLOLEDB) und den OLE DB-Treiber für SQL Server verwendet, kann sowohl auf „sqloledb.h“ als auch auf „msoledbsql.h“ verwiesen werden, unter der Voraussetzung, dass „sqloledb.h“ zuerst angegeben wird.  
  
## <a name="using-the-ole-db-driver-for-sql-server-header-file"></a>Verwenden des OLE DB Treibers für SQL Server Header Datei  
 Wenn Sie den OLE DB-Treiber für die SQL Server Header Datei verwenden möchten, müssen Sie eine **include** -AnweisungC++ innerhalb des C/Programmiercodes verwenden. In den folgenden Abschnitten wird beschrieben, wie Sie in OLE DB Anwendungen Vorgehen.  
  
> [!NOTE]  
>  Der OLE DB Treiber für SQL Server Header-und Bibliotheksdateien kann nur mit Visual Studio C++ 2012 oder höher kompiliert werden.  
  
### <a name="ole-db"></a>OLE DB  
 Verwenden Sie die folgenden Programmiercode Zeilen, um den OLE DB Treiber für SQL Server Header Datei in einer OLE DB Anwendung zu verwenden:  
  
```    
include "msoledbsql.h";  
```  
  
> [!NOTE]  
>  Wenn die Anwendung über eine **include** -Anweisung für sqloledb. h verfügt, muss die **include** -Anweisung für msoledbsql. h darauf folgen.  
  
 Verwenden Sie beim Erstellen einer Verbindung mit einer Datenquelle über OLE DB Treiber für SQL Server "msoledbsql" als Zeichenfolge für den Anbieter Namen.  

  
## <a name="component-names-and-properties-by-version"></a>Komponentennamen und Eigenschaften nach Version  

|Eigenschaft|OLE DB-Treiber für SQL Server|MDAC|  
|--------|----------------------------|----|   
|OLE DB PROGID|MSOLEDBSQL|SQLOLEDB|  
|OLE DB-Headerdateiname|msoledbsql.h|Sqloledb.h|  
|OLE DB-Anbieter-DLL|msoledbsql.dll|Sqloledb.dll| 
  
  
## <a name="static-linking-and-bcp-functions"></a>Statische Verknüpfung und BCP-Funktionen  
 Wenn eine Anwendung BCP-Funktionen verwendet, muss in der Verbindungszeichenfolge der Treiber mit derselben Version angegeben werden, die mit der für die Anwendungskompilierung verwendeten Headerdatei und Bibliothek ausgeliefert wurde.  
  
 Weitere Informationen finden Sie unter Ausführen von [Massen Kopier Vorgängen](../../oledb/features/performing-bulk-copy-operations.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Anwendungen mit dem OLE DB-Treiber für SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
  
  
