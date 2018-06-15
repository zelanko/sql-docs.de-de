---
title: Nächste Abrufposition | Microsoft Docs
description: Das Abrufen von Zeilen - nächste Abrufposition
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
ms.openlocfilehash: e5fb2612c10ceb82458888c01adbfc7e156beebb
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35306409"
---
# <a name="fetching-rows---next-fetch-position"></a>Das Abrufen von Zeilen - nächste Abrufposition
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der OLE DB-Treiber für SQL Server verfolgt Verfolgen der die nächste Abrufposition daher, die eine Sequenz von Aufrufen an die **GetNextRows** Methode (ohne überspringt, Änderungen der Richtung oder dazwischen liegende aufruft, um die **FindNextRow** **Seek**, oder **RestartPosition** Methoden) das gesamte Rowset liest, ohne überspringen oder eine beliebige Zeile wiederholt. Die nächste Abrufposition wird entweder durch Aufrufen geändert **IRowset:: GetNextRows**, **IRowset:: RestartPosition**, oder **IRowsetIndex:: Seek**, oder durch Aufrufen von **FindNextRow** mit einer Null *pBookmark* Wert. Aufrufen von **FindNextRow** mit einem ungleich NULL *pBookmark* Wert wirkt sich auf die nächste Abrufposition nicht.  
  
## <a name="see-also"></a>Siehe auch  
 [Abrufen von Zeilen](../../oledb/ole-db-rowsets/fetching-rows.md)  
  
  
