---
title: Transaktionslebensdauer | Microsoft Docs
description: Erfahren Sie mehr über die Transaktionslebensdauer in der SQL Server CLR-Integration. In gespeicherten Transact-SQL-Prozeduren gestarteten Transaktionen unterscheiden sich von Transaktionen, die in verwaltetem Code gestartet wurden.
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
ms.openlocfilehash: 1fed737c644ebb241a5761fffd2409c2556d28ea
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487502"
---
# <a name="transaction-lifetimes"></a>Lebensdauer von Transaktionen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Es gibt einen wichtigen Unterschied zwischen Transaktionen, die in gespeicherten [!INCLUDE[tsql](../../includes/tsql-md.md)] -Prozeduren gestartet werden, und Transaktionen, die in verwaltetem Code gestartet werden: CLR-Code (Common Language Runtime) kann den Transaktionsstatus bei Eintritt oder Verlassen eines CLR-Aufrufs nicht aus dem Gleichgewicht bringen. Dieser Unterschied wirkt sich wie folgt aus:  
  
-   Für eine in einem CLR-Rahmen gestartete Transaktion muss ein Commit oder ein Rollback ausgeführt werden, da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sonst beim Verlassen des Rahmens einen Fehler generiert.  
  
-   Für eine äußere Transaktion kann im CLR-Code kein Commit oder Rollback ausgeführt werden.  
  
-   Wenn für eine Transaktion, die nicht in derselben Prozedur gestartet wurde, ein Commit ausgeführt wird, wird ein Laufzeitfehler verursacht.  
  
-   Der Versuch, eine Transaktion zurückzuschlagen, die nicht in derselben Prozedur gestartet wurde, führt dazu, dass die Transaktion nicht mehr reagiert (verhindert, dass ein anderer Nebeneffektvorgang ausgeführt wird). Die Transaktion reagiert nicht mehr, bis der CLR-Code den Bereich verlässt. Dies kann hilfreich sein, wenn Sie innerhalb der Prozedur einen Fehler erkennen und sicherstellen möchten, dass die ganze Transaktion beendet wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [CLR-Integration und Transaktionen](../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
  
  
