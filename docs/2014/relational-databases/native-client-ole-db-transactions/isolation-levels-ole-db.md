---
title: Isolationsstufen (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- isolation levels [OLE DB]
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: d70ee72c-6e2a-4bcd-9456-4a697a866361
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f6a83ec8d81a3c9e07c36c3973735c3a62746bd1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160897"
---
# <a name="isolation-levels-ole-db"></a>Isolationsstufen (OLE DB)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Clients können Transaktionsisolationsstufen für eine Verbindung steuern. Isolationsstufe der Transaktion, steuern die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter Consumer verwendet:  
  
-   DBPROPSET_SESSION-Eigenschaft DBPROP_SESS_AUTOCOMMITISOLEVELS für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter standardmäßigen Autocommitmodus.  
  
     Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter-Standardeinstellung für die Stufe ist DBPROPVAL_TI_READCOMMITTED.  
  
-   Die *IsoLevel* Parameter von der **ITransactionLocal:: StartTransaction** Methode für lokale Manualcommit-Transaktionen.  
  
-   Die *IsoLevel* Parameter von der **ITransactionDispenser:: BeginTransaction** Methode für die MS DTC koordinierte verteilte Transaktionen.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lässt schreibgeschützten Zugriff auf die Dirty Read-Isolationsstufe zu. Alle anderen Stufen schränken Parallelität ein, indem sie Sperren für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Objekte anwenden. Da der Client größere Parallelitätsstufen benötigt, wendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] größere Einschränkungen auf gleichzeitigem Zugriff auf Daten an. Verwalten Sie das höchste Maß an gleichzeitigen Zugriff auf Daten, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Consumer der Native Client OLE DB-Anbieter muss seine Anforderungen für spezielle Parallelitätsstufen auf intelligente Weise steuern.  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] hat Momentaufnahmeisolationsstufe eingeführt. Weitere Informationen finden Sie unter [arbeiten mit Snapshot-Isolation](../native-client/features/working-with-snapshot-isolation.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Transaktionen](transactions.md)  
  
  