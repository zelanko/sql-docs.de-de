---
title: Erstellen eines Rowsets mit IOpenRowset | Microsoft-Dokumentation
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
ms.openlocfilehash: 2c6da41d19fed61fd83a7d4a1521ddba8726ba46
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67994312"
---
# <a name="creating-a-rowset-with-iopenrowset"></a>Erstellen eines Rowsets mit 'IopenRowset'
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server unterstützt die Methode **IOpenRowset::OpenRowset** mit den folgenden Einschränkungen:  
  
-   Eine Basistabelle oder -sicht muss in einer Datenbank-ID-Struktur angegeben sein, auf die der *pTableID*-Parameter zeigt.  
  
-   Das DBID-Element *eKind* muss DBKIND_NAME anzeigen.  
  
-   Das DBI-Element *uName* muss den Namen einer vorhandenen Basistabelle oder einer Ansicht als Unicode-Zeichenfolge angeben.  
  
-   Der *pIndexID*-Parameter von **OpenRowset** muss NULL sein.  
  
 Das Resultset von **IOpenRowset::OpenRowset** enthält ein einzelnes Rowset. Resultsets, die ein einzelnes Rowset enthalten, können von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Cursorn unterstützt werden. Die Cursorunterstützung ermöglicht dem Entwickler die Verwendung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Parallelitätsmechanismen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Rowsets](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
