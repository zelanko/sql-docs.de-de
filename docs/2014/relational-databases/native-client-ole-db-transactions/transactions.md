---
title: Transaktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: 3b41e33a-c1ca-4b2a-9464-312b0ed3ca89
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dca9b7a3289390b1d1e20e1b0d18c23b44b87617
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63213891"
---
# <a name="transactions"></a>Transaktionen
  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter implementiert lokale Transaktionsunterstützung. Der Consumer kann verteilte oder koordinierte Transaktionen mit Microsoft Distributed Transaction Coordinator (MS DTC) verwenden. Für Consumer, die Transaktions Steuerung benötigen, die mehrere Sitzungen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] umfasst, kann der Native Client OLE DB-Anbieter Transaktionen beitreten, die von MS DTC initiiert und verwaltet werden.  
  
 Standardmäßig verwendet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter einen Autocommit-Transaktionsmodus, bei dem jede einzelne Aktion in einer Consumersitzung eine komplette Transaktion für eine Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]von umfasst. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Autocommitmodus des Native Client OLE DB-Anbieters ist lokal, und Autocommit-Transaktionen umfassen nie mehr als eine einzelne Sitzung.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter macht die **itransaktionlocal** -Schnittstelle verfügbar und ermöglicht dem Consumer, Transaktionen explizit und implizit auf einer einzelnen Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Instanz von zu starten. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt keine netsted local-Transaktionen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Unterstützen lokaler Transaktionen](supporting-local-transactions.md)  
  
-   [Unterstützen von verteilten Transaktionen](supporting-distributed-transactions.md)  
  
-   [Isolationsstufe &#40;OLE DB&#41;](isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
