---
title: Komponenten des OLE DB-Treibers für SQL Server
description: Komponenten des OLE DB-Treibers für SQL Server
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
- data access [OLE DB Driver for SQL Server], components
- components [OLE DB Driver for SQL Server]
- MSOLEDBSQL, about OLE DB Driver for SQL Server
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: b1b46e57b3be42fa93f8a246db528a5f85709d9e
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2018
ms.locfileid: "39109832"
---
# <a name="components-of-ole-db-driver-for-sql-server"></a>Komponenten des OLE DB-Treibers für SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB-Treiber für SQL Server enthält die folgenden Komponenten:  

|Komponente|und Beschreibung|  
|---------------|-----------------|  
|msoledbsql.dll|Die Dynamic Link Library (DLL)-Datei, die alle von der OLE DB-Treiber für SQL Server-Funktionen enthält.|  
|msoledbsqlr.rll|Die begleitende Ressourcendatei für die OLE DB-Treiber für SQL Server-Bibliothek.|   
|msoledbsql.h|Der OLE DB-Treiber für SQL Server-Headerdatei, die alle erforderlichen neuen Definitionen enthält erforderlich, um die OLE DB-Treiber für SQL Server verwenden. Diese Headerdatei ersetzt die sqloledb.h-Header-Datei.<br /><br /> Hinweis: Sie können msoledbsql.h und sqloledb.h im selben Programm verweisen, solange sqloledb.h zuerst definiert wird.|  
|msoledbsql.lib|Die Bibliotheksdatei benötigt für den direkten Aufruf der [OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md) -Funktion, die Teil der OLE DB-Treiber für SQL Server ist.<br /><br /> Hinweis: Wenn Sie in Ihrem Programmcode auf die Datei „msoledbsql.lib“ verweisen, stellen Sie sicher, dass diese sich in Ihrem Systempfad sowie in den Systempfaden der Benutzer befindet, die mit Ihrer Anwendung arbeiten.|  

## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erstellen von Anwendungen mit dem OLE DB-Treiber für SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
