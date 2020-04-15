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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8779b68d6ab1070514f8ef6685ef378437d09539
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302527"
---
# <a name="transactions"></a>Transaktionen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter implementiert die lokale Transaktionsunterstützung. Der Consumer kann verteilte oder koordinierte Transaktionen mit Microsoft Distributed Transaction Coordinator (MS DTC) verwenden. Für Consumer, die eine Transaktionssteuerung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] benötigen, die sich über mehrere Sitzungen erstreckt, kann der native Client-OLE-DB-Anbieter Transaktionen beitreten, die von MS DTC initiiert und verwaltet werden.  
  
 Standardmäßig verwendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der native Client-OLE-DB-Anbieter einen Autocommit-Transaktionsmodus, in dem jede diskrete [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Aktion in einer Consumersitzung eine vollständige Transaktion für eine Instanz von umfasst. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Autocommit-Modus des nativen Client-OLE-DB-Anbieters ist lokal, und Autocommit-Transaktionen umfassen nie mehr als eine einzelne Sitzung.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter macht die **ITransactionLocal-Schnittstelle** verfügbar, sodass der Consumer Transaktionen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]für eine einzelne Verbindung mit einer Instanz von explizit und implizit starten kann. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter unterstützt keine geschachtelten lokalen Transaktionen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Unterstützen lokaler Transaktionen](../../relational-databases/native-client-ole-db-transactions/supporting-local-transactions.md)  
  
-   [Unterstützen von verteilten Transaktionen](../../relational-databases/native-client-ole-db-transactions/supporting-distributed-transactions.md)  
  
-   [Isolationsstufe &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-transactions/isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
