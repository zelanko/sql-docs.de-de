---
title: Simulieren einer IF-WHILE EXISTS-Anweisung in einem nativ kompilierten Modul | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c0e187c1-cbd9-463c-b417-8a734574f102
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 26a6075e835e98fb31b13251ba671412b13101dc
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52514009"
---
# <a name="simulating-an-if-while-exists-statement-in-a-natively-compiled-module"></a>Simulieren einer IF-WHILE EXISTS-Anweisung in einem nativ kompilierten Modul
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Nativ kompilierte gespeicherte Prozeduren unterstützen in bedingten Anweisungen nicht die **EXISTS** -Klausel, z. B. IF und WHILE.  
  
 Das folgende Beispiel veranschaulicht eine Behelfslösung unter Verwendung einer BIT-Variablen mit einer SELECT-Anweisung zum Simulieren einer EXISTS-Klausel:  
  
```sql  
DECLARE @exists BIT = 0  
SELECT TOP 1 @exists = 1 FROM MyTable WHERE ...  
IF @exists = 1  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Migrationsprobleme bei nativ kompilierten gespeicherten Prozeduren](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)   
 [Von In-Memory OLTP nicht unterstützte Transact-SQL-Konstrukte](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
