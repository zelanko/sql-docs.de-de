---
title: Komponenten des OLE DB-Treibers für SQL Server | Microsoft-Dokumentation
description: Komponenten des OLE DB-Treibers für SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], components
- components [OLE DB Driver for SQL Server]
- MSOLEDBSQL, about OLE DB Driver for SQL Server
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 5a5124519bd95ec02e93a007d9881ec80814cfc8
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67989322"
---
# <a name="components-of-ole-db-driver-for-sql-server"></a>Komponenten des OLE DB-Treibers für SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server enthält die folgenden Komponenten:  

|Komponente|Beschreibung|  
|---------------|-----------------|  
|msoledbsql.dll|Die DLL-Datei (Dynamic Link Library), die alle Funktionen des OLE DB-Treibers für SQL Server enthält|  
|msoledbsqlr.rll|Die zugehörige Ressourcendatei für die Bibliothek des OLE DB-Treibers für SQL Server|   
|msoledbsql.h|Die Headerdatei des OLE DB-Treibers für SQL Server, die alle neuen Definitionen enthält, die für die Verwendung des OLE DB-Treibers für SQL Server erforderlich sind. Diese Headerdatei ersetzt die Headerdatei „sqloledb.h“.<br /><br /> Hinweis: Sie können im gleichen Programm auf „msoledbsql.h“ und „sqloledb.h“ verweisen, solange „sqloledb.h“ zuerst definiert wird.|  
|msoledbsql.lib|Die Bibliotheksdatei, die benötigt wird, um die Funktion [OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md) direkt aufzurufen, die Teil des OLE DB-Treibers für SQL Server ist.<br /><br /> Hinweis: Wenn Sie in Ihrem Programmcode auf die Datei „msoledbsql.lib“ verweisen, stellen Sie sicher, dass sich die Datei „msoledbsql.dll“ in Ihrem Systempfad sowie in den Systempfaden der Benutzer befindet, die mit Ihrer Anwendung arbeiten.|  

## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Anwendungen mit dem OLE DB-Treiber für SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
