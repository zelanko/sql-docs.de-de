---
title: Transaktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: 3b41e33a-c1ca-4b2a-9464-312b0ed3ca89
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0bf9bf1d02c09007bfeed695ec7f01ca34ef1e9b
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37411529"
---
# <a name="transactions"></a>Transaktionen
  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter implementiert die lokale transaktionsunterstützung. Der Consumer kann verteilte oder koordinierte Transaktionen mit Microsoft Distributed Transaction Coordinator (MS DTC) verwenden. Für Verbraucher, die transaktionssteuerung, die mehreren Sitzungen, umfasst die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter kann initiierte und verwaltete von MS DTC Transaktionen verknüpfen.  
  
 In der Standardeinstellung die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter verwendet einen Autocommit-Transaktionsmodus, in dem jede diskrete Aktion in einer consumersitzung eine vollständige Transaktion für eine Instanz von umfasst [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Autocommit-Modus von Native Client OLE DB-Anbieters ist lokal, und Autocommit-Transaktionen erstrecken sich nie über mehr als eine einzelne Sitzung.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter stellt die **ITransactionLocal** -Schnittstelle, sodass des Consumers explizit und implizit starttransaktionen für eine einzelverbindung zu einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt keine geschachtelte lokale Transaktionen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Unterstützen lokaler Transaktionen](supporting-local-transactions.md)  
  
-   [Unterstützen von verteilten Transaktionen](supporting-distributed-transactions.md)  
  
-   [Isolationsstufen &#40;OLE-DB&#41;](isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
