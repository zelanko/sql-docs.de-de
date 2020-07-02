---
title: Transaktions Lebensdauer | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Transaktions Lebensdauer in SQL Server CLR-Integration. Transaktionen, die in gespeicherten Transact-SQL-Prozeduren gestartet werden, unterscheiden sich von den in verwaltetem
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- lifetimes [SQL Server]
- Transact-SQL vs. managed code
ms.assetid: cb076fda-6488-4959-a6a4-7adaccf3f25c
author: rothja
ms.author: jroth
ms.openlocfilehash: 8a9783922f2e1e908ee13efb97512b4c16135341
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85765391"
---
# <a name="transaction-lifetimes"></a>Lebensdauer von Transaktionen
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Es gibt einen wichtigen Unterschied zwischen Transaktionen, die in gespeicherten [!INCLUDE[tsql](../../includes/tsql-md.md)] -Prozeduren gestartet werden, und Transaktionen, die in verwaltetem Code gestartet werden: CLR-Code (Common Language Runtime) kann den Transaktionsstatus bei Eintritt oder Verlassen eines CLR-Aufrufs nicht aus dem Gleichgewicht bringen. Dieser Unterschied wirkt sich wie folgt aus:  
  
-   Für eine in einem CLR-Rahmen gestartete Transaktion muss ein Commit oder ein Rollback ausgeführt werden, da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sonst beim Verlassen des Rahmens einen Fehler generiert.  
  
-   Für eine äußere Transaktion kann im CLR-Code kein Commit oder Rollback ausgeführt werden.  
  
-   Wenn für eine Transaktion, die nicht in derselben Prozedur gestartet wurde, ein Commit ausgeführt wird, wird ein Laufzeitfehler verursacht.  
  
-   Der Versuch, einen Rollback für eine Transaktion auszuführen, der nicht in derselben Prozedur gestartet wurde, reagiert nicht mehr, da die Transaktion nicht mehr reagiert. Die Transaktion reagiert nicht mehr, bis der CLR-Code den Bereich verlässt. Dies kann hilfreich sein, wenn Sie innerhalb der Prozedur einen Fehler erkennen und sicherstellen möchten, dass die ganze Transaktion beendet wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [CLR-Integration und Transaktionen](../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
  
  
