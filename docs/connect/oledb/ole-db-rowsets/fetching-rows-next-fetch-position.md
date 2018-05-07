---
title: Nächste Abrufposition | Microsoft Docs
description: Das Abrufen von Zeilen - nächste Abrufposition
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: b3e7bb16d9f2c04525a0646b9f4647fdd1e811e0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="fetching-rows---next-fetch-position"></a>Das Abrufen von Zeilen - nächste Abrufposition
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der OLE DB-Treiber für SQL Server verfolgt Verfolgen der die nächste Abrufposition daher, die eine Sequenz von Aufrufen an die **GetNextRows** Methode (ohne überspringt, Änderungen der Richtung oder dazwischen liegende aufruft, um die **FindNextRow** **Seek**, oder **RestartPosition** Methoden) das gesamte Rowset liest, ohne überspringen oder eine beliebige Zeile wiederholt. Die nächste Abrufposition wird entweder durch Aufrufen geändert **IRowset:: GetNextRows**, **IRowset:: RestartPosition**, oder **IRowsetIndex:: Seek**, oder durch Aufrufen von **FindNextRow** mit einer Null *pBookmark* Wert. Aufrufen von **FindNextRow** mit einem ungleich NULL *pBookmark* Wert wirkt sich auf die nächste Abrufposition nicht.  
  
## <a name="see-also"></a>Siehe auch  
 [Abrufen von Zeilen](../../oledb/ole-db-rowsets/fetching-rows.md)  
  
  
