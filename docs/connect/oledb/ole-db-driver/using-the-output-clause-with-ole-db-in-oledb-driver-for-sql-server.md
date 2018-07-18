---
title: Mithilfe der OUTPUT-Klausel mit OLE DB in OLE DB-Treiber für SQLServer | Microsoft Docs
description: Mithilfe der OUTPUT-Klausel mit OLE DB in OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|oledb-driver-for-sql-server
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 8cf2e08b76636ab8509ab07fd1f3d60a102fa76d
ms.sourcegitcommit: e1bc8c486680e6d6929c0f5885d97d013a537149
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2018
ms.locfileid: "35665330"
---
# <a name="using-the-output-clause-with-ole-db-in-ole-db-driver-for-sql-server"></a>Mithilfe der OUTPUT-Klausel mit OLE DB in OLE DB-Treiber für SQLServer
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Wenn Sie in einem INSERT-, UPDATE-, DELETE- oder MERGE-Befehl eine OUTPUT-Klausel verwenden, ist die Anzahl der betroffenen Zeilen nicht verfügbar. Die Anwendung muss die Anzahl von Zeilen im Rowset zählen, die von der OUTPUT-Klausel zurückgegeben werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines OLE DB-Treibers für eine SQL Server-Anwendung](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md) 
  
  
