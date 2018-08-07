---
title: Implementieren von IDENTITY in einer speicheroptimierten Tabelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: in-memory-oltp
ms.reviewer: ''
ms.suite: sql
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c0a704a3-3a31-4c2c-b967-addacda62ef8
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: a62b2ffa660aa6741e3189b1c1577bbb913f5f29
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2018
ms.locfileid: "39558720"
---
# <a name="implementing-identity-in-a-memory-optimized-table"></a>Implementieren von IDENTITY in einer speicheroptimierten Tabelle
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

IDENTITY wird in einer speicheroptimierten Tabelle unterstützt, vorausgesetzt, Ausgangswert und Inkrement sind jeweils auf 1 festgelegt (Standardeinstellung). Identitätsspalten mit der Definition IDENTITY(x, y), wobei x != 1 oder y != 1 ist, werden in speicheroptimierten Tabellen nicht unterstützt.   
    
Um den Ausgangswert für IDENTITY zu erhöhen, fügen Sie eine neue Zeile mit einem expliziten Wert für die Identitätsspalte ein und verwenden die Sitzungsoption `SET IDENTITY_INSERT table_name ON`. Nach dem Einfügen der Zeile wird der IDENTITY-Ausgangswert auf den explizit eingefügten Wert plus 1 geändert. Um den Ausgangswert auf 1000 zu erhöhen, fügen Sie eine Zeile mit dem Wert 999 in der Identitätsspalte ein. Die generierten Identitätswerte beginnen dann bei 1000.     
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Migrieren zu In-Memory OLTP](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  
  
