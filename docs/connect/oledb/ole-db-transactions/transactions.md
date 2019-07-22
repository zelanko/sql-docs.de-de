---
title: Transaktionen | Microsoft-Dokumentation
description: Transaktionen im OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- OLE DB Driver for SQL Server, transactions
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 8fc245cebdb106eb81af8c5ae1fba6a2bcc041b3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015228"
---
# <a name="transactions"></a>Transaktionen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server implementiert lokale Transaktionsunterstützung. Der Consumer kann verteilte oder koordinierte Transaktionen mit Microsoft Distributed Transaction Coordinator (MS DTC) verwenden. Für Consumer, die über mehrere Sitzungen hinweg Transaktionskontrolle erfordern, kann der OLE DB-Treiber für SQL Server von MS DTC initiierte und verwaltete Transaktionen verknüpfen.  
  
 Standardmäßig verwendet der OLE DB-Treiber für SQL Server einen Autocommit-Transaktionsmodus, bei dem jede diskrete Aktion in einer Consumersitzung eine vollständige Transaktion für eine Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] umfasst. Der Autocommitmodus des OLE DB-Treibers für SQL Server ist lokal, und Autocommittransaktionen erstrecken sich grundsätzlich nur über eine Sitzung.  
  
 Der OLE DB-Treiber für SQL Server stellt die **ITransactionLocal**-Schnittstelle zur Verfügung und ermöglicht dem Consumer, Starttransaktionen für eine Einzelverbindung zu einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] explizit und implizit zu verwenden. Der OLE DB-Treiber für SQL Server unterstützt keine unterstützten lokalen Transaktionen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Unterstützen lokaler Transaktionen](../../oledb/ole-db-transactions/supporting-local-transactions.md)  
  
-   [Unterstützen von verteilten Transaktionen](../../oledb/ole-db-transactions/supporting-distributed-transactions.md)  
  
-   [OLE DB Isolations Stufen &#40;&#41;](../../oledb/ole-db-transactions/isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Treiber für SQL Server-Programmierung](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
