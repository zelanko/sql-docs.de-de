---
title: UTF-16-Unterstützung im OLE DB-Treiber für SQL Server | Microsoft-Dokumentation
description: UTF-16-Unterstützung im OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 421b7e37054fbc283959373a01921fd4f9e8ca2b
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66796054"
---
# <a name="utf-16-support-in-ole-db-driver-for-sql-server"></a>UTF-16-Unterstützung im OLE DB-Treiber für SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Wenn Sie ab [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] einen Puffer mit fester Länge beim Binden eines Spaltenergebnisses oder eines Ausgabeparameters angeben, wenn das **wchar**-Zeichen, das vor dem abschließenden Zeichen in den Puffer geschrieben wird, ein hoher Codepunkt eines Ersatzzeichenpaars ist, und wenn das nächste **wchar**-Zeichen ein niedriger Codepunkt ist, fügt der OLE DB-Treiber für SQL Server den hohen Codepunkt nicht zum Puffer hinzu.  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Treiber für SQL Server-Features](../../oledb/features/oledb-driver-for-sql-server-features.md)   
  
  
