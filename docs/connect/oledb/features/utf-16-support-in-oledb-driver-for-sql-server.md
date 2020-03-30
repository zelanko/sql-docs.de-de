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
ms.openlocfilehash: 0ae8a83de24341b7f9672296a9bfe713ae882dfe
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67988760"
---
# <a name="utf-16-support-in-ole-db-driver-for-sql-server"></a>UTF-16-Unterstützung im OLE DB-Treiber für SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Wenn Sie ab [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] einen Puffer mit fester Länge beim Binden eines Spaltenergebnisses oder eines Ausgabeparameters angeben, wenn das **wchar**-Zeichen, das vor dem abschließenden Zeichen in den Puffer geschrieben wird, ein hoher Codepunkt eines Ersatzzeichenpaars ist, und wenn das nächste **wchar**-Zeichen ein niedriger Codepunkt ist, fügt der OLE DB-Treiber für SQL Server den hohen Codepunkt nicht zum Puffer hinzu.  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Treiber für SQL Server-Features](../../oledb/features/oledb-driver-for-sql-server-features.md)   
  
  
