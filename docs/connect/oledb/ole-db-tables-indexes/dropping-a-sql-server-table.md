---
title: Löschen einer SQL Server-Tabelle | Microsoft Docs
description: Löschen einer SQL Server-Tabelle, die mithilfe von OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-tables-indexes
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- tables [OLE DB]
- deleting tables
- OLE DB Driver for SQL Server, tables
- removing tables
- dropping tables
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 9b4c86501d6265a5a756d0d88ca6305cd96ee9d9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="dropping-a-sql-server-table"></a>Löschen einer SQL Server-Tabelle
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der OLE DB-Treiber für SQL Server macht die **dropTable** Function zum Entfernen einer [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Tabelle aus einer Datenbank.  
  
 Geben Sie den Tabellennamen als Unicode-Zeichenfolge in der *PwszName* Mitglied der *uName* -Vereinigung der *pTableID* Parameter. Die *eKind* Mitglied *pTableID* muss DBKIND_NAME sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellen und Indizes](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)  
  
  
