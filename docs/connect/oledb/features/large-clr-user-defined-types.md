---
title: Große CLR-benutzerdefinierte Typen | Microsoft-Dokumentation
description: Große CLR-benutzerdefinierte Typen im OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- large CLR user-defined types
author: pmasl
ms.author: pelopes
ms.openlocfilehash: acbdd170808ed9f6d7f67265a4e0d18f3b9e8eb0
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67989069"
---
# <a name="large-clr-user-defined-types"></a>Große benutzerdefinierte CLR-Typen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  In SQL Server 2005 waren benutzerdefinierte Typen (User-Defined Types, UDTs) in der Common Language Runtime (CLR) auf eine Größe von 8.000 Bytes beschränkt. Diese Einschränkung wurde in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] und höheren Versionen aufgehoben. CLR-UDTs werden jetzt auf eine ähnliche Weise wie große Objekttypen (LOB) behandelt. UDTs mit genau oder weniger als 8.000 Byte verhalten sich also genau wie in SQL Server 2005. Größere UDTs werden aber unterstützt und zeigen ihre Größe als "unbegrenzt" an.  
  
 Weitere Informationen finden Sie unter [Große CLR-benutzerdefinierte Typen &#40;OLE DB&#41;](../../oledb/ole-db/large-clr-user-defined-types-ole-db.md).  
  
## <a name="use-cases"></a>Anwendungsfälle   
  
 Für OLE DB umfasst die Unterstützung großer UDTs die Möglichkeit zum Streamen von UDT-Werten zum und vom Server mithilfe der ISequentialStream-Bindung.  
  
 UDTs kleiner oder gleich 8.000 Byte verhalten sich wie in SQL Server 2005. Für OLE DB können Sie immer noch kleine UDTs mithilfe einer ISequentialStream-Bindung streamen.  
  
 Manchmal muss systemeigener Code den Inhalt von CLR-UDTs verstehen, muss aber keine verwalteten Objekte instanziieren. In diesem Fall können Sie die benutzerdefinierte Serialisierung verwenden, um UDT-Werte auf dem Server in ein für die Clients bekanntes Format zu konvertieren.  
  
 Bei Anwendungen, die über einen vorhandenen Datenzugriffscode verfügen, können Sie das CLR-UDT-Verhalten auf dem Client nutzen, indem Sie UDTs über systemeigene APIs abrufen und sie mithilfe von C++ CLI Interop in Anwendungen des gemischten Modus instanziieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Treiber für SQL Server-Features](../../oledb/features/oledb-driver-for-sql-server-features.md)    
  
  
