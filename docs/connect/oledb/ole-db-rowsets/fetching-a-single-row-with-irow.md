---
title: Abrufen einer einzelnen Zeile mit IRow | Microsoft Docs
description: Abrufen einer einzelnen Zeile mithilfe von IRow-Schnittstelle von OLE DB-Treiber für SQL Server
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
- OLE DB Driver for SQL Server, fetching
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 21123e4d9918216f9b23ca2c7304bdcb1be2b0c7
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/16/2018
ms.locfileid: "35690043"
---
# <a name="fetching-a-single-row-with-irow"></a>Abrufen einer einzelnen Zeile mit IRow
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Die **IRow** schnittstellenimplementierung in der OLE DB-Treiber für SQL Server vereinfacht wird, um die Leistung zu steigern. **IRow** ermöglicht den direkten Zugriff auf Spalten eines einzelnen Zeilenobjekts. Wenn Sie vorab wissen, dass das Ergebnis einer befehlsausführung genau eine Zeile erzeugt **IRow** werden die Spalten dieser Zeile abgerufen. Wenn das Resultset mehrere Zeilen umfasst **IRow** nur die erste Zeile verfügbar.  
  
 Die **IRow** -Implementierung lässt keine Navigation in der Zeile. Mit folgender Ausnahme wird auf jede Spalte der Zeile nur ein einziges Mal zugegriffen: Einmal kann zur Ermittlung der Spaltenbreite auf eine Spalte zugegriffen werden, und dann kann nochmals zum Abruf der Daten auf die Spalte zugegriffen werden.  
  
> [!NOTE]  
>  **IRow:: Open** unterstützt nur Typs DBGUID_STREAM und DBGUID_NULL von Objekten, die geöffnet werden.  
  
 Um ein Zeilenobjekt mithilfe erhalten **ICommand:: Execute** Methode IID_IRow übergeben werden muss. Die **IMultipleResults** Schnittstelle muss verwendet werden, um mehrere Resultsets verarbeiten. **IMultipleResults** unterstützt **IRow** und **IRowset**. **IRowset** für Massenvorgänge verwendet wird.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Verwenden von IRow::GetColumns](../../oledb/ole-db-rowsets/using-irow-getcolumns.md)   
  
## <a name="see-also"></a>Siehe auch  
 [Rowsets](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
