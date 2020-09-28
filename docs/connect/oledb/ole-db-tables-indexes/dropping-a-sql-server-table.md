---
title: Löschen einer SQL Server-Tabelle (OLE DB-Treiber) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine SQL Server-Tabelle aus einer Datenbank entfernen, indem Sie die ITableDefinition::DropTable-Funktion im OLE DB-Treiber für SQL Server verwenden.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- tables [OLE DB]
- deleting tables
- OLE DB Driver for SQL Server, tables
- removing tables
- dropping tables
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c3bdcc2b2b96c2cd1d9af0bbf7d31457eed71381
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88859401"
---
# <a name="dropping-a-sql-server-table"></a>Löschen einer SQL Server-Tabelle
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server macht die **ITableDefinition::DropTable**-Funktion verfügbar, mit der sich [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Tabellen aus Datenbanken entfernen lassen.  
  
 Geben Sie den Tabellennamen als Unicode-Zeichenfolge in das *pwszName* -Element der *uName*-Vereinigung des *pTableID*-Parameters ein. Das *eKind*-Element von *pTableID* muss DBKIND_NAME sein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellen und Indizes](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)  
  
  
