---
title: Verwenden von OLE DB-Treiber für SQLServer | Microsoft-Dokumentation
description: Verwendung des OLE DB-Treibers für SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server
- MSOLEDBSQL, about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], about OLE DB Driver for SQL Server
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: d4e83751fe83db3ab678547a3a1fde68b5db22df
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2018
ms.locfileid: "39107672"
---
# <a name="when-to-use-ole-db-driver-for-sql-server"></a>Verwendung des OLE DB-Treibers für SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

  OLE DB-Treiber für SQL Server ist eine Technologie, mit denen Sie Zugriff auf Daten in einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank.  Eine Besprechung der unterschiedlichen Datenzugriffstechnologien finden Sie unter [Data Access Technologies Road Map (Übersicht über Datenzugriffstechnologien)](http://go.microsoft.com/fwlink/?LinkID=179186).  
  
 Sie sollten bei der Entscheidung, ob Sie den OLE DB-Treiber für SQL Server als Datenzugriffstechnologie in einer Anwendung verwenden möchten, verschiedene Faktoren berücksichtigen.  
  
 Wenn Sie neue Anwendungen in einer verwalteten Programmiersprache wie Microsoft Visual C# oder Visual Basic schreiben und auf die neuen Funktionen, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eingeführt wurden, zugreifen müssen, sollten Sie den .NET Framework-Datenanbieter für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwenden, der Teil von .NET Framework ist.  
  
 Wenn Sie eine COM-basierte Anwendung entwickeln und auf die neuen Funktionen zugreifen müssen, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eingeführt wurden, dann sollten Sie den OLE DB-Treiber für SQL Server verwenden. Wenn Sie nicht auf die neuen Funktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugreifen müssen, können Sie weiterhin Windows Data Access Components (WDAC) verwenden.  
  
 Bei vorhandenen OLE DB-Anwendungen ist ausschlaggebend, ob Sie auf die neuen Funktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugreifen müssen. Wenn Sie eine ausgereifte Anwendung haben, die nicht auf die neuen Funktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugreifen muss, können Sie weiterhin WDAC verwenden. Falls Sie jedoch auf diese neuen Funktionen zugreifen müssen, wie etwa auf den [xml-Datentyp](../../t-sql/xml/xml-transact-sql.md), dann sollten Sie den OLE DB-Treiber für SQL Server verwenden.  
  
 Beide OLE DB-Treiber für SQL Server auch MDAC unterstützen lesen committed-Transaktionsisolation mit zeilenversionsverwaltung, aber nur OLE DB-Treiber für SQL Server unterstützt die Momentaufnahmen-Transaktionsisolation. (Programmiertechnisch ausgedrückt ist die Read Committed-Transaktionsisolation mit Zeilenversionsverwaltung gleichbedeutend mit einer Read Committed-Transaktion.)  
  
 Weitere Informationen zu den Unterschieden zwischen OLE DB-Treiber für SQL Server und MDAC finden Sie unter [Aktualisieren einer Anwendung auf OLE DB-Treiber für SQL Server über MDAC](../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [OLE DB-Treiber für SQL Server](../oledb/oledb-driver-for-sql-server.md)     
 [Vorgehensweisen für OLE DB](../oledb/ole-db-how-to/ole-db-how-to-topics.md)  
  
  
