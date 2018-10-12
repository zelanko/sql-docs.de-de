---
title: Isolationsstufen (OLE DB) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: c5f6d9f56b4485c2aa5aa8383a425bedb85a38a8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47674918"
---
# <a name="isolation-levels-ole-db"></a>Isolationsstufen (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Clients können Transaktionsisolationsstufen für eine Verbindung steuern. Wird verwendet um Transaktionsisolationsstufen zu steuern, die OLE DB-Treiber für SQL Server-Consumer aus:  
  
-   DBPROPSET_SESSION-Eigenschaft DBPROP_SESS_AUTOCOMMITISOLEVELS für den standardmäßigen Autocommitmodus des OLE DB Driver for SQL Server.  
  
     Der OLE DB-Treiber für SQL Server-Standard für die Stufe ist DBPROPVAL_TI_READCOMMITTED.  
  
-   Der *isoLevel*-Parameter der **ITransactionLocal::StartTransaction**-Methode für lokale Manualcommit-Transaktionen.  
  
-   Der *isoLevel*-Parameter der **ITransactionDispenser::BeginTransaction**-Methode für MS DTC-koordinierte verteilte Transaktionen.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] lässt schreibgeschützten Zugriff auf die Dirty Read-Isolationsstufe zu. Alle anderen Stufen schränken Parallelität ein, indem sie Sperren für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Objekte anwenden. Da der Client größere Parallelitätsstufen benötigt, wendet [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] größere Einschränkungen auf gleichzeitigem Zugriff auf Daten an. Um die höchste Stufe des gleichzeitigen Zugriffs auf Daten beizubehalten sollte der Consumer des OLE DB Driver for SQL Server seine Anforderungen für spezielle Parallelitätsstufen auf intelligente Weise steuern.  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] hat Momentaufnahmeisolationsstufe eingeführt. Weitere Informationen finden Sie unter [Arbeiten mit der Momentaufnahmeisolation](../../oledb/features/working-with-snapshot-isolation.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Transaktionen](../../oledb/ole-db-transactions/transactions.md)  
  
  
