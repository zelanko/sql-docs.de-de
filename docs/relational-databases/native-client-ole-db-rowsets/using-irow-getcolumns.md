---
title: 'Verwenden von IRow:: GetColumns | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 50608f4bb72f982ca5e4651ab5da3cb17cd35cf9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73761671"
---
# <a name="using-irowgetcolumns"></a>Verwenden von IRow::GetColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Die **IRow**-Implementierung lässt sequenzielle Vorwärtszugriffe auf die Spalten zu. Sie können entweder mit einem einzigen Aufruf von **IRow::GetColumns** auf alle Spalten einer Zeile zugreifen oder **IRow::GetColumns** mehrmals aufrufen, um jeweils auf einige Spalten in der Zeile zuzugreifen.  
  
 Die verschiedenen Aufrufe von **IRow::GetColumns** sollten sich nicht überschneiden. Wenn beispielsweise mit dem ersten **IRow::GetColumns**-Aufruf die Spalten 1, 2 und 3 abgerufen werden, dann sollten mit dem zweiten **IRow::GetColumns**-Aufruf die Spalten 4, 5 und 6 abgerufen werden. Wenn sich spätere Aufrufe von **IRow::GetColumns** mit früheren Aufrufen überschneiden, wird das Statusflag (dwstatus-Feld in der DBCOLUMNACCESS-Struktur) auf DBSTATUS_E_UNAVAILABLE festgelegt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Abrufen einer einzelnen Zeile mit IRow](../../relational-databases/native-client-ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
  
