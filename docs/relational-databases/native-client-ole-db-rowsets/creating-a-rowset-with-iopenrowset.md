---
description: Erstellen eines Rowsets mit IOpenRowset (Native Client OLE DB-Anbieter)
title: Erstellen eines Rowsets mit IOpenRowset (Native Client OLE DB Provider) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- IOpenRowset interface
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
ms.assetid: e8bc3de7-4b97-4de9-8df8-e11947d24045
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1b6d6d554c6ac0335ec0504886ea7e8de06437f6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499134"
---
# <a name="creating-a-rowset-with-iopenrowset-in-sql-server-native-client"></a>Erstellen eines Rowsets mit IOpenRowset in SQL Server Native Client
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt die **IOpenRowset:: OPENROWSET** -Methode mit den folgenden Einschränkungen:  
  
-   Eine Basistabelle oder -sicht muss in einer Datenbank-ID-Struktur angegeben sein, auf die der *pTableID*-Parameter zeigt.  
  
-   Das DBID-Element *eKind* muss DBKIND_NAME anzeigen.  
  
-   Das DBI-Element *uName* muss den Namen einer vorhandenen Basistabelle oder einer Ansicht als Unicode-Zeichenfolge angeben.  
  
-   Der *pIndexID*-Parameter von **OpenRowset** muss NULL sein.  
  
 Das Resultset von **IOpenRowset::OpenRowset** enthält ein einzelnes Rowset. Resultsets, die ein einzelnes Rowset enthalten, können von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Cursorn unterstützt werden. Die Cursorunterstützung ermöglicht dem Entwickler die Verwendung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Parallelitätsmechanismen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Rowsets](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
