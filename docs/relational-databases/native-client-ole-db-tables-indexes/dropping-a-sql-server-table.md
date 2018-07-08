---
title: Löschen einer SQL Server-Tabelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- tables [OLE DB]
- deleting tables
- SQL Server Native Client OLE DB provider, tables
- removing tables
- dropping tables
ms.assetid: b6d6c4de-43c6-473e-92aa-34ffddd58cbe
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 8662d6c8b1ef1017ac00a84d717224c1ce020a22
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37430209"
---
# <a name="dropping-a-sql-server-table"></a>Löschen einer SQL Server-Tabelle
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter stellt die **dropTable** Funktion, um zu einem [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabelle aus einer Datenbank.  
  
 Geben Sie den Tabellennamen als Unicode-Zeichenfolge in die *PwszName* Mitglied der *uName* -Vereinigung der *pTableID* Parameter. Die *eKind* Mitglied *pTableID* muss DBKIND_NAME sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellen und Indizes](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
  
