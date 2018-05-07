---
title: Erstellen eines Rowsets mit IOpenRowset | Microsoft Docs
description: Erstellen eines Rowsets mit IOpenRowset-Schnittstelle des OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IOpenRowset interface
- rowsets [OLE DB], creating
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets, creating
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: d518a5e7f2b4f5823317f20bd1669d8bd3adeeb7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="creating-a-rowset-with-iopenrowset"></a>Erstellen eines Rowsets mit 'IopenRowset'
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der OLE DB-Treiber für SQL Server unterstützt die **IOpenRowset:: OPENROWSET** Methode mit den folgenden Einschränkungen:  
  
-   Eine Basistabelle oder Sicht muss angegeben werden in einer Datenbank-ID (DBID) Struktur, die die *pTableID* -Parameter zeigt.  
  
-   Die DBID *eKind* Element muss dbkind_name.  
  
-   Die DBID *uName* Member muss den Namen einer vorhandenen Basistabelle oder einer Sicht als Unicode-Zeichenfolge angeben.  
  
-   Die *pIndexID* Parameter **OpenRowset** muss NULL sein.  
  
 Das Resultset von **IOpenRowset:: OPENROWSET** enthält ein einzelnes Rowset. Resultsets, die ein einzelnes Rowset enthalten können unterstützt werden, indem [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Cursor. Die Cursorunterstützung ermöglicht dem Entwickler die Verwendung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Parallelitätsmechanismen.  
  
## <a name="see-also"></a>Siehe auch  
 [Rowsets](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
