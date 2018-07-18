---
title: Abrufen einer einzelnen Zeile mit IRow | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- SQL Server Native Client OLE DB provider, fetching
ms.assetid: 07c803ca-299a-42c5-ba02-360b9631d15f
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ab4a6e50ce20b1bceddfb639e5780938f3687639
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37411999"
---
# <a name="fetching-a-single-row-with-irow"></a>Abrufen einer einzelnen Zeile mit IRow
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Die **IRow** -schnittstellenimplementierung die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter wurde vereinfacht, um die Leistung zu steigern. **IRow** ermöglicht den direkten Zugriff auf Spalten eines einzelnen Zeilenobjekts. Wenn Sie vorab wissen, dass das Ergebnis einer befehlsausführung genau eine Zeile erzeugt **IRow** werden die Spalten dieser Zeile abgerufen. Wenn das Resultset mehrere Zeilen umfasst **IRow** nur die erste Zeile verfügbar macht.  
  
 Die **IRow** -Implementierung lässt keine Navigation in der Zeile. Mit folgender Ausnahme wird auf jede Spalte der Zeile nur ein einziges Mal zugegriffen: Einmal kann zur Ermittlung der Spaltenbreite auf eine Spalte zugegriffen werden, und dann kann nochmals zum Abruf der Daten auf die Spalte zugegriffen werden.  
  
> [!NOTE]  
>  **IRow:: Open** unterstützt nur Typs DBGUID_STREAM und DBGUID_NULL von Objekten, die geöffnet werden.  
  
 Um ein Zeilenobjekt mithilfe **ICommand:: Execute** Methode IID_IRow übergeben werden muss. Die **IMultipleResults** Schnittstelle muss verwendet werden, um die Behandlung mehrerer Resultsets. **IMultipleResults** unterstützt **IRow** und **IRowset**. **IRowset** für Massenvorgänge verwendet wird.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Verwenden von IRow::GetColumns](../../relational-databases/native-client-ole-db-rowsets/using-irow-getcolumns.md)  
  
-   [Abrufen von BLOB-Daten mit IRow](http://msdn.microsoft.com/library/badbd6ac-20aa-4891-a14f-48d38e7f30de)  
  
## <a name="see-also"></a>Siehe auch  
 [Rowsets](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
