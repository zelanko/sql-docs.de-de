---
title: Implementieren von IDENTITY in einer speicheroptimierten Tabelle | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über IDENTITY in speicheroptimierten Tabellen in SQL Server. Speicheroptimierte Tabellen unterstützen IDENTITY für einen Seed und inkrementieren den Wert um eins.
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c0a704a3-3a31-4c2c-b967-addacda62ef8
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5aecab53a9144d5254eb85190f7652dbe090bf82
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91869127"
---
# <a name="implementing-identity-in-a-memory-optimized-table"></a>Implementieren von IDENTITY in einer speicheroptimierten Tabelle
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

IDENTITY wird in einer speicheroptimierten Tabelle unterstützt, vorausgesetzt, Ausgangswert und Inkrement sind jeweils auf 1 festgelegt (Standardeinstellung). Identitätsspalten mit der Definition IDENTITY(x, y), wobei x != 1 oder y != 1 ist, werden in speicheroptimierten Tabellen nicht unterstützt.   
    
Um den Ausgangswert für IDENTITY zu erhöhen, fügen Sie eine neue Zeile mit einem expliziten Wert für die Identitätsspalte ein und verwenden die Sitzungsoption `SET IDENTITY_INSERT table_name ON`. Nach dem Einfügen der Zeile wird der IDENTITY-Ausgangswert auf den explizit eingefügten Wert plus 1 geändert. Um den Ausgangswert auf 1000 zu erhöhen, fügen Sie eine Zeile mit dem Wert 999 in der Identitätsspalte ein. Die generierten Identitätswerte beginnen dann bei 1000.     
  
## <a name="see-also"></a>Weitere Informationen  
 [Migrieren zu In-Memory OLTP](./plan-your-adoption-of-in-memory-oltp-features-in-sql-server.md)  
  
