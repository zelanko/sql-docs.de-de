---
title: Erstellen von Rowsets mit IOpenRowset (OLE DB-Treiber) | Microsoft-Dokumentation
description: Erstellen eines Rowsets mit der IOpenRowset-Schnittstelle des OLE DB-Treibers für SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- IOpenRowset interface
- rowsets [OLE DB], creating
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets, creating
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 721a54d4e423675fa5dad39d22e8f94c178228d6
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86942383"
---
# <a name="creating-a-rowset-with-iopenrowset"></a>Erstellen eines Rowsets mit 'IopenRowset'
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server unterstützt die Methode **IOpenRowset::OpenRowset** mit den folgenden Einschränkungen:  
  
-   Eine Basistabelle oder -sicht muss in einer Datenbank-ID-Struktur angegeben sein, auf die der *pTableID*-Parameter zeigt.  
  
-   Das DBID-Element *eKind* muss DBKIND_NAME anzeigen.  
  
-   Das DBI-Element *uName* muss den Namen einer vorhandenen Basistabelle oder einer Ansicht als Unicode-Zeichenfolge angeben.  
  
-   Der *pIndexID*-Parameter von **OpenRowset** muss NULL sein.  
  
 Das Resultset von **IOpenRowset::OpenRowset** enthält ein einzelnes Rowset. Resultsets, die ein einzelnes Rowset enthalten, können von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Cursorn unterstützt werden. Die Cursorunterstützung ermöglicht dem Entwickler die Verwendung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Parallelitätsmechanismen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Rowsets](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
