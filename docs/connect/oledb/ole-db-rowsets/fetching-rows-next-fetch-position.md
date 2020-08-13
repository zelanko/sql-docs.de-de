---
title: Nächste Abrufposition (OLE DB-Treiber) | Microsoft-Dokumentation
description: Abrufen von Zeilen – Nächste Abrufposition
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
author: pmasl
ms.author: pelopes
ms.openlocfilehash: d6fd65f54f0c6f6aa219595e1948ce758c50b4db
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87244199"
---
# <a name="fetching-rows---next-fetch-position-ole-db-driver"></a>Abrufen von Zeilen: Nächste Abrufposition (OLE DB-Treiber)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server überwacht die nächste Abrufposition, sodass eine Sequenz von Aufrufen der **GetNextRows**-Methode (ohne Auslassungen, Richtungsänderungen oder zwischenzeitliche Aufrufe der Methoden **FindNextRow**, **Seek** oder **RestartPosition**) das gesamte Rowset liest, ohne ein Zeile auszulassen oder zu wiederholen. Die nächste Abrufposition wird entweder durch Aufrufen von **IRowset::GetNextRows**, **IRowset::RestartPosition** oder **IRowsetIndex::Seek** oder durch Aufrufen von **FindNextRow** mit einem NULL-Wert für *pBookmark* geändert. Das Aufrufen von **FindNextRow** mit einem *pBookmark*-Wert ungleich NULL beeinflusst die nächste Abrufposition nicht.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Abrufen von Zeilen](../../oledb/ole-db-rowsets/fetching-rows.md)  
  
  
