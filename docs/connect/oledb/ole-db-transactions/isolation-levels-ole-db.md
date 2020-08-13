---
title: Isolationsstufen (OLE DB-Treiber) | Microsoft-Dokumentation
description: Isolationsstufen (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- isolation levels [OLE DB]
- transactions [OLE DB]
- OLE DB Driver for SQL Server, transactions
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 60fce8b96ff116f1c1e92a75e1335a33207d36d3
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87244101"
---
# <a name="isolation-levels-ole-db"></a>Isolationsstufen (OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Clients können Transaktionsisolationsstufen für eine Verbindung steuern. Zum Steuern der Transaktionsisolationsstufe verwendet der Consumer des OLE DB-Treibers für SQL Server Folgendes:  
  
-   DBPROPSET_SESSION-Eigenschaft DBPROP_SESS_AUTOCOMMITISOLEVELS für den standardmäßigen Autocommitmodus des OLE DB Driver for SQL Server.  
  
     Der Standardwert des OLE DB-Treibers für SQL Server für die Stufe ist „DBPROPVAL_TI_READCOMMITTED“.  
  
-   Der *isoLevel*-Parameter der **ITransactionLocal::StartTransaction**-Methode für lokale Manualcommit-Transaktionen.  
  
-   Der *isoLevel*-Parameter der **ITransactionDispenser::BeginTransaction**-Methode für MS DTC-koordinierte verteilte Transaktionen.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] lässt schreibgeschützten Zugriff auf die Dirty Read-Isolationsstufe zu. Alle anderen Stufen schränken Parallelität ein, indem sie Sperren für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Objekte anwenden. Da der Client größere Parallelitätsstufen benötigt, wendet [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] größere Einschränkungen auf gleichzeitigem Zugriff auf Daten an. Um die höchste Stufe des gleichzeitigen Zugriffs auf Daten beizubehalten sollte der Consumer des OLE DB Driver for SQL Server seine Anforderungen für spezielle Parallelitätsstufen auf intelligente Weise steuern.  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] hat Momentaufnahmeisolationsstufe eingeführt. Weitere Informationen finden Sie unter [Arbeiten mit der Momentaufnahmeisolation](../../oledb/features/working-with-snapshot-isolation.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Transaktionen](../../oledb/ole-db-transactions/transactions.md)  
  
  
