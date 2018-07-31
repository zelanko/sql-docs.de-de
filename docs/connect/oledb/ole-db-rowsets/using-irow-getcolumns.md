---
title: 'Mithilfe von IRow:: GetColumns | Microsoft-Dokumentation'
description: 'Zugriff auf alle Spalten in einer Zeile mithilfe von IRow:: GetColumns'
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [OLE DB Driver for SQL Server]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- GetColumns method
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 88a191c468c733979aae57886fb0365165323295
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2018
ms.locfileid: "39109792"
---
# <a name="using-irowgetcolumns"></a>Verwenden von IRow::GetColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Die **IRow**-Implementierung lässt sequenzielle Vorwärtszugriffe auf die Spalten zu. Sie können entweder mit einem einzigen Aufruf von **IRow::GetColumns** auf alle Spalten einer Zeile zugreifen oder **IRow::GetColumns** mehrmals aufrufen, um jeweils auf einige Spalten in der Zeile zuzugreifen.  
  
 Die verschiedenen Aufrufe von **IRow::GetColumns** sollten sich nicht überschneiden. Wenn beispielsweise mit dem ersten **IRow::GetColumns**-Aufruf die Spalten 1, 2 und 3 abgerufen werden, dann sollten mit dem zweiten **IRow::GetColumns**-Aufruf die Spalten 4, 5 und 6 abgerufen werden. Wenn sich spätere Aufrufe von **IRow::GetColumns** mit früheren Aufrufen überschneiden, wird das Statusflag (dwstatus-Feld in der DBCOLUMNACCESS-Struktur) auf DBSTATUS_E_UNAVAILABLE festgelegt.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Abrufen einer einzelnen Zeile mit IRow](../../oledb/ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
  
