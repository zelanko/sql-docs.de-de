---
title: 'Mithilfe von IRow:: GetColumns | Microsoft Docs'
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
ms.openlocfilehash: be29bec8c92036b6d53a56f4aab8ccdfc8e8c369
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/16/2018
ms.locfileid: "35690053"
---
# <a name="using-irowgetcolumns"></a>Verwenden von IRow::GetColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Die **IRow** Implementierung ermöglicht Vorwärtscursor sequenziellen Zugriff auf die Spalten. Sie können entweder alle Spalten in der Zeile mit einem einzigen Aufruf zugreifen **von IRow:: GetColumns** , oder rufen Sie **von IRow:: GetColumns** mehrere Male auf, jedes Mal, wenn Sie mehrere Spalten in der Zeile zugreifen.  
  
 Die verschiedenen Aufrufe von **von IRow:: GetColumns** sollten sich nicht überschneiden. Angenommen, wenn der erste Aufruf **von IRow:: GetColumns** Spalten 1, 2 und 3, der zweite Aufruf ruft **von IRow:: GetColumns** sollten für die Spalten 4, 5 und 6 aufrufen. Wenn spätere Aufrufe von **von IRow:: GetColumns** überlappen, ist das Statusflag (Dwstatus-Feld in der DBCOLUMNACCESS) auf DBSTATUS_E_UNAVAILABLE festgelegt.  
  
## <a name="see-also"></a>Siehe auch  
 [Abrufen einer einzelnen Zeile mit IRow](../../oledb/ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
  
