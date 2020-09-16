---
title: Verwendung des OLE DB-Treibers
description: Informieren Sie sich über die Einsatzmöglichkeiten des OLE DB-Treibers für SQL Server und die Konzepte für allgemeinen Datenzugriff, die ihn von anderen Treibern unterscheiden.
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bd5237556ec0bbe1bf4101cb5adde9734088217c
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88860189"
---
# <a name="when-to-use-ole-db-driver-for-sql-server"></a>Verwendung des OLE DB-Treibers für SQL Server
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server ist eine Technologie, die Sie verwenden können, um auf Daten in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank zuzugreifen.  Eine Besprechung der unterschiedlichen Datenzugriffstechnologien finden Sie unter [Data Access Technologies Road Map (Übersicht über Datenzugriffstechnologien)](https://go.microsoft.com/fwlink/?LinkID=179186).  
  
 Sie sollten bei der Entscheidung, ob Sie den OLE DB-Treiber für SQL Server als Datenzugriffstechnologie in einer Anwendung verwenden möchten, verschiedene Faktoren berücksichtigen.  
  
 Wenn Sie neue Anwendungen in einer verwalteten Programmiersprache wie Microsoft Visual C# oder Visual Basic schreiben und auf die neuen Funktionen, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eingeführt wurden, zugreifen müssen, sollten Sie den .NET Framework-Datenanbieter für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwenden, der Teil von .NET Framework ist.  
  
 Wenn Sie eine COM-basierte Anwendung entwickeln und auf die neuen Funktionen zugreifen müssen, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eingeführt wurden, dann sollten Sie den OLE DB-Treiber für SQL Server verwenden. Wenn Sie nicht auf die neuen Funktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugreifen müssen, können Sie weiterhin Windows Data Access Components (WDAC) verwenden.  
  
 Bei vorhandenen OLE DB-Anwendungen ist ausschlaggebend, ob Sie auf die neuen Funktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugreifen müssen. Wenn Sie eine ausgereifte Anwendung haben, die nicht auf die neuen Funktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugreifen muss, können Sie weiterhin WDAC verwenden. Falls Sie jedoch auf diese neuen Funktionen zugreifen müssen, wie etwa auf den [xml-Datentyp](../../t-sql/xml/xml-transact-sql.md), dann sollten Sie den OLE DB-Treiber für SQL Server verwenden.  
  
 Sowohl der OLE DB-Treiber für SQL Server als auch MDAC unterstützen die Transaktionsisolation „Read Committed“ mit Zeilenversionsverwaltung, aber nur der OLE DB-Treiber für SQL Server unterstützt die Momentaufnahmen-Transaktionsisolation. (Programmiertechnisch ausgedrückt ist die Read Committed-Transaktionsisolation mit Zeilenversionsverwaltung gleichbedeutend mit einer Read Committed-Transaktion.)  
  
 Informationen zu den Unterschieden zwischen dem OLE DB-Treiber für SQL Server und MDAC finden Sie unter [Aktualisieren einer Anwendung auf den OLE DB-Treiber für SQL Server über MDAC](../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Treiber für SQL-Server](oledb-driver-for-sql-server.md)  
 [Vorgehensweisen für OLE DB](ole-db-how-to/ole-db-how-to-topics.md)  
  
  
