---
title: Isolationsstufen (OLE DB) | Microsoft-Dokumentation
description: Isolationsstufen (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-transactions
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- isolation levels [OLE DB]
- transactions [OLE DB]
- OLE DB Driver for SQL Server, transactions
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 4bcb9de1cc0d09875dbe283b6ac8fe3cf46e883f
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43024776"
---
# <a name="isolation-levels-ole-db"></a>Isolationsstufen (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Clients können Transaktionsisolationsstufen für eine Verbindung steuern. Wird verwendet um Transaktionsisolationsstufen zu steuern, die OLE DB-Treiber für SQL Server-Consumer aus:  
  
-   DBPROPSET_SESSION-Eigenschaft DBPROP_SESS_AUTOCOMMITISOLEVELS für den standardmäßigen Autocommitmodus des  Native Client OLE DB-Anbieters  
  
     Der OLE DB-Treiber für SQL Server-Standard für die Stufe ist DBPROPVAL_TI_READCOMMITTED.  
  
-   Der isoLevel *-Parameter der ITransactionLocal::StartTransaction*-Methode für lokale Manualcommit-Transaktionen.  
  
-   Der isoLevel *-Parameter der ITransactionDispenser::BeginTransaction*-Methode für MS DTC-koordinierte verteilte Transaktionen.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] lässt schreibgeschützten Zugriff auf die Dirty Read-Isolationsstufe zu. Alle anderen Stufen schränken Parallelität ein, indem sie Sperren für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Objekte anwenden. Da der Client größere Parallelitätsstufen benötigt, wendet [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] größere Einschränkungen auf gleichzeitigem Zugriff auf Daten an. Um die höchste Stufe des gleichzeitigen Zugriffs auf Daten beizubehalten sollte der Consumer des  Native Client OLE DB-Anbieters seine Anforderungen für spezielle Parallelitätsstufen auf intelligente Weise steuern.  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] hat Momentaufnahmeisolationsstufe eingeführt. Weitere Informationen finden Sie unter [Arbeiten mit Momentaufnahmen](../../oledb/features/working-with-snapshot-isolation.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Transaktionen](../../oledb/ole-db-transactions/transactions.md)  
  
  
