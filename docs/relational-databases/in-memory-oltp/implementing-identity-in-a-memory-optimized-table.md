---
title: Implementieren von IDENTITY in einer speicheroptimierten Tabelle | Microsoft-Dokumentation
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
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 670cbaf1532c5d958c746ec8645a02815a7e5c01
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63047662"
---
# <a name="implementing-identity-in-a-memory-optimized-table"></a>Implementieren von IDENTITY in einer speicheroptimierten Tabelle
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

IDENTITY wird in einer speicheroptimierten Tabelle unterstützt, vorausgesetzt, Ausgangswert und Inkrement sind jeweils auf 1 festgelegt (Standardeinstellung). Identitätsspalten mit der Definition IDENTITY(x, y), wobei x != 1 oder y != 1 ist, werden in speicheroptimierten Tabellen nicht unterstützt.   
    
Um den Ausgangswert für IDENTITY zu erhöhen, fügen Sie eine neue Zeile mit einem expliziten Wert für die Identitätsspalte ein und verwenden die Sitzungsoption `SET IDENTITY_INSERT table_name ON`. Nach dem Einfügen der Zeile wird der IDENTITY-Ausgangswert auf den explizit eingefügten Wert plus 1 geändert. Um den Ausgangswert auf 1000 zu erhöhen, fügen Sie eine Zeile mit dem Wert 999 in der Identitätsspalte ein. Die generierten Identitätswerte beginnen dann bei 1000.     
  
## <a name="see-also"></a>Weitere Informationen  
 [Migrieren zu In-Memory OLTP](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  
  
