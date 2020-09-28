---
title: Verwenden der OUTPUT-Klausel mit OLE DB im OLE DB-Treiber für SQL Server | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Verwendung der OUTPUT-Klausel in einem INSERT-, UPDATE-, DELETE- oder MERGE-Befehl im OLE DB-Treiber für SQL Server.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1374dab2ac4954d173d8d131d59bfa4b39f2ad0a
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88861516"
---
# <a name="using-the-output-clause-with-ole-db-in-ole-db-driver-for-sql-server"></a>Verwenden der OUTPUT-Klausel mit OLE DB im OLE DB-Treiber für SQL Server
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Wenn Sie in einem INSERT-, UPDATE-, DELETE- oder MERGE-Befehl eine OUTPUT-Klausel verwenden, ist die Anzahl der betroffenen Zeilen nicht verfügbar. Die Anwendung muss die Anzahl von Zeilen im Rowset zählen, die von der OUTPUT-Klausel zurückgegeben werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines OLE DB-Treibers für eine SQL Server-Anwendung](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md) 
  
  
