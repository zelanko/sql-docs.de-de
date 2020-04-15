---
title: Isolationsstufen (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- isolation levels [OLE DB]
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: d70ee72c-6e2a-4bcd-9456-4a697a866361
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c3535360e120e0f9c61a8cfb7cb578e531e92572
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280266"
---
# <a name="isolation-levels-ole-db"></a>Isolationsstufen (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Clients können Transaktionsisolationsstufen für eine Verbindung steuern. Um die Transaktionsisolationsstufe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu steuern, verwendet der Consumer des nativen Client-OLE-DB-Anbieters:  
  
-   DBPROPSET_SESSION Eigenschaft DBPROP_SESS_AUTOCOMMITISOLEVELS [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für den standardmäßigen Autocommit-Modus des nativen Client-OLE-DB-Anbieters.  
  
     Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standardwert des nativen Client-OLE-DB-Anbieters für die Ebene ist DBPROPVAL_TI_READCOMMITTED.  
  
-   Der *isoLevel*-Parameter der **ITransactionLocal::StartTransaction**-Methode für lokale Manualcommit-Transaktionen.  
  
-   Der *isoLevel*-Parameter der **ITransactionDispenser::BeginTransaction**-Methode für MS DTC-koordinierte verteilte Transaktionen.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lässt schreibgeschützten Zugriff auf die Dirty Read-Isolationsstufe zu. Alle anderen Stufen schränken Parallelität ein, indem sie Sperren für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Objekte anwenden. Da der Client größere Parallelitätsstufen benötigt, wendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] größere Einschränkungen auf gleichzeitigem Zugriff auf Daten an. Um den gleichzeitig höchsten Zugriff auf Daten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aufrechtzuerhalten, sollte der Consumer des nativen Client-OLE-DB-Anbieters seine Anforderungen für bestimmte Parallelitätsebenen intelligent steuern.  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] hat Momentaufnahmeisolationsstufe eingeführt. Weitere Informationen finden Sie unter [Arbeiten mit der Momentaufnahmeisolation](../../relational-databases/native-client/features/working-with-snapshot-isolation.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Transaktionen](../../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
  
