---
title: Isolations Stufen (OLE DB) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4ddfe4bd9d8760fa561e7b0221f61413b3c6d111
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73761614"
---
# <a name="isolation-levels-ole-db"></a>Isolationsstufen (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Clients können Transaktionsisolationsstufen für eine Verbindung steuern. Zum Steuern der Transaktions Isolationsstufe verwendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der Consumer des Native Client OLE DB Anbieters Folgendes:  
  
-   DBPROPSET_SESSION Eigenschaften DBPROP_SESS_AUTOCOMMITISOLEVELS für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] standardmäßigen Autocommitmodus des Native Client OLE DB Anbieters.  
  
     Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standardwert für den Native Client OLE DB-Anbieter für die Ebene ist DBPROPVAL_TI_READCOMMITTED.  
  
-   Der *isoLevel*-Parameter der **ITransactionLocal::StartTransaction**-Methode für lokale Manualcommit-Transaktionen.  
  
-   Der *isoLevel*-Parameter der **ITransactionDispenser::BeginTransaction**-Methode für MS DTC-koordinierte verteilte Transaktionen.  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lässt schreibgeschützten Zugriff auf die Dirty Read-Isolationsstufe zu. Alle anderen Stufen schränken Parallelität ein, indem sie Sperren für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Objekte anwenden. Da der Client größere Parallelitätsstufen benötigt, wendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] größere Einschränkungen auf gleichzeitigem Zugriff auf Daten an. Um die höchste Ebene des gleichzeitigen Zugriffs auf Daten aufrechtzuerhalten, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sollte der Consumer des Native Client OLE DB Anbieters seine Anforderungen für bestimmte Parallelitäts Ebenen intelligent steuern.  
  
> [!NOTE]  
>  
  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] hat Momentaufnahmeisolationsstufe eingeführt. Weitere Informationen finden Sie unter [Arbeiten mit der Momentaufnahmeisolation](../../relational-databases/native-client/features/working-with-snapshot-isolation.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Transaktionen](../../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
  
