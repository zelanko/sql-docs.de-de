---
title: Verwendung des OLE DB-Treibers für SQL Server | Microsoft-Dokumentation
description: Verwendung des OLE DB-Treibers für SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server
- MSOLEDBSQL, about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], about OLE DB Driver for SQL Server
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 74bd79c24b913cd3c3d2f782b77cf2bb4c23e397
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015187"
---
# <a name="when-to-use-ole-db-driver-for-sql-server"></a>Verwendung des OLE DB-Treibers für SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

  OLE DB Treiber für SQL Server ist eine Technologie, die Sie verwenden können, um auf Daten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in einer Datenbank zuzugreifen.  Eine Besprechung der unterschiedlichen Datenzugriffstechnologien finden Sie unter [Data Access Technologies Road Map (Übersicht über Datenzugriffstechnologien)](https://go.microsoft.com/fwlink/?LinkID=179186).  
  
 Sie sollten bei der Entscheidung, ob Sie den OLE DB-Treiber für SQL Server als Datenzugriffstechnologie in einer Anwendung verwenden möchten, verschiedene Faktoren berücksichtigen.  
  
 Wenn Sie neue Anwendungen in einer verwalteten Programmiersprache wie Microsoft Visual C# oder Visual Basic schreiben und auf die neuen Funktionen, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eingeführt wurden, zugreifen müssen, sollten Sie den .NET Framework-Datenanbieter für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwenden, der Teil von .NET Framework ist.  
  
 Wenn Sie eine COM-basierte Anwendung entwickeln und auf die neuen Funktionen zugreifen müssen, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eingeführt wurden, dann sollten Sie den OLE DB-Treiber für SQL Server verwenden. Wenn Sie nicht auf die neuen Funktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugreifen müssen, können Sie weiterhin Windows Data Access Components (WDAC) verwenden.  
  
 Bei vorhandenen OLE DB-Anwendungen ist ausschlaggebend, ob Sie auf die neuen Funktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugreifen müssen. Wenn Sie eine ausgereifte Anwendung haben, die nicht auf die neuen Funktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugreifen muss, können Sie weiterhin WDAC verwenden. Falls Sie jedoch auf diese neuen Funktionen zugreifen müssen, wie etwa auf den [xml-Datentyp](../../t-sql/xml/xml-transact-sql.md), dann sollten Sie den OLE DB-Treiber für SQL Server verwenden.  
  
 Sowohl OLE DB Treiber für SQL Server als auch MDAC unterstützen die Transaktions Isolation mit Leseberechtigung mithilfe der Zeilen Versionsverwaltung, aber nur OLE DB Treiber für SQL Server unterstützt die Momentaufnahme Transaktions Isolation. (Programmiertechnisch ausgedrückt ist die Read Committed-Transaktionsisolation mit Zeilenversionsverwaltung gleichbedeutend mit einer Read Committed-Transaktion.)  
  
 Informationen zu den Unterschieden zwischen OLE DB Treiber für SQL Server und MDAC finden [Sie unter Aktualisieren einer Anwendung auf OLE DB Treiber für SQL Server von MDAC](../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Treiber für SQL Server](../oledb/oledb-driver-for-sql-server.md)     
 [Vorgehensweisen für OLE DB](../oledb/ole-db-how-to/ole-db-how-to-topics.md)  
  
  
