---
title: Transaktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d54dbe8e3df6e930ebd026e638d0a21f2f88f32e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73772556"
---
# <a name="transactions"></a>Transaktionen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter implementiert lokale Transaktionsunterstützung. Der Consumer kann verteilte oder koordinierte Transaktionen mit Microsoft Distributed Transaction Coordinator (MS DTC) verwenden. Für Consumer, die Transaktions Steuerung benötigen, die mehrere Sitzungen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] umfasst, kann der Native Client OLE DB-Anbieter Transaktionen beitreten, die von MS DTC initiiert und verwaltet werden.  
  
 Standardmäßig verwendet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter einen Autocommit-Transaktionsmodus, bei dem jede einzelne Aktion in einer Consumersitzung eine komplette Transaktion für eine Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]von umfasst. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Autocommitmodus des Native Client OLE DB-Anbieters ist lokal, und Autocommit-Transaktionen umfassen nie mehr als eine einzelne Sitzung.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter macht die **itransaktionlocal** -Schnittstelle verfügbar und ermöglicht dem Consumer, Transaktionen explizit und implizit auf einer einzelnen Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Instanz von zu starten. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt keine netsted local-Transaktionen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Unterstützen lokaler Transaktionen](../../relational-databases/native-client-ole-db-transactions/supporting-local-transactions.md)  
  
-   [Unterstützen von verteilten Transaktionen](../../relational-databases/native-client-ole-db-transactions/supporting-distributed-transactions.md)  
  
-   [Isolations Stufen &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-transactions/isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
