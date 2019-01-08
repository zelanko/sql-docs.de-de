---
title: Simulieren einer EXISTS-Klausel in einer systemintern kompilierten gespeicherten Prozedur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c0e187c1-cbd9-463c-b417-8a734574f102
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6827f14702063765ccf64c8b70ba5088a8509ff1
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52510083"
---
# <a name="simulating-an-exists-clause-in-a-natively-compiled-stored-procedure"></a>Simulieren einer EXISTS-Klausel in einer systemintern kompilierten gespeicherten Prozedur
  Die `EXISTS`-Klausel wird von systemintern kompilierten gespeicherten Prozeduren nicht unterstützt, es gibt jedoch eine Problemumgehung:  
  
```tsql  
DECLARE @exists BIT = 0  
SELECT TOP 1 @exists = 1 FROM MyTable WHERE ...  
IF @exists = 1  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Migrationsprobleme bei nativ kompilierten gespeicherten Prozeduren](migration-issues-for-natively-compiled-stored-procedures.md)   
 [Von In-Memory OLTP nicht unterstützte Transact-SQL-Konstrukte](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
