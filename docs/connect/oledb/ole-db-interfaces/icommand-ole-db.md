---
title: ICommand (OLE DB) | Microsoft-Dokumentation
description: ICommand-Schnittstelle (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- ICommand [OLE DB Driver for SQL Server]
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 722536a086abf280cacded3ecd2cd0d450a417ae
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67994487"
---
# <a name="icommand-ole-db"></a>ICommand (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  In diesem Artikel wird OLE DB Verhalten erläutert, das für OLE DB Treiber für SQL Server spezifisch ist.  
  
## <a name="icommandexecute"></a>ICommand::Execute  
 Das Einfügen von Daten, die größer als die Größe einer Spalte sind, führt in der Regel zu einem Fehler. In bestimmten Situationen wird zwar S_OK zurückgegeben, der *dwStatus* wird jedoch auf DBSTATUS_S_TRUNCATED festgelegt. Dies tritt in der Regel auf, wenn Daten mit Parametern eingefügt werden, die Spalte jedoch zum Speichern der Daten nicht groß genug ist und **ICommandWithParameters::SetParameterInfo** nicht aufgerufen wurde.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schnitt &#40;stellen OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md)
  
  
