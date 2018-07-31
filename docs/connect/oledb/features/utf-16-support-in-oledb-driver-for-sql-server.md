---
title: UTF-16-Unterstützung im OLE DB-Treiber für SQL Server (OLE DB)
description: UTF-16-Unterstützung im OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 8374545412ca244e6af643ed10f101a714985da6
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2018
ms.locfileid: "39108142"
---
# <a name="utf-16-support-in-ole-db-driver-for-sql-server"></a>UTF-16-Unterstützung im OLE DB-Treiber für SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Wenn Sie ab [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] einen Puffer mit fester Länge beim Binden eines Spaltenergebnisses oder eines Ausgabeparameters angeben, wenn das **wchar**-Zeichen, das vor dem abschließenden Zeichen in den Puffer geschrieben wird, ein hoher Codepunkt eines Ersatzzeichenpaars ist, und wenn das nächste **wchar**-Zeichen ein niedriger Codepunkt ist, fügt der OLE DB-Treiber für SQL Server den hohen Codepunkt nicht zum Puffer hinzu.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [OLE DB-Treiber für SQL Server-Features](../../oledb/features/oledb-driver-for-sql-server-features.md)   
  
  
