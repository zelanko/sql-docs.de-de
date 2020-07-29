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
ms.openlocfilehash: 64a05f57c40027a4db448a987d32f77d62f0a837
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86011235"
---
# <a name="transactions"></a>Transaktionen
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server implementiert Unterstützung für lokale Transaktionen. Der Consumer kann verteilte oder koordinierte Transaktionen mit Microsoft Distributed Transaction Coordinator (MS DTC) verwenden. Für Consumer, die über mehrere Sitzungen hinweg Transaktionskontrolle erfordern, kann der OLE DB-Treiber für SQL Server von MS DTC initiierte und verwaltete Transaktionen verknüpfen.  
  
 Standardmäßig verwendet der OLE DB-Treiber für SQL Server einen Autocommit-Transaktionsmodus, bei dem jede diskrete Aktion in einer Consumersitzung eine vollständige Transaktion für eine Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] umfasst. Der Autocommitmodus des OLE DB-Treibers für SQL Server ist lokal, und Autocommittransaktionen erstrecken sich grundsätzlich nur über eine Sitzung.  
  
 Der OLE DB-Treiber für SQL Server stellt die **ITransactionLocal**-Schnittstelle zur Verfügung und ermöglicht dem Consumer, Starttransaktionen für eine Einzelverbindung zu einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] explizit und implizit zu verwenden. Der OLE DB-Treiber für SQL Server unterstützt geschachtelte lokale Transaktionen nicht.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Unterstützen lokaler Transaktionen](../../oledb/ole-db-transactions/supporting-local-transactions.md)  
  
-   [Unterstützen von verteilten Transaktionen](../../oledb/ole-db-transactions/supporting-distributed-transactions.md)  
  
-   [Isolationsstufe &#40;OLE DB&#41;](../../oledb/ole-db-transactions/isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Treiber für SQL Server-Programmierung](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
