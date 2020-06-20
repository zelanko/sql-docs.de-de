---
title: Isolationsstufen (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- isolation levels [OLE DB]
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: d70ee72c-6e2a-4bcd-9456-4a697a866361
author: rothja
ms.author: jroth
ms.openlocfilehash: c7f6cbff4e68eaedd3e78a82cddd872ba5f8f19e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85017819"
---
# <a name="isolation-levels-ole-db"></a>Isolationsstufen (OLE DB)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Clients können Transaktionsisolationsstufen für eine Verbindung steuern. Zum Steuern der Transaktions Isolationsstufe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet der Consumer des Native Client OLE DB Anbieters Folgendes:  
  
-   DBPROPSET_SESSION Eigenschaften DBPROP_SESS_AUTOCOMMITISOLEVELS für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] standardmäßigen Autocommitmodus des Native Client OLE DB Anbieters.  
  
     Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standardwert für den Native Client OLE DB-Anbieter für die Ebene ist DBPROPVAL_TI_READCOMMITTED.  
  
-   Der *isoLevel*-Parameter der **ITransactionLocal::StartTransaction**-Methode für lokale Manualcommit-Transaktionen.  
  
-   Der *isoLevel*-Parameter der **ITransactionDispenser::BeginTransaction**-Methode für MS DTC-koordinierte verteilte Transaktionen.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lässt schreibgeschützten Zugriff auf die Dirty Read-Isolationsstufe zu. Alle anderen Stufen schränken Parallelität ein, indem sie Sperren für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Objekte anwenden. Da der Client größere Parallelitätsstufen benötigt, wendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] größere Einschränkungen auf gleichzeitigem Zugriff auf Daten an. Um die höchste Ebene des gleichzeitigen Zugriffs auf Daten aufrechtzuerhalten, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sollte der Consumer des Native Client OLE DB Anbieters seine Anforderungen für bestimmte Parallelitäts Ebenen intelligent steuern.  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] hat Momentaufnahmeisolationsstufe eingeführt. Weitere Informationen finden Sie unter [Arbeiten mit der Momentaufnahmeisolation](../native-client/features/working-with-snapshot-isolation.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Transaktionen](transactions.md)  
  
  
