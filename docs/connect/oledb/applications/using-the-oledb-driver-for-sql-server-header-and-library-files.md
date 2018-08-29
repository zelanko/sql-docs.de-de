---
title: Verwenden des OLE DB-Treibers für SQL Server-Header- und -Bibliotheksdateien | Microsoft-Dokumentation
description: Verwenden des OLE DB-Treibers für SQL Server-Header- und -Bibliotheksdateien
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
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
manager: craigg
ms.openlocfilehash: bb2d14d1426e339773c4ed6494d95dea527eec29
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43030596"
---
# <a name="using-the-ole-db-driver-for-sql-server-header-and-library-files"></a>Verwenden des OLE DB-Treibers für SQL Server-Header- und -Bibliotheksdateien
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server-Header und Bibliotheksdateien werden installiert, wenn während des Installationsvorgangs der OLE DB-Treiber für SQL Server-SDK-Option ausgewählt ist. Es ist wichtig, beim Entwickeln von Anwendungen alle für die Entwicklung erforderlichen Dateien in die Entwicklungsumgebung zu kopieren. Weitere Informationen zum Installieren und Verteilen von OLE DB-Treiber für SQL Server finden Sie unter [Installieren von OLE DB-Treiber für SQL Server](../../oledb/applications/installing-oledb-driver-for-sql-server.md).  
  
 Der OLE DB-Treiber für SQL Server-Header und Bibliotheksdateien werden am folgenden Speicherort installiert:  
  
 *%Program*\Microsoft SQL Server\Client SDK\OLEDB\181\SDK  
  
 Der OLE DB-Treiber für SQL Server-Headerdatei (msoledbsql.h) kann verwendet werden, um OLE DB-Treiber für SQL Server-Funktionen für den Datenzugriff auf Ihre benutzerdefinierten Anwendungen hinzuzufügen. Die Headerdatei des OLE DB-Treibers für SQL Server enthält alle Definitionen, Attribute, Eigenschaften und Schnittstellen, damit Sie die neuen, in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] eingeführten Funktionen nutzen können.  
  
 Zusätzlich zu den OLE DB-Treiber für SQL Server-Headerdatei ist auch eine msoledbsql.lib Library-Datei handelt es sich die Exportbibliothek für [OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md) Funktionalität.  
  
 Die Headerdatei des OLE DB-Treibers für SQL Server ist abwärtskompatibel mit der mit Microsoft Data Access Components (MDAC) verwendeten Headerdatei „sqloledb.h“, enthält aber weder die CLSIDs für SQLOLEDB (den in MDAC enthaltenen OLE DB-Anbieter für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]) noch die Symbole für die XML-Funktionalität. Letztere wird nicht vom OLE DB-Treiber für SQL Server unterstützt.    
  
 OLE DB-Anwendungen, die der OLE DB-Treiber für SQL Server verwenden müssen sich nur auf msoledbsql.h verweisen. Wenn eine Anwendung MDAC (SQLOLEDB) und den OLE DB-Treiber für SQL Server verwendet, kann sowohl auf „sqloledb.h“ als auch auf „msoledbsql.h“ verwiesen werden, unter der Voraussetzung, dass „sqloledb.h“ zuerst angegeben wird.  
  
## <a name="using-the-ole-db-driver-for-sql-server-header-file"></a>Mithilfe des OLE DB-Treibers für SQL Server-Headerdatei  
 Um den OLE DB-Treiber für SQL Server-Headerdatei verwenden zu können, müssen Sie verwenden eine **enthalten** Anweisung in Ihrem C-/C++-Code zu programmieren. In den folgenden Abschnitten wird beschrieben, wie Sie diese OLE DB-Anwendungen.  
  
> [!NOTE]  
>  Der OLE DB-Treiber für SQL Server-Header- und-Bibliotheksdateien können nur kompilierte mithilfe von Visual Studio C++ 2012 oder höher sein.  
  
### <a name="ole-db"></a>OLE DB  
 So verwenden den OLE DB-Treiber für SQL Server-Headerdatei in einer OLE DB-Anwendung, die mit den folgenden Programmiercode:  
  
```    
include "msoledbsql.h";  
```  
  
> [!NOTE]  
>  Verfügt die Anwendung eine **enthalten** -Anweisung für sqloledb.h, die **enthalten** -Anweisung für msoledbsql.h muss nach dem sie stammen.  
  
 Wenn Sie eine Verbindung mit einer Datenquelle über OLE DB-Treiber für SQL Server zu erstellen, verwenden Sie "MSOLEDBSQL" als die Zeichenfolge des Anbieternamens aus.  

  
## <a name="component-names-and-properties-by-version"></a>Komponentennamen und Eigenschaften nach Version  

|Eigenschaft|OLE DB-Treiber für SQL Server|MDAC|  
|--------|----------------------------|----|   
|OLE DB PROGID|MSOLEDBSQL|SQLOLEDB|  
|OLE DB-Headerdateiname|msoledbsql.h|Sqloledb.h|  
|OLE DB-Anbieter-DLL|msoledbsql.dll|Sqloledb.dll| 
  
  
## <a name="static-linking-and-bcp-functions"></a>Statische Verknüpfung und BCP-Funktionen  
 Wenn eine Anwendung BCP-Funktionen verwendet, muss in der Verbindungszeichenfolge der Treiber mit derselben Version angegeben werden, die mit der für die Anwendungskompilierung verwendeten Headerdatei und Bibliothek ausgeliefert wurde.  
  
 Weitere Informationen finden Sie unter Performing [Durchführen von Massenkopiervorgängen](../../oledb/features/performing-bulk-copy-operations.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erstellen von Anwendungen mit dem OLE DB-Treiber für SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
  
  
