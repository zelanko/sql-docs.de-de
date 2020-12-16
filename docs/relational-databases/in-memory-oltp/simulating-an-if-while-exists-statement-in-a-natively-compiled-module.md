---
title: Simulieren einer IF-WHILE EXISTS-Anweisung in einem nativ kompilierten Modul
description: Hier erfahren Sie, wie Sie die EXISTS-Klausel in Bedingungsanweisungen simulieren, die nicht von nativ kompilierten gespeicherten Prozeduren in SQL Server unterstützt werden.
ms.custom: seo-dt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c0e187c1-cbd9-463c-b417-8a734574f102
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0438806d15caf806c4598f3d2b3882011d77d0f5
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97485202"
---
# <a name="simulating-an-if-while-exists-statement-in-a-natively-compiled-module"></a>Simulieren einer IF-WHILE EXISTS-Anweisung in einem nativ kompilierten Modul
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Nativ kompilierte gespeicherte Prozeduren unterstützen in bedingten Anweisungen nicht die **EXISTS** -Klausel, z. B. IF und WHILE.  
  
 Das folgende Beispiel veranschaulicht eine Behelfslösung unter Verwendung einer BIT-Variablen mit einer SELECT-Anweisung zum Simulieren einer EXISTS-Klausel:  
  
```sql  
DECLARE @exists BIT = 0  
SELECT TOP 1 @exists = 1 FROM MyTable WHERE ...  
IF @exists = 1  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Migrationsprobleme bei systemintern kompilierten gespeicherten Prozeduren](./a-guide-to-query-processing-for-memory-optimized-tables.md)   
 [Von In-Memory OLTP nicht unterstützte Transact-SQL-Konstrukte.](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
