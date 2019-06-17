---
title: 'Mithilfe von IRow:: GetColumns | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- GetColumns method
ms.assetid: 1f5d2e03-e6fe-4ea1-b71d-55d02b5d59ae
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b26d13fd5e1158c93118de3efb495469ff0d8f6b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62938628"
---
# <a name="using-irowgetcolumns"></a>Verwenden von IRow::GetColumns
  Die **IRow**-Implementierung lässt sequenzielle Vorwärtszugriffe auf die Spalten zu. Sie können entweder mit einem einzigen Aufruf von **IRow::GetColumns** auf alle Spalten einer Zeile zugreifen oder **IRow::GetColumns** mehrmals aufrufen, um jeweils auf einige Spalten in der Zeile zuzugreifen.  
  
 Die verschiedenen Aufrufe von **IRow::GetColumns** sollten sich nicht überschneiden. Wenn beispielsweise mit dem ersten **IRow::GetColumns**-Aufruf die Spalten 1, 2 und 3 abgerufen werden, dann sollten mit dem zweiten **IRow::GetColumns**-Aufruf die Spalten 4, 5 und 6 abgerufen werden. Wenn sich spätere Aufrufe von **IRow::GetColumns** mit früheren Aufrufen überschneiden, wird das Statusflag (dwstatus-Feld in der DBCOLUMNACCESS-Struktur) auf DBSTATUS_E_UNAVAILABLE festgelegt.  
  
## <a name="see-also"></a>Siehe auch  
 [Abrufen einer einzelnen Zeile mit IRow](fetching-a-single-row-with-irow.md)  
  
  
