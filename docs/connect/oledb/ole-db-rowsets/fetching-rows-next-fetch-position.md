---
title: Nächste Abrufposition | Microsoft-Dokumentation
description: Abrufen von Zeilen – Nächste Abrufposition
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
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: ec1149b615c64f2113afc007c0ea04e4c4665698
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2018
ms.locfileid: "39106106"
---
# <a name="fetching-rows---next-fetch-position"></a>Abrufen von Zeilen – Nächste Abrufposition
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server überwacht die nächste Abrufposition, sodass eine Sequenz von Aufrufen der **GetNextRows**-Methode (ohne Auslassungen, Richtungsänderungen oder zwischenzeitliche Aufrufe der Methoden **FindNextRow**, **Seek** oder **RestartPosition**) das gesamte Rowset liest, ohne ein Zeile auszulassen oder zu wiederholen. Die nächste Abrufposition wird entweder durch Aufrufen von **IRowset::GetNextRows**, **IRowset::RestartPosition** oder **IRowsetIndex::Seek** oder durch Aufrufen von **FindNextRow** mit einem NULL-Wert für *pBookmark* geändert. Das Aufrufen von **FindNextRow** mit einem *pBookmark*-Wert ungleich NULL beeinflusst die nächste Abrufposition nicht.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Abrufen von Zeilen](../../oledb/ole-db-rowsets/fetching-rows.md)  
  
  
