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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a18986af71f652a833f413ee1fa62ca2fd44ba06
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48188630"
---
# <a name="isolation-levels-ole-db"></a>Isolationsstufen (OLE DB)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Clients können Transaktionsisolationsstufen für eine Verbindung steuern. Transaktions-Isolierungsstufe, steuern die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter, Consumer verwendet:  
  
-   DBPROPSET_SESSION-Eigenschaft DBPROP_SESS_AUTOCOMMITISOLEVELS für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter standardmäßigen Autocommitmodus.  
  
     Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter-Standard für die Stufe ist DBPROPVAL_TI_READCOMMITTED.  
  
-   Die *IsoLevel* Parameter, der die **ITransactionLocal:: StartTransaction** -Methode für lokale Manualcommit-Transaktionen.  
  
-   Die *IsoLevel* Parameter, der die **ITransactionDispenser:: BeginTransaction** Methode für die MS DTC koordinierte verteilte Transaktionen.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lässt schreibgeschützten Zugriff auf die Dirty Read-Isolationsstufe zu. Alle anderen Stufen schränken Parallelität ein, indem sie Sperren für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Objekte anwenden. Da der Client größere Parallelitätsstufen benötigt, wendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] größere Einschränkungen auf gleichzeitigem Zugriff auf Daten an. Verwalten Sie die höchste Ebene des gleichzeitigen Zugriffs auf Daten, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter Consumer sollte seine Anforderungen für spezielle Parallelitätsstufen auf intelligente Weise steuern.  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] hat Momentaufnahmeisolationsstufe eingeführt. Weitere Informationen finden Sie unter [arbeiten mit Momentaufnahmeisolation](../native-client/features/working-with-snapshot-isolation.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Transaktionen](transactions.md)  
  
  
