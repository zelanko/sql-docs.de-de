---
title: Lebensdauer von Transaktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- lifetimes [SQL Server]
- Transact-SQL vs. managed code
ms.assetid: cb076fda-6488-4959-a6a4-7adaccf3f25c
caps.latest.revision: 10
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 4a007db3f753bf803e2ecf9b8d1775bd8723ac3b
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37352516"
---
# <a name="transaction-lifetimes"></a>Lebensdauer von Transaktionen
  Es gibt einen wichtigen Unterschied zwischen Transaktionen, die in gespeicherten [!INCLUDE[tsql](../../includes/tsql-md.md)] -Prozeduren gestartet werden, und Transaktionen, die in verwaltetem Code gestartet werden: CLR-Code (Common Language Runtime) kann den Transaktionsstatus bei Eintritt oder Verlassen eines CLR-Aufrufs nicht aus dem Gleichgewicht bringen. Dieser Unterschied wirkt sich wie folgt aus:  
  
-   Für eine in einem CLR-Rahmen gestartete Transaktion muss ein Commit oder ein Rollback ausgeführt werden, da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sonst beim Verlassen des Rahmens einen Fehler generiert.  
  
-   Für eine äußere Transaktion kann im CLR-Code kein Commit oder Rollback ausgeführt werden.  
  
-   Wenn für eine Transaktion, die nicht in derselben Prozedur gestartet wurde, ein Commit ausgeführt wird, wird ein Laufzeitfehler verursacht.  
  
-   Wenn für eine Transaktion, die nicht in derselben Prozedur gestartet wurde, ein Rollback ausgeführt wird, reagiert die Transaktion nicht mehr (was dazu führt, dass keine anderen Vorgänge mit Nebenwirkungen mehr ausgeführt werden). Die Transaktion reagiert nicht mehr, bis der CLR-Code den Bereich verlässt. Dies kann hilfreich sein, wenn Sie innerhalb der Prozedur einen Fehler erkennen und sicherstellen möchten, dass die ganze Transaktion beendet wird.  
  
## <a name="see-also"></a>Siehe auch  
 [CLR-Integration und -Transaktionen](../native-client-ole-db-transactions/transactions.md)  
  
  
