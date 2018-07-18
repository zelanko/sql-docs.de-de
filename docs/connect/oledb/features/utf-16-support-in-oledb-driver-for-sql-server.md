---
title: UTF-16-Unterstützung in OLE DB-Treiber für SQLServer | Microsoft Docs
description: UTF-16-Unterstützung in OLE DB-Treiber für SQLServer
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
ms.openlocfilehash: bcb7393315063102315fdf5062bdfa05ee07282d
ms.sourcegitcommit: 354ed9c8fac7014adb0d752518a91d8c86cdce81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/14/2018
ms.locfileid: "35611625"
---
# <a name="utf-16-support-in-ole-db-driver-for-sql-server"></a>UTF-16-Unterstützung in OLE DB-Treiber für SQLServer
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Ab [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], wenn Sie beim Binden eines Spaltenergebnisses oder Ausgabeparameters einen Puffer fester Länge angeben und die **Wchar** Zeichen, die in den Puffer geschrieben werden, bevor das abschließende Zeichen ein hoher Ersatzzeichencodepunkt ist ein Ersatzzeichenpaars, und wenn das nächste **Wchar** Zeichen ist ein niedriger Ersatzzeichencodepunkt, OLE DB-Treiber für SQL Server wird nicht die hoher Ersatzzeichencodepunkt hinzugefügt, in den Puffer.  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB-Treiber für SQL Server-Features](../../oledb/features/oledb-driver-for-sql-server-features.md)   
  
  
