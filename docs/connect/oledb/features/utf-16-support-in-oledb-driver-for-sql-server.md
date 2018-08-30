---
title: Unterstützung von Sparsespalten im OLE DB-Treiber für SQL Server | Microsoft-Dokumentation
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
ms.author: pelopes
manager: craigg
ms.openlocfilehash: a5bd68ec8035e9a0f52300ac486ad6942384325b
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43025151"
---
# <a name="utf-16-support-in-ole-db-driver-for-sql-server"></a>UTF-16-Unterstützung im OLE DB-Treiber für SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Wenn Sie ab [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] einen Puffer mit fester Länge beim Binden eines Spaltenergebnisses oder eines Ausgabeparameters angeben, wenn das **wchar**-Zeichen, das vor dem abschließenden Zeichen in den Puffer geschrieben wird, ein hoher Codepunkt eines Ersatzzeichenpaars ist, und wenn das nächste **wchar**-Zeichen ein niedriger Codepunkt ist, fügt der OLE DB-Treiber für SQL Server den hohen Codepunkt nicht zum Puffer hinzu.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [OLE DB-Treiber für SQL Server-Features](../../oledb/features/oledb-driver-for-sql-server-features.md)   
  
  
