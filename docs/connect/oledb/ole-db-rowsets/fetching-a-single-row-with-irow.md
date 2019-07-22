---
title: Abrufen einer einzelnen Zeile mit IRow | Microsoft-Dokumentation
description: Abrufen einer einzelnen Zeile mithilfe der IRow-Schnittstelle OLE DB Treibers für SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [OLE DB Driver for SQL Server]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- OLE DB Driver for SQL Server, fetching
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 542875dc322cd94970c238747db0adb139b9a480
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67994292"
---
# <a name="fetching-a-single-row-with-irow"></a>Abrufen einer einzelnen Zeile mit IRow
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Die Implementierung der **IRow** -Schnittstelle im OLE DB Treiber für SQL Server wird vereinfacht, um die Leistung zu verbessern. **IRow** lässt den direkten Zugriff auf Spalten eines einzelnen Zeilenobjekts zu. Wenn Sie vorab wissen, dass das Ergebnis einer Befehlsausführung genau eine Zeile erzeugt, dann lassen sich mit **IRow** die Spalten dieser Zeile abrufen. Wenn das Resultset mehrere Zeilen umfasst, macht **IRow** nur die erste Zeile verfügbar.  
  
 Die **IRow**-Implementierung lässt keine Navigation in der Zeile zu. Mit folgender Ausnahme wird auf jede Spalte der Zeile nur ein einziges Mal zugegriffen: Einmal kann zur Ermittlung der Spaltenbreite auf eine Spalte zugegriffen werden, und dann kann nochmals zum Abruf der Daten auf die Spalte zugegriffen werden.  
  
> [!NOTE]  
>  **IRow::Open** unterstützt nur das Öffnen von Objekten des Typs DBGUID_STREAM und DBGUID_NULL.  
  
 IID_IRow muss übergeben werden, um ein Zeilenobjekt mithilfe der **ICommand::Execute**-Methode zu erhalten. Die **IMultipleResults**-Schnittstelle muss zur Behandlung mehrerer Resultsets verwendet werden. **IMultipleResults** unterstützt **IRow** und **IRowset**. **IRowset** wird für Massenvorgänge verwendet.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Verwenden von IRow::GetColumns](../../oledb/ole-db-rowsets/using-irow-getcolumns.md)   
  
## <a name="see-also"></a>Weitere Informationen  
 [Rowsets](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
